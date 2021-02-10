---
title: Zobrazit vlastní typ pomocí používání DebuggerTypeProxy | Microsoft Docs
description: Použijte instanci DebuggerTypeProxyAttribute – k určení proxy (pro) pro určitý typ pro změnu způsobu zobrazení typu v ladicím programu.
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
ms.openlocfilehash: 2fdd0b67075a66663146d706d8f82e8c5d9f76e2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940537"
---
# <a name="tell-the-debugger-what-type-to-show-using-debuggertypeproxy-attribute-c-visual-basic-ccli"></a>Sdělte ladicímu programu, jaký typ se má zobrazit pomocí atributu používání DebuggerTypeProxy (C#, Visual Basic, C++/CLI).

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> Určuje proxy server nebo jeho nezávisle pro typ a mění způsob, jakým se typ zobrazuje v oknech ladicího programu. Pokud zobrazíte proměnnou, která má proxy server, proxy server je v části pro původní typ v **zobrazení**. Okno proměnné ladicího programu zobrazuje pouze veřejné členy typu proxy serveru. Soukromé členy nejsou zobrazeny.

Tento atribut lze použít pro:

- Struktury
- Třídy
- Sestavení

> [!NOTE]
> Pro nativní kód je tento atribut podporován pouze v kódu jazyka C++/CLI.

Třída typu proxy musí mít konstruktor, který přebírá argument typu, který bude server nahrazen. Ladicí program vytvoří novou instanci třídy typu proxy pokaždé, když potřebuje zobrazit proměnnou cílového typu. To může mít vliv na výkon. V důsledku toho byste neměli v konstruktoru dělat žádné další práce, než je nezbytně nutné.

Pro minimalizaci sankcí za výkon vyhodnocovací filtr výrazů neověřuje atributy na proxy zobrazení typu, pokud typ není rozbalen uživatelem kliknutím na symbol + v okně ladicího programu nebo pomocí <xref:System.Diagnostics.DebuggerBrowsableAttribute> . Proto byste neměli umístit atributy na samotný typ zobrazení. Atributy mohou a by měly být použity v těle typu zobrazení.

Je vhodné, aby proxy typ byl privátní vnořenou třídou v rámci třídy, které cílí na atribut. To umožňuje snadno získat přístup k interním členům.

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> může být zděděno, takže pokud je typ proxy serveru zadán v základní třídě, bude platit pro všechny odvozené třídy, pokud tyto odvozené třídy neurčí svůj vlastní typ proxy.

Pokud <xref:System.Diagnostics.DebuggerTypeProxyAttribute> je použita na úrovni sestavení, `Target` parametr určuje typ, který bude server nahrazen.

Příklad použití tohoto atributu spolu s <xref:System.Diagnostics.DebuggerDisplayAttribute> a <xref:System.Diagnostics.DebuggerTypeProxyAttribute> naleznete v tématu[using the DebuggerDisplay Attribute](../debugger/using-the-debuggerdisplay-attribute.md).

## <a name="using-generics-with-debuggertypeproxy"></a>Použití generických typů s používání DebuggerTypeProxy

Podpora pro obecné typy je omezená. V jazyce C# `DebuggerTypeProxy` podporuje pouze otevřené typy. Otevřený typ, označovaný také jako nekonstruovaný typ, je obecný typ, který nebyl vytvořen s argumenty pro jeho parametry typu. Uzavřené typy, označované také jako konstruované typy, nejsou podporovány.

Syntaxe pro otevřený typ vypadá takto:

`Namespace.TypeName<,>`

Použijete-li obecný typ jako cíl v `DebuggerTypeProxy` , je nutné použít tuto syntaxi. `DebuggerTypeProxy`Mechanismus odvodí parametry typu pro vás.

Další informace o otevřených a uzavřených typech v jazyce C# naleznete v tématu [specifikace jazyka C#](/dotnet/csharp/language-reference/language-specification), 20.5.2 otevřené a uzavřené typy oddílu.

Visual Basic nemá syntaxi otevřeného typu, takže nemůžete v Visual Basic provádět stejné věci. Místo toho je nutné použít řetězcovou reprezentaci názvu otevřeného typu.

`"Namespace.TypeName'2"`

## <a name="see-also"></a>Viz také

- [Používání atributu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Vytváření vlastních zobrazení spravovaných objektů](../debugger/create-custom-views-of-managed-objects.md)
- [Rozšíření ladění pomocí atributů zobrazení ladicího programu](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
