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
ms.openlocfilehash: 2b07c987bdaa2d037c8c6dc95a37d5e77069dea5
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449333"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021: Vyhněte se výstupním parametrům

|||
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|Kategorie|Microsoft. Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Veřejná nebo chráněná metoda ve veřejném typu má parametr `out`.

## <a name="rule-description"></a>Popis pravidla
Předávání typů odkazem (pomocí `out` nebo `ref`) vyžaduje zkušenosti s ukazateli, porozumění způsobu, jakým se liší typy hodnot a referenční typy, a metody zpracování s více návratových hodnot. Rozdíl mezi parametry `out` a `ref` se navíc nepovažují za široce.

Pokud je odkazový typ předán "odkazem", metoda zamýšlí použít parametr pro návrat jiné instance objektu. Předání typu odkazu odkazem je také známo, že používá dvojité ukazatele, ukazatel na ukazatel nebo dvojitou indirekce. Pomocí výchozí konvence volání, která je předána "podle hodnoty", parametr, který přebírá odkazový typ již obdrží ukazatel na objekt. Ukazatel, nikoli objekt, na který odkazuje, je předán podle hodnoty. Hodnota Pass by znamená, že metoda nemůže změnit ukazatel tak, aby odkazovala na novou instanci typu odkazu. Může však změnit obsah objektu, na který odkazuje. Pro většinu aplikací je to dostačující a vede k požadovanému chování.

Pokud metoda musí vracet jinou instanci, použijte k tomu vrácenou hodnotu metody. V případě různých metod, které pracují s řetězci a návratové nové instance řetězce, se podívejte na třídu <xref:System.String?displayProperty=fullName>. Při použití tohoto modelu musí volající rozhodnout, zda je původní objekt zachován.

I když jsou návratové hodnoty maloobchodech a silně využívány, správné použití parametrů `out` a `ref` vyžaduje průběžné navrhování a kódování. Architekti knihoven, kteří navrhují pro obecnou cílovou skupinu, by neměli očekávat, že uživatelé budou hlavní pracovat s parametry `out` nebo `ref`.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, které je způsobeno typem hodnoty, je třeba, aby metoda vracela objekt jako vrácenou hodnotu. Pokud metoda musí vracet více hodnot, změňte její návrh a vraťte jednu instanci objektu, který obsahuje hodnoty.

Chcete-li opravit porušení tohoto pravidla, která je způsobena odkazovým typem, ujistěte se, že požadované chování je vrácení nové instance odkazu. Pokud je, metoda by k tomu měla použít jeho návratovou hodnotu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Z tohoto pravidla je bezpečné potlačit upozornění. Tento návrh ale může způsobit problémy s použitelností.

## <a name="example"></a>Příklad
Následující knihovna ukazuje dvě implementace třídy, které generují odpovědi na zpětnou vazbu uživatele. První implementace (`BadRefAndOut`) přinutí uživateli knihovny spravovat tři návratové hodnoty. Druhá implementace (`RedesignedRefAndOut`) zjednodušuje uživatelské prostředí vrácením instance třídy kontejneru (`ReplyData`), která spravuje data jako jednu jednotku.

[!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]

## <a name="example"></a>Příklad
Následující aplikace znázorňuje prostředí uživatele. Volání přepracované knihovny (metoda `UseTheSimplifiedClass`) je jednodušší a informace vrácené metodou se dají snadno spravovat. Výstup ze dvou metod je stejný.

[!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]

## <a name="example"></a>Příklad
Následující příklad knihovny ukazuje, jak se používají parametry `ref` pro typy odkazů, a ukazuje lepší způsob implementace této funkce.

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
Metody, které implementují vzor **Try @ no__t-1Something >** , jako je například <xref:System.Int32.TryParse%2A?displayProperty=fullName>, nevyvolávají toto porušení. Následující příklad ukazuje strukturu (typ hodnoty), která implementuje metodu <xref:System.Int32.TryParse%2A?displayProperty=fullName>.

### <a name="code"></a>Kód
[!code-csharp[FxCop.Design.TryPattern#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_5.cs)]

## <a name="related-rules"></a>Související pravidla
[CA1045: Nepředávejte typy odkazem](../code-quality/ca1045-do-not-pass-types-by-reference.md)
