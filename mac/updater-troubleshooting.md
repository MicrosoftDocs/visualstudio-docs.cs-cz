---
title: Aktualizační program obsahuje chyby při načítání informací
description: Pokyny, jak opravit, když se zobrazí chyba "Chyba při načítání informací o aktualizaci". in Visual Studio 2019 for Mac
ms.topic: troubleshooting
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: b25285ff3060734ee18085d7a9e89cd0d0c43439
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74984401"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Řešení potíží: aktualizace obsahuje chyby, které načítají informace

V některých případech se může zobrazit chybová zpráva "Chyba při načítání informací o aktualizaci", která se zobrazí při pokusu o [aktualizaci Visual Studio pro Mac](update.md). Pokud k tomu dojde, vyzkoušejte následující kroky a opravte je:

- Zkontrolujte připojení k internetu. V rámci připojení je nejčastější příčinou této chyby.
  - Pokud se součást nepovede stáhnout, můžete zkusit stáhnout znovu kliknutím na tlačítko Opakovat vedle názvu součásti.
- Restartujte integrované vývojové prostředí (IDE).
- Pokud se tato chybová zpráva zobrazuje i nadále, můžete se také pokusit aktualizovat pomocí instalačního programu, pokud je soubor **. dmg** stále na vašem počítači, nebo si ho můžete stáhnout z [VisualStudio.com](https://visualstudio.microsoft.com/vs/mac/) .
  - Instalační program aktualizuje všechny nainstalované komponenty na vašem počítači.
  - Po opětovném spuštění instalačního programu budete moct nainstalovat i všechny chybějící součásti, které jste předtím nenainstalovali.
- Můžete také zkusit vymazat soubory stažené z mezipaměti odstraněním souboru umístěného na adrese `~/Library/Caches/VisualStudio/7.0/TempDownload/index.xml`.
