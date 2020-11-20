---
title: Windows Communication Foundation a WCF Data Services
description: Prozkoumejte služby Windows Communication Foundation (WCF) a WCF Data Services v aplikaci Visual Studio, abyste mohli vytvářet distribuované aplikace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- services, WCF Data
- WCF services, binding to
- WCF services, asynchronous service methods
- service references [Visual Studio]
- WCF Data Services
- asynchronous calls
- service references [Visual Studio], type sharing
- endpoints [WCF]
- asynchronous service methods
- service references [Visual Studio] endpoints
- WCF services, type sharing
- Windows Communication Foundation, in Visual Studio
- services, WCF
- WCF service, Visual Studio
- data services, WCF
- services, in Visual Studio
- data binding [Visual Studio], WCF
- service endpoints [Visual Studio]
- service references [Visual Studio], asynchronous calls
- services, Windows Communication Foundation
- type sharing in WCF services
- WCF services, endpoints
- service method, called asynchronously[Visual Studio]
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 983ff598003a4f966b5173dc9ae78dd9aaa16580
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2020
ms.locfileid: "94997898"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Služby Windows Communication Foundation a služby WCF Data Services v sadě Visual Studio

Visual Studio poskytuje nástroje pro práci s Windows Communication Foundation (WCF) a WCF Data Services technologie Microsoftu pro vytváření distribuovaných aplikací. Toto téma poskytuje Úvod ke službám z perspektivy sady Visual Studio. Úplnou dokumentaci najdete v tématu [WCF Data Services 4,5](/dotnet/framework/data/wcf/index).

## <a name="what-is-wcf"></a>Co je WCF?

Windows Communication Foundation (WCF) je sjednocený rámec pro vytváření zabezpečených, spolehlivých, transakčních a interoperabilních distribuovaných aplikací. Nahrazuje starší technologie pro komunikaci mezi procesy, jako jsou webové služby na ASMX, Vzdálená komunikace .NET, podnikové služby (DCOM) a služba MSMQ. WCF přináší funkce všech těchto technologií v rámci jednotného programovacího modelu. To zjednodušuje prostředí vývoje distribuovaných aplikací.

### <a name="what-are-wcf-data-services"></a>Co jsou WCF Data Services

