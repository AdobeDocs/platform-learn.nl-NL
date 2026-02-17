---
title: Uw georkestreerde campagne maken
description: Uw georkestreerde campagne maken
kt: 5342
doc-type: tutorial
exl-id: f3ca3230-db30-4e41-91f1-9324b12211a6
source-git-commit: 53be5cf34db144e346f9810359b583072743382f
workflow-type: tm+mt
source-wordcount: '830'
ht-degree: 0%

---

# 3.8.2 Maak uw georkestreerde campagne

## 3.8.2.1 Uw geordende campagne maken

Ga naar **Campagnes**. Klik **creeer campagne**.

![&#x200B; AJO OC &#x200B;](./images/ajooc1.png)

Selecteer **Orchestration - marketing** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc2.png)

Ga de campagnenaam in: `--aepUserLdap-- - CitiSignal Family Account Optimization Campaign` en klik **sparen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc3.png)

Dan moet je dit zien. Klik op het pictogram **+** .

![&#x200B; AJO OC &#x200B;](./images/ajooc4.png)

Selecteer **Fork**.

![&#x200B; AJO OC &#x200B;](./images/ajooc5.png)

### Gebouwd publiek 1

Klik het **+** pictogram en selecteer dan **Publiek van de Bouwstijl**.

![&#x200B; AJO OC &#x200B;](./images/ajooc6.png)

Klik om de omslag voor **het richten afmeting** te openen.

![&#x200B; AJO OC &#x200B;](./images/ajooc7.png)

Selecteer **`--aepUserLdap--_citisignal_recipients`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc8.png)

Klik **creëren publiek**.

![&#x200B; AJO OC &#x200B;](./images/ajooc9.png)

Klik **toevoegen voorwaarde**.

![&#x200B; AJO OC &#x200B;](./images/ajooc10.png)

Selecteer **receiving_type** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc11.png)

Ga **`account_holder`** op het gebied **Waarde** in en klik **berekent**.

![&#x200B; AJO OC &#x200B;](./images/ajooc12.png)

U zou dan een aantal voor **gerichte profielen** moeten zien. Klik ergens in het grijze gebied zoals aangegeven.

![&#x200B; AJO OC &#x200B;](./images/ajooc13.png)

Klik **toevoegen voorwaarde**.

![&#x200B; AJO OC &#x200B;](./images/ajooc14.png)

Boor neer aan **`citisignal_accounts`**.

![&#x200B; AJO OC &#x200B;](./images/ajooc15.png)

Selecteer **`account_status`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc16.png)

Ga **`active`** op het gebied **Waarde** in. Klik vervolgens ergens in het grijze gebied zoals aangegeven.

![&#x200B; AJO OC &#x200B;](./images/ajooc17.png)

Klik **toevoegen voorwaarde**.

![&#x200B; AJO OC &#x200B;](./images/ajooc18.png)

Boor neer aan **`citisignal_mobile_subscriptions`**.

![&#x200B; AJO OC &#x200B;](./images/ajooc19.png)

Selecteer **`subscription_id`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc20.png)

Laat de schakelaar voor **samengevoegde gegevens** toe. Selecteer vervolgens het volgende:

- **samengevoegde functie**: **Telling**
- **Exploitant**: **groter dan of gelijk aan**
- **Waarde**: **1**

Klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc21.png)

Dan moet je dit zien. Klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc22.png)

### publiek 2 samenstellen

Klik op het pictogram **+** op het volgende knooppunt in het andere pad.

![&#x200B; AJO OC &#x200B;](./images/ajooc23.png)

Selecteer **Bouwstijl publiek**.

![&#x200B; AJO OC &#x200B;](./images/ajooc24.png)

Klik om de omslag voor **het richten afmeting** te openen.

![&#x200B; AJO OC &#x200B;](./images/ajooc25.png)

Selecteer **`--aepUserLdap--_mobile_subscriptions`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc26.png)

Klik **creëren publiek**.

![&#x200B; AJO OC &#x200B;](./images/ajooc27.png)

Klik **toevoegen voorwaarde**.

![&#x200B; AJO OC &#x200B;](./images/ajooc28.png)

Selecteer **subscription_status** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc29.png)

Ga **`active`** op het gebied **Waarde** in. Dan, klik **toevoegen voorwaarde**.

![&#x200B; AJO OC &#x200B;](./images/ajooc30.png)

Selecteer **`is_upgrade_eligible`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc31.png)

Plaats de **Waarde** aan **waar**

![&#x200B; AJO OC &#x200B;](./images/ajooc32.png)

Klik **berekenen** om een schatting van de profielen te zien die voor dit publiek kwalificeren. Dan, klik **bevestigen**

![&#x200B; AJO OC &#x200B;](./images/ajooc33.png)

### Splitsen

Klik **+** pictogram en selecteer dan **Splitsen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc34.png)

Verander het gebied **Etiket** in **Behandeling 90/10 vs Controle**. Klik om de objecten **Subset** te openen.

![&#x200B; AJO OC &#x200B;](./images/ajooc35.png)

Laat de schakelaar voor **toe toelaten grens** en plaats de **grootte van de Grens** aan **10 percenten**.

![&#x200B; AJO OC &#x200B;](./images/ajooc36.png)

Klik **toevoegen segment** en dan zou u het **voorwerp moeten zien van het Resultaat** dat wordt toegevoegd.

Klik **sparen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc37.png)

### Doelgroep opslaan

Klik **+** pictogram en selecteer dan **sparen publiek**.

![&#x200B; AJO OC &#x200B;](./images/ajooc38.png)

Plaats het etiket van het gebied **publiek** aan **`--aepUserLdap-- - Control Group`**. Klik **Toewijzing van het publiek** toevoegen.

![&#x200B; AJO OC &#x200B;](./images/ajooc39.png)

Boor neer aan **richtend afmeting**.

![&#x200B; AJO OC &#x200B;](./images/ajooc40.png)

Selecteer **`account_id`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc41.png)

### Verrijking: internetabonnement

Klik op het pictogram **+** .

![&#x200B; AJO OC &#x200B;](./images/ajooc42.png)

Selecteer **Verrijking**.

![&#x200B; AJO OC &#x200B;](./images/ajooc43.png)

Dan moet je dit zien. Klik **verrijkingsgegevens** toevoegen.

![&#x200B; AJO OC &#x200B;](./images/ajooc44.png)

Boor neer aan **`Targeting dimension`**.

![&#x200B; AJO OC &#x200B;](./images/ajooc44a.png)

Boor neer aan **`citisignal_accounts`**.

![&#x200B; AJO OC &#x200B;](./images/ajooc45.png)

Boor neer aan **`citisignal_internet_subscriptions`**.

![&#x200B; AJO OC &#x200B;](./images/ajooc45a.png)

Selecteer **`account_id`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc46.png)

Dan moet je dit zien. Klik **toevoegen attributen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc47.png)

Selecteer **`subscription_status`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc48.png)

Klik **toevoegen attributen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc49.png)

Selecteer **`connection_type`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc50.png)

Klik **toevoegen attributen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc51.png)

Selecteer **`service_city`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc52.png)

Klik **toevoegen attributen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc53.png)

Selecteer **`avg_dowload_usage_gb`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc54.png)

Klik **toevoegen attributen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc55.png)

Selecteer **`data_cap_gb`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc56.png)

Klik **toevoegen attributen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc57.png)

Selecteer **`advertised_speed_mbps`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc58.png)

Klik **toevoegen attributen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc59.png)

Selecteer **`monthly_recurring_charge`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc60.png)

Klik **sparen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc61.png)

De rol omhoog en verandert het gebied **Etiket** aan `Enrichment: Internet Subscription`.

![&#x200B; AJO OC &#x200B;](./images/ajooc61a.png)

### Verrijking: abonnement op mobiele apparaten

Klik **+** pictogram op de volgende knoop en selecteer **Verrijking**.

![&#x200B; AJO OC &#x200B;](./images/ajooc62.png)

Verander het gebied **Etiket** aan `Enrichment: Mobile Devices Subscription` en klik dan **verrijkingsgegevens** toevoegen.

![&#x200B; AJO OC &#x200B;](./images/ajooc63.png)

Boor neer aan **het richten afmeting**.

![&#x200B; AJO OC &#x200B;](./images/ajooc64.png)

Boor neer aan **`citisignal_mobile_subscriptions`**.

![&#x200B; AJO OC &#x200B;](./images/ajooc65.png)

Selecteer **`account_id`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc66.png)

Klik **toevoegen attributen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc67.png)

Selecteer **`subscription_id`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc68.png)

Klik **toevoegen attributen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc69.png)

Selecteer **`phone_number`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc70.png)

Klik **toevoegen attributen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc71.png)

Selecteer **`renewal_eligibility_date`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc72.png)

Klik **toevoegen attributen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc73.png)

Selecteer **`line_user_recipient_id`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc74.png)

