---
title: 'CA1703: Řetězce prostředků by měly být zadány správně'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edd3945953a07b10aee5c2690a25aafe446e2c10
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234328"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Řetězce prostředků by měly být zadány správně

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Kategorie|Microsoft.Naming|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Zdrojový řetězec obsahuje jedno nebo více slov, která knihovna kontroly pravopisu společnosti Microsoft nerozpoznala.

## <a name="rule-description"></a>Popis pravidla

Toto pravidlo analyzuje řetězec prostředku na slova (složená slova tokenizací) a kontroluje pravopis každého slova nebo tokenu. Informace o algoritmu analýzy naleznete v tématu [CA1704: Identifikátory by měly být zadány](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)správně.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, použijte úplná slova, která jsou správně zadána nebo přidejte slova do vlastního slovníku. Informace o tom, jak používat vlastní slovníky, [najdete v tématu CA1704: Identifikátory by měly být zadány](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)správně.

## <a name="change-the-dictionary-language"></a>Změna jazyka slovníku

Ve výchozím nastavení se používá anglická (EN) verze kontroly pravopisu. Pokud chcete změnit jazyk kontroly pravopisu, můžete to udělat tak, že do souboru *AssemblyInfo.cs* nebo *AssemblyInfo. vb* přidáte jeden z následujících atributů:

- Použijte <xref:System.Reflection.AssemblyCultureAttribute> k určení jazykové verze, pokud jsou prostředky v satelitním sestavení.
- Použijte <xref:System.Resources.NeutralResourcesLanguageAttribute> k určení *neutrální jazykové verze* sestavení, pokud jsou prostředky ve stejném sestavení jako váš kód.

> [!IMPORTANT]
> Pokud nastavíte jazykovou verzi na jinou než anglickou jazykovou verzi, toto pravidlo analýzy kódu je tiše zakázané.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo. Správná pravopisná slova zkracují dobu potřebnou k učení nových knihoven softwaru.

## <a name="related-rules"></a>Související pravidla

- [CA1701: Složená slova řetězce prostředků by se měla použita správně.](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704: Identifikátory by měly být zadány správně](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204: Literály by měly být zadány správně](../code-quality/ca2204-literals-should-be-spelled-correctly.md)