---
title: Apparaat-id's van de eerste fabrikant genereren
description: ID's voor uw apparaten leren genereren
feature: Web SDK
level: Experienced
jira: KT-9728
thumbnail: KT-9728.jpeg
exl-id: 2e3c1f71-e224-4631-b680-a05ecd4c01e7
source-git-commit: fd60f7ad338c81f5b32e7951d5a00b49c5aa1756
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 0%

---

# Apparaat-id&#39;s van de eerste fabrikant genereren

Adobe Experience Cloud-toepassingen hebben van oudsher cookies gegenereerd om apparaatid&#39;s op te slaan met behulp van verschillende technologieën, zoals:

1. Cookies van andere bedrijven
1. CNAME-configuraties van eerste bedrijven die zijn ingesteld door een Adobe-server met de CNAME-configuratie van een domeinnaam
1. Door JavaScript ingestelde cookies van de eerste partij

Recente browserwijzigingen beperken de duur van dit type cookies. De koekjes van de eerste partij zijn het meest efficiënt wanneer zij gebruikend een klant-bezeten server gebruikend DNS A/AAAA-verslag in tegenstelling tot DNS CNAME worden geplaatst. De [&#x200B; eerste-partij apparaat identiteitskaart (FPID) functionaliteit &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/web-sdk/identity/first-party-device-ids) staat klanten die het Web SDK van Adobe Experience Platform uitvoeren toe om apparaat IDs in koekjes van servers te gebruiken die DNS A/AAAA-verslagen gebruiken. Deze id&#39;s kunnen vervolgens naar Adobe worden verzonden en worden gebruikt als zaden voor het genereren van Experience Cloud-id&#39;s (ECID&#39;s), wat de primaire id blijft in Adobe Experience Cloud-toepassingen.

Hier volgt een kort voorbeeld van de werking van de functionaliteit:

![&#x200B; Eerste-partij apparaat IDs (FPIDs) en Experience Cloud IDs (ECIDs) &#x200B;](../assets/kt-9728.png)

1. De browser van een eindgebruiker vraagt om een webpagina van de webserver of CDN van een klant.
1. De klant genereert een apparaat-id (FPID) op zijn webserver of CDN (de webserver moet zijn gekoppeld aan de DNS A/AAAA-record van de domeinnaam).
1. De klant stelt een cookie van de eerste partij in om de FPID in de browser van de eindgebruiker op te slaan.
1. De Adobe Experience Platform Web SDK-implementatie van door de klant doet een verzoek aan het Platform Edge Network en:
   1. Hiermee neemt u de FPID op in de identiteitskaart.
   1. Vormt een CNAME voor hun verzoeken van SDK van het Web en vormt hun gegevensstroom met de naam van hun koekje FPID.
1. Experience Platform Edge Network ontvangt de FPID en gebruikt deze om een Experience Cloud-id (ECID) te genereren.
1. De reactie van SDK van het Web van het platform verzendt ECID terug naar browser van de eindgebruiker.
1. Als de `idMigrationEnabled=true` , gebruikt Platform Web SDK JavaScript om de ECID op te slaan als de `AMCV_` -cookie in de browser van de eindgebruiker.
1. Als het `AMCV_` -cookie vervalt, wordt het proces zelf herhaald. Zolang dezelfde apparaat-id van de eerste fabrikant beschikbaar is, wordt een nieuw `AMCV_` -cookie gemaakt met dezelfde ECID-waarde als voorheen.

>[!NOTE]
>
>`idMigrationEnabled` hoeft niet op `true` te worden ingesteld om FPID te gebruiken. Met `idMigrationEnabled=false` ziet u echter wellicht geen `AMCV_` -cookie en moet u naar de ECID-waarde in de netwerkreactie zoeken.


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
>Het naamruimtesymbool voor identiteit dat wordt gebruikt in het identiteitsoverzicht, moet `FPID` worden genoemd.
>
> `FPID` is een gereserveerde naamruimte voor identiteiten die niet zichtbaar is in de interfacelijsten met naamruimten.


## ECID-generatie valideren

Valideer de implementatie door te bevestigen dat dezelfde ECID wordt gegenereerd op basis van uw apparaat-id van de eerste partij:

1. Een FPID-cookie genereren.
1. Verzend een aanvraag naar Platform Edge Network met Platform Web SDK.
1. Er wordt een cookie met de notatie `AMCV_<IMSORGID@AdobeOrg>` gegenereerd. Dit cookie bevat de ECID.
1. Maak een notitie van de cookiewaarde die wordt gegenereerd en verwijder vervolgens alle cookies voor uw site, behalve het `FPID` -cookie.
1. Stuur nog een aanvraag naar Platform Edge Network.
1. Bevestig dat de waarde in het `AMCV_<IMSORGID@AdobeOrg>` -cookie dezelfde `ECID` -waarde is als in het `AMCV_` -cookie dat is verwijderd. Als de cookiewaarde voor een bepaalde FPID gelijk is, is het zaadproces voor de ECID geslaagd.

Voor meer informatie over deze eigenschap, zie [&#x200B; de documentatie &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/first-party-device-ids.html?lang=nl-NL).
