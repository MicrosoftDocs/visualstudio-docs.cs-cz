---
title: Karta okna, dialogové okno Vlastnosti okna | Microsoft Docs
description: Pomocí karty Windows vlastností Windows můžete zobrazit informace o oknech, které souvisejí s vybraným oknem. Nastavení najdete v tomto článku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Windows Tab
ms.assetid: 9001342a-09a8-4f5e-b6ed-881a3b9d7246
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ffc7f8a80e86779f2cc419f841a3b80280f39c9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896400"
---
# <a name="windows-tab-window-properties-dialog-box"></a>Karta Okna, dialogové okno vlastnosti okna
Pomocí karty **Windows** můžete zobrazit informace o systému Windows, které souvisí s vybraným oknem. Chcete-li zobrazit [dialogové okno Vlastnosti okna](../debugger/window-properties-dialog-box.md), přesuňte fokus do okna [zobrazení systému Windows](../debugger/windows-view.md) . Ve stromové struktuře vyberte libovolný uzel okna a pak v nabídce **zobrazení** zvolte možnost **vlastnosti** .

 Na kartě **Windows** jsou k dispozici následující nastavení:

|Entry|Description|
|-----------|-----------------|
|**Další okno**|Obslužná rutina dalšího okna na stejné úrovni ve stejné sekvenci (pořadí vykreslování) zobrazené v zobrazení stromu okna ("none", pokud neexistuje žádné další okno). Výběrem této položky zobrazíte vlastnosti dalšího okna.|
|**Předchozí okno**|Popisovač předchozího okna na stejné úrovni ve stejné sekvenci (pořadí vykreslování) zobrazené v zobrazení stromu okna ("none", pokud neexistuje žádné předchozí okno). Vyberte tuto položku, chcete-li zobrazit vlastnosti předchozího okna.|
|**Nadřazené okno**|Popisovač nadřazeného okna tohoto okna ("none", pokud není k dispozici žádná nadřazená položka). Vyberte tuto položku, chcete-li zobrazit vlastnosti nadřazeného okna.|
|**První podřízená položka**|Obslužná rutina prvního podřízeného okna tohoto okna v sekvenci (pořadí vykreslování) zobrazené v zobrazení stromu okna ("none", pokud nejsou k dispozici žádná podřízená okna). Tuto hodnotu vyberte, chcete-li zobrazit vlastnosti prvního podřízeného okna.|
|**Vlastník – okno**|Popisovač okna vlastníka tohoto okna Hlavní okno aplikace obvykle vlastní dialogová okna v systému, například "none", pokud není k dispozici vlastník). Výběrem této položky zobrazíte vlastnosti okna vlastníka.|