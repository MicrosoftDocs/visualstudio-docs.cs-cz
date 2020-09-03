---
title: 'CA1707: identifikátory by neměly obsahovat podtržítka | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fe6b90ef971bd00392381f47860d85f34e10dc26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544024"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Identifikátory by neměly obsahovat podtržítka
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio najdete v tématu [CA1707: identifikátory by neměly obsahovat podtržítka](/visualstudio/code-quality/ca1707-identifiers-should-not-contain-underscores).

|Položka|Hodnota|
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Kategorie|Microsoft. pojmenování|
|Narušující změna|Přerušení – při vyvolání na sestavení<br /><br /> Nerozdělitelné – při vyvolání u parametrů typu|

## <a name="cause"></a>Příčina
 Název identifikátoru obsahuje znak podtržítka (_).

## <a name="rule-description"></a>Popis pravidla
 Názvy identifikátorů podle konvence neobsahují znak podtržítka (_). Pravidlo kontroluje obory názvů, typy, členy a parametry.

 Zásady vytváření názvů poskytují běžný vzhled pro knihovny, které cílí na modul CLR (Common Language Runtime). Tím se zmenší výuková křivka, která je požadována pro nové knihovny softwaru, a zvyšuje důvěru zákazníků, že knihovna byla vyvinuta někým, kdo má zkušenosti s vývojem spravovaného kódu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Odebere všechny znaky podtržítka z názvu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="related-rules"></a>Související pravidla
 [CA1709: Malá a velká písmena identifikátorů by měla být použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Identifikátory by se měly lišit více než použitím malých a velkých písmen](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
