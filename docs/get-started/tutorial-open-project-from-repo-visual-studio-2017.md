---
title: 'Kurz: otevření projektu z úložiště v aplikaci Visual Studio 2017'
description: Naučte se, jak otevřít projekt v úložišti Git nebo Azure DevOps pomocí sady Visual Studio 2017.
ms.custom: get-started
ms.date: 01/25/2021
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
monikerRange: vs-2017
ms.openlocfilehash: 6989de1c5b4542998d048e5eadd47f48dc7e05b1
ms.sourcegitcommit: cfeffe2364275a347db0ba2dce36d8e80001c081
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2021
ms.locfileid: "99181292"
---
# <a name="tutorial-open-a-project-from-a-repo-in-visual-studio-2017"></a>Kurz: otevření projektu z úložiště v aplikaci Visual Studio 2017

V tomto kurzu použijete Visual Studio 2017 k prvnímu připojení k úložišti a pak z něho otevřete projekt.

> [!TIP]
> Existuje nový, plně integrovaný způsob připojení k úložišti GitHub v [aplikaci Visual Studio 2019](https://visualstudio.microsoft.com/downloads). Další informace najdete na stránce [**nové prostředí Git v aplikaci Visual Studio 2019**](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true) .

## <a name="open-a-project-from-a-github-repo-by-using-visual-studio-2017"></a>Otevření projektu z úložiště GitHub pomocí sady Visual Studio 2017

1. Otevřete sadu Visual Studio 2017.

1. V horním řádku nabídek vyberte otevřít **soubor**  >    >  **Otevřít ze správy zdrojového kódu**.

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

## <a name="open-a-project-from-an-azure-devops-repo-by-using-visual-studio-2017"></a>Otevření projektu z úložiště Azure DevOps pomocí sady Visual Studio 2017

1. Otevřete sadu Visual Studio 2017.

1. V horním řádku nabídek vyberte otevřít **soubor**  >    >  **Otevřít ze správy zdrojového kódu**.

   Otevře se podokno **Team Explorer – připojit** .

    ![Team Explorer okno v integrovaném vývojovém prostředí sady Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Tady jsou dva způsoby, jak se připojit k úložišti Azure DevOps:

      - V části **poskytovatelé hostovaných služeb** vyberte **připojit...**.

        ![Část poskytovatele hostovaných služeb v okně Team Explorer v rámci integrovaného vývojového prostředí (IDE) sady Visual Studio](./media/open-proj-repo-azure-devops.png)

      - V rozevíracím seznamu **Spravovat připojení** vyberte **připojit k projektu...**.

        ![Oddíl spravovat připojení v okně Team Explorer v rámci integrovaného vývojového prostředí (IDE) sady Visual Studio](./media/open-proj-repo-azuredevops-manage-connections.png)

1. V dialogovém okně **připojit k projektu** zvolte úložiště, ke kterému se chcete připojit, a pak vyberte **klonovat**.

      ![Dialogové okno připojit k projektu, které je vygenerováno ze sady Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Co vidíte v seznamu, závisí na úložištích Azure DevOps, ke kterým máte přístup.

1. Jakmile aplikace Visual Studio naklonuje vaše úložiště, Team Explorer se zavře a Průzkumník řešení otevře. Zobrazí se zpráva s informacemi *o tom, jak kliknout na řešení a složky výše, a zobrazit seznam řešení*. Vyberte **řešení a složky**.

      ![Oznámení "řešení a složky" z Team Explorer v aplikaci Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Soubor řešení (konkrétně soubor. sln) se zobrazí v rozevírací nabídce "řešení a složky". Vyberte ho a Visual Studio otevře vaše řešení.

   Pokud ve svém úložišti nemáte soubor řešení, pozastaví se nabídka bez nalezených řešení. Můžete však dvakrát kliknout na libovolný soubor v nabídce složka a otevřít ho v editoru kódu sady Visual Studio.

## <a name="next-steps"></a>Další kroky

Pokud jste připravení na kód v rámci sady Visual Studio 2017, podrobně do některého z následujících kurzů pro konkrétní jazyk:

- [Kurzy pro Visual Studio | **Jazyk C#**](./csharp/index.yml)
- [Kurzy pro Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Kurzy pro Visual Studio | **Jazyk C++**](/cpp/get-started/tutorial-console-cpp)
- [Kurzy pro Visual Studio | **Python**](../python/index.yml)
- [Kurzy pro Visual Studio | **JavaScript**, **TypeScript** a **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Viz také

- [Azure DevOps Services: Začínáme s Azure Repos a sadou Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Začínáme s Azure DevOps](/learn/modules/get-started-with-devops/)
- [Nové prostředí Git v aplikaci Visual Studio 2019](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true)
