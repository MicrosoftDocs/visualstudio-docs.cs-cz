---
title: 'CA2204: literály by měly být zadány správně | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ecf829251cbeab600cb95f8f0c0b0173cd7338d4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546273"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Literály by měly být zadány správně
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Metoda předává literální řetězec do, který je použit v parametru nebo vlastnosti, který vyžaduje lokalizovaný řetězec a řetězcový literál obsahuje jedno nebo více slov, která nejsou rozpoznána knihovnou kontroly pravopisu společnosti Microsoft.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo zkontroluje literálový řetězec, který je předán jako hodnota parametru nebo vlastnosti v případě, že jeden nebo více následujících případů je pravdivé:

- <xref:System.ComponentModel.LocalizableAttribute>Atribut parametru nebo vlastnosti je nastaven na hodnotu true.

- Název parametru nebo vlastnosti obsahuje text "text", "zpráva" nebo "titulek".

- Název řetězcového parametru, který je předán metodě Console. Write nebo Console. WriteLine, je buď hodnota, nebo formát.

  Toto pravidlo analyzuje řetězcový literál do slov, tokenizací složených slov a kontroluje pravopis každého slova nebo tokenu. Informace o algoritmu analýzy naleznete v tématu [CA1704: identifikátory by měly být zadány správně](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

  Ve výchozím nastavení se používá anglická (EN) verze kontroly pravopisu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, opravte pravopis slova nebo přidejte slovo do vlastního slovníku. Informace o použití vlastních slovníků naleznete v tématu [How to: Customize a Code Analysis Dictionary](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo. Správná pravopisná slova omezují výukovou křivku nutnou pro nové knihovny softwaru.

## <a name="related-rules"></a>Související pravidla
 [CA1704: Identifikátory by měly být zadány správně](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA1703: Řetězce prostředků by měly být zadány správně](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
