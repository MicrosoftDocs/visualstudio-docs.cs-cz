---
title: Návrhář postupu provádění – Návrhář aktivity Send
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7cbbcc01001d663e927431b99915bf69d9a223ce
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836421"
---
# <a name="send-activity-designer"></a>Návrhář aktivity Send

**Odeslat** Návrhář aktivity se používá k vytvoření a konfigurace <xref:System.ServiceModel.Activities.Send> aktivity.

## <a name="the-send-activity"></a>Aktivita Send

 A <xref:System.ServiceModel.Activities.Send> aktivita se používá k odeslání zprávy do služby. A <xref:System.ServiceModel.Activities.ReceiveReply> aktivity může být vázaný na <xref:System.ServiceModel.Activities.Send> aktivitu, která obdrží zprávu jako součást vzoru výměny zpráv žádost odpověď na straně klienta.

### <a name="using-the-send-activity-designer"></a>Pomocí návrháře aktivity Send

Přístup **odeslat** návrháře aktivit v **zasílání zpráv** kategorii **nástrojů**. **Odeslat** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřadit na povrch návrháře postupu provádění bez ohledu na to aktivity jsou obvykle umístěny. Tím se vytvoří <xref:System.ServiceModel.Activities.Send> aktivity s výchozím <xref:System.Activities.Activity.DisplayName%2A> odeslání. <xref:System.Activities.Activity.DisplayName%2A> Můžete upravovat v záhlaví **odeslat** Návrhář aktivity nebo v **DisplayName** pole mřížku vlastností.

Vytvoření <xref:System.ServiceModel.Activities.ReceiveReply> aktivity a jeho vazbu na vybrané <xref:System.ServiceModel.Activities.Send> aktivity, klikněte pravým tlačítkem na **odeslat** návrháře, klikněte na aktivitu **vytvořit ReceiveReply** položku v kontextové nabídce a **ReceiveReplyForSend** návrháře se zobrazí pod **odeslat** návrháře. <xref:System.ServiceModel.Activities.ReceiveReply> Aktivita je aktivitou, která obdrží zprávu jako součást vzoru výměny zpráv žádost odpověď na straně klienta. To může mít nakonfigurovanou **ReceiveReplyForSend** návrháře.

Alternativně **SendAndReceiveReply** návrhář šablony v **zasílání zpráv** kategorii **nástrojů** slouží k vytvoření páru předem nakonfigurované <xref:System.ServiceModel.Activities.Send>a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity. Další informace o použití **SendAndReceiveReply** a **ReceiveReplyForSend** šablony, najdete v článku [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) tématu.

### <a name="the-send-activity-properties"></a>Vlastnosti aktivity Send

Následující tabulka ukazuje <xref:System.ServiceModel.Activities.Send> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti můžete upravit v mřížce vlastností nebo na plochu návrháře postupu provádění.


