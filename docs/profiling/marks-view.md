---
title: Značka zobrazení | Microsoft Docs
description: Přečtěte si, jak zobrazení značek zobrazuje vzorkování a události ETW, které byly vloženy do aplikace.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.marks
helpviewer_keywords:
- profiling tools, Marks view
- profiling tools reports, Marks view
ms.assetid: b2773344-8081-4116-85a1-58f770448f6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 969bf0debfc1da9f7ca1763d8c9c001d565ce64a
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98718977"
---
# <a name="marks-view"></a>Zobrazení značek
Zobrazení značky zobrazuje vzorkování a události ETW, které byly vloženy do aplikace.

 Výchozí značky, které jsou předem vyplněné v sestavě, jsou označeny jako začátek programu a koncem programu.

 V tomto zobrazení se zobrazují také data čítačů systému Windows z automaticky generovaných značek. Další informace najdete v tématu [Postup: shromažďování dat čítače Windows](../profiling/how-to-collect-windows-counter-data.md).

 Chcete-li vytvořit filtr mezi dvěma značkami, vyberte značky, klikněte pravým tlačítkem myši a pak klikněte na **Přidat filtr podle značky** nebo **Přidat filtr podle časového razítka**.

 Následující tabulka poskytuje definice sloupců, které jsou k dispozici v zobrazení značek.

 **ID značky** Jedinečný identifikátor značky profilace.

 **Název značky** Název události.

 **Časové razítko** Čas od začátku profilace až do doby, kdy se událost zaznamená.

 Data čítačů výkonu systému Windows při shromažďování dat čítače výkonu systému Windows hodnoty jsou zobrazeny ve sloupci s názvem čítače.

## <a name="see-also"></a>Viz také
- [Přehled sestavy výkonu](../profiling/performance-report-overview.md)
- [Postupy: shromažďování dat čítače Windows](../profiling/how-to-collect-windows-counter-data.md)
- [ Okno řízení kolekce dat&#93;&#91;NIB](/previous-versions/bb385767(v=vs.110))