Klik **toevoegen attributen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc75.png)

Selecteer **`is_upgrade_eligible`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc76.png)

Klik **toevoegen attributen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc77.png)

Selecteer **`current_device_id`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc78.png)

Klik **toevoegen attributen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc79.png)

Selecteer **`contract_start_date`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc80.png)

Klik **toevoegen attributen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc81.png)

Boor neer aan **`citisignal_equipment_subscriptions`**.

![&#x200B; AJO OC &#x200B;](./images/ajooc82.png)

Selecteer **`model`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc83.png)

Klik **toevoegen attributen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc86.png)

Boor neer aan **`citisignal_equipment_subscriptions`**.

![&#x200B; AJO OC &#x200B;](./images/ajooc87.png)

Selecteer **`manufacturer`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc88.png)

Klik **toevoegen attributen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc89.png)

Boor neer aan **`citisignal_equipment_subscriptions`**.

![&#x200B; AJO OC &#x200B;](./images/ajooc90.png)

Selecteer **`device_age_months`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc91.png)

Klik **toevoegen attributen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc92.png)

Boor neer aan **`citisignal_equipment_subscriptions`**.

![&#x200B; AJO OC &#x200B;](./images/ajooc93.png)

Selecteer **`is_upgrade_eligible`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc94.png)

