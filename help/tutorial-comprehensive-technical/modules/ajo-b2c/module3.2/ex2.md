---
title: Adobe Journey Optimizer - External Weather API, SMS Action & more - Een externe gegevensbron definiëren
description: Adobe Journey Optimizer - External Weather API, SMS Action & more - Een externe gegevensbron definiëren
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---

# 3.2.2 Een externe gegevensbron definiëren

In deze oefening, zult u een douane externe gegevensbron tot stand brengen door gebruik van Adobe Journey Optimizer te maken.

Login aan Adobe Journey Optimizer door naar [ Adobe Experience Cloud ](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![ ACOP ](./../../../modules/ajo-b2c/module3.2/images/acophome.png)

U zult aan de **1} mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxId--` genoemd. Om van één zandbak in een andere te veranderen, klik op **Prod van de PRODUCTIE (VA7)** en selecteer de zandbak van de lijst. In dit voorbeeld, wordt de zandbak genoemd **AEP Enablement FY22**. U zult dan in de **1} mening van het Huis {van uw zandbak `--aepSandboxId--` zijn.**

![ ACOP ](./../../../modules/ajo-b2c/module3.2/images/acoptriglp.png)

In het linkermenu, scrol neer en klik **Configuraties**. Daarna, klik **leiden** knoop onder **Gegevensbronnen**.

![ Demo ](./images/menudatasources.png)

U zult dan de **Bronnen van Gegevens** lijst zien.
Klik **creëren Gegevens Source** beginnen uw gegevensbron toe te voegen.

![ Demo ](./images/dshome.png)

Er verschijnt een lege pop-up voor de gegevensbron.

![ Demo ](./images/emptyds.png)

Alvorens u kunt beginnen dit te vormen, zult u een rekening met de **Open Weather Kaart** dienst nodig hebben. Voer de volgende stappen uit om uw account te maken en uw API-sleutel op te halen.

Ga naar [ https://openweathermap.org/ ](https://openweathermap.org/). Voor de homepage, klik **Teken binnen**.

![ WeatherMap ](./images/owm.png)

Klik **creeer een Rekening**.

![ WeatherMap ](./images/owm1.png)

Vul de details in.

![ WeatherMap ](./images/owm2.png)

Klik **creëren Rekening**.

![ WeatherMap ](./images/owm3.png)

U wordt vervolgens omgeleid naar uw accountpagina.

![ WeatherMap ](./images/owm4.png)

In het menu, klik **API Sleutels** om uw API Sleutel terug te winnen, die u uw douane externe gegevensbron zult moeten plaatsen.

![ WeatherMap ](./images/owm5.png)

Een **Sleutel van API** kijkt als dit: `b2c4c36b6bb59c3458d6686b05311dc3`.

U kunt de **API Documentatie** voor **Huidige Weer** [ hier ](https://openweathermap.org/current) vinden.

In ons gebruik-geval, zullen wij de verbinding met Open Kaart van het Weer uitvoeren die op de plaats wordt gebaseerd de klant in is.

![ WeatherMap ](./images/owm6.png)

Ga terug naar **Adobe Journey Optimizer**, aan uw lege **Externe Gegevens Source** popup.

![ Demo ](./images/emptyds.png)

Gebruik `--demoProfileLdap--WeatherApi` als naam voor de gegevensbron. In dit voorbeeld is de naam van de gegevensbron `vangeluwWeatherApi ` .

Stel Beschrijving in op: `Access to the Open Weather Map` .

URL voor Open Weather Kaart API is: **http://api.openweathermap.org/data/2.5/weather?units=metric**

![ Demo ](./images/dsname.png)

Vervolgens moet u de verificatie selecteren die u wilt gebruiken.

Gebruik de volgende variabelen:

| Veld | Waarde |
|:-----------------------:| :-----------------------|
| Type | **API sleutel** |
| Naam | **APPID** |
| Waarde | **uw API Sleutel** |
| Locatie | **Parameter van de Vraag** |

![ Demo ](./images/dsauth.png)

Tot slot moet u a **FieldGroup** bepalen, die fundamenteel het verzoek is u naar het Weer API zult verzenden. In ons geval, willen wij de naam van de Stad gebruiken om het Huidige Weer voor die Stad te verzoeken.

![ Demo ](./images/fg.png)

Volgens de Weather API-documentatie moeten we een parameter `q=City` verzenden.

![ Demo ](./images/owmapi.png)

Configureer uw FieldGroup als volgt om de verwachte API-aanvraag af te stemmen:

>[!IMPORTANT]
>
>De naam van de veldgroep moet uniek zijn. Gebruik de volgende naamgevingsconventie: `--demoProfileLdap--WeatherByCity` in dit geval moet de naam `vangeluwWeatherByCity` zijn

![ Demo ](./images/fg1.png)

Voor de Payload van de Reactie, moet u een voorbeeld van de Reactie kleven die door Weather API zal worden verzonden.

U kunt de verwachte Reactie van API JSON op de API documentatiepagina [ hier ](https://openweathermap.org/current) vinden.

![ Demo ](./images/owmapi1.png)

Of u kunt de JSON-reactie hier kopiëren:

```json
{"coord": { "lon": 139,"lat": 35},
  "weather": [
    {
      "id": 800,
      "main": "Clear",
      "description": "clear sky",
      "icon": "01n"
    }
  ],
  "base": "stations",
  "main": {
    "temp": 281.52,
    "feels_like": 278.99,
    "temp_min": 280.15,
    "temp_max": 283.71,
    "pressure": 1016,
    "humidity": 93
  },
  "wind": {
    "speed": 0.47,
    "deg": 107.538
  },
  "clouds": {
    "all": 2
  },
  "dt": 1560350192,
  "sys": {
    "type": 3,
    "id": 2019346,
    "message": 0.0065,
    "country": "JP",
    "sunrise": 1560281377,
    "sunset": 1560333478
  },
  "timezone": 32400,
  "id": 1851632,
  "name": "Shuzenji",
  "cod": 200
}
```

Kopieer de bovenstaande JSON-reactie naar het klembord en ga vervolgens naar het configuratiescherm van de aangepaste gegevensbron.

Klik **uitgeven het pictogram van de Lading**.

![ Demo ](./images/owmapi2.png)

U ziet een popup waar u nu de bovengenoemde Reactie van JSON moet kleven.

![ Demo ](./images/owmapi3.png)

Plak uw JSON-reactie, waarna u dit ziet. Klik **sparen**.

![ Demo ](./images/owmapi4.png)

De aangepaste configuratie van de gegevensbron is nu voltooid. De rol omhoog en klikt **sparen**.

![ Demo ](./images/dssave.png)

Uw gegevensbron is nu met succes gecreeerd en maakt deel uit van de **Bronnen van Gegevens** lijst.

![ Demo ](./images/dslist.png)

Volgende Stap: [ 3.2.3 bepaalt een douaneactie ](./ex3.md)

[Terug naar module 3.2](journey-orchestration-external-weather-api-sms.md)

[Terug naar alle modules](../../../overview.md)
