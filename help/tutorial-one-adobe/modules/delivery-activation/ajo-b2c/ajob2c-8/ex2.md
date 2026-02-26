---
title: Uw georkestreerde campagne maken
description: Uw georkestreerde campagne maken
kt: 5342
doc-type: tutorial
exl-id: f3ca3230-db30-4e41-91f1-9324b12211a6
source-git-commit: 0328260e8699107bc82103af98caae684319a60d
workflow-type: tm+mt
source-wordcount: '1075'
ht-degree: 0%

---

# 3.8.2 Maak uw georkestreerde campagne

## 3.8.2.1 Uw geordende campagne maken

Ga naar **Campagnes**. Klik **creeer campagne**.

![ AJO OC ](./images/ajooc1.png)

Selecteer **Orchestration - marketing** en klik **bevestigen**.

![ AJO OC ](./images/ajooc2.png)

Ga de campagnenaam in: `--aepUserLdap-- - CitiSignal Family Account Optimization Campaign` en klik **sparen**.

![ AJO OC ](./images/ajooc3.png)

Dan moet je dit zien. Klik op het pictogram **+** .

![ AJO OC ](./images/ajooc4.png)

Selecteer **Fork**.

![ AJO OC ](./images/ajooc5.png)

### Gebouwd publiek 1

Klik het **+** pictogram en selecteer dan **Publiek van de Bouwstijl**.

![ AJO OC ](./images/ajooc6.png)

Klik om de omslag voor **het richten afmeting** te openen.

![ AJO OC ](./images/ajooc7.png)

Selecteer **`--aepUserLdap--_citisignal_recipients`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc8.png)

Klik **creëren publiek**.

![ AJO OC ](./images/ajooc9.png)

Klik **toevoegen voorwaarde**.

![ AJO OC ](./images/ajooc10.png)

Selecteer **receiving_type** en klik **bevestigen**.

![ AJO OC ](./images/ajooc11.png)

Ga **`account_holder`** op het gebied **Waarde** in en klik **berekent**.

![ AJO OC ](./images/ajooc12.png)

U zou dan een aantal voor **gerichte profielen** moeten zien. Klik ergens in het grijze gebied zoals aangegeven.

![ AJO OC ](./images/ajooc13.png)

Klik **toevoegen voorwaarde**.

![ AJO OC ](./images/ajooc14.png)

Boor neer aan **`citisignal_accounts`**.

![ AJO OC ](./images/ajooc15.png)

Selecteer **`account_status`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc16.png)

Ga **`active`** op het gebied **Waarde** in. Klik vervolgens ergens in het grijze gebied zoals aangegeven.

![ AJO OC ](./images/ajooc17.png)

Klik **toevoegen voorwaarde**.

![ AJO OC ](./images/ajooc18.png)

Boor neer aan **`citisignal_mobile_subscriptions`**.

![ AJO OC ](./images/ajooc19.png)

Selecteer **`subscription_id`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc20.png)

Laat de schakelaar voor **samengevoegde gegevens** toe. Selecteer vervolgens het volgende:

- **samengevoegde functie**: **Telling**
- **Exploitant**: **groter dan of gelijk aan**
- **Waarde**: **1**

Klik **bevestigen**.

![ AJO OC ](./images/ajooc21.png)

Dan moet je dit zien. Klik **bevestigen**.

![ AJO OC ](./images/ajooc22.png)

### publiek 2 samenstellen

Klik op het pictogram **+** op het volgende knooppunt in het andere pad.

![ AJO OC ](./images/ajooc23.png)

Selecteer **Bouwstijl publiek**.

![ AJO OC ](./images/ajooc24.png)

Klik om de omslag voor **het richten afmeting** te openen.

![ AJO OC ](./images/ajooc25.png)

Selecteer **`--aepUserLdap--_mobile_subscriptions`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc26.png)

Klik **creëren publiek**.

![ AJO OC ](./images/ajooc27.png)

Klik **toevoegen voorwaarde**.

![ AJO OC ](./images/ajooc28.png)

Selecteer **subscription_status** en klik **bevestigen**.

![ AJO OC ](./images/ajooc29.png)

Ga **`active`** op het gebied **Waarde** in. Dan, klik **toevoegen voorwaarde**.

![ AJO OC ](./images/ajooc30.png)

Selecteer **`is_upgrade_eligible`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc31.png)

Plaats de **Waarde** aan **waar**

![ AJO OC ](./images/ajooc32.png)

Klik **berekenen** om een schatting van de profielen te zien die voor dit publiek kwalificeren. Dan, klik **bevestigen**

