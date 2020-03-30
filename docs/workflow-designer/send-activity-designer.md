---
title: Návrhář pracovního postupu – odeslat Návrháře aktivit
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
ms.openlocfilehash: 8690d5ccf18c752aacb37a71243d9f591fb9ee30
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395225"
---
# <a name="send-activity-designer"></a>Návrhář aktivity Send

Návrhář **aktivity Odeslat** se používá <xref:System.ServiceModel.Activities.Send> k vytvoření a konfiguraci aktivity.

## <a name="the-send-activity"></a>Aktivita odeslání

 Aktivita <xref:System.ServiceModel.Activities.Send> se používá k odeslání zprávy službě. Aktivita <xref:System.ServiceModel.Activities.ReceiveReply> může být <xref:System.ServiceModel.Activities.Send> vázána na aktivitu, která přijímá zprávu jako součást vzoru výměny zpráv požadavek/odpověď na straně klienta.

### <a name="using-the-send-activity-designer"></a>Použití Návrháře odesílání aktivit

Přístup k návrháři aktivit **odesílání** v kategorii **Zasílání zpráv** v **panelu nástrojů**. Návrháře **aktivit Odeslat** lze přetáhnout z **panelu nástrojů** a přetáhnout na povrch návrháře pracovních postupů, kde jsou obvykle umístěny aktivity. Tím se <xref:System.ServiceModel.Activities.Send> vytvoří aktivita s výchozí <xref:System.Activities.Activity.DisplayName%2A> Odeslat. Lze <xref:System.Activities.Activity.DisplayName%2A> je upravit v záhlaví návrháře aktivit **Odeslat** nebo v poli **DisplayName** mřížky vlastností.

Chcete-li <xref:System.ServiceModel.Activities.ReceiveReply> vytvořit aktivitu a <xref:System.ServiceModel.Activities.Send> svázat ji s vybranou aktivitou, klepněte pravým tlačítkem myši na návrháře aktivit **odeslat,** klepněte na položku **Vytvořit příjemnou odpověď** v místní nabídce a pod návrhářem **Odeslat** se zobrazí návrhář **ReceiveReplyForSend.** Aktivita <xref:System.ServiceModel.Activities.ReceiveReply> je aktivita, která obdrží zprávu jako součást vzoru výměny zpráv požadavek/odpověď na straně klienta. Může být nakonfigurován s návrhářem **ReceiveReplyForSend.**

Případně **SendAndReceiveReply** návrhář emotivní šablony v kategorii **Zasílání zpráv** **panelu nástrojů** lze použít <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> k vytvoření dvojice předem nakonfigurované a aktivity. Další informace o použití šablon **SendAndReceiveReply** a **ReceiveReplyForSend** naleznete v tématu [SendAndReceiveReply.](../workflow-designer/sendandreceivereply-template-designer.md)

### <a name="the-send-activity-properties"></a>Vlastnosti aktivity odesílání

V následující tabulce <xref:System.ServiceModel.Activities.Send> jsou uvedeny vlastnosti a popisuje, jak jsou používány v návrháři. Tyto vlastnosti lze upravovat v mřížce vlastností nebo na povrchu Návrháře pracovních postupů.

