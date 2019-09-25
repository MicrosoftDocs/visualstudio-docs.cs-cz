---
title: 'CA1701: Malá a velká písmena složených slov řetězců prostředků by měla být použita správně'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed5ae8c0845755fe626e7e801f500389f9263cf5
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234366"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: Malá a velká písmena složených slov řetězců prostředků by měla být použita správně

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Kategorie|Microsoft.Naming|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Řetězec prostředku obsahuje složené slovo, které zřejmě není správně použita.

## <a name="rule-description"></a>Popis pravidla

Každé slovo v řetězci prostředku je rozděleno na tokeny, které jsou založeny na velikosti písmen. Každá kombinace dvou sousedících tokenů je zkontrolována knihovnou kontroly pravopisu společnosti Microsoft. Je-li kombinace rozpoznána, způsobí slovo porušení pravidla. Příklady složených slov, která způsobují porušení, jsou "kontrolní součet" a "MultiPart", které by měly být použita jako "kontrolní součet" a "multipart". Kvůli předchozímu běžnému využití jsou do pravidla integrována několik výjimek a několik jednoduchých slov je označeno jako "panel nástrojů" a "filename", které by se měly použita jako dvě odlišná slova. V tomto příkladu by byl označený příznak "panel nástrojů" a "FileName".

Zásady vytváření názvů poskytují běžný vzhled pro knihovny, které cílí na modul CLR (Common Language Runtime). Tím se zmenší výuková křivka, která je požadována pro nové knihovny softwaru, a zvyšuje důvěru zákazníků, že knihovna byla vyvinuta někým, kdo má zkušenosti s vývojem spravovaného kódu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Změňte slovo tak, aby se použita správně.

## <a name="change-the-dictionary-language"></a>Změna jazyka slovníku

Ve výchozím nastavení se používá anglická (EN) verze kontroly pravopisu. Pokud chcete změnit jazyk kontroly pravopisu, můžete to udělat tak, že do souboru *AssemblyInfo.cs* nebo *AssemblyInfo. vb* přidáte jeden z následujících atributů:

- Použijte <xref:System.Reflection.AssemblyCultureAttribute> k určení jazykové verze, pokud jsou prostředky v satelitním sestavení.
- Použijte <xref:System.Resources.NeutralResourcesLanguageAttribute> k určení *neutrální jazykové verze* sestavení, pokud jsou prostředky ve stejném sestavení jako váš kód.

> [!IMPORTANT]
> Pokud nastavíte jazykovou verzi na jinou než anglickou jazykovou verzi, toto pravidlo analýzy kódu je tiše zakázané.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Z tohoto pravidla je bezpečné potlačit upozornění, pokud slovník pravopisu rozpozná obě části složeného slova a záměr je použít dvě slova.

Pro kontrolu pravopisu můžete také přidat složená slova do vlastního slovníku. Slova ve vlastním slovníku nezpůsobují porušení. Další informace najdete v tématu [jak: Přizpůsobení slovníku](../code-quality/how-to-customize-the-code-analysis-dictionary.md)analýzy kódu.

## <a name="related-rules"></a>Související pravidla

- [CA1702: Složená slova by se měla použita správně.](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)
- [CA1709: Identifikátory by se měly použita správně.](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Identifikátory by se měly lišit o více než malých písmenech](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Viz také:

- [Konvence pro malá a velká písmena](/dotnet/standard/design-guidelines/capitalization-conventions)
- [Pokyny pro pojmenování](/dotnet/standard/design-guidelines/naming-guidelines)