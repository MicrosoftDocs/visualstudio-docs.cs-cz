---
title: 'CA1021: Vyhněte se výstupním parametrům | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3f90b4487824695fe0045c06638679607e4464b3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917662"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021: Vyhněte se výstupním parametrům
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|Kategorie|Microsoft.Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Veřejná nebo chráněná metoda veřejného typu má `out` parametru.

## <a name="rule-description"></a>Popis pravidla
 Předávání typů odkazem (pomocí `out` nebo `ref`) vyžaduje zkušenosti s ukazateli, pochopení, jak se liší typy hodnot a odkazové typy a metody s více návratových zpracování. Také rozdíl mezi `out` a `ref` parametrů není běžně chápán.

 Při "podle odkazu" je předán odkaz na typ, metodu v úmyslu použít parametr a vrátí jinou instanci objektu. Předávání odkazem odkazový typ se označuje také jako pomocí dvojitých ukazatel, ukazatel na ukazatel nebo dvojitou dereferenci. Pomocí výchozí konvence volání, což je předat "value", přijímá parametr, který již má odkazový typ ukazatel na objekt. Ukazatel, nikoli objekt, na kterou odkazuje, je předán podle hodnoty. Předejte jako hodnota znamená, že metoda nelze změnit tak, aby odkazoval na nové instanci typu odkazu ukazatel. Můžete však změnit obsah objektu, na kterou odkazuje. Pro většinu aplikací je dostačující a provede požadované chování.

 Pokud metoda musí vracet jinou instanci, použijte k tomu návratovou hodnotu metody. Zobrazit <xref:System.String?displayProperty=fullName> třídy pro celou řadu metod, které pracují na řetězce a vrátí novou instanci řetězce. Když se tento model používá, volající musíte rozhodnout, jestli se zachová původní objekt.

 I když vrácené hodnoty jsou běžné a nejčastěji používá správné použití `out` a `ref` parametry vyžaduje zprostředkující návrhu a dovednosti kódování. Knihovna architektům, kteří návrhu pro širokou veřejnost, by neměli očekávat uživatelům pracovat s `out` nebo `ref` parametry.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, která je způsobeno tím, typ hodnoty, mají metoda vrátit objekt jako jeho návratovou hodnotu. Metoda musí vracet více hodnot, změnit návrh jej vrátí jednu instanci objektu, který obsahuje hodnoty.

 Chcete-li opravit porušení tohoto pravidla, která je způsobeno tím, typ odkazu, zajistěte, aby požadované chování vrácení nové instance odkazu. Pokud se jedná, používejte metodu k tomu jeho návratovou hodnotu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla. Tento návrh však může způsobit problémy se použitelnost.

## <a name="example"></a>Příklad
 Následující knihovny ukazuje dvě implementace třídy, která generuje odpovědi na zpětnou vazbu od uživatele. První provedení (`BadRefAndOut`) vynutí knihovny uživatele ke správě tři návratové hodnoty. Druhý implementace (`RedesignedRefAndOut`) zjednodušuje činnost koncového uživatele tak, že vrací instanci třídy kontejneru (`ReplyData`), která zvládne správu dat jako jeden celek.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>Příklad
 Následující aplikace ukazuje možnosti uživatele. Volání přepracovaný knihovny (`UseTheSimplifiedClass` metoda) je jednodušší, a snadno se spravuje informace vrácené metodou. Je stejný jako výstup ze dvou metod.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>Příklad
 Knihovna následující příklad ukazuje, jak `ref` parametrů pro typy odkazů se používají a zobrazuje lepší způsob, jak implementovat tuto funkci.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>Příklad
 Následující aplikace volá při každé metody v knihovně k předvedení chování.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 Tento příklad vytvoří následující výstup.

 **Změna ukazatel - předán podle hodnoty:**
**12345**
**12345**
**změna ukazatel - předány podle odkazu:** 
 ** 12345**
**12345 ABCDE**
**předávání návratovou hodnotu:**
**12345 ABCDE**
## <a name="try-pattern-methods"></a>Zkuste vzor metody

### <a name="description"></a>Popis
 Metody, které implementují **zkuste\<něco >** vzorku, jako například <xref:System.Int32.TryParse%2A?displayProperty=fullName>, nevyvolávejte toto porušení. Následující příklad ukazuje strukturu (typ hodnoty), který implementuje <xref:System.Int32.TryParse%2A?displayProperty=fullName> metody.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Design.TryPattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TryPattern/cs/FxCop.Design.TryPattern.cs#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1045: Nepředávejte typy odkazem](../code-quality/ca1045-do-not-pass-types-by-reference.md)



