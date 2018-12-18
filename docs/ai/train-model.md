---
title: Odeslání úlohy k trénování modelů v Azure Batch AI
description: trénování modelu cloudu
keywords: AI, visual studio, trénování modelu cloudu
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.devlang: multiple
ms.service: multiple
ms.technology: vs-ai-tools
ms.workload:
- azure
ms.openlocfilehash: 6fd6f8befce66a117f5f2dcb598a7359ba9c15c0
ms.sourcegitcommit: 8cdc6e2ad2341f34bd6b02859a7c975daa0c9320
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2018
ms.locfileid: "53307642"
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Trénování modelů AI v Azure Batch AI

Batch AI je spravovaná služba, která umožňuje odborníkům přes data a výzkumní pracovníci AI trénovat modely AI a jiných modelů strojového učení na clusterech virtuálních počítačů Azure, včetně virtuálních počítačů s podporou GPU. Popíšete požadavky svojí úlohy, kam se ukládají výstupy a služby Batch AI vstupů a ostatní se postará. [Další informace o Azure Batch AI](https://docs.microsoft.com/azure/batch-ai/overview)

To je integrovaná s Visual Studio Tools pro AI tak můžete dynamicky horizontálně navýšit trénování modelů ve službě Azure.  Jakmile [nainstalované Visual Studio Tools pro AI](installation.md), je snadné vytvoření nového projektu Pythonu pomocí předpřipravených recepty v ukázkové Galerie Azure Machine Learning.

1. Spusťte sadu Visual Studio. Otevřít **Průzkumníka serveru** tak, že otevřete **nástroje AI** nabídku a zvolíte **vyberte clusteru**

    ![Výběr clusteru](media/train-model/select-cluster.png)

2. Rozbalte **nástroje AI**. Všechny prostředky služby Batch AI, ke kterým máte bude možné automaticky zjištěno a zobrazí v Průzkumníku serveru.

    ![Galerie ukázek](media/train-model/batchai.png)

3. Vyberte **zobrazení > Průzkumník týmových projektů...**  otevřít **Team Exploreru** okno, ve kterém můžete připojit ke Githubu nebo Azure DevOps nebo klonování úložiště.

    ![Okno Průzkumníka týmu zobrazující Azure DevOps, Githubu a klonování úložiště](media/train-model/team-explorer.png)

4. Do pole Adresa URL v části **místní úložiště Git**, zadejte `https://github.com/Microsoft/samples-for-ai`zadejte složky pro klonované soubory a vyberte **klonování**.

    > [!Tip]
    > Složka, kterou zadáte v Průzkumníku týmových projektů je konkrétní složky pro klonované soubory příjem. Na rozdíl od `git clone` příkazu, vytváření v Team Exploreru klonu neprovádí automatické vytváření podsložku s názvem úložiště.

5. Po klonování je hotové, klikněte na tlačítko **soubor > Otevřít řešení > Projekt / řešení**

    ![Galerie ukázek](media/train-model/open-solution.png)

6. Otevřít **samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln** v adresáři jste naklonovali úložiště

    ![Galerie ukázek](media/train-model/tensorflowexamples.png)

7. Sada mnist ručně projektu jako **spouštěný projekt**

    ![Galerie ukázek](media/train-model/mnist-startup.png)

8. <strong>Klikněte pravým tlačítkem na **mnist ručně projektu** **odeslat úlohu**</strong>

    ![Galerie ukázek](media/train-model/submit-job.png)
9. Vyberte vaše **Azure Batch AI** clusteru a potom klikněte na **Import**. Vyberte `AzureBatchAI_TF_MNIST.json` do které rychle přidáte některé výchozí hodnoty, jako který Image Dockeru pro použití. Pak klikněte na tlačítko **odeslat**

    ![Galerie ukázek](media/train-model/submit-batch.png)
