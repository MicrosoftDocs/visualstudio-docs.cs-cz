---
title: Karta paměť, dialogové okno Vlastnosti procesu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b43dd047e4ebdb145092dc3b9f37098b8db6322e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474616"
---
# <a name="memory-tab-process-properties-dialog-box"></a>Karta Paměť, dialogové okno vlastností procesu
Použití **paměti** kartě Zobrazit, jak tento proces se používá paměti. Chcete-li zobrazit [dialogové okno Vlastnosti procesu](../debugger/process-properties-dialog-box.md), přesunout fokus na [zobrazení procesů](../debugger/processes-view.md) okno. Vyberte libovolný uzel procesu ve stromové struktuře, a potom vyberte **vlastnosti** z **zobrazení** nabídky.  
  
 Následující nastavení jsou k dispozici na **paměti** karty:  
  
|Položka|Popis|  
|-----------|-----------------|  
|**Virtuální bajty**|Aktuální velikost (v bajtech) prostoru virtuálních adres proces používá. Použití virtuálního adresového prostoru ještě nutně neznamená odpovídající použití buď disku nebo stránek hlavní paměti. Ale virtuální prostor je omezený a pomocí příliš mnoho může omezit schopnost procesu načítat knihovny.|  
|**Virtuální bajty ve špičce**|Maximální počet bajtů virtuálního adresového prostoru procesu se používá v daném okamžiku.|  
|**Pracovní sada**|Sada stránek paměti nedávno přistupovaly vláken v procesu. Pokud volné paměti v počítači je nad prahovou hodnotou, ponechají se stránky v pracovní sadě procesu, i když nejsou v použití. Když volná paměť počítače klesne pod prahovou hodnotu, jsou oříznut stránky z pracovní sady. Pokud jsou potřeba, budou se softwarovou chybou zpátky do pracovní sady před opuštěním hlavní paměti.|  
|**Nejvyšší velikost pracovní sady**|Maximální počet stránek v pracovní sadě procesu v libovolného bodu v čase.|  
|**Bajty stránkovaného fondu**|Aktuální velikost stránkovaného fondu proces alokoval. Stránkovaný fond je systémová oblast paměti kde komponent operačního systému získat místo podle jejich provedení jejich určených úloh. Stránkovaný fond stránky může být stránkování na stránkovacího souboru přistupováno není systémem pro dlouhodobě období.|  
|**Bajty nestránkovaného fondu**|Aktuální počet bajtů ve nestránkovaného fondu přidělené procesem. Nestránkovaného fondu je systémová oblast paměti kde místa se získávají pomocí součásti operačního systému jako jejich provedení jejich určených úloh. Nestránkovaného fondu stránky nemůže být stránkování na stránkovacího souboru; zůstanou v hlavní paměti, dokud jejich přidělení.|  
|**Soukromé bajty**|Aktuální počet bytů, které tento proces alokoval, které nelze sdílet s jinými procesy.|  
|**Volných bajtů**|Celkový počet nepoužívané virtuální adresní prostor tohoto procesu.|  
|**Vyhrazené bajtů**|Celková velikost virtuální paměti vyhrazené pro budoucí použití tohoto procesu.|  
|**Volné Image bajtů**|Velikost virtuálního adresového prostoru, který se nepoužívá, nebo vyhrazený pro bitové kopie v rámci tohoto procesu.|  
|**Vyhrazené Image bajtů**|Součet všech virtuální paměti vyhrazené bitové kopie spustit v rámci tohoto procesu.|