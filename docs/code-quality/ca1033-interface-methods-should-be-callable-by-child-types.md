---
title: 'CA1033: Metody rozhraní by měla být volatelné podřízenými typy'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b56cd055fa8413d7d98a1c0d6d8b538a8a858af6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941318"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: Metody rozhraní by měla být volatelné podřízenými typy

|||
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Kategorie|Microsoft.Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Nezapečetěný externě viditelný typ poskytuje explicitní implementaci metod veřejného rozhraní a neposkytuje alternativní externě viditelnou metodu stejného názvu.

## <a name="rule-description"></a>Popis pravidla
 Vezměte v úvahu základní typ, který explicitně implementuje metodu veřejných rozhraní. Typ, který se odvozuje od základního typu má přístup k zděděné metody pouze prostřednictvím odkaz na aktuální instanci (`this` v jazyce C#), který je přetypován na rozhraní. Pokud je odvozený typ reimplements (explicitně) metoda zděděné rozhraní, základní implementaci už je přístupný. Vyvolá odvozené provádění; volání prostřednictvím odkazu na aktuální instanci To způsobí, že rekurze a přetečení zásobníku konečný výsledek.

 Toto pravidlo nevytváří sestavu porušení pro explicitní implementaci <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> při externě viditelného `Close()` nebo `System.IDisposable.Dispose(Boolean)` metoda je k dispozici.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, implementovat novou metodu, která poskytuje stejné funkce a je viditelná pro odvozené typy nebo změňte implicitními implementace. Pokud k zásadní změně je přijatelné, alternativou je učiňte typ zapečetěná.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla, pokud je externě viditelná metoda, která má stejné funkce, ale jiný název než explicitně implementované metody.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, `ViolatingBase`, který porušuje pravidla a typ, `FixedBase`, která zobrazuje oprava porušení zásady.

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]

## <a name="see-also"></a>Viz také:
 [Rozhraní](/dotnet/csharp/programming-guide/interfaces/index)