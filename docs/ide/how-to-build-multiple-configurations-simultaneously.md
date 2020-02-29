---
title: 'Postupy: sestavení více konfigurací současně'
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
ms.sourcegitcommit: b016ea260856264eee730ee8cbcab198314a7ece
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "77904084"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Postupy: sestavení více konfigurací současně

Většinu typů projektů s více nebo dokonce i všemi konfiguracemi sestavení můžete sestavit současně pomocí dialogového okna **dávkové sestavení** . Nemůžete však sestavit následující typy projektů ve více konfiguracích sestavení současně:

1. [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikace sestavené pro Windows pomocí JavaScriptu.

2. Všechny projekty Visual Basic.

Pokud řešení obsahuje libovolný projekt těchto dvou typů projektu, není **dávkové sestavení** pro toto řešení k dispozici. V takovém případě se příkaz nezobrazí v nabídce **sestavení** .

   Další informace o konfiguracích sestavení naleznete v tématu [Principy konfigurací sestavení](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Sestavení projektu v rámci více konfigurací sestavení

1. Na panelu nabídek vyberte **sestavení** > **dávkové sestavení**. Případně můžete stisknutím klávesy **Ctrl**+**Q** otevřít vyhledávací pole a vyhledat `Batch Build`.

2. Ve sloupci **sestavení** zaškrtněte políčka pro konfigurace, ve kterých chcete sestavit projekt.

    > [!TIP]
    > Chcete-li upravit nebo vytvořit konfiguraci sestavení pro řešení, vyberte možnost **sestavit** > **Configuration Manager** na řádku nabídek, čímž otevřete dialogové okno **Configuration Manager** . Po úpravě konfigurace sestavení pro řešení klikněte na tlačítko **znovu sestavit** v dialogovém okně **dávkové sestavení** , aby se aktualizovaly všechny konfigurace sestavení pro projekty v řešení.

3. Kliknutím na tlačítko **sestavení** nebo znovu **sestavit** Sestavte projekt s konfiguracemi, které jste určili.

## <a name="see-also"></a>Viz také

- [Postupy: vytváření a úpravy konfigurací](../ide/how-to-create-and-edit-configurations.md)
- [Principy konfigurací sestavení](../ide/understanding-build-configurations.md)
- [Paralelní sestavení více projektů](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)