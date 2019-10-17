---
title: 'CA1016: Označte sestavení pomocí atributu AssemblyVersionAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 85a8d2d9efe83f62bd0bd40021ffe0e752cf4666
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72441602"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: Označte sestavení pomocí atributu AssemblyVersionAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|Kategorie|Microsoft. Design|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Sestavení nemá číslo verze.

## <a name="rule-description"></a>Popis pravidla

Identita sestavení se skládá z následujících informací:

- Název sestavení

- Číslo verze

- jazykových

- Veřejný klíč (pro silně pojmenovaná sestavení).

Rozhraní .NET používá číslo verze k jednoznačné identifikaci sestavení a k vytvoření vazby na typy v silně pojmenovaných sestaveních. Číslo verze je používáno spolu se zásadou verze a vydavatele. Ve výchozím nastavení mohou být aplikace spuštěny pouze ve verzi sestavení, v níž byly sestaveny.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, přidejte do sestavení číslo verze pomocí atributu <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName>.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Potlačit upozornění z tohoto pravidla pro sestavení, která používají třetí strany nebo v produkčním prostředí.

## <a name="example"></a>Příklad

Následující příklad ukazuje sestavení, které má atribut <xref:System.Reflection.AssemblyVersionAttribute> použit.

[!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
[!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
[!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]

## <a name="see-also"></a>Viz také:

- [Správa verzí sestavení](/dotnet/framework/app-domains/assembly-versioning)
- [Postupy: vytvoření zásady vydavatele](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)
