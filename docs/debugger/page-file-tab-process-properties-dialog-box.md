---
title: Karta soubor stránky, dialogové okno Vlastnosti procesu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 624be76badf8d57b060198c2ee910ead17b5efcb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472965"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Karta Soubor stránky, dialogové okno vlastností procesu
Použití **stránkovacího souboru** kartě prozkoumat stránkovacího souboru procesu. Chcete-li zobrazit [dialogové okno Vlastnosti procesu](../debugger/process-properties-dialog-box.md), přesunout fokus na [zobrazení procesů](../debugger/processes-view.md) okno. Vyberte libovolný uzel procesu ve stromové struktuře, a potom vyberte **vlastnosti** z **zobrazení** nabídky.  
  
 Následující nastavení jsou k dispozici na **stránkovacího souboru** kartě:  
  
|Položka|Popis|  
|-----------|-----------------|  
|**Soubor stránky bajtů**|Aktuální počet stránek, které tento proces používá ve stránkovacím souboru. Stránkovací soubor ukládá stránky dat používá proces, ale nejsou obsažené v jiné soubory. Stránkovací soubor je používán všechny procesy a nedostatku místa ve stránkovacím souboru mohou způsobit chyby, když jsou spuštěny jiné procesy.|  
|**Soubor stránky bajtů ve špičce**|Maximální počet stránek, které tento proces se používá ve stránkovacím souboru.|  
|**Chyby stránek**|Počet chyb stránek podprocesů, spuštěných v tomto procesu. Chyby stránky nastane, když vlákno odkazuje na stránku virtuální paměti, která není v jeho pracovní sadě v hlavní paměti. Proto nebude možné stránce načíst z disku Pokud je v seznamu pohotovostní a proto už v hlavní paměti, nebo pokud se právě používá jiná zpracovat stránky se sdílí.|