---
title: Zobrazení vlastního typu pomocí třídy DebuggerTypeProxy | Microsoft Docs
description: Pomocí instance DebuggerTypeProxyAttribute můžete zadat proxy (stand-in) pro typ a změnit způsob zobrazení typu v oknech ladicího programu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerTypeProxyAttribute class
- DebuggerTypeProxy attribute
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 532850f8bb4ac6198481188c2a57a8db15a13873
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389277"
---
# <a name="tell-the-debugger-what-type-to-show-using-debuggertypeproxy-attribute-c-visual-basic-ccli"></a>Sdělte ladicímu programu, jaký typ se má zobrazit, pomocí atributu DebuggerTypeProxy (C#, Visual Basic, C++/CLI)

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> určuje proxy nebo stand-in pro typ a změní způsob zobrazení typu v oknech ladicího programu. Když zobrazíte proměnnou, která má proxy server, proxy zastupuje původní typ v **zobrazení**. V okně proměnné ladicího programu se zobrazují pouze veřejné členy typu proxy. Soukromé členy se nezobrazují.

Tento atribut lze použít pro:

- Struktury
- Třídy
- Sestavení

> [!NOTE]
> Pro nativní kód je tento atribut podporován pouze v kódu C++/CLI.

Třída typu proxy musí mít konstruktor, který přebírá argument typu, který bude proxy server nahradit. Ladicí program vytvoří novou instanci třídy typu proxy pokaždé, když potřebuje zobrazit proměnnou cílového typu. To může mít vliv na výkon. V důsledku toho byste neměli v konstruktoru dělat nic dalšího, než je nezbytně nutné.

Aby se minimalizovaly penalizování výkonu, vyhodnocovač výrazů neprozkoumá atributy na zobrazované proxy serveru typu, pokud uživatel nerozšířuje typ kliknutím na symbol + v okně ladicího programu nebo použitím <xref:System.Diagnostics.DebuggerBrowsableAttribute> . Proto byste neměli umisovat atributy do samotného typu zobrazení. Atributy lze a by měly být použity v těle zobrazovaný typ.

Je vhodné, aby proxy typ byl privátní vnořenou třídou v rámci třídy, na kterou cílí atribut . To umožňuje snadný přístup k interním členům.

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> může být zděděn, takže pokud je v základní třídě zadán proxy typ, použije se pro všechny odvozené třídy, pokud tyto odvozené třídy neurčí svůj vlastní typ proxy.

Pokud <xref:System.Diagnostics.DebuggerTypeProxyAttribute> se používá na úrovni sestavení, parametr určuje `Target` typ, který bude proxy server nahradit.

Příklad použití tohoto atributu spolu s a najdete v <xref:System.Diagnostics.DebuggerDisplayAttribute> <xref:System.Diagnostics.DebuggerTypeProxyAttribute> tématu Použití [atributu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).

## <a name="using-generics-with-debuggertypeproxy"></a>Použití obecných typů s DebuggerTypeProxy

Podpora obecných typů je omezená. V jazyce C# `DebuggerTypeProxy` podporuje pouze otevřené typy. Otevřený typ, také nazývaný nekonstruovaný typ, je obecný typ, který nebyl vytvořen s argumenty pro jeho parametry typu. Uzavřené typy, také nazývané konstruované typy, nejsou podporovány.

Syntaxe otevřeného typu vypadá takhle:

`Namespace.TypeName<,>`

Pokud jako cíl v použijete obecný `DebuggerTypeProxy` typ, musíte použít tuto syntaxi. Mechanismus `DebuggerTypeProxy` odvodí parametry typu za vás.

Další informace o otevřených a uzavřených typech v jazyce C# najdete ve specifikaci jazyka [C#](/dotnet/csharp/language-reference/language-specification)v části 20.5.2 Otevřené a uzavřené typy.

Visual Basic nemá otevřenou syntaxi typu, takže v tomto případě nemůžete Visual Basic. Místo toho musíte použít řetězcovou reprezentaci názvu otevřeného typu.

`"Namespace.TypeName'2"`

## <a name="see-also"></a>Viz také

- [Používání atributu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Vytváření vlastních zobrazení spravovaných objektů](../debugger/create-custom-views-of-managed-objects.md)
- [Rozšíření ladění pomocí atributů zobrazení ladicího programu](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
