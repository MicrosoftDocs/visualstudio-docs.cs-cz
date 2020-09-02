---
title: 'Postupy: zápis Vizualizér | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, writing
ms.assetid: 625a0d4f-abcc-43f2-9f8c-31c131a4378e
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ce50276e4e83a1a055294c8e2b6e09cd0f93d54d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64833364"
---
# <a name="how-to-write-a-visualizer"></a>Postupy: Zápis vizualizéru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete napsat vlastní Vizualizér pro objekt jakékoli spravované třídy s výjimkou <xref:System.Object> nebo <xref:System.Array> .  
  
> [!NOTE]
> V aplikacích pro **Store** se podporují jenom standardní texty, HTML, XML a vizualizace JSON. Vlastní (uživatelsky vytvořené) vizualizace se nepodporují.  
  
 Architektura Vizualizér ladicího programu má dvě části:  
  
- V ladicím programu sady Visual Studio je spuštěna na *straně ladicího programu* . Kód na straně ladicího programu vytvoří a zobrazí uživatelské rozhraní pro svůj Vizualizér.  
  
- *Laděného procesu strana* se spouští v rámci procesu Visual Studio, který je laděním ( *laděného procesu*).  
  
  Datový objekt, který chcete vizualizovat (například objekt řetězce), existuje v laděného procesu-Process. Laděného procesu strana proto musí odeslat datový objekt na stranu ladicího programu, která ji pak může zobrazit pomocí uživatelského rozhraní, které vytvoříte.  
  
  Ladicí program obdrží tento datový objekt, který bude vizuálně vytvořen z *poskytovatele objektu* , který implementuje <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> rozhraní. Laděného procesu strana odesílá datový objekt prostřednictvím *zdroje objektu*, který je odvozen z <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> . Poskytovatel objektů může také odesílat data zpět do zdroje objektů, což umožňuje napsat vizualizér, který upravuje, a také zobrazení, data. Poskytovatel objektů lze přepsat tak, aby komunikoval s vyhodnocovacím filtrem výrazů, a proto se zdrojem objektu.  
  
  Strana laděného procesu a ladicí program vzájemně komunikují s sebou <xref:System.IO.Stream> . Metody jsou k dispozici pro serializaci datového objektu do <xref:System.IO.Stream> a deserializaci <xref:System.IO.Stream> zpět do datového objektu.  
  
  Kód strany laděného procesu je určen pomocí atributu DebuggerVisualizer ( <xref:System.Diagnostics.DebuggerVisualizerAttribute> ).  
  
  Chcete-li vytvořit uživatelské rozhraní Vizualizátoru na straně ladicího programu, je nutné vytvořit třídu, která dědí z <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> a přepsat <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> metodu pro zobrazení rozhraní.  
  
  Můžete použít <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> k zobrazení formulářů, dialogových oken a ovládacích prvků Windows z vašeho Vizualizér.  
  
  Podpora pro obecné typy je omezená. Můžete napsat Vizualizér pro cíl, který je obecný typ pouze v případě, že obecný typ je otevřený typ. Toto omezení je stejné jako omezení při použití `DebuggerTypeProxy` atributu. Podrobnosti najdete v tématu [použití atributu používání DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).  
  
  Vlastní vizualizace můžou mít bezpečnostní požadavky. Viz téma [informace o zabezpečení Vizualizátoru](../debugger/visualizer-security-considerations.md).  
  
  Níže uvedené postupy poskytují přehled o tom, co musíte udělat, abyste mohli vytvořit Vizualizér. Podrobnější vysvětlení najdete v tématu [Návod: zápis Vizualizér v jazyce C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
### <a name="to-create-the-debugger-side"></a>Vytvoření strany ladicího programu  
  
1. Použijte <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> metody k získání vizuálního objektu na straně ladicího programu.  
  
2. Vytvořte třídu, která dědí z <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> .  
  
3. Přepsáním <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> metody zobrazíte vaše rozhraní. Použijte <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> metody pro zobrazení formulářů, dialogových oken a ovládacích prvků Windows jako součást vašeho rozhraní.  
  
4. Použijte <xref:System.Diagnostics.DebuggerVisualizerAttribute> a umožněte tak Vizualizér ( <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> ).  
  
### <a name="to-create-the-debuggee-side"></a>Vytvoření laděného procesuové strany  
  
1. Použijte a <xref:System.Diagnostics.DebuggerVisualizerAttribute> umožněte tak Vizualizér ( <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> ) a zdroji objektů ( <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> ). Vynecháte-li zdroj objektu, bude použit výchozí zdroj objektu.  
  
2. Pokud chcete, aby váš Vizualizér mohl upravovat datové objekty, a zobrazit je, bude nutné přepsat `TransferData` `CreateReplacementObject` metody nebo z <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> .  
  
## <a name="see-also"></a>Viz také  
 [Vytvořit vlastní vizualizace](../debugger/create-custom-visualizers-of-data.md)   
 [Postupy: instalace Vizualizátoru](../debugger/how-to-install-a-visualizer.md)   
 [Postupy: testování a ladění Vizualizér](../debugger/how-to-test-and-debug-a-visualizer.md)   
 [Hlediska zabezpečení vizualizéru](../debugger/visualizer-security-considerations.md)
