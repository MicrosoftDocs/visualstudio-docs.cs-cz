---
title: Windows Communication Foundation a služby WCF Data Services
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b9f2202c96799fcc2e258e79f050d15fb474d0aa
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305504"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Služby Windows Communication Foundation a služby WCF Data Services v sadě Visual Studio

Visual Studio poskytuje nástroje pro práci s Windows Communication Foundation (WCF) a datové služby WCF technologií Microsoftu a vytváření distribuovaných aplikací. Toto téma obsahuje úvod do služeb z hlediska sady Visual Studio. Úplnou dokumentaci najdete v tématu [4.5 služby WCF Data](/dotnet/framework/data/wcf/index).

## <a name="what-is-wcf"></a>Co je WCF?

Windows Communication Foundation (WCF) je jednotné rozhraní pro vytváření zabezpečené, spolehlivé, počet zrušených zpracovaných a interoperabilní distribuovaných aplikací. Nahrazuje starší technologie meziprocesové komunikace, jako je webovými službami ASMX, vzdálené komunikace .NET, podnikové služby (DCOM) a služby MSMQ. WCF v sobě spojuje funkčnost všech těchto technologií ještě používáte v rámci jednotný programovací model. To zjednodušuje vývoj distribuovaných aplikací.

### <a name="what-are-wcf-data-services"></a>Co jsou služby WCF Data Services

