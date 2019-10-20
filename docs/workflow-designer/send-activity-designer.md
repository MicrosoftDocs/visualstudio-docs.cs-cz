---
title: Návrhář aktivity Návrhář postupu provádění – odeslání
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 86eab31b2d268475f4ae6c9fe91c9ee5b6a4e4bc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649974"
---
# <a name="send-activity-designer"></a>Návrhář aktivity Send

Návrhář aktivity **odeslání** slouží k vytvoření a konfiguraci aktivity <xref:System.ServiceModel.Activities.Send>.

## <a name="the-send-activity"></a>Aktivita odeslání

 Aktivita <xref:System.ServiceModel.Activities.Send> slouží k odeslání zprávy službě. Aktivita <xref:System.ServiceModel.Activities.ReceiveReply> může být vázána na aktivitu <xref:System.ServiceModel.Activities.Send>, která přijímá zprávu jako součást vzoru výměny zprávy žádosti nebo odpovědi na klientovi.

### <a name="using-the-send-activity-designer"></a>Použití návrháře aktivity pro odeslání

Přihlaste se k Návrháři aktivity **odeslání** v kategorii **zprávy** sady **nástrojů**. Návrhář aktivity **odeslání** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity. Tím se vytvoří aktivita <xref:System.ServiceModel.Activities.Send> s výchozím <xref:System.Activities.Activity.DisplayName%2A> odeslání. @No__t_0 lze upravit v záhlaví návrháře aktivity **odeslání** nebo v poli **DisplayName** v mřížce vlastností.

Chcete-li vytvořit aktivitu <xref:System.ServiceModel.Activities.ReceiveReply> a vytvořit její propojení s vybranou aktivitou <xref:System.ServiceModel.Activities.Send>, klikněte pravým tlačítkem myši na Návrhář aktivity **Odeslat** , klikněte na položku **vytvořit ReceiveReply** v kontextové nabídce a **ReceiveReplyForSend** Designer se zobrazí pod  **Odeslat** návrháře Aktivita <xref:System.ServiceModel.Activities.ReceiveReply> je aktivita, která přijímá zprávy jako součást vzoru výměny zprávy žádosti nebo odpovědi na klientovi. Dá se nakonfigurovat pomocí návrháře **ReceiveReplyForSend** .

