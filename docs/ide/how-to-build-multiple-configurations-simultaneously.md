---
title: 'Postup: Vytvoření více konfigurací současně'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33cd217a08f62b4919af6d72017176c110cf5e5a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77904084"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Postup: Vytvoření více konfigurací současně

Můžete vytvořit většinu typů projektů s více nebo dokonce všechny jejich konfigurace sestavení současně pomocí dialogového okna **dávkové sestavení.** Nelze však vytvořit následující typy projektů ve více konfiguracích sestavení současně:

1. [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]aplikace vytvořené pro Windows pomocí JavaScriptu.

2. Všechny projekty jazyka.

Pokud řešení obsahuje libovolný projekt těchto dvou typů projektů, **pak dávkové sestavení** není k dispozici pro toto řešení. V takovém případě se příkaz nezobrazí v nabídce **Sestavení.**

   Další informace o konfiguracích sestavení naleznete v [tématu Understand build configurations](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Vytvoření projektu ve více konfiguracích sestavení

1. Na řádku nabídek zvolte **Sestavení** > **dávkového sestavení**. Nebo stisknutím **klávesy Ctrl**+**Q** otevřete `Batch Build`vyhledávací pole a vyhledejte .

2. Ve sloupci **Sestavení** zaškrtněte políčka pro konfigurace, ve kterých chcete vytvořit projekt.

    > [!TIP]
    > Chcete-li upravit nebo vytvořit konfiguraci sestavení pro řešení, zvolte **Vytvořit** > **Nástroj pro konfiguraci na** řádku nabídek a otevřete dialogové okno Správce **konfigurace.** Po úpravě konfigurace sestavení pro řešení zvolte tlačítko **Znovu sestavit** v dialogovém okně **Dávkové sestavení** a aktualizujte všechny konfigurace sestavení pro projekty v řešení.

3. Zvolte **tlačítka sestavení** nebo znovu **sestavit** k sestavení projektu s konfiguracemi, které jste zadali.

## <a name="see-also"></a>Viz také

- [Postup: Vytváření a úpravy konfigurací](../ide/how-to-create-and-edit-configurations.md)
- [Vysvětlení konfigurací sestavení](../ide/understanding-build-configurations.md)
- [Paralelní vytváření více projektů](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)