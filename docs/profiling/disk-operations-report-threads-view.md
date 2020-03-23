---
title: Sestava operací disku (zobrazení vláken) | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 69cbef53bcca74cceba4f9409b578fca45a58806
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62970067"
---
# <a name="disk-operations-report-threads-view"></a>Sestava diskových operací (Zobrazení vláken)
Sestava operací disku zobrazuje vstupně-nosné operace disku v diskových kanálech.

 Pro každý přístup k disku, ke kterému dochází jménem procesu, který je profilován v aktuálně viditelném časovém okně, jsou tyto informace hlášeny:

- Název a PID procesu, který provedl přístup k disku

- ID vlákna, které přistupovalo k disku

- Název souboru, ke kterému byl přistupován

- Počet čtení na soubor

- Počet přečtených bajtů

- Latence čtení v milisekundách

- Počet zápisů

- Počet zapsaných bajtů

- Latence zápisu v milisekundách

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)