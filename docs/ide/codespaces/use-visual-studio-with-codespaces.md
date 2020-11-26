---
title: Visual Studio s codespace (Preview)
description: Přečtěte si o použití integrovaného vývojového prostředí sady Visual Studio s GitHubem Codespaces for Windows.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: c3a2e14236c2d24bc9650fab81150cc295826844
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189924"
---
# <a name="how-to-use-visual-studio-with-a-codespace-preview"></a>Jak používat Visual Studio s codespace (Preview)

Visual Studio má skvělou podporu pro vývoj na GitHubu Codespaces. Můžete vytvořit a připojit se k codespace a máte plnou sílu sady Visual Studio pro práci na vašich projektech ve vzdáleném hostovaném prostředí. I když se váš zdrojový kód a nástroje nacházejí v codespace a vaše kompilace a ladění probíhá v cloudu, vývojové prostředí bude fungovat jako rychlé a bez obav, jako kdyby pracovali místně. Můžete pracovat s codespace ze sady Visual Studio 2019 Preview ([Zaregistrujte se do omezené veřejné beta verze](https://github.com/features/codespaces/signup-vs)).

> [!NOTE]
> Tento článek konkrétně popisuje použití sady Visual Studio pro připojení k GitHub Codespaces. Informace o připojení k codespace s dalšími klienty najdete v dokumentaci k [Visual Studio Code](https://docs.github.com/github/developing-online-with-codespaces/connecting-to-your-codespace-from-visual-studio-code) nebo [GitHubu](https://docs.github.com/github/developing-online-with-codespaces/developing-in-a-codespace) .

> [!NOTE]
> Pokud ještě nemáte nainstalovanou [aplikaci Visual Studio 2019 Preview](https://aka.ms/vspreview) , můžete si ji stáhnout z [VisualStudio.Microsoft.com](https://aka.ms/vspreview).

## <a name="enable-connect-to-github-codespaces"></a>Povolit připojení k GitHub Codespaces

Připojení k GitHub Codespaces s Visual Studio 2019 Preview není ve výchozím nastavení povolené, takže budete nejdřív muset povolit možnost funkce verze Preview.

1. V aplikaci Visual Studio 2019 Preview pomocí **Tools**  >  položky nabídky **Možnosti** nástrojů otevřete dialogové okno Možnosti.

2. V části **prostředí** vyberte **funkce verze Preview** a podívejte se na funkci **připojit k GitHub Codespaces** verze Preview.

   ![Podívejte se na funkci připojit k GitHubu Codespaces Preview](media/connect-to-github-codespaces-preview-feature.png)

3. Aby byla funkce k dispozici, bude nutné restartovat Visual Studio.

## <a name="create-a-codespace"></a>Vytvoření codespace

Pokud ještě nemáte codespace, můžete si ho vytvořit ze sady Visual Studio.

1. Po spuštění sady Visual Studio se v okně Start zobrazí tlačítko **připojit k codespace** v části "Začínáme".

   ![Úvodní okno sady Visual Studio s připojením k codespace](media/visual-studio-start-window.png)

2. Vyberte **připojit k codespace** a budete vyzváni, abyste se přihlásili k GitHubu. Můžete také vytvořit účet GitHub, pokud ho ještě nemáte.

   ![Přihlášení sady Visual Studio do GitHubu](media/visual-studio-sign-in-to-github.png)

   Jakmile vyberete možnost **Přihlásit se k GitHubu**, postupujte podle pracovního postupu online registrace GitHubu.

3. Pokud jste nikdy nevytvořili codespace, zobrazí se výzva k jeho vytvoření.

   V části Codespace Details (podrobnosti) musíte zadat **adresu URL úložiště**. Codespaces GitHubu naklonuje zadané úložiště do vaší codespace při jeho vytvoření.

   Můžete také změnit **typ instance** a **pozastavit po** vypršení časového limitu prostřednictvím jejich rozevíracích seznamů. Po nastavení podrobností codespace vyberte tlačítko **vytvořit a připojit** .

   ![Podrobnosti o codespace sady Visual Studio](media/visual-studio-codespace-details.png)

   Codespaces GitHub začne připravovat codespace a otevřít Visual Studio, jakmile bude codespace připravený.

   Název codespace se zobrazí na vzdáleném indikátoru v řádku nabídek.

   ![Připojení sady Visual Studio k codespace úložiště eShopOnWeb](media/visual-studio-eshoponweb-codespace.png)

4. Začněte používat aplikaci Visual Studio stejně, jako byste pracovali místně. Možná řešení:

   * Procházet zdrojový kód.
   * Vyberte soubor řešení a sestavte řešení (**CTRL + SHIFT + B**).
   * Nastavte zarážku ve zdrojovém souboru a stisknutím klávesy **F5** spusťte aplikaci v ladicím programu.
   * Proveďte změny a potvrďte je do úložiště.   

> [!NOTE]
> V tuto chvíli nemůžete vytvořit GitHub Codespaces pro Visual Studio prostřednictvím [portálu Codespaces](https://github.com/codespaces)na GitHubu. Můžete je vytvořit pouze pomocí sady Visual Studio.

## <a name="connect-to-a-codespace"></a>Připojení k codespace

Po vytvoření codespace můžete otevřít codespace přímo ze sady Visual Studio.

1. Po spuštění sady Visual Studio se v okně Start zobrazí tlačítko **připojit k Codespace** v části "Začínáme".

   ![Úvodní okno sady Visual Studio s připojením k codespace](media/visual-studio-start-window.png)

   Pokud jste již v aplikaci Visual Studio, můžete použít **File**  >  položku **připojit k** položce nabídky Codespace.

   ![Soubor sady Visual Studio připojit k položce nabídky codespace](media/visual-studio-file-connect-to-codespace.png)

2. Vyberte **připojit k codespace**. Pokud jste to ještě neudělali, budete vyzváni k přihlášení k GitHubu.

3. Pak uvidíte všechny codespaces GitHubu spolu s jejich podrobnostmi uvedenými na pravém panelu.

   ![Visual Studio zobrazující dostupné codespaces GitHubu a podrobnosti](media/visual-studio-connect-codespace.png)

   Všechny codespaces, které naklonují úložiště Azure DevOps, se tady budou zobrazovat jenom v aplikaci Visual Studio, a ne na stránce Codespaces na GitHubu.

4. Zvolte codespace a klikněte na tlačítko **připojit** . Pokud byl codespace pozastaven, bude restartován a aplikace Visual Studio se otevře jako připojené k tomuto codespace.

   Název codespace se zobrazí na vzdáleném indikátoru v řádku nabídek.

   ![Připojení sady Visual Studio k codespace úložiště eShopOnWeb](media/visual-studio-eshoponweb-codespace.png)

5. Začněte používat aplikaci Visual Studio stejně, jako byste pracovali místně. Možná řešení:

   * Procházet zdrojový kód.
   * Vyberte soubor řešení a sestavte řešení (**CTRL + SHIFT + B**).
   * Nastavte zarážku ve zdrojovém souboru a stisknutím klávesy **F5** spusťte aplikaci v ladicím programu.
   * Proveďte změny a potvrďte je do úložiště.

<!-- TBD ## Suspend a codespace -->

<!-- TBD ## Disconnect from a codespace -->

## <a name="see-also"></a>Viz také

* [Co je GitHub Codespaces?](codespaces-overview.md)
* [Přizpůsobení codespace](customize-codespaces.md)
* [Podporované funkce sady Visual Studio](supported-features-codespaces.md)
