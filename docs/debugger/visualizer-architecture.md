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
ms.openlocfilehash: a6dfbc8c57ff2e78bf0c6ebbd4e9899c372d7084
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "73187168"
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

 Kód na straně ladicího programu vytvoří vlastní uživatelské rozhraní, které lze vyvolat z rozhraní ladicího programu, jako je například DataTip, okno kukátka nebo QuickWatch. Rozhraní Vizualizátoru je vytvořeno pomocí <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> třídy a <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> rozhraní. Stejně jako všechna rozhraní API Vizualizátor se v oboru názvů DialogDebuggerVisualizer a IDialogVisualizerService <xref:Microsoft.VisualStudio.DebuggerVisualizers> .

|Debugger – strana|Laděného procesu strana|
|-------------------|-------------------|
|DialogDebuggerVisualizer – třída<br /><br /> Rozhraní IDialogVisualizerService|Datový objekt|

 Uživatelské rozhraní získá data, která mají být vizuálně z poskytovatele objektu, který existuje na straně ladicího programu:

|Debugger – strana|Laděného procesu strana|
|-------------------|-------------------|
|DialogDebuggerVisualizer – třída<br /><br /> Rozhraní IDialogVisualizerService|Datový objekt|
|Poskytovatel objektů (Implements <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> )||

 K dispozici je odpovídající objekt na straně laděného procesu, která se nazývá zdroj objektu:

|Debugger – strana|Laděného procesu strana|
|-------------------|-------------------|
|DialogDebuggerVisualizer – třída<br /><br /> Rozhraní IDialogVisualizerService|Datový objekt|
|Poskytovatel objektů (Implements <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> )|Zdroj objektu (odvozený od <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> )|

 Poskytovatel objektů poskytuje data objektů, která se mají vizuálně přilišit k uživatelskému rozhraní Vizualizér. Poskytovatel objektů získá data objektu ze zdroje objektu. Poskytovatel objektů a zdroj objektů poskytují rozhraní API pro komunikaci objektů dat mezi stranou ladicího programu a laděného objektu stranou.

 Každý Vizualizér musí získat datový objekt, který se má vizuálně zobrazit. Následující tabulka uvádí odpovídající rozhraní API, které poskytovatel objektů a zdroj objektů používají pro tento účel:

|Poskytovatel objektů|Zdroj objektu|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A><br /><br /> —nebo—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A>|

 Všimněte si, že poskytovatel objektů může použít buď <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> nebo <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A> . Rozhraní API má za následek volání <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A> ve zdroji objektu. Volání do <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A?displayProperty=fullName> vyplňování <xref:System.IO.Stream?displayProperty=fullName> , které představuje serializovanou formu objektu, který je znázorněný jako vizuální.

 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> deserializace data zpět do formuláře objektu, který lze poté zobrazit v uživatelském rozhraní, pomocí kterého jste vytvořili <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> . <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> vyplní data jako nezpracovaná `Stream` , která je nutné odkonstruovat sami. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> funguje voláním <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> pro získání serializovaného `Stream` a následného deserializace dat. Použijte <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> , pokud objekt není serializovatelný rozhraním .NET a vyžaduje vlastní serializaci. V takovém případě je nutné také přepsat <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A?displayProperty=fullName> metodu.

 Pokud vytváříte Vizualizér jen pro čtení, jednosměrnou komunikaci s <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> nebo <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A> je dostačující. Pokud vytváříte vizualizér, který podporuje úpravy datových objektů, je nutné provést další. Musíte být schopni odeslat datový objekt z poskytovatele objektu zpátky do zdroje objektu. Následující tabulka ukazuje poskytovatele objektu a zdrojová rozhraní API objektů používaná pro tento účel:

|Poskytovatel objektů|Zdroj objektu|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A><br /><br /> —nebo—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>|

 Všimněte si znovu, že existují dvě rozhraní API, která může použít poskytovatel objektů. Data jsou vždy odesílána z poskytovatele objektu do zdroje objektu jako `Stream` , ale <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> vyžaduje, abyste objekt serializováni `Stream` sami sobě.

 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A> převezme objekt, který poskytnete, jeho serializaci do a `Stream` , potom volání <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> k odeslání `Stream` do <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A> .

 Použití jedné z metod Replace vytvoří nový datový objekt v laděného procesu, který nahradí vizuálně vyladěný objekt. Chcete-li změnit obsah původního objektu bez jeho nahrazení, použijte jednu z metod přenosu, které jsou uvedeny v následující tabulce. Tato rozhraní API přenášejí data v obou směrech současně bez nahrazení objektu, který je vizuálně vytvořen:

|Poskytovatel objektů|Zdroj objektu|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A><br /><br /> —nebo—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A>|

## <a name="see-also"></a>Viz také
- [Postupy: Zápis vizualizéru](create-custom-visualizers-of-data.md)
- [Návod: Zápis vizualizéru v jazyce C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Návod: Zápis vizualizéru v jazyce Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Návod: Zápis vizualizéru v jazyce Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Hlediska zabezpečení vizualizéru](../debugger/visualizer-security-considerations.md)