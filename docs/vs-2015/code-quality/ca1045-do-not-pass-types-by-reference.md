---
title: 'CA1045: nepředávejte typy odkazem | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 259e0d17ccf71518759ac192ee87a6ef5b921b23
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668284"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: Nepředávejte typy odkazem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPassTypesByReference|
|CheckId|CA1045|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Veřejná nebo chráněná metoda ve veřejném typu má parametr `ref`, který přebírá primitivní typ, odkazový typ nebo typ hodnoty, který není jedním z vestavěných typů.

## <a name="rule-description"></a>Popis pravidla
 Předávání typů odkazem (pomocí `out` nebo `ref`) vyžaduje zkušenosti s ukazateli, porozumění způsobu, jakým se liší typy hodnot a typy odkazů, a metody zpracování, které mají více vrácených hodnot. Rozdíl mezi parametry `out` a `ref` se navíc nepovažují za široce.

 Pokud je odkazový typ předán "odkazem", metoda zamýšlí použít parametr pro návrat jiné instance objektu. (Předání typu odkazu odkazem je také známo, že používá dvojité ukazatel, ukazatel na ukazatel nebo dvojitou indirekce.) Pomocí výchozí konvence volání, která je předána hodnotou, parametr, který přebírá odkazový typ, již obdrží ukazatel na objekt. Ukazatel, nikoli objekt, na který odkazuje, je předán podle hodnoty. Předání hodnotou znamená, že metoda nemůže změnit ukazatel tak, aby odkazovala na novou instanci typu odkazu, ale může změnit obsah objektu, na který odkazuje. Pro většinu aplikací je to dostačující a poskytuje požadované chování.

 Pokud metoda musí vracet jinou instanci, použijte k tomu vrácenou hodnotu metody. V případě různých metod, které pracují s řetězci a návratové nové instance řetězce, se podívejte na třídu <xref:System.String?displayProperty=fullName>. Pomocí tohoto modelu je ponechán volajícím, aby se rozhodlo, zda je původní objekt zachován.

 I když jsou návratové hodnoty maloobchodech a silně využívány, správné použití parametrů `out` a `ref` vyžaduje průběžné navrhování a kódování. Architekti knihoven, kteří navrhují pro obecnou cílovou skupinu, by neměli očekávat, že uživatelé budou hlavní pracovat s parametry `out` nebo `ref`.

> [!NOTE]
> Při práci s parametry, které jsou velké struktury, mohou další prostředky, které jsou požadovány ke kopírování těchto struktur, způsobit vliv na výkon při předání hodnoty. V těchto případech je možné zvážit použití parametrů `ref` nebo `out`.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, které je způsobeno typem hodnoty, je třeba, aby metoda vracela objekt jako vrácenou hodnotu. Pokud metoda musí vracet více hodnot, změňte její návrh a vraťte jednu instanci objektu, který obsahuje hodnoty.

 Chcete-li opravit porušení tohoto pravidla, která je způsobena odkazovým typem, ujistěte se, že požadované chování je vrácení nové instance odkazu. Pokud je, metoda by k tomu měla použít jeho návratovou hodnotu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění od tohoto pravidla; Tento návrh ale může způsobit problémy s použitelností.

## <a name="example"></a>Příklad
 Následující knihovna ukazuje dvě implementace třídy, které generují odpovědi na zpětnou vazbu uživatele. První implementace (`BadRefAndOut`) přinutí uživateli knihovny spravovat tři návratové hodnoty. Druhá implementace (`RedesignedRefAndOut`) zjednodušuje uživatelské prostředí vrácením instance třídy kontejneru (`ReplyData`), která spravuje data jako jednu jednotku.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>Příklad
 Následující aplikace znázorňuje prostředí uživatele. Volání přepracované knihovny (metoda `UseTheSimplifiedClass`) je jednodušší a informace, které jsou vráceny metodou, lze snadno spravovat. Výstup ze dvou metod je stejný.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>Příklad
 Následující příklad knihovny ukazuje, jak se používají parametry `ref` pro typy odkazů, a ukazuje lepší způsob implementace této funkce.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>Příklad
 Následující aplikace volá jednotlivé metody v knihovně k demonstraci chování.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 Tento příklad vytvoří následující výstup.

 **Mění se ukazatel – předává se hodnota:** 
**12345** 
**12345** 
**Změna ukazatele-předané odkazem:** 
**12345** 
**12345 abcde** 1**předávání návratovou hodnotou: **3**12345 abcde**
## <a name="related-rules"></a>Související pravidla
 [CA1021: Vyhněte se výstupním parametrům](../code-quality/ca1021-avoid-out-parameters.md)