WCF Data Services je implementace standardu protokolu OData (Open data).  WCF Data Services umožňuje vystavit tabulková data jako sadu rozhraní REST API, což vám umožní vracet data pomocí standardních příkazů HTTP, jako je GET, POST, PUT nebo DELETE. Na straně serveru WCF Data Services pro vytváření nových služeb OData nahrazuje [webový rozhraní API ASP.NET](https://dotnet.microsoft.com/apps/aspnet/apis) . Klientská knihovna WCF Data Services je nadále vhodnou volbou pro využívání služeb OData v aplikaci .NET ze sady Visual Studio (**projekt**  >  **Přidat odkaz na službu**). Další informace najdete v tématu [WCF Data Services 4,5](/dotnet/framework/data/wcf).

### <a name="wcf-programming-model"></a>Programovací model WCF

Programovací model WCF je založen na komunikaci mezi dvěma entitami: službou WCF a klientem WCF. Programovací model je zapouzdřený v <xref:System.ServiceModel> oboru názvů v .NET.

### <a name="wcf-service"></a>Služba WCF

Služba WCF je založena na rozhraní, které definuje kontrakt mezi službou a klientem. Je označen <xref:System.ServiceModel.ServiceContractAttribute> atributem, jak je znázorněno v následujícím kódu:

[!code-csharp[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
[!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]

Můžete definovat funkce nebo metody, které jsou zpřístupněny službou WCF jejich označením pomocí <xref:System.ServiceModel.OperationContractAttribute> atributu.

[!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
[!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]

Kromě toho můžete vystavit Serializovaná data tak, že označíte složený typ s <xref:System.Runtime.Serialization.DataContractAttribute> atributem. Tato možnost povolí datovou vazbu v klientovi.

Po definování rozhraní a jeho metod jsou zapouzdřeny ve třídě, která implementuje rozhraní. Jedna třída služby WCF může implementovat několik kontraktů služeb.

Služba WCF je vystavená pro spotřebu prostřednictvím toho, co je známé jako *koncový bod*. Koncový bod poskytuje jediný způsob, jak komunikovat se službou. k této službě nemůžete přistupovat přes přímý odkaz, stejně jako u jiných tříd.

Koncový bod se skládá z adresy, vazby a kontraktu. Adresa určuje, kde se služba nachází; může to být adresa URL, adresa FTP nebo síťová nebo místní cesta. Vazba definuje způsob, jakým komunikujete se službou. Vazby WCF poskytují univerzální model pro určení protokolu, jako je HTTP nebo FTP, mechanismu zabezpečení, jako je například ověřování systému Windows nebo uživatelská jména a hesla, a mnoho dalšího. Kontrakt zahrnuje operace, které jsou zpřístupněny třídou služby WCF.

Pro jednu službu WCF může být vystaveno více koncových bodů. Díky tomu můžou Různí klienti komunikovat se stejnou službou různými způsoby. Například bankovní služba může poskytovat jeden koncový bod pro zaměstnance a druhý pro externí zákazníky, přičemž každý z nich používá jinou adresu, vazbu nebo kontrakt.

### <a name="wcf-client"></a>Klient WCF

Klient WCF se skládá z *proxy serveru* , který umožňuje aplikaci komunikovat se službou WCF, a koncovým bodem, který odpovídá koncovému bodu definovanému pro službu. Proxy je vygenerován na straně klienta v souboru *app.config* a obsahuje informace o typech a metodách, které jsou zpřístupněny službou. U služeb, které zveřejňují více koncových bodů, může klient vybrat ten, který nejlépe vyhovuje jeho potřebám, například pro komunikaci přes protokol HTTP a použití ověřování systému Windows.

Po vytvoření klienta WCF odkazujete na službu v kódu stejným způsobem jako jakýkoliv jiný objekt. Například pro volání `GetData` výše uvedené metody byste měli napsat kód, který se podobá následujícímu:

[!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
[!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]

## <a name="wcf-tools-in-visual-studio"></a>Nástroje WCF v aplikaci Visual Studio

Visual Studio poskytuje nástroje, které vám pomůžou vytvořit služby WCF i klienty WCF. Návod, který demonstruje nástroje, naleznete [v tématu Návod: Vytvoření jednoduché služby WCF v model Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).

### <a name="create-and-test-wcf-services"></a>Vytváření a testování služeb WCF

Šablony sady Visual Studio WCF můžete použít jako základ k rychlému vytvoření vlastní služby. Pak můžete použít automatické hostování služby WCF a testovacího klienta WCF pro ladění a testování služby. Tyto nástroje společně poskytují rychlý a pohodlný cyklus ladění a testování a odstraňují požadavek na zápis do modelu hostování v rané fázi.

#### <a name="wcf-templates"></a>Šablony WCF

Šablony sady Visual Studio pro WCF poskytují základní strukturu tříd pro vývoj služeb. V dialogovém okně **Přidat nový projekt** jsou k dispozici několik šablon WCF. Patří mezi ně lLibrary projekty služby WCF, websites služby WCF a šablony položek služby WCF.

Když vyberete šablonu, přidají se soubory pro kontrakt služby, implementaci služby a konfiguraci služby. Všechny nezbytné atributy jsou již přidány, vytváření jednoduchého typu "Hello World" služby a nemusíte psát žádný kód. Budete samozřejmě chtít přidat kód pro poskytování funkcí a metod pro vaši skutečnou světovou službu, ale šablony poskytují základní základ.

Další informace o šablonách WCF najdete v tématu [šablony pro WCF sady Visual Studio](/dotnet/framework/wcf/wcf-vs-templates).

#### <a name="wcf-service-host"></a>Hostitel služby WCF

Po spuštění ladicího programu sady Visual Studio (stisknutím klávesy **F5**) pro projekt služby WCF je hostitelský nástroj služby WCF automaticky spuštěn pro místní hostování služby. Hostitel služby WCF vypíše služby v projektu služby WCF, načte konfiguraci projektu a vytvoří instanci hostitele pro každou službu, kterou najde.

Pomocí hostitele služby WCF můžete testovat službu WCF bez psaní dalšího kódu nebo potvrzení konkrétního hostitele během vývoje.

Další informace o hostiteli služby WCF najdete v tématu [Hostitel služby WCF (WcfSvcHost.exe)](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe).

#### <a name="wcf-test-client"></a>Testovací klient WCF

Nástroj testovacího klienta WCF umožňuje zadat parametry testu, odeslat tento vstup do služby WCF a zobrazit odpověď, kterou služba odesílá zpět. Nabízí praktické prostředí pro testování služeb při kombinaci s hostitelem služby WCF. Vyhledejte nástroj ve složce *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE* .

Když stisknete klávesu **F5** k ladění projektu služby WCF, otevře se klient testu WCF a zobrazí seznam koncových bodů služby, které jsou definovány v konfiguračním souboru. Můžete testovat parametry a spustit službu a opakováním tohoto procesu průběžně testovat a ověřovat vaši službu.

Další informace o testovacím klientovi WCF najdete v článku [WCF test Client (WcfTestClient.exe)](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe).

### <a name="accessing-wcf-services-in-visual-studio"></a>Přístup ke službám WCF v aplikaci Visual Studio

Visual Studio zjednodušuje úlohu vytváření klientů WCF, automatické generování proxy serveru a koncového bodu pro služby, které přidáte pomocí dialogového okna **Přidat odkaz na službu** . Do souboru *app.config* jsou přidány všechny nezbytné informace o konfiguraci. Ve většině případů je vše, co musíte udělat, vytvořit instanci služby, aby ji bylo možné použít.

Dialogové okno **Přidat odkaz na službu** umožňuje zadat adresu služby nebo vyhledat službu, která je definována ve vašem řešení. Dialogové okno vrátí seznam služeb a operací poskytovaných těmito službami. Umožňuje také definovat obor názvů, pomocí kterého budete odkazovat na služby v kódu.

Dialogové okno **konfigurace odkazů na službu** umožňuje přizpůsobit konfiguraci služby. Můžete změnit adresu pro službu, zadat úroveň přístupu, asynchronní chování a typy kontraktů zpráv a nakonfigurovat opakované použití typu.

## <a name="how-to-select-a-service-endpoint"></a>Postupy: výběr koncového bodu služby

Některé služby Windows Communication Foundation (WCF) zpřístupňují několik koncových bodů, prostřednictvím kterých klient může komunikovat se službou. Služba může například vystavovat jeden koncový bod, který používá vazby HTTP a uživatelské jméno a heslo a druhý koncový bod, který používá ověřování pomocí protokolu FTP a systému Windows. První koncový bod můžou použít aplikace přistupující k této službě mimo bránu firewall, zatímco druhá se může použít na intranetu.

V takovém případě můžete zadat `endpointConfigurationName` jako parametr konstruktoru pro odkaz na službu.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-select-a-service-endpoint"></a>Výběr koncového bodu služby

1. Přidejte odkaz na službu WCF tak, že kliknete pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a zvolíte **Přidat odkaz na službu**.

2. V editoru kódu přidejte konstruktor pro odkaz na službu:

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > Nahraďte *ServiceReference* oborem názvů pro odkaz na službu a nahraďte *Service1Client* názvem služby.

3. Zobrazí se seznam IntelliSense, který obsahuje přetížení pro konstruktor. Vyberte `endpointConfigurationName As String` přetížení.

4. Po přetížení zadejte `=` *ConfigurationName*, kde *ConfigurationName* je název koncového bodu, který chcete použít.

    > [!NOTE]
    > Pokud názvy dostupných koncových bodů neznáte, najdete je v souboru *app.config* .

### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Vyhledání dostupných koncových bodů pro službu WCF

1. V **Průzkumník řešení** klikněte pravým tlačítkem na soubor **app.config** pro projekt, který obsahuje odkaz na službu, a pak klikněte na **otevřít**. Soubor se zobrazí v editoru kódu.

2. Vyhledejte `<Client>` značku v souboru.

3. Pod `<Client>` značkou vyhledejte značku, která začíná na `<Endpoint>` .

     Pokud odkaz na službu poskytuje více koncových bodů, bude obsahovat dvě nebo více `<Endpoint` značek.

4. Uvnitř `<EndPoint>` značky najdete `name="` parametr *SomeService* `"` (kde *SomeService* představuje název koncového bodu). Toto je název koncového bodu, který lze předat `endpointConfigurationName As String` přetížení konstruktoru pro odkaz na službu.

## <a name="how-to-call-a-service-method-asynchronously"></a>Postupy: asynchronní volání metody služby

Většina metod ve službě Windows Communication Foundation (WCF) se může volat buď synchronně, nebo asynchronně. Asynchronní volání metody umožňuje, aby vaše aplikace pokračovala v práci, zatímco metoda je volána, když funguje přes pomalé připojení.

Ve výchozím nastavení, když je přidán odkaz na službu do projektu, je nakonfigurován tak, aby volal metody synchronně. Chování můžete změnit na asynchronní volání metod změnou nastavení v dialogovém okně **Konfigurovat odkaz na službu** .

> [!NOTE]
> Tato možnost je nastavena na základě jednotlivých služeb. Pokud je jedna metoda pro službu volána asynchronně, všechny metody musí být volány asynchronně.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-call-a-service-method-asynchronously"></a>Postup asynchronního volání metody služby

1. V **Průzkumník řešení** vyberte odkaz na službu.

2. V nabídce **projekt** klikněte na položku **Konfigurovat odkaz na službu**.

3. V dialogovém okně **Konfigurovat odkaz na službu** vyberte zaškrtávací políčko **Generovat asynchronní operace** .

## <a name="how-to-bind-data-returned-by-a-service"></a>Postupy: vytvoření vazby dat vrácených službou

Data vrácená službou Windows Communication Foundation (WCF) můžete navazovat do ovládacího prvku stejně, jako můžete navazovat na ovládací prvek jakýkoliv jiný zdroj dat. Pokud přidáte odkaz na službu WCF, pokud služba obsahuje složené typy, které vracejí data, budou automaticky přidány do okna **zdroje dat** .

### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Svázání ovládacího prvku s jedním datovým polem vráceným službou WCF

1. V nabídce **data** klikněte na možnost **Zobrazit zdroje dat**.

   Zobrazí se okno **zdroje dat** .

2. V okně **zdroje dat** rozbalte uzel pro svůj odkaz na službu. Všechny složené typy vrácené zobrazením služby.

3. Rozbalte uzel pro typ. Zobrazí se datová pole pro daný typ.

4. Vyberte pole a kliknutím na šipku rozevíracího seznamu zobrazte seznam ovládacích prvků, které jsou k dispozici pro datový typ.

5. Klikněte na typ ovládacího prvku, na který chcete vytvořit vazby.

6. Přetáhněte pole na formulář. Ovládací prvek je přidán do formuláře společně s <xref:System.Windows.Forms.BindingSource> komponentou a <xref:System.Windows.Forms.BindingNavigator> komponentou.

7. Opakujte kroky 4 až 6 pro všechna další pole, která chcete vytvořit.

### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>Navázání ovládacího prvku na složený typ vrácený službou WCF

1. V nabídce **data** vyberte možnost **Zobrazit zdroje dat**. Zobrazí se okno **zdroje dat** .

2. V okně **zdroje dat** rozbalte uzel pro svůj odkaz na službu. Všechny složené typy vrácené zobrazením služby.

3. Vyberte uzel pro typ a kliknutím na šipku rozevíracího seznamu zobrazte seznam dostupných možností.

4. Klikněte na tlačítko **DataGridView** a zobrazte tak data v tabulce nebo v **podrobnostech** , aby se zobrazila data v jednotlivých ovládacích prvcích.

5. Přetáhněte uzel do formuláře. Ovládací prvky jsou přidány do formuláře společně s <xref:System.Windows.Forms.BindingSource> komponentou a <xref:System.Windows.Forms.BindingNavigator> komponentou.

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Postupy: Konfigurace služby pro opětovné použití stávajících typů

Při přidání odkazu na službu do projektu jsou všechny typy definované ve službě generovány v místním projektu. V mnoha případech to vytvoří duplicitní typy, pokud služba používá běžné typy rozhraní .NET nebo když jsou typy definovány ve sdílené knihovně.

Chcete-li se tomuto problému vyhnout, jsou typy v odkazovaných sestaveních sdíleny ve výchozím nastavení. Pokud chcete zakázat sdílení typů pro jedno nebo více sestavení, můžete tak učinit v dialogovém okně **konfigurace odkazů na službu** .

### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Zakázání sdílení typu v jednom sestavení

1. V **Průzkumník řešení** vyberte odkaz na službu.

2. V nabídce **projekt** klikněte na položku **Konfigurovat odkaz na službu**.

3. V dialogovém okně **konfigurovat odkazy na službu** vyberte možnost **znovu použít typy v zadaných odkazovaných sestaveních**.

4. Zaškrtněte políčko pro každé sestavení, ve kterém chcete povolit sdílení typů. Chcete-li zakázat sdílení typů pro sestavení, ponechejte políčko nezaškrtnuté.

### <a name="to-disable-type-sharing-in-all-assemblies"></a>Zakázání sdílení typů ve všech sestaveních

1. V **Průzkumník řešení** vyberte odkaz na službu.

2. V nabídce **projekt** klikněte na položku **Konfigurovat odkaz na službu**.

3. V dialogovém okně **konfigurovat odkazy na službu** zrušte zaškrtnutí políčka **znovu použít typy v odkazovaných sestaveních** .

## <a name="related-topics"></a>Související témata

| Nadpis | Popis |
| - | - |
| [Návod: Vytvoření jednoduché služby WCF v modelu Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md) | Poskytuje podrobné ukázky vytváření a používání služeb WCF v aplikaci Visual Studio. |
| [Návod: vytvoření datové služby WCF pomocí WPF a Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md) | Poskytuje podrobné informace o tom, jak vytvořit a používat WCF Data Services v aplikaci Visual Studio. |
| [Používání vývojářských nástrojů WCF](/dotnet/framework/wcf/using-the-wcf-development-tools) | Popisuje, jak vytvářet a testovat služby WCF v aplikaci Visual Studio. |
| | [Postupy: Přidání, aktualizace nebo odebrání odkazu na službu WCF Data Service](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md) |
| [Řešení potíží s odkazy na služby](../data-tools/troubleshooting-service-references.md) | Představuje některé běžné chyby, ke kterým může dojít s odkazy na služby a jak je zabránit. |
| [Ladění služeb WCF](../debugger/debugging-wcf-services.md) | Popisuje běžné problémy s laděním a techniky, se kterými se můžete setkat při ladění služeb WCF. |
| [Návod: Vytvoření n-vrstvých datových aplikací](../data-tools/walkthrough-creating-an-n-tier-data-application.md) | Poskytuje podrobné pokyny pro vytvoření typové datové sady a oddělení kódu TableAdapter a datové sady do více projektů. |
| [Dialogové okno Konfigurovat odkaz na službu](../data-tools/configure-service-reference-dialog-box.md) | Popisuje prvky uživatelského rozhraní dialogového okna **Konfigurovat odkaz na službu** . |

## <a name="reference"></a>Referenční informace

- <xref:System.ServiceModel>
- <xref:System.Data.Services>

## <a name="see-also"></a>Viz také

- [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
