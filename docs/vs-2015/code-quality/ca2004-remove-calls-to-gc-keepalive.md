---
title: 'CA2004: odeberte volání GC. Udržení naživu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 53fa5f61cb7c503502956831452bc3eca1a9fece
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85521196"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Odeberte volání GC.KeepAlive
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Kategorie|Microsoft.Reliability|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Třídy používají `SafeHandle` , ale stále obsahují volání `GC.KeepAlive` .

## <a name="rule-description"></a>Popis pravidla
 Pokud převádíte na `SafeHandle` použití, odeberte všechna volání `GC.KeepAlive` (Object). V takovém případě třídy by neměly být volány `GC.KeepAlive` , za předpokladu, že nemají finalizační metodu, ale spoléhají na `SafeHandle` dokončení popisovače operačního systému pro ně.  I když náklady na zanechání v volání `GC.KeepAlive` může být zanedbatelné na základě výkonu, vnímání, že volání `GC.KeepAlive` je buď nezbytné, nebo dostačující k vyřešení potíží při životnosti, která již možná neexistuje, způsobuje, že by se kód těžší udržovat.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Odeberte volání `GC.KeepAlive` .

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Toto upozornění můžete potlačit pouze v případě, že není technicky správné převést na `SafeHandle` využití ve vaší třídě.
