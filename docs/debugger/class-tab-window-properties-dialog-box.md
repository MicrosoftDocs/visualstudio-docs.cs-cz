---
title: Karta třída, dialogové okno Vlastnosti okna | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0917c9a038b42e6302ec1f1782f095ca397a92ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62565010"
---
# <a name="class-tab-window-properties-dialog-box"></a>Karta Třída, dialogové okno vlastnosti okna
Kartu **Třída** použijte k zobrazení informací o třídě vybraného okna. Chcete-li zobrazit [dialogové okno Vlastnosti okna](../debugger/window-properties-dialog-box.md), přesuňte fokus do okna [zobrazení systému Windows](../debugger/windows-view.md) . Ve stromové struktuře vyberte libovolný uzel okna a pak v nabídce **zobrazení** zvolte možnost **vlastnosti** .

 Následující nastavení jsou k dispozici na kartě **Třída** :

|Entry|Popis|
|-----------|-----------------|
|**Název třídy**|Název (nebo ordinální číslo) této třídy okna.|
|**Styly tříd**|Kombinace kódů stylu třídy.|
|**Bajty třídy**|Data specifická pro aplikaci přidružená k této třídě okna.|
|**Atom třídy**|Atom pro třídu vrácenou voláním metody **registerClass** .|
|**Popisovač instance**|Obslužná rutina instance modulu, který zaregistroval třídu. Obslužné rutiny instancí nejsou jedinečné.|
|**Bajty oken**|Počet přebytečných bajtů spojených s každým oknem této třídy. Význam těchto bajtů určuje aplikace. Rozbalením seznamu zobrazíte hodnoty bajtů ve formátu DWORD.|
|**Procedura okna**|Aktuální adresa funkce **WndProc** pro systém Windows této třídy. To se liší od **procedury okna** na kartě **Obecné** , pokud je okno roztříděné.|
|**Název nabídky**|Název hlavní nabídky, která je přidružena k systému Windows této třídy ("none", pokud není k dispozici žádná nabídka).|
|**Popisovač ikony**|Popisovač pro ikonu, která je přidružena k systému Windows této třídy ("none", pokud není ikona).|
|**Popisovač kurzoru**|Popisovač pro kurzor, který je přidružen k systému Windows této třídy ("none", pokud neexistuje žádný kurzor).|
|**Štětec štětec**|Popisovač pozadí štětce, který je spojen s Windows této třídy, nebo jednu z předdefinovaných COLOR_ * barev pro vykreslování pozadí okna ("none", pokud není k dispozici žádný štětec).|