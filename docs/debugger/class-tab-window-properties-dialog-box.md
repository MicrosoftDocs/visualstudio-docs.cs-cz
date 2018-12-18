---
title: Karta třída, dialogové okno Vlastnosti okna | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4afce149a2124ba8caa827b73b258fb421792c13
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31458902"
---
# <a name="class-tab-window-properties-dialog-box"></a>Karta Třída, dialogové okno vlastnosti okna
Použití **třída** karty zobrazíte informace o třídě vybrané okno. Chcete-li zobrazit [dialogové okno Vlastnosti okna](../debugger/window-properties-dialog-box.md), přesunout fokus na [zobrazení oken](../debugger/windows-view.md) okno. Vyberte libovolný uzel okno ve stromové struktuře, a potom vyberte **vlastnosti** z **zobrazení** nabídky.  
  
 Následující nastavení jsou k dispozici na **– třída** karty:  
  
|Položka|Popis|  
|-----------|-----------------|  
|**Název třídy**|Název (nebo řadová číslovka) této třídy oken.|  
|**Styly – třída**|Kombinace kódů styl třídy.|  
|**Bajtů – třída**|Specifické pro aplikaci data související s touto třídou okno.|  
|**Atom – třída**|Atom pro třídu vrácený **RegisterClass** volání.|  
|**Popisovač instance**|Instance popisovače modul, který registrované třídy. Instance popisovače nejsou jedinečné.|  
|**Okno bajtů**|Počet bajtů navíc spojené s každou okno této třídy. Význam těchto bajtů je určen podle aplikace. Rozbalte seznam zobrazíte bajtových hodnot ve formátu DWORD.|  
|**Procedury oken**|Aktuální adresa **WndProc** funkce pro systém windows této třídy. Tím se liší od **okno Proc** na **Obecné** Pokud podtřídou třídy okna.|  
|**Název nabídky**|Název hlavní nabídky, která souvisí s windows této třídy ("žádný" Pokud neexistuje žádné nabídky).|  
|**Ikona popisovač**|Popisovač pro ikonu, která souvisí s windows této třídy ("žádný" Pokud není žádná ikona).|  
|**Popisovač ukazatele**|Popisovač pro kurzor, který je přidružen windows této třídy ("žádný" Pokud neexistuje žádný ukazatel).|  
|**Štětec pozadí –**|Popisovač pro štětec pozadí plochy, která souvisí s windows této třídy, nebo jeden z předdefinovaných COLOR_ * barvy pro vykreslování pozadí okno ("žádný" Pokud neexistuje žádné štětce).|