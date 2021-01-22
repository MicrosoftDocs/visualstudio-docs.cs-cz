---
title: Sestava diskových operací (zobrazení vláken) | Microsoft Docs
description: Sestava operací disku zobrazuje vstupně-výstupní operace disku v kanálech disku. Podívejte se, jaké informace jsou hlášeny pro každý přístup k disku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.diskoperations
helpviewer_keywords:
- Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44975999c71b1c331d90aa10f709071cef466cb1
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686529"
---
# <a name="disk-operations-report-threads-view"></a>Sestava diskových operací (Zobrazení vláken)
Sestava operací disku zobrazuje vstupně-výstupní operace disku v kanálech disku.

 Pro každý přístup k disku, ke kterému dochází jménem procesu, který je profilované v okně aktuálně zobrazeného času, se zobrazí tyto informace:

- Název a PID procesu, který provedl přístup k disku

- ID vlákna, které získalo přístup k disku

- Název souboru, ke kterému byl přidaný

- Počet čtení na soubor

- Počet přečtených bajtů

- Latence čtení v milisekundách

- Počet zápisů

- Počet zapsaných bajtů

- Latence zápisu v milisekundách

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)