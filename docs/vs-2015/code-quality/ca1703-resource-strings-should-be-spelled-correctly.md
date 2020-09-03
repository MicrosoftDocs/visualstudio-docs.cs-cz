---
title: 'CA1703: řetězce prostředků by měly být zadány správně | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2e720c1c491e88b6d89fb4b1f0175e8bc8a56e27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544050"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Řetězce prostředků by měly být zadány správně
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Kategorie|Microsoft. pojmenování|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Zdrojový řetězec obsahuje jedno nebo více slov, která knihovna kontroly pravopisu společnosti Microsoft nerozpoznala.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo analyzuje řetězec prostředku na slova (složená slova tokenizací) a kontroluje pravopis každého slova nebo tokenu. Informace o algoritmu analýzy naleznete v tématu [CA1704: identifikátory by měly být zadány správně](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

 Ve výchozím nastavení se používá anglická (EN) verze kontroly pravopisu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, použijte úplná slova, která jsou správně zadána nebo přidejte slova do vlastního slovníku. Informace o tom, jak používat vlastní slovníky, najdete v tématu [CA1704: identifikátory by měly být zadány správně](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo. Správná pravopisná slova zkracují dobu potřebnou k učení nových knihoven softwaru.

## <a name="related-rules"></a>Související pravidla
 [CA1701: Malá a velká písmena složených slov řetězců prostředků by měla být použita správně](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1704: Identifikátory by měly být zadány správně](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA2204: Literály by měly být zadány správně](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
