---
title: Klonování úložiště
description: Naučte se, jak pomocí Visual Studio Tools for AI naklonovat úložiště kódu Pythonu a vytvořit z něj projekt.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 303c410bf519561844d95cc13fa036534ddb2aa7
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726615"
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>Klonování úložiště kódu Pythonu v aplikaci Visual Studio

Po [instalaci Visual Studio Tools for AI](installation.md)můžete snadno klonovat úložiště kódu Pythonu a vytvořit z něj projekt.

1. Pokud se chcete připojit k úložištím GitHub, spusťte instalační program sady Visual Studio, vyberte **Upravit** a vyberte kartu **jednotlivé součásti** . Přejděte dolů do části **nástroje kódu** , vyberte **rozšíření GitHub pro Visual Studio** a vyberte **změnit**.

    ![Výběr rozšíření GitHub v instalačním programu sady Visual Studio](media/create-project-repo/installation-github-extension.png)

2. Spusťte Visual Studio.

3. Výběrem **zobrazit > Team Explorer** otevřete okno **Team Explorer** , ve kterém se můžete připojit k GitHubu nebo Azure DevOps nebo klonovat úložiště.

    ![Okno Průzkumníka týmových oken zobrazující Azure DevOps, GitHub a klonování úložiště](media/create-project-repo/team-explorer-devops.png)

4. V poli Adresa URL v části **místní úložiště Git** zadejte `https://github.com/Microsoft/samples-for-ai` , zadejte složku pro klonované soubory a vyberte **klonovat**.

    > [!Tip]
    > Složka, kterou zadáte v Team Explorer, je konkrétní složka pro příjem klonovaných souborů. Na rozdíl od `git clone` příkazu vytvoření klonu v Team Explorer nevytvoří automaticky podsložku s názvem úložiště.

5. Po dokončení klonování poklikejte na složku úložiště v dolní části Team Explorer a přejděte na řídicí panel úložiště. V části **řešení** vyberte **Nový**.

    ![Okno Průzkumník týmových projektů, vytvoření nového projektu z klonu](media/create-project-repo/team-explorer-new-project.png)

6. V dialogu **Nový projekt** , který se zobrazí, vyberte "**z existujícího kódu Pythonu**", zadejte název projektu, nastavte **umístění** na stejnou složku jako úložiště a vyberte **OK**. V průvodci, který se zobrazí, vyberte **Dokončit**.

7. V nabídce vyberte **zobrazení > Průzkumník řešení** .

8. V Průzkumník řešení rozbalte `TensorFlow Examples> MNIST` uzel, klikněte pravým tlačítkem myši `convolutional.py` a vyberte **nastavit jako spouštěcí soubor**. Tento krok informuje Visual Studio, který soubor má použít při spuštění projektu.

9. Stiskněte **klávesu CTRL** + **F5** nebo vyberte **ladit > spustit bez ladění** pro spuštění programu. Pokud se zobrazí chyba, zkontrolujte znovu nastavení pracovního adresáře v předchozím kroku.

10. Když se program úspěšně spustí, uvidíte, že se spustí, abyste si stáhli datovou sadu pro školení a testování a potom provedli model a navedli výstup vaší míry chyb. Chcete snížit počet chyb v průběhu času

    ![První výstup z programu Python MNIST ručně zapsaných](media/create-project-repo/tensorflow-mnist-running.png)

   > [!NOTE]
   > Pokud používáte Anaconda a obdržíte chybu týkající se chybějících numpy, možná budete muset [změnit prostředí Python na používání Anaconda](../python/selecting-a-python-environment-for-a-project.md).

11. Průběh můžete vizualizovat pomocí TensorBoard. Klikněte pravým tlačítkem na projekt a pak klikněte na **Spustit TensorBoard** a pak vyberte adresář výstupních protokolů TensorBoard.

   ![Snímek obrazovky sady Visual Studio Průzkumník řešení s vybraným projektem MNIST ručně zapsaných a možností spustit TensorBoard vybranou v místní nabídce](media/create-project-repo/run-tensorboard.png)

12. Všimněte si chyby při snižování přesčasu, což znamená, že kvalita vylepšuje.

   ![Snímek obrazovky hlavního okna TensorBoard zobrazující čtyři grafy, které vizualizují data z protokolů TensorBoard.](media/create-project-repo/tensorboard.png)
