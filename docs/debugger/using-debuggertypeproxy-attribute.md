---
title: Používání atributu DebuggerTypeProxy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ab54c754fdc3b7ae773e71a96936a1c17c6bc5ce
ms.sourcegitcommit: 9571742f4a808c75b1034aa72fc24b54bc50692e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2018
ms.locfileid: "49411063"
---
# <a name="using-debuggertypeproxy-attribute"></a>Používání atributu DebuggerTypeProxy

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> Určuje proxy server nebo stand-in pro typ a provedené změny tak, jak typ se zobrazí v oknech ladicího programu. Pokud zobrazíte proměnnou, která má proxy server, proxy zastupuje původní typ v **zobrazit**. V okně proměnné ladicího programu se zobrazí pouze veřejné členy typu proxy. Soukromé členy nejsou zobrazeny.

Tento atribut lze použít pro:

- Struktury
- Třídy
- Sestavení

Typ třídy proxy server musí mít konstruktor, který přebírá argument typu, který nahradí proxy serveru. Ladicí program vytvoří novou instanci třídy proxy pokaždé, když je potřeba zobrazení proměnné cílového typu. To může mít vliv na výkon. V důsledku toho by neměla provést žádné další práci v konstruktoru, než je nezbytně nutné.

Chcete-li minimalizovat snížení výkonu, vyhodnocovací filtr výrazů nezkoumá atributy u proxy zobrazení typu Pokud typ rozbalen uživatel kliknutím + symbol v okně ladicího programu, nebo pomocí <xref:System.Diagnostics.DebuggerBrowsableAttribute>. Proto by neměl umístit atributy na samotném zobrazení typu. Atributy lze a by měl být použit v těle typu zobrazení.

Je vhodné pro proxy server typů být privátní vnořené třídy v rámci třídy, které cíle atributů. To umožňuje snadno získat přístup vnitřní členy.

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> je možné zdědit, takže pokud není zadán proxy server typů v základní třídě bude platit pro všechny odvozené třídy, pokud tyto odvozené třídy zadat své vlastní proxy server typů.

Pokud <xref:System.Diagnostics.DebuggerTypeProxyAttribute> se používá na úrovni sestavení `Target` parametr určuje typ, který nahradí proxy serveru.

Příklad, jak používat tento atribut spolu s <xref:System.Diagnostics.DebuggerDisplayAttribute> a <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, naleznete v tématu[pomocí atributu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).

## <a name="using-generics-with-debuggertypeproxy"></a>Použití obecných typů pomocí DebuggerTypeProxy

Podpora je omezená. Pro jazyk C# `DebuggerTypeProxy` typů podporuje pouze otevřít. Otevřený typ, zkratka typu unconstructed je obecného typu, která nebyla vytvořena instance s argumenty pro svoje parametry typu. Uzavřené typy zkratka sestavené typy nejsou podporované.

Syntaxe pro otevřený typ. vypadá takto:

`Namespace.TypeName<,>`

Pokud jako cíl v použití obecného typu `DebuggerTypeProxy`, je nutné použít tuto syntaxi. `DebuggerTypeProxy` Mechanismus parametry typu odvodí z nich za vás.

Další informace o typech otevřené a uzavřené v jazyce C# najdete v článku [specifikace jazyka C#](/dotnet/csharp/language-reference/language-specification), otevřete část 20.5.2 a uzavření typů.

Visual Basic nemá otevřeného typu syntaxe proto nelze provést totéž v jazyce Visual Basic. Místo toho musíte použít řetězec představující název otevřeného typu.

`"Namespace.TypeName'2"`

## <a name="see-also"></a>Viz také

- [Používání atributu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Vytváření vlastních zobrazení .managed objektů](../debugger/create-custom-views-of-dot-managed-objects.md)
- [Rozšíření ladění pomocí atributů zobrazení ladicího programu](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
