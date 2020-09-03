---
title: Vytváření a úpravy konfigurací sestavení
description: Tento článek popisuje vytvoření konfigurací sestavení v Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: CC1B72D6-12FF-4CCC-A9D4-00F2DC14589F
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: eb3ceed624e3bbba67564bb8f7c359841c0e496d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85939186"
---
# <a name="creating-and-editing-build-configurations"></a>Vytváření a úpravy konfigurací sestavení

Konfigurace sestavení vám poskytují přesnou kontrolu nad sestavením, které vám umožní vytvářet konfigurace pro stravování v různých situacích testování a distribuce. Můžete vytvářet konfigurace sestavení pro jednotlivé projekty nebo na úrovni jednotlivých řešení.

Pomocí dialogového okna Možnosti projektu můžete vytvořit nové konfigurace a upravit stávající pro oba projekty a řešení.

>[!NOTE]
>Toto téma se týká Visual Studio pro Mac. V případě sady Visual Studio ve Windows, přečtěte si téma [Postupy: vytváření a úpravy konfigurací](/visualstudio/ide/how-to-create-and-edit-configurations).

## <a name="creating-a-project-build-configuration"></a>Vytváření konfigurace sestavení projektu

Chcete-li vytvořit konfiguraci sestavení projektu, použijte následující postup:

1. Klikněte pravým tlačítkem myši na uzel projektu a vyberte **možnost možnosti**. Můžete také dvakrát kliknout na uzel projektu a vyvolat tak dialogové okno Možnosti projektu.

2. V dialogovém okně Možnosti projektu vyberte **sestavení > konfigurace**:

    ![Správce konfigurace v možnostech projektu](media/create-and-edit-configurations-image2.png)

3. Pokud chcete vytvořit novou konfiguraci, vyberte **Přidat** . Můžete také zkopírovat jakoukoli existující konfiguraci.

Po vytvoření konfigurace můžete použít část **sestavení** v možnostech projektu pro přizpůsobení vlastností, které jsou vhodné pro vaši konfiguraci:

![Konfigurovat možnosti sestavení](media/create-and-edit-configurations-image3.png)

## <a name="creating-a-solution-build-configuration"></a>Vytváření konfigurace sestavení řešení

Chcete-li vytvořit konfiguraci sestavení řešení, postupujte podle následujících kroků:

1. Klikněte pravým tlačítkem na uzel řešení a vyberte **Možnosti**. Můžete také dvakrát kliknout na uzel řešení a vyvolat tak dialogové okno Možnosti řešení.

2. V dialogovém okně Možnosti řešení vyberte **sestavení > konfigurace**:

    ![Správce konfigurace v možnostech řešení](media/create-and-edit-configurations-image1.png)

3. Pokud chcete vytvořit novou konfiguraci, vyberte **Přidat** . Můžete také zkopírovat jakoukoli existující konfiguraci.

Po vytvoření konfigurace můžete použít část **sestavení** v dialogovém okně Možnosti projektu pro každý z vašich projektů k přizpůsobení vlastností, které jsou vhodné pro vaši konfiguraci:

![Konfigurovat možnosti sestavení](media/create-and-edit-configurations-image3.png)

## <a name="renaming-a-build-configuration"></a>Přejmenování konfigurace sestavení

Pokud chcete přejmenovat konfiguraci, vyberte ji ze seznamu konfigurace tak, že přejdete na **sestavení > konfigurací** v projektu nebo v možnostech řešení:

![seznam konfigurací](media/create-and-edit-configurations-image4.png)

Vyberte tlačítko **Přejmenovat** .

![Dialogové okno Přejmenovat](media/create-and-edit-configurations-image5.png)

Pak kliknutím na **OK** potvrďte.

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Launch-Multiple-Projects/player]

## <a name="see-also"></a>Viz také

- [Vytváření a úpravy konfigurací sestavení (Visual Studio ve Windows)](/visualstudio/ide/how-to-create-and-edit-configurations)