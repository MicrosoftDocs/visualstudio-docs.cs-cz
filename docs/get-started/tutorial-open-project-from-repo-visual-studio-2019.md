---
title: 'Kurz: otevření projektu z úložiště v aplikaci Visual Studio 2019'
description: Naučte se, jak otevřít projekt v úložišti Git nebo Azure DevOps pomocí sady Visual Studio 2019.
ms.custom: vs-acquisition, get-started
ms.date: 03/18/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
monikerRange: vs-2019
ms.openlocfilehash: b6f7cd57a1753ca5926ac73a9bb4c8c918d1bd10
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389940"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Kurz: otevření projektu z úložiště

V tomto kurzu použijete Visual Studio k prvnímu připojení k úložišti a pak z něho otevřete projekt.

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

## <a name="open-a-project-from-a-github-repo"></a>Otevření projektu z úložiště GitHub

Způsob otevření projektu z úložiště GitHub pomocí sady Visual Studio 2019 závisí na tom, kterou verzi máte. Konkrétně, pokud jste nainstalovali verzi verze [**16,8**](/visualstudio/releases/2019/release-notes/) nebo novější, je k dispozici nové a plně integrované [prostředí Git v aplikaci Visual Studio](../ide/git-with-visual-studio.md) .

Ale bez ohledu na to, jakou verzi jste nainstalovali, můžete vždy otevřít projekt z úložiště GitHub se sadou Visual Studio.

#### <a name="168-and-later"></a>[16,8 a novější](#tab/vs168later)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Naklonujte úložiště GitHub a pak otevřete projekt.

1. Otevřete Visual Studio 2019.

1. V okně Start vyberte **klonovat úložiště**.

   ![Snímek obrazovky s dialogovým oknem klonování úložiště v aplikaci Visual Studio 2019 verze 16,8 a novější](../ide/media/vs-2019/clone-repository.png)

1. Zadejte nebo zadejte umístění úložiště a pak vyberte **klonovat**.

   ![Snímek obrazovky s dialogovým oknem klonovat úložiště, kde zadáte adresu URL úložiště Git ve Visual Studiu 2019 verze 16,8 a novější](../ide/media/vs-2019/clone-repository-enter-location.png)

1. V dialogovém okně **informace o uživateli Git** se může zobrazit výzva k zadání přihlašovacích údajů uživatele. Můžete buď přidat svoje informace, nebo upravit výchozí informace, které poskytuje.

   ![Snímek obrazovky dialogového okna informace o uživateli Git, kam zadáte nebo upravíte informace o účtu v aplikaci Visual Studio 2019 verze 16,8 a novější](../ide/media/vs-2019/git-user-information-dialog.png)

    Pokud chcete přidat informace do globálního souboru. gitconfig, vyberte **Save (Uložit** ). (Nebo ji můžete zvolit později kliknutím na **Zrušit**.)

    > [!TIP]
    > Další informace o přihlašování k aplikaci Visual Studio naleznete na stránce [přihlášení do sady Visual Studio](../ide/signing-in-to-visual-studio.md) . Konkrétní informace o tom, jak se přihlašovat pomocí účtu GitHubu, najdete v tématu [práce s účty GitHubu na stránce sady Visual Studio](../ide/work-with-github-accounts.md) .

    V dalším kroku aplikace Visual Studio automaticky načte a otevře řešení z úložiště.

   ![Snímek obrazovky projektu v Gitu, který je otevřený v Průzkumník řešení ve Visual Studiu 2019 verze 16,8 a novější](../ide/media/vs-2019/git-solution-explorer.png )

