---
title: 'CA1801: Zkontrolujte nepoužité parametry'
ms.date: 06/24/2019
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6de48bf273a5c93afcd14e7bab2c5d4c4c4b5a7c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233829"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Zkontrolujte nepoužité parametry

|||
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Bez přerušení – Pokud člen není viditelný mimo sestavení, bez ohledu na změnu, kterou provedete.<br /><br /> Bez přerušení – Pokud změníte člena tak, aby používal parametr v rámci jeho těla.<br /><br /> Přerušení – Pokud odeberete parametr a je viditelný mimo sestavení.|

## <a name="cause"></a>příčina

Signatura metody obsahuje parametr, který se nepoužívá v těle metody.

Toto pravidlo neověřuje následující druhy metod:

- Metody, na které se odkazuje delegát.

- Metody používané jako obslužné rutiny událostí.

- Metody deklarované s `abstract` modifikátorem`MustOverride` (v Visual Basic).

- Metody deklarované s `virtual` modifikátorem`Overridable` (v Visual Basic).

- Metody deklarované s `override` modifikátorem`Overrides` (v Visual Basic).

- Metody deklarované s `extern` modifikátorem`Declare` (příkaz v Visual Basic)

Pokud používáte [analyzátory FxCop](install-fxcop-analyzers.md), toto pravidlo neoznačí parametry, které jsou pojmenovány symbolem [zahození](/dotnet/csharp/discards) , `_` `_1`například,, a `_2`. Tím se snižuje šum v parametrech, které jsou potřeba pro požadavky na signatury, například metodu použitou jako delegáta, parametr se speciálními atributy nebo parametr, jehož hodnota je implicitně přistupovaná v době běhu rozhraním, ale neodkazuje se na. znakovou.

## <a name="rule-description"></a>Popis pravidla

Zkontrolujte parametry v nevirtuálních metodách, které se nepoužívají v těle metody, abyste se ujistili, že k nim neexistují žádné neopravitelné chyby. Nepoužité parametry účtují náklady na údržbu a výkon.

V některých případech může porušení tohoto pravidla ukazovat na chybu implementace v metodě. Například parametr by měl být použit v těle metody. Potlačí upozornění tohoto pravidla, pokud musí existovat parametr z důvodu zpětné kompatibility.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, odeberte nepoužitý parametr (zásadní změnu) nebo použijte parametr v těle metody (nerušená změna).

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Z tohoto pravidla je bezpečné potlačit upozornění:

- V dříve dodaném kódu, pro který by došlo k zásadní změně opravy.

- Pro parametr v metodě vlastního rozšíření pro <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=nameWithType>. `this` Funkce ve <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> třídě jsou statické, takže není nutné `this` přístup k parametru v těle metody.

## <a name="example"></a>Příklad

Následující příklad ukazuje dvě metody. Jedna metoda narušuje pravidlo a druhá metoda bude toto pravidlo splňovat.

[!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]

## <a name="related-rules"></a>Související pravidla

[CA1811: Vyhněte se nevolanému privátnímu kódu](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812: Vyhněte se nevytváření instancí vnitřních tříd](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1804: Odebrat nepoužívané místní hodnoty](../code-quality/ca1804-remove-unused-locals.md)
