---
title: 'CA1065: Nevyvolávejte výjimky v neočekávaných umístěních'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4999770367ad7b170398333cf7c7cf2cb9d1c407
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546691"
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065: Nevyvolávejte výjimky v neočekávaných umístěních

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|CheckId|CA1065|
|Kategorie|Microsoft.Design|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina

Metoda, u které není předpokládáno vyvolání výjimky, vyvolá výjimku.

## <a name="rule-description"></a>Popis pravidla

Metody, které není předpokládáno vyvolání výjimky lze označit následujícím způsobem:

- Metody Get vlastnosti

- Metody přístupových objektů události

- Metody Equals

- Metody GetHashCode

- Metody ToString

- Statické konstruktory

- Finalizační metody

- Metody Dispose

- Operátory rovnosti

- Implicitní přetypování operátory

Následující části popisují tyto typy metody.

### <a name="property-get-methods"></a>Metody Get vlastnosti

Vlastnosti jsou v podstatě inteligentních polí. Proto by se měly chovat jako pole co největší míře. Pole není vyvolat výjimky a ani by měly vlastnosti. Pokud je vlastnost, která vyvolá výjimku, zvažte jeho metodu.

Následující výjimky mohou být vyvolány z metody get vlastnosti:

- <xref:System.InvalidOperationException?displayProperty=fullName> a všechny odvozené (včetně <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> a všechny odvozené konfigurace

- <xref:System.ArgumentException?displayProperty=fullName> (pouze z indexované get)

- <xref:System.Collections.Generic.KeyNotFoundException> (pouze z indexované get)

### <a name="event-accessor-methods"></a>Metody přístupových objektů události

Přístupové objekty událostí by měl být jednoduché operace, které není vyvolat výjimku. Události by neměly vyvolat výjimku při pokusu o přidání nebo odebrání obslužné rutiny události.

Z přístupový objekt události mohou být vyvolány následující výjimky:

- <xref:System.InvalidOperationException?displayProperty=fullName> a všechny odvozené (včetně <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> a všechny odvozené konfigurace

- <xref:System.ArgumentException> a vy

### <a name="equals-methods"></a>Metody Equals

Následující **rovná** metody by neměla vyvolávat výjimky:

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- <xref:System.IEquatable%601.Equals%2A>

**Rovná** metoda by měla vrátit `true` nebo `false` namísto vyvolání výjimky. Například pokud se rovná se předá dva typy neodpovídající měla by jenom vrátit `false` namísto vyvolání <xref:System.ArgumentException>.

### <a name="gethashcode-methods"></a>Metody GetHashCode

Následující **GetHashCode** metody obvykle by neměla vyvolávat výjimky:

- <xref:System.Object.GetHashCode%2A>

- <xref:System.Collections.IEqualityComparer.GetHashCode%2A>

**Metoda GetHashCode** by vždy vrátit hodnotu. V opačném případě může dojít ke ztrátě položky v zatřiďovací tabulce.

Verze **GetHashCode** trvají může vyvolat argument <xref:System.ArgumentException>. Ale **Object.GetHashCode** by nikdy nevyvolají výjimku.

### <a name="tostring-methods"></a>Metody ToString

Ladicí program používá <xref:System.Object.ToString%2A?displayProperty=fullName> usnadňují zobrazení informací o objektech ve formátu řetězce. Proto **ToString** by neměly měnit stav objektu, a to by neměla vyvolávat výjimky.

### <a name="static-constructors"></a>Statické konstruktory

Vyvolávání výjimek ze statického konstruktoru způsobí, že typ nebude v aktuální doméně aplikace. Pro vyvolání výjimky z statický konstruktor byste měli mít dobrý důvod (například potíže se zabezpečením).

### <a name="finalizers"></a>Finalizační metody

Došlo k výjimce z finalizační metody způsobí, že modul CLR k selhání, které strhne proces. Proto vyvolávání výjimek v finalizační metody by vždy se jim vyhnout.

### <a name="dispose-methods"></a>Metody Dispose

A <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> metoda by neměla vyvolávat výjimky. Uvolnění se často označuje jako součást logiky čištění `finally` klauzuli. Proto se explicitně vyvolání výjimky z metody Dispose vynutí uživateli přidat uvnitř zpracování výjimek `finally` klauzuli.

**Dispose(false)** cesta kódu by nikdy nevyvolají výjimky, protože metody Dispose je téměř vždy volán z finalizační metody.

### <a name="equality-operators--"></a>Operátory rovnosti (==,! =)

Stejně jako metody Equals, operátory rovnosti by měla vrátit buď `true` nebo `false`a by neměla vyvolávat výjimky.

### <a name="implicit-cast-operators"></a>Implicitní přetypování operátory

Vzhledem k tomu, že uživatel je často vědět, že operátor implicitní přetypování se zavolala, je výjimka vyvolána operátorem implicitní přetypování neočekávané. Proto žádné výjimky, měla by být vyvolána z operátory implicitní přetypování.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

U gettery vlastností buď změnit logiku tak, aby už byly k vyvolání výjimky, nebo změňte vlastnost na metodu.

Pro všechny ostatní metody typy uvedených výše změňte tak, aby ho už musí vyvolat výjimku logiku.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Pokud deklaraci výjimky namísto vyvolanou výjimku způsobila porušení zásady, je bezpečný pro potlačení upozornění tohoto pravidla.

## <a name="related-rules"></a>Související pravidla

- [CA2219: Nevyvolávejte výjimky v klauzulích výjimky](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>Viz také:

- [Upozornění ohledně návrhu](../code-quality/design-warnings.md)