1. Pokud vaše úložiště obsahuje více řešení, zobrazí se v Průzkumník řešení. Seznam řešení můžete zobrazit tak, že v Průzkumník řešení vyberete tlačítko **Přepnout zobrazení** .

   ![Snímek obrazovky projektu v Gitu, který je otevřený v Průzkumník řešení, s tlačítkem zobrazení přepínače zvýrazněným ve Visual Studiu 2019 verze 16,8 a novější](../ide/media/vs-2019/git-solution-explorer-switch-views.png)

   Průzkumník řešení pak nabídne možnost otevřít kořenovou složku v **zobrazení složky** nebo vybrat soubor řešení, který chcete otevřít.

   ![Snímek obrazovky se souborem. sln v Gitu, který je otevřený v Průzkumník řešení, po výběru tlačítka pro zobrazení přepínače v aplikaci Visual Studio 2019 verze 16,8 a novější](../ide/media/vs-2019/git-solution-explorer-view-solution.png)

    Chcete-li přepnout zobrazení, klikněte znovu na tlačítko **Přepnout zobrazení** .

    > [!TIP]
    > Můžete také použít nabídku **Git** v integrovaném vývojovém prostředí sady Visual Studio k naklonování úložiště a otevření projektu.
    >
    > ![Snímek nabídky Git v aplikaci Visual Studio 2019 verze 16,8 a novější](../ide/media/vs-2019/git-menu-clone-create-git-repository.png)

#### <a name="open-a-project-locally-from-a-previously-cloned-github-repo"></a>Otevření projektu místně z dříve naklonovaného úložiště GitHubu

1. Otevřete Visual Studio 2019.

1. V okně Start vyberte **Otevřít projekt nebo řešení**.

    Visual Studio otevře instanci Průzkumníka souborů, kde můžete přejít k řešení nebo projektu a pak ho vybrat k otevření.

   ![Snímek obrazovky okna otevřít projekt nebo řešení v aplikaci Visual Studio 2019 verze 16,8 a novější](../ide/media/vs-2019/open-local-project-from-cloned-repo.png)

    Pokud jste projekt nebo řešení v poslední době otevřeli, vyberte ho v části **otevřít poslední** a rychle ho otevřete.

    > [!TIP]
    > Můžete také použít nabídku **Git** v integrovaném vývojovém prostředí sady Visual Studio k otevření místních složek a souborů z úložiště, které jste předtím naklonoval.
    >
    > ![Snímek nabídky Git v aplikaci Visual Studio 2019 verze 16,8 a novější s rozšířenou možností místní úložiště](../ide/media/vs-2019/git-menu-local-repositories.png)

    Spustit kódování!

#### <a name="167-and-earlier"></a>[16,7 a starší](#tab/vs167earlier)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Naklonujte úložiště GitHub a pak otevřete projekt.

1. Otevřete Visual Studio 2019.

