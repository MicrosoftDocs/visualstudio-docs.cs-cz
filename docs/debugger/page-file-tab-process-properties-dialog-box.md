---
title: Karta soubor stránky, dialogové okno vlastností procesu | Microsoft Docs
description: K prohlédnutí stránkovacího souboru procesu použijte kartu stránkovací soubor vlastností procesu. Tento článek popisuje dostupná nastavení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47f4a2e9215cb2e98fdfefecdf978cb4a442ad84
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975053"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Karta Soubor stránky, dialogové okno vlastností procesu
Použijte kartu **soubor stránky** k prohlédnutí stránkovacího souboru procesu. Chcete-li zobrazit [dialogové okno Vlastnosti procesu](../debugger/process-properties-dialog-box.md), přesuňte fokus do okna [zobrazení procesů](../debugger/processes-view.md) . Ve stromové struktuře vyberte libovolný uzel procesu a pak v nabídce **zobrazení** zvolte možnost **vlastnosti** .

 Na kartě **soubor stránky** jsou k dispozici následující nastavení:

|Entry|Popis|
|-----------|-----------------|
|**Bajty stránkovacího souboru**|Aktuální počet stránek, které tento proces používá ve stránkovacím souboru. Stránkovací soubor ukládá stránky dat, která proces používá, ale není obsažen v jiných souborech. Stránkovací soubor je používán všemi procesy a nedostatek místa ve stránkovacím souboru může způsobit chyby, pokud jsou spuštěné jiné procesy.|
|**Bajty stránkovacího souboru ve špičce**|Maximální počet stránek, které tento proces použil ve stránkovacím souboru.|
|**Chyby stránky**|Počet chyb stránek podle vláken spuštěných v tomto procesu. K chybě stránky dojde, když vlákno odkazuje na stránku virtuální paměti, která není v pracovní sadě v hlavní paměti. Proto se stránka z disku nenačte, pokud se nachází v pohotovostním seznamu, takže už je v hlavní paměti, nebo pokud ji používá jiný proces, se kterým se stránka sdílí.|