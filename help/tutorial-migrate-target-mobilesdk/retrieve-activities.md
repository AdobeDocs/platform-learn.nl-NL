---
title: Doelactiviteiten ophalen - De Adobe Target-implementatie in uw mobiele app migreren naar de Offer Decisioning- en Target-extensie
description: Leer hoe u Adobe Target-activiteiten ophaalt tijdens het migreren van de Adobe Target naar de extensie Offer Decisioning en Target Mobile.
exl-id: 39569088-a254-4e64-9956-0c6e1a8ed2a5
source-git-commit: 876e664a213aec954105bf2d5547baab5d8a84ea
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---

# Doelactiviteiten ophalen

Voor mobiele doelimplementaties worden regionale selectievakjes (nu ook wel &quot;bereik&quot; genoemd) gebruikt om inhoud te leveren van activiteiten die gebruikmaken van de op formulieren gebaseerde Experience Composer van Target. U moet uw mobiele toepassing bijwerken om werkingsgebied in uw netwerkvraag te omvatten.

De inhoud die door Target wordt geretourneerd, ook wel &quot;aanbiedingen&quot; genoemd, bestaat meestal uit tekst of een stuk dat u in uw toepassing moet gebruiken om de uiteindelijke ervaring van de klant weer te geven. Aanbiedingen van Doel worden vaak gebruikt om:

* Functiemarkeringen inschakelen in uw toepassing
* Alternatieve tekst of afbeeldingen behouden

Als u activiteiten hebt die in zowel de extensie van het Doel als de extensie van Offer Decisioning en Doel van uw toepassing moeten worden uitgevoerd, moet u de test grondig uitvoeren. Als u verschillende aanbiedingen voor verschillende versies van uw app moet gebruiken, kunt u overwegen de doelopties in de interface te gebruiken om verschillende aanbiedingen aan de verschillende versies te leveren.

Zorg er altijd voor dat u foutafhandeling opneemt om geschikte ervaringen onder fouten weer te geven.


## Inhoud aanvragen en op aanvraag toepassen

>[!IMPORTANT]
>
>Nadat u inhoud op de app hebt toegepast, moet u de API van `displayed` starten om aan Target te laten weten dat de bezoeker de alternatieve of standaardinhoud heeft gezien die in de activiteit is opgegeven. Gelieve te zien de [ de omzettingsgebeurtenissen van het Doel van het Spoor ](track-events.md) pagina voor meer details.


+++ Android-voorbeeld

>[!BEGINTABS]

>[!TAB  optimaliseer SDK ]

```Java
// Mboxes for Target activities
final DecisionScope decisionScope1 = DecisionScope("myTargetMbox1");
final DecisionScope decisionScope2 = new DecisionScope("myTargetMbox2");
 
final List<DecisionScope> decisionScopes = new ArrayList<>();
decisionScopes.add(decisionScope1);
decisionScopes.add(decisionScope2);
 
// Prefetch the Target mboxes
Optimize.updatePropositions(decisionScopes,
                            new HashMap<String, Object>() {
                                {
                                    put("xdmKey", "xdmValue");
                                }
                            },
                            new HashMap<String, Object>() {
                                {
                                    put("dataKey", "dataValue");
                                }
                            },
                            new AdobeCallbackWithOptimizeError<Map<DecisionScope, OptimizeProposition>>() {
                                @Override
                                public void fail(AEPOptimizeError optimizeError) {
                                    // Log in case of error
                                    Log.d("Target Prefetch error", optimizeError.title);
                                }
 
                                @Override
                                public void call(Map<DecisionScope, OptimizeProposition> propositionsMap) {
                                    // Retrieve cached propositions if prefetch succeeds
                                    Optimize.getPropositions(scopes, new AdobeCallbackWithError<Map<DecisionScope, OptimizeProposition>>() {
                                        @Override
                                      public void fail(final AdobeError adobeError) {
                                              // handle error
                                        }
 
                                        @Override
                                        public void call(Map<DecisionScope, OptimizeProposition> propositionsMap) {
                                              if (propositionsMap != null && !propositionsMap.isEmpty()) {
                                                // get the propositions for the given decision scopes
                                                if (propositionsMap.contains(decisionScope1)) {
                                                      final OptimizeProposition proposition1 = propsMap.get(decisionScope1)
                                                      // read proposition1 offers and display them
                                                }
                                                if (propositionsMap.contains(decisionScope2)) {
                                                      final OptimizeProposition proposition2 = propsMap.get(decisionScope2)
                                                      // read proposition2 offers and display them
                                                }
                                              }
                                        }
                                      });
                                }
                            });
```

>[!ENDTABS]

+++

+++ iOS-voorbeeld

>[!BEGINTABS]

>[!TAB  optimaliseer SDK ]

```Swift
// Mboxes for Target activities
let decisionScope1 = DecisionScope(name: "myTargetMbox1")
let decisionScope2 = DecisionScope(name: "myTargetMbox2")
 
// Prefetch the Target mboxes
Optimize.updatePropositions(for: [decisionScope1, decisionScope2]
                            withXdm: ["xdmKey": "xdmValue"]
                            andData: ["dataKey": "dataValue"]) { data, error in
            if let error = error as? AEPOptimizeError {
                // handle error
                return
            }
            // Retrieve cached propositions if prefetch succeeds
            Optimize.getPropositions(for: [decisionScope1, decisionScope2]) { propositionsDict, error in
                if let error = error {
                    // handle error
                    return
                }
 
                if let propositionsDict = propositionsDict {
                    // get the propositions for the given decision scopes
 
                    if let proposition1 = propositionsDict[decisionScope1] {
                        // read proposition1 offers and display them
                    }
 
                    if let proposition2 = propositionsDict[decisionScope2] {
                        // read proposition2 offers and display them
                    }
                }
            }
        }
```

>[!ENDTABS]

+++



Daarna, leer hoe te [ parameters overgaan van het Doel gebruikend Offer Decisioning en de uitbreiding van het Doel ](send-parameters.md).

>[!NOTE]
>
>We helpen u graag succesvol te zijn met uw mobiele doelmigratie van de doelextensie naar de Offer Decisioning en de doelextensie. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-adobe-target-to-mobile-sdk-on-edge/m-p/747484#M625) te posten.
