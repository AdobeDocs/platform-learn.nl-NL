---
title: Toestemming
description: Leer hoe u toestemming implementeert in een mobiele app.
exl-id: 08042569-e16e-4ed9-9b5a-864d8b7f0216
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 1%

---

# Toestemming

Leer hoe u toestemming implementeert in een mobiele app.

Met de mobiele extensie Adobe Experience Platform Consent kunt u de verzameling met voorkeuren voor toestemming vanuit uw mobiele app inschakelen wanneer u de Adobe Experience Platform Mobile SDK en de Edge Network-extensie gebruikt. Meer informatie over de [Toegestane extensie](https://aep-sdks.gitbook.io/docs/foundation-extensions/consent-for-edge-network)in de documentatie.

## Vereisten

* App met SDK&#39;s geïnstalleerd en geconfigureerd met succes gemaakt en uitgevoerd.

## Leerdoelstellingen

In deze les zult u:

* Vraag de gebruiker om toestemming.
* Werk de extensie bij op basis van de gebruikersreactie.
* Leer hoe u de huidige status van toestemming krijgt.

## Goedkeuring aanvragen

Als u de zelfstudie vanaf het begin hebt gevolgd, zult u het instellen van de **[!UICONTROL Standaardniveau van toestemming]** in &quot;In behandeling&quot;. Om te beginnen met het verzamelen van gegevens, moet u toestemming van de gebruiker krijgen. In deze zelfstudie vraagt u eenvoudig om toestemming door in een echte app de beste praktijken voor toestemming voor uw regio te raadplegen.

1. U wilt het de gebruiker slechts eenmaal vragen. Een eenvoudige manier om dat te beheren is door eenvoudig te gebruiken `UserDefaults`.
1. Ga naar `Home.swift`.
1. De volgende code toevoegen aan `viewDidLoad()`.

   ```swift
   let defaults = UserDefaults.standard
   let consentKey = "askForConsentYet"
   let hidePopUp = defaults.bool(forKey: consentKey)
   ```

1. Als de gebruiker de waarschuwing nog niet eerder heeft gezien, geeft u deze weer en werkt u de toestemming bij op basis van hun reactie. De volgende code toevoegen aan `viewDidLoad()`.

   ```swift
   if(hidePopUp == false){
       //Consent Alert
       let alert = UIAlertController(title: "Allow Data Collection?", message: "Selecting Yes will begin data collection", preferredStyle: .alert)
       alert.addAction(UIAlertAction(title: "Yes", style: .default, handler: { action in
           //Update Consent -> "yes"
           let collectConsent = ["collect": ["val": "y"]]
           let currentConsents = ["consents": collectConsent]
           Consent.update(with: currentConsents)
           defaults.set(true, forKey: consentKey)
       }))
       alert.addAction(UIAlertAction(title: "No", style: .cancel, handler: { action in
           //Update Consent -> "no"
           let collectConsent = ["collect": ["val": "n"]]
           let currentConsents = ["consents": collectConsent]
           Consent.update(with: currentConsents)
           defaults.set(true, forKey: consentKey)
       }))
       self.present(alert, animated: true)
   }
   ```


## Huidige status van toestemming ophalen

De mobiele extensie voor toestemming onderdrukt automatisch het bijhouden van wijzigingen, voegt deze toe of staat deze toe op basis van de huidige waarde van de toestemming. U kunt ook zelf toegang krijgen tot de huidige staat van toestemming:

1. Ga naar `Home.swift`.
1. De volgende code toevoegen aan `viewDidLoad()`.

```swift
Consent.getConsents{ consents, error in
    guard error == nil, let consents = consents else { return }
    guard let jsonData = try? JSONSerialization.data(withJSONObject: consents, options: .prettyPrinted) else { return }
    guard let jsonStr = String(data: jsonData, encoding: .utf8) else { return }
    print("Consent getConsents: ",jsonStr)
}
```

In het bovenstaande voorbeeld drukt u gewoon de toestemmingsstatus af op de console. In een echt scenario, zou u het kunnen gebruiken om te wijzigen welke menu&#39;s of opties aan de gebruiker worden getoond.

## Valideren met betrouwbaarheid

1. Controleer de [Betrouwbaarheid](assurance.md) les.
1. Installeer de toepassing.
1. Start de app met de door Betrouwbaarheid gegenereerde URL.
1. Als u de bovenstaande code correct hebt toegevoegd, wordt u gevraagd om toestemming te geven. Selecteren **Ja**.
   ![instemming pop](assets/mobile-consent-validate.png)
1. U dient een **[!UICONTROL Voorkeuren voor goedkeuring bijgewerkt]** gebeurtenis in de betrouwbaarheidsinterface.
   ![toestemming valideren](assets/mobile-consent-update.png)

Volgende: **[Levenscyclusgegevens verzamelen](lifecycle-data.md)**

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)