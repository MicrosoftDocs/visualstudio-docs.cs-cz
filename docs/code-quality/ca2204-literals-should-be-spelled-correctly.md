---
title: 'CA2204: Literály by měly být zadány správně'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f86658978a105c1fa4f3c4602b5c838f4c80726
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31918420"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Literály by měly být zadány správně

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Kategorie|Microsoft.Usage|
|Narušující změna|Bez ukončování řádků|

## <a name="cause"></a>příčina

Řetězcový literál je předat jako argument pro parametr lokalizovatelný, nebo lokalizovatelný vlastností a řetězec obsahuje jeden nebo více slova, která nerozpoznal kontrola pravopisu knihovně společnosti Microsoft.

## <a name="rule-description"></a>Popis pravidla

Toto pravidlo zkontroluje řetězcový literál, který je předán jako hodnotu parametru nebo vlastnost, pokud jeden nebo více následujících případech platí:

- <xref:System.ComponentModel.LocalizableAttribute> Atribut parametru nebo vlastnosti je nastaven na hodnotu true.

- Název parametru nebo vlastnost obsahuje "Text", "Zpráva" nebo "Titulek".

- Název proměnné řetězec, který je předán do <xref:System.Console.Write%2A> nebo <xref:System.Console.WriteLine> metoda je "value" nebo "format".

Toto pravidlo analyzuje řetězcového literálu do slova, tokenizaci složených slov a kontrola pravopisu pro každé slovo nebo token. Informace o analýzy algoritmus najdete v tématu [CA1704: identifikátory by měly být zadány správně](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="language"></a>Jazyk

Kontrola pravopisu kontroluje aktuálně jen pro jazykovou verzi na základě angličtina slovník. Jazyková verze projektu v souboru projektu, můžete změnit tak, že přidáte **CodeAnalysisCulture** element.

Příklad:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Pokud nastavíte jazykovou verzi na jakoukoli jinou hodnotu než jazykovou verzi na základě angličtina, je tato pravidel nástroje Analýza kódu bezobslužně zakázané.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení toto pravidlo, opravte pravopis aplikace word nebo přidat slovo do slovníku. Informace o tom, jak používat vlastní slovník najdete v tématu [postupy: přizpůsobení slovníku analýzy kódu](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Při potlačení upozornění

Nepotlačujte upozornění na toto pravidlo. Správně hláskovaným slova redukovat křivku vyžaduje nové knihovny softwaru.

## <a name="related-rules"></a>Související pravidla

- [CA1704: Identifikátory by měly být zadány správně](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA1703: Řetězce prostředků by měly být zadány správně](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)