Služby WCF Data Services je implementace standardní protokol Open Data (OData).  Služby WCF Data Services umožňuje vystavit tabulková data jako sadu rozhraní REST API, což vám umožní vrátit data pomocí standardních příkazů HTTP, jako získat, POST, PUT nebo odstranění. Na straně serveru se nahrazuje služeb WCF Data Services [rozhraní ASP.NET Web API](http://www.asp.net/web-api) pro vytvoření nové služby OData. Klientská knihovna služby WCF Data Services i nadále být dobrou volbou pro využívání služby OData v aplikacích .NET v sadě Visual Studio (**projektu** > **přidat odkaz na službu**). Další informace najdete v tématu [4.5 služby WCF Data](http://go.microsoft.com/fwlink/?LinkID=119952).

### <a name="wcf-programming-model"></a>Model programování WCF

Komunikace mezi dvěma entitami podle programovacího modelu WCF: klienta WCF a služby WCF. Programovací model, je zapouzdřena v <xref:System.ServiceModel> oboru názvů v rozhraní .NET Framework.

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

### <a name="wcf-client"></a>Klienta WCF

Klienta WCF se skládá z *proxy* , který umožňuje aplikaci komunikovat se službou WCF a koncový bod, který odpovídá koncový bod definovaný pro službu. Proxy server se generuje na straně klienta v *app.config* souboru a obsahuje informace o typech a metody, které jsou vystavené služby. Pro služby, které poskytují několik koncových bodů můžete klienta vybrat ten, který nejlépe vyhovuje jejich potřebám, například ke komunikaci přes protokol HTTP a používat ověřování Windows.

Po vytvoření klienta WCF odkazujete služby ve vašem kódu stejně jako jakýkoli jiný objekt. Například volání `GetData` metoda uvedená výše, měli byste napsat kód, který má následující podobu:

[!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
[!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]

## <a name="wcf-tools-in-visual-studio"></a>WCF nástroje v sadě Visual Studio

Visual Studio poskytuje nástroje, které vám pomůžou vytvořit WCF services a klienti WCF. Návod, který ukazuje nástroje najdete v tématu [návod: vytvoření jednoduché služby WCF ve Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).

### <a name="create-and-test-wcf-services"></a>Vytvoření a testování služeb WCF

Šablony sady Visual Studio WCF můžete použít jako základ rychle vytvářet vlastní služby. Pak můžete automaticky hostitel služby WCF a testovacího klienta WCF pro ladění a otestování služby. Tyto nástroje společně poskytují rychlý a pohodlný ladění a testovací cyklus a eliminuje požadavek na potvrzení na model hostingu v rané fázi.

#### <a name="wcf-templates"></a>Šablony pro WCF

Šablony sady Visual Studio WCF poskytují strukturu základní třída pro vývoj služby. Jsou k dispozici v několika šablon WCF **přidat nový projekt** dialogové okno. Patří mezi ně projekty lLibrary služeb WCF, WCF služby websites a šablon položek služby WCF.

Když vyberete šablonu, soubory jsou přidány pro servisní smlouvy, implementace služby a konfiguraci služby. Všechny atributy vyžadované již byly přidány, vytvoření jednoduchého typu "Hello World" služby, a nemáte psát jakýkoli kód. Samozřejmě, můžete přidat kód k poskytování funkcí a metod pro vaši službu reálného světa, ale šablony poskytují základ.

Další informace o šablonách WCF najdete v tématu [šablony sady Visual Studio WCF](/dotnet/framework/wcf/wcf-vs-templates).

#### <a name="wcf-service-host"></a>Hostitel služby WCF

Při spuštění ladicího programu sady Visual Studio (stisknutím klávesy **F5**) pro projekt služby WCF, se automaticky spustí nástroj hostitele služeb WCF pro hostování služby místně. Hostitel služby WCF vytvoří výčet služby v projektu služby WCF, načte konfiguraci projektu a vytvoří instanci hostitele pro každou službu, kterou zjistí.

Pomocí hostitele služby WCF můžete testovat službu WCF bez psaní kódu navíc nebo potvrzení pouze určitého hostitele během vývoje.

Další informace o hostiteli služby WCF najdete v tématu [hostitel služby WCF (WcfSvcHost.exe)](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe).

#### <a name="wcf-test-client"></a>Testovací klient WCF

Nástroj testovacího klienta WCF umožňuje vstupní parametry testu, odeslat tento vstup na službu WCF a zobrazovat odpovědi, které služba odesílá zpět. Poskytuje pohodlné službu testování prostředí, když ho spojovat se hostitel služby WCF. Nástroj v *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE* složky.

Když stisknete klávesu **F5** ladit projekt služby WCF, Testovací klient WCF se otevře a zobrazí seznam koncových bodů služby, které jsou definovány v konfiguračním souboru. Můžete testovat parametry a spustit službu a opakujte tento postup a průběžné testování a ověřování služby.

Další informace o testovacího klienta WCF najdete v tématu [WCF otestovat klienta (WcfTestClient.exe)](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe).

### <a name="accessing-wcf-services-in-visual-studio"></a>Přístup ke službám WCF v sadě Visual Studio

Visual Studio zjednodušuje vytváření klientů WCF, automaticky se generuje proxy server a koncový bod služby, které můžete přidat pomocí **přidat odkaz na službu** dialogové okno. Všechny potřebné informace o konfiguraci se přidá do *app.config* souboru. Většinu času, vše, co musíte udělat, je vytvořit instanci služby použít.

**Přidat odkaz na službu** dialogové okno umožňuje zadat adresu pro službu nebo vyhledejte službu, která je definována v rámci vašeho řešení. Dialogové okno vrátí seznam operací poskytuje tyto služby a služby. Také umožňuje definovat obor názvů, ve které bude odkazovat na službu v kódu.

**Nakonfigurovat odkazy na služby** dialogové okno umožňuje upravit konfiguraci pro službu. Můžete změnit adresu pro službu, zadat úroveň přístupu, asynchronní chování a typy kontraktů zpráv a nakonfigurovat znovuvyužití typů.

## <a name="how-to-select-a-service-endpoint"></a>Postupy: Výběr koncového bodu služby

Některé služby Windows Communication Foundation (WCF) vystavit několik koncových bodů, pomocí kterých může klient komunikovat se službou. Služba může například vystavit jeden koncový bod, který používá vazbu protokolu HTTP a uživatelské jméno a heslo zabezpečení a druhý koncového bodu, který používá ověřování Windows a protokolu FTP. První koncový bod můžou používat aplikace, které přístup ke službě z mimo bránu firewall, zatímco druhá mohou být použity v síti intranet.

V takovém případě můžete zadat `endpointConfigurationName` jako parametr do konstruktoru pro odkaz na službu.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-select-a-service-endpoint"></a>Chcete-li vybrat koncový bod služby

1.  Přidat odkaz na službu WCF kliknutím pravým tlačítkem myši na uzel projektu v **Průzkumníka řešení** a zvolíte **přidat odkaz na službu**.

2.  V editoru kódu přidejte konstruktor pro odkaz na službu:

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > Nahraďte *ServiceReference* s oborem názvů pro odkaz na službu a nahraďte *Service1Client* s názvem služby.

3.  Zobrazí seznam technologie IntelliSense, která obsahuje přetížení konstruktoru. Vyberte `endpointConfigurationName As String` přetížení.

4.  Po přetížení, zadejte `=` *ConfigurationName*, kde *ConfigurationName* je název koncového bodu, který chcete použít.

    > [!NOTE]
    > Pokud si nejste jisti názvy dostupné koncové body, najdete je *app.config* souboru.

### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Chcete-li najít dostupné koncové body služby WCF

1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem **app.config** souboru pro projekt, který obsahuje odkaz na službu a pak klikněte na **otevřít**. Soubor se zobrazí v editoru kódu.

2.  Hledat `<Client>` značky v souboru.

3.  Vyhledejte pod `<Client>` značky pro značky začínající `<Endpoint>`.

     Pokud odkaz na službu poskytuje několik koncových bodů, bude existovat dva nebo více `<Endpoint` značky.

4.  Uvnitř `<EndPoint>` označit, najdete `name="` *SomeService* `"` parametr (kde *SomeService* představuje název koncového bodu). Toto je název koncového bodu, který lze předat `endpointConfigurationName As String` přetížení konstruktoru pro odkaz na službu.

## <a name="how-to-call-a-service-method-asynchronously"></a>Postupy: asynchronní volání metody služby

Většina metod služby Windows Communication Foundation (WCF) může volat synchronně nebo asynchronně. Asynchronní volání metody umožňuje vaší aplikaci a pokračujte v práci, zatímco metoda je volána při práci s pomalým připojením.

Ve výchozím nastavení když se přidá odkaz na službu do projektu, je nakonfigurován k volání metody synchronně. Můžete změnit chování při volání metody asynchronně změnou nastavení v **nastavit odkaz na službu** dialogové okno.

> [!NOTE]
> Tato možnost nastavená na základě služby. Pokud jedna metoda pro službu je volána asynchronně, všechny metody musí být volána asynchronně.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-call-a-service-method-asynchronously"></a>Asynchronně volat metodu služby

1.  V **Průzkumníka řešení**, vyberte odkaz na službu.

2.  Na **projektu** nabídky, klikněte na tlačítko **nastavit odkaz na službu**.

3.  V **nastavit odkaz na službu** dialogové okno, vyberte **Generovat asynchronní operace** zaškrtávací políčko.

## <a name="how-to-bind-data-returned-by-a-service"></a>Postupy: vytvoření vazby dat vrácených službou

Můžete vytvořit vazbu dat vrácené službou Windows Communication Foundation (WCF) na ovládací prvek, stejně jako kterýkoli jiný zdroj dat. můžete svázat do ovládacího prvku. Když přidáte odkaz na službu WCF, pokud služba obsahuje složené typy, které nevracejí data, se automaticky přidají do **zdroje dat** okna.

### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>K vytvoření vazby ovládacího prvku do jednoho datového pole vrácené službou WCF

1.  Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.

   **Zdroje dat** zobrazí se okno.

2.  V **zdroje dat** okna, rozbalte uzel pro odkaz na službu. Složené typy vrácených zobrazení služby.

3.  Rozbalte uzel typu. Datová pole pro tento typ se zobrazí.

4.  Vyberte pole a klikněte na šipku rozevíracího seznamu a zobrazte seznam ovládacích prvků, které jsou k dispozici pro datový typ.

5.  Klikněte na typ ovládacího prvku, na kterou chcete vytvořit vazbu.

6.  Přetáhněte pole do formuláře. Ovládací prvek je přidán do formuláře, spolu s <xref:System.Windows.Forms.BindingSource> komponenty a <xref:System.Windows.Forms.BindingNavigator> komponenty.

7.  Opakujte kroky 4 až 6 pro jakékoli jiné pole, které chcete vytvořit vazbu.

### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>K vytvoření vazby ovládacího prvku na složený typ vrácené službou WCF

1.  Na **Data** nabídce vyberte možnost **zobrazit zdroje dat**. **Zdroje dat** zobrazí se okno.

2.  V **zdroje dat** okna, rozbalte uzel pro odkaz na službu. Složené typy vrácených zobrazení služby.

3.  Vyberte uzel pro typ a klikněte na šipku rozevíracího seznamu a zobrazte seznam dostupných možností.

4.  Klikněte na možnost **DataGridView** k zobrazení dat v mřížce nebo **podrobnosti** k zobrazení dat v jednotlivých ovládacích prvků.

5.  Přetáhněte uzel na formuláři. Ovládací prvky jsou přidány do formuláře, spolu s <xref:System.Windows.Forms.BindingSource> komponenty a <xref:System.Windows.Forms.BindingNavigator> komponenty.

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Postupy: konfigurace ve službě znovu použít existující typy

Při odkazu na službu se přidá do projektu, jsou generovány všechny typy definované v rámci služby v místním projektu. V mnoha případech se vytvoří duplicitní typy, když služba používá běžné typy rozhraní .NET Framework, nebo když jsou definovány typy ve sdílené knihovně.

K tomuto problému vyhnout, typy v odkazovaných sestaveních jsou sdílené ve výchozím nastavení. Pokud chcete zakázat sdílení typu pro jeden nebo více sestavení, můžete provést, **nakonfigurovat odkazy na služby** dialogové okno.

### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Zakázat sdílení do jednoho sestavení typu

1.  V **Průzkumníka řešení**, vyberte odkaz na službu.

2.  Na **projektu** nabídky, klikněte na tlačítko **nastavit odkaz na službu**.

3.  V **nakonfigurovat odkazy na služby** dialogu **znovu použít typy v zadaných odkazovaných sestaveních**.

4.  Zaškrtněte políčko pro každé sestavení, ve kterém chcete povolit typ sdílení. Zakázat sdílení pro sestavení typu, ponechejte políčko zaškrtnuto.

### <a name="to-disable-type-sharing-in-all-assemblies"></a>Zakázat sdílení ve všech sestaveních typu

1.  V **Průzkumníka řešení**, vyberte odkaz na službu.

2.  Na **projektu** nabídky, klikněte na tlačítko **nastavit odkaz na službu**.

3.  V **nakonfigurovat odkazy na služby** dialogové okno, zrušte **znovu použít typy v odkazovaných sestaveních** zaškrtávací políčko.

## <a name="related-topics"></a>Související témata

| Název | Popis |
| - | - |
| [Návod: Vytvoření jednoduché služby WCF v modelu Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md) | Poskytuje podrobné demonstraci vytvoření a použití služeb WCF v sadě Visual Studio. |
| [Návod: Vytvoření datové služby WCF s WPF a Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md) | Poskytuje podrobné demonstraci toho, jak vytvořit a používat datové služby WCF v sadě Visual Studio. |
| [Používání vývojářských nástrojů WCF](/dotnet/framework/wcf/using-the-wcf-development-tools) | Tento článek popisuje postup vytvoření a testování služeb WCF v sadě Visual Studio. |
| | [Postupy: Přidání, aktualizace nebo odebrání odkazu na službu WCF Data Service](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md) |
| [Řešení potíží s odkazy na služby](../data-tools/troubleshooting-service-references.md) | Uvádí některé běžné chyby, které se mohou vyskytnout s odkazy na služby a jak nechcete, aby. |
| [Ladění služeb WCF](../debugger/debugging-wcf-services.md) | Popisuje běžné problémy ladění a postupy, které se můžete setkat při ladění služeb WCF. |
| [Návod: Vytvoření vícevrstvé datové aplikace](../data-tools/walkthrough-creating-an-n-tier-data-application.md) | Obsahuje podrobné pokyny pro vytvoření typové datové sady a oddělení kódu TableAdapter a datové sady do více projektů. |
| [Odkaz na službu dialogové okno Konfigurace](../data-tools/configure-service-reference-dialog-box.md) | Popisuje prvky uživatelského rozhraní **nastavit odkaz na službu** dialogové okno. |

## <a name="reference"></a>Odkaz

- <xref:System.ServiceModel>
- <xref:System.Data.Services>

## <a name="see-also"></a>Viz také:

- [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)