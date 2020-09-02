---
title: Zobrazení procesů | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99ba60021410f1965e05f7c5479231013d53cb71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62904223"
---
# <a name="processes-view"></a>Zobrazení procesů
Zobrazení procesy zobrazuje strom všech aktivních procesů v systému. Zobrazí se ID procesu a název modulu. Použijte zobrazení procesy, pokud chcete prošetřit konkrétní systémový proces, který obvykle odpovídá spuštěnému programu. Procesy se identifikují podle názvů modulů nebo jsou určené "systémové procesy".

 Systém Microsoft Windows podporuje více procesů. Každý proces může mít jeden nebo více vláken a každé vlákno může mít jednu nebo více přidružených oken nejvyšší úrovně. Každé okno nejvyšší úrovně může mít řadu oken. Symbol + označuje, že je úroveň sbalená. Sbalené zobrazení se skládá z jednoho řádku na proces. Kliknutím na symbol + rozbalte úroveň.

 Použijte zobrazení procesy, pokud chcete prošetřit konkrétní systémový proces, který obvykle odpovídá spuštěnému programu. Procesy se identifikují podle názvů modulů nebo jsou určené "systémové procesy". Chcete-li najít proces, sbalte strom a vyhledejte seznam.

## <a name="procedures"></a>Procedury

#### <a name="to-open-the-processes-view"></a>Otevření zobrazení procesů

1. V nabídce **Spy** vyberte možnost **procesy**.

   ![Zobrazení Spy&#43;&#43; ch procesů](../debugger/media/spy--_processes.png "_Processes nástroje Spy + +") Zobrazení procesů Spy + +

   Výše uvedený obrázek ukazuje zobrazení procesů s rozbalenými uzly procesu a vlákna.

### <a name="in-this-section"></a>V tomto oddílu
 [Hledání procesu v zobrazení procesů](../debugger/how-to-search-for-a-process-in-processes-view.md) Vysvětluje, jak najít konkrétní proces v zobrazení procesů.

 [Zobrazení vlastností procesu](../debugger/how-to-display-process-properties.md) Vysvětluje, jak zobrazit další informace o zprávě.

### <a name="related-sections"></a>Související oddíly
 [Zobrazení nástroje Spy + +](../debugger/spy-increment-views.md) Vysvětluje zobrazení stromové struktury nástroje Spy + + pro Windows, zprávy, procesy a vlákna.

 [Pomocí nástroje Spy + +](../debugger/using-spy-increment.md) Zavádí nástroj Spy + + a vysvětluje, jak ho lze použít.

 [Dialogové okno pro hledání procesů](../debugger/process-search-dialog-box.md) Slouží k vyhledání uzlu pro určitý proces v zobrazení procesů.

 [Dialogové okno Vlastnosti procesu](../debugger/process-properties-dialog-box.md) Zobrazí vlastnosti procesu vybraného v zobrazení procesů.

 [Referenční dokumentace nástroje Spy + +](../debugger/spy-increment-reference.md) Obsahuje oddíly popisující jednotlivé nabídky a dialogová okna nástroje Spy + +.