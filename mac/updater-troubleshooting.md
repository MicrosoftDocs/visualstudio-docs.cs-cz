---
title: Aktualizátor obsahuje chyby načítání informací
description: Pokyny, jak opravit, když se zobrazí chyba "Chyba při načítání informací o aktualizaci". v aplikaci Visual Studio 2019 pro Mac
ms.topic: troubleshooting
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: 2ccef07a2889f66df3e7f217ea292b61ffc0008f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75405476"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Řešení potíží: Aktualizátor obsahuje chyby načítání informací

V některých případech se může zobrazit chybová zpráva "Chyba při načítání informací o aktualizaci", která se zobrazí při pokusu o [aktualizaci Visual Studio pro Mac](update.md). Pokud k tomu dojde, vyzkoušejte následující kroky a opravte je:

- Zkontrolujte si připojení k internetu. V rámci připojení je nejčastější příčinou této chyby.
  - Pokud se součást nepovede stáhnout, můžete zkusit stáhnout znovu kliknutím na tlačítko Opakovat vedle názvu součásti.
- Restartujte integrované vývojové prostředí (IDE).
- Pokud se tato chybová zpráva zobrazuje i nadále, můžete se také pokusit aktualizovat pomocí instalačního programu, pokud je soubor **. dmg** stále na vašem počítači, nebo si ho můžete stáhnout z [VisualStudio.com](https://visualstudio.microsoft.com/vs/mac/) .
  - Instalační program aktualizuje všechny nainstalované komponenty na vašem počítači.
  - Po opětovném spuštění instalačního programu budete moct nainstalovat i všechny chybějící součásti, které jste předtím nenainstalovali.
- Můžete také zkusit vymazat soubory stažené z mezipaměti tím, že odstraníte soubor umístěný v `~/Library/Caches/VisualStudio/8.0/TempDownload/index.xml` .
- Pokud pracujete se starší verzí Visual Studio pro Mac, můžete mít v adresáři jiná čísla verzí `VisualStudio` . Odstraňte `index.xml` soubor i v těchto cestách.
