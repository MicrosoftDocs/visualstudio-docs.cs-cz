---
title: 'CA1021: Vyhněte se výstupním parametrům'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e333e53fea1b965b250bdc97924e93728d55805a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236182"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021: Vyhněte se výstupním parametrům

|||
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|Kategorie|Microsoft.Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Veřejná nebo chráněná metoda ve veřejném typu má `out` parametr.

## <a name="rule-description"></a>Popis pravidla
Předávání typů odkazem (pomocí `out` nebo `ref`) vyžaduje zkušenosti s ukazateli, porozumění způsobu, jakým se liší typy hodnot a typy odkazů, a metody zpracování s více návratových hodnot. Také rozdíl mezi `out` parametry a `ref` není široce srozumitelný.

Pokud je odkazový typ předán "odkazem", metoda zamýšlí použít parametr pro návrat jiné instance objektu. Předání typu odkazu odkazem je také známo, že používá dvojité ukazatele, ukazatel na ukazatel nebo dvojitou indirekce. Pomocí výchozí konvence volání, která je předána "podle hodnoty", parametr, který přebírá odkazový typ již obdrží ukazatel na objekt. Ukazatel, nikoli objekt, na který odkazuje, je předán podle hodnoty. Hodnota Pass by znamená, že metoda nemůže změnit ukazatel tak, aby odkazovala na novou instanci typu odkazu. Může však změnit obsah objektu, na který odkazuje. Pro většinu aplikací je to dostačující a vede k požadovanému chování.

Pokud metoda musí vracet jinou instanci, použijte k tomu vrácenou hodnotu metody. Podívejte se <xref:System.String?displayProperty=fullName> na třídu pro různé metody, které pracují s řetězci a vracejí novou instanci řetězce. Při použití tohoto modelu musí volající rozhodnout, zda je původní objekt zachován.

I když návratové hodnoty jsou maloobchodech a silně využívány, `out` správné `ref` použití parametrů a vyžaduje pokročilou návrh a kódování. Architekti knihoven, kteří navrhují pro obecnou cílovou skupinu, by neměli očekávat `out` , `ref` že uživatelé budou hlavní pracovat s parametry nebo.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, které je způsobeno typem hodnoty, je třeba, aby metoda vracela objekt jako vrácenou hodnotu. Pokud metoda musí vracet více hodnot, změňte její návrh a vraťte jednu instanci objektu, který obsahuje hodnoty.

Chcete-li opravit porušení tohoto pravidla, která je způsobena odkazovým typem, ujistěte se, že požadované chování je vrácení nové instance odkazu. Pokud je, metoda by k tomu měla použít jeho návratovou hodnotu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Z tohoto pravidla je bezpečné potlačit upozornění. Tento návrh ale může způsobit problémy s použitelností.

## <a name="example"></a>Příklad
Následující knihovna ukazuje dvě implementace třídy, které generují odpovědi na zpětnou vazbu uživatele. První implementace (`BadRefAndOut`) vynutí, aby uživatel knihovny spravoval tři návratové hodnoty. Druhá implementace (`RedesignedRefAndOut`) zjednodušuje uživatelské prostředí vrácením instance třídy kontejneru (`ReplyData`), která spravuje data jako jednu jednotku.

[!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]

## <a name="example"></a>Příklad
Následující aplikace znázorňuje prostředí uživatele. Volání přepracované knihovny (`UseTheSimplifiedClass` metoda) je jednodušší a informace vrácené metodou lze snadno spravovat. Výstup ze dvou metod je stejný.

[!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]

## <a name="example"></a>Příklad
Následující příklad knihovny ukazuje, jak `ref` se používají parametry pro typy odkazů, a ukazuje lepší způsob implementace této funkce.

[!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]

## <a name="example"></a>Příklad
Následující aplikace volá jednotlivé metody v knihovně k demonstraci chování.

[!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_4.cs)]

Tento příklad vytvoří následující výstup:

```txt
Changing pointer - passed by value:
12345
12345
Changing pointer - passed by reference:
12345
12345 ABCDE
Passing by return value:
12345 ABCDE
```

## <a name="try-pattern-methods"></a>Vyzkoušet metody vzoru

### <a name="description"></a>Popis
Metody, které implementují <xref:System.Int32.TryParse%2A?displayProperty=fullName>vzorec **Try\<>** , například, nevyvolávají toto porušení. Následující příklad ukazuje strukturu (typ hodnoty), která implementuje <xref:System.Int32.TryParse%2A?displayProperty=fullName> metodu.

### <a name="code"></a>Kód
[!code-csharp[FxCop.Design.TryPattern#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_5.cs)]

## <a name="related-rules"></a>Související pravidla
[CA1045: Nepředávejte typy odkazem](../code-quality/ca1045-do-not-pass-types-by-reference.md)