---
title: Porovnání výsledků zátěžového testu
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, reporting
- load tests, results
ms.assetid: 31874114-459a-45d5-9f8b-2ea503627db8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d2390b7efde62d475008dcb17aa24ed69ebf4bf5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288842"
---
# <a name="report-load-tests-results-for-test-comparisons-or-trend-analysis"></a>Výsledky testů zatížení sestav pro porovnání testů nebo analýzy trendů

Můžete generovat sestavy zátěžového testu v aplikaci Microsoft Excel, které jsou založeny na dvou nebo více výsledcích testů.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

K dispozici jsou dva typy sestav zátěžových testů:

- Spustit porovnání &mdash; Tato sestava je ve skutečnosti dvě sestavy, které zobrazují data souběžného porovnání pomocí tabulek a pruhových grafů.

- Trend můžete &mdash; vygenerovat analýzu trendů ve dvou nebo více sestavách. Výsledky se zobrazí ve spojnicových grafech.

Každá sestava se dá použít ke sdílení dat o výkonu se zúčastněnými stranami a vyjadřuje, jestli celkový výkon a stav systému je lepší nebo horší.

Definice sestav jsou uloženy v databázi zátěžového testu. Při uložení sestavy je definice sestavy uložena v databázi a lze ji později znovu použít.

Soubor tabulky se taky může sdílet se zúčastněnými stranami, aby se zúčastněné strany nemuseli připojovat k databázi, aby se zobrazila sestava.

> [!NOTE]
> Pokud přidáte komentáře do zátěžového testu, zobrazí se v sestavě aplikace Excel.

## <a name="tasks"></a>Úlohy

|Úlohy|Přidružená témata|
|-|-|
|**Vytvoření sestavy výkonu a zátěže:** Můžete vytvářet sestavy pro zátěžové a webové testy výkonu pomocí aplikace Microsoft Excel.|- [Postupy: vytváření sestav výkonu zátěžového testu pomocí aplikace Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)|
|**Ruční vytvoření sestavy výkonu a zátěže pomocí Microsoft Wordu:** Můžete vytvořit sestavy pro testy výkonu zatížení a webu ručně zkopírováním a vložením dat souhrnu, tabulky a grafu do dokumentu aplikace Microsoft Word.|- [Postupy: Ruční vytvoření sestavy výkonu zátěžového testu pomocí Microsoft Wordu](../test/how-to-manually-create-a-load-test-performance-report-using-microsoft-word.md)|

## <a name="see-also"></a>Viz také

- [Analyzovat výsledky zátěžového testu](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
