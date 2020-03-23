---
title: Vytvoření projektu
description: vytvoření projektu pomocí ukázky z galerie Azure Machine Learning
keywords: ai, visual studio, azure machine learning
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: d5e73757e10eec5e7e8c290772822f49129fd1e5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75915903"
---
# <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Vytvoření projektu AI z Galerie Azure Machine Learning v Sadě Visual Studio

Azure Machine Learning je integrovaný s Visual Studio Tools pro AI. Můžete ji použít k odesílání úloh strojového učení do vzdálených výpočetních cílů, jako jsou virtuální počítače Azure, clustery Spark a další. 

Po instalaci [nástrojů Visual Studio pro umělou přípravu](installation.md)je snadné vytvořit nový projekt Pythonu pomocí předem nastavených receptů v Galerii ukázek Azure Machine Learning.

> [!NOTE]
> Azure Machine Learning Workbench musí být nainstalovaný. Informace o jeho instalaci najdete v [tématu Azure Machine Learning instalace rychlý start](/azure/machine-learning/preview/quickstart-installation)

1. Spusťte Visual Studio. Otevření **Průzkumníka serveru** otevřením nabídky **Nástroje ai** a výběrem **možnosti Vybrat cluster**

    ![Výběr clusteru](media/create-project-gallery/select-cluster.png)

2. Přihlaste se k předplatnému Azure Machine Learning kliknutím pravým tlačítkem myši na uzel **Azure Machine Learning** v Průzkumníkovi serveru a pak vyberte **Přihlásit** a postupujte podle pokynů.

    ![přihlášení](media/create-project-gallery/azureml-login.png)

3. Vyberte **nástroje AI > Azure Machine Learning Sample Gallery**.

    ![Ukázková galerie](media/create-project-gallery/gallery.png)

4. Pro tento úvodní start vyberte ukázku **" MNIST using TensorFlow**" a klepněte na **tlačítko Instalovat**. Uveďte následující:

   - **Skupina prostředků:** Skupina prostředků Azure, kde budou uložena vaše metadata
   - **Účet:** Účet experimentování Azure Machine Learning
   - **Pracovní prostor:** Pracovní prostor Azure Machine Learning
   - **Typ projektu**: Rámec strojového učení. V tomto případě zvolte **TensorFlow**
   - **Přidat do řešení**: určuje, zda chcete přidat do aktuálního řešení Sady Visual Studio nebo vytvořit a otevřít nové řešení
   - **Cesta k projektu:** Umístění pro uložení kódu
   - **Název projektu**: Typ **TensorFlowMNIST**

   ![Výsledný projekt při použití šablony aplikace Pythonu](media/create-project-gallery/new-AzureSampleProject.png)

5. Visual Studio vytvoří soubor `.pyproj` projektu (soubor na disku) spolu s dalšími soubory definovanými v ukázce. Se šablonou "MNIST" projekt obsahuje několik souborů.

    ![mnist (Mnist)](media/create-project-gallery/azml-mnist.png)

6. Odešlete úlohu do Azure Machine Learning.

    ![mnist (Mnist)](media/create-project-gallery/submit-azml.png)

7. Spuštění v kontejneru Dockeru nebo v místním počítači

    ![mnist (Mnist)](media/create-project-gallery/azml-local.png)
