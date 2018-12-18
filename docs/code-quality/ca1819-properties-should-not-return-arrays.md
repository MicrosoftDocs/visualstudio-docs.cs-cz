---
title: 'CA1819: Vlastnosti by neměly vracet pole'
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 99fd9627c06b11dae9348a85f417cf152ac1c8c9
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859030"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: Vlastnosti by neměly vracet pole

|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|Kategorie|Microsoft.Performance|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina

Veřejné nebo chráněné vlastnosti veřejného typu vrací pole.

## <a name="rule-description"></a>Popis pravidla

Pole vrácená vlastnostmi nejsou chráněna proti zápisu, i v případě, že vlastnost je jen pro čtení. Abyste pole ochránili před změnou, musí vlastnost vrátit kopii tohoto pole. Uživatelé obvykle nebudou rozumět nepříznivým výkonnostním důsledkům volání těchto vlastností. Konkrétně se může použít vlastnost jako indexovaná vlastnost.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Chcete-li opravit porušení tohoto pravidla, metodu nastavení vlastnosti nebo změňte vlastnost na vrácení kolekce.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Můžete potlačit upozornění, která se vyvolá pro vlastnost, která je odvozena z atributu <xref:System.Attribute> třídy. Atributy mohou obsahovat vlastnosti, které vrací pole, ale nemůže obsahovat vlastnosti, které vracejí kolekce.

Upozornění můžete potlačit, pokud vlastnost je součástí [objekt pro přenos dat (DTO)](/previous-versions/msp-n-p/ff649585(v=pandp.10)) třídy.

V opačném případě nepotlačujte upozornění tohoto pravidla.

## <a name="example-violation"></a>Příklad porušení

Následující příklad ukazuje vlastnost, která porušuje tato pravidla:

[!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
[!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]

Chcete-li opravit porušení tohoto pravidla, metodu nastavení vlastnosti nebo změňte vlastnost na vrácení kolekce místo pole.

### <a name="change-the-property-to-a-method"></a>Změňte hodnotu vlastnosti na metodu

V následujícím příkladu řeší porušení změnou vlastnosti na metodu:

[!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
[!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]

### <a name="change-the-property-to-return-a-collection"></a>Změňte vlastnost na vrácení kolekce

V následujícím příkladu řeší porušení změnou vlastnosti se vraťte <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>:

[!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
[!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]

## <a name="allow-users-to-modify-a-property"></a>Povolit uživatelům změnit vlastnost

Můžete chtít umožnit příjemci třídy k úpravě vlastností. Následující příklad ukazuje vlastnost pro čtení a zápis, který porušuje tato pravidla:

[!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
[!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]

V následujícím příkladu řeší porušení změnou vlastnosti se vraťte <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>:

[!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
[!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]

## <a name="related-rules"></a>Související pravidla

- [CA1024: Použijte vlastnosti, kde je to vhodné](../code-quality/ca1024-use-properties-where-appropriate.md)