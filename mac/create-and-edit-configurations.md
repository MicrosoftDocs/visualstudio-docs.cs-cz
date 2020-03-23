---
title: Vytváření a úpravy konfigurací sestavení
description: Tento článek popisuje vytváření konfigurací sestavení v Sadě Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: CC1B72D6-12FF-4CCC-A9D4-00F2DC14589F
ms.custom: video
ms.openlocfilehash: 26f6e25bfe1284fc31bcd484b905bf5d75c2ba15
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128423"
---
# <a name="creating-and-editing-build-configurations"></a>Vytváření a úpravy konfigurací sestavení

Konfigurace sestavení poskytují přesnou kontrolu nad sestavením, které vám umožní vytvářet konfigurace, které uspokojí různé testovací a distribuční situace. Můžete vytvořit konfigurace sestavení pro jednotlivé projekty nebo na základě celého řešení.

Pomocí dialogového okna Možnosti projektu můžete vytvořit nové konfigurace a upravit stávající konfigurace pro projekty i řešení.

>[!NOTE]
>Toto téma se týká Visual Studia pro Mac. Visual Studio ve Windows najdete v [tématu Postup: Vytváření a úpravy konfigurací](/visualstudio/ide/how-to-create-and-edit-configurations).

## <a name="creating-a-project-build-configuration"></a>Vytvoření konfigurace sestavení projektu

Chcete-li vytvořit konfiguraci sestavení projektu, postupujte takto:

1. Klikněte pravým tlačítkem myši na uzel projektu a vyberte **možnosti**. Můžete také poklepat na uzel projektu a vyvolat dialogové okno Možnosti projektu.

2. V dialogovém okně Možnosti projektu vyberte **Vytvořit > konfigurace**:

    ![Správce konfigurací v možnostech projektu](media/create-and-edit-configurations-image2.png)

3. Chcete-li vytvořit novou konfiguraci, vyberte **přidat.** Můžete také zkopírovat libovolnou existující konfiguraci.

Po vytvoření konfigurace můžete pomocí části **Sestavení** v části Možnosti projektu přizpůsobit vlastnosti odpovídající vaší konfiguraci:

![Konfigurace možností sestavení](media/create-and-edit-configurations-image3.png)

## <a name="creating-a-solution-build-configuration"></a>Vytvoření konfigurace sestavení řešení

Chcete-li vytvořit konfiguraci sestavení řešení, postupujte takto:

1. Klikněte pravým tlačítkem myši na uzel řešení a vyberte **možnosti**. Můžete také poklepat na uzel řešení a vyvolat dialogové okno Možnosti řešení.

2. V dialogovém okně Možnosti řešení vyberte **Vytvořit > konfigurace**:

    ![Správce konfigurací v možnostech řešení](media/create-and-edit-configurations-image1.png)

3. Chcete-li vytvořit novou konfiguraci, vyberte **přidat.** Můžete také zkopírovat libovolnou existující konfiguraci.

Po vytvoření konfigurace můžete použít část **Sestavení** v dialogovém okně Možnosti projektu pro každý z projektů a přizpůsobit vlastnosti odpovídající vaší konfiguraci:

![Konfigurace možností sestavení](media/create-and-edit-configurations-image3.png)

## <a name="renaming-a-build-configuration"></a>Přejmenování konfigurace sestavení

Chcete-li konfiguraci přejmenovat, vyberte ji ze seznamu Konfigurace tak, že přejdete na **příkaz Vytvořit > konfigurace** v možnostech projektu nebo řešení:

![konfigurační seznam](media/create-and-edit-configurations-image4.png)

Vyberte tlačítko **Přejmenovat.**

![dialogové okno přejmenovat](media/create-and-edit-configurations-image5.png)

Potvrďte to klepnutím na **tlačítko OK.**

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Launch-Multiple-Projects/player]

## <a name="see-also"></a>Viz také

- [Vytváření a úpravy konfigurací sestavení (Visual Studio ve Windows)](/visualstudio/ide/how-to-create-and-edit-configurations)