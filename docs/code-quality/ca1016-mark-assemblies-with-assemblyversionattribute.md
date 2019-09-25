---
title: 'CA1016: Označte sestavení pomocí AssemblyVersionAttribute'
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
ms.openlocfilehash: 140037b025db88230762bc0d540d933cec7a5119
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236314"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: Označte sestavení pomocí AssemblyVersionAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|Kategorie|Microsoft.Design|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Sestavení nemá číslo verze.

## <a name="rule-description"></a>Popis pravidla

Identita sestavení se skládá z následujících informací:

- Název sestavení

- Číslo verze

- Jazyková verze

- Veřejný klíč (pro silně pojmenovaná sestavení).

Rozhraní .NET používá číslo verze k jednoznačné identifikaci sestavení a k vytvoření vazby na typy v silně pojmenovaných sestaveních. Číslo verze je používáno spolu se zásadou verze a vydavatele. Ve výchozím nastavení mohou být aplikace spuštěny pouze ve verzi sestavení, v níž byly sestaveny.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, přidejte do sestavení číslo verze pomocí <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> atributu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Potlačit upozornění z tohoto pravidla pro sestavení, která používají třetí strany nebo v produkčním prostředí.

## <a name="example"></a>Příklad

Následující příklad ukazuje sestavení, které má <xref:System.Reflection.AssemblyVersionAttribute> atribut použit.

[!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
[!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
[!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]

## <a name="see-also"></a>Viz také:

- [Správa verzí sestavení](/dotnet/framework/app-domains/assembly-versioning)
- [Postupy: Vytvoření zásady vydavatele](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)