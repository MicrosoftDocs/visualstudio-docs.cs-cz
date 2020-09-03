---
title: 'Postupy: sestavení více konfigurací'
ms.date: 05/13/2020
ms.technology: vs-ide-compile
ms.topic: how-to
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7820d56bcb266e8361f36cb5350475f31445800
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85284759"
---
# <a name="how-to-build-multiple-configurations-in-a-single-build-request"></a>Postupy: sestavení více konfigurací v rámci jedné žádosti o sestavení

Můžete sestavit většinu typů projektů s více nebo dokonce všechny konfigurace sestavení s jednou akcí IDE pomocí dialogového okna **dávkové sestavení** . Nemůžete však sestavit následující typy projektů ve více konfiguracích sestavení současně:

1. [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikace sestavené pro Windows pomocí JavaScriptu

2. Všechny projekty Visual Basic.

3. Projekty CMake.

Pokud řešení obsahuje libovolný projekt těchto dvou typů projektu, není **dávkové sestavení** pro toto řešení k dispozici. V takovém případě se příkaz nezobrazí v nabídce **sestavení** .

   Další informace o konfiguracích sestavení naleznete v tématu [Principy konfigurací sestavení](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Sestavení projektu v rámci více konfigurací sestavení

1. Na řádku nabídek klikněte na položku **sestavit**  >  **dávkovou sestavování**. Nebo stiskněte klávesu **CTRL** + **Q** pro otevření vyhledávacího pole a vyhledejte `Batch Build` .

2. Ve sloupci **sestavení** zaškrtněte políčka pro konfigurace, ve kterých chcete sestavit projekt.

    > [!TIP]
    > Chcete-li upravit nebo vytvořit konfiguraci sestavení pro řešení, vyberte možnost **sestavit**  >  **Configuration Manager** na řádku nabídek, čímž otevřete dialogové okno **Configuration Manager** . Po úpravě konfigurace sestavení pro řešení klikněte na tlačítko **znovu sestavit** v dialogovém okně **dávkové sestavení** , aby se aktualizovaly všechny konfigurace sestavení pro projekty v řešení.

3. Kliknutím na tlačítko **sestavení** nebo znovu **sestavit** Sestavte projekt s konfiguracemi, které jste určili.

## <a name="see-also"></a>Viz také

- [Postupy: vytváření a úpravy konfigurací](../ide/how-to-create-and-edit-configurations.md)
- [Vysvětlení konfigurací sestavení](../ide/understanding-build-configurations.md)
- [Paralelní sestavení více projektů](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)