---
title: 'CA1014: Označte sestavení pomocí CLSCompliantAttribute'
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
ms.openlocfilehash: 387eb464959fba522e31f9586998335cb306d844
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236328"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: Označte sestavení pomocí CLSCompliantAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Kategorie|Microsoft.Design|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Pro sestavení není <xref:System.CLSCompliantAttribute?displayProperty=fullName> použit atribut.

## <a name="rule-description"></a>Popis pravidla
Specifikace Common Language Specification (CLS) definuje omezení názvů, datové typy a pravidla, která musí sestavení dodržovat, pokud budou použita napříč programovacími jazyky. Dobrý návrh určuje, že všechna sestavení explicitně označují dodržování specifikace CLS <xref:System.CLSCompliantAttribute>pomocí. Pokud atribut není v sestavení přítomen, sestavení nedodržuje předpisy.

Sestavení kompatibilní se specifikací CLS může obsahovat typy nebo členy typu, které nedodržují předpisy.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, přidejte atribut do sestavení. Místo označení celého sestavení jako nedodržující předpisy byste měli určit, které typy nebo členy typu nejsou kompatibilní, a označit tyto prvky jako takové. Pokud je to možné, měli byste poskytnout alternativu neodpovídající specifikaci CLS pro členy, kteří nedodržují předpisy, aby co nejširšímu možnému posluchači mohl přistupovat ke všem funkcím sestavení.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo. Pokud nechcete, aby sestavení bylo kompatibilní, použijte atribut a nastavte jeho hodnotu na `false`.

## <a name="example"></a>Příklad
Následující příklad ukazuje sestavení, které má <xref:System.CLSCompliantAttribute?displayProperty=fullName> atribut použit, který deklaruje specifikaci kompatibilní se specifikací CLS.

[!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
[!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
[!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]

## <a name="see-also"></a>Viz také:

- <xref:System.CLSCompliantAttribute?displayProperty=fullName>
- [Jazyková nezávislost a jazykově nezávislé komponenty](/dotnet/standard/language-independence-and-language-independent-components)