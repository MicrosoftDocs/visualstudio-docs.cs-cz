---
title: 'CA1708: identifikátory by se měly lišit o více než případu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 22a33c852b941b4c7e7398416aa1e74e69ff1786
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544037"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: Identifikátory by se měly lišit více než použitím malých a velkých písmen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|Kategorie|Microsoft. pojmenování|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Názvy dvou typů, členů, parametrů nebo plně kvalifikovaných oborů názvů jsou identické, když jsou převedeny na malá písmena.

## <a name="rule-description"></a>Popis pravidla
 Identifikátory pro obory názvů, typy, členy a parametry nelze odlišit pouze ve velikosti písmen, protože jazyky cílené na modul CLR (Common Language Runtime) nemusí rozlišovat malá a velká písmena. Například [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] je široce používaný jazyk bez rozlišení velkých a malých písmen.

 Toto pravidlo je vyvoláno pouze u veřejně viditelných členů.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Vyberte název, který je jedinečný, pokud je porovnán s jinými identifikátory při nerozlišování velkých a malých písmen.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo. Knihovna nemusí být použitelná ve všech dostupných jazycích v [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

## <a name="example-of-a-violation"></a>Příklad porušení
 Následující příklad demonstruje porušení tohoto pravidla.

 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase/cs/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase.cs#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1709: Malá a velká písmena identifikátorů by měla být použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
