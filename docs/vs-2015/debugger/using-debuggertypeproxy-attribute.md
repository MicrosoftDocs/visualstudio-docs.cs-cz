---
title: Použití atributu používání DebuggerTypeProxy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerTypeProxyAttribute class
- DebuggerTypeProxy attribute
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f6e349dd5bea4e0d89c31864960a5438d1e2b13f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684077"
---
# <a name="using-debuggertypeproxy-attribute"></a>Používání atributu DebuggerTypeProxy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DebuggerTypeProxyAttribute –] (assetId:///T: System. Diagnostics. DebuggerTypeProxyAttribute –? qualifyHint = false&autoupgrade = true) určuje proxy nebo místní typ pro typ a mění způsob, jakým se typ zobrazuje v oknech ladicího programu. Pokud zobrazíte proměnnou, která má proxy server, proxy server je v části pro původní typ v **zobrazení**. Okno proměnné ladicího programu zobrazuje pouze veřejné členy typu proxy serveru. Soukromé členy nejsou zobrazeny.  
  
 Tento atribut lze použít pro:  
  
- Struktury  
  
- Třídy  
  
- Sestavení  
  
  Třída typu proxy musí mít konstruktor, který přebírá argument typu, který bude server nahrazen. Ladicí program vytvoří novou instanci třídy typu proxy pokaždé, když potřebuje zobrazit proměnnou cílového typu. To může mít vliv na výkon. V důsledku toho byste neměli v konstruktoru dělat žádné další práce, než je nezbytně nutné.  
  
  Pro minimalizaci sankcí za výkon vyhodnocovací filtr výrazů neověřuje atributy na proxy zobrazení typu, pokud typ není rozbalen uživatelem kliknutím na symbol + v okně ladicího programu nebo pomocí <xref:System.Diagnostics.DebuggerBrowsableAttribute> . Proto byste neměli umístit atributy na samotný typ zobrazení. Atributy mohou a by měly být použity v těle typu zobrazení.  
  
  Je vhodné, aby proxy typ byl privátní vnořenou třídou v rámci třídy, které cílí na atribut. To umožňuje snadno získat přístup k interním členům.  
  
  Pokud <xref:System.Diagnostics.DebuggerTypeProxyAttribute> je použita na úrovni sestavení, `Target` parametr určuje typ, který bude server nahrazen.  
  
  Příklad použití tohoto atributu spolu s <xref:System.Diagnostics.DebuggerDisplayAttribute> a <xref:System.Diagnostics.DebuggerTypeProxyAttribute> naleznete v tématu[using the DebuggerDisplay Attribute](../debugger/using-the-debuggerdisplay-attribute.md).  
  
## <a name="using-generics-with-debuggertypeproxy"></a>Použití generických typů s používání DebuggerTypeProxy  
 Podpora pro obecné typy je omezená. V jazyce C# `DebuggerTypeProxy` podporuje pouze otevřené typy. Otevřený typ, označovaný také jako nekonstruovaný typ, je obecný typ, který nebyl vytvořen s argumenty pro jeho parametry typu. Uzavřené typy, označované také jako konstruované typy, nejsou podporovány.  
  
 Syntaxe pro otevřený typ vypadá takto:  
  
 `Namespace.TypeName<,>`  
  
 Použijete-li obecný typ jako cíl v `DebuggerTypeProxy` , je nutné použít tuto syntaxi. `DebuggerTypeProxy`Mechanismus odvodí parametry typu pro vás.  
  
 Další informace o otevřených a uzavřených typech v jazyce C# naleznete v tématu [specifikace jazyka C#](https://msdn.microsoft.com/library/e5d5a5cc-636b-4bff-b9c8-a8edc6207c22), 20.5.2 otevřené a uzavřené typy oddílu.  
  
 Visual Basic nemá syntaxi otevřeného typu, takže nemůžete v Visual Basic provádět stejné věci. Místo toho je nutné použít řetězcovou reprezentaci názvu otevřeného typu.  
  
 `"Namespace.TypeName'2"`  
  
## <a name="see-also"></a>Viz také  
 [Použití atributu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
  [Rozšíření ladění pomocí atributů zobrazení ladicího programu](https://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)
