---
title: Windows Communication Foundation a WCF Data Services
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: abcfde777223ada130e06ab7766319e1d982258c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585935"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Služby Windows Communication Foundation a služby WCF Data Services v sadě Visual Studio

Visual Studio poskytuje nástroje pro práci s Windows Communication Foundation (WCF) a WCF Data Services technologie Microsoftu pro vytváření distribuovaných aplikací. Toto téma poskytuje Úvod ke službám z perspektivy sady Visual Studio. Úplnou dokumentaci najdete v tématu [4.5 služby WCF Data](/dotnet/framework/data/wcf/index).

## <a name="what-is-wcf"></a>Co je WCF?

Windows Communication Foundation (WCF) je sjednocený rámec pro vytváření zabezpečených, spolehlivých, transakčních a interoperabilních distribuovaných aplikací. Nahrazuje starší technologie pro komunikaci mezi procesy, jako jsou webové služby na ASMX, Vzdálená komunikace .NET, podnikové služby (DCOM) a služba MSMQ. WCF v sobě spojuje funkčnost všech těchto technologií ještě používáte v rámci jednotný programovací model. To zjednodušuje vývoj distribuovaných aplikací.

### <a name="what-are-wcf-data-services"></a>Co jsou služby WCF Data Services

WCF Data Services je implementace standardu protokolu OData (Open data).  WCF Data Services umožňuje vystavit tabulková data jako sadu rozhraní REST API, což vám umožní vracet data pomocí standardních příkazů HTTP, jako je GET, POST, PUT nebo DELETE. Na straně serveru se nahrazuje služeb WCF Data Services [rozhraní ASP.NET Web API](https://dotnet.microsoft.com/apps/aspnet/apis) pro vytvoření nové služby OData. Klientská knihovna WCF Data Services je nadále vhodnou volbou pro využívání služeb OData v aplikaci .NET ze sady Visual Studio (**projekt** > **Přidat odkaz na službu**). Další informace najdete v tématu [4.5 služby WCF Data](/dotnet/framework/data/wcf).

### <a name="wcf-programming-model"></a>Programovací model WCF

Programovací model WCF je založen na komunikaci mezi dvěma entitami: službou WCF a klientem WCF. Programovací model je zapouzdřený v oboru názvů <xref:System.ServiceModel> v .NET.

### <a name="wcf-service"></a>Služby WCF

Služba WCF je založená na rozhraní, které definuje kontrakt mezi službou a klienta. Je označené atributem <xref:System.ServiceModel.ServiceContractAttribute> atributu, jak je znázorněno v následujícím kódu:

[!code-csharp[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
[!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]

Definování funkcí nebo metod, které jsou vystavené služby WCF jejich označením <xref:System.ServiceModel.OperationContractAttribute> atribut.

[!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
[!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]

Kromě toho můžete zveřejnit serializovaná data složeného typu s označením <xref:System.Runtime.Serialization.DataContractAttribute> atribut. To umožňuje datové vazby v klientovi.

Po definování rozhraní a jeho metody jsou zapouzdřeny v třídě, která implementuje rozhraní. Více kontraktů služby můžete implementovat jednu třídu služby WCF.

Služby WCF je přístupný pro spotřebu prostřednictvím co se označuje jako *koncový bod*. Koncový bod poskytuje jediný způsob, jak komunikovat se službou; službu nelze přistupovat prostřednictvím přímého odkazu stejně jako s jinými třídami.

Koncový bod se skládá z adresy, vazby a kontrakt. Adresa definuje, ve kterém se služba nachází; může jít adresu URL, adresa protokolu FTP, nebo síť nebo místní cestu. Vazby definuje způsob, jakým komunikujete se službou. Vazby WCF poskytují univerzální model pro zadání protokolu, jako je například HTTP nebo FTP, mechanismus zabezpečení, jako je například ověřování Windows nebo uživatelská jména a hesla a mnohem víc. Kontrakt zahrnuje operace, které jsou vystavené třídy služby WCF.

Více koncových bodů mohou být vystaveny pro jednu službu WCF. To umožňuje různé klienty komunikovat se stejnou službou různými způsoby. Například bankovní služba může poskytnout jeden koncový bod pro zaměstnance a druhý pro externí zákazníky, každý pomocí jiné adresy, vazby a/nebo smlouvy.

### <a name="wcf-client"></a>Klient WCF

Klienta WCF se skládá z *proxy* , který umožňuje aplikaci komunikovat se službou WCF a koncový bod, který odpovídá koncový bod definovaný pro službu. Proxy je vygenerován na straně klienta v souboru *App. config* a obsahuje informace o typech a metodách, které jsou zpřístupněny službou. Pro služby, které poskytují několik koncových bodů můžete klienta vybrat ten, který nejlépe vyhovuje jejich potřebám, například ke komunikaci přes protokol HTTP a používat ověřování Windows.

Po vytvoření klienta WCF odkazujete služby ve vašem kódu stejně jako jakýkoli jiný objekt. Například volání `GetData` metoda uvedená výše, měli byste napsat kód, který má následující podobu:

[!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
[!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]

## <a name="wcf-tools-in-visual-studio"></a>Nástroje WCF v aplikaci Visual Studio

Visual Studio poskytuje nástroje, které vám pomůžou vytvořit služby WCF i klienty WCF. Návod, který demonstruje nástroje, naleznete [v tématu Návod: Vytvoření jednoduché služby WCF v model Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).

### <a name="create-and-test-wcf-services"></a>Vytváření a testování služeb WCF

Šablony sady Visual Studio WCF můžete použít jako základ k rychlému vytvoření vlastní služby. Pak můžete automaticky hostitel služby WCF a testovacího klienta WCF pro ladění a otestování služby. Tyto nástroje společně poskytují rychlý a pohodlný ladění a testovací cyklus a eliminuje požadavek na potvrzení na model hostingu v rané fázi.

#### <a name="wcf-templates"></a>Šablony pro WCF

Šablony sady Visual Studio pro WCF poskytují základní strukturu tříd pro vývoj služeb. Jsou k dispozici v několika šablon WCF **přidat nový projekt** dialogové okno. Patří mezi ně lLibrary projekty služby WCF, websites služby WCF a šablony položek služby WCF.

Když vyberete šablonu, soubory jsou přidány pro servisní smlouvy, implementace služby a konfiguraci služby. Všechny atributy vyžadované již byly přidány, vytvoření jednoduchého typu "Hello World" služby, a nemáte psát jakýkoli kód. Samozřejmě, můžete přidat kód k poskytování funkcí a metod pro vaši službu reálného světa, ale šablony poskytují základ.

Další informace o šablonách WCF najdete v tématu [šablony pro WCF sady Visual Studio](/dotnet/framework/wcf/wcf-vs-templates).

#### <a name="wcf-service-host"></a>Hostitel služby WCF

Po spuštění ladicího programu sady Visual Studio (stisknutím klávesy **F5**) pro projekt služby WCF je hostitelský nástroj služby WCF automaticky spuštěn pro místní hostování služby. Hostitel služby WCF vypíše služby v projektu služby WCF, načte konfiguraci projektu a vytvoří instanci hostitele pro každou službu, kterou najde.

Pomocí hostitele služby WCF můžete testovat službu WCF bez psaní kódu navíc nebo potvrzení pouze určitého hostitele během vývoje.

Další informace o hostiteli služby WCF najdete v tématu [Hostitel služby WCF (WcfSvcHost. exe)](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe).

#### <a name="wcf-test-client"></a>Testovací klient WCF

Nástroj testovacího klienta WCF umožňuje vstupní parametry testu, odeslat tento vstup na službu WCF a zobrazovat odpovědi, které služba odesílá zpět. Poskytuje pohodlné službu testování prostředí, když ho spojovat se hostitel služby WCF. Vyhledejte nástroj ve složce *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE* .

Když stisknete klávesu **F5** k ladění projektu služby WCF, otevře se klient testu WCF a zobrazí seznam koncových bodů služby, které jsou definovány v konfiguračním souboru. Můžete testovat parametry a spustit službu a opakujte tento postup a průběžné testování a ověřování služby.

Další informace o testovacím klientovi WCF naleznete v tématu [klient testu WCF (WcfTestClient. exe)](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe).

### <a name="accessing-wcf-services-in-visual-studio"></a>Přístup ke službám WCF v aplikaci Visual Studio

Visual Studio zjednodušuje úlohu vytváření klientů WCF, automatické generování proxy serveru a koncového bodu pro služby, které přidáte pomocí dialogového okna **Přidat odkaz na službu** . Do souboru *App. config* se přidají všechny potřebné informace o konfiguraci. Většinu času, vše, co musíte udělat, je vytvořit instanci služby použít.

**Přidat odkaz na službu** dialogové okno umožňuje zadat adresu pro službu nebo vyhledejte službu, která je definována v rámci vašeho řešení. Dialogové okno vrátí seznam operací poskytuje tyto služby a služby. Také umožňuje definovat obor názvů, ve které bude odkazovat na službu v kódu.

**Nakonfigurovat odkazy na služby** dialogové okno umožňuje upravit konfiguraci pro službu. Můžete změnit adresu pro službu, zadat úroveň přístupu, asynchronní chování a typy kontraktů zpráv a nakonfigurovat znovuvyužití typů.

## <a name="how-to-select-a-service-endpoint"></a>Postupy: výběr koncového bodu služby

Některé služby Windows Communication Foundation (WCF) vystavit několik koncových bodů, pomocí kterých může klient komunikovat se službou. Služba může například vystavovat jeden koncový bod, který používá vazby HTTP a uživatelské jméno a heslo a druhý koncový bod, který používá ověřování pomocí protokolu FTP a systému Windows. První koncový bod můžou používat aplikace, které přístup ke službě z mimo bránu firewall, zatímco druhá mohou být použity v síti intranet.

V takovém případě můžete zadat `endpointConfigurationName` jako parametr do konstruktoru pro odkaz na službu.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-select-a-service-endpoint"></a>Chcete-li vybrat koncový bod služby

1. Přidejte odkaz na službu WCF tak, že kliknete pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a zvolíte **Přidat odkaz na službu**.

2. V editoru kódu přidejte konstruktor pro odkaz na službu:

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > Nahraďte *ServiceReference* s oborem názvů pro odkaz na službu a nahraďte *Service1Client* s názvem služby.

3. Zobrazí se seznam IntelliSense, který obsahuje přetížení pro konstruktor. Vyberte `endpointConfigurationName As String` přetížení.

4. Po přetížení, zadejte `=` *ConfigurationName*, kde *ConfigurationName* je název koncového bodu, který chcete použít.

    > [!NOTE]
    > Pokud neznáte názvy dostupných koncových bodů, najdete je v souboru *App. config* .

### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Chcete-li najít dostupné koncové body služby WCF

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na soubor **App. config** pro projekt, který obsahuje odkaz na službu, a pak klikněte na tlačítko **otevřít**. Soubor se zobrazí v editoru kódu.

2. Hledat `<Client>` značky v souboru.

3. Vyhledejte pod `<Client>` značky pro značky začínající `<Endpoint>`.

     Pokud odkaz na službu poskytuje několik koncových bodů, bude existovat dva nebo více `<Endpoint` značky.

4. Uvnitř značky `<EndPoint>` naleznete parametr`"` `name="`*SomeService* (kde *SomeService* představuje název koncového bodu). Toto je název koncového bodu, který lze předat `endpointConfigurationName As String` přetížení konstruktoru pro odkaz na službu.

## <a name="how-to-call-a-service-method-asynchronously"></a>Postupy: asynchronní volání metody služby

Většina metod služby Windows Communication Foundation (WCF) může volat synchronně nebo asynchronně. Asynchronní volání metody umožňuje vaší aplikaci a pokračujte v práci, zatímco metoda je volána při práci s pomalým připojením.

Ve výchozím nastavení, když je přidán odkaz na službu do projektu, je nakonfigurován tak, aby volal metody synchronně. Můžete změnit chování při volání metody asynchronně změnou nastavení v **nastavit odkaz na službu** dialogové okno.

> [!NOTE]
> Tato možnost nastavená na základě služby. Pokud jedna metoda pro službu je volána asynchronně, všechny metody musí být volána asynchronně.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-call-a-service-method-asynchronously"></a>Asynchronně volat metodu služby

1. V **Průzkumníka řešení**, vyberte odkaz na službu.

2. Na **projektu** nabídky, klikněte na tlačítko **nastavit odkaz na službu**.

3. V **nastavit odkaz na službu** dialogové okno, vyberte **Generovat asynchronní operace** zaškrtávací políčko.

## <a name="how-to-bind-data-returned-by-a-service"></a>Postupy: vytvoření vazby dat vrácených službou

Můžete vytvořit vazbu dat vrácené službou Windows Communication Foundation (WCF) na ovládací prvek, stejně jako kterýkoli jiný zdroj dat. můžete svázat do ovládacího prvku. Když přidáte odkaz na službu WCF, pokud služba obsahuje složené typy, které nevracejí data, se automaticky přidají do **zdroje dat** okna.

### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>K vytvoření vazby ovládacího prvku do jednoho datového pole vrácené službou WCF

1. Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.

   Zobrazí se okno **zdroje dat** .

2. V **zdroje dat** okna, rozbalte uzel pro odkaz na službu. Všechny složené typy vrácené zobrazením služby.

3. Rozbalte uzel typu. Zobrazí se datová pole pro daný typ.

4. Vyberte pole a klikněte na šipku rozevíracího seznamu a zobrazte seznam ovládacích prvků, které jsou k dispozici pro datový typ.

5. Klikněte na typ ovládacího prvku, na který chcete vytvořit vazby.

6. Přetáhněte pole do formuláře. Ovládací prvek je přidán do formuláře společně s komponentou <xref:System.Windows.Forms.BindingSource> a komponentou <xref:System.Windows.Forms.BindingNavigator>.

7. Opakujte kroky 4 až 6 pro jakékoli jiné pole, které chcete vytvořit vazbu.

### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>K vytvoření vazby ovládacího prvku na složený typ vrácené službou WCF

1. Na **Data** nabídce vyberte možnost **zobrazit zdroje dat**. Zobrazí se okno **zdroje dat** .

2. V **zdroje dat** okna, rozbalte uzel pro odkaz na službu. Všechny složené typy vrácené zobrazením služby.

3. Vyberte uzel pro typ a klikněte na šipku rozevíracího seznamu a zobrazte seznam dostupných možností.

4. Klikněte na možnost **DataGridView** k zobrazení dat v mřížce nebo **podrobnosti** k zobrazení dat v jednotlivých ovládacích prvků.

5. Přetáhněte uzel na formuláři. Ovládací prvky jsou přidány do formuláře společně s <xref:System.Windows.Forms.BindingSource> komponentou a <xref:System.Windows.Forms.BindingNavigator> komponentou.

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Postupy: Konfigurace služby pro opětovné použití stávajících typů

Při odkazu na službu se přidá do projektu, jsou generovány všechny typy definované v rámci služby v místním projektu. V mnoha případech to vytvoří duplicitní typy, pokud služba používá běžné typy rozhraní .NET nebo když jsou typy definovány ve sdílené knihovně.

K tomuto problému vyhnout, typy v odkazovaných sestaveních jsou sdílené ve výchozím nastavení. Pokud chcete zakázat sdílení typu pro jeden nebo více sestavení, můžete provést, **nakonfigurovat odkazy na služby** dialogové okno.

### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Zakázat sdílení do jednoho sestavení typu

1. V **Průzkumníka řešení**, vyberte odkaz na službu.

2. Na **projektu** nabídky, klikněte na tlačítko **nastavit odkaz na službu**.

3. V **nakonfigurovat odkazy na služby** dialogu **znovu použít typy v zadaných odkazovaných sestaveních**.

4. Zaškrtněte políčko pro každé sestavení, ve kterém chcete povolit typ sdílení. Zakázat sdílení pro sestavení typu, ponechejte políčko zaškrtnuto.

### <a name="to-disable-type-sharing-in-all-assemblies"></a>Zakázat sdílení ve všech sestaveních typu

1. V **Průzkumníka řešení**, vyberte odkaz na službu.

2. Na **projektu** nabídky, klikněte na tlačítko **nastavit odkaz na službu**.

3. V **nakonfigurovat odkazy na služby** dialogové okno, zrušte **znovu použít typy v odkazovaných sestaveních** zaškrtávací políčko.

## <a name="related-topics"></a>Příbuzná témata

| Název | Popis |
| - | - |
| [Návod: Vytvoření jednoduché služby WCF v modelu Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md) | Poskytuje podrobné ukázky vytváření a používání služeb WCF v aplikaci Visual Studio. |
| [Návod: vytvoření datové služby WCF pomocí WPF a Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md) | Poskytuje podrobné informace o tom, jak vytvořit a používat WCF Data Services v aplikaci Visual Studio. |
| [Používání vývojářských nástrojů WCF](/dotnet/framework/wcf/using-the-wcf-development-tools) | Popisuje, jak vytvářet a testovat služby WCF v aplikaci Visual Studio. |
| | [Postupy: Přidání, aktualizace nebo odebrání odkazu na službu WCF Data Service](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md) |
| [Řešení potíží s odkazy na služby](../data-tools/troubleshooting-service-references.md) | Uvádí některé běžné chyby, které se mohou vyskytnout s odkazy na služby a jak nechcete, aby. |
| [Ladění služeb WCF](../debugger/debugging-wcf-services.md) | Popisuje běžné problémy ladění a postupy, které se můžete setkat při ladění služeb WCF. |
| [Návod: Vytvoření n-vrstvých datových aplikací](../data-tools/walkthrough-creating-an-n-tier-data-application.md) | Obsahuje podrobné pokyny pro vytvoření typové datové sady a oddělení kódu TableAdapter a datové sady do více projektů. |
| [Dialogové okno Konfigurovat odkaz na službu](../data-tools/configure-service-reference-dialog-box.md) | Popisuje prvky uživatelského rozhraní **nastavit odkaz na službu** dialogové okno. |

## <a name="reference"></a>Odkaz

- <xref:System.ServiceModel>
- <xref:System.Data.Services>

## <a name="see-also"></a>Viz také:

- [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
