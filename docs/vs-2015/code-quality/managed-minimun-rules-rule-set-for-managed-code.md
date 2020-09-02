---
title: Sada pravidel spravovaná minimální pravidla pro spravovaný kód | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 83f8654a3cca246fa4853add231008e2fadbfc1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667903"
---
# <a name="managed-minimun-rules-rule-set-for-managed-code"></a>Sada pravidel Spravovaná minimální pravidla pro spravovaný kód
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spravovaná minimální pravidla se zaměřují na nejdůležitější problémy v kódu, včetně možných bezpečnostních otvorů, chyb aplikací a dalších důležitých chyb logiky a návrhu. Tuto sadu pravidel byste měli zahrnout v jakékoli vlastní sadě pravidel, kterou vytvoříte pro vaše projekty.

|Pravidlo|Popis|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Typy, které vlastní uvolnitelné pole, by měly být uvolnitelné|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Odeberte prázdné finalizační metody|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Uvolnitelná pole by měla být uvolněna|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Přetižte operátor rovnosti při přetížení ValueType.Equals|
