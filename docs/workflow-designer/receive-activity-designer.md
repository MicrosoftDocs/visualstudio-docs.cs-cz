---
title: Návrhář aktivity Receive Návrhář postupu provádění
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 55f49a32036fcfd5e9f75f3d8dd61499c4af0b2e
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86875719"
---
# <a name="receive-activity-designer"></a>Návrhář aktivity Receive

Návrhář aktivity **Receive** slouží k vytvoření a konfiguraci <xref:System.ServiceModel.Activities.Receive> aktivity. <xref:System.ServiceModel.Activities.Receive>Aktivita je aktivita, která přijímá zprávu, která může být buď vestavěný typ <xref:System.ServiceModel.Channels.Message> , jako je například <xref:System.IO.Stream> nebo <xref:System.Xml.Linq.XElement> , nebo kontrakt dat definovaný aplikací, kontrakt zprávy nebo třída XML, které mohou být serializovány.

## <a name="the-receive-activity"></a>Aktivita Receive

<xref:System.ServiceModel.Activities.Receive>Aktivita může obdržet jednu položku nebo více položek v závislosti na typu použitého obsahu pro příjem. <xref:System.ServiceModel.Activities.SendReply>Aktivita může být svázána s <xref:System.ServiceModel.Activities.Receive> aktivitou, která přijímá zprávu jako součást vzoru výměny zprávy žádosti nebo odpovědi ve službě.

### <a name="using-the-receive-activity-designer"></a>Použití návrháře aktivity Receive

Přístup k Návrháři aktivity **Receive** v kategorii **zprávy** sady **nástrojů**. Návrhář aktivity **Receive** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity. Tím se vytvoří <xref:System.ServiceModel.Activities.Receive> aktivita s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> Receive. <xref:System.Activities.Activity.DisplayName%2A>Lze upravit v záhlaví návrháře aktivity **Receive** nebo v poli **DisplayName** v mřížce vlastností.

Chcete-li vytvořit <xref:System.ServiceModel.Activities.SendReply> aktivitu a vytvořit její propojení s vybranou <xref:System.ServiceModel.Activities.Receive> aktivitou, klikněte pravým tlačítkem myši na Návrhář aktivity **Receive** , klikněte na položku **vytvořit aktivitu SendReply** v místní nabídce a v Návrháři **SendReplyToReceive** se zobrazí pod návrhářem **příjmu** . <xref:System.ServiceModel.Activities.SendReply>Aktivita je aktivita, která posílá zprávu odpovědi jako součást vzoru výměny zprávy požadavku nebo odpovědi na službě. Dá se nakonfigurovat pomocí návrháře **SendReplyToReceive** .

Alternativně je možné pomocí návrháře šablon **ReceiveAndSendReply** v kategorii **zasílání zpráv** v **sadě nástrojů** vytvořit dvojici předem nakonfigurovaných <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivit. Další informace o použití šablony **ReceiveAndSendReply** a **SendReplyToReceive** naleznete v tématu [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) .

### <a name="the-receive-activity-properties"></a>Vlastnosti aktivity Receive

V následující tabulce jsou uvedeny <xref:System.ServiceModel.Activities.Receive> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v mřížce vlastností nebo na Návrhář postupu provádění ploše. Jediná požadovaná vlastnost je <xref:System.ServiceModel.Activities.Receive.OperationName%2A> vlastnost.

