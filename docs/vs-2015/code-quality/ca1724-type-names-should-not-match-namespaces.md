---
title: 'CA1724: názvy typů by neměly odpovídat oborům názvů | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 53c99e34bf253b0962d054685ce637c3849a2857
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671598"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: Názvy typů by neměly odpovídat oborům názvů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Kategorie|Microsoft. pojmenování|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Název typu odpovídá názvům oboru názvů [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] při porovnávání bez rozlišování velkých a malých písmen.

## <a name="rule-description"></a>Popis pravidla
 Názvy typů by neměly odpovídat názvům oborů názvů, které jsou definovány v knihovně tříd [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Porušení tohoto pravidla může snížit použitelnost knihovny.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Vyberte název typu, který se neshoduje s názvem [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] obor názvů knihovny tříd.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pro nový vývoj se nevyskytují žádné známé scénáře, kdy je nutné potlačit upozornění od tohoto pravidla. Před potlačením upozornění pečlivě zvažte, jak může být uživatelům vaší knihovny zaměněno pomocí odpovídajícího názvu. U přenosných knihoven možná budete muset potlačit upozornění od tohoto pravidla.