Klik **toevoegen attributen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc95.png)

Boor neer aan **`citisignal_equipment_subscriptions`**.

![&#x200B; AJO OC &#x200B;](./images/ajooc96.png)

Selecteer **`recommended_upgrade_product_id`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc97.png)

Klik **toevoegen attributen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc98.png)

Boor neer aan **`citisignal_equipment_subscriptions`**.

![&#x200B; AJO OC &#x200B;](./images/ajooc99.png)

Selecteer **`monthly_payment`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc100.png)

Klik **toevoegen attributen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc101.png)

Boor neer aan **`citisignal_equipment_subscriptions`**.

![&#x200B; AJO OC &#x200B;](./images/ajooc102.png)

Laat de schakelaar voor **toe het Sorteren**. Klik **uitgeven** pictogram.

![&#x200B; AJO OC &#x200B;](./images/ajooc103.png)

Selecteer **`phone_number`** en klik **bevestigen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc104.png)

Dan moet je dit hebben.

![&#x200B; AJO OC &#x200B;](./images/ajooc105.png)




Dan moet je dit hebben. Klik **sparen**.

![&#x200B; AJO OC &#x200B;](./images/ajooc80a.png)














![&#x200B; AJO OC &#x200B;](./images/ajooc103.png)


## Volgende stappen

Ga terug naar [&#x200B; Adobe Journey Optimizer: Geordende Campagnes &#x200B;](./ajocampaigns.md){target="_blank"}

Ga terug naar [&#x200B; Alle modules &#x200B;](./../../../../overview.md){target="_blank"}