1. V okně Start vyberte **klonovat nebo rezervovat kód**.

   ![Snímek obrazovky okna vytvořit nový projekt v aplikaci Visual Studio 2019 verze 16,7 a starší](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Zadejte nebo zadejte umístění úložiště a pak vyberte **klonovat**.

   ![Snímek obrazovky okna klonovat nebo rezervovat kód v aplikaci Visual Studio 2019 verze 16,7 a starší](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio otevře projekt z úložiště.

1. Pokud máte soubor řešení k dispozici, zobrazí se v rozevírací nabídce "řešení a složky". Vyberte ho a Visual Studio otevře vaše řešení.

   ![Snímek obrazovky s rozevíracím seznamem Průzkumník řešení v aplikaci Visual Studio 2019 verze 16,7 a starší](./media/open-proj-repo-github-solutions-folders-picker.png)

   Pokud v úložišti nemáte soubor řešení (konkrétně soubor. sln), nabídka rozchodu označuje "nenašla se žádná řešení." Můžete však dvakrát kliknout na libovolný soubor v nabídce složka a otevřít ho v editoru kódu sady Visual Studio.

    Spustit kódování!

---

> [!NOTE]
> Informace, které jsou specifické pro Visual Studio 2017, najdete v tématu [otevření projektu na stránce úložiště v aplikaci Visual Studio 2017](tutorial-open-project-from-repo-visual-studio-2017.md) .

## <a name="connect-to-an-azure-devops-server"></a>Připojení k serveru Azure DevOps

Co vidíte, když se připojíte k serveru Azure DevOps pomocí sady Visual Studio 2019 závisí na tom, kterou verzi máte. Konkrétně, pokud jste nainstalovali verzi verze [**16,8**](/visualstudio/releases/2019/release-notes/) nebo novější, změnili jsme uživatelské rozhraní tak, aby vyhovovalo novému a více plně integrovanému [prostředí Git v](../ide/git-with-visual-studio.md) aplikaci Visual Studio.

Ale bez ohledu na to, kterou verzi máte nainstalovanou, se můžete kdykoli připojit k serveru Azure DevOps pomocí sady Visual Studio.

#### <a name="168-and-later"></a>[16,8 a novější](#tab/vs168later)

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

#### <a name="167-and-earlier"></a>[16,7 a starší](#tab/vs167earlier)

1. Otevřete Visual Studio 2019.

1. V okně Start vyberte **klonovat nebo rezervovat kód**.

   ![Snímek obrazovky okna vytvořit nový projekt v aplikaci Visual Studio 2019 verze 16,7 a starší](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. V části **Procházet úložiště** vyberte **Azure DevOps**.

   ![Snímek obrazovky okna klonovat nebo rezervovat kód s částí procházet úložiště se seznamem Azure DevOps ve Visual Studiu 2019 verze 16,7 a starší](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Pokud se zobrazí okno pro přihlášení, přihlaste se ke svému účtu.

1. V dialogovém okně **připojit k projektu** zvolte úložiště, ke kterému se chcete připojit, a pak vyberte **klonovat**.

      ![Snímek obrazovky dialogového okna připojit k projektu, které je vygenerováno ze sady Visual Studio 2019 verze 16,7 a starší](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Co vidíte v seznamu, závisí na úložištích Azure DevOps, ke kterým máte přístup.

   Otevře se aplikace Visual Studio **Team Explorer** a po dokončení klonu se zobrazí oznámení.

     ![Snímek obrazovky okna Team Explorer v aplikaci Visual Studio 2019 verze 16,7 a starší po dokončení klonu](./media/vs-2019/clone-complete-azure-devops.png)

1. Chcete-li zobrazit složky a soubory, vyberte odkaz **Zobrazit zobrazení složky** .

     ![Snímek obrazovky oddílu Solutions okna Team Explorer v aplikaci Visual Studio 2019 verze 16,7 a starší po dokončení klonu](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio otevře **Průzkumník řešení**.

1. Vyberte odkaz **řešení a složky** a vyhledejte soubor řešení (konkrétně soubor. sln), který chcete otevřít.

      ![Snímek obrazovky s oznámením o řešeních a složkách od Team Explorer ve Visual Studiu 2019 verze 16,7 a starší](./media/open-proj-repo-solutions-folders.png)

   Pokud v úložišti nemáte soubor řešení, zobrazí se zpráva "žádná řešení nalezena". Můžete však dvakrát kliknout na libovolný soubor v nabídce složka a otevřít ho v editoru kódu sady Visual Studio.

---

## <a name="next-steps"></a>Další kroky

Pokud jste připravení na kód v rámci sady Visual Studio, podrobně do některého z následujících kurzů pro konkrétní jazyk:

- [Kurzy pro Visual Studio | **Jazyk C#**](./csharp/index.yml)
- [Kurzy pro Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Kurzy pro Visual Studio | **Jazyk C++**](/cpp/get-started/tutorial-console-cpp)
- [Kurzy pro Visual Studio | **Python**](../python/index.yml)
- [Visual Studio kurzy | **JavaScript,** **TypeScript** **aNode.js**](../javascript/index.yml)

## <a name="see-also"></a>Viz také

- [Otevření projektu z Visual Studio 2017](tutorial-open-project-from-repo-visual-studio-2017.md)
- [Nové prostředí Gitu v Visual Studio 2019](../ide/git-with-visual-studio.md)
- [Porovnání Team Explorer a Úložiště vedle sebe](../ide/git-team-explorer-feature-comparison.md)
- [Azure DevOps Services: Začínáme s Azure Repos a Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Začínáme s Azure DevOps](/learn/modules/get-started-with-devops/)
