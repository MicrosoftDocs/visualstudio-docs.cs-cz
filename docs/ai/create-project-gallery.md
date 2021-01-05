---
title: Vytvoření projektu
description: Vytvoření projektu pomocí ukázky z Galerie Azure Machine Learning
keywords: AI, Visual Studio, Azure Machine Learning
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: a6813e834af00330b4018f16d4a19be945be2be9
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726641"
---
# <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Vytvoření projektu AI z Galerie Azure Machine Learning v aplikaci Visual Studio

Azure Machine Learning je integrována s Visual Studio Tools for AI. Můžete ji použít k odesílání úloh strojového učení do vzdálených výpočetních cílů, jako jsou virtuální počítače Azure, clustery Spark a další. 

Po [instalaci Visual Studio Tools for AI](installation.md)je snadné vytvořit nový projekt v Pythonu pomocí předem připraveného recepty v galerii Azure Machine Learning Sample Gallery.

> [!NOTE]
> Azure Machine Learning Workbench musí být nainstalované. 

1. Spusťte Visual Studio. Otevřete **Průzkumník serveru** otevřením nabídky **nástroje AI** a výběrem možnosti **Vybrat cluster** .

    ![Výběr clusteru](media/create-project-gallery/select-cluster.png)

2. Přihlaste se k předplatnému Azure Machine Learning tak, že kliknete pravým tlačítkem na uzel **Azure Machine Learning** v Průzkumník serveru pak vyberete **přihlášení** a postupujte podle pokynů.

    ![přihlášení](media/create-project-gallery/azureml-login.png)

3. Vyberte možnost **nástroje AI > Azure Machine Learning Galerie ukázek**.

    ![Galerie ukázek](media/create-project-gallery/gallery.png)

4. Pro tento rychlý Start vyberte ukázku "**mnist ručně zapsaných using TensorFlow**" a klikněte na **instalovat**. Zadejte následující:

   - **Skupina prostředků**: Skupina prostředků Azure, do které se uloží vaše metadata
   - **Účet**: Azure Machine Learning experimentální účet
   - **Pracovní prostor**: Azure Machine Learning pracovní prostor
   - **Typ projektu**: architektura strojového učení. V tomto případě vyberte **TensorFlow**
   - **Přidat do řešení**: Určuje, jestli se má přidat do aktuálního řešení sady Visual Studio, nebo vytvořit a otevřít nové řešení.
   - **Cesta k projektu**: umístění pro uložení kódu
   - **Název projektu**: typ **TensorFlowMNIST**

   ![Výsledný projekt při použití šablony aplikace Pythonu](media/create-project-gallery/new-AzureSampleProject.png)

5. Visual Studio vytvoří soubor projektu ( `.pyproj` soubor na disku) spolu s dalšími soubory definovanými v ukázce. S šablonou "MNIST ručně zapsaných" projekt obsahuje několik souborů.

    ![Snímek obrazovky sady Visual Studio Průzkumník řešení zobrazující soubory projektu TensorFlowMNIST. V hlavním okně se zobrazí kód pro tf_mnist. py.](media/create-project-gallery/azml-mnist.png)

6. Odešlete úlohu do Azure Machine Learning.

    ![Snímek obrazovky sady Visual Studio Průzkumník řešení zobrazující kontextovou nabídku projektu TensorFlowMNIST pomocí příkazu Odeslat úlohu... Vyberte.](media/create-project-gallery/submit-azml.png)

7. Spuštění v kontejneru Docker nebo na místním počítači

    ![Snímek obrazovky s dialogem odeslat úlohu s použitím sady clusterů s názvem "AzureML:/local" a spouštěcím skriptem nastaveným na "tf_mnist. py".](media/create-project-gallery/azml-local.png)
