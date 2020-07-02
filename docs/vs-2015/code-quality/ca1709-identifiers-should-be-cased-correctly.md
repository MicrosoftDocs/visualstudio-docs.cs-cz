---
title: 'CA1709: identifikátory by měly být použita správně | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 14c50ed94f05401cc5575af9f8b98472c35b261d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543998"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Malá a velká písmena identifikátorů by měla být použita správně
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio najdete v tématu [CA1709: identifikátory by měly být použita správně](/visualstudio/code-quality/ca1709-identifiers-should-be-cased-correctly).

|Položka|Hodnota|
|-|-|
|TypeName|IdentifiersShouldBeCasedCorrectly|
|CheckId|CA1709|
|Kategorie|Microsoft. pojmenování|
|Narušující změna|Přerušení – při vyvolání v sestaveních, oborech názvů, typech, členech a parametrech.<br /><br /> Nerozdělitelné – při vyvolání v parametrech obecného typu|

## <a name="cause"></a>Příčina
 Název identifikátoru není správně použita.

 \-ani

 Název identifikátoru obsahuje zkratku se dvěma písmeny a druhé písmeno je malými písmeny.

 \-ani

 Název identifikátoru obsahuje akronym o třech nebo více velkých písmenech.

## <a name="rule-description"></a>Popis pravidla
 Zásady vytváření názvů poskytují běžný vzhled pro knihovny, které cílí na modul CLR (Common Language Runtime). Tím se zmenší výuková křivka, která je požadována pro nové knihovny softwaru, a zvyšuje důvěru zákazníků, že knihovna byla vyvinuta někým, kdo má zkušenosti s vývojem spravovaného kódu.

 Podle konvence názvy parametrů používají ve stylu CamelCase velká a malá písmena; obor názvů, typ a názvy členů používají velká a malá písmena Pascal. V názvu ve stylu CamelCase-použita je první písmeno malé písmeno a první písmeno všech zbývajících slov v názvu je velkými písmeny. Příklady názvů ve stylu CamelCase-použita jsou "packetSniffer", "ioFile" a "fatalErrorCode". V názvu Pascal-použita je první písmeno velkými písmeny a první písmeno všech zbývajících slov v názvu je velkými písmeny. Příklady názvů Pascal-použita jsou "PacketSniffer", "IOFile" a "FatalErrorCode".

 Toto pravidlo rozdělí název na slova na základě velkých a malých písmen a kontroluje všechna slova v seznamu běžných dvou písmen, například "in" nebo "my". Pokud se shoda nenajde, slovo se považuje za akronym. Kromě toho toto pravidlo předpokládá, že našla akronym, když název obsahuje buď čtyři velká písmena v řádku, nebo tři velká písmena v řádku na konci názvu.

 Podle konvence používají akronym se dvěma písmeny všechna velká písmena a akronymy se třemi nebo více znaky používají velká a malá písmena Pascal. V následujících příkladech se používají tyto zásady vytváření názvů: ' DB ', ' CR ', ' CPA ' a ' ECMA '. Následující příklady porušují konvenci: ' IO ', ' XML ' a ' DoD ' a pro názvy neparametrs, ' XP ' a ' cpl '.

 ' ID ' je speciální – použita způsob porušení tohoto pravidla. ' ID ' není akronym, ale zkratka pro ' Identification '.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Změňte název tak, aby byl použita správně.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Toto upozornění je bezpečné potlačit, pokud máte vlastní konvence pojmenování, nebo pokud identifikátor představuje správný název, například název společnosti nebo technologie.

 Můžete také přidat konkrétní výrazy, zkratky a zkratky, které jsou k vlastnímu slovníku nástroje Code Analysis. U podmínek zadaných ve vlastním slovníku nebude porušení tohoto pravidla způsobovat. Další informace najdete v tématu [Postup: přizpůsobení slovníku analýzy kódu.](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

## <a name="related-rules"></a>Související pravidla
 [CA1708: Identifikátory by se měly lišit více než použitím malých a velkých písmen](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
