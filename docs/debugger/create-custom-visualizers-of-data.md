---
title: Vytváření vlastních vizualizací dat | Microsoft Docs
description: Visual Studio vizualizace ladicího programu jsou komponenty, které zobrazují data. Přečtěte si o šesti standardních vizualizujích a o tom, jak můžete psát nebo stahovat ostatní.
ms.custom: SEO-VS-2020
ms.date: 05/27/2020
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b8310133520231434ba7ed342a5e855892e3c53a
ms.sourcegitcommit: d0061f62c8543ff0db500972d9402a7f00e017c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2021
ms.locfileid: "114201738"
---
# <a name="create-custom-data-visualizers"></a>Vytváření vlastních vizualizací dat

 *Vizualizér* je součástí [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] uživatelského rozhraní ladicího programu, které zobrazuje proměnnou nebo objekt způsobem vhodným pro svůj datový typ. Například Vizualizér HTML interpretuje řetězec HTML a zobrazí výsledek tak, jak by se zobrazil v okně prohlížeče. Vizualizér rastrového obrázku interpretuje strukturu rastrového obrázku a zobrazuje obrázek, který představuje. Některé vizualizace umožňují úpravu dat a jejich zobrazení.

 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]Ladicí program obsahuje šest standardních vizualizací. Vizualizace textu, HTML, XML a JSON fungují na objektech řetězců. Vizualizér stromu WPF zobrazuje vlastnosti vizuálního stromu objektu WPF. Vizualizér DataSet funguje pro objekty DataSet, DataView a DataTable.

Další vizualizace mohou být k dispozici ke stažení od Microsoftu, třetích stran a komunity. Můžete také napsat vlastní vizualizace a nainstalovat je do [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] ladicího programu.

V ladicím programu je Vizualizér reprezentován ikonou lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Ikona Vizualizátoru"). Můžete vybrat ikonu v **DataTip**, okně **kukátka kukátka** nebo **QuickWatch** dialogovém okně a pak vybrat vhodný Vizualizér pro odpovídající objekt.

## <a name="write-custom-visualizers"></a>Psát vlastní vizualizace

 > [!NOTE]
 > Chcete-li vytvořit vlastní Vizualizér pro nativní kód, přečtěte si ukázku [Vizualizér nativního ladicího programu SQLite](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) . vlastní vizualizace nejsou podporované pro UWP a aplikace Windows 8. x.

Můžete napsat vlastní Vizualizér pro objekt jakékoli spravované třídy s výjimkou <xref:System.Object> a <xref:System.Array> .

Architektura Vizualizér ladicího programu má dvě části:

- na *straně ladicího programu* běží v ladicím programu Visual Studio a vytvoří a zobrazí uživatelské rozhraní vizualizátoru.

- *laděného procesuá strana* se spouští v rámci Visual Studio procesu ladění ( *laděného procesu*). Datový objekt k vizualizaci (například objekt String) v procesu laděného procesu existuje. Laděného procesu strana odesílá objekt na stranu ladicího programu, která ji zobrazí v uživatelském rozhraní, které vytvoříte.

Na straně ladicího programu obdrží datový objekt od *poskytovatele objektu* , který implementuje <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> rozhraní. Laděného procesu strana odesílá objekt prostřednictvím *zdroje objektu*, který je odvozen z <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> .

Poskytovatel objektů může také odesílat data zpět do zdroje objektů, což umožňuje napsat vizualizér, který může upravovat data. Přepíšete poskytovatele objektů, aby komunikoval s vyhodnocovacím filtrem výrazů a zdrojem objektu.

Strana laděného procesu a ladicí program spolu vzájemně komunikují prostřednictvím <xref:System.IO.Stream> metod, které serializovat datový objekt do <xref:System.IO.Stream> a deserializace <xref:System.IO.Stream> zpátky do datového objektu.

Můžete napsat Vizualizér pro obecný typ pouze v případě, že typ je typ otevřený. Toto omezení je stejné jako omezení při použití `DebuggerTypeProxy` atributu. Podrobnosti najdete v tématu [použití atributu používání DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).

Vlastní vizualizace můžou mít bezpečnostní požadavky. Viz téma [informace o zabezpečení Vizualizátoru](../debugger/visualizer-security-considerations.md).

Následující kroky poskytují podrobný přehled vytváření Vizualizér. Podrobné pokyny najdete v tématu [Návod: zápis Vizualizér v jazyce C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md) nebo [Návod: zápis Vizualizér do Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md).

### <a name="to-create-the-debugger-side"></a>Vytvoření strany ladicího programu

Chcete-li vytvořit uživatelské rozhraní Vizualizátoru na straně ladicího programu, vytvořte třídu, která dědí z <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> , a přepište <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> metodu pro zobrazení rozhraní. můžete použít <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> k zobrazení Windowsch formulářů, dialogových oken a ovládacích prvků v vizualizér.

1. Použijte <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> metody k získání vizuálního objektu na straně ladicího programu.

1. Vytvořte třídu, která dědí z <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> .

1. Přepsáním <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> metody zobrazíte vaše rozhraní. použijte <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> metody pro zobrazení Windowsch formulářů, dialogových oken a ovládacích prvků v rozhraní.

1. Použijte <xref:System.Diagnostics.DebuggerVisualizerAttribute> a umožněte tak Vizualizér zobrazení ( <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> ).

