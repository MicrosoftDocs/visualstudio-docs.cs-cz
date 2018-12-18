---
title: 'CA2214: Nevolejte přepisovatelné metody v konstruktorech'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ddc827e77b37de6490cb4bee081748f317865b57
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549557"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Nevolejte přepisovatelné metody v konstruktorech

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Kategorie|Microsoft.Usage|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina

Konstruktor nezapečetěný typ volání virtuální metody definované ve své třídě.

## <a name="rule-description"></a>Popis pravidla

Při volání virtuální metody, skutečný typ, který se spustí metodu není vybraná až do spuštění. Pokud konstruktor volání virtuální metody, je možné, že se neprovedlo konstruktoru pro instanci, která vyvolá metodu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Chcete-li opravit porušení tohoto pravidla, nevolejte virtuální metody tohoto typu z konstruktorů tohoto typu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo. Chcete-li odstranit volání virtuální metody by se měla změnit konstruktoru.

## <a name="example"></a>Příklad

Následující příklad ukazuje účinek porušení tohoto pravidla. Testovací aplikace vytvoří instanci `DerivedType`, což způsobí, že její základní třídě (`BadlyConstructedType`) konstruktor ke spuštění. `BadlyConstructedType`pro konstruktor nesprávně volání virtuální metody `DoSomething`. Jak ukazuje výstup, `DerivedType.DoSomething()` spustí a nebude tak před `DerivedType`v konstruktoru.

[!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
[!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

Tento příklad vytvoří následující výstup:

```txt
Calling base ctor.
Derived DoSomething is called - initialized ? No
Calling derived ctor.
```