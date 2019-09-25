---
title: 'CA1809: Vyhněte se nadměrným lokálním hodnotám'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89d6ee4d1a53f63cffb31439a124d3d9358e976f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233649"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Vyhněte se nadměrným lokálním hodnotám

|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Kategorie|Microsoft. Performance|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Člen obsahuje více než 64 místních proměnných, z nichž některé mohou být generovány kompilátorem.

## <a name="rule-description"></a>Popis pravidla
Běžnou optimalizací výkonu je uložení hodnoty v registru procesoru místo v paměti, která se označuje jako *zaregistrování* hodnoty. Modul CLR (Common Language Runtime) zohledňuje až 64 místních proměnných pro enregistration. Proměnné, které nejsou registrován, jsou vloženy do zásobníku a musí být před manipulací přesunuty do registru. Pro umožnění pravděpodobnosti, že všechny místní proměnné získají registrován, omezte počet místních proměnných na 64.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, refaktorujte implementaci, aby nepoužívala více než 64 místních proměnných.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Je bezpečné potlačit upozornění z tohoto pravidla nebo zakázat pravidlo, pokud se nejedná o problém s výkonem.

## <a name="related-rules"></a>Související pravidla
[CA1804: Odebrat nepoužívané místní hodnoty](../code-quality/ca1804-remove-unused-locals.md)