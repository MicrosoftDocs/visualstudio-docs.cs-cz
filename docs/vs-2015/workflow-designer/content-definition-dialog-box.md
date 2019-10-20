---
title: Dialogové okno Definice obsahu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d989f5a0c57e381041e8fe9c200aae1a76316ad8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656949"
---
# <a name="content-definition-dialog-box"></a>Dialogové okno Definice obsahu
Dialogové okno **definice obsahu** se používá v [!INCLUDE[wfd1](../includes/wfd1-md.md)] ke konfiguraci vlastností **obsahu** aktivit <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> a <xref:System.ServiceModel.Activities.ReceiveReply>. [!INCLUDE[crabout](../includes/crabout-md.md)] návrháři aktivit, kteří používají toto pole, najdete v tématech [posílání](../workflow-designer/send-activity-designer.md), [příjem](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)a [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

 Následující tabulka popisuje prvky uživatelského rozhraní (UI) v dialogovém okně **inicializace korelace** .

|Prvek uživatelského rozhraní (UI)|Popis|
|----------------|-----------------|
|**Zpráva**|Určuje obsah zprávy obsahující textové pole výrazu **data zprávy** a typ pomocí rozevíracího seznamu **typ zprávy** . Ve výchozím nastavení **definice obsahu** používá <xref:System.ServiceModel.Activities.ReceiveMessageContent>, což očekává <xref:System.ServiceModel.Channels.Message> nebo typ kontraktu zprávy v rámci definice služby pracovního postupu.|
|**Parametry**|Kliknutím na přepínač **parametry** můžete použít <xref:System.ServiceModel.Activities.ReceiveParametersContent>, což očekává kontrakt dat. Datovou mřížku použijte k nastavení Obecné kolekce <xref:System.Activities.OutArgument> párů klíč/hodnota, jejichž hodnoty jsou přiřazeny parametrům proměnné v aktuálním pracovním postupu.|

 Dialogové okno **definice obsahu** se používá v návrhářích **Odeslat**, **přijmout**, **ReceiveAndSendReply**a **SendAndReceiveReply** . Přístup k nim je podobný v každém případě a k ilustraci tohoto postupu slouží případ přijetí.

 Návrhář aktivity **Receive** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu všude, kde jsou obvykle umístěny aktivity. Tím se vytvoří aktivita <xref:System.ServiceModel.Activities.Receive> s výchozím <xref:System.Activities.Activity.DisplayName%2A> příjmu. Vyberte návrháře aktivity **Receive** a klikněte na tlačítko se třemi tečkami vedle textu (obsah) vlastnosti **Content** v mřížce vlastností dialogového okna **definice obsahu** , které se zobrazí.

 Obsah lze zadat v části **zprávy** pro aktivitu <xref:System.ServiceModel.Activities.ReceiveMessageContent> nebo v části **parametru** pro aktivitu <xref:System.ServiceModel.Activities.ReceiveParametersContent>.

## <a name="see-also"></a>Viz také
 [Nápověda k uživatelskému rozhraní návrháře postupu provádění](../workflow-designer/workflow-designer-ui-help.md)