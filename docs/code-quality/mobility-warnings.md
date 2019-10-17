---
title: Upozornění mobility
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bf1d9402294980a2202bbd3ab99c03b5e438eaa
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448857"
---
# <a name="mobility-warnings"></a>Upozornění mobility
Upozornění mobility podporují efektivní využívání energie.

## <a name="in-this-section"></a>V tomto oddílu

|Pravidlo|Popis|
|----------|-----------------|
|[CA1600: Nepoužívejte prioritu nečinného procesu](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Nenastavujte prioritu procesu na Neaktivní. Procesy, které mají nastaveny System.Diagnostics.ProcessPriorityClass.Idle, budou zaměstnávat procesor, pokud by jinak byl nečinný, a tím budou blokovat úsporný režim.|
|[CA1601: Nepoužívejte časovače, které zabraňují změně stavu napájení](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Vyšší frekvence periodické aktivity budou udržovat procesor zaneprázdněný a ovlivňovat časovače úspory energie nečinnosti, které vypnou zobrazení a pevné disky.|
