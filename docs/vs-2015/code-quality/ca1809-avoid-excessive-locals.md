---
title: 'CA1809: Vyhněte se nadměrným lokálním hodnotám | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d39c8d9d09cf457738df87e3c2e6e109f7bc1696
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543855"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Vyhněte se nadměrným lokálním hodnotám
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Kategorie|Microsoft. Performance|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Člen obsahuje více než 64 místních proměnných, z nichž některé mohou být generovány kompilátorem.

## <a name="rule-description"></a>Popis pravidla
 Běžnou optimalizací výkonu je uložení hodnoty v registru procesoru místo v paměti, která se označuje jako *zaregistrování* hodnoty. Modul CLR (Common Language Runtime) zohledňuje až 64 místních proměnných pro enregistration. Proměnné, které nejsou registrován, jsou vloženy do zásobníku a musí být před manipulací přesunuty do registru. Pro umožnění pravděpodobnosti, že všechny místní proměnné získají registrován, omezte počet místních proměnných na 64.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, refaktorujte implementaci, aby nepoužívala více než 64 místních proměnných.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění z tohoto pravidla nebo zakázat pravidlo, pokud se nejedná o problém s výkonem.

## <a name="related-rules"></a>Související pravidla
 [CA1804: Odeberte nepoužívané lokální hodnoty](../code-quality/ca1804-remove-unused-locals.md)
