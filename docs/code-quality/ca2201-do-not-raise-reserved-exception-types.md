---
title: 'CA2201: Nevyvolávejte vyhrazené typy výjimek'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d9b787a4e50f43867b5d9b4ec7a11aba03f8599
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231671"
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201: Nevyvolávejte vyhrazené typy výjimek

|||
|-|-|
|TypeName|DoNotRaiseReservedExceptionTypes|
|CheckId|CA2201|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Metoda vyvolá typ výjimky, který je příliš obecný nebo který je rezervován modulem runtime.

## <a name="rule-description"></a>Popis pravidla

Následující typy výjimek jsou příliš obecné, aby poskytovaly dostatečné informace uživateli:

- <xref:System.Exception?displayProperty=fullName>

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.SystemException?displayProperty=fullName>

Následující typy výjimek jsou vyhrazené a měly by být vyvolány jenom modulem CLR (Common Language Runtime):

- <xref:System.AccessViolationException?displayProperty=fullName>

- <xref:System.ExecutionEngineException?displayProperty=fullName>

- <xref:System.IndexOutOfRangeException?displayProperty=fullName>

- <xref:System.NullReferenceException?displayProperty=fullName>

- <xref:System.OutOfMemoryException?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.COMException?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.ExternalException?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SEHException?displayProperty=fullName>

- <xref:System.StackOverflowException?displayProperty=fullName>

**Negenerovat obecné výjimky**

Pokud vyvoláte obecný typ výjimky, například <xref:System.Exception> nebo <xref:System.SystemException> v knihovně nebo v architektuře, vynutí si příjemce zachytit všechny výjimky, včetně neznámých výjimek, které neznají způsob zpracování.

Místo toho buď vyvolejte více odvozeného typu, který již v rozhraní existuje, nebo vytvořte vlastní typ, který je odvozen <xref:System.Exception>z.

**Vyvolat specifické výjimky**

V následující tabulce jsou uvedeny parametry a výjimky, které mají být vyhozeny při ověřování parametru, včetně parametru value v přístupovém objektu set vlastnosti:

|Popis parametru|Výjimka|
|---------------------------|---------------|
|`null`odkaz|<xref:System.ArgumentNullException?displayProperty=fullName>|
|Mimo povolený rozsah hodnot (například index pro kolekci nebo seznam)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|
|Neplatná `enum` hodnota|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|
|Obsahuje formát, který nesplňuje specifikace parametrů metody (například formátovací řetězec pro `ToString(String)`).|<xref:System.FormatException?displayProperty=fullName>|
|Jinak neplatné|<xref:System.ArgumentException?displayProperty=fullName>|

Když je operace neplatná pro aktuální stav objektu throw<xref:System.InvalidOperationException?displayProperty=fullName>

Když je provedena operace u objektu, který byl uvolněn throw<xref:System.ObjectDisposedException?displayProperty=fullName>

V případě, že operace není podporována (například v přepsaném **datovém proudu. zápis** do datového proudu otevřeného pro čtení) vyvolání<xref:System.NotSupportedException?displayProperty=fullName>

Pokud by převod způsobil přetečení (například v explicitním přetížení operátoru přetypování), throw<xref:System.OverflowException?displayProperty=fullName>

Pro všechny ostatní situace zvažte vytvoření vlastního typu, který je odvozen od <xref:System.Exception> a vyvolávají ho.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, změňte typ vyvolané výjimky na konkrétní typ, který není jedním z rezervovaných typů.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo.

## <a name="related-rules"></a>Související pravidla

- [CA1031: Nezachytit obecné typy výjimek](../code-quality/ca1031-do-not-catch-general-exception-types.md)