Alternativně lze pomocí návrháře šablon **SendAndReceiveReply** v kategorii **zasílání zpráv** v **sadě nástrojů** vytvořit dvojici předkonfigurovaných <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply>ch aktivit. Další informace o použití šablon **SendAndReceiveReply** a **ReceiveReplyForSend** naleznete v tématu [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

### <a name="the-send-activity-properties"></a>Vlastnosti aktivity odeslání

V následující tabulce jsou uvedeny vlastnosti <xref:System.ServiceModel.Activities.Send> a popisuje, jak se používají v návrháři. Tyto vlastnosti se dají upravovat v mřížce vlastností nebo na Návrhář postupu provádění ploše.

| Název vlastnosti | Požadováno | Použití |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Popisný název aktivity <xref:System.ServiceModel.Activities.Send>. Výchozí hodnota je Send. I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | Podmínka | Název operace služby volané touto aktivitou <xref:System.ServiceModel.Activities.Send>. Tato vlastnost slouží k vytvoření výchozí hodnoty pro vlastnost **Action** , pokud vlastnost **Action** není explicitně nastavena. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | Podmínka | Název kontraktu služby, který služba má volat implementující. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | False | Určuje zprávu nebo parametr obsahu, který se má přijmout. Může to být buď aktivita <xref:System.ServiceModel.Activities.ReceiveMessageContent>, nebo aktivita <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Upravte tuto vlastnost tak, že vyberete tlačítko se třemi tečkami vedle pole **obsah** v mřížce vlastností nebo kliknete na tlačítko **definovat...** vedle popisku **obsahu** na ploše návrháře aktivity **příjmu** . V obou zobrazeních se zobrazí dialogové okno **definice obsahu** . Další informace o tom, jak používat toto pole, najdete v tématu věnovaném [definici obsahu v dialogu](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | False | Určuje <xref:System.ServiceModel.Activities.CorrelationHandle>, který se použije ke směrování zprávy do příslušné instance pracovního postupu.<br /><br /> Kliknutím na tlačítko se třemi tečkami vedle vlastnosti <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> v mřížce vlastnosti otevřete dialogové okno **Editor výrazů** . Další informace o použití tohoto dialogového okna naleznete v tématu [Postupy: použití editoru výrazů](../workflow-designer/how-to-use-the-expression-editor.md) . |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | False | Určuje kolekci <xref:System.ServiceModel.Activities.CorrelationInitializer> objektů, které inicializují více objektů <xref:System.ServiceModel.Activities.CorrelationHandle>, které konfigurují tuto <xref:System.ServiceModel.Activities.Send> aktivitu v rámci pracovního postupu. Kliknutím na tlačítko se třemi tečkami vedle vlastnosti <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> v mřížce vlastnosti otevřete dialogové okno **Přidat Inicializátory korelace** . Další informace o použití tohoto pole najdete v tématu věnovaném [dialogovému oknu Přidat inicializátoři CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | False | Kolekce známých typů pro operaci služby, kterou má tato aktivita <xref:System.ServiceModel.Activities.Send> vyvolat. Tato vlastnost by měla být použita společně s vlastností <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> nastavenou na hodnotu <xref:System.Runtime.Serialization.DataContractSerializer>. Pokud se používá <xref:System.Xml.Serialization.XmlSerializer>, ignoruje se.<br /><br /> Kliknutím na tlačítko se třemi tečkami vedle pole **KnownTypes** v mřížce vlastností zobrazíte dialogové okno **Editor kolekcí typů** , ve kterém můžete přidat relevantní typy.<br /><br /> Kliknutím na tlačítko se třemi tečkami vedle pole **KnownTypes** v mřížce vlastností zobrazíte dialogové okno **Editor kolekcí typů** , ve kterém můžete přidat relevantní typy. Další informace o použití tohoto pole naleznete v tématu [dialogové okno Editor kolekcí typů](../workflow-designer/type-collection-editor-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | Podmínka | Určuje <xref:System.Net.Security.ProtectionLevel> zprávy.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> znamená pouze ověřování.<br />2. <xref:System.Net.Security.ProtectionLevel> znamená znaménka dat, která pomůžou zajistit integritu přenášených dat.<br />3. <xref:System.Net.Security.ProtectionLevel> znamená šifrování a podepsání dat, které vám pomůžou zajistit důvěrnost a integritu přenášených dat. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | Podmínka | Serializátor, který se má použít k volání operace služby <xref:System.ServiceModel.Activities.Send> aktivitou. Výchozí hodnota je <xref:System.Runtime.Serialization.DataContractSerializer>, která serializace a deserializace instance typu do datového proudu XML nebo dokumentu pomocí dodaného kontraktu dat. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | False | Určuje hlavičku akce zprávy. Pokud není nastavené explicitně, jeho hodnota se nastaví na výchozí hodnotu: https://tempuri.org/{service obor názvů kontraktu}/{Service název kontraktu}/{Operation název}. Pokud je tato aktivita zadána u aktivity <xref:System.ServiceModel.Activities.Send>, musí mít <xref:System.ServiceModel.Activities.Receive> aktivity, která přijímá zprávu, stejnou hodnotu, aby byla zpráva správně doručena. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | @No__t_0 povolených pro příjemce zprávy. Definuje úrovně zosobnění zabezpečení, které určují míru, na kterou proces serveru může působit jménem procesu klienta. <xref:System.Security.Principal.TokenImpersonationLevel> indikuje, že úroveň zosobnění není přiřazena. <xref:System.Security.Principal.TokenImpersonationLevel> označuje, že proces serveru nemůže získat identifikační informace o klientovi a nemůže zosobnit klienta. <xref:System.Security.Principal.TokenImpersonationLevel> označuje, že proces serveru může získat informace o klientovi, například identifikátory zabezpečení a oprávnění, ale že nemůže zosobnit klienta. To je užitečné pro servery, které exportují své vlastní objekty, například databázové produkty, které exportují tabulky a zobrazení. Pomocí načtených informací o zabezpečení klienta může server provádět rozhodnutí o ověření přístupu, aniž by bylo možné používat jiné služby, které používají kontext zabezpečení klienta. <xref:System.Security.Principal.TokenImpersonationLevel> označuje, že proces serveru může zosobnit kontext zabezpečení klienta v místním systému. Server nemůže zosobnit klienta ve vzdálených systémech. <xref:System.Security.Principal.TokenImpersonationLevel> označuje, že proces serveru může zosobnit kontext zabezpečení klienta ve vzdálených systémech. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | @No__t_0, na kterou aktivita <xref:System.ServiceModel.Activities.Send> odesílá zprávu Pokud je tato vlastnost nastavená, vlastnost <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> by měla mít **hodnotu null**. |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | @No__t_0, na kterou se zpráva odesílá |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | Název konfigurace koncového bodu. Tato vlastnost se nastavuje při konfiguraci koncového bodu v konfiguračním souboru. Tato vlastnost by měla být nastavena na název zadaný v prvku **\<endpoint >** v konfiguračním souboru. Pokud je tato vlastnost nastavena, vlastnost <xref:System.ServiceModel.Activities.Send.Endpoint%2A> by měla mít **hodnotu null**. |

## <a name="see-also"></a>Viz také:

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)