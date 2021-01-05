---
title: Odeslání úlohy pro výuku modelu
description: Odeslání úlohy pro výuku modelu pomocí Azure Batch AI
ms.custom: SEO-VS-2020
keywords: AI, Visual Studio, výukový model, Cloud
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- azure
ms.openlocfilehash: 72f5fa5aab9f9afa6268f8acd737430af0568928
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727356"
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Výuka modelů AI v Azure Batch AI

Batch AI je spravovaná služba, která umožňuje odborníkům přes data a výzkumným pracovníkům v oblasti AI trénovat modely AI a další modely strojového učení na clusterech virtuálních počítačů Azure, včetně virtuálních počítačů s podporou GPU. Popíšete požadavky svojí úlohy, umístění vstupů a výstupů a o zbytek se postará služba Batch AI. [Další informace o Azure Batch AI](/azure/batch-ai/overview)

Integruje se s Visual Studio Tools for AI, takže můžete dynamicky škálovat školicí modely v Azure.  Po [instalaci Visual Studio Tools for AI](installation.md)je snadné vytvořit nový projekt v Pythonu pomocí předem připraveného recepty v galerii Azure Machine Learning Sample Gallery.

1. Spusťte Visual Studio. Otevřete **Průzkumník serveru** otevřením nabídky **nástroje AI** a výběrem možnosti **Vybrat cluster** .

    ![Výběr clusteru](media/train-model/select-cluster.png)

2. Rozbalte položku **nástroje AI**. Všechny Batch AI prostředky, které budete mít, se automaticky zjistí a zobrazí se v Průzkumník serveru.

    ![Snímek obrazovky rozbaleného stromu složek pro nástroje AI v Průzkumník serveru, který zobrazuje rozšířené podsložky pro Azure Batch AI a Azure Machine Learning.](media/train-model/batchai.png)

3. Vyberte **zobrazení > Team Explorer...** a otevřete tak okno **Team Explorer** , ve kterém se můžete připojit k GitHubu nebo Azure DevOps nebo klonovat úložiště.

    ![Okno Průzkumníka týmových oken zobrazující Azure DevOps, GitHub a klonování úložiště](media/train-model/team-explorer-devops.png)

4. V poli Adresa URL v části **místní úložiště Git** zadejte `https://github.com/Microsoft/samples-for-ai` , zadejte složku pro klonované soubory a vyberte **klonovat**.

    > [!Tip]
    > Složka, kterou zadáte v Team Explorer, je konkrétní složka pro příjem klonovaných souborů. Na rozdíl od `git clone` příkazu vytvoření klonu v Team Explorer nevytvoří automaticky podsložku s názvem úložiště.

5. Po dokončení klonování klikněte na **soubor > otevřít řešení > projekt/řešení** .

    ![Snímek obrazovky, který ukazuje část nabídky soubor Průzkumník serveru s vybraným příkazem otevřít a projektem nebo řešením vybraným v místní nabídce](media/train-model/open-solution.png)

6. Otevřete **Samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln** v adresáři, který jste naklonoval do úložiště.

    ![Snímek obrazovky zobrazující soubor řešení TensorflowExamples. sln uvedený v obsahu složky TensorflowExamples v úložišti Samples-for-AI.](media/train-model/tensorflowexamples.png)

7. Nastavit projekt MNIST ručně zapsaných jako **spouštěný projekt**

    ![Snímek obrazovky s vybranou možností nastavit jako spouštěný projekt v kontextové nabídce pro projekt MNIST ručně zapsaných v Průzkumník řešení.](media/train-model/mnist-startup.png)

8. <strong>Klikněte pravým tlačítkem na **projekt mnist ručně zapsaných,** **odešlete úlohu** .</strong>

    ![Snímek obrazovky s vybranou úlohou odeslat v kontextové nabídce pro projekt MNIST ručně zapsaných v Průzkumník řešení.](media/train-model/submit-job.png)
9. Vyberte cluster **Azure Batch AI** a pak klikněte na **importovat**. Vyberte `AzureBatchAI_TF_MNIST.json` soubor, abyste mohli rychle naplnit některé výchozí hodnoty, jako je například ta, kterou image Docker má použít. Pak klikněte na **Odeslat** .

    ![Snímek obrazovky s dialogem odeslat úlohu s hodnotami naplněnými pro použít cluster, spouštěcí skript, název úlohy, název Image, Předpona cesty StdOutErr a parametry CLI](media/train-model/submit-batch.png)
