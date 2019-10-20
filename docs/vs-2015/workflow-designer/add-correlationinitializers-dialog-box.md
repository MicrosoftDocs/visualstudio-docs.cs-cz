---
title: Dialogové okno Přidat Inicializátoři CorrelationInitializers | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e1402b90dfc78068546b510ce6b85379b1695f47
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672043"
---
# <a name="add-correlationinitializers-dialog-box"></a>Dialogové okno Přidat inicializátory korelace
Dialogové okno **Přidat Inicializátory korelace** se používá v [!INCLUDE[wfd1](../includes/wfd1-md.md)] ke konfiguraci vlastností **inicializátoři CorrelationInitializers** aktivit <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> a <xref:System.ServiceModel.Activities.ReceiveReply>. [!INCLUDE[crabout](../includes/crabout-md.md)] návrháři aktivit, kteří používají toto pole, najdete v tématech [posílání](../workflow-designer/send-activity-designer.md), [příjem](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)a [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

 Inicializátory korelace v kolekci zadané s tímto dialogovým oknem můžou inicializovat dotaz, kontext, kontext zpětného volání nebo korelace požadavek-odpověď mezi aktivitami zasílání zpráv.

 Následující tabulka popisuje prvky uživatelského rozhraní (UI) v dialogovém okně **Přidat Inicializátory korelace** .

|Prvek uživatelského rozhraní (UI)|Popis|
|----------------|-----------------|
|**Přidat inicializátor**|Kliknutím na pole **přidat inicializaci** přidejte do kolekce další inicializátor.|
|**Typ korelace**|Určuje typ inicializátoru korelace. Existují čtyři typy, ze kterých si můžete vybrat:<br /><br /> 1. inicializátor korelace zpětného volání pro určení <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2. inicializátor korelace kontextu pro určení <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3. inicializátor korelace požadavek-odpověď pro určení <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4. inicializátor korelace dotazu pro určení <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Postup úpravy **CorrelationType**<br /><br /> 1. karta do konkrétního řádku v ovládacím prvku **Přidat inicializátor inicializátoru**<br />2. Stisknutím kombinace kláves CTRL + TAB nastavte fokus na **CorrelationTypeComboBox**<br />3. Kliknutím na tlačítko Alt + šipka dolů zobrazíte okno se **seznamem** a upravíte ho.|
|**Dotazy XPath**|Pár klíč/hodnota, který obsahuje dotazy použité k extrakci dat korelace z příchozích a odchozích zpráv. Tento seznam je platný pouze při použití typů <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Spuštění dialogového okna Přidat Inicializátory korelace
 Dialogové okno **Přidat Inicializátory korelace** se používá v návrhářích **Odeslat**, **přijmout**, **ReceiveAndSendReply**a **SendAndReceiveReply** . Přístup k nim je podobný v každém případě a v případě, že je k tomu potřeba Návrhář pro **příjem** , se tady používá k ilustraci postupu.

 Návrhář aktivity **Receive** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu všude, kde jsou obvykle umístěny aktivity. Tím se vytvoří aktivita <xref:System.ServiceModel.Activities.Receive> s výchozím <xref:System.Activities.Activity.DisplayName%2A> příjmu. Vyberte Návrhář aktivity **Receive** a klikněte na tlačítko se třemi tečkami vedle textu (kolekce) pro vlastnost **inicializátoři CorrelationInitializers** v mřížce vlastností pro zobrazení dialogového okna **Přidat Inicializátory korelace** .

## <a name="see-also"></a>Viz také
 [Dialogové okno Inicializace korelace](../workflow-designer/initialize-correlation-dialog-box.md)