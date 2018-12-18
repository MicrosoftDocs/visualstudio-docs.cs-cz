---
title: Návrhář postupu provádění – dialogové okno Definice obsahu
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f8307db1858ba50d209e456dc17ddd36dcaab722
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49870770"
---
# <a name="content-definition-dialog-box"></a>Dialogové okno Definice obsahu

**Definici obsahu** dialogové okno se používá v Návrháři pracovních postupů ke konfiguraci **obsahu** vlastnosti <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity. Další informace o návrháři aktivit, které používají toto políčko, najdete v článku [odeslat](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), a [SendAndReceiveReply ](../workflow-designer/sendandreceivereply-template-designer.md) témata.

Následující tabulka popisuje prvky uživatelského rozhraní (UI) **inicializace korelace** dialogové okno:

|Prvek uživatelského rozhraní (UI)|Popis|
|-|-----------------|
|**Zpráva**|Určuje zprávu, která obsahu s **zprávy data** výraz textové pole a typu pomocí **typ zprávy** rozevíracího seznamu. Ve výchozím nastavení **definici obsahu** používá <xref:System.ServiceModel.Activities.ReceiveMessageContent>, která očekává <xref:System.ServiceModel.Channels.Message> nebo zprávy smlouvy typu v definici služby pracovního postupu.|
|**Parametry**|Klikněte na tlačítko **parametry** přepínač použít <xref:System.ServiceModel.Activities.ReceiveParametersContent>, který očekává, že data smlouvy. Můžete nastavit obecné kolekce datové mřížce <xref:System.Activities.OutArgument> jehož hodnoty jsou přiřazeny k parametry proměnné jsou v aktuálním pracovním postupu dvojic klíč/hodnota.|

**Definici obsahu** dialogové okno používá **odeslat**, **Receive**, **ReceiveAndSendReply**, a  **SendAndReceiveReply** návrháře. Přístup k nim je podobné jako v každém případě a případ Receive se zde používá k znázorňují postup.

**Receive** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřadit na povrch návrháře postupu provádění bez ohledu na to aktivity jsou obvykle umístěny. Tím se vytvoří <xref:System.ServiceModel.Activities.Receive> aktivity s výchozím <xref:System.Activities.Activity.DisplayName%2A> Receive. Vyberte **Receive** návrháře aktivit a klikněte na tlačítko se třemi tečkami vedle textu u (obsah) **obsahu** v mřížce vlastností pro vlastnost **definici obsahu**dialogového okna.

Obsah se dá nastavit v rámci **zpráva** v části <xref:System.ServiceModel.Activities.ReceiveMessageContent> aktivity nebo v rámci **parametr** v části <xref:System.ServiceModel.Activities.ReceiveParametersContent> aktivity.

## <a name="see-also"></a>Viz také:

- [Nápověda k uživatelskému rozhraní návrháře postupu provádění](../workflow-designer/workflow-designer-ui-help.md)