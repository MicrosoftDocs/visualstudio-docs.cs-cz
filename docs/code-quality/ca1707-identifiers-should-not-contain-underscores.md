---
title: 'CA1707: Identifikátory by neměly obsahovat podtržítka'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ba9e8dda927edca08565b088cbde90d63443908
ms.sourcegitcommit: 3e94d9fb6dc56fa8b23fbacd5d11cf8d6e7e18f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252571"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Identifikátory by neměly obsahovat podtržítka

|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Category|Microsoft.Naming|
|Zásadní změna|Přerušení – při vyvolání na sestavení<br /><br /> Nerozdělitelné – při vyvolání u parametrů typu|

## <a name="cause"></a>Příčina

Název identifikátoru obsahuje znak podtržítka (\_).

## <a name="rule-description"></a>Popis pravidla

Podle konvence názvy identifikátorů neobsahují znak podtržítka (\_). Pravidlo kontroluje obory názvů, typy, členy a parametry.

Zásady vytváření názvů poskytují běžný vzhled pro knihovny, které cílí na modul CLR (Common Language Runtime). Tím se zmenší výuková křivka, která je požadována pro nové knihovny softwaru, a zvyšuje důvěru zákazníků, že knihovna byla vyvinuta někým, kdo má zkušenosti s vývojem spravovaného kódu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Odebere všechny znaky podtržítka z názvu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Potlačit upozornění pro produkční kód. Je však bezpečné potlačit toto upozornění pro testovací kód. Upozornění můžete z tohoto pravidla potlačit nastavením jeho [závažnosti](use-roslyn-analyzers.md#rule-severity) na **None (žádné**). 

## <a name="related-rules"></a>Související pravidla

- [CA1709: Identifikátory by se měly použita správně @ no__t-0.
- [CA1708: Identifikátory by se měly lišit o více než případu @ no__t-0.
