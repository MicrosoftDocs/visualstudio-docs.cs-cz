---
title: 'CA1819: vlastnosti by neměly vracet pole | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a96d2164cbd6c03cb0d191b2d0c3c4607468209c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545324"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: Vlastnosti by neměly vracet pole
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|Kategorie|Microsoft. Performance|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Veřejná nebo chráněná vlastnost ve veřejném typu vrací pole.

## <a name="rule-description"></a>Popis pravidla
 Pole vrácená vlastnostmi nejsou chráněna proti zápisu, a to i v případě, že je vlastnost určena pouze pro čtení. Abyste pole ochránili před změnou, musí vlastnost vrátit kopii tohoto pole. Uživatelé obvykle nebudou rozumět nepříznivým výkonnostním důsledkům volání těchto vlastností. Konkrétně můžou použít vlastnost jako indexovanou vlastnost.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, buď vlastnost nastavte jako metodu, nebo změňte vlastnost tak, aby vracela kolekci.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Atributy můžou obsahovat vlastnosti, které vracejí pole, ale nemůžou obsahovat vlastnosti, které vracejí kolekce. Můžete potlačit upozornění, která je vyvolána pro vlastnost atributu odvozeného od [System. Attribute] (<!-- TODO: review code entity reference <xref:assetId:///System.Attribute?qualifyHint=False&amp;autoUpgrade=True>  -->Deník. V opačném případě potlačíte upozornění z tohoto pravidla.

## <a name="example-violation"></a>Příklad porušení

### <a name="description"></a>Popis
 Následující příklad ukazuje vlastnost, která je v rozporu s tímto pravidlem.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/cs/FxCop.Performance.PropertyArrayViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/vb/FxCop.Performance.PropertyArrayViolation.vb#1)]

### <a name="comments"></a>Komentáře
 Chcete-li opravit porušení tohoto pravidla, buď vlastnost nastavte jako metodu, nebo změňte vlastnost tak, aby vracela kolekci místo pole.

## <a name="change-the-property-to-a-method-example"></a>Změňte vlastnost na příklad metody.

### <a name="description"></a>Popis
 Následující příklad opravuje porušení změnou vlastnosti na metodu.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/cs/FxCop.Performance.PropertyArrayFixedMethod.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/vb/FxCop.Performance.PropertyArrayFixedMethod.vb#1)]

## <a name="return-a-collection-example"></a>Příklad vrácení kolekce

### <a name="description"></a>Popis
 Následující příklad opravuje porušení změnou vlastnosti tak, aby vracela

 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/cs/FxCop.Performance.PropertyArrayFixedCollection.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/vb/FxCop.Performance.PropertyArrayFixedCollection.vb#1)]

## <a name="allowing-users-to-modify-a-property"></a>Umožnění uživatelům upravovat vlastnost

### <a name="description"></a>Popis
 Můžete chtít, aby příjemce třídy mohl upravovat vlastnost. Následující příklad ukazuje vlastnost pro čtení a zápis, která toto pravidlo porušuje.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/cs/FxCop.Performance.PropertyModifyViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/vb/FxCop.Performance.PropertyModifyViolation.vb#1)]

### <a name="comments"></a>Komentáře
 Následující příklad opravuje porušení změnou vlastnosti tak, aby vrátila hodnotu <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName> .

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/cs/FxCop.Performance.PropertyModifyFixed.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/vb/FxCop.Performance.PropertyModifyFixed.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1024: Použijte vlastnosti, kde je to vhodné](../code-quality/ca1024-use-properties-where-appropriate.md)
