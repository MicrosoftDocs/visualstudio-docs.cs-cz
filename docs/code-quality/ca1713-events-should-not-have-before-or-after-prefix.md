---
title: 'CA1713: Události by neměly mít předponu před nebo po'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 834c0f73a1fdc26f06c62e1c6e3a2d19372a244d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234099"
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713: Události by neměly mít předponu před nebo po

|||
|-|-|
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|
|CheckId|CA1713|
|Kategorie|Microsoft.Naming|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Název události začíná na ' before ' nebo ' After '.

## <a name="rule-description"></a>Popis pravidla
Názvy událostí by měly popsat akci, která vyvolá událost. Pro pojmenování souvisejících událostí vyvolaných v určitém pořadí je vhodné používat přítomný a minulý čas, který naznačí relativní pozici v pořadí akcí. Například při pojmenovávání páru událostí, které jsou vyvolány při zavírání prostředku, můžete pojmenovat klíčové slovo ' Zavřít ' a ' Zavřít ' namísto ' BeforeClose ' a ' AfterClose '.

Zásady vytváření názvů poskytují běžný vzhled pro knihovny, které cílí na modul CLR (Common Language Runtime). Tím se zmenší výuková křivka, která je požadována pro nové knihovny softwaru, a zvyšuje důvěru zákazníků, že knihovna byla vyvinuta někým, kdo má zkušenosti s vývojem spravovaného kódu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Odeberte předponu z názvu události a zvažte změnu názvu tak, aby používala stávající nebo poslední vhodné operace.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.