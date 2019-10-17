---
title: 'CA1724: Názvy typů by neměly odpovídat oborům názvů'
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e5ab83a73da6035df985b93294f850b5a49248f
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72443449"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: názvy typů by neměly odpovídat oborům názvů

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Kategorie|Microsoft. pojmenování|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Název typu odpovídá názvu odkazovaného oboru názvů, který má jeden nebo více externě viditelných typů. Porovnání názvů rozlišuje velká a malá písmena.

## <a name="rule-description"></a>Popis pravidla

Uživatelem vytvořené názvy typů by neměly odpovídat názvům odkazovaných oborů názvů, které mají externě viditelné typy. Porušení tohoto pravidla může snížit použitelnost knihovny.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Přejmenujte typ tak, aby se neshodoval s názvem odkazovaného oboru názvů, který má externě viditelné typy.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Pro nový vývoj se nevyskytují žádné známé scénáře, kdy je nutné potlačit upozornění od tohoto pravidla. Před potlačením upozornění pečlivě zvažte, jak může být uživatelům vaší knihovny zaměněno pomocí odpovídajícího názvu. U přenosných knihoven možná budete muset potlačit upozornění od tohoto pravidla.
