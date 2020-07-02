---
title: 'CA1900: pole typu hodnoty by měly být přenosné | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2ece4788a277bfc4d16568d4014f9eae2ed4de33
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545272"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: Pole typů hodnot by měla být přenosná
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio naleznete v tématu [CA1900: pole typu hodnoty by měly být přenosné](/visualstudio/code-quality/ca1900-value-type-fields-should-be-portable).

|Položka|Hodnota|
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|Kategorie|Microsoft. přenositelnost|
|Narušující změna|Přerušení – Pokud se pole může zobrazit mimo sestavení.<br /><br /> Bez přerušení – Pokud pole není viditelné mimo sestavení.|

## <a name="cause"></a>Příčina
 Toto pravidlo kontroluje, zda struktury, které jsou deklarovány s explicitním rozložením, budou správně zarovnány při zařazení do nespravovaného kódu v 64 operačních systémech. IA-64 neumožňuje nezarovnaný přístup k paměti a proces se nezdaří, pokud toto porušení není opraveno.

## <a name="rule-description"></a>Popis pravidla
 Struktury, které mají explicitní rozložení obsahující nesprávně zarovnaná pole, způsobují chyby v 64 operačních systémech.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Všechna pole, která jsou menší než 8 bajtů, musí mít posuny, které mají násobek jejich velikosti, a pole, která jsou 8 bajtů nebo více, musí mít posuny, které jsou násobkem 8. Jiné řešení je vhodné použít `LayoutKind.Sequential` místo `LayoutKind.Explicit` , pokud je to přijatelné.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Toto upozornění by mělo být potlačeno pouze v případě, že dojde k chybě.
