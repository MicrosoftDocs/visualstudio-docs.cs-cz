---
title: 'CA2204: Literály by měly být zadány správně'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6763fd9f8999bd590511026f6571db6a747c43bc
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231847"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Literály by měly být zadány správně

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Literální řetězec je předán jako argument pro Lokalizovatelný parametr nebo na Lokalizovatelný vlastnost a řetězec obsahuje jedno nebo více slov, která nejsou rozpoznána knihovnou kontroly pravopisu společnosti Microsoft.

## <a name="rule-description"></a>Popis pravidla

Toto pravidlo zkontroluje literálový řetězec, který je předán jako hodnota parametru nebo vlastnosti v případě, že jeden nebo více následujících případů je pravdivé:

- <xref:System.ComponentModel.LocalizableAttribute> Atribut parametru nebo vlastnosti je nastaven na hodnotu true.

- Název parametru nebo vlastnosti obsahuje text "text", "zpráva" nebo "titulek".

- Název řetězcové proměnné, která je předána <xref:System.Console.Write%2A> metodě nebo <xref:System.Console.WriteLine> , je buď "value" nebo "Format".

Toto pravidlo analyzuje řetězcový literál do slov, tokenizací složených slov a kontroluje pravopis každého slova nebo tokenu. Informace o algoritmu analýzy naleznete v tématu [CA1704: Identifikátory by měly být zadány](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)správně.

## <a name="language"></a>Jazyk

Kontrola pravopisu aktuálně kontroluje pouze proti slovníkům jazykové verze v angličtině. Můžete změnit jazykovou verzi projektu v souboru projektu přidáním elementu **CodeAnalysisCulture** .

Příklad:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Pokud nastavíte jazykovou verzi na jinou než anglickou jazykovou verzi, toto pravidlo analýzy kódu je tiše zakázané.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, opravte pravopis slova nebo přidejte slovo do vlastního slovníku. Informace o tom, jak používat vlastní slovníky, [najdete v tématu How to: Přizpůsobení slovníku](../code-quality/how-to-customize-the-code-analysis-dictionary.md)analýzy kódu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo. Správná pravopisná slova omezují výukovou křivku nutnou pro nové knihovny softwaru.

## <a name="related-rules"></a>Související pravidla

- [CA1704: Identifikátory by měly být zadány správně](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA1703: Řetězce prostředků by měly být zadány správně](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)