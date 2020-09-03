---
title: Návrhář aktivity Návrhář postupu provádění – odeslání
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd1eff0a52dfb258d7f7af49b03543fd741bc88c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86875953"
---
# <a name="send-activity-designer"></a>Návrhář aktivity Send

Návrhář aktivity **odeslání** slouží k vytvoření a konfiguraci <xref:System.ServiceModel.Activities.Send> aktivity.

## <a name="the-send-activity"></a>Aktivita odeslání

 <xref:System.ServiceModel.Activities.Send>Aktivita se používá k odeslání zprávy službě. <xref:System.ServiceModel.Activities.ReceiveReply>Aktivita může být svázána s <xref:System.ServiceModel.Activities.Send> aktivitou, která přijímá zprávu jako součást vzoru výměny zprávy žádosti nebo odpovědi na klientovi.

### <a name="using-the-send-activity-designer"></a>Použití návrháře aktivity pro odeslání

Přihlaste se k Návrháři aktivity **odeslání** v kategorii **zprávy** sady **nástrojů**. Návrhář aktivity **odeslání** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity. Tím se vytvoří <xref:System.ServiceModel.Activities.Send> aktivita s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> Odeslat. <xref:System.Activities.Activity.DisplayName%2A>Lze upravit v záhlaví návrháře aktivity **odeslání** nebo v poli **DisplayName** v mřížce vlastností.

Pokud chcete vytvořit <xref:System.ServiceModel.Activities.ReceiveReply> aktivitu a navazovat ji na vybranou <xref:System.ServiceModel.Activities.Send> aktivitu, klikněte pravým tlačítkem myši na Návrhář aktivity pro **odeslání** , klikněte na položku **vytvořit ReceiveReply** v kontextové nabídce a v okně návrháře **ReceiveReplyForSend** se zobrazí pod tlačítkem **Odeslat** návrháře. <xref:System.ServiceModel.Activities.ReceiveReply>Aktivita je aktivita, která přijímá zprávy jako součást vzoru výměny zprávy žádosti nebo odpovědi na klientovi. Dá se nakonfigurovat pomocí návrháře **ReceiveReplyForSend** .

