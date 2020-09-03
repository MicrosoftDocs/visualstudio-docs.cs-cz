---
title: 'Postupy: vytvoření a odebrání závislostí projektu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1403beccdb6bf9b938787f62cb3da2e5bb5c259
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668124"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Postupy: Vytváření a odebrání závislostí projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při sestavování řešení, které obsahuje více projektů, může být nutné nejprve sestavit určité projekty, aby bylo možné vygenerovat kód používaný jinými projekty. Když projekt spotřebovává spustitelný kód vygenerovaný jiným projektem, projekt, který generuje kód, je označován jako závislost projektu projektu, který využívá kód. Tyto vztahy závislostí lze definovat v dialogovém okně **závislosti projektu** .

### <a name="to-assign-dependencies-to-projects"></a>Přiřazení závislostí k projektům

1. V Průzkumník řešení vyberte projekt.

2. V nabídce **projekt** vyberte **závislosti projektu**.

    Zobrazí se dialogové okno **závislosti projektu** .

   > [!NOTE]
   > Možnost **závislosti projektu** je k dispozici pouze v řešení s více než jedním projektem.

3. Na kartě **závislosti** vyberte projekt z rozevírací nabídky **projekt** .

4. V poli **závisí na** zaškrtněte políčko u všech dalších projektů, které musí být sestaveny před tímto projektem.

   Vaše řešení musí obsahovat více než jeden projekt, aby bylo možné vytvořit závislosti projektu.

### <a name="to-remove-dependencies-from-projects"></a>Postup odebrání závislostí z projektů

1. V Průzkumník řešení vyberte projekt.

2. V nabídce **projekt** vyberte **závislosti projektu**.

     Zobrazí se dialogové okno **závislosti projektu** .

    > [!NOTE]
    > Možnost **závislosti projektu** je k dispozici pouze v řešení s více než jedním projektem.

3. Na kartě **závislosti** vyberte projekt z rozevírací nabídky **projekt** .

4. V poli **závisí na** zrušte zaškrtnutí políček u všech ostatních projektů, které již nejsou závislé na tomto projektu.

## <a name="see-also"></a>Viz také
 [Sestavování a čištění projektů a řešení v nástroji Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [kompilace a sestavování](../ide/compiling-and-building-in-visual-studio.md) [porozumění konfiguracím sestavení](../ide/understanding-build-configurations.md) [NIB postupy: Změna vlastností projektu a nastavení konfigurace](https://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
