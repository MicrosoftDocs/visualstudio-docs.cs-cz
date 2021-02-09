---
title: Sada pravidel Spravovaná minimální pravidla pro spravovaný kód
ms.date: 11/04/2016
description: Přečtěte si o sadě pravidel spravované minimální pravidla v sadě Visual Studio, která se zaměřuje na zabezpečení, odolnost a další kritické problémy. Podívejte se na téma popisy pravidel.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 8711fd0a265618a5aaf4f84edcf7dd2b081b16a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859811"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Sada pravidel Spravovaná minimální pravidla pro spravovaný kód

Spravovaná minimální pravidla se zaměřují na nejdůležitější problémy v kódu, včetně možných bezpečnostních otvorů, chyb aplikací a dalších důležitých chyb logiky a návrhu. Zahrňte tuto sadu pravidel do jakékoli vlastní sady pravidel, kterou vytvoříte pro vaše projekty.

|Pravidlo|Description|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Typy, které vlastní uvolnitelné pole, by měly být uvolnitelné|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Odeberte prázdné finalizační metody|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Uvolnitelná pole by měla být uvolněna|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Operátor přetížení se rovná při přepsání. `ValueType.Equals`|
