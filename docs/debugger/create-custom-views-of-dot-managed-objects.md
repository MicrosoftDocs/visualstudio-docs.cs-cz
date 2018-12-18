---
title: Vytváření vlastních zobrazení spravovaných objektů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data types [C#], custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 970051c5f53c152ea6fee334c3c1f856172b5ed9
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280542"
---
# <a name="create-custom-views-of-managed-objects"></a>Vytváření vlastních zobrazení spravovaných objektů
Můžete přizpůsobit tak, jak Visual Studio zobrazí datové typy v oknech proměnných ladicího programu.  
  
## <a name="attributes"></a>Atributy  
 V jazyce C# a Visual Basic, přidáte rozšíření pro vlastní data s využitím <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute>, a <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
 V [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] kódu Visual Basic nepodporuje atribut DebuggerBrowsable. Toto omezení neplatí v novějších verzích rozhraní .NET Framework.  
  
## <a name="visualizers"></a>Vizualizéry  
 Můžete napsat vizualizéru pro zobrazení libovolného typu spravovaná data. Další informace najdete v tématu [postupy: zápis Vizualizéru](../debugger/how-to-write-a-visualizer.md).  
  
## <a name="native-code"></a>Nativní kód  
 Pro nativní kód můžete přidat vlastní datový typ rozšíření do autoexp.dat – soubor, který je umístěn v adresáři 11.0\Common7\Packages\Debugger Program Files\Microsoft Visual Studio. Pokyny, jak psát `autoexp` pravidla jsou umístěny v samotném souboru.  
  
> [!CAUTION]
>  Struktura tohoto souboru a syntaxe pravidla autoexp může změnit v každé verzi sady Visual Studio na další.  
  
 Nativní typ zobrazení můžete přizpůsobit také napsáním výrazu chyba při vyhodnocování doplňku. Další informace najdete v tématu [EEAddIn vzorku: ladění Expression Evaluator Add-In](https://msdn.microsoft.com/library/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Používání atributu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Kukátko a Rychlé kukátko Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Rozšíření ladění pomocí atributů zobrazení ladicího programu](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)