---
title: Služby Windows Communication Foundation a služby WCF Data Services
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c366ce44ab65ded62370dd3c219473089d5ca111
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299565"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Služby Windows Communication Foundation a služby WCF Data Services v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio poskytuje nástroje pro práci s Windows Communication Foundation (WCF) a [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]technologie Microsoftu pro vytváření distribuovaných aplikací. V tomto tématu najdete Úvod ke službám z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] perspektivy. Úplnou dokumentaci najdete v tématu [WCF Data Services 4,5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a).

## <a name="what-is-wcf"></a>Co je WCF?
 [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] je sjednocený rámec pro vytváření zabezpečených, spolehlivých, transakčních a interoperabilních distribuovaných aplikací. Nahrazuje starší technologie meziprocesové komunikace, jako je ASMX webové služby vzdálené komunikace .NET, podnikové služby (DCOM) a služby MSMQ. WCF v sobě spojuje funkčnost všech těchto technologií ještě používáte v rámci jednotný programovací model. To zjednodušuje vývoj distribuovaných aplikací.

#### <a name="what-are-wcf-data-services"></a>Co jsou služby WCF Data Services
 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] je implementace standardu protokolu OData (Open data).  Služby WCF Data Services umožňuje vystavit tabulková data jako sadu rozhraní REST API, což vám umožní vrátit data pomocí standardních příkazů HTTP, jako získat, POST, PUT nebo odstranit. Na straně serveru WCF Data Services pro vytváření nových služeb OData nahrazuje [webový rozhraní API ASP.NET](https://dotnet.microsoft.com/apps/aspnet/apis) . Klientská knihovna WCF Data Services je nadále vhodnou volbou pro využívání služeb OData v aplikaci .NET ze sady Visual Studio (**projekt &#124; přidat odkaz na službu**). Další informace najdete v tématu [WCF Data Services 4,5](https://go.microsoft.com/fwlink/?LinkID=119952).

### <a name="wcf-programming-model"></a>Model programování WCF
 Model programování WCF je založen na komunikaci mezi dvěma entitami: klienta WCF a služby WCF. Programovací model je zapouzdřený v oboru názvů <xref:System.ServiceModel> v [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

#### <a name="wcf-service"></a>Služby WCF
 Služba WCF je založená na rozhraní, které definuje kontrakt mezi službou a klienta. Je označen atributem <xref:System.ServiceModel.ServiceContractAttribute>, jak je znázorněno v následujícím kódu:

 [!code-csharp[WCFWalkthrough#6](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#6)]
 [!code-vb[WCFWalkthrough#6](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#6)]

 [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
 [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]

 Můžete definovat funkce nebo metody, které jsou zpřístupněny službou WCF jejich označením pomocí atributu <xref:System.ServiceModel.OperationContractAttribute>. Kromě toho můžete vystavit Serializovaná data tak, že označíte složený typ s atributem <xref:System.Runtime.Serialization.DataContractAttribute>. To umožňuje datové vazby v klientovi.

 Po definování rozhraní a jeho metody jsou zapouzdřeny v třídě, která implementuje rozhraní. Více kontraktů služby můžete implementovat jednu třídu služby WCF.

 Služba WCF je vystavená pro spotřebu prostřednictvím toho, co je známé jako *koncový bod*. Koncový bod poskytuje jediný způsob, jak komunikovat se službou; službu nelze přistupovat prostřednictvím přímého odkazu stejně jako s jinými třídami.

 Koncový bod se skládá z adresy, vazby a kontrakt. Adresa definuje, ve kterém se služba nachází; může jít adresu URL, adresa protokolu FTP, nebo síť nebo místní cestu. Vazby definuje způsob, jakým komunikujete se službou. Vazby WCF poskytují univerzální model pro zadání protokolu, jako je například HTTP nebo FTP, mechanismus zabezpečení, jako je například ověřování Windows nebo uživatelská jména a hesla a mnohem víc. Kontrakt zahrnuje operace, které jsou vystavené třídy služby WCF.

 Více koncových bodů mohou být vystaveny pro jednu službu WCF. To umožňuje různé klienty komunikovat se stejnou službou různými způsoby. Například bankovní služba může poskytnout jeden koncový bod pro zaměstnance a druhý pro externí zákazníky, každý pomocí jiné adresy, vazby a/nebo smlouvy.

#### <a name="wcf-client"></a>Klienta WCF
 Klient WCF se skládá z *proxy serveru* , který umožňuje aplikaci komunikovat se službou WCF, a koncovým bodem, který odpovídá koncovému bodu definovanému pro službu. Proxy server se generuje na straně klienta v souboru app.config a obsahuje informace o typech a metody, které jsou vystavené služby. Pro služby, které poskytují několik koncových bodů můžete klienta vybrat ten, který nejlépe vyhovuje jejich potřebám, například ke komunikaci přes protokol HTTP a používat ověřování Windows.

 Po vytvoření klienta WCF odkazujete služby ve vašem kódu stejně jako jakýkoli jiný objekt. Například pro volání výše uvedené metody `GetData` byste měli napsat kód, který se podobá následujícímu:

 [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
 [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]

## <a name="wcf-tools-in-visual-studio"></a>WCF nástroje v sadě Visual Studio
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] poskytuje nástroje, které vám pomůžou vytvořit služby WCF i klienty WCF. Návod, který demonstruje nástroje, naleznete [v tématu Návod: Vytvoření jednoduché služby WCF v model Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).

### <a name="creating-and-testing-wcf-services"></a>Vytváření a testování služeb WCF
 Můžete použít šablony WCF [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jako základ k rychlému vytvoření vlastní služby. Pak můžete automaticky hostitel služby WCF a testovacího klienta WCF pro ladění a otestování služby. Tyto nástroje společně poskytují rychlý a pohodlný ladění a testovací cyklus a eliminuje požadavek na potvrzení na model hostingu v rané fázi.

#### <a name="wcf-templates"></a>Šablony pro WCF
 Šablony [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] WCF poskytují základní strukturu tříd pro vývoj služeb. V dialogovém okně **Přidat nový projekt** jsou k dispozici několik šablon WCF. Patří mezi ně projekty knihovny služby WCF, webové servery služby WCF a šablon položek služby WCF.

 Když vyberete šablonu, soubory jsou přidány pro servisní smlouvy, implementace služby a konfiguraci služby. Všechny atributy vyžadované již byly přidány, vytvoření jednoduchého typu "Hello World" služby, a nemáte psát jakýkoli kód. Samozřejmě, můžete přidat kód k poskytování funkcí a metod pro vaši službu reálného světa, ale šablony poskytují základ.

 Další informace o šablonách WCF najdete v tématu [šablony pro WCF sady Visual Studio](https://msdn.microsoft.com/library/6a608575-3535-4190-89da-911e24c8374f).

#### <a name="wcf-service-host"></a>Hostitel služby WCF
 Při spuštění ladicího programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (stisknutím klávesy F5) pro projekt služby WCF je hostitelský nástroj služby WCF automaticky spuštěn pro místní hostování služby. Hostitel služby WCF vytvoří výčet služby v projektu služby WCF, načte konfiguraci projektu a vytvoří instanci hostitele pro každou službu, kterou zjistí.

 Pomocí hostitele služby WCF můžete testovat službu WCF bez psaní kódu navíc nebo potvrzení pouze určitého hostitele během vývoje.

 Další informace o hostiteli služby WCF najdete v tématu [Hostitel služby WCF (WcfSvcHost. exe)](https://msdn.microsoft.com/library/8643a63d-a357-4c39-bd6c-cdfdf71e370e).

#### <a name="wcf-test-client"></a>Testovací klient WCF
 Nástroj testovacího klienta WCF umožňuje vstupní parametry testu, odeslat tento vstup na službu WCF a zobrazovat odpovědi, které služba odesílá zpět. Poskytuje pohodlné službu testování prostředí, když ho spojovat se hostitel služby WCF. Tento nástroj najdete ve složce \Common7\IDE, která je pro Visual Studio 2015 nainstalovaná na jednotce C: **C:\Program Files (x86) \Microsoft Visual Studio 14.0 \ Common7\IDE\\** .

 Po stisknutí klávesy F5 začít ladit projekt služby WCF, Testovací klient WCF se otevře a zobrazí seznam koncových bodů služby, které jsou definovány v konfiguračním souboru. Můžete testovat parametry a spustit službu a opakujte tento postup a průběžné testování a ověřování služby.

 Další informace o testovacím klientovi WCF naleznete v tématu [klient testu WCF (WcfTestClient. exe)](https://msdn.microsoft.com/library/d4302855-677f-4640-aa90-c5d785d72fb7).

### <a name="accessing-wcf-services-in-visual-studio"></a>Přístup ke službám WCF v sadě Visual Studio
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zjednodušuje úlohu vytváření klientů WCF, automatické generování proxy serveru a koncového bodu pro služby, které přidáte pomocí dialogového okna **Přidat odkaz na službu** . Všechny potřebné informace o konfiguraci se přidá do souboru app.config. Většinu času, vše, co musíte udělat, je vytvořit instanci služby použít.

 Dialogové okno **Přidat odkaz na službu** umožňuje zadat adresu služby nebo vyhledat službu, která je definována ve vašem řešení. Dialogové okno vrátí seznam operací poskytuje tyto služby a služby. Také umožňuje definovat obor názvů, ve které bude odkazovat na službu v kódu.

 Dialogové okno **konfigurace odkazů na službu** umožňuje přizpůsobit konfiguraci služby. Můžete změnit adresu pro službu, zadat úroveň přístupu, asynchronní chování a typy kontraktů zpráv a nakonfigurovat znovuvyužití typů.

## <a name="how-to-select-a-service-endpoint"></a>Postupy: Výběr koncového bodu služby
 Některé služby Windows Communication Foundation (WCF) vystavit několik koncových bodů, pomocí kterých může klient komunikovat se službou. Služba může například vystavit jeden koncový bod, který používá HTTP vazby a uživatelské jméno / heslo zabezpečení a druhý koncového bodu, který používá ověřování Windows a protokolu FTP. První koncový bod můžou používat aplikace, které přístup ke službě z mimo bránu firewall, zatímco druhá mohou být použity v síti intranet.

 V takovém případě můžete zadat `endpointConfigurationName` jako parametr do konstruktoru pro odkaz na službu.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-select-a-service-endpoint"></a>Chcete-li vybrat koncový bod služby

1. Přidejte odkaz na službu WCF tak, že kliknete pravým tlačítkem myši na uzel projektu v Průzkumník řešení a zvolíte **Přidat odkaz na službu** .

2. V editoru kódu přidejte konstruktor pro odkaz na službu:

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > Nahraďte *ServiceReference* oborem názvů pro odkaz na službu a nahraďte *Service1Client* názvem služby.

3. Zobrazí se seznam technologie IntelliSense pomocí přetížení konstruktoru. Vyberte přetížení `endpointConfigurationName As String`.

4. Po přetížení zadejte `=` *ConfigurationName*, kde *ConfigurationName* je název koncového bodu, který chcete použít.

    > [!NOTE]
    > Pokud si nejste jisti názvy dostupné koncové body, najdete je v souboru app.config.

#### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Chcete-li najít dostupné koncové body služby WCF

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na soubor App. config pro projekt, který obsahuje odkaz na službu, a pak klikněte na tlačítko **otevřít**. Soubor se zobrazí v editoru kódu.

2. V souboru vyhledejte značku `<Client>`.

3. Vyhledejte pod značkou `<Client>` značku, která začíná na `<Endpoint>`.

     Pokud odkaz na službu poskytuje více koncových bodů, bude obsahovat dvě nebo více značek `<Endpoint`.

4. Uvnitř značky `<EndPoint>` naleznete parametr`"` `name="`*SomeService* (kde *SomeService* představuje název koncového bodu). Toto je název koncového bodu, který lze předat `endpointConfigurationName As String` přetížení konstruktoru pro odkaz na službu.

## <a name="how-to-call-a-service-method-asynchronously"></a>Postupy: asynchronní volání metody služby
 Většina metod služby Windows Communication Foundation (WCF) může volat synchronně nebo asynchronně. Asynchronní volání metody umožňuje vaší aplikaci a pokračujte v práci, zatímco metoda je volána při práci s pomalým připojením.

 Ve výchozím nastavení když se přidá odkaz na službu do projektu je nakonfigurován k volání metody synchronně. Chování můžete změnit na asynchronní volání metod změnou nastavení v dialogovém okně **Konfigurovat odkaz na službu** .

> [!NOTE]
> Tato možnost nastavená na základě služby. Pokud jedna metoda pro službu je volána asynchronně, všechny metody musí být volána asynchronně.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-call-a-service-method-asynchronously"></a>Asynchronně volat metodu služby

1. V **Průzkumník řešení**vyberte odkaz na službu.

2. V nabídce **projekt** klikněte na položku **Konfigurovat odkaz na službu**.

3. V dialogovém okně **Konfigurovat odkaz na službu** vyberte zaškrtávací políčko **Generovat asynchronní operace** .

## <a name="how-to-bind-data-returned-by-a-service"></a>Postupy: vytvoření vazby dat vrácených službou
 Můžete vytvořit vazbu dat vrácené službou Windows Communication Foundation (WCF) na ovládací prvek, stejně jako kterýkoli jiný zdroj dat. můžete svázat do ovládacího prvku. Pokud přidáte odkaz na službu WCF, pokud služba obsahuje složené typy, které vracejí data, budou automaticky přidány do okna **zdroje dat** .

#### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>K vytvoření vazby ovládacího prvku do jednoho datového pole vrácené službou WCF

1. V nabídce **data** klikněte na možnost **Zobrazit zdroje dat**. Zobrazí se okno **zdroje dat** .

2. V okně **zdroje dat** rozbalte uzel pro svůj odkaz na službu. Zobrazí se všechny složené typy vrácené službou.

3. Rozbalte uzel typu. Datová pole pro tento typ se zobrazí.

4. Vyberte pole a klikněte na šipku rozevíracího seznamu a zobrazte seznam ovládacích prvků, které jsou k dispozici pro datový typ.

5. Klikněte na typ ovládacího prvku, který chcete vytvořit vazbu.

6. Přetáhněte pole do formuláře. Ovládací prvek se přidá do formuláře společně s komponentou <xref:System.Windows.Forms.BindingSource> a <xref:System.Windows.Forms.BindingNavigator> komponentou.

7. Opakujte kroky 4 až 6 pro jakékoli jiné pole, které chcete vytvořit vazbu.

#### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>K vytvoření vazby ovládacího prvku na složený typ vrácené službou WCF

1. V nabídce **data** vyberte možnost **Zobrazit zdroje dat**. Zobrazí se okno **zdroje dat** .

2. V okně **zdroje dat** rozbalte uzel pro svůj odkaz na službu. Zobrazí se všechny složené typy vrácené službou.

3. Vyberte uzel pro typ a klikněte na šipku rozevíracího seznamu a zobrazte seznam dostupných možností.

4. Klikněte na tlačítko **DataGridView** a zobrazte tak data v tabulce nebo v **podrobnostech** , aby se zobrazila data v jednotlivých ovládacích prvcích.

5. Přetáhněte uzel na formuláři. Ovládací prvky budou přidány do formuláře společně s komponentou <xref:System.Windows.Forms.BindingSource> a <xref:System.Windows.Forms.BindingNavigator> komponentou.

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Postupy: konfigurace ve službě znovu použít existující typy
 Při odkazu na službu se přidá do projektu, jsou generovány všechny typy definované v rámci služby v místním projektu. V mnoha případech to vytvoří duplicitní typy, pokud služba používá společné typy [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] nebo když jsou typy definovány ve sdílené knihovně.

 K tomuto problému vyhnout, typy v odkazovaných sestaveních jsou sdílené ve výchozím nastavení. Pokud chcete zakázat sdílení typů pro jedno nebo více sestavení, můžete tak učinit v dialogovém okně **konfigurace odkazů na službu** .

#### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Zakázat sdílení do jednoho sestavení typu

1. V **Průzkumník řešení**vyberte odkaz na službu.

2. V nabídce **projekt** klikněte na položku **Konfigurovat odkaz na službu**.

3. V dialogovém okně **konfigurovat odkazy na službu** vyberte možnost **znovu použít typy v zadaných odkazovaných sestaveních**.

4. Zaškrtněte políčko pro každé sestavení, ve kterém chcete povolit typ sdílení. Zakázat sdílení pro sestavení typu, ponechejte políčko zaškrtnuto.

#### <a name="to-disable-type-sharing-in-all-assemblies"></a>Zakázat sdílení ve všech sestaveních typu

1. V **Průzkumník řešení**vyberte odkaz na službu.

2. V nabídce **projekt** klikněte na položku **Konfigurovat odkaz na službu**.

3. V dialogovém okně **konfigurovat odkazy na službu** zrušte zaškrtnutí políčka **znovu použít typy v odkazovaných sestaveních** .

## <a name="related-topics"></a>Související témata

|Titul|Popis|
|-----------|-----------------|
|[Návod: Vytvoření jednoduché služby WCF v modelu Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|Poskytuje podrobné ukázky vytváření a používání služeb WCF v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Návod: Vytvoření datové služby WCF pomocí WPF a Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|Poskytuje podrobné informace o tom, jak vytvořit a používat [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Používání vývojářských nástrojů WCF](https://msdn.microsoft.com/library/054adb87-c244-4d5a-83d1-0b2b44bd454b)|Popisuje, jak vytvářet a testovat služby WCF v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Postupy: Přidání, aktualizace nebo odebrání odkazu na službu](https://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)|Popisuje postup přidání, aktualizace nebo odebrání služeb WCF z projektu.|
|[Postupy: Přidání, aktualizace nebo odebrání odkazu na službu WCF Data Service](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|Popisuje, jak odkazovat a používat [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Řešení potíží s odkazy na služby](../data-tools/troubleshooting-service-references.md)|Uvádí některé běžné chyby, které se mohou vyskytnout s odkazy na služby a jak nechcete, aby.|
|[Ladění služeb WCF](../debugger/debugging-wcf-services.md)|Popisuje běžné problémy ladění a postupy, které se můžete setkat při ladění služeb WCF.|
|[Přehled služby Windows Communication Foundation Authentication Service](https://msdn.microsoft.com/library/6e121a28-89e8-4974-88a8-70aaa6a7d52b)|Popisuje způsob použití WCF k poskytování služeb role webového serveru.|
|[Návod: Vytvoření vícevrstvé datové aplikace](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|Obsahuje podrobné pokyny pro vytvoření typové datové sady a oddělení kódu TableAdapter a datové sady do více projektů.|
|[Dialogové okno Nastavit odkaz na službu](../data-tools/configure-service-reference-dialog-box.md)|Popisuje prvky uživatelského rozhraní dialogového okna **Konfigurovat odkaz na službu** .|

## <a name="reference"></a>Odkaz
 <xref:System.ServiceModel>

 <xref:System.Data.Services>

## <a name="see-also"></a>Viz také
 [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
