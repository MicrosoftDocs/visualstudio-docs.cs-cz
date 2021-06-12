---
title: Připojení k projektům v Team Exploreru
description: Naučte se používat Team Explorer v aplikaci Visual Studio pro práci se členy týmu pro vývoj a správu projektů.
ms.custom: SEO-VS-2020
ms.date: 06/11/2021
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
ms.openlocfilehash: 4d3d2c005f32aaebacc251414218f5ae03edf546
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2021
ms.locfileid: "112043013"
---
# <a name="connect-to-projects-in-team-explorer"></a>Připojení k projektům v Team Exploreru

::: moniker range="vs-2017"

Použijte okno **Team Explorer** Tool k koordinaci vašeho kódu s ostatními členy týmu pro vývoj projektu a ke správě práce, která je přiřazena vám, vašemu týmu nebo vašim projektům. **Team Explorer** připojuje sadu Visual Studio k úložištím Git a GitHubu, úložištím správy verzí Team Foundation (TFVC) a projektům hostovaným v [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) nebo v místní [Azure DevOps Server](/azure/devops/index-all) (dříve označované jako TFS). Můžete spravovat zdrojový kód, pracovní položky a sestavení.

::: moniker-end

::: moniker range="vs-2019"

Team Explorer připojuje sadu Visual Studio k úložištím verzí Team Foundation (TFVC) a k projektům hostovaným v [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) nebo v místní [Azure DevOps Server](/azure/devops/user-guide/about-azure-devops-services-tfs?view=azure-devops&preserve-view=true) (dříve označované jako TFS). Můžete spravovat zdrojový kód, pracovní položky a sestavení.

> [!IMPORTANT]
> S vydáním sady Visual Studio 2019 [**verze 16,8**](/visualstudio/releases/2019/release-notes-history)je prostředí pro řízení verzí Git ve výchozím nastavení zapnuté. Pokud se chcete dozvědět víc o tom, jak porovnává Team Explorer, podívejte se na [**Souběžné porovnání Gitu a Team Explorer**](../version-control/git-team-explorer-feature-comparison.md) stránky.
>
> Pokud ale dáváte přednost i nadále používat Team Explorer, přejděte do části **nástroje** > **Možnosti** > **prostředí** > **verze Preview** a potom zaškrtněte políčko **nové uživatelské prostředí Git** .

Způsob použití Team Explorer pro připojení k projektu závisí na verzi sady Visual Studio 2019, kterou používáte.

## <a name="in-version-168-and-later"></a>Ve verzi 16,8 a novější

1. Otevřete Visual Studio 2019.

1. V okně Start vyberte **klonovat úložiště**.

   ![Snímek obrazovky s dialogovým oknem klonování úložiště v aplikaci Visual Studio 2019 verze 16,8 a novější pro Azure DevOps](../ide/media/vs-2019/clone-repository.png)

