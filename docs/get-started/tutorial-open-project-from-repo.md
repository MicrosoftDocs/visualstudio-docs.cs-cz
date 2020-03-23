---
title: 'Kurz: Otevření projektu z repo'
description: Zjistěte, jak otevřít projekt v úložišti Git nebo Azure DevOps pomocí Visual Studia.
ms.custom: get-started
ms.date: 03/30/2019
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
ms.openlocfilehash: 3af54d663cee1ad2b2dd4e8241678b88c635d376
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "70180436"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Kurz: Otevření projektu z repo

V tomto kurzu budete používat Visual Studio pro první připojení k úložišti a potom z něj otevřete projekt.

::: moniker range="vs-2017"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ji zdarma.

::: moniker-end

## <a name="open-a-project-from-a-github-repo"></a>Otevření projektu z úložiště GitHub

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

1. V horním řádku nabídek zvolte Otevřít **soubor** > **Open** > **ze správy zdrojového kódu**.

   Otevře se **podokno Průzkumník týmu – Připojit** se otevře.

    ![Okno Průzkumníka týmu v rozhraní IDE sady Visual Studio](./media/open-proj-repo-team-explorer.png)

1. V části **Místní úložiště Git** zvolte **Klonování**.

    ![Zvolte Klonování v části Místní úložiště Git.](./media/open-proj-repo-local-git-repo-clone.png)

1. Do pole s ***textem Zadejte adresu URL úložiště Git, které chcete klonovat***, zadejte nebo vložte adresu URL úložiště a stiskněte **Enter**. (Můžete obdržet výzvu k přihlášení k GitHubu; pokud ano, udělejte to.)

   Po Visual Studio klony repo, Průzkumník týmu zavře a Průzkumník řešení otevře. Zobrazí se zpráva s *textem Klikněte na řešení a složky výše pro zobrazení seznamu řešení*. Zvolte **Řešení a složky**.

   ![Zvolte "Řešení a složky" z Průzkumníka řešení](./media/open-proj-repo-github-solutions-folders.png)

1. Pokud máte k dispozici soubor řešení, zobrazí se v informační nabídce "Řešení a složky". Vyberte ji a Visual Studio otevře vaše řešení.

   ![V rozevíracím seznamu Průzkumník řešení zvolte, co chcete otevřít.](./media/open-proj-repo-github-solutions-folders-picker.png)

   Pokud nemáte soubor řešení (konkrétně soubor .sln) v repo, rozbalovací menu bude říkat "Nebyla nalezena žádná řešení". Můžete však poklepat na libovolný soubor z nabídky složek a otevřít jej v editoru kódu sady Visual Studio.

### <a name="review-your-work"></a>Kontrola práce

V následující animaci zkontrolujte práci, kterou jste dokončili v předchozí části.

   ![Animace otevření projektu v úložišti GitHub pomocí sady Visual Studio](./media/open-project-from-github.gif)

::: moniker-end

::: moniker range="vs-2019"

1. Otevřete Visual Studio 2019.

