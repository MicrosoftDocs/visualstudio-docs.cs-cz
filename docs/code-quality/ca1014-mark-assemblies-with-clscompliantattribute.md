---
title: 'CA1014: Označte sestavení pomocí atributu CLSCompliantAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c615015fac5e8e9b60425679e116b8c7680ea637
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72441639"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: Označte sestavení pomocí atributu CLSCompliantAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Kategorie|Microsoft. Design|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
V sestavení není použit atribut <xref:System.CLSCompliantAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla
Specifikace Common Language Specification (CLS) definuje omezení názvů, datové typy a pravidla, která musí sestavení dodržovat, pokud budou použita napříč programovacími jazyky. Dobrý návrh určuje, že všechna sestavení explicitně označují dodržování specifikace CLS pomocí <xref:System.CLSCompliantAttribute>. Pokud atribut není v sestavení přítomen, sestavení nedodržuje předpisy.

Sestavení kompatibilní se specifikací CLS může obsahovat typy nebo členy typu, které nedodržují předpisy.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, přidejte atribut do sestavení. Místo označení celého sestavení jako nedodržující předpisy byste měli určit, které typy nebo členy typu nejsou kompatibilní, a označit tyto prvky jako takové. Pokud je to možné, měli byste poskytnout alternativu neodpovídající specifikaci CLS pro členy, kteří nedodržují předpisy, aby co nejširšímu možnému posluchači mohl přistupovat ke všem funkcím sestavení.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo. Pokud nechcete, aby sestavení bylo kompatibilní, použijte atribut a nastavte jeho hodnotu na `false`.

## <a name="example"></a>Příklad
Následující příklad ukazuje sestavení s použitým atributem <xref:System.CLSCompliantAttribute?displayProperty=fullName>, který deklaruje kompatibilní s IT specifikací CLS.

[!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
[!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
[!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]

## <a name="see-also"></a>Viz také:

- <xref:System.CLSCompliantAttribute?displayProperty=fullName>
- [Jazyková nezávislost a jazykově nezávislé komponenty](/dotnet/standard/language-independence-and-language-independent-components)
