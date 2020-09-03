---
title: Značka zobrazení | Microsoft Docs
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
ms.openlocfilehash: c9a0537e146ead1c163941a0f552bdea7a28b89c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74773965"
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
- [ Okno řízení kolekce dat&#93;&#91;NIB](https://msdn.microsoft.com/98d740d8-459f-4605-bf04-fb17aafaaa8f)