| Název vlastnosti | Požaduje se | Využití |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Nepravda | Určuje popisný název <xref:System.ServiceModel.Activities.Receive> aktivity. Výchozí hodnota je Receive.<br /><br /> I když použití jiné než výchozí hodnoty pro popis není <xref:System.Activities.Activity.DisplayName%2A> bezpodmínečně nutné, jedná se o osvědčený postup pro použití takové hodnoty. |
| <xref:System.ServiceModel.Activities.Receive.OperationName%2A> | Ano | Určuje název operace služby implementované touto <xref:System.ServiceModel.Activities.Receive> aktivitou. Tato vlastnost slouží k vytvoření výchozí hodnoty pro vlastnost **Action** , pokud vlastnost **Action** není explicitně nastavena. |
| <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> | Nepravda | Určuje název kontraktu služby. Tato vlastnost slouží k seskupení operací služby do jednotlivých kontraktů služby. Všechny <xref:System.ServiceModel.Activities.Receive> aktivity, které jsou stejné, <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> se seskupují do stejné kontraktu služby (typ portu WSDL). Výchozí hodnota je plně kvalifikovaný název CLR aktivity nejvyšší úrovně (kořene). |
| <xref:System.ServiceModel.Activities.Receive.Content%2A> | Nepravda | Určuje zprávu nebo parametr obsahu, který se má přijmout. Může to být buď <xref:System.ServiceModel.Activities.ReceiveMessageContent> aktivita, nebo <xref:System.ServiceModel.Activities.ReceiveParametersContent> aktivita. Upravte tuto vlastnost tak, že vyberete tlačítko se třemi tečkami vedle pole **obsah** v mřížce vlastností nebo kliknete na tlačítko **definovat...** vedle popisku **obsahu** na ploše návrháře aktivity **příjmu** . V obou zobrazeních se zobrazí dialogové okno **definice obsahu** . Další informace o tom, jak používat toto pole, najdete v tématu věnovaném [definici obsahu v dialogu](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> | Nepravda | Určuje korelace mezi <xref:System.ServiceModel.Activities.Receive> aktivitami v rámci operací služby pracovního postupu s <xref:System.ServiceModel.MessageQuerySet> objektem. Kliknutím na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> vlastnosti v mřížce vlastnosti otevřete dialogové okno **definice vlastnosti CorrelatesOn** . Další informace o použití tohoto dialogového okna najdete v části [definice obsahu](../workflow-designer/content-definition-dialog-box.md) v tématu. |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> | Nepravda | Určuje, že se <xref:System.ServiceModel.Activities.CorrelationHandle> použije ke směrování zprávy do příslušné instance pracovního postupu.<br /><br /> Kliknutím na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> vlastnosti v mřížce vlastnosti otevřete dialogové okno **Editor výrazů** . Další informace o použití tohoto dialogového okna naleznete v tématu [Postupy: použití editoru výrazů](../workflow-designer/how-to-use-the-expression-editor.md) . |
| <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> | Nepravda | Určuje kolekci <xref:System.ServiceModel.Activities.CorrelationInitializer> objektů, které inicializují více <xref:System.ServiceModel.Activities.CorrelationHandle> objektů, které konfigurují tuto <xref:System.ServiceModel.Activities.Receive> aktivitu v rámci pracovního postupu. Kliknutím na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> vlastnosti v mřížce vlastnosti otevřete dialogové okno **Přidat Inicializátory korelace** . Další informace o použití tohoto pole najdete v tématu věnovaném [dialogovému oknu Přidat inicializátoři CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> | Nepravda | Určuje hodnotu, která určuje, zda je vytvořena nová instance pracovního postupu pro zpracování zprávy, pokud zpráva nekoreluje s existující instancí pracovního postupu. Pokud je hodnota nastavená na **true**, vytvoří se nová instance pracovního postupu pro zpracování zprávy, když se zpráva nekoreluje s existující instancí pracovního postupu. |
| <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> | Nepravda | Určuje kolekci známých typů pro operaci služby implementovanou touto <xref:System.ServiceModel.Activities.Receive> aktivitou. Tato vlastnost by měla být použita ve spojení s <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> vlastností nastavenou na <xref:System.Runtime.Serialization.DataContractSerializer> . Pokud <xref:System.Xml.Serialization.XmlSerializer> je použita, bude ignorována.<br /><br /> Kliknutím na tlačítko se třemi tečkami vedle pole **KnownTypes** v mřížce vlastností zobrazíte dialogové okno **Editor kolekcí typů** , ve kterém můžete přidat relevantní typy. Další informace o použití tohoto pole naleznete v tématu [dialogové okno Editor kolekcí typů](../workflow-designer/type-collection-editor-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> | Nepravda | Určuje <xref:System.Net.Security.ProtectionLevel> pro zprávu.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> znamená pouze ověřování.<br />2. <xref:System.Net.Security.ProtectionLevel> označuje podpisová data, která vám pomůžou zajistit integritu přenášených dat.<br />3. <xref:System.Net.Security.ProtectionLevel> znamená šifrování a podepsání dat, které vám pomůžou zajistit důvěrnost a integritu přenášených dat. |
| <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> | Nepravda | Určuje typ serializátoru, který se má použít pro operaci služby implementovanou <xref:System.ServiceModel.Activities.Receive> aktivitou. Výchozí hodnota je <xref:System.Runtime.Serialization.DataContractSerializer> , která serializace a deserializace instance typu do datového proudu XML nebo dokumentu, který používá zadaný kontrakt dat. <xref:System.Xml.Serialization.XmlSerializer>Lze také použít, pokud je v kódu XML vyžadován větší ovládací prvek. |
| <xref:System.ServiceModel.Activities.Receive.Action%2A> | Nepravda | Určuje hlavičku akce zprávy. Pokud není nastavena explicitně, jeho hodnota je výchozím nastavením: `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` . |

## <a name="see-also"></a>Viz také

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Odeslat](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)
