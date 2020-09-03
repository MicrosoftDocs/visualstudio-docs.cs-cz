---
title: Vytváření vlastních zobrazení spravovaných objektů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb5b56404c7ddc99b7999b47cf3c2a899f915efd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72578053"
---
# <a name="create-custom-views-of-managed-objects"></a>Vytváření vlastních zobrazení spravovaných objektů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete přizpůsobit způsob, jakým aplikace Visual Studio zobrazuje datové typy v oknech proměnných ladicího programu.  
  
## <a name="attributes"></a>Atributy  
 V jazyce C# a Visual Basic můžete přidat rozšíření pro vlastní data pomocí <xref:System.Diagnostics.DebuggerTypeProxyAttribute> , <xref:System.Diagnostics.DebuggerDisplayAttribute> a <xref:System.Diagnostics.DebuggerBrowsableAttribute> .  
  
 V [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] kódu Visual Basic nepodporuje atribut DebuggerBrowsable. Toto omezení je odebráno v novějších verzích .NET Framework.  
  
## <a name="visualizers"></a>Vizualizéry  
 Můžete napsat Vizualizér pro zobrazení libovolného spravovaného datového typu. Další informace naleznete v tématu [How to: Write a Vizualizér](../debugger/how-to-write-a-visualizer.md).  
  
## <a name="native-code"></a>Nativní kód  
 V případě nativního kódu můžete přidat rozšíření vlastních datových typů do souboru autoexp. dat, který je umístěn v adresáři Program Files\Microsoft Visual Studio 11.0 \ Common7\Packages\Debugger. Pokyny, jak psát `autoexp` pravidla, jsou umístěny v samotném souboru.  
  
> [!CAUTION]
> Struktura tohoto souboru a syntaxe pravidel autoexp se může změnit z jedné verze sady Visual Studio na další.  
  
 Zobrazení nativního typu lze také přizpůsobit zápisem doplňku vyhodnocení výrazu. Další informace najdete v tématu [Ukázka EEAddIn: doplněk vyhodnocovacího filtru výrazů ladění](https://msdn.microsoft.com/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## <a name="see-also"></a>Viz také  
 [Použití atributu používání DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Použití atributu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Kukátko a QuickWatch okna](../debugger/watch-and-quickwatch-windows.md)   
 [Rozšíření ladění pomocí atributů zobrazení ladicího programu](https://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)
