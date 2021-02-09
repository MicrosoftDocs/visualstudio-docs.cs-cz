---
title: Karta Obecné, dialogové okno vlastností procesu | Microsoft Docs
description: Na kartě Obecné si můžete zobrazit informace o procesu, včetně názvu modulu, ID procesu, základní priority, počtu vláken, času procesoru, času uživatele a uplynulého času.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dae82479044df6c031e5aa9f023b17c5e7902965
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870555"
---
# <a name="general-tab-process-properties-dialog-box"></a>Karta Obecné, dialogové okno vlastností procesu
Použijte kartu **Obecné** a zjistěte další informace o konkrétním procesu. Chcete-li zobrazit [dialogové okno Vlastnosti procesu](../debugger/process-properties-dialog-box.md), přesuňte fokus do okna [zobrazení procesů](../debugger/processes-view.md) . Ve stromové struktuře vyberte libovolný uzel procesu a pak v nabídce **zobrazení** zvolte možnost **vlastnosti** .

 Na kartě **Obecné** jsou k dispozici následující nastavení:

|Entry|Description|
|-----------|-----------------|
|**Název modulu**|Název modulu.|
|**ID procesu**|Jedinečné ID tohoto procesu. Čísla ID procesu se znovu používají, takže identifikují proces jenom za dobu života tohoto procesu. Typ objektu procesu se vytvoří při spuštění programu. Všechna vlákna v procesu sdílejí stejný adresní prostor a mají přístup ke stejným datům.|
|**Základ priority**|Aktuální základní priorita tohoto procesu. Vlákna v rámci procesu mohou zvýšit a snížit svou vlastní základní prioritu vzhledem k základní prioritě procesu.|
|**Vlákna**|Počet vláken, která jsou aktuálně aktivní v tomto procesu.|
|**Čas procesoru**|Celkový čas procesoru strávený tímto procesem a jeho vlákny. Rovná se času uživatele a privilegovaného času.|
|**Čas uživatele**|Kumulativní uplynulý čas, po který vlákna tohoto procesu strávily spouštění kódu v uživatelském režimu v nečinných vláknech. Aplikace se spouští v uživatelském režimu jako subsystémy, jako je například správce oken a grafický modul.|
|**Privilegovaný čas**|Celkový uplynulý čas, po který tento proces běžel v privilegovaném režimu v nečinných vláknech. Vrstva služby, rutiny pro vedení a jádro se spouštějí v privilegovaném režimu. Ovladače zařízení pro většinu zařízení kromě grafických adaptérů a tiskáren se také spouštějí v privilegovaném režimu. Některá práce, kterou systém Windows pro vaši aplikaci může zobrazit v jiných procesech subsystému kromě privilegovaného času.|
|**Uplynulý čas**|Celkový uplynulý čas, který tento proces běžel.|