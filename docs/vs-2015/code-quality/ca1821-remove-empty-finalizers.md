---
title: 'CA1821: odebrat prázdné finalizační metody | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a2e704202773447e353f041df66b05cb5f648c00
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545350"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Odeberte prázdné finalizační metody
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|Kategorie|Microsoft. Performance|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Typ implementuje finalizační metodu, která je prázdná, volá pouze finalizační metodu základního typu nebo volá pouze podmíněně emitované metody.

## <a name="rule-description"></a>Popis pravidla
 Kdykoli je to možné, vyhněte se použití finalizačních metod kvůli dodatečným nárokům na výkon spojeným se sledováním životního cyklu objektu. Systém uvolňování paměti spustí finalizační metodu před tím, než bude objekt shromažďovat. To znamená, že ke shromáždění objektu budou požadovány dvě kolekce. Prázdná finalizační metoda má tuto přidanou režii bez jakýchkoli výhod.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Odeberte prázdný finalizační metodu. Pokud je pro ladění vyžadován finalizační metoda, vložte celý finalizační metodu do `#if DEBUG / #endif` direktiv.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit zprávu od tohoto pravidla. Nepovedlo se potlačit konečné snížení výkonu a neposkytuje žádné výhody.

## <a name="example"></a>Příklad
 Následující příklad ukazuje prázdný finalizační metodu, která by měla být odebrána, finalizační metoda, která by měla být uzavřena do `#if DEBUG / #endif` direktiv a finalizační metoda, která používá `#if DEBUG / #endif` direktivy správně.

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RemoveEmptyFinalizers/cs/FxCop.Performance.RemoveEmptyFinalizers.cs#1)]
