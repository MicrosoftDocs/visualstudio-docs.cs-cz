---
title: 'Postup: Vytvoření a odebrání závislostí projektu'
ms.date: 06/21/2017
ms.topic: conceptual
f1_keywords:
- VS.ProjectDependenciesDlg
helpviewer_keywords:
- vs.build.projectdependencies
- project dependencies
- builds [Visual Studio], setting up
- project build configurations, dependencies
- dependencies, project
- projects [Visual Studio], dependencies
ms.assetid: e2a0a8ff-dae7-40a8-b774-b88aa5235183
ms.technology: vs-ide-compile
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a286a84d01c6a49b32445106488688ba5b489be
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114550"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Postup: Vytvoření a odebrání závislostí projektu

Při vytváření řešení, které obsahuje více projektů, může být nutné nejprve vytvořit určité projekty, generovat kód používaný jinými projekty. Když projekt spotřebovává spustitelný kód generovaný jiným projektem, projekt, který generuje kód, se označuje jako závislost projektu, která spotřebovává kód. Tyto vztahy závislostí lze definovat v dialogovém okně **Závislosti projektu.**

## <a name="to-assign-dependencies-to-projects"></a>Přiřazení závislostí projektům

1. V **Průzkumníku řešení**vyberte projekt.

2. V nabídce **Project** zvolte **Závislosti projektu**.

    Otevře se dialogové okno **Závislosti projektu.**

   > [!NOTE]
   > Možnost **Závislosti projektu** je k dispozici pouze v řešení s více než jeden projekt.

3. Na kartě **Závislosti** vyberte projekt z rozevírací nabídky **Projekt.**

4. V poli **Závisí na** zaškrtněte políčko u jakéhokoli jiného projektu, který musí být sestavován dříve, než tento projekt.

   Vaše řešení se musí skládat z více než jednoho projektu před vytvořením závislostí projektu.

## <a name="to-remove-dependencies-from-projects"></a>Odebrání závislostí z projektů

1. V **Průzkumníku řešení**vyberte projekt.

2. V nabídce **Project** zvolte **Závislosti projektu**.

     Otevře se dialogové okno **Závislosti projektu.**

    > [!NOTE]
    > Možnost **Závislosti projektu** je k dispozici pouze v řešení s více než jeden projekt.

3. Na kartě **Závislosti** vyberte projekt z rozevírací nabídky **Projekt.**

4. V **poli Závisí na** zrušte zaškrtnutí políček vedle jiných projektů, které již nejsou závislostmi tohoto projektu.

## <a name="see-also"></a>Viz také

- [Vytváření a čištění projektů a řešení v sadě Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)
- [Vysvětlení konfigurací sestavení](../ide/understanding-build-configurations.md)
- [Správa vlastností projektu a řešení](managing-project-and-solution-properties.md)
