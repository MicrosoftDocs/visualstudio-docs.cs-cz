---
title: 'CA1030: použijte události, kde je to vhodné | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7ab3a576b5014799e470260567a4942b5c3ef9de
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661925"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Použijte události, kde je to vhodné
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Kategorie|Microsoft. Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Veřejný, chráněný nebo soukromý název metody začíná jedním z následujících způsobů:

- PhotoDraw

- RemoveOn

- Nebezpečí

- Výkop

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo zjišťuje metody, které mají názvy obvykle používané pro události. Události následují za řídicím vzorem pro pozorovatele nebo publikování a odběr. používají se v případě, že změna stavu v jednom objektu musí být předávána jiným objektům. Pokud je metoda volána v reakci na jasně definovanou změnu stavu, metoda by měla být vyvolána obslužnou rutinou události. Objekty volající tuto metodu by měly místo přímého volání metody vyvolat událost.

 Některé běžné příklady událostí jsou k dispozici v aplikacích uživatelského rozhraní, kde akce uživatele, jako je kliknutí na tlačítko, způsobí spuštění segmentu kódu. Model události [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] není omezen na uživatelská rozhraní; měl by se použít všude, kde je nutné sdělit změny stavu jednomu nebo více objektům.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Pokud je metoda volána, když se změní stav objektu, měli byste zvážit změnu návrhu pro použití [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]ho modelu událostí.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačí upozornění z tohoto pravidla, pokud metoda nefunguje s modelem události [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].
