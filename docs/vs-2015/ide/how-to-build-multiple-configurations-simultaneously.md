---
title: 'Postupy: sestavení více konfigurací současně | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 719b31e834b5410dd137a0c5b69cc07ae01651e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645476"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Postupy: Sestavení více konfigurací současně
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Většinu typů projektů s více nebo dokonce i všemi konfiguracemi sestavení můžete sestavit současně pomocí dialogového okna **dávkové sestavení** . Nemůžete však sestavit následující typy projektů ve více konfiguracích sestavení současně:

1. [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace sestavené pro Windows pomocí JavaScriptu

2. Všechny projekty Visual Basic.

   Další informace o konfiguracích sestavení naleznete v tématu [Principy konfigurací sestavení](../ide/understanding-build-configurations.md).

### <a name="to-build-a-project-in-multiple-build-configurations"></a>Sestavení projektu v rámci více konfigurací sestavení

1. Na řádku nabídek klikněte na položku **sestavení**, **dávkové sestavení**.

2. Ve sloupci **sestavení** zaškrtněte políčka pro konfigurace, ve kterých chcete sestavit projekt.

    > [!TIP]
    > Chcete-li upravit nebo vytvořit konfiguraci sestavení pro řešení, vyberte možnost **sestavit**, **Configuration Manager** na řádku nabídek, čímž otevřete dialogové okno **Configuration Manager** . Po úpravě konfigurace sestavení pro řešení klikněte na tlačítko **znovu sestavit** v dialogovém okně **dávkové sestavení** , aby se aktualizovaly všechny konfigurace sestavení pro projekty v řešení.

3. Kliknutím na tlačítko **sestavení** nebo znovu **sestavit** Sestavte projekt s konfiguracemi, které jste určili.

## <a name="see-also"></a>Viz také
 [Postupy: vytváření a úpravy konfigurací](../ide/how-to-create-and-edit-configurations.md) pro [porozumění konfiguracím sestavení](../ide/understanding-build-configurations.md) [sestavování více projektů paralelně](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
