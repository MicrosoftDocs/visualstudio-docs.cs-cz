---
title: 'CA2201: nevyvolávat rezervované typy výjimek | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a550226a5ea1edb3b30e317be6b5682f4c204d52
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667380"
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201: Nevyvolávejte vyhrazené typy výjimek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotRaiseReservedExceptionTypes|
|CheckId|CA2201|
|Kategorie|Microsoft. Usage|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Metoda vyvolá typ výjimky, který je příliš obecný nebo který je rezervován modulem runtime.

## <a name="rule-description"></a>Popis pravidla
 Následující typy výjimek jsou příliš obecné, aby poskytovaly dostatečné informace uživateli:

- <xref:System.Exception?displayProperty=fullName>

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.SystemException?displayProperty=fullName>

  Následující typy výjimek jsou vyhrazené a měly by být vyvolány jenom modulem CLR (Common Language Runtime):

- <xref:System.ExecutionEngineException?displayProperty=fullName>

- <xref:System.IndexOutOfRangeException?displayProperty=fullName>

- <xref:System.NullReferenceException?displayProperty=fullName>

- <xref:System.OutOfMemoryException?displayProperty=fullName>

  **Negenerovat obecné výjimky**

  Pokud vyvoláte obecný typ výjimky, například <xref:System.Exception> nebo <xref:System.SystemException> v knihovně nebo v rámci architektury, vynutí si příjemce zachytit všechny výjimky, včetně neznámých výjimek, které neznají způsob zpracování.

  Místo toho buď vyvolejte více odvozeného typu, který již v rozhraní existuje, nebo vytvořte vlastní typ, který je odvozen z <xref:System.Exception>.

  **Vyvolat specifické výjimky**

  V následující tabulce jsou uvedeny parametry a výjimky, které mají být vyhozeny při ověřování parametru, včetně parametru value v přístupovém objektu set vlastnosti:

|Popis parametru|Výjimka|
|---------------------------|---------------|
|odkaz na `null`|<xref:System.ArgumentNullException?displayProperty=fullName>|
|Mimo povolený rozsah hodnot (například index pro kolekci nebo seznam)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|
|Neplatná hodnota `enum`|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|
|Obsahuje formát, který nesplňuje specifikace parametrů metody (například formátovací řetězec pro `ToString(String)`).|<xref:System.FormatException?displayProperty=fullName>|
|Jinak neplatné|<xref:System.ArgumentException?displayProperty=fullName>|

 Když je operace neplatná pro aktuální stav objektu throw <xref:System.InvalidOperationException?displayProperty=fullName>

 Je-li operace provedena u objektu, který byl uvolněn jako throw <xref:System.ObjectDisposedException?displayProperty=fullName>

 V případě, že operace není podporována (například v přepsaném **datovém proudu. zápis** do datového proudu otevřeného pro čtení) vyvolat <xref:System.NotSupportedException?displayProperty=fullName>

 Pokud by převod způsobil přetečení (například v explicitním přetížení operátoru přetypování), throw <xref:System.OverflowException?displayProperty=fullName>

 Pro všechny ostatní situace zvažte vytvoření vlastního typu, který je odvozen z <xref:System.Exception> a throw.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte typ vyvolané výjimky na konkrétní typ, který není jedním z rezervovaných typů.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="related-rules"></a>Související pravidla
 [CA1031: Nezachycujte výjimky obecného typu](../code-quality/ca1031-do-not-catch-general-exception-types.md)
