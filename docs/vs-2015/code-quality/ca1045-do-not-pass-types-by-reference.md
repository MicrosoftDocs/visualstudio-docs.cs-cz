---
title: 'CA1045: Nepředávejte typy odkazem. | Dokumentace Microsoftu'
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
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1aa9077a0d27c105cd7008d550a4315ce8daf91a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836564"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: Nepředávejte typy odkazem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPassTypesByReference|
|CheckId|CA1045|
|Kategorie|Microsoft.Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Veřejná nebo chráněná metoda veřejného typu má `ref` parametr, který přijímá primitivní typ, typ odkazu nebo hodnotový typ, který není jeden z předdefinovaných typů.

## <a name="rule-description"></a>Popis pravidla
 Předávání typů odkazem (pomocí `out` nebo `ref`) vyžaduje zkušenosti s ukazateli, pochopení, jak se liší typy hodnot a typy odkazů a zpracování metody, které mají více návratových hodnot. Také rozdíl mezi `out` a `ref` parametrů není běžně chápán.

 Při "podle odkazu" je předán odkaz na typ, metodu v úmyslu použít parametr a vrátí jinou instanci objektu. (Předávání odkazem odkazový typ se taky říká pomocí dvojitých ukazatel, ukazatel na ukazatel nebo dvojitou dereferenci.) Výchozí konvence volání, což je předat "value", pomocí parametru, která přebírá typ odkazu ještě přijímá ukazatel na objekt. Ukazatel, nikoli objekt, na kterou odkazuje, je předán podle hodnoty. Předání hodnotou znamená, že metoda nelze změnit tak, aby odkazoval na novou instanci třídy odkaz na ukazatel typu, ale můžete změnit obsah objektu, na kterou odkazuje. Pro většinu aplikací je dostačující a vrací chování, které chcete.

 Pokud metoda musí vracet jinou instanci, použijte k tomu návratovou hodnotu metody. Zobrazit <xref:System.String?displayProperty=fullName> třídy pro celou řadu metod, které pracují na řetězce a vrátí novou instanci řetězce. Pomocí tohoto modelu je ponecháno na volající rozhodnout, jestli se zachová původní objekt.

 I když vrácené hodnoty jsou běžné a nejčastěji používá správné použití `out` a `ref` parametry vyžaduje zprostředkující návrhu a dovednosti kódování. Knihovna architektům, kteří návrhu pro širokou veřejnost, by neměli očekávat uživatelům pracovat s `out` nebo `ref` parametry.

> [!NOTE]
>  Při práci s parametry, které jsou velké struktury další prostředky, které jsou nutné ke zkopírování těchto struktur může způsobit, že vliv výkon při předání hodnotou. V těchto případech můžete zvážit použití `ref` nebo `out` parametry.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, která je způsobeno tím, typ hodnoty, mají metoda vrátit objekt jako jeho návratovou hodnotu. Metoda musí vracet více hodnot, změnit návrh jej vrátí jednu instanci objektu, který obsahuje hodnoty.

 Chcete-li opravit porušení tohoto pravidla, která je způsobeno tím, typ odkazu, zajistěte, aby chování, které chcete vrátit novou instanci třídy odkaz. Pokud se jedná, používejte metodu k tomu jeho návratovou hodnotu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla; Tento návrh však může způsobit problémy se použitelnost.

## <a name="example"></a>Příklad
 Následující knihovny ukazuje dvě implementace třídy, která generuje odpovědi na zpětnou vazbu od uživatele. První provedení (`BadRefAndOut`) vynutí knihovny uživatele ke správě tři návratové hodnoty. Druhý implementace (`RedesignedRefAndOut`) zjednodušuje činnost koncového uživatele tak, že vrací instanci třídy kontejneru (`ReplyData`), která zvládne správu dat jako jeden celek.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>Příklad
 Následující aplikace ukazuje možnosti uživatele. Volání přepracovaný knihovny (`UseTheSimplifiedClass` metoda) je jednodušší, a informace, které je vrácen touto metodou se snadno spravuje. Je stejný jako výstup ze dvou metod.

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
## <a name="related-rules"></a>Související pravidla
 [CA1021: Vyhněte se výstupním parametrům](../code-quality/ca1021-avoid-out-parameters.md)



