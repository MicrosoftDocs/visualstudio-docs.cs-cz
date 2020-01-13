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
ms.openlocfilehash: c4da0414c9923a8ed7bb01456f38000433641522
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919224"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Malá a velká písmena identifikátorů by měla být použita správně
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio najdete v tématu [CA1709: identifikátory by měly být použita správně](/visualstudio/code-quality/ca1709-identifiers-should-be-cased-correctly).

|||
|-|-|
|TypeName|IdentifiersShouldBeCasedCorrectly|
|CheckId|CA1709|
|Kategorie|Microsoft.Naming|
|Narušující změna|Přerušení – při vyvolání v sestaveních, oborech názvů, typech, členech a parametrech.<br /><br /> Nerozdělitelné – při vyvolání v parametrech obecného typu|

## <a name="cause"></a>příčina
 Název identifikátoru není správně použita.

 \- nebo –

 Název identifikátoru obsahuje zkratku se dvěma písmeny a druhé písmeno je malými písmeny.

 \- nebo –

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
