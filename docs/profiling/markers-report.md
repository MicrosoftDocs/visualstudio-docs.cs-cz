---
title: Sestava značek | Microsoft Docs
description: Přečtěte si, jak sestava značek zobrazuje seznam značek v zobrazeném časovém intervalu a jakým způsobem může zobrazení nebo přiblížení značek způsobit zobrazení nebo zmizení značek.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3b674a2051a0b8b7b96a9c9bf0fb114f0fef46e1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876924"
---
# <a name="markers-report"></a>Sestava značek
Sestava značek obsahuje seznam značek v zobrazeném časovém rámci.  Posouvání nebo přiblížení nebo skrývání drah může způsobit zobrazení značek nebo zmizení. Sestava obsahuje tyto informace o každé značce:

- Čas, kdy byl zahájen, vzhledem k začátku trasování.

- Doba jeho trvání. Doba trvání je nulová pro příznaky a zprávy, protože představují okamžitý.

- ID vlákna, které vygenerovalo.

- Zprostředkovatel sledování událostí pro Windows (ETW), který ji vygeneroval.

- Série značek, ze které byla napsána.

- Kategorie událostí, ke kterým patří.

- Úroveň důležitosti.

- Jeho typ (span, příznak nebo zpráva).

- Popis toho, co to představuje, na nejvyšší úrovni

  Kliknutím na tlačítko **exportovat** uložte sestavu značek jako soubor CSV. Data v souboru CSV můžete použít i v jiných aplikacích nebo nástrojích.

> [!NOTE]
> Sestava značek může zobrazit 1 000 značek. Chcete-li zobrazit všechny značky, exportujte celou sestavu do souboru CSV.