---
title: 'Postupy: otevření více řešení'
description: Naučte se, jak otevřít více než jedno řešení v Visual Studio pro Mac a jak otevřít více než jednu instanci aplikace.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/19/2018
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.custom: video
ms.openlocfilehash: 3568ab8dd68deb83d668c6e46f556516e29a81ae
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74985008"
---
# <a name="open-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>Otevřete více řešení nebo instancí Visual Studio pro Mac

Ve výchozím nastavení jsou všechny aplikace na Macu, včetně Visual Studio pro Mac, aplikace s _jednou instancí_ . To znamená, že pokud je aplikace, kterou chcete použít, už otevřená (znázorněná tečkou pod ikonou v Docku), pak se znovu vybere ikona se spuštěnou instancí namísto nového. Pokud požadujete další instance aplikace, můžete si systém vyzvat, aby ho otevřel za vás, jak je popsáno v [následující části](#open-a-second-instance-of-visual-studio-for-mac).

Kromě toho, když otevřete řešení, výchozí chování je otevřít řešení v novém pracovním prostoru a zavřít aktuální pracovní prostor (v případě potřeby). Toto výchozí chování můžete přepsat tak, že zachováte otevřený aktuální pracovní prostor, jak je popsáno v části [otevření druhého řešení](#open-a-second-solution-inside-a-single-instance) .

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>Otevření druhé instance Visual Studio pro Mac

Chcete-li otevřít druhou instanci integrovaného vývojového prostředí (IDE), otevřete aplikaci **terminálu** a zadejte následující řádek:

```bash
open -n "/Applications/Visual Studio.app"
```

## <a name="open-a-second-solution-inside-a-single-instance"></a>Otevřít druhé řešení v rámci jedné instance

Pokud chcete otevřít druhé řešení společně s vaším prvním řešením, použijte následující postup:

1. Když máte vaše první řešení otevřené, vyberte **soubor** > **otevřít**.
2. Procházejte systémem souborů a vyhledejte existující řešení.
3. Vyberte soubor **. sln** a vyberte **Možnosti**:

    ![Snímek obrazovky Visual Studio pro Mac se zvýrazněným souborem. sln a vybranými možnostmi](media/open-multiple-solutions-image3.png)

4. Zrušte zaškrtnutí políčka **Zavřít aktuální pracovní prostor** :

    ![Snímek obrazovky dialogového okna Možnosti s nezaškrtnutým políčkem Zavřít aktuální pracovní prostor](media/open-multiple-solutions-image1.png)

5. Výběrem **otevřít** otevřete druhé řešení v oblast řešení.

Případně, pokud jste řešení nedávno otevřeli, můžete použít následující postup:

1. Přejít na **soubor** > **Poslední řešení**.

    ![Snímek obrazovky s posledními nabídkami řešení](media/open-multiple-solutions-image2.png)

1. Podržte stisknutou klávesu **CTRL** a vyberte řešení. Tato kombinace otevře druhé řešení v Oblast řešení.

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Work-With-Multiple-Solutions/player]
