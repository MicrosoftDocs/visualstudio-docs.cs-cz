---
title: 'CA1021: Vyhněte se parametrům | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f8f1b0c17fe9135bf534b9f30bf4e54c8c286ada
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546689"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021: Vyhněte se výstupním parametrům
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Veřejná nebo chráněná metoda ve veřejném typu má `out` parametr.

## <a name="rule-description"></a>Popis pravidla
 Předávání typů odkazem (pomocí `out` nebo `ref` ) vyžaduje zkušenosti s ukazateli, porozumění způsobu, jakým se liší typy hodnot a typy odkazů, a metody zpracování s více návratových hodnot. Také rozdíl mezi `out` parametry a není `ref` široce srozumitelný.

 Pokud je odkazový typ předán "odkazem", metoda zamýšlí použít parametr pro návrat jiné instance objektu. Předání typu odkazu odkazem je také známo, že používá dvojité ukazatele, ukazatel na ukazatel nebo dvojitou indirekce. Pomocí výchozí konvence volání, která je předána "podle hodnoty", parametr, který přebírá odkazový typ již obdrží ukazatel na objekt. Ukazatel, nikoli objekt, na který odkazuje, je předán podle hodnoty. Hodnota Pass by znamená, že metoda nemůže změnit ukazatel tak, aby odkazovala na novou instanci typu odkazu. Může však změnit obsah objektu, na který odkazuje. Pro většinu aplikací je to dostačující a vede k požadovanému chování.

 Pokud metoda musí vracet jinou instanci, použijte k tomu vrácenou hodnotu metody. Podívejte se na <xref:System.String?displayProperty=fullName> třídu pro různé metody, které pracují s řetězci a vracejí novou instanci řetězce. Při použití tohoto modelu musí volající rozhodnout, zda je původní objekt zachován.

 I když návratové hodnoty jsou maloobchodech a silně využívány, správné použití `out` `ref` parametrů a vyžaduje pokročilou návrh a kódování. Architekti knihoven, kteří navrhují pro obecnou cílovou skupinu, by neměli očekávat, že uživatelé budou hlavní pracovat s `out` `ref` parametry nebo.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, které je způsobeno typem hodnoty, je třeba, aby metoda vracela objekt jako vrácenou hodnotu. Pokud metoda musí vracet více hodnot, změňte její návrh a vraťte jednu instanci objektu, který obsahuje hodnoty.

 Chcete-li opravit porušení tohoto pravidla, která je způsobena odkazovým typem, ujistěte se, že požadované chování je vrácení nové instance odkazu. Pokud je, metoda by k tomu měla použít jeho návratovou hodnotu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Z tohoto pravidla je bezpečné potlačit upozornění. Tento návrh ale může způsobit problémy s použitelností.

## <a name="example"></a>Příklad
 Následující knihovna ukazuje dvě implementace třídy, které generují odpovědi na zpětnou vazbu uživatele. První implementace ( `BadRefAndOut` ) vynutí, aby uživatel knihovny spravoval tři návratové hodnoty. Druhá implementace ( `RedesignedRefAndOut` ) zjednodušuje uživatelské prostředí vrácením instance třídy kontejneru ( `ReplyData` ), která spravuje data jako jednu jednotku.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>Příklad
 Následující aplikace znázorňuje prostředí uživatele. Volání přepracované knihovny ( `UseTheSimplifiedClass` Metoda) je jednodušší a informace vrácené metodou lze snadno spravovat. Výstup ze dvou metod je stejný.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>Příklad
 Následující příklad knihovny ukazuje, jak `ref` se používají parametry pro typy odkazů, a ukazuje lepší způsob implementace této funkce.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>Příklad
 Následující aplikace volá jednotlivé metody v knihovně k demonstraci chování.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 Tento příklad vytvoří následující výstup.

 **Mění se ukazatel – předává se hodnota:** 
 **12345** 
 **12345** 
 **Mění se ukazatel – předaný odkazem:** 
 **12345** 
 **12345 abcde** 
 **Předávání návratovou hodnotou:** 
 **12345 abcde**
## <a name="try-pattern-methods"></a>Vyzkoušet metody vzoru

### <a name="description"></a>Popis
 Metody, které implementují model **Try \<Something> ** , například <xref:System.Int32.TryParse%2A?displayProperty=fullName> , nevyvolávají toto porušení. Následující příklad ukazuje strukturu (typ hodnoty), která implementuje <xref:System.Int32.TryParse%2A?displayProperty=fullName> metodu.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Design.TryPattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TryPattern/cs/FxCop.Design.TryPattern.cs#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1045: Nepředávejte typy odkazem](../code-quality/ca1045-do-not-pass-types-by-reference.md)