1. V části **Procházet úložiště** vyberte **Azure DevOps**.

    ![Snímek obrazovky s oddílem procházet úložiště v dialogovém okně připojit k projektu ve Visual Studiu 2019 verze 16,8 a novější](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. Pokud se zobrazí okno pro přihlášení, přihlaste se ke svému účtu.

1. V dialogovém okně **připojit k projektu** zvolte úložiště, ke kterému se chcete připojit, a pak vyberte **klonovat**.

      ![Snímek obrazovky dialogového okna připojit k projektu, které je vygenerováno ze sady Visual Studio 2019 verze 16,8 a novější](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > Pokud nevidíte předem vyplněný seznam úložišť, ke kterým se chcete připojit, vyberte **přidat Azure DevOps Server** a zadejte adresu URL serveru. (Případně se může zobrazit výzva "nebyly nalezeny žádné servery", která obsahuje odkazy na přidání existující Azure DevOps Server nebo vytvoření účtu Azure DevOps.)

   V dalším kroku se otevře aplikace Visual Studio **Průzkumník řešení** , která zobrazuje složky a soubory.

1. Vyberte kartu **Team Explorer** pro zobrazení akcí Azure DevOps.

      ![Snímek obrazovky s dialogem ' Team Explorer ', který je vygenerován ze sady Visual Studio 2019 verze 16,8 a novější](../ide/media/vs-2019/team-explorer-azure-devops.png)

## <a name="in-version-167-and-earlier"></a>Ve verzi 16,7 a starší

1. Otevřete Visual Studio 2019.

1. V okně Start vyberte **klonovat nebo rezervovat kód**.

   ![Snímek obrazovky okna vytvořit nový projekt v aplikaci Visual Studio 2019 verze 16,7 a starší](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. V části **Procházet úložiště** vyberte **Azure DevOps**.

   ![Snímek obrazovky okna klonovat nebo rezervovat kód s částí procházet úložiště se seznamem Azure DevOps ve Visual Studiu 2019 verze 16,7 a starší](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Pokud se zobrazí okno pro přihlášení, přihlaste se ke svému účtu.

1. V dialogovém okně **připojit k projektu** zvolte úložiště, ke kterému se chcete připojit, a pak vyberte **klonovat**.

      ![Snímek obrazovky dialogového okna připojit k projektu, které je vygenerováno ze sady Visual Studio 2019 verze 16,7 a starší](../get-started/media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Co vidíte v seznamu, závisí na úložištích Azure DevOps, ke kterým máte přístup.

   Otevře se aplikace Visual Studio **Team Explorer** a po dokončení klonu se zobrazí oznámení.

     ![Snímek obrazovky okna Team Explorer v aplikaci Visual Studio 2019 verze 16,7 a starší po dokončení klonu](../get-started/media/vs-2019/clone-complete-azure-devops.png)

1. Chcete-li zobrazit složky a soubory, vyberte odkaz **Zobrazit zobrazení složky** .

     ![Snímek obrazovky oddílu Solutions okna Team Explorer v aplikaci Visual Studio 2019 verze 16,7 a starší po dokončení klonu](../get-started/media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio otevře **Průzkumník řešení**.

1. Vyberte odkaz **řešení a složky** a vyhledejte soubor řešení (konkrétně soubor. sln), který chcete otevřít.

      ![Snímek obrazovky s oznámením o řešeních a složkách od Team Explorer ve Visual Studiu 2019 verze 16,7 a starší](../get-started/media/open-proj-repo-solutions-folders.png)

   Pokud v úložišti nemáte soubor řešení, zobrazí se zpráva "žádná řešení nalezena&quot;. Můžete však dvakrát kliknout na libovolný soubor v nabídce složka a otevřít ho v editoru kódu sady Visual Studio.

::: moniker-end

::: moniker range=&quot;vs-2017&quot;

![Team Explorer domovskou stránku v aplikaci Visual Studio](media/team-explorer/team-explorer.png &quot;Team Explorer – Domovská stránka v aplikaci Visual Studio.")

> [!TIP]
> Pokud otevřete Visual Studio a **Team Explorer** se nezobrazí, otevřete ho tak, že v řádku nabídek kliknete na **Zobrazit**  >  **Team Explorer** nebo stisknete **CTRL** + **&#92;**, **CTRL** + **M**.

## <a name="connect-to-a-project-or-repository"></a>Připojení k projektu nebo úložišti

Připojte se k projektu nebo úložišti na stránce **připojit** .

![Připojit stránku v Team Explorer](media/team-explorer/connect.png "Stránka Team Explorer-Connect v aplikaci Visual Studio")

Připojení k projektu:

1. Otevřete stránku **připojit** výběrem ikony **Spravovat připojení** .

   ![Tlačítko Spravovat připojení v Team Explorer](media/team-explorer/manage-connections.png "Tlačítko Team Explorer-spravovat připojení v aplikaci Visual Studio.")

1. Na stránce **připojit** vyberte možnost **Spravovat připojení** > **připojit k projektu**.

   ![Připojit se k projektu v Team Explorer](media/team-explorer/connect-project.png "Team Explorer – připojení k možnosti projektu v aplikaci Visual Studio.")

> [!TIP]
> Pokud chcete otevřít projekt z úložiště, přečtěte si téma [otevření projektu z úložiště](../get-started/tutorial-open-project-from-repo-visual-studio-2017.md). Pokud chcete vytvořit nový projekt nebo přidat uživatele do projektu, přečtěte si téma [Vytvoření projektu (Azure DevOps)](/azure/devops/organizations/projects/create-project) a [Přidání uživatelů do projektu nebo týmu (Azure DevOps)](/azure/devops/organizations/security/add-users-team-project).

::: moniker-end

## <a name="see-also"></a>Viz také

- [Porovnání Gitu a Team Explorer vedle sebe](git-team-explorer-feature-comparison.md)
- [Nové prostředí Git v aplikaci Visual Studio](git-with-visual-studio.md)
- [Referenční dokumentace k Team Exploreru](reference/team-explorer-reference.md)
- [Připojení k projektu (Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects)
- [Řešení potíží s připojením k projektu](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops&preserve-view=true)
