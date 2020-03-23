---
title: 'Postup: Otevření více řešení'
description: Zjistěte, jak otevřít více než jedno řešení v Sadě Visual Studio pro Mac a jak otevřít více než jednu instanci aplikace.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/19/2018
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.custom: video
ms.openlocfilehash: 3568ab8dd68deb83d668c6e46f556516e29a81ae
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74985008"
---
# <a name="open-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>Otevření více řešení nebo instancí Visual Studia pro Mac

Ve výchozím nastavení jsou všechny aplikace na Macu, včetně Visual Studia pro Mac, aplikace _s jednou instancí._ To znamená, že pokud je aplikace, kterou chcete použít, již otevřená (znázorněno tečkou pod ikonou v doku), výběrem ikony znovu otevřete spuštěnou instanci, nikoli novou. Pokud požadujete další instance aplikace, můžete systém vyzvat k jeho otevření, jak je popsáno v [další části](#open-a-second-instance-of-visual-studio-for-mac).

Kromě toho při otevření řešení je výchozí chování otevřít řešení v novém pracovním prostoru a zavřete aktuální pracovní prostor (v případě potřeby). Toto výchozí chování můžete přepsat tak, že aktuální pracovní prostor ponesete tak, jak je popsáno v části [Otevřít druhé řešení.](#open-a-second-solution-inside-a-single-instance)

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>Otevření druhé instance Visual Studia pro Mac

Chcete-li otevřít druhou instanci integrovaného vývojového prostředí (IDE), otevřete aplikaci **Terminál** a zadejte následující řádek:

```bash
open -n "/Applications/Visual Studio.app"
```

## <a name="open-a-second-solution-inside-a-single-instance"></a>Otevření druhého řešení uvnitř jedné instance

Chcete-li otevřít druhé řešení vedle prvního řešení, použijte následující kroky:

1. Když je první řešení již otevřené, vyberte **Soubor** > **otevřít**.
2. Vyhledejte existující řešení v systému souborů.
3. Vyberte soubor **.sln** a vyberte **Možnosti**:

    ![Snímek obrazovky Visual Studia pro Mac se zvýrazněným souborem .sln a možnostmi](media/open-multiple-solutions-image3.png)

4. Zrušte zaškrtnutí políčka **Zavřít aktuální pracovní plochu:**

    ![Snímek obrazovky s dialogovým oknem Možnosti s nezaškrtnutou možností Zavřít aktuální pracovní plochu](media/open-multiple-solutions-image1.png)

5. Výběrem **možnosti Otevřít** otevřete druhé řešení v panelu řešení.

Případně pokud jste nedávno otevřeli řešení, můžete použít následující kroky:

1. Přejděte na **soubor** > **posledních řešení**.

    ![Snímek obrazovky s nabídkou Nedávná řešení](media/open-multiple-solutions-image2.png)

1. Podržte stisknutou klávesu **Ctrl** a vyberte řešení. Tato kombinace otevírá druhé řešení v panelu řešení.

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Work-With-Multiple-Solutions/player]