Alternativně je možné pomocí návrháře šablon **SendAndReceiveReply** v kategorii **zasílání zpráv** v **sadě nástrojů** vytvořit dvojici předem nakonfigurovaných <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivit. Další informace o použití šablon **SendAndReceiveReply** a **ReceiveReplyForSend** naleznete v tématu [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

### <a name="the-send-activity-properties"></a>Vlastnosti aktivity odeslání

V následující tabulce jsou uvedeny <xref:System.ServiceModel.Activities.Send> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti se dají upravovat v mřížce vlastností nebo na Návrhář postupu provádění ploše.

| Název vlastnosti | Požaduje se | Využití |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Ne | Popisný název <xref:System.ServiceModel.Activities.Send> aktivity Výchozí hodnota je Send. I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | Ano | Název operace služby volané touto <xref:System.ServiceModel.Activities.Send> aktivitou. Tato vlastnost slouží k vytvoření výchozí hodnoty pro vlastnost **Action** , pokud vlastnost **Action** není explicitně nastavena. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | Ano | Název kontraktu služby, který služba má volat implementující. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | Ne | Určuje zprávu nebo parametr obsahu, který se má přijmout. Může to být buď <xref:System.ServiceModel.Activities.ReceiveMessageContent> aktivita, nebo <xref:System.ServiceModel.Activities.ReceiveParametersContent> aktivita. Upravte tuto vlastnost tak, že vyberete tlačítko se třemi tečkami vedle pole **obsah** v mřížce vlastností nebo kliknete na tlačítko **definovat...** vedle popisku **obsahu** na ploše návrháře aktivity **příjmu** . V obou zobrazeních se zobrazí dialogové okno **definice obsahu** . Další informace o tom, jak používat toto pole, najdete v tématu věnovaném [definici obsahu v dialogu](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | Ne | Určuje, že se <xref:System.ServiceModel.Activities.CorrelationHandle> použije ke směrování zprávy do příslušné instance pracovního postupu.<br /><br /> Kliknutím na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> vlastnosti v mřížce vlastnosti otevřete dialogové okno **Editor výrazů** . Další informace o použití tohoto dialogového okna naleznete v tématu [Postupy: použití editoru výrazů](../workflow-designer/how-to-use-the-expression-editor.md) . |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | Ne | Určuje kolekci <xref:System.ServiceModel.Activities.CorrelationInitializer> objektů, které inicializují více <xref:System.ServiceModel.Activities.CorrelationHandle> objektů, které konfigurují tuto <xref:System.ServiceModel.Activities.Send> aktivitu v rámci pracovního postupu. Kliknutím na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> vlastnosti v mřížce vlastnosti otevřete dialogové okno **Přidat Inicializátory korelace** . Další informace o použití tohoto pole najdete v tématu věnovaném [dialogovému oknu Přidat inicializátoři CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | Ne | Kolekce známých typů pro operaci služby, kterou má tato <xref:System.ServiceModel.Activities.Send> aktivita volat. Tato vlastnost by měla být použita ve spojení s <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> vlastností nastavenou na <xref:System.Runtime.Serialization.DataContractSerializer> . Pokud <xref:System.Xml.Serialization.XmlSerializer> je použita, bude ignorována.<br /><br /> Kliknutím na tlačítko se třemi tečkami vedle pole **KnownTypes** v mřížce vlastností zobrazíte dialogové okno **Editor kolekcí typů** , ve kterém můžete přidat relevantní typy.<br /><br /> Kliknutím na tlačítko se třemi tečkami vedle pole **KnownTypes** v mřížce vlastností zobrazíte dialogové okno **Editor kolekcí typů** , ve kterém můžete přidat relevantní typy. Další informace o použití tohoto pole naleznete v tématu [dialogové okno Editor kolekcí typů](../workflow-designer/type-collection-editor-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | Ano | Určuje <xref:System.Net.Security.ProtectionLevel> pro zprávu.<br /><br /> 1.  <xref:System.Net.Security.ProtectionLevel> znamená pouze ověřování.<br />2.  <xref:System.Net.Security.ProtectionLevel> označuje podpisová data, která vám pomůžou zajistit integritu přenášených dat.<br />3.  <xref:System.Net.Security.ProtectionLevel> znamená šifrování a podepsání dat, které vám pomůžou zajistit důvěrnost a integritu přenášených dat. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | Ano | Serializátor, který se má použít pro operaci služby, která má být volána <xref:System.ServiceModel.Activities.Send> aktivitou. Výchozí hodnota je <xref:System.Runtime.Serialization.DataContractSerializer> , která serializace a deserializace instance typu do datového proudu XML nebo dokumentu pomocí dodaného kontraktu dat. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | Ne | Určuje hlavičku akce zprávy. Pokud není nastavena explicitně, jeho hodnota je výchozím nastavením: `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` . Je-li tento parametr zadán v <xref:System.ServiceModel.Activities.Send> aktivitě, <xref:System.ServiceModel.Activities.Receive> musí mít aktivita, která přijímá zprávu, stejnou hodnotu pro správné doručení zprávy. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | <xref:System.Security.Principal.TokenImpersonationLevel>Povolené pro přijímač zprávy. Definuje úrovně zosobnění zabezpečení, které určují míru, na kterou proces serveru může působit jménem procesu klienta.<xref:System.Security.Principal.TokenImpersonationLevel> indikuje, že úroveň zosobnění není přiřazena. <xref:System.Security.Principal.TokenImpersonationLevel> indikuje, že proces serveru nemůže získat identifikační informace o klientovi a nemůže zosobnit klienta. <xref:System.Security.Principal.TokenImpersonationLevel> indikuje, že proces serveru může získat informace o klientovi, například identifikátory zabezpečení a oprávnění, ale že nemůže zosobnit klienta. To je užitečné pro servery, které exportují své vlastní objekty, například databázové produkty, které exportují tabulky a zobrazení. Pomocí načtených informací o zabezpečení klienta může server provádět rozhodnutí o ověření přístupu, aniž by bylo možné používat jiné služby, které používají kontext zabezpečení klienta. <xref:System.Security.Principal.TokenImpersonationLevel> indikuje, že proces serveru může zosobnit kontext zabezpečení klienta v místním systému. Server nemůže zosobnit klienta ve vzdálených systémech. <xref:System.Security.Principal.TokenImpersonationLevel> indikuje, že proces serveru může zosobnit kontext zabezpečení klienta ve vzdálených systémech. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | <xref:System.ServiceModel.Endpoint> <xref:System.ServiceModel.Activities.Send> Aktivity, na kterou aktivita odesílá zprávu. Pokud je tato vlastnost nastavena na <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> **hodnotu null**. |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | Do <xref:System.ServiceModel.EndpointAddress> kterého se zpráva posílá |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | Název konfigurace koncového bodu. Tato vlastnost se nastavuje při konfiguraci koncového bodu v konfiguračním souboru. Tato vlastnost by měla být nastavena na název zadaný v **\<endpoint>** prvku v konfiguračním souboru. Pokud je tato vlastnost nastavena, <xref:System.ServiceModel.Activities.Send.Endpoint%2A> vlastnost by měla mít **hodnotu null**. |

## <a name="see-also"></a>Viz také

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Přijmout](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)