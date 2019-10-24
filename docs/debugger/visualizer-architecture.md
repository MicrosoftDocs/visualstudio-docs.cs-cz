---
title: Architektura Vizualizér | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 6aad395f-7170-4d9e-b2b8-a5faf453380e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c92723a1b6abb371b44f1793f9ea5b1f8ad3bca
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728477"
---
# <a name="visualizer-architecture"></a>Architektura vizualizéru
Architektura Vizualizér ladicího programu má dvě části:

- V ladicím programu sady Visual Studio je spuštěna na *straně ladicího programu* . Kód na straně ladicího programu vytvoří a zobrazí uživatelské rozhraní pro svůj Vizualizér.

- *Laděného procesu strana* se spouští v rámci procesu Visual Studio, který je laděním ( *laděného procesu*).

  Vizualizér je komponenta ladicího programu, která umožňuje ladicímu programu zobrazit (*vizualizovat*) obsah datového objektu v smysluplném, srozumitelném formuláři. Některé vizualizace podporují také úpravu datového objektu. Vytvořením vlastních vizualizací můžete roztáhnout ladicí program, který bude zpracovávat vaše vlastní datové typy.

  Datový objekt, který se má vizuálně umístit v rámci procesu, který ladíte (proces *laděného procesu* ). Uživatelské rozhraní, které zobrazí data, se vytvoří v rámci procesu ladicího programu sady Visual Studio:

|Proces ladicího programu|Laděného procesu proces|
|----------------------|----------------------|
|Uživatelské rozhraní ladicího programu (tipy, okno kukátka, QuickWatch)|Datový objekt, který se má vizuálně|

 Chcete-li vizualizovat datový objekt v rámci rozhraní ladicího programu, potřebujete kód pro komunikaci mezi dvěma procesy. V důsledku toho se architektura Vizualizér skládá ze dvou částí: kód na *straně ladicího programu* a kód *strany laděného procesu* .

 Kód na straně ladicího programu vytvoří vlastní uživatelské rozhraní, které lze vyvolat z rozhraní ladicího programu, jako je například DataTip, okno kukátka nebo QuickWatch. Rozhraní Vizualizátoru je vytvořeno pomocí třídy <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> a rozhraní <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>. Podobně jako všechna rozhraní API pro Vizualizér se DialogDebuggerVisualizer a IDialogVisualizerService nacházejí v oboru názvů <xref:Microsoft.VisualStudio.DebuggerVisualizers>.

|Debugger – strana|Laděného procesu strana|
|-------------------|-------------------|
|DialogDebuggerVisualizer – třída<br /><br /> Rozhraní IDialogVisualizerService|Datový objekt|

 Uživatelské rozhraní získá data, která mají být vizuálně z poskytovatele objektu, který existuje na straně ladicího programu:

|Debugger – strana|Laděného procesu strana|
|-------------------|-------------------|
|DialogDebuggerVisualizer – třída<br /><br /> Rozhraní IDialogVisualizerService|Datový objekt|
|Poskytovatel objektů (implementuje <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>)||

 K dispozici je odpovídající objekt na straně laděného procesu, která se nazývá zdroj objektu:

|Debugger – strana|Laděného procesu strana|
|-------------------|-------------------|
|DialogDebuggerVisualizer – třída<br /><br /> Rozhraní IDialogVisualizerService|Datový objekt|
|Poskytovatel objektů (implementuje <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>)|Zdroj objektu (odvozený z <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>)|

 Poskytovatel objektů poskytuje data objektů, která se mají vizuálně přilišit k uživatelskému rozhraní Vizualizér. Poskytovatel objektů získá data objektu ze zdroje objektu. Poskytovatel objektů a zdroj objektů poskytují rozhraní API pro komunikaci objektů dat mezi stranou ladicího programu a laděného objektu stranou.

 Každý Vizualizér musí získat datový objekt, který se má vizuálně zobrazit. Následující tabulka uvádí odpovídající rozhraní API, které poskytovatel objektů a zdroj objektů používají pro tento účel:

|Poskytovatel objektů|Zdroj objektu|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A><br /><br /> —nebo—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A>|

 Všimněte si, že zprostředkovatel objektu může použít buď <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A>, nebo <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>. Rozhraní API má za následek volání <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A> ve zdroji objektu. Volání <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A?displayProperty=fullName> vyplní <xref:System.IO.Stream?displayProperty=fullName>, která představuje serializovanou formu objektu, který je vizuálně vytvořen.

 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> deserializace data zpět do formuláře objektu, který pak můžete zobrazit v uživatelském rozhraní, které vytvoříte pomocí <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> vyplní data jako nezpracovaný `Stream`, které je nutné odkonstruovat sami. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> funguje voláním <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> k získání serializovaného `Stream` a pak deserializaci dat. Použijte <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName>, pokud objekt není serializovatelný rozhraním .NET a vyžaduje vlastní serializaci. V takovém případě je nutné také přepsat metodu <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A?displayProperty=fullName>.

 Pokud vytváříte Vizualizér jen pro čtení, bude stačit jednosměrná komunikace s <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> nebo <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>. Pokud vytváříte vizualizér, který podporuje úpravy datových objektů, je nutné provést další. Musíte být schopni odeslat datový objekt z poskytovatele objektu zpátky do zdroje objektu. Následující tabulka ukazuje poskytovatele objektu a zdrojová rozhraní API objektů používaná pro tento účel:

|Poskytovatel objektů|Zdroj objektu|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A><br /><br /> —nebo—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>|

 Všimněte si znovu, že existují dvě rozhraní API, která může použít poskytovatel objektů. Data jsou vždy odesílána z poskytovatele objektu do zdroje objektu jako `Stream`, ale <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> vyžaduje, abyste objekt serializováni do `Stream` sami.

 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A> převezme objekt, který zadáte, zaserializaci ho do `Stream` a pak zavolá <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> k odeslání `Stream` do <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>.

 Použití jedné z metod Replace vytvoří nový datový objekt v laděného procesu, který nahradí vizuálně vyladěný objekt. Chcete-li změnit obsah původního objektu bez jeho nahrazení, použijte jednu z metod přenosu, které jsou uvedeny v následující tabulce. Tato rozhraní API přenášejí data v obou směrech současně bez nahrazení objektu, který je vizuálně vytvořen:

|Poskytovatel objektů|Zdroj objektu|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A><br /><br /> —nebo—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A>|

## <a name="see-also"></a>Viz také:
- [How to: Write a Visualizer](/visualstudio/debugger/create-custom-visualizers-of-data)
- [Návod: Zápis vizualizéru v jazyce C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Návod: Zápis vizualizéru v jazyce Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Návod: Zápis vizualizéru v jazyce Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Informace o zabezpečení vizualizéru](../debugger/visualizer-security-considerations.md)