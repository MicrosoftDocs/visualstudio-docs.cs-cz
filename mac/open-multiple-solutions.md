---
title: 'Postupy: otevření více řešení v sadě Visual Studio pro Mac'
description: Zjistěte, jak otevřít více než jednoho řešení v sadě Visual Studio pro Mac a tom, jak otevřít více než jednu instanci aplikace.
author: conceptdev
ms.author: crdun
ms.date: 07/19/2018
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.openlocfilehash: 76a536f621a3c715a62b9e132dc661a2bcf8eb07
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294926"
---
# <a name="open-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>Otevřít více řešení nebo instance sady Visual Studio pro Mac

Ve výchozím nastavení, všechny aplikace na počítači Mac, včetně sady Visual Studio pro Mac, jsou _jednou instancí_ aplikace. To znamená, že pokud aplikace, kterou chcete použít už otevřené (znázorněný v části ikonu v doku tečkou), znovu vyberte ikonu otevře spuštěnou instanci, nikoli nové. Pokud budete potřebovat další instance aplikace, může vyzvat systém a otevřete ho za vás, jak je popsáno v [další části](#open-a-second-instance-of-visual-studio-for-mac).

Kromě toho když otevřete řešení, výchozí chování je otevřete řešení v nový pracovní prostor a zavřít aktuální pracovní prostor (v případě potřeby). Toto výchozí chování můžete přepsat udržováním aktuální pracovní prostor otevřít, jak je popsáno v [otevřete druhou řešení](#open-a-second-solution-inside-a-single-instance) oddílu.

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>Spusťte druhou instanci aplikace Visual Studio pro Mac

Chcete-li otevřít druhou instanci integrovaného vývojového prostředí (IDE), otevřete **terminálu** aplikace a zadejte následující řádek:

```bash
open -n "/Applications/Visual Studio.app"
```

## <a name="open-a-second-solution-inside-a-single-instance"></a>Otevřete druhou řešení v jediné instance

Chcete-li otevřít druhé řešení spolu s svoje první řešení, postupujte následovně:

1. S svoje první řešení otevřen, vyberte **souboru** > **otevřete**.
2. Procházejte a najít stávající řešení v systému souborů.
3. Vyberte **.sln** a vyberte možnost **možnosti**:

    ![Snímek obrazovky sady Visual Studio pro Mac, soubor .sln a zvýrazněnou možností](media/open-multiple-solutions-image3.png)

4. Zrušte **zavřít aktuální pracovní prostor** pole:

    ![Snímek obrazovky s možností dialogovém okně s zavřít aktuální pracovní prostor políčka](media/open-multiple-solutions-image1.png)

5. Vyberte **otevřete** otevřete druhou řešení v oblasti řešení.

Případně pokud jste nedávno otevřeli řešení, můžete následující kroky:

1. Přejděte na **souboru** > **poslední řešení**.

    ![snímek obrazovky nabídky poslední řešení](media/open-multiple-solutions-image2.png)

1. Podržte stisknutou klávesu **Ctrl** klíče a vyberte řešení. Tato kombinace otevře druhý řešení v oblasti řešení.
