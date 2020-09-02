---
title: Začínáme s C++
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 99c73344-86ba-4b08-9e15-f6111cc04185
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 001b394d86e56b172bb1a50c335bd8ba5bcacb15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645620"
---
# <a name="getting-started-with-c-in-visual-studio"></a>Začínáme s C++ v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po dokončení tohoto návodu se seznámíte s mnoha nástroji a dialogovými okny, které můžete použít při vývoji aplikací pomocí sady Visual Studio. Vytvoříte jednoduchou aplikaci ve stylu "Hello, World" a získáte další informace o práci v integrovaném vývojovém prostředí (IDE).

 Toto téma obsahuje následující oddíly:

 [Přihlásit se k Visual Studiu](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_Configure)

 [Vytvoření jednoduché aplikace](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_CreateApp)

 [Přidat kód do aplikace](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_AddCode)

 [Ladění a testování aplikace](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_DebugTest)

 [Sestavení verze pro vydání aplikace](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_BuildRelease)

## <a name="sign-in-to-visual-studio"></a><a name="BKMK_Configure"></a> Přihlásit se k Visual Studiu
 Při prvním spuštění sady Visual Studio budete mít možnost se přihlásit pomocí účet Microsoft, jako je například Live nebo Outlook. Přihlášení umožňuje synchronizovat nastavení napříč všemi vašimi zařízeními. Další informace najdete v tématu [přihlášení do sady Visual Studio](../ide/signing-in-to-visual-studio.md) .

 Obrázek 1: integrované vývojové prostředí (IDE) sady Visual Studio

 ![IDE s použitým nastavením&#43;&#43; jazyka Visual C](../ide/media/c-ide-defaultenvironmentlayout.png "IDE_DefaultEnvironmentLayout c++")

 Po otevření sady Visual Studio se můžete podívat na tři základní části rozhraní IDE: okna nástrojů, nabídky a panely nástrojů a prostor hlavního okna. Okna nástrojů jsou ukotvena na levé a pravé straně okna aplikace, s možností **snadného spuštění**, řádku nabídek a standardní panel nástrojů v horní části. Uprostřed okna aplikace se nachází **Úvodní stránka**. Po otevření řešení nebo projektu se na tomto místě zobrazí editory a návrháři. Při vývoji aplikace strávíte nejvíce času v této centrální oblasti.

## <a name="create-a-simple-application"></a><a name="BKMK_CreateApp"></a> Vytvoření jednoduché aplikace
 Při vytváření aplikace v aplikaci Visual Studio je třeba nejprve vytvořit projekt a řešení. V tomto příkladu vytvoříte konzolovou aplikaci pro Windows.

#### <a name="to-create-a-console-app"></a>Vytvoření konzolové aplikace

1. Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.

    ![Na panelu nabídek vyberte možnosti soubor, nový, projekt.](../ide/media/exploreide-filenewproject.png "ExploreIDE-FileNewProject")

2. V kategorii **Visual C++** zvolte šablonu **Konzolová aplikace Win32** a potom název projektu `GreetingsConsoleApp` .

    ![Šablona konzolové aplikace Win32](../ide/media/c-ide-newprojectdlg.png "IDE_NewProjectDlg c++")

3. Po zobrazení Průvodce aplikací Win32 klikněte na tlačítko **Dokončit** .

    ![Průvodce konzolovou aplikací Win32](../ide/media/c-ide-win32consoleappwizard.png "IDE_Win32ConsoleAppWizard c++")

   Projekt a řešení GreetingsConsoleApp, se základními soubory pro konzolovou aplikaci Win32, se vytvoří a automaticky načtou do **Průzkumník řešení**. V editoru kódu se otevře soubor GreetingsConsoleApp. cpp. V **Průzkumník řešení**se zobrazí následující položky:

   Obrázek 4: položky projektu

   ![Soubory pro řešení v Průzkumník řešení](../ide/media/c-ide-solutioncontents.png "IDE_SolutionContents c++")

## <a name="add-code-to-the-application"></a><a name="BKMK_AddCode"></a> Přidat kód do aplikace
 Dále přidáte kód, který zobrazí slovo "Hello" v okně konzoly.

#### <a name="to-display-hello-in-the-console-window"></a>Zobrazení "Hello" v okně konzoly

1. V souboru GreetingsConsoleApp. cpp zadejte před řádek prázdný řádek `return 0;` a zadejte následující kód:

    ```
    cout << "Hello\n";
    ```

     V části je zobrazena červená vlnovka `cout` . Pokud na ni odkazujete, zobrazí se chybová zpráva.

     ![Text chyby pro cout](../ide/media/c-ide-couterror.png "IDE_CoutError c++")

     Chybová zpráva se zobrazí také v okně **Seznam chyb** . Můžete zobrazit okno podle, v řádku nabídek, výběrem možnosti **zobrazení**, **Seznam chyb**.

     [cout](https://msdn.microsoft.com/library/d87db6c3-e4e1-4d09-9ec5-458f55018257) je součástí \<iostream\> souboru hlaviček.

2. Chcete-li zahrnout hlavičku iostream –, zadejte následující kód po `#include "stdafx.h"` :

    ```
    #include \<iostream\>
    using namespace std;
    ```

     Pravděpodobně jste si všimli, že při zadávání kódu se objevilo pole, které poskytuje návrhy na zadané znaky. Toto pole je součástí C++ IntelliSense, který poskytuje výzvy pro kódování, včetně výpisu tříd nebo členů rozhraní a informací o parametrech. Můžete také použít fragmenty kódu, které jsou předem definované bloky kódu. Další informace naleznete v tématu [Using IntelliSense](../ide/using-intellisense.md) a [fragmenty kódu](../ide/code-snippets.md).

     Červená vlnovka v rámci `cout` zmizí při opravě chyby.

3. Uložte změny souboru.

     ![Kód, který opravuje chybu cout](../ide/media/c-ide-coutfix.png "IDE_CoutFix c++")

## <a name="debug-and-test-the-application"></a><a name="BKMK_DebugTest"></a> Ladění a testování aplikace
 Můžete ladit GreetingsConsoleApp a zjistit, zda se v okně konzoly zobrazí slovo "Hello".

#### <a name="to-debug-the-application"></a>Ladění aplikace

- Spusťte ladicí program.

     ![Spustit ladění – příkaz v nabídce ladění](../ide/media/exploreide-startdebugging.png "ExploreIDE-StartDebugging")

     Ladicí program se spustí a spustí kód. Okno konzoly (samostatné okno, které vypadá jako příkazový řádek), se zobrazí po dobu několika sekund, ale při zastavení ladicího programu se rychle zavře. Chcete-li zobrazit text, je nutné nastavit zarážku pro zastavení provádění programu.

#### <a name="to-add-a-breakpoint"></a>Přidání zarážky

1. Přidejte zarážku z řádku nabídek na řádku `return 0;` . Můžete také pouze kliknout na levý okraj pro nastavení zarážky.

    ![Přepnout zarážku – příkaz v nabídce ladění](../ide/media/exploreide-togglebreakpoint.png "ExploreIDE – Togglebreakpoint –")

    Na levém okraji okna editoru se vedle řádku kódu zobrazí červený kruh.

2. Kliknutím na klávesu F5 spusťte ladění.

    Spustí se ladicí program a zobrazí se okno konzoly se zobrazeným slovem **Hello**.

    ![Text Hello v okně příkazového řádku systému Windows](../ide/media/c-ide-hellocommandwindow.png "IDE_HelloCommandWindow c++")

3. Pro zastavení ladění stiskněte SHIFT + F5.

   Další informace naleznete v tématu [projekty konzoly](../debugger/debugging-preparation-console-projects.md).

## <a name="build-a-release-version-of-the-app"></a><a name="BKMK_BuildRelease"></a> Sestavení verze pro vydání aplikace
 Nyní poté, co jste ověřili, že vše funguje, jak má, lze připravit sestavení pro vydání aplikace.

#### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Vyčištění souborů řešení a sestavení verze pro vydání

1. V řádku nabídek odstraňte mezilehlé soubory a výstupní soubory, které byly vytvořeny během předchozích sestavení.

    ![Příkaz vyčistit řešení v nabídce sestavení](../ide/media/exploreide-cleansolution.png "ExploreIDE-CleanSolution")

2. Změňte konfiguraci sestavení pro GreetingsConsoleApp z **ladění** na **verzi**.

    ![Sestavení verze pro vydání aplikace](../ide/media/c-ide-changingbuildtorelease.png "IDE_ChangingBuildtoRelease c++")

3. Sestavte řešení.

    ![Příkaz Sestavit řešení v nabídce sestavení](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")

   Blahopřejeme k dokončení tohoto návodu! Pokud chcete prozkoumat další příklady, přečtěte si téma [ukázky sady Visual Studio](../ide/visual-studio-samples.md).

## <a name="see-also"></a>Viz také
 [Návod: vytvoření jednoduchých](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md) [tipů pro produktivitu](../ide/productivity-tips-for-visual-studio.md) aplikace [Visual Studio ukázky](../ide/visual-studio-samples.md) [Začínáme se sadou Visual Studio](../ide/get-started-developing-with-visual-studio.md)