1. V úvodním okně zvolte **Klonování nebo kód rezervovat**.

   ![Zobrazit okno Vytvořit nový projekt](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Zadejte nebo zadejte umístění úložiště a pak zvolte **Klonovat**.

   ![Zobrazit okno Klonovací kód nebo kód pokladny](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio otevře projekt z repo.

1. Pokud máte k dispozici soubor řešení, zobrazí se v informační nabídce "Řešení a složky". Vyberte ji a Visual Studio otevře vaše řešení.

   ![V rozevíracím seznamu Průzkumník řešení zvolte, co chcete otevřít.](./media/open-proj-repo-github-solutions-folders-picker.png)

   Pokud nemáte soubor řešení (konkrétně soubor .sln) v repo, rozbalovací menu bude říkat "Nebyla nalezena žádná řešení". Můžete však poklepat na libovolný soubor z nabídky složek a otevřít jej v editoru kódu sady Visual Studio.

::: moniker-end

## <a name="open-a-project-from-an-azure-devops-repo"></a>Otevření projektu z repo Azure DevOps

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

1. V horním řádku nabídek zvolte Otevřít **soubor** > **Open** > **ze správy zdrojového kódu**.

   Otevře se **podokno Průzkumník týmu – Připojit** se otevře.

    ![Okno Průzkumníka týmu v rozhraní IDE sady Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Tady jsou dva způsoby, jak se připojit k vašemu repo Azure DevOps:

      - V části **Hostitelé služeb** zvolte **Připojit...**.

        ![Část Hostitelé služeb v okně Průzkumník týmu v rozhraní IDE sady Visual Studio](./media/open-proj-repo-azure-devops.png)

      - V rozevíracím seznamu **Spravovat připojení** zvolte Připojit **k projectu...**.

        ![Část Spravovat připojení v okně Průzkumníka týmu v rozhraní IDE sady Visual Studio](./media/open-proj-repo-azuredevops-manage-connections.png)

1. V **dialogovém** okně Připojit k projektu zvolte úložiště, ke kterému se chcete připojit, a pak zvolte **Klonovat**.

      ![Dialogové okno Připojit k projektu, které je generováno z Visual Studia](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Co se zobrazí v seznamu závisí na azure devops úložišť, které máte přístup.

1. Po Visual Studio klony repo, Průzkumník týmu zavře a Průzkumník řešení otevře. Zobrazí se zpráva s *textem Klikněte na řešení a složky výše pro zobrazení seznamu řešení*. Zvolte **Řešení a složky**.

      ![Oznámení "Řešení a složky" z Průzkumníka týmu v sadě Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Soubor řešení (konkrétně soubor .sln) se zobrazí v rozbalovací nabídce "Řešení a složky". Vyberte ji a Visual Studio otevře vaše řešení.

   Pokud nemáte soubor řešení v repo, fly-out menu bude říkat "Žádná řešení nalezena". Můžete však poklepat na libovolný soubor z nabídky složek a otevřít jej v editoru kódu sady Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

1. Otevřete Visual Studio 2019.

1. V úvodním okně zvolte **Klonování nebo kód rezervovat**.

   ![Zobrazit okno Vytvořit nový projekt](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. V části **Procházet úložiště** zvolte **Azure DevOps**.

   ![Zobrazit okno Klonování nebo kód rezervovat](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Pokud se zobrazí přihlašovací okno, přihlaste se ke svému účtu.

1. V **dialogovém** okně Připojit k projektu zvolte úložiště, ke kterému se chcete připojit, a pak zvolte **Klonovat**.

      ![Dialogové okno Připojit k projektu, které je generováno z Visual Studia](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Co se zobrazí v seznamu závisí na azure devops úložišť, které máte přístup.

   Visual Studio otevře **Průzkumníka týmu** a po dokončení klonování se zobrazí oznámení.

     ![Okno Průzkumníktýmu v sadě Visual Studio po dokončení klonování](./media/vs-2019/clone-complete-azure-devops.png)

1. Chcete-li zobrazit složky a soubory, zvolte odkaz **Zobrazit zobrazení složky.**

     ![Část Řešení v okně Průzkumníktýmu v sadě Visual Studio po dokončení klonování](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio otevře **Průzkumníka řešení**.

1. Zvolte odkaz **Řešení a složky,** chcete-li vyhledat soubor řešení (konkrétně soubor .sln), který chcete otevřít.

      ![Oznámení "Řešení a složky" z Průzkumníka týmu v sadě Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Pokud nemáte soubor řešení v repo, zobrazí se zpráva "Žádná řešení nalezena". Můžete však poklepat na libovolný soubor z nabídky složek a otevřít jej v editoru kódu sady Visual Studio.

::: moniker-end

## <a name="next-steps"></a>Další kroky

Pokud jste připraveni ke kódování pomocí sady Visual Studio, ponořte se do některého z následujících kurzů specifických pro jazyk:

- [Výukové lekce visual studia | **C#**](./csharp/index.yml)
- [Výukové lekce visual studia | **Visual Basic**](./visual-basic/index.yml)
- [Výukové lekce visual studia | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Výukové lekce visual studia | **Python**](/visualstudio/python/)
- [Výukové lekce visual studia | **JavaScript**, **TypeScript**a **Node.js**](/visualstudio/javascript/)

## <a name="see-also"></a>Viz také

- [Azure DevOps Services: Začínáme s Azure Repos a Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Začínáme s Azure DevOps](/learn/modules/get-started-with-devops/)