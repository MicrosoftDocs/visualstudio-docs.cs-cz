---
title: 'CA1709: Identifikátory by měly být správně formátováno | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 795bf9c307862195cd9ec70bb2de1f89ca4d1e17
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199547"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Malá a velká písmena identifikátorů by měla být použita správně
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio 2017, najdete v části [CA1709: identifikátory by měly být správně formátováno](https://docs.microsoft.com/visualstudio/code-quality/ca1709-identifiers-should-be-cased-correctly) na webu docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|IdentifiersShouldBeCasedCorrectly|  
|CheckId|CA1709|  
|Kategorie|Microsoft.Naming|  
|Narušující změna|Zásadní – při aktivaci pro sestavení, oborů názvů, typy, členy a parametry.<br /><br /> Bez konce – při vyvolání v parametrech obecného typu.|  
  
## <a name="cause"></a>příčina  
 Název identifikátoru není správně formátováno.  
  
 \- nebo –  
  
 Název identifikátoru obsahuje dvoupísmenné zkratky a druhý písmena jsou malá písmena.  
  
 \- nebo –  
  
 Název identifikátoru obsahuje zkratka tři nebo více velkých písmen.  
  
## <a name="rule-description"></a>Popis pravidla  
 Zásady vytváření názvů poskytují obecný vzhled knihovnám využívajících common language runtime. To snižuje učit se, která vyžaduje nové knihovny softwaru a zvyšuje důvěru zákazníků, že byla vyvinuta knihovny někdo, kdo má odborných znalostí v vývoj spravovaného kódu.  
  
 Podle konvence používají názvy parametrů camelCase; obor názvů, typů a členů názvy používat Pascal velká a malá písmena. V názvu ve formátu camelCase první písmena jsou malá písmena a je první písmeno zbývající slov v názvu na velká písmena. Příklady-ve formátu camelCase názvů, které jsou "packetSniffer", "ioFile" a "fatalErrorCode". Název stylu jazyka Pascal je velké písmeno první písmeno a je první písmeno zbývající slov v názvu na velká písmena. Příklady názvů Pascal malými a velkými písmeny, které jsou "PacketSniffer", "IOFile" a "FatalErrorCode".  
  
 Toto pravidlo rozdělí slova malých a velkých písmen podle názvu a kontroluje všechny slova dvoupísmenné seznamem běžná slova dvou písmen, jako je například "V" nebo "My". Pokud není nalezena shoda, slovo je považován za zkratka. Kromě toho toto pravidlo předpokládá, že našla zkratka, pokud název obsahuje buď čtyři velká písmena v řádku nebo v řádku na konec názvu tři velká písmena.  
  
 Podle konvence dvoupísmenné zkratky používat všechna velká písmena a zkratky tři nebo více znaků používat Pascal velká a malá písmena. Následující příklady používají tyto zásady vytváření názvů: "DB", "Vy", "Cpa" a "Ecma". Následující příklady porušují Tato konvence: ' Vstup/výstup', 'XML' a "Amerického ministerstva obrany" a pro názvy nonparameter, "xp" a "panelu".  
  
 "ID" je speciální malými a velkými písmeny způsobit porušení tohoto pravidla. 'Id' není zkratka, ale je zkratkou pro "Identifikace".  
  
## <a name="how-to-fix-violations"></a>Jak vyřešit porušení  
 Změňte název tak, že je správně formátováno.  
  
## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění  
 Je bezpečné pro potlačení tohoto upozornění, pokud máte vlastní zásady vytváření názvů, nebo pokud tento identifikátor představuje název správný, například název společnosti nebo technologie.  
  
 Můžete také přidat konkrétní podmínky, zkratky a zkratky, které do vlastního slovníku analýzy kódu. Podmínky zadané ve slovníku nezpůsobí porušení tohoto pravidla. Další informace najdete v tématu [postupy: přizpůsobení slovníku analýzy kódu](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
## <a name="related-rules"></a>Související pravidla  
 [CA1708: Identifikátory by se měly lišit více než použitím malých a velkých písmen](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

