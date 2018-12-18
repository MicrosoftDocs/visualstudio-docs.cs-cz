---
title: 'CA1702: Malá a velká písmena složených slov by měla být použita správně'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4703c43c81df13432f45fb4ba519a02b39a839e0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917840"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: Malá a velká písmena složených slov by měla být použita správně

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|Kategorie|Microsoft.Naming|
|Narušující změna|Při ukončování aktivováno u sestavení.<br /><br /> Non narušující - při vyvolání parametrů typů.|

## <a name="cause"></a>příčina

Název identifikátoru obsahuje více slov a alespoň jedno ze slov se zdá být složené slovo, které není správně formátováno.

## <a name="rule-description"></a>Popis pravidla

Název identifikátoru je rozdělení do slova, které jsou založeny na malá a velká písmena. Každý souvislý dva slovní spojení je ve kontrola pravopisu knihovně společnosti Microsoft. Pokud je rozpoznána, vytvoří identifikátor narušení pravidla. Příklady složených slov, které způsobí narušení jsou "Kontrolního součtu" a "MultiPart", která by měla být použita jako "Kontrolního součtu" a "Multipart", v uvedeném pořadí. Z důvodu předchozí běžné použití několika výjimkami je součástí pravidlo, a jsou označeny několik jednoho slova, jako je například "Nástrojů" a "Název souboru", která by měla být použita jako dvě různá slova (v tomto případě "Nástrojů" a "Název").

Zásady vytváření názvů zadejte obecný vzhled pro knihovny cílené modul common language runtime. Tím se snižuje křivky learning, který je vyžadován pro nové knihovny softwaru a zvyšuje sebejistotu zákazníka, knihovny byla vyvinuta uživatelem s odbornými znalostmi v vývoj spravovaného kódu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Změňte název tak, aby je použita správně.

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

## <a name="when-to-suppress-warnings"></a>Při potlačení upozornění

Je bezpečné potlačit upozornění na toto pravidlo, pokud jsou obě části složené slovo rozpoznáno slovníku a je použít dvě slova.

## <a name="related-rules"></a>Související pravidla

- [CA1701: Malá a velká písmena složených slov prostředku řetězců by měla být použita správně](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1709: Malá a velká písmena identifikátorů by měla být použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Identifikátory by se měly lišit více než použitím malých a velkých písmen](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Viz také

- [Pokyny pro pojmenování](/dotnet/standard/design-guidelines/naming-guidelines)
- [Konvence pro malá a velká písmena](/dotnet/standard/design-guidelines/capitalization-conventions)