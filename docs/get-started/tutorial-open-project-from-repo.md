---
title: 'Kurz: otevření projektu z úložiště'
description: Naučte se, jak otevřít projekt v úložišti Git nebo Azure DevOps pomocí sady Visual Studio.
ms.custom: get-started
ms.date: 11/10/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 91fb06a50fe0c992d3018aee31cfc963544f8b97
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436078"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Kurz: otevření projektu z úložiště

V tomto kurzu použijete Visual Studio k prvnímu připojení k úložišti a pak z něho otevřete projekt.

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

## <a name="open-a-project-from-a-github-repo"></a>Otevření projektu z úložiště GitHub

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

1. V horním řádku nabídek vyberte otevřít **soubor** > **Open** > **Otevřít ze správy zdrojového kódu**.

   Otevře se podokno **Team Explorer – připojit** .

    ![Team Explorer okno v integrovaném vývojovém prostředí sady Visual Studio](./media/open-proj-repo-team-explorer.png)

1. V části **místní úložiště Git** vyberte **klonovat**.

    ![V části místní úložiště Git vyberte klonovat.](./media/open-proj-repo-local-git-repo-clone.png)

1. Do pole **_Zadejte adresu URL úložiště Git, které se má klonovat_*, zadejte nebo vložte adresu URL pro své úložiště a potom stiskněte _* ENTER**. (Můžete obdržet výzvu k přihlášení do GitHubu. Pokud ano, udělejte to.)

   Jakmile aplikace Visual Studio naklonuje vaše úložiště, Team Explorer se zavře a Průzkumník řešení otevře. Zobrazí se zpráva s informacemi *o tom, jak kliknout na řešení a složky výše, a zobrazit seznam řešení*. Vyberte **řešení a složky**.

   ![Vyberte řešení a složky z Průzkumník řešení](./media/open-proj-repo-github-solutions-folders.png)

1. Pokud máte soubor řešení k dispozici, zobrazí se v rozevírací nabídce "řešení a složky". Vyberte ho a Visual Studio otevře vaše řešení.

   ![Z rozevíracího seznamu Průzkumník řešení vyberte, co chcete otevřít.](./media/open-proj-repo-github-solutions-folders-picker.png)

   Pokud v úložišti nemáte soubor řešení (konkrétně soubor. sln), nabídka rozchodu znamená "žádná řešení nebyla nalezena." Můžete však dvakrát kliknout na libovolný soubor v nabídce složka a otevřít ho v editoru kódu sady Visual Studio.

### <a name="review-your-work"></a>Kontrola práce

Prohlédněte si následující animaci a zkontrolujte práci, kterou jste dokončili v předchozí části.

   ![Animace otevření projektu v úložišti GitHub pomocí sady Visual Studio](./media/open-project-from-github.gif)

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Pokud chcete vyzkoušet nové integrované prostředí Git v aplikaci Visual Studio 2019, nezapomeňte aktualizovat na [**verzi 16,8**](/visualstudio/releases/2019/release-notes/). Další informace najdete na stránce [nové prostředí Git na stránce sady Visual Studio](../ide/git-with-visual-studio.md) .

1. Otevřete Visual Studio 2019.

