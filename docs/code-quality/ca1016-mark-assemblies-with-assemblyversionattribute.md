---
title: 'CA1016: Označte sestavení pomocí atributu AssemblyVersionAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7fbc3fa747171892066705ddc32a114cb34e1b02
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2018
ms.locfileid: "47858172"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: Označte sestavení pomocí atributu AssemblyVersionAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|Kategorie|Microsoft.Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina

Sestavení nemá číslo verze.

## <a name="rule-description"></a>Popis pravidla

Identita sestavení se skládá z následujících informací:

- Název sestavení

- Číslo verze

- Jazyková verze

- Veřejný klíč (pro sestavení se silným názvem).

Rozhraní .NET Framework používá číslo verze k jednoznačné identifikaci sestavení a pro svázání s typy v sestaveních se silným názvem. Číslo verze je používáno spolu se zásadou verze a vydavatele. Ve výchozím nastavení mohou být aplikace spuštěny pouze ve verzi sestavení, v níž byly sestaveny.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přidejte číslo verze na sestavení s použitím <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> atribut. Podívejte se na téma v následujícím příkladu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění tohoto pravidla pro sestavení, které jsou používány třetími stranami, nebo v produkčním prostředí.

## <a name="example"></a>Příklad
 Následující příklad ukazuje sestavení, který má <xref:System.Reflection.AssemblyVersionAttribute> atribut.

 [!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]

## <a name="see-also"></a>Viz také:

- [Správa verzí sestavení](/dotnet/framework/app-domains/assembly-versioning)
- [Postupy: Vytváření zásad vydavatele](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)