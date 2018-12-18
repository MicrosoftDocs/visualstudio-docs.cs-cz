---
title: 'CA1701: Malá a velká písmena složených slov prostředku řetězců by měla být použita správně'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ecc558cb9c069c19b545434afe0a851130fdb300
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915654"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: Malá a velká písmena složených slov prostředku řetězců by měla být použita správně

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Kategorie|Microsoft.Naming|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina

Řetězec prostředku obsahuje složené slovo nezdá se být použita správně.

## <a name="rule-description"></a>Popis pravidla

Jednotlivých slov v řetězec prostředku je rozdělená do tokenů, které jsou založeny na malá a velká písmena. Každá kombinace dvou sousedících tokenů je zkontrolována knihovnou kontroly pravopisu společnosti Microsoft. Je-li kombinace rozpoznána, způsobí slovo porušení pravidla. Příklady složených slov, které způsobí narušení jsou "Kontrolního součtu" a "MultiPart", která by měla být použita jako "Kontrolního součtu" a "Multipart", v uvedeném pořadí. Z důvodu předchozí běžné použití několika výjimkami jsou integrované do pravidla a jsou označeny několik jednoho slova, jako je například "Nástrojů" a "Název", která by měla být použita jako dvě různá slova. V tomto příkladu by být označeny "Nástrojů" a "Název".

Zásady vytváření názvů zadejte obecný vzhled pro knihovny cílené modul common language runtime. Tím se snižuje křivky learning, který je vyžadován pro nové knihovny softwaru a zvyšuje sebejistotu zákazníka, knihovny byla vyvinuta uživatelem s odbornými znalostmi v vývoj spravovaného kódu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Změňte slovo tak, aby je použita správně.

## <a name="change-the-dictionary-language"></a>Změnit jazyk slovníku

Ve výchozím nastavení se používá verze Angličtina (en) nástroj pro kontrolu pravopisu. Pokud chcete změnit jazyk pravopisu, můžete to udělat tak přidáním jednu z těchto atributů k vaší *AssemblyInfo.cs* nebo *AssemblyInfo.vb* souboru:

- Použití <xref:System.Reflection.AssemblyCultureAttribute> zadat jazykovou verzi, pokud jsou vaše prostředky v satelitní sestavení.
- Použití <xref:System.Resources.NeutralResourcesLanguageAttribute> k určení *neutrální jazykovou verzi* vašeho sestavení, pokud vaše prostředky jsou ve stejném sestavení jako váš kód.

> [!IMPORTANT]
> Pokud nastavíte jazykovou verzi na jakoukoli jinou hodnotu než jazykovou verzi na základě angličtina, je tato pravidel nástroje Analýza kódu bezobslužně zakázané.

## <a name="when-to-suppress-warnings"></a>Při potlačení upozornění

Je bezpečné potlačit upozornění na toto pravidlo, pokud jsou obě části složené slovo rozpoznáno slovníku a je použít dvě slova.

Můžete také přidat složených slov do slovníku pro kontrolu pravopisu. Vlastní slovník nezpůsobí narušení. Další informace najdete v tématu [postupy: přizpůsobení slovníku analýzy kódu](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Související pravidla

- [CA1702: Malá a velká písmena složených slov by měla být použita správně](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)
- [CA1709: Malá a velká písmena identifikátorů by měla být použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Identifikátory by se měly lišit více než použitím malých a velkých písmen](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Viz také

- [Konvence pro malá a velká písmena](/dotnet/standard/design-guidelines/capitalization-conventions)
- [Pokyny pro pojmenování](/dotnet/standard/design-guidelines/naming-guidelines)