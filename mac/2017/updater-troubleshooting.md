---
title: Aktualizátor obsahuje chyby načítání informací
description: Pokyny, jak opravit, když se zobrazí chyba "Chyba při načítání informací o aktualizaci". v aplikaci Visual Studio 2017 pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 8825BBAD-65C0-480F-9868-A01E64F28250
ms.topic: troubleshooting
ms.openlocfilehash: c631bae40d06a000e2e90c26ae5a9862c1e09aaa
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2020
ms.locfileid: "85950579"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Řešení potíží: Aktualizátor obsahuje chyby načítání informací

V některých případech se může zobrazit chybová zpráva "Chyba při načítání informací o aktualizaci", která se zobrazí při pokusu o [aktualizaci Visual Studio pro Mac](update.md). Pokud k tomu dojde, vyzkoušejte následující kroky a opravte je:

- Zkontrolujte si připojení k internetu. V rámci připojení je nejčastější příčinou této chyby.
  - Pokud se součást nepovede stáhnout, můžete zkusit stáhnout znovu kliknutím na tlačítko Opakovat vedle názvu součásti.
- Restartujte integrované vývojové prostředí (IDE).
- Pokud se tato chybová zpráva zobrazuje i nadále, můžete se také pokusit aktualizovat pomocí instalačního programu sady Visual Studio 2017 pro Mac, pokud je soubor **. dmg** stále na vašem počítači nebo si ho můžete stáhnout z [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=Visual%20Studio%20for%20Mac) .
  - Instalační program aktualizuje všechny nainstalované komponenty na vašem počítači.
  - Po opětovném spuštění instalačního programu budete moct nainstalovat i všechny chybějící součásti, které jste předtím nenainstalovali.
