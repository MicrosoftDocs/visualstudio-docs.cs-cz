---
title: Návrhář postupu provádění – dialogové okno Definice obsahu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4925d6f6321cd039daca469844ebac6627b08f81
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189788"
---
# <a name="content-definition-dialog-box"></a>Dialogové okno Definice obsahu

Dialogové okno **definice obsahu** se používá v Návrhář postupu provádění ke konfiguraci vlastností **obsahu** aktivit <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> a <xref:System.ServiceModel.Activities.ReceiveReply>. Další informace o návrhářech aktivity, které používají toto pole, najdete v tématech [posílání](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)a [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

Následující tabulka popisuje prvky uživatelského rozhraní (UI) v dialogovém okně **inicializace korelace** :

|Prvek uživatelského rozhraní (UI)|Popis|
|-|-----------------|
|**Zpráva**|Určuje obsah zprávy obsahující textové pole výrazu **data zprávy** a typ pomocí rozevíracího seznamu **typ zprávy** . Ve výchozím nastavení **definice obsahu** používá <xref:System.ServiceModel.Activities.ReceiveMessageContent>, což očekává <xref:System.ServiceModel.Channels.Message> nebo typ kontraktu zprávy v rámci definice služby pracovního postupu.|
|**Parametry**|Kliknutím na přepínač **parametry** můžete použít <xref:System.ServiceModel.Activities.ReceiveParametersContent>, což očekává kontrakt dat. Datovou mřížku použijte k nastavení Obecné kolekce <xref:System.Activities.OutArgument> párů klíč/hodnota, jejichž hodnoty jsou přiřazeny parametrům proměnné v aktuálním pracovním postupu.|

Dialogové okno **definice obsahu** se používá v návrhářích **Odeslat**, **přijmout**, **ReceiveAndSendReply**a **SendAndReceiveReply** . Přístup k nim je podobný v každém případě a k ilustraci tohoto postupu slouží případ přijetí.

Návrhář aktivity **Receive** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity. Tím se vytvoří aktivita <xref:System.ServiceModel.Activities.Receive> s výchozím <xref:System.Activities.Activity.DisplayName%2A> příjmu. Vyberte návrháře aktivity **Receive** a klikněte na tlačítko se třemi tečkami vedle textu (obsah) vlastnosti **Content** v mřížce vlastností dialogového okna **definice obsahu** , které se zobrazí.

Obsah lze zadat v části **zprávy** pro aktivitu <xref:System.ServiceModel.Activities.ReceiveMessageContent> nebo v části **parametru** pro aktivitu <xref:System.ServiceModel.Activities.ReceiveParametersContent>.

## <a name="see-also"></a>Viz také:

- [Nápověda k uživatelskému rozhraní návrháře postupu provádění](browse-and-select-a-dotnet-type-dialog-box.md)