#### <a name="special-debugger-side-considerations-for-net-50"></a>Speciální pokyny pro ladicí program pro .NET 5.0 +

Vlastní nástroje pro vizualizaci přenášejí data mezi *laděného procesu* a *ladicími programy* prostřednictvím binární serializace pomocí <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> třídy ve výchozím nastavení. Tento druh serializace se ale přizpůsobené podle toho v rozhraní .NET 5 a vyšším vzhledem k bezpečnostním hrozbám souvisejícím s chybami *unfixible* .
navíc byl označen jako zcela zastaralý v ASP.NET Core 5 a jeho použití bude zahozeno, jak je popsáno v [dokumentaci k ASP.NET Core](/dotnet/core/compatibility/core-libraries/5.0/binaryformatter-serialization-obsolete).
Proto tato část popisuje nezbytné kroky, které by měly být provedeny, aby byl v tomto scénáři stále podporován Vizualizér.

- Z důvodu kompatibility <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A> metoda, která byla přepsána v předchozí části, stále trvá v <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> . Nicméně je to vlastně typ <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider2> .
Proto přetypování `objectProvider` objektu na aktualizované rozhraní.

- Při odesílání objektů, jako jsou příkazy nebo data, na *laděného procesu* použití `IVisualizerObjectProvider2.Serialize` metody k předání do datového proudu, určíte nejlepší formát serializace, který bude použit na základě modulu runtime procesu *laděného procesu* .
Pak předejte datový proud do `IVisualizerObjectProvider2.TransferData` metody.

- Pokud komponenta Vizualizátor na *straně laděného procesu* potřebuje vrátit cokoli na *straně ladicího programu*, bude umístěna v <xref:System.IO.Stream> objektu vráceném <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A> metodou. Použijte `IVisualizerObjectProvider2.GetDeserializableObjectFrom` metodu k získání <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDeserializableObject> instance z ní a jejímu zpracování podle potřeby.

Další informace o tom, jaké další změny jsou nutné na *laděného procesu* při použití binární serializace, najdete v části [speciální doporučení na straně laděného procesu pro .NET 5.0 +](#special-debuggee-side-considerations-for-net-50) .

> [!NOTE]
> Pokud byste chtěli získat další informace o problému, přečtěte si [příručku zabezpečení BinaryFormatter](/dotnet/standard/serialization/binaryformatter-security-guide).

### <a name="to-create-the-visualizer-object-source-for-the-debuggee-side"></a>Vytvoření zdroje objektu Vizualizér pro stranu laděného procesu

V kódu na straně ladicího programu upravte a <xref:System.Diagnostics.DebuggerVisualizerAttribute> Zadejte typ pro vizualizaci (zdroj objektu na straně laděného procesu) ( <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> ). `Target`Vlastnost nastaví zdroj objektu. Vynecháte-li zdroj objektu, Vizualizér použije výchozí zdroj objektu.

::: moniker range=">=vs-2019"
Kód na straně laděného procesu obsahuje zdroj objektu, který je vizuálně vizuální. Datový objekt může přepsat metody <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> . Laděného procesuá knihovna DLL je nutná, pokud chcete vytvořit samostatný Vizualizér.
::: moniker-end

V kódu na straně laděného procesu:

- Aby mohl Vizualizér upravovat datové objekty, zdroj objektu musí dědit z <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> a přepsat `TransferData` `CreateReplacementObject` metody nebo.

- Pokud potřebujete podporovat cílení na více verzí v vizualizér, můžete v souboru projektu laděného procesu použít následující monikery cílového rozhraní (TFM).

   ```xml
   <TargetFrameworks>net20;netstandard2.0;netcoreapp2.0</TargetFrameworks>
   ```

   Toto jsou jediné podporované TFM.

#### <a name="special-debuggee-side-considerations-for-net-50"></a>Zvláštní důležité laděného procesu pro .NET 5.0 +

> [!IMPORTANT]
> K tomu, aby Vizualizér fungoval v rozhraní .NET 5,0 a vyšším, může být nutné provést další kroky z důvodu obav zabezpečení týkajících se základní binární serializace metody, která se používá ve výchozím nastavení. Než budete pokračovat, přečtěte si prosím tuto [část](#special-debugger-side-considerations-for-net-50) .

- Pokud Vizualizér implementuje <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A> metodu, použijte nově přidanou <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetDeserializableObject%2A> metodu, která je k dispozici v nejnovější verzi nástroje `VisualizerObjectSource` . <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDeserializableObject>Vrátí se k určení formátu serializace objektu (Binary nebo JSON) a k deserializaci podkladového objektu tak, aby mohl být použit.

- Pokud *laděného procesu* vrátí data na *stranu ladicího programu* jako součást `TransferData` volání, zaserializovat odpověď na datový proud na *straně ladicího programu* prostřednictvím <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A> metody.

## <a name="see-also"></a>Viz také

- [Návod: Zápis vizualizéru v jazyce C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Návod: Zápis vizualizéru v jazyce Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Postupy: Instalace vizualizéru](../debugger/how-to-install-a-visualizer.md)
- [Postupy: Testování a ladění vizualizéru](../debugger/how-to-test-and-debug-a-visualizer.md)
- [Referenční dokumentace k rozhraní API vizualizéru](../debugger/visualizer-api-reference.md)
- [Zobrazit data v ladicím programu](../debugger/viewing-data-in-the-debugger.md)
