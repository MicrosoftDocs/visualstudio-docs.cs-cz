---
title: 'CA1014: Označte sestavení pomocí CLSCompliantAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9408a7b55c800a7979c39075afdf8e9e6e4c7cdb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663150"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: Označte sestavení pomocí atributu CLSCompliantAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Kategorie|Microsoft. Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 V sestavení není použit atribut <xref:System.CLSCompliantAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla
 Specifikace Common Language Specification (CLS) definuje omezení názvů, datové typy a pravidla, která musí sestavení dodržovat, pokud budou použita napříč programovacími jazyky. Dobrý návrh určuje, že všechna sestavení explicitně označují dodržování specifikace CLS pomocí <xref:System.CLSCompliantAttribute>. Pokud atribut není v sestavení přítomen, sestavení nedodržuje předpisy.

 Sestavení kompatibilní se specifikací CLS může obsahovat typy nebo členy typu, které nedodržují předpisy.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přidejte atribut do sestavení. Místo označení celého sestavení jako nedodržující předpisy byste měli určit, které typy nebo členy typu nejsou kompatibilní, a označit tyto prvky jako takové. Pokud je to možné, měli byste poskytnout alternativu neodpovídající specifikaci CLS pro členy, kteří nedodržují předpisy, aby co nejširšímu možnému posluchači mohl přistupovat ke všem funkcím sestavení.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo. Pokud nechcete, aby sestavení bylo kompatibilní, použijte atribut a nastavte jeho hodnotu na `false`.

## <a name="example"></a>Příklad
 Následující příklad ukazuje sestavení s použitým atributem <xref:System.CLSCompliantAttribute?displayProperty=fullName>, který deklaruje kompatibilní s IT specifikací CLS.

 [!code-cpp[FxCop.Design.AssembliesCls#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cpp/FxCop.Design.AssembliesCls.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCls#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cs/FxCop.Design.AssembliesCls.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/vb/FxCop.Design.AssembliesCls.vb#1)]

## <a name="see-also"></a>Viz také
 nezávislá <xref:System.CLSCompliantAttribute?displayProperty=fullName> [jazyka a součásti nezávislé na jazyce](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