| Název vlastnosti | Požadováno | Použití |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Popisný název <xref:System.ServiceModel.Activities.Send> aktivity. Výchozí hodnota je odeslat. I když <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutné, je osvědčeným postupem je použití jednoho. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | Hodnota TRUE | Název operace služby volané to <xref:System.ServiceModel.Activities.Send> aktivity. Tato vlastnost se používá k sestavení kompletních výchozí hodnota **akce** vlastnost Pokud **akce** není explicitně nastavena vlastnost. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | Hodnota TRUE | Název kontraktu služby, který implementuje volání služby. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | False | Určuje zprávu nebo parametr obsah, který se zobrazí. Může se jednat buď <xref:System.ServiceModel.Activities.ReceiveMessageContent> aktivity nebo <xref:System.ServiceModel.Activities.ReceiveParametersContent> aktivity. Tato vlastnost upravit tak, že vyberete tlačítko se třemi tečkami vedle **obsahu** v mřížce vlastností nebo kliknutím **definovat...**  tlačítko vedle **obsahu** popisek **Receive** povrch návrháře aktivit. Obě zobrazení **definici obsahu** dialogového okna. Další informace o tom, jak pomocí tohoto políčka, najdete v článku [obsahu dialogové okno Definice](../workflow-designer/content-definition-dialog-box.md) tématu. |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | False | Určuje, <xref:System.ServiceModel.Activities.CorrelationHandle> využívá ke směrování do instance pracovního postupu odpovídající zprávu.<br /><br /> Klikněte na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> vlastnost v mřížce vlastnosti otevřít **Editor výrazů** dialogové okno. Další informace o použití tohoto dialogového okna, najdete v článku [postupy: použití editoru výrazů](../workflow-designer/how-to-use-the-expression-editor.md) tématu. |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | False | Určuje kolekci <xref:System.ServiceModel.Activities.CorrelationInitializer> objekty, které inicializovat více <xref:System.ServiceModel.Activities.CorrelationHandle> objekty, které to nakonfigurovat <xref:System.ServiceModel.Activities.Send> aktivity v pracovním postupu. Klikněte na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> vlastnost v mřížce vlastnosti otevřít **přidat inicializátory korelace** dialogové okno. Další informace o použití tohoto pole, najdete v článku [dialogové okno Přidat inicializátory korelace](../workflow-designer/add-correlationinitializers-dialog-box.md) tématu. |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | False | Kolekce známých typů pro operaci služby volat situace <xref:System.ServiceModel.Activities.Send> aktivity. Tuto vlastnost byste měli použít ve spojení s <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> nastavenou na <xref:System.Runtime.Serialization.DataContractSerializer>. Se ignoruje, pokud <xref:System.Xml.Serialization.XmlSerializer> se používá.<br /><br /> Vyberte tlačítko se třemi tečkami vedle **KnownTypes** v mřížce vlastností zobrazíte **Editor typu kolekce** dialogové okno, pomocí kterého můžete přidat odpovídající typy.<br /><br /> Vyberte tlačítko se třemi tečkami vedle **KnownTypes** v mřížce vlastností zobrazíte **Editor typu kolekce** dialogovému oknu, pomocí kterého můžete přidat odpovídající typy. Další informace o použití tohoto pole, najdete v článku [dialogové okno Editor typu kolekce](../workflow-designer/type-collection-editor-dialog-box.md) tématu. |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | Hodnota TRUE | Určuje, <xref:System.Net.Security.ProtectionLevel> zprávy.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> znamená, že jenom ověřování.<br />2. <xref:System.Net.Security.ProtectionLevel> znamená, že podepsat data k zajištění integrity dat přenášených.<br />3. <xref:System.Net.Security.ProtectionLevel> znamená, že šifrování a podepisování dat k zajištění důvěrnost a integrita dat přenášených. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | Hodnota TRUE | Serializátoru, který je určený pro operaci služby má být volána <xref:System.ServiceModel.Activities.Send> aktivity. Výchozí hodnota je <xref:System.Runtime.Serialization.DataContractSerializer>, který serializuje a deserializuje instance typu do datový proud XML nebo do dokumentu s použitím kontraktu dat zadaný. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | False | Určuje akci záhlaví zprávy. Pokud není explicitně nastavena, její výchozí hodnota je: https://tempuri.org/{service obor názvů kontraktu} / {název kontraktu služby} / {název operace}. Pokud zadaný na <xref:System.ServiceModel.Activities.Send> aktivity, <xref:System.ServiceModel.Activities.Receive> aktivitu, která obdrží zprávu musí mít stejnou hodnotu pro zpráva, která má být správně doručena. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | <xref:System.Security.Principal.TokenImpersonationLevel> Povolené pro příjemce zprávy. Definuje úrovní zosobnění zabezpečení, které určují, do jaké míry, do které proces serveru můžou fungovat jménem klienta procesu.<xref:System.Security.Principal.TokenImpersonationLevel> Označuje, že není přiřazena úroveň zosobnění. <xref:System.Security.Principal.TokenImpersonationLevel> Označuje, že proces serveru nelze získat identifikační informace o klientovi a nelze jej zosobnit klienta. <xref:System.Security.Principal.TokenImpersonationLevel> Označuje, že proces serveru můžete získat informace o klientovi, jako je například identifikátory zabezpečení a oprávnění, ale, že nelze zosobnit klienta. To je užitečné pro servery, které exportovat vlastní objekty, například databáze produktů, které export tabulek a zobrazení. Pomocí informací o načtený zabezpečení klienta, serveru můžete rozhodovat ověření přístupu k aniž by bylo možné použít i jiné služby, které používají klienta kontext zabezpečení. <xref:System.Security.Principal.TokenImpersonationLevel> Označuje, že proces serveru může zosobnit kontext zabezpečení klienta ve svém místním systému. Server nelze zosobnit klienta na vzdálených systémů. <xref:System.Security.Principal.TokenImpersonationLevel> Označuje, že proces serveru můžou zosobnit kontext zabezpečení klienta ve vzdálených systémech. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | <xref:System.ServiceModel.Endpoint> , Který <xref:System.ServiceModel.Activities.Send> aktivita odesílá zprávu. Pokud je tato vlastnost nastavená <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> vlastnost by měla být **null**. |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | <xref:System.ServiceModel.EndpointAddress> Na kterém je zpráva odeslána. |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | Název konfigurace koncového bodu. Tato vlastnost nastavena, když konfigurujete koncový bod v konfiguračním souboru. Tato vlastnost musí být nastavená na daný název  **\<koncový bod >** element v konfiguračním souboru. Pokud je tato vlastnost nastavena, <xref:System.ServiceModel.Activities.Send.Endpoint%2A> vlastnost by měla být **null**. |

## <a name="see-also"></a>Viz také:

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)