1. V okně Start vyberte **klonovat nebo rezervovat kód**.

   ![Zobrazit okno vytvořit nový projekt](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Zadejte nebo zadejte umístění úložiště a pak zvolte **klonovat**.

   ![Zobrazení okna klonovat nebo rezervovat kód](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio otevře projekt z úložiště.

1. Pokud máte soubor řešení k dispozici, zobrazí se v rozevírací nabídce "řešení a složky". Vyberte ho a Visual Studio otevře vaše řešení.

   ![Z rozevíracího seznamu Průzkumník řešení vyberte, co chcete otevřít.](./media/open-proj-repo-github-solutions-folders-picker.png)

   Pokud v úložišti nemáte soubor řešení (konkrétně soubor. sln), nabídka rozchodu znamená "žádná řešení nebyla nalezena." Můžete však dvakrát kliknout na libovolný soubor v nabídce složka a otevřít ho v editoru kódu sady Visual Studio.

::: moniker-end

## <a name="open-a-project-from-an-azure-devops-repo"></a>Otevření projektu z úložiště Azure DevOps

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

1. V horním řádku nabídek vyberte otevřít **soubor** > **Open** > **Otevřít ze správy zdrojového kódu**.

   Otevře se podokno **Team Explorer – připojit** .

    ![Team Explorer okno v integrovaném vývojovém prostředí sady Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Tady jsou dva způsoby, jak se připojit k úložišti Azure DevOps:

      - V části **poskytovatelé hostovaných služeb** vyberte **připojit...**.

        ![Část poskytovatele hostovaných služeb v okně Team Explorer v rámci integrovaného vývojového prostředí (IDE) sady Visual Studio](./media/open-proj-repo-azure-devops.png)

      - V rozevíracím seznamu **Spravovat připojení** vyberte **připojit k projektu...**.

        ![Oddíl spravovat připojení v okně Team Explorer v rámci integrovaného vývojového prostředí (IDE) sady Visual Studio](./media/open-proj-repo-azuredevops-manage-connections.png)

1. V dialogovém okně **připojit k projektu** zvolte úložiště, ke kterému se chcete připojit, a pak zvolte **klonovat**.

      ![Dialogové okno připojit k projektu, které je vygenerováno ze sady Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Co vidíte v seznamu, závisí na úložištích Azure DevOps, ke kterým máte přístup.

1. Jakmile aplikace Visual Studio naklonuje vaše úložiště, Team Explorer se zavře a Průzkumník řešení otevře. Zobrazí se zpráva s informacemi *o tom, jak kliknout na řešení a složky výše, a zobrazit seznam řešení*. Vyberte **řešení a složky**.

      ![Oznámení "řešení a složky" z Team Explorer v aplikaci Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Soubor řešení (konkrétně soubor. sln) se zobrazí v rozevírací nabídce "řešení a složky". Vyberte ho a Visual Studio otevře vaše řešení.

   Pokud ve svém úložišti nemáte soubor řešení, pozastaví se nabídka bez nalezených řešení. Můžete však dvakrát kliknout na libovolný soubor v nabídce složka a otevřít ho v editoru kódu sady Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

1. Otevřete Visual Studio 2019.

1. V okně Start vyberte **klonovat nebo rezervovat kód**.

   ![Zobrazit okno vytvořit nový projekt](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. V části **Procházet úložiště** vyberte **Azure DevOps**.

   ![Zobrazit okno klonovat nebo rezervovat kód](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Pokud se zobrazí okno pro přihlášení, přihlaste se ke svému účtu.

1. V dialogovém okně **připojit k projektu** zvolte úložiště, ke kterému se chcete připojit, a pak zvolte **klonovat**.

      ![Dialogové okno připojit k projektu, které je vygenerováno ze sady Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Co vidíte v seznamu, závisí na úložištích Azure DevOps, ke kterým máte přístup.

   Otevře se aplikace Visual Studio **Team Explorer** a po dokončení klonu se zobrazí oznámení.

     ![Team Explorer okno v aplikaci Visual Studio po dokončení klonování](./media/vs-2019/clone-complete-azure-devops.png)

1. Chcete-li zobrazit složky a soubory, klikněte na odkaz **Zobrazit zobrazení složky** .

     ![Oddíl Solutions okna Team Explorer v aplikaci Visual Studio po dokončení klonu](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio otevře **Průzkumník řešení**.

1. Vyberte odkaz **řešení a složky** a vyhledejte soubor řešení (konkrétně soubor. sln), který chcete otevřít.

      ![Oznámení "řešení a složky" z Team Explorer v aplikaci Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Pokud v úložišti nemáte soubor řešení, zobrazí se zpráva "bez nalezených řešení". Můžete však dvakrát kliknout na libovolný soubor v nabídce složka a otevřít ho v editoru kódu sady Visual Studio.

::: moniker-end

## <a name="next-steps"></a>Další kroky

Pokud jste připravení na kód v rámci sady Visual Studio, podrobně do některého z následujících kurzů pro konkrétní jazyk:

- [Kurzy pro Visual Studio | **Jazyk C#**](./csharp/index.yml)
- [Kurzy pro Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Kurzy pro Visual Studio | **Jazyk C++**](/cpp/get-started/tutorial-console-cpp)
- [Kurzy pro Visual Studio | **Python**](../python/index.yml)
- [Kurzy pro Visual Studio | **JavaScript** , **TypeScript** a **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Viz také

::: moniker range="vs-2017"

- [Azure DevOps Services: Začínáme s Azure Repos a sadou Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Začínáme s Azure DevOps](/learn/modules/get-started-with-devops/)
- [Nové prostředí Git v aplikaci Visual Studio 2019](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true)

::: moniker-end

::: moniker range="vs-2019"

- [Nové prostředí Git v aplikaci Visual Studio](../ide/git-with-visual-studio.md)
- [Azure DevOps Services: Začínáme s Azure Repos a sadou Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Začínáme s Azure DevOps](/learn/modules/get-started-with-devops/)

::: moniker-end
