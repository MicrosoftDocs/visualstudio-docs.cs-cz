---
title: Klonovat repo
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 73f1595e0e6c8f182f0bedcece51011390964ed2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62539616"
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>Klonování úložiště kódu Pythonu v sadě Visual Studio

Po instalaci [nástrojů Sady Visual Studio pro umělou přípravu](installation.md)můžete snadno naklonovat úložiště kódu Pythonu a vytvořit z něj projekt.

1. Chcete-li se připojit k úložištím GitHub, spusťte instalační program Sady Visual Studio, vyberte **GitHub extension for Visual Studio** **Změnit**a vyberte kartu **Modify** **Jednotlivé součásti.** **Code tools**

    ![Výběr rozšíření GitHub v instalačním programu Sady Visual Studio](media/create-project-repo/installation-github-extension.png)

2. Spusťte Visual Studio.

3. Vyberte **Zobrazit > Průzkumníktýmu** otevřete okno **Průzkumníka týmu,** ve kterém se můžete připojit k GitHubu nebo Azure DevOps, nebo naklonovat úložiště.

    ![Okno průzkumníka týmu zobrazující Azure DevOps, GitHub a klonování úložiště](media/create-project-repo/team-explorer-devops.png)

4. Do pole URL v části Místní `https://github.com/Microsoft/samples-for-ai`úložiště **Git**zadejte , zadejte složku pro klonované soubory a vyberte **Klonovat**.

    > [!Tip]
    > Složka zadaná v Průzkumníkovi týmu je konkrétní složka pro příjem klonovaných souborů. Na `git clone` rozdíl od příkazu vytvoření klonu v Průzkumníkovi týmu automaticky nevytvoří podsložku s názvem úložiště.

5. Po dokončení klonování poklikejte na složku úložiště v dolní části Průzkumníka týmu a přejděte na řídicí panel úložiště. V části **Řešení**vyberte **Nový**.

    ![Okno průzkumníka týmu, vytvoření nového projektu z klonu](media/create-project-repo/team-explorer-new-project.png)

6. V dialogovém okně **Nový projekt,** které se zobrazí, vyberte "**Z existujícího kódu Pythonu**", zadejte název projektu, nastavte **umístění** na stejnou složku jako úložiště a vyberte **OK**. V průvodci, který se zobrazí, vyberte **dokončit**.

7. V nabídce vyberte **Zobrazit Průzkumníka řešení >.**

8. V Průzkumníku řešení `TensorFlow Examples> MNIST` rozbalte uzel, `convolutional.py`klikněte pravým tlačítkem myši a vyberte **Nastavit jako spouštěcí soubor**. Tento krok informuje visual studio, který soubor by měl použít při spuštění projektu.

9. Stisknutím **klávesy Ctrl**+**F5** nebo stisknutím **možnosti Ladění > Spustit bez ladění** program spustíte. Pokud se zobrazí chyba, zkontrolujte nastavení pracovního adresáře v předchozím kroku.

10. Když program úspěšně spustí, uvidíte, že začne stahovat trénovací a testovací datovou sadu, pak trénovat model a výstup chybové frekvence. Chcete, aby se míra chyb v průběhu času snižovala

    ![První výstup z programu Python MNIST](media/create-project-repo/tensorflow-mnist-running.png)

   > [!NOTE]
   > Pokud používáte Anaconda a zobrazí se vám chyba ohledně chybějícího numpy, možná budete muset [změnit prostředí Pythonu, abyste mohli používat Anakonda](../python/selecting-a-python-environment-for-a-project.md).

11. Průběh si můžete představit pomocí TensorBoardu. Klikněte pravým tlačítkem myši na projekt a klikněte na **spustit tensorboard** a vyberte adresář výstupních protokolů TensorBoard.

   ![spustit tendenstož](media/create-project-repo/run-tensorboard.png)

12. Všimněte si chyby snižující se přesčas, což znamená, že se kvalita zlepšuje.

   ![spustit tendenstož](media/create-project-repo/tensorboard.png)
