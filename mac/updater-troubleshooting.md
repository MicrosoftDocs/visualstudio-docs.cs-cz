---
title: Aktualizátor obsahuje chyby načítání informací
description: Pokyny, jak opravit, když se zobrazí chyba "Chyba načítání informací o aktualizaci". ve Visual Studiu 2019 pro Mac
ms.topic: troubleshooting
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: 2ccef07a2889f66df3e7f217ea292b61ffc0008f
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75405476"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Poradce při potížích: Updater má chyby načítání informací

Ve výjimečných případech se může zobrazit chybová zpráva "Chyba načítání informací o aktualizaci" při pokusu o [aktualizaci sady Visual Studio for Mac](update.md). Pokud k tomu dojde, vyzkoušejte následující kroky, abyste to opravili:

- Zkontrolujte si připojení k internetu. Drop v připojení je nejčastější příčinou této chyby.
  - Pokud se součást nepodaří stáhnout, můžete klepnutím na tlačítko opakovat vedle názvu komponenty zkusit stahování znovu.
- Restartujte ide.
- Pokud se tato chybová zpráva bude dál zoavnější, můžete se také pokusit aktualizovat pomocí instalačního programu, pokud je **rozhraní .dmg** stále v počítači nebo jej můžete stáhnout z [visualstudio.com](https://visualstudio.microsoft.com/vs/mac/)
  - Instalační program aktualizuje všechny nainstalované součásti v počítači.
  - Opětovným spuštěním instalačního programu budete také moci nainstalovat všechny chybějící součásti, které jste dříve nenainstalovali.
- Můžete také zkusit vymazat soubory ke stažení uložené v `~/Library/Caches/VisualStudio/8.0/TempDownload/index.xml`mezipaměti odstraněním souboru umístěného na adrese .
- Pokud pracujete se starší verzí Visual Studia pro Mac, můžete mít `VisualStudio` pod adresářem další čísla verzí. Odstraňte `index.xml` také soubor v těchto cestách.
