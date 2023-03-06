---
title: Apparaat-id's van de eerste fabrikant genereren
description: ID's voor uw apparaten leren genereren
feature: Web SDK
kt: 9728
thumbnail: KT-9728.jpeg
exl-id: 2e3c1f71-e224-4631-b680-a05ecd4c01e7
source-git-commit: 0c3edbeaa5cb46f159a3efe72c108dfd2235f04b
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 1%

---

# Apparaat-id&#39;s van de eerste fabrikant genereren

Adobe Experience Cloud-toepassingen hebben van oudsher cookies gegenereerd om apparaatid&#39;s op te slaan met behulp van verschillende technologieën, zoals:

1. Cookies van andere bedrijven
1. De koekjes van de eerste partij die door een server van Adobe worden geplaatst gebruikend de configuratie van CNAME van een domeinnaam
1. Cookies van eerste partijen ingesteld door JavaScript

Recente browserwijzigingen beperken de duur van dit type cookies. De koekjes van de eerste partij zijn het meest efficiënt wanneer zij gebruikend een klant-bezeten server gebruikend DNS A/AAAA-verslag in tegenstelling tot DNS CNAME worden geplaatst. Met de FPID-functionaliteit (First-party device ID) kunnen klanten die Adobe Experience Platform Web SDK implementeren, apparaat-id&#39;s gebruiken in cookies van servers die DNS A/AAAA-records gebruiken. Deze id&#39;s kunnen vervolgens naar Adobe worden verzonden en als zaden worden gebruikt om Experience Cloud-id&#39;s (ECID&#39;s) te genereren, wat in Adobe Experience Cloud-toepassingen de primaire id blijft.

Hier volgt een kort voorbeeld van de werking van de functionaliteit:

