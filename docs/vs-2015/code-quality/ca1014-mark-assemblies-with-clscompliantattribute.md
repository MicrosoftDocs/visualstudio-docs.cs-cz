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
ms.openlocfilehash: c6dc131a2bb5f0c54943213fbb42561a0c72d95c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545467"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: Označte sestavení pomocí CLSCompliantAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Kategorie|Microsoft. Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Pro sestavení není <xref:System.CLSCompliantAttribute?displayProperty=fullName> použit atribut.

## <a name="rule-description"></a>Popis pravidla
 Specifikace Common Language Specification (CLS) definuje omezení názvů, datové typy a pravidla, která musí sestavení dodržovat, pokud budou použita napříč programovacími jazyky. Dobrý návrh určuje, že všechna sestavení explicitně označují dodržování specifikace CLS pomocí <xref:System.CLSCompliantAttribute> . Pokud atribut není v sestavení přítomen, sestavení nedodržuje předpisy.

 Sestavení kompatibilní se specifikací CLS může obsahovat typy nebo členy typu, které nedodržují předpisy.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přidejte atribut do sestavení. Místo označení celého sestavení jako nedodržující předpisy byste měli určit, které typy nebo členy typu nejsou kompatibilní, a označit tyto prvky jako takové. Pokud je to možné, měli byste poskytnout alternativu neodpovídající specifikaci CLS pro členy, kteří nedodržují předpisy, aby co nejširšímu možnému posluchači mohl přistupovat ke všem funkcím sestavení.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo. Pokud nechcete, aby sestavení bylo kompatibilní, použijte atribut a nastavte jeho hodnotu na `false` .

## <a name="example"></a>Příklad
 Následující příklad ukazuje sestavení, které má <xref:System.CLSCompliantAttribute?displayProperty=fullName> atribut použit, který deklaruje specifikaci kompatibilní se specifikací CLS.

 [!code-cpp[FxCop.Design.AssembliesCls#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cpp/FxCop.Design.AssembliesCls.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCls#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cs/FxCop.Design.AssembliesCls.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/vb/FxCop.Design.AssembliesCls.vb#1)]

## <a name="see-also"></a>Viz také
 <xref:System.CLSCompliantAttribute?displayProperty=fullName>[Jazyková nezávislost a jazykově nezávislé komponenty](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
