---
title: 'CA1044: Vlastnosti by neměly být pouze pro zápis'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6018957bc6de32668cbaf0a719f2a603dc7f496f
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550983"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: Vlastnosti by neměly být pouze pro zápis

|||
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|CheckId|CA1044|
|Kategorie|Microsoft.Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Veřejné nebo chráněné vlastnosti má přistupující objekt set, ale nemá přistupující objekt get.

## <a name="rule-description"></a>Popis pravidla
 Získat přístupové objekty poskytnout oprávnění ke čtení pro vlastnost a přístupové objekty set poskytují přístup pro zápis. Ačkoli je přijatelné a často nezbytné použít vlastnost jen pro čtení, směrnice návrhu zakazují použití vlastností jen pro zápis. Je to proto, že umožnit uživateli nastavit hodnotu a poté uživateli zabránit v zobrazování hodnotě neposkytuje žádné zabezpečení. Taktéž bez přístupu pro čtení není možné zobrazit stav sdílených objektů, což omezuje jejich užitečnost.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přidejte přístupový objekt get vlastnosti. Případně pokud chování vlastnost jen pro zápis, je nezbytné, zvažte, převod této vlastnosti na metodu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění tohoto pravidla se doporučuje.

## <a name="example"></a>Příklad
 V následujícím příkladu `BadClassWithWriteOnlyProperty` je typ s vlastností jen pro zápis. `GoodClassWithReadWriteProperty` obsahuje opraveným kódem.

 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]