![ AJO OC ](./images/ajooc33.png)

### Splitsen

Klik **+** pictogram en selecteer dan **Splitsen**.

![ AJO OC ](./images/ajooc34.png)

Verander het gebied **Etiket** in **Behandeling 90/10 vs Controle**. Klik om de objecten **Subset** te openen.

![ AJO OC ](./images/ajooc35.png)

Laat de schakelaar voor **toe toelaten grens** en plaats de **grootte van de Grens** aan **10 percenten**.

![ AJO OC ](./images/ajooc36.png)

Klik **toevoegen segment** en dan zou u het **voorwerp moeten zien van het Resultaat** dat wordt toegevoegd.

Klik **sparen**.

![ AJO OC ](./images/ajooc37.png)

### Doelgroep opslaan

Klik **+** pictogram en selecteer dan **sparen publiek**.

![ AJO OC ](./images/ajooc38.png)

Plaats het etiket van het gebied **publiek** aan **`--aepUserLdap-- - Control Group`**. Klik **Toewijzing van het publiek** toevoegen.

![ AJO OC ](./images/ajooc39.png)

Boor neer aan **richtend afmeting**.

![ AJO OC ](./images/ajooc40.png)

Selecteer **`account_id`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc41.png)

Plaats het **de afbeeldingsgebied van het Profiel** aan **`--aepUserLdap--_citisignal_recipients - account_id`**.

![ AJO OC ](./images/ajooc41a.png)

### Verrijking: internetabonnement

Klik op het pictogram **+** .

![ AJO OC ](./images/ajooc42.png)

Selecteer **Verrijking**.

![ AJO OC ](./images/ajooc43.png)

Dan moet je dit zien. Klik **verrijkingsgegevens** toevoegen.

![ AJO OC ](./images/ajooc44.png)

Boor neer aan **`Targeting dimension`**.

![ AJO OC ](./images/ajooc44a.png)

Boor neer aan **`citisignal_accounts`**.

![ AJO OC ](./images/ajooc45.png)

Boor neer aan **`citisignal_internet_subscriptions`**.

![ AJO OC ](./images/ajooc45a.png)

Selecteer **`account_id`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc46.png)

Dan moet je dit zien. Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc47.png)

Selecteer **`subscription_status`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc48.png)

Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc49.png)

Selecteer **`connection_type`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc50.png)

Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc51.png)

Selecteer **`service_city`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc52.png)

Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc53.png)

Selecteer **`avg_bandwidth_usage_gb`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc54.png)

Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc55.png)

Selecteer **`data_cap_gb`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc56.png)

Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc57.png)

Selecteer **`advertised_speed_mbps`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc58.png)

Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc59.png)

Selecteer **`monthly_recurring_charge`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc60.png)

Klik **sparen**.

![ AJO OC ](./images/ajooc61.png)

De rol omhoog en verandert het gebied **Etiket** aan `Enrichment: Internet Subscription`.

![ AJO OC ](./images/ajooc61a.png)

### Verrijking: abonnement op mobiele apparaten

Klik **+** pictogram op de volgende knoop en selecteer **Verrijking**.

![ AJO OC ](./images/ajooc62.png)

Verander het gebied **Etiket** aan `Enrichment: Mobile Devices Subscription` en klik dan **verrijkingsgegevens** toevoegen.

![ AJO OC ](./images/ajooc63.png)

Boor neer aan **het richten afmeting**.

![ AJO OC ](./images/ajooc64.png)

Boor neer aan **`citisignal_accounts`**.

![ AJO OC ](./images/ajooc65.png)

Boor neer aan **`citisignal_mobile_subscriptions`**.

![ AJO OC ](./images/ajooc65a.png)

Selecteer **`phone_number`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc66.png)

Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc67.png)

Boor neer aan **`citisignal_equipment_subscriptions`**.

![ AJO OC ](./images/ajooc68.png)

Selecteer **`model`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc68a.png)

Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc69.png)

Boor neer aan **`citisignal_equipment_subscriptions`**.

![ AJO OC ](./images/ajooc69a.png)

Selecteer **`recommended_device_model`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc70.png)

Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc71.png)

Boor neer aan **`citisignal_equipment_subscriptions`**.

![ AJO OC ](./images/ajooc71a.png)

Selecteer **`is_upgrade_eligible`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc72.png)

U kunt nu de voortgang testen door een test uit te voeren en te zien welke gegevens beschikbaar zijn in uw campagne.

Sparen uw veranderingen en klik dan **Begin**.

![ AJO OC ](./images/ajooctest1.png)

