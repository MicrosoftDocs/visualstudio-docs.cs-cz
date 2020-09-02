---
title: Sestava značek | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64808269"
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