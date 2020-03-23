---
title: Nastavení více projektů po spuštění
description: Tento článek popisuje, jak nastavit více projektů spustit při spuštění nebo ladění.
author: sayedihashimi
ms.author: sayedha
ms.date: 02/21/2019
ms.topic: conceptual
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: 55519960a6b84968ced43183833167a365e91b35
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "68872315"
---
# <a name="set-multiple-startup-projects"></a>Nastavení více projektů po spuštění

Visual Studio pro Mac umožňuje určit, že více než jeden projekt by měla být spuštěna při ladění nebo spuštění řešení.

## <a name="to-set-multiple-startup-projects"></a>Nastavení více projektů při spuštění

1. V panelu řešení vyberte řešení (horní uzel).

2. Klikněte pravým tlačítkem myši na uzel řešení a potom vyberte **Nastavit projekty po spuštění**:

   ![Vybrat možnost Nastavit projekty po spuštění](media/startup-proj-ctx-menu.png)

3. Otevře se dialogové okno **Vytvořit konfiguraci spuštění řešení.** Toto dialogové okno umožňuje vytvořit nový pojmenovaný Konfigurace spuštění řešení pro vaše řešení. Můžete použít libovolné jméno, které se vám líbí. Výchozí název `Multiple Projects`je .

   ![Dialogové okno Vytvořit konfiguraci spuštění řešení](media/create-sln-run-config.png)

4. Vyberte **možnost Vytvořit konfiguraci spuštění**. Otevře se dialogové okno **Možnosti řešení** s vybranou novou možností Konfigurace spuštění řešení:

   ![Dialogové okno Možnosti řešení](media/sln-options-run-config-multi-projects.png)

5. Vyberte projekty, které chcete spustit při ladění nebo spuštění aplikace z Visual Studia pro Mac:

   ![Dialogové okno Možnosti řešení s vybranými projekty](media/sln-options-run-config-multi-projects-configured.png)

6. Vyberte **OK**. Nová konfigurace spuštění řešení je nastavena jako konfigurace aktivního spuštění:

   ![Řešení s více projekty nakonfigurovanými pro spuštění ladění nebo spuštění](media/startup-project-configured.png)

   Můžete vidět, že dva projekty jsou nakonfigurovány tak, aby spustit, protože oba projekty jsou **tučně** v panelu řešení. V panelu nástrojů je nová konfigurace spuštění nastavena jako aktuální konfigurace spuštění řešení.

## <a name="next-steps"></a>Další kroky

- [Kompilace a vytváření v Visual Studiu pro Mac](compiling-and-building.md)
- [Principy konfigurací sestavení](configurations.md)
