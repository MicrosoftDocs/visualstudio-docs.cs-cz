---
title: Odeslání úlohy k trénování modelu v Azure Batch AI
description: vlak model cloud
keywords: ai, visual studio, model vlaku, cloud
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: dec70c9e9aeb9c916b511241a74b550354aff175
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75915771"
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Trénování modelů AI v Azure Batch AI

Batch AI je spravovaná služba, která umožňuje odborníkům přes data a výzkumným pracovníkům v oblasti AI trénovat modely AI a další modely strojového učení na clusterech virtuálních počítačů Azure, včetně virtuálních počítačů s podporou GPU. Popíšete požadavky svojí úlohy, umístění vstupů a výstupů a o zbytek se postará služba Batch AI. [Další informace o Azure Batch AI](/azure/batch-ai/overview)

Je integrovaný s visual studio nástroje pro AI, takže můžete dynamicky škálovat tréninkové modely v Azure.  Po instalaci [nástrojů Visual Studio pro umělou přípravu](installation.md)je snadné vytvořit nový projekt Pythonu pomocí předem nastavených receptů v Galerii ukázek Azure Machine Learning.

1. Spusťte Visual Studio. Otevření **Průzkumníka serveru** otevřením nabídky **Nástroje ai** a výběrem **možnosti Vybrat cluster**

    ![Výběr clusteru](media/train-model/select-cluster.png)

2. Rozbalte **nástroje AI .** Všechny dávkové prostředky AI budou automaticky rozpoznány a zobrazí se v Průzkumníku serveru.

    ![Ukázková galerie](media/train-model/batchai.png)

3. Vyberte **Zobrazit > Průzkumníktýmu... otevřete** okno **Průzkumníka týmu,** ve kterém se můžete připojit k GitHubu nebo Azure DevOps, nebo naklonovat úložiště.

    ![Okno průzkumníka týmu zobrazující Azure DevOps, GitHub a klonování úložiště](media/train-model/team-explorer-devops.png)

4. Do pole URL v části Místní `https://github.com/Microsoft/samples-for-ai`úložiště **Git**zadejte , zadejte složku pro klonované soubory a vyberte **Klonovat**.

    > [!Tip]
    > Složka zadaná v Průzkumníkovi týmu je konkrétní složka pro příjem klonovaných souborů. Na `git clone` rozdíl od příkazu vytvoření klonu v Průzkumníkovi týmu automaticky nevytvoří podsložku s názvem úložiště.

5. Po dokončení klonování klikněte na **položku Soubor > otevřít řešení > projectu / řešení.**

    ![Ukázková galerie](media/train-model/open-solution.png)

6. Otevřít **ukázky pro ai\TensorFlowExamples\TensorFlowExamples.sln** v adresáři, který jste naklonovali úložiště

    ![Ukázková galerie](media/train-model/tensorflowexamples.png)

7. Nastavit projekt MNIST jako **projekt po spuštění**

    ![Ukázková galerie](media/train-model/mnist-startup.png)

8. <strong>Klikněte pravým tlačítkem myši na **projekt MNIST,** **Odeslat úlohu**</strong>

    ![Ukázková galerie](media/train-model/submit-job.png)
9. Vyberte cluster **Azure Batch AI** a klikněte na **Importovat**. Vyberte `AzureBatchAI_TF_MNIST.json` soubor, chcete-li rychle naplnit některé výchozí hodnoty, jako je to, který obrázek Dockeru použít. Pak klikněte na **Odeslat**

    ![Ukázková galerie](media/train-model/submit-batch.png)
