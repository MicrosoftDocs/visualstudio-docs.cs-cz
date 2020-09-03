---
title: 'CA1016: Označte sestavení pomocí AssemblyVersionAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 97bd41e51c8d6b5415ffb91c5696c7055f46cf7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545402"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: Označte sestavení pomocí AssemblyVersionAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|Kategorie|Microsoft. Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Sestavení nemá číslo verze.

## <a name="rule-description"></a>Popis pravidla
 Identita sestavení se skládá z následujících informací:

- Název sestavení

- Číslo verze

- Kultura

- Veřejný klíč (pro silně pojmenovaná sestavení).

  [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]Používá číslo verze k jednoznačné identifikaci sestavení a k vytvoření vazby na typy v silně pojmenovaných sestaveních. Číslo verze je používáno spolu se zásadou verze a vydavatele. Ve výchozím nastavení mohou být aplikace spuštěny pouze ve verzi sestavení, v níž byly sestaveny.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přidejte do sestavení číslo verze pomocí <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> atributu. Prohlédněte si následující příklad.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit upozornění z tohoto pravidla pro sestavení, která používají třetí strany nebo v produkčním prostředí.

## <a name="example"></a>Příklad
 Následující příklad ukazuje sestavení, které má <xref:System.Reflection.AssemblyVersionAttribute> atribut použit.

 [!code-cpp[FxCop.Design.AssembliesVersion#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cpp/FxCop.Design.AssembliesVersion.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesVersion#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cs/FxCop.Design.AssembliesVersion.cs#1)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/vb/FxCop.Design.AssembliesVersion.vb#1)]

## <a name="see-also"></a>Viz také
 [Správa verzí sestavení](https://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903) [Postupy: vytvoření zásady vydavatele](https://msdn.microsoft.com/library/8046bc5d-2fa9-4277-8a5e-6dcc96c281d9)
