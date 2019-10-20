---
title: Sada pravidel Spravovaná minimální pravidla pro spravovaný kód
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: efb282d8876d48d4f8e7eb81963719e2d14e5900
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649259"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Sada pravidel Spravovaná minimální pravidla pro spravovaný kód

Spravovaná minimální pravidla se zaměřují na nejdůležitější problémy v kódu, včetně možných bezpečnostních otvorů, chyb aplikací a dalších důležitých chyb logiky a návrhu. Zahrňte tuto sadu pravidel do jakékoli vlastní sady pravidel, kterou vytvoříte pro vaše projekty.

|Pravidlo|Popis|
|----------|-----------------|
|[CA1001](../code-quality/ca1001.md)|Typy, které vlastní uvolnitelné pole, by měly být uvolnitelné|
|[CA1821](../code-quality/ca1821.md)|Odeberte prázdné finalizační metody|
|[CA2213](../code-quality/ca2213.md)|Uvolnitelná pole by měla být uvolněna|
|[CA2231](../code-quality/ca2231.md)|Operátor přetížení se rovná při přepsání `ValueType.Equals`|
