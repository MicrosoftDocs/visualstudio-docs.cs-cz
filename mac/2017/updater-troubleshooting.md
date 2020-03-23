---
title: Aktualizátor obsahuje chyby načítání informací
description: Pokyny, jak opravit, když se zobrazí chyba "Chyba načítání informací o aktualizaci". ve Visual Studiu 2017 pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 8825BBAD-65C0-480F-9868-A01E64F28250
ms.openlocfilehash: 2ff0703171f5854baed2dd9be3767571a930bcb7
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983479"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Poradce při potížích: Updater má chyby načítání informací

Ve výjimečných případech se může zobrazit chybová zpráva "Chyba načítání informací o aktualizaci" při pokusu o [aktualizaci sady Visual Studio for Mac](update.md). Pokud k tomu dojde, vyzkoušejte následující kroky, abyste to opravili:

- Zkontrolujte si připojení k internetu. Drop v připojení je nejčastější příčinou této chyby.
  - Pokud se součást nepodaří stáhnout, můžete klepnutím na tlačítko opakovat vedle názvu komponenty zkusit stahování znovu.
- Restartujte ide.
- Pokud se tato chybová zpráva bude dál zoavnější, můžete se taky pokusit aktualizovat pomocí Instalační služby Visual Studia 2017 pro Mac, pokud je **rozhraní .dmg** stále v počítači nebo si ho můžete stáhnout z [my.visualstudio.com](https://my.visualstudio.com/Downloads?q=Visual%20Studio%20for%20Mac)
  - Instalační program aktualizuje všechny nainstalované součásti v počítači.
  - Opětovným spuštěním instalačního programu budete také moci nainstalovat všechny chybějící součásti, které jste dříve nenainstalovali.