![FPID&#39;s (First-party device ID&#39;s) en Experience Cloud-id&#39;s (ECID&#39;s)](../assets/kt-9728.png)

1. De browser van een eindgebruiker vraagt om een webpagina van de webserver of CDN van een klant.
1. De klant genereert een apparaat-id (FPID) op zijn webserver of CDN (de webserver moet zijn gekoppeld aan de DNS A/AAAA-record van de domeinnaam).
1. De klant stelt een cookie van de eerste partij in om de FPID in de browser van de eindgebruiker op te slaan.
1. De Adobe Experience Platform Web SDK-implementatie van de van de klant vraagt om een aanvraag bij het Edge Network van de Platform, inclusief de FPID in de identiteitskaart.
1. Experience Platform Edge Network ontvangt de FPID en gebruikt deze om een Experience Cloud-id (ECID) te genereren.
1. De reactie van SDK van het Web van het Platform verzendt ECID terug naar browser van de eindgebruiker.
1. Als de `idMigrationEnabled=true`, gebruikt Platform Web SDK JavaScript om de ECID op te slaan als de `AMCV_` cookie in de browser van de eindgebruiker.
1. In geval van `AMCV_` cookie verloopt, wordt het proces zelf herhaald. Zolang dezelfde apparaat-id van de eerste fabrikant beschikbaar is, voert u een nieuwe `AMCV_` cookie wordt gemaakt met dezelfde ECID-waarde als voorheen.

>[!NOTE]
>
>De `idMigrationEnabled` hoeft niet te worden ingesteld op `true` om FPID te gebruiken. Met `idMigrationEnabled=false` u kunt geen `AMCV_` cookie, echter, en zal naar de waarde ECID in de netwerkreactie moeten zoeken.


In deze zelfstudie wordt een specifiek voorbeeld met PHP-scripttaal gebruikt om te tonen hoe:

* Een UUIDv4 genereren
* UUIDv4-waarde naar een cookie schrijven
* De cookiewaarde opnemen in het identiteitsoverzicht
* De ECID-generatie valideren

Aanvullende documentatie met betrekking tot apparaat-id&#39;s van de eerste fabrikant vindt u in de productdocumentatie.

## Een UUIDv4 genereren

PHP heeft geen native bibliotheek voor het genereren van UUID, dus deze codevoorbeelden zijn uitgebreider dan wat waarschijnlijk vereist zou zijn als een andere programmeertaal werd gebruikt. PHP werd gekozen voor dit voorbeeld omdat het een breed ondersteunde server-side taal is.


Wanneer de volgende functie wordt aangeroepen, genereert deze een willekeurige UUID-versie 4:

```
<?php
    
    function guidv4($data)
    {
        $data = $data ?? random_bytes(16);

        $data[6] = chr(ord($data[6]) & 0x0f | 0x40); // set version to 0100
        $data[8] = chr(ord($data[8]) & 0x3f | 0x80); // set bits 6-7 to 10

        return vsprintf('%s%s-%s-%s-%s-%s%s%s', str_split(bin2hex($data), 4));
    }

?>
```

## UUIDv4-waarde naar een cookie schrijven

De volgende code vraagt de bovenstaande functie om een UUID te genereren. Vervolgens worden de cookie-vlaggen ingesteld die door uw organisatie worden bepaald. Als er al een cookie is gegenereerd, wordt de vervaldatum verlengd.

```
<?php

    if(!isset($_COOKIE['FPID'])) {
        $cookie_value = guidv4(openssl_random_pseudo_bytes(16));        
        $arr_cookie_options = array (
        'expires' => time() + 60*60*24*30*13,
        'path' => '/',
        'domain' => 'mysiteurl.com',
        'secure' => true,
        'httponly' => true,
        'samesite' => 'lax'
        );
        setcookie($cookie_name, $cookie_value, $arr_cookie_options);
        $_COOKIE[$cookie_name] = $cookie_value;
    }
    else {
        $cookie_value = $_COOKIE[$cookie_name];
        $arr_cookie_options = array (
        'expires' => time() + 60*60*24*30*13,
        'path' => '/',
        'domain' => 'mysiteurl.com',
        'secure' => true,
        'httponly' => true,
        'samesite' => 'lax'
        );
        setcookie($cookie_name, $cookie_value, $arr_cookie_options);
    }

?>
```

>[!NOTE]
>
>De cookie die de apparaat-id van de eerste fabrikant bevat, kan een willekeurige naam hebben.

## De cookie-waarde opnemen in het identiteitsoverzicht

De laatste stap is om PHP te gebruiken om de koekjeswaarde aan de Kaart van de Identiteit te echo.


```
{
    "identityMap": {
        "FPID": [
                    {
                        "id": "<? echo $_COOKIE[$cookie_name] ?>",
                        "authenticatedState": "ambiguous",
                        "primary": true
                    }
                ]
        }
}
```

>[!IMPORTANT]
>
>Het naamruimtesymbool voor identiteiten dat wordt gebruikt in het identiteitsoverzicht, moet worden aangeroepen `FPID`.
>
> `FPID` is een gereserveerde naamruimte voor de identiteit die niet zichtbaar is in de interfacelijsten met naamruimten.


## ECID-generatie valideren

Valideer de implementatie door te bevestigen dat dezelfde ECID wordt gegenereerd op basis van uw apparaat-id van de eerste partij:

1. Genereer een FPID-cookie.
1. Verzend een verzoek naar het Netwerk van de Rand van het Platform gebruikend het Web SDK van het Platform.
1. Een cookie met de notatie `AMCV_<IMSORGID@AdobeOrg>` wordt gegenereerd. Dit cookie bevat de ECID.
1. Maak een notitie van de cookiewaarde die wordt gegenereerd en verwijder vervolgens alle cookies voor uw site behalve de `FPID` cookie.
1. Verzend een ander verzoek naar het Netwerk van de Rand van het Platform.
1. Bevestig de waarde in het dialoogvenster `AMCV_<IMSORGID@AdobeOrg>` cookie is hetzelfde `ECID` waarde zoals in de `AMCV_` cookie die is verwijderd. Als de cookiewaarde voor een bepaalde FPID gelijk is, is het zaadproces voor de ECID geslaagd.

Voor meer informatie over deze functie raadpleegt u [de documentatie](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/first-party-device-ids.html).
