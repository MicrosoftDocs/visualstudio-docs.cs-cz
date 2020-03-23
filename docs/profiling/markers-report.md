---
title: Zpráva o značkách | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9502d2cf0081985cfbee2283af820c06d681ad9f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "64808269"
---
# <a name="markers-report"></a>Sestava značek
Sestava značek obsahuje seznam značek v zobrazeném časovém rámci.  Posouvání nebo zvětšování nebo skrytí pruhů může způsobit, že se značky zobrazí nebo zmizí. Sestava obsahuje tyto informace o každé značce:

- Čas, kdy to začalo, vzhledem k začátku stopy.

- Jeho trvání. Doba trvání je nula pro příznaky a zprávy, protože představují okamžik.

- ID vlákna, které jej vygenerovalo.

- Sledování událostí pro Windows (ETW) zprostředkovatele, který jej vygeneroval.

- Značka série, ze které byl napsán.

- Kategorie událostí, ke kterému patří.

- Jeho úroveň důležitosti.

- Jeho typ (rozpětí, příznak nebo zpráva).

- Popis toho, co představuje na vysoké úrovni

  Zvolte tlačítko **Exportovat,** chcete-li sestavu značek uložit jako soubor CSV. Data v souboru CSV můžete použít s jinými aplikacemi nebo nástroji.

> [!NOTE]
> Sestava značek může zobrazit 1 000 značek. Chcete-li zobrazit všechny značky, exportujte celou sestavu do souboru CSV.