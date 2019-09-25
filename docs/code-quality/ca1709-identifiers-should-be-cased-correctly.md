---
title: 'CA1709: Malá a velká písmena identifikátorů by měla být použita správně'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ff614d9fdc4b250bd91abf24908b33d71a182df
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234154"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Malá a velká písmena identifikátorů by měla být použita správně

|||
|-|-|
|TypeName|IdentifiersShouldBeCasedCorrectly|
|CheckId|CA1709|
|Kategorie|Microsoft.Naming|
|Zásadní změna|Přerušení – při vyvolání v sestaveních, oborech názvů, typech, členech a parametrech.<br /><br /> Nerozdělitelné – při vyvolání v parametrech obecného typu|

## <a name="cause"></a>příčina

Název identifikátoru není správně použita.

\- nebo –

Název identifikátoru obsahuje zkratku se dvěma písmeny a druhé písmeno je malými písmeny.

\- nebo –

Název identifikátoru obsahuje akronym o třech nebo více velkých písmenech.

## <a name="rule-description"></a>Popis pravidla

Zásady vytváření názvů poskytují běžný vzhled pro knihovny, které cílí na modul CLR (Common Language Runtime). Tato konzistence snižuje výukovou křivku, která je požadována pro nové knihovny softwaru, a zvyšuje důvěru zákazníků, že knihovna byla vyvinuta někým, kdo má zkušenosti s vývojem spravovaného kódu.

Podle konvence názvy parametrů používají ve stylu CamelCase velká a malá písmena, typy a názvy členů používají název Pascal. V názvu ve stylu CamelCase-použita je první písmeno malé písmeno a první písmeno všech zbývajících slov v názvu je velká písmena. Příklady názvů ve stylu CamelCase-použita jsou `packetSniffer`, `ioFile`a `fatalErrorCode`. V názvu Pascal-použita je první písmeno velkými písmeny a první písmeno všech zbývajících slov v názvu je velká písmena. Příklady názvů Pascal-použita jsou `PacketSniffer`, `IOFile`a `FatalErrorCode`.

Toto pravidlo rozdělí název na slova na základě velkých a malých písmen a kontroluje všechna slova v seznamu běžných dvou písmen, například "in" nebo "my". Pokud se shoda nenajde, slovo se považuje za akronym. Kromě toho toto pravidlo předpokládá, že našla akronym, když název obsahuje buď čtyři velká písmena v řádku, nebo tři velká písmena v řádku na konci názvu.

Podle konvence používají akronym se dvěma písmeny všechna velká písmena a akronymy se třemi nebo více znaky používají velká a malá písmena Pascal. Tato konvence vytváření názvů se používá v následujících příkladech: ' DB ', ' CR ', ' CPA ' a ' ECMA '. Následující příklady porušují konvenci: ' IO ', ' XML ' a ' DoD ' a pro názvy bez parametrů, ' XP ' a ' cpl '.

' ID ' je speciální – použita způsob porušení tohoto pravidla. ' ID ' není akronym, ale zkratka pro ' Identification '.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Změňte název tak, aby byl použita správně.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Toto upozornění je bezpečné potlačit, pokud máte vlastní konvence pojmenování, nebo pokud identifikátor představuje správný název, například název společnosti nebo technologie.

Můžete také přidat konkrétní výrazy, zkratky a zkratky, které jsou k vlastnímu slovníku nástroje Code Analysis. U podmínek zadaných ve vlastním slovníku nebude porušení tohoto pravidla způsobovat. Další informace najdete v tématu [jak: Přizpůsobení slovníku](../code-quality/how-to-customize-the-code-analysis-dictionary.md)analýzy kódu.

## <a name="related-rules"></a>Související pravidla

[CA1708: Identifikátory by se měly lišit o více než malých písmenech](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)