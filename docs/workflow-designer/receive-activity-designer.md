---
title: Návrhář postupu provádění – Návrhář aktivity Receive
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eb48c19befc3cf2c155248cfc33c01eedd16ce26
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950092"
---
# <a name="receive-activity-designer"></a>Návrhář aktivity Receive

**Receive** Návrhář aktivity se používá k vytvoření a konfigurace <xref:System.ServiceModel.Activities.Receive> aktivity. A <xref:System.ServiceModel.Activities.Receive> aktivitu, která bude přijímat zprávy, která může být buď vestavěný typ, jako je aktivita <xref:System.ServiceModel.Channels.Message>, <xref:System.IO.Stream> nebo <xref:System.Xml.Linq.XElement>, nebo kontraktu dat definované aplikací, kontraktu zprávy nebo třída XML, který lze serializovat.

## <a name="the-receive-activity"></a>Aktivita příjmu

<xref:System.ServiceModel.Activities.Receive> Aktivity může přijímat jednu položku nebo více položek v závislosti na typu přijmout obsah použít. A <xref:System.ServiceModel.Activities.SendReply> aktivity může být vázaný na <xref:System.ServiceModel.Activities.Receive> aktivitu, která obdrží zprávu jako součást vzoru výměny zpráv žádost odpověď na službu.

### <a name="using-the-receive-activity-designer"></a>Použití Návrhář aktivity Receive

Přístup **Receive** návrháře aktivit v **zasílání zpráv** kategorii **nástrojů**. **Receive** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřadit na povrch návrháře postupu provádění bez ohledu na to aktivity jsou obvykle umístěny. Tím se vytvoří <xref:System.ServiceModel.Activities.Receive> aktivity s výchozím <xref:System.Activities.Activity.DisplayName%2A> Receive. <xref:System.Activities.Activity.DisplayName%2A> Můžete upravovat v záhlaví **Receive** Návrhář aktivity nebo v **DisplayName** pole mřížku vlastností.

Vytvoření <xref:System.ServiceModel.Activities.SendReply> aktivity a jeho vazbu na vybrané <xref:System.ServiceModel.Activities.Receive> aktivity, klikněte pravým tlačítkem na **Receive** návrháře, klikněte na aktivitu **vytvořit odeslání odpovědi SendReply** položku v kontextové nabídce a **SendReplyToReceive** návrháře se zobrazí pod **Receive** návrháře. <xref:System.ServiceModel.Activities.SendReply> Aktivita je aktivitou, která odesílá zprávy s odpovědí jako součást vzoru výměny zpráv žádost odpověď na službu. To může mít nakonfigurovanou **SendReplyToReceive** návrháře.

Alternativně **ReceiveAndSendReply** návrhář šablony v **zasílání zpráv** kategorii **nástrojů** slouží k vytvoření páru předem nakonfigurované <xref:System.ServiceModel.Activities.Receive>a <xref:System.ServiceModel.Activities.SendReply> aktivity. Další informace o použití **ReceiveAndSendReply** a **SendReplyToReceive** šablony, najdete v článku [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) tématu.

### <a name="the-receive-activity-properties"></a>Zobrazí vlastnosti aktivity

Následující tabulka ukazuje <xref:System.ServiceModel.Activities.Receive> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti můžete upravit v mřížce vlastností nebo na povrchu návrháře postupu provádění. Je pouze požadovaná vlastnost <xref:System.ServiceModel.Activities.Receive.OperationName%2A> vlastnost.


| Název vlastnosti | Požadováno | Použití |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Určuje popisný název <xref:System.ServiceModel.Activities.Receive> aktivity. Výchozí hodnota je Receive.<br /><br /> Ačkoli použití jinou než výchozí hodnotu pro popisný <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutné, je vhodné použít taková hodnota. |
| <xref:System.ServiceModel.Activities.Receive.OperationName%2A> | Hodnota TRUE | Určuje název operace služby implementovaná tímto objektem <xref:System.ServiceModel.Activities.Receive> aktivity. Tato vlastnost se používá k sestavení kompletních výchozí hodnota **akce** vlastnost Pokud **akce** není explicitně nastavena vlastnost. |
| <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> | False | Určuje název kontraktu služby. Tato vlastnost slouží k operacím služby skupiny do jednotlivých služeb smluv. Všechny <xref:System.ServiceModel.Activities.Receive> aktivity, které mají stejné <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> jsou seskupené do stejné kontrakt služby (typ portu WSDL). Výchozí hodnota je plně kvalifikovaný název CLR aktivity nejvyšší úrovně (kořenový). |
| <xref:System.ServiceModel.Activities.Receive.Content%2A> | False | Určuje zprávu nebo parametr obsah, který se zobrazí. Může se jednat buď <xref:System.ServiceModel.Activities.ReceiveMessageContent> aktivity nebo <xref:System.ServiceModel.Activities.ReceiveParametersContent> aktivity. Tato vlastnost upravit tak, že vyberete tlačítko se třemi tečkami vedle **obsahu** v mřížce vlastností nebo kliknutím **definovat...**  tlačítko vedle **obsahu** popisek **Receive** povrch návrháře aktivit. Obě zobrazení **definici obsahu** dialogového okna. Další informace o tom, jak pomocí tohoto políčka, najdete v článku [obsahu dialogové okno Definice](../workflow-designer/content-definition-dialog-box.md) tématu. |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> | False | Určuje korelace mezi <xref:System.ServiceModel.Activities.Receive> aktivit v servisní operace pracovního postupu s <xref:System.ServiceModel.MessageQuerySet> objektu. Klikněte na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> vlastnost v mřížce vlastnosti otevřít **definice vlastnosti CorrelatesOn** dialogové okno. Další informace o použití tohoto dialogového okna, najdete v článku [obsahu dialogové okno Definice](../workflow-designer/content-definition-dialog-box.md) tématu. |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> | False | Určuje, <xref:System.ServiceModel.Activities.CorrelationHandle> využívá ke směrování do instance pracovního postupu odpovídající zprávu.<br /><br /> Klikněte na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> vlastnost v mřížce vlastnosti otevřít **Editor výrazů** dialogové okno. Další informace o použití tohoto dialogového okna, najdete v článku [postupy: použití editoru výrazů](../workflow-designer/how-to-use-the-expression-editor.md) tématu. |
| <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> | False | Určuje kolekci <xref:System.ServiceModel.Activities.CorrelationInitializer> objekty, které inicializovat více <xref:System.ServiceModel.Activities.CorrelationHandle> objekty, které to nakonfigurovat <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu. Klikněte na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> vlastnost v mřížce vlastnosti otevřít **přidat inicializátory korelace** dialogové okno. Další informace o použití tohoto pole, najdete v článku [dialogové okno Přidat inicializátory korelace](../workflow-designer/add-correlationinitializers-dialog-box.md) tématu. |
| <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> | False | Určuje hodnotu, která určuje, zda zpracovat zprávu, pokud zpráva neodpovídá existující instance pracovního postupu je vytvořena nová instance pracovního postupu. Pokud je hodnota nastavena na **true**, zpracovat zprávu, pokud zpráva není korelují s existující instancí pracovního postupu je vytvořena nová instance pracovního postupu. |
| <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> | False | Určuje kolekci známých typů pro operaci služby implementovaná tímto objektem <xref:System.ServiceModel.Activities.Receive> aktivity. Tuto vlastnost byste měli použít ve spojení s <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> nastavenou na <xref:System.Runtime.Serialization.DataContractSerializer>. Se ignoruje, pokud <xref:System.Xml.Serialization.XmlSerializer> se používá.<br /><br /> Vyberte tlačítko se třemi tečkami vedle **KnownTypes** v mřížce vlastností zobrazíte **Editor typu kolekce** dialogovému oknu, pomocí kterého můžete přidat odpovídající typy. Další informace o použití tohoto pole, najdete v článku [dialogové okno Editor typu kolekce](../workflow-designer/type-collection-editor-dialog-box.md) tématu. |
| <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> | False | Určuje, <xref:System.Net.Security.ProtectionLevel> zprávy.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> znamená, že jenom ověřování.<br />2. <xref:System.Net.Security.ProtectionLevel> znamená, že podepsat data k zajištění integrity dat přenášených.<br />3. <xref:System.Net.Security.ProtectionLevel> znamená, že šifrování a podepisování dat k zajištění důvěrnost a integrita dat přenášených. |
| <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> | False | Určuje typ serializátoru pro operaci služby, které jsou implementované <xref:System.ServiceModel.Activities.Receive> aktivity. Výchozí hodnota je <xref:System.Runtime.Serialization.DataContractSerializer>, který serializuje a deserializuje instance typu do datový proud XML nebo dokument, který používá zadaný datový kontrakt. <xref:System.Xml.Serialization.XmlSerializer> Lze také pokud je potřeba použít větší kontrolu nad XML. |
| <xref:System.ServiceModel.Activities.Receive.Action%2A> | False | Určuje akci záhlaví zprávy. Pokud není explicitně nastavena, její výchozí hodnota je: https://tempuri.org/{service obor názvů kontraktu} / {název kontraktu služby} / {název operace}. |

## <a name="see-also"></a>Viz také:

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)