---
title: 'Postupy: vytvoření a odebrání závislostí projektu'
ms.date: 06/21/2017
ms.topic: how-to
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
ms.openlocfilehash: ad21aeae2d348f56cb722365cd1e2ded249bbefe
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284461"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Postupy: vytvoření a odebrání závislostí projektu

Při sestavování řešení, které obsahuje více projektů, může být nutné nejprve sestavit určité projekty, aby bylo možné vygenerovat kód používaný jinými projekty. Když projekt spotřebovává spustitelný kód vygenerovaný jiným projektem, projekt, který generuje kód, je označován jako závislost projektu projektu, který využívá kód. Tyto vztahy závislostí lze definovat v dialogovém okně **závislosti projektu** .

## <a name="to-assign-dependencies-to-projects"></a>Přiřazení závislostí k projektům

1. V **Průzkumník řešení**vyberte projekt.

2. V nabídce **projekt** vyberte **závislosti projektu**.

    Zobrazí se dialogové okno **závislosti projektu** .

   > [!NOTE]
   > Možnost **závislosti projektu** je k dispozici pouze v řešení s více než jedním projektem.

3. Na kartě **závislosti** vyberte projekt z rozevírací nabídky **projekt** .

4. V poli **závisí na** zaškrtněte políčko u všech dalších projektů, které musí být sestaveny před tímto projektem.

   Vaše řešení musí obsahovat více než jeden projekt, aby bylo možné vytvořit závislosti projektu.

## <a name="to-remove-dependencies-from-projects"></a>Postup odebrání závislostí z projektů

1. V **Průzkumník řešení**vyberte projekt.

2. V nabídce **projekt** vyberte **závislosti projektu**.

     Zobrazí se dialogové okno **závislosti projektu** .

    > [!NOTE]
    > Možnost **závislosti projektu** je k dispozici pouze v řešení s více než jedním projektem.

3. Na kartě **závislosti** vyberte projekt z rozevírací nabídky **projekt** .

4. V poli **závisí na** zrušte zaškrtnutí políček u všech ostatních projektů, které již nejsou závislé na tomto projektu.

## <a name="see-also"></a>Viz také

- [Sestavování a čištění projektů a řešení v aplikaci Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)
- [Vysvětlení konfigurací sestavení](../ide/understanding-build-configurations.md)
- [Správa vlastností projektu a řešení](managing-project-and-solution-properties.md)