Na enige tijd moet je dit zien. Klik **resultaten van de Voorproef**.

![ AJO OC ](./images/ajooctest2.png)

Dan zou je iets gelijkaardigs moeten zien. Klik **dicht**.

![ AJO OC ](./images/ajooctest3.png)

Ga terug in de knoop **Verrijking: Mobiele Abonnement van Apparaten**.

Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc73.png)

Selecteer **`account_id`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc74.png)

Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc75.png)

Selecteer **`subscription_id`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc76.png)

Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc77.png)

Selecteer **`renewal_eligibility_date`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc78.png)

Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc79.png)

Selecteer **`line_user_recipient_id`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc80.png)

Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc81.png)

Selecteer **`current_device_id`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc82.png)

Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc86.png)

Selecteer **`contract_start_date`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc87.png)

Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc89.png)

Boor neer aan **`citisignal_equipment_subscriptions`**.

![ AJO OC ](./images/ajooc90.png)

Selecteer **`manufacturer`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc91.png)

Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc92.png)

Boor neer aan **`citisignal_equipment_subscriptions`**.

![ AJO OC ](./images/ajooc93.png)

Selecteer **`device_age_months`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc94.png)

Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc95.png)

Boor neer aan **`citisignal_equipment_subscriptions`**.

![ AJO OC ](./images/ajooc96.png)

Selecteer **`trade_in_value`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc97.png)

Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc98.png)

Boor neer aan **`citisignal_equipment_subscriptions`**.

![ AJO OC ](./images/ajooc99.png)

Selecteer **`monthly_payment`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc100.png)

### Verrijking: abonnement op mobiele apparaten

Dan moet je dit hebben. Klik **sparen**. Dan, klik het **+** pictogram om een nieuwe knoop toe te voegen en **Verrijking** te selecteren.

![ AJO OC ](./images/ajooc101.png)

Dan moet je dit zien. Klik **verrijkingsgegevens** toevoegen.

![ AJO OC ](./images/ajooc102.png)

Boor neer aan **het richten afmeting**.

![ AJO OC ](./images/ajooc103.png)

Boor neer aan **`citisignal_offer_eligibility`**.

![ AJO OC ](./images/ajooc104.png)

Boor neer aan **`citisignal_offers`**.

![ AJO OC ](./images/ajooc105.png)

Selecteer **`offer_name`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc106.png)

Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc107.png)

Boor neer aan **`citisignal_offers`**.

![ AJO OC ](./images/ajooc108.png)

Selecteer **`offer_code`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc109.png)

Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc110.png)

Boor neer aan **`citisignal_offers`**.

![ AJO OC ](./images/ajooc111.png)

Selecteer **`offer_description`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc112.png)

Klik **toevoegen attributen**.

![ AJO OC ](./images/ajooc110.png)

Boor neer aan **`citisignal_offers`**.

![ AJO OC ](./images/ajooc113.png)

Selecteer **`offer_description`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc114.png)

Schakel **toe laat het sorteren**.

![ AJO OC ](./images/ajooc115.png)

Boor neer aan **`citisignal_offers`**.

![ AJO OC ](./images/ajooc116.png)

Selecteer **`offer_priority`** en klik **bevestigen**.

![ AJO OC ](./images/ajooc117.png)

Je kunt nu je campagne testen. Klik **Begin**.

![ AJO OC ](./images/ajooc118.png)

Na enige tijd moet u dit zien. Klik het **Resultaat** en selecteer dan **Resultaten van de Voorproef**.

![ AJO OC ](./images/ajooc120.png)

Dan zou je iets gelijkaardigs moeten zien.

![ AJO OC ](./images/ajooc121.png)

### E-mailactiviteit

Klik **+** pictogram en selecteer dan **E-mail**.

![ AJO OC ](./images/ajooc122.png)

Klik **uitgeven e-mail**.

![ AJO OC ](./images/ajooc123.png)

Ga naar **Acties**.

![ AJO OC ](./images/ajooc124.png)

Selecteer de **configuratie van het E-mailkanaal** die u vóór creeerde en dan **klikt geef inhoud** uit.

![ AJO OC ](./images/ajooc125.png)

Voor de **Onderwerpregel**, kleef dit:

`{{target.--aepUserLdap--_citisignal_recipients.first_name}}, Your CitiSignal Family Account Summary`

Klik **uitgeeft e-maillichaam**.

![ AJO OC ](./images/ajooc126.png)

## Volgende stappen

Ga terug naar [ Adobe Journey Optimizer: Geordende Campagnes ](./ajocampaigns.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../../overview.md){target="_blank"}