| Název vlastnosti | Požaduje se | Využití |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Popisný název <xref:System.ServiceModel.Activities.Send> aktivity. Výchozí hodnota je Odeslat. Ačkoli <xref:System.Activities.Activity.DisplayName%2A> to není nezbytně nutné, je osvědčeným postupem používat jeden. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | True | Název operace služby volané <xref:System.ServiceModel.Activities.Send> touto aktivitou. Tato vlastnost se používá k vytvoření výchozí hodnoty vlastnosti **Action,** pokud vlastnost **Action** není explicitně nastavena. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | True | Název servisní smlouvy, kterou služba, která má být volána, implementuje. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | False | Určuje zprávu nebo obsah parametrů, který má být přijímán. Může to být <xref:System.ServiceModel.Activities.ReceiveMessageContent> aktivita <xref:System.ServiceModel.Activities.ReceiveParametersContent> nebo aktivita. Upravte tuto vlastnost tak, že vyberete tlačítko tři tečky vedle pole **Obsah** v mřížce vlastností nebo kliknete na tlačítko **Definovat...** vedle popisku **Obsah** na povrchu návrháře **aktivit příjmu.** Obě zobrazí dialogové **okno Definice obsahu.** Další informace o použití tohoto pole naleznete v tématu [dialogového okna Definice obsahu.](../workflow-designer/content-definition-dialog-box.md) |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | False | Určuje způsob, jak <xref:System.ServiceModel.Activities.CorrelationHandle> se použije ke směrování zprávy do příslušné instance pracovního postupu.<br /><br /> Klepnutím na tlačítko se třemi tečkami vedle vlastnosti <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> v mřížce vlastností otevřete dialogové okno Editor **výrazů.** Další informace o použití tohoto dialogového okna naleznete v tématu [Postup: Použití tématu Editor výrazů.](../workflow-designer/how-to-use-the-expression-editor.md) |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | False | Určuje kolekci <xref:System.ServiceModel.Activities.CorrelationInitializer> objektů, které inicializují <xref:System.ServiceModel.Activities.CorrelationHandle> <xref:System.ServiceModel.Activities.Send> více objektů, které konfigurují tuto aktivitu v rámci pracovního postupu. Kliknutím na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> vlastnosti v mřížce vlastností otevřete dialogové okno Přidat **intezivace korelace.** Další informace o použití tohoto pole naleznete v tématu [dialogového okna Přidat korelaciinivázivalizé inkrese.](../workflow-designer/add-correlationinitializers-dialog-box.md) |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | False | Kolekce známých typů pro operaci služby, <xref:System.ServiceModel.Activities.Send> které mají být volány touto aktivitou. Tato vlastnost by měla <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> být použita ve spojení s vlastností nastavenou na <xref:System.Runtime.Serialization.DataContractSerializer>. Pokud se používá, <xref:System.Xml.Serialization.XmlSerializer> je ignorován.<br /><br /> Vyberte tlačítko se třemi tečkami vedle pole **Známé Typy** v mřížce vlastností, chcete-li zobrazit dialogové okno **Editor kolekce typů,** se kterým můžete přidat příslušné typy.<br /><br /> Vyberte tlačítko se třemi tečkami vedle pole **Známé Typy** v mřížce vlastností, chcete-li zobrazit dialogové okno **Editor kolekce typů,** pomocí kterého můžete přidat příslušné typy. Další informace o použití tohoto pole naleznete v tématu [dialogového okna Editor kolekce typů.](../workflow-designer/type-collection-editor-dialog-box.md) |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | True | Určuje <xref:System.Net.Security.ProtectionLevel> pro zprávu.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> znamená pouze ověřování.<br />2. <xref:System.Net.Security.ProtectionLevel> znamená údaje o podepisování, které pomáhají zajistit integritu předávaných údajů.<br />3. <xref:System.Net.Security.ProtectionLevel> znamená šifrovat a podepisovat údaje, které pomáhají zajistit důvěrnost a integritu předávaných údajů. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | True | Serializátor, který má být používán <xref:System.ServiceModel.Activities.Send> pro operaci služby, která má být volána aktivitou. Výchozí hodnota <xref:System.Runtime.Serialization.DataContractSerializer>je , která serializuje a reserializuje instanci typu do datového proudu XML nebo dokumentu pomocí zadané datové smlouvy. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | False | Určuje záhlaví akce zprávy. Pokud není explicitně nastavena, jeho `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`hodnota je výchozí: . Pokud je <xref:System.ServiceModel.Activities.Send> zadán na <xref:System.ServiceModel.Activities.Receive> aktivitu, aktivita, která obdrží zprávu musí mít stejnou hodnotu pro zprávu, která má být doručena správně. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | Povoleno <xref:System.Security.Principal.TokenImpersonationLevel> pro příjemce zprávy. Definuje úrovně zosobnění zabezpečení, které určují, do jaké míry může serverový proces jednat jménem klientského procesu.<xref:System.Security.Principal.TokenImpersonationLevel> označuje, že úroveň zosobnění není přiřazena. <xref:System.Security.Principal.TokenImpersonationLevel>označuje, že proces serveru nemůže získat identifikační informace o klientovi a nemůže zosobnit klienta. <xref:System.Security.Principal.TokenImpersonationLevel>označuje, že proces serveru může získat informace o klientovi, například identifikátory zabezpečení a oprávnění, ale že nemůže klienta zosobnit. To je užitečné pro servery, které exportují své vlastní objekty, například databázové produkty, které exportují tabulky a zobrazení. Pomocí načtených informací o zabezpečení klienta může server provádět rozhodnutí o ověření přístupu, aniž by mohl používat jiné služby, které používají kontext zabezpečení klienta. <xref:System.Security.Principal.TokenImpersonationLevel>označuje, že proces serveru může zosobnit kontext zabezpečení klienta v místním systému. Server nemůže zosobnit klienta ve vzdálených systémech. <xref:System.Security.Principal.TokenImpersonationLevel>označuje, že proces serveru může zosobnit kontext zabezpečení klienta ve vzdálených systémech. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | Že <xref:System.ServiceModel.Endpoint> aktivita <xref:System.ServiceModel.Activities.Send> odešle zprávu. Pokud je tato <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> vlastnost nastavena vlastnost by měla být **null**. |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | Do <xref:System.ServiceModel.EndpointAddress> kterého je zpráva odeslána. |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | Název konfigurace koncového bodu. Tato vlastnost je nastavena při konfiguraci koncového bodu v konfiguračním souboru. Tato vlastnost by měla být nastavena na název uvedený v ** \<koncovém bodu>** prvek v konfiguračním souboru. Pokud je tato vlastnost <xref:System.ServiceModel.Activities.Send.Endpoint%2A> nastavena, vlastnost by měla být **null**. |

## <a name="see-also"></a>Viz také

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Přijmout](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)