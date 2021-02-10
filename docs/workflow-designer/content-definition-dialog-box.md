---
title: Návrhář postupu provádění – dialogové okno Definice obsahu
description: Naučte se, jak můžete použít dialogové okno Definice obsahu ke konfiguraci vlastností obsahu aktivit Send, Receive, SendReply a ReceiveReply.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a25d049b17381c49bfa1b4a5544972b6dc5fe499
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955642"
---
# <a name="content-definition-dialog-box"></a>Dialogové okno Definice obsahu

Dialogové okno **definice obsahu** se používá v Návrhář postupu provádění ke konfiguraci vlastností **obsahu** pro <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> aktivity,, <xref:System.ServiceModel.Activities.SendReply> a <xref:System.ServiceModel.Activities.ReceiveReply> . Další informace o návrhářech aktivity, které používají toto pole, najdete v tématech [posílání](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)a [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

Následující tabulka popisuje prvky uživatelského rozhraní (UI) v dialogovém okně **inicializace korelace** :

|Prvek uživatelského rozhraní (UI)|Description|
|-|-----------------|
|**Zpráva**|Určuje obsah zprávy obsahující textové pole výrazu **data zprávy** a typ pomocí rozevíracího seznamu **typ zprávy** . Ve výchozím nastavení **definice obsahu** používá <xref:System.ServiceModel.Activities.ReceiveMessageContent> , který v <xref:System.ServiceModel.Channels.Message> definici služby pracovního postupu očekává nebo typ kontraktu zprávy.|
|**Parametry**|Klikněte na přepínač **parametry** <xref:System.ServiceModel.Activities.ReceiveParametersContent> , který chcete použít, což očekává kontrakt dat. Datovou mřížku použijte k nastavení Obecné kolekce <xref:System.Activities.OutArgument> párů klíč/hodnota, jejichž hodnoty jsou přiřazeny parametrům proměnné v aktuálním pracovním postupu.|

Dialogové okno **definice obsahu** se používá v návrhářích **Odeslat**, **přijmout**, **ReceiveAndSendReply** a **SendAndReceiveReply** . Přístup k nim je podobný v každém případě a k ilustraci tohoto postupu slouží případ přijetí.

Návrhář aktivity **Receive** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity. Tím se vytvoří <xref:System.ServiceModel.Activities.Receive> aktivita s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> Receive. Vyberte návrháře aktivity **Receive** a klikněte na tlačítko se třemi tečkami vedle textu (obsah) vlastnosti **Content** v mřížce vlastností dialogového okna **definice obsahu** , které se zobrazí.

Obsah lze zadat v části **zprávy** pro <xref:System.ServiceModel.Activities.ReceiveMessageContent> aktivitu nebo v části **parametru** pro <xref:System.ServiceModel.Activities.ReceiveParametersContent> aktivitu.

## <a name="see-also"></a>Viz také

- [Nápověda k uživatelskému rozhraní návrháře postupu provádění](browse-and-select-a-dotnet-type-dialog-box.md)