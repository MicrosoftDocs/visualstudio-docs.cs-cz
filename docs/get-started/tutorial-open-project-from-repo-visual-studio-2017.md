---
title: 'Kurz: Otevření projektu z Visual Studio 2017'
description: Zjistěte, jak otevřít projekt v Gitu nebo Azure DevOps úložiště pomocí Visual Studio 2017.
ms.custom: vs-acquisition, get-started
ms.date: 02/15/2021
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
monikerRange: vs-2017
ms.openlocfilehash: 5543a568f7246d9600ba375d9a1cf19af4cbd2d4
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389199"
---
# <a name="tutorial-open-a-project-from-a-repo-in-visual-studio-2017"></a>Kurz: Otevření projektu z Visual Studio 2017

V tomto kurzu použijete Visual Studio 2017 pro první připojení k úložišti a pak z něj otevřete projekt.

> [!TIP]
> V roce 2019 je k dispozici nový, plně integrovaný způsob připojení k úložišti GitHub [Visual Studio 2019.](https://visualstudio.microsoft.com/downloads) Další informace najdete na stránce [**Nové prostředí Git Visual Studio 2019.**](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true)

## <a name="open-a-project-from-a-github-repo-by-using-visual-studio-2017"></a>Otevření projektu z úložiště GitHub pomocí Visual Studio 2017

1. Otevřete sadu Visual Studio 2017.

1. V horním řádku nabídek vyberte **File** Open Open from Source Control (Otevřít  >    >  **soubor otevřít ze správy zdrojového kódu).**

   Otevře **Team Explorer –** Připojit.

    ![Okno Team Explorer v integrovaném vývojovém prostředí Visual Studio ideu](./media/open-proj-repo-team-explorer.png)

1. V části **Místní úložiště Git vyberte** Clone (Klonovat). 

    ![V části Místní úložiště Git zvolte Clone (Klonovat).](./media/open-proj-repo-local-git-repo-clone.png)

1. Do pole s textem * Zadejte adresu URL úložiště **Git,** do něj zadejte nebo vložte adresu URL úložiště a stiskněte _*Enter**. (Může se zobrazit výzva k přihlášení ke GitHubu. Pokud ano, můžete to udělat.)

   Po Visual Studio klonování se vaše Team Explorer zavře a Průzkumník řešení otevře. Zobrazí se zpráva *Klikněte na Řešení a složky výše a zobrazte seznam řešení.* Zvolte **Řešení a složky.**

   ![Zvolte Řešení a složky z Průzkumník řešení](./media/open-proj-repo-github-solutions-folders.png)

1. Pokud máte k dispozici soubor řešení, zobrazí se v místní nabídce Řešení a složky. Zvolte ji a Visual Studio otevře vaše řešení.

   ![V rozevíracím seznamu vyberte, co Průzkumník řešení otevřít.](./media/open-proj-repo-github-solutions-folders-picker.png)

   Pokud v tomto repo nemáte soubor řešení (konkrétně soubor .sln), v místní nabídce se zobrazí Zpráva Nenašla se žádná řešení. Dvojitým kliknutím na libovolný soubor z nabídky složky ho ale můžete otevřít v editoru Visual Studio kódu.

### <a name="review-your-work"></a>Kontrola práce

Podívejte se na následující animaci a zkontrolujte práci, kterou jste dokončili v předchozí části.

   ![Animace otevření projektu v úložišti GitHub pomocí Visual Studio](./media/open-project-from-github.gif)

> [!NOTE]
> Informace specifické pro Visual Studio 2019 najdete na stránce Otevření projektu z [Visual Studio 2019.](tutorial-open-project-from-repo-visual-studio-2019.md)

## <a name="open-a-project-from-an-azure-devops-repo-by-using-visual-studio-2017"></a>Otevření projektu z Azure DevOps pomocí Visual Studio 2017

1. Otevřete sadu Visual Studio 2017.

1. V horním řádku nabídek vyberte **File** Open Open from Source Control (Otevřít  >    >  **soubor otevřít ze správy zdrojového kódu).**

   Otevře **Team Explorer –** Připojit.

    ![Okno Team Explorer v integrovaném vývojovém prostředí Visual Studio ideu](./media/open-proj-repo-team-explorer.png)

1. Tady jsou dva způsoby připojení k vašemu Azure DevOps:

      - V části **Poskytovatelé hostovaných** služeb vyberte **Připojit...**.

        ![Část Poskytovatelé hostovaných služeb v okně Team Explorer v integrovaném vývojovém prostředí Visual Studio.](./media/open-proj-repo-azure-devops.png)

      - V **rozevíracím seznamu** Spravovat připojení vyberte **Připojit k projektu...**.

        ![Část Správa připojení v okně Team Explorer integrovaného vývojového prostředí (IDE) Visual Studio.](./media/open-proj-repo-azuredevops-manage-connections.png)

1. V dialogovém **okně Connect to a Project** (Připojit k projektu) zvolte repo, ke které se chcete připojit, a pak vyberte Clone (Klonovat). 

      ![Dialogové okno Připojit k projektu vygenerované z Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > To, co se zobrazí v seznamu, závisí na Azure DevOps, ke které máte přístup.

1. Po Visual Studio klonování se vaše Team Explorer zavře a Průzkumník řešení otevře. Zobrazí se zpráva *Klikněte na Řešení a složky výše a zobrazte seznam řešení.* Zvolte **Řešení a složky.**

      ![Oznámení "Řešení a složky" z Team Explorer v Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Soubor řešení (konkrétně soubor .sln) se zobrazí v místní nabídce Řešení a složky. Zvolte ji a Visual Studio otevře vaše řešení.

   Pokud v tomto repo nemáte soubor řešení, v místní nabídce se zobrazí Zpráva Nenašla se žádná řešení. Dvojitým kliknutím na libovolný soubor z nabídky složky ho ale můžete otevřít v editoru Visual Studio kódu.

## <a name="next-steps"></a>Další kroky

Pokud jste připraveni kódovat pomocí Visual Studio 2017, projděte si některý z následujících kurzů pro konkrétní jazyk:

- [Visual Studio kurzy | **C#**](./csharp/index.yml)
- [Visual Studio kurzy | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio kurzy | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio kurzy | **Python**](../python/index.yml)
- [Visual Studio kurzy | **JavaScript,** **TypeScript** **aNode.js**](../javascript/index.yml)

## <a name="see-also"></a>Viz také

- [Otevření projektu z Visual Studio 2019](tutorial-open-project-from-repo-visual-studio-2019.md)
- [Nové prostředí Gitu v Visual Studio 2019](../ide/git-with-visual-studio.md)
- [Azure DevOps Services: Začínáme s Azure Repos a Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Začínáme s Azure DevOps](/learn/modules/get-started-with-devops/)
