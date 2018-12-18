---
title: Vytvoření projektu v nástroje AI pro sadu Visual studio
description: Vytvořte projekt pomocí ukázky z Galerie azure machine learning
keywords: AI, visual studio, azure machine learning
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.devlang: multiple
ms.service: multiple
ms.technology: vs-ai-tools
ms.workload:
- multiple
ms.openlocfilehash: 18cf719b100aa7c216de2903c05a24a3abcca244
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916488"
---
## <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Vytvoření projektu aplikace AI z Galerie Azure Machine Learning v sadě Visual Studio

Azure Machine Learning je integrovaná se službou Visual Studio Tools pro AI. Slouží k odesílání úloh machine learning do cílových výpočetních prostředí vzdálené jako virtuální počítače Azure, clusterů Spark a dalších. Další informace o [experimentování ve službě Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/preview/experimentation-service-configuration)

Jakmile [nainstalované Visual Studio Tools pro AI](installation.md), je snadné vytvoření nového projektu Pythonu pomocí předpřipravených recepty v ukázkové Galerie Azure Machine Learning.

> [!NOTE]
> Musí být nainstalována aplikace Azure Machine Learning Workbench. K jeho instalaci prosím najdete [stručném Průvodci instalací Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/preview/quickstart-installation)

1. Spusťte sadu Visual Studio. Otevřít **Průzkumníka serveru** tak, že otevřete **nástroje AI** nabídku a zvolíte **vyberte clusteru**

    ![Výběr clusteru](media/create-project-gallery/select-cluster.png)

2. Přihlaste se ke svému předplatnému Azure Machine Learning kliknutím pravým tlačítkem myši **Azure Machine Learning** uzlu v Průzkumníku serveru vyberte **přihlášení** a postupujte podle pokynů.

    ![přihlášení](media/create-project-gallery/azureml-login.png)

3. Vyberte **nástroje AI > ukázková Galerie služby Azure Machine Learning**.

    ![Galerie ukázek](media/create-project-gallery/gallery.png)

4. Pro účely tohoto rychlého startu vyberte "**mnist ručně pomocí TensorFlow**" vzorku a klikněte na tlačítko **nainstalovat**. Poskytnout následující:

   - **Skupina prostředků**: Skupina prostředků Azure, kam se budou ukládat vaše metadata
   - **Účet**: Azure Machine Learning experimentálního účtu
   - **Pracovní prostor**: pracovního prostoru Azure Machine Learning
   - **Typ projektu**: rozhraní machine learning. V tomto případě zvolte **TensorFlow**
   - **Přidat do řešení**: Určuje, jestli se má přidat do aktuálního řešení Visual Studio nebo použít příkaz pro vytvoření a otevření nového řešení
   - **Cesta k projektu**: umístění pro uložení kódu
   - **Název projektu**: typ **TensorFlowMNIST**

   ![Výsledný projekt při použití šablony aplikace v Pythonu](media/create-project-gallery/new-AzureSampleProject.png)

5. Visual Studio vytvoří soubor projektu ( `.pyproj` souboru na disku) společně s další soubory definované v ukázce. Projekt se šablonou "Mnist ručně" obsahuje několik souborů.

    ![mnist ručně](media/create-project-gallery/azml-mnist.png)

6. Odešlete úlohu do Azure Machine Learning.

    ![mnist ručně](media/create-project-gallery/submit-azml.png)

7. Spuštění v kontejneru Dockeru nebo na místním počítači

    ![mnist ručně](media/create-project-gallery/azml-local.png)