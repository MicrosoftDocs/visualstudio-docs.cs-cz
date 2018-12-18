---
title: Začínáme s C++
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 99c73344-86ba-4b08-9e15-f6111cc04185
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7e982db6bf37caf201f75e563a23a28a528a61e7
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052381"
---
# <a name="getting-started-with-c-in-visual-studio"></a>Začínáme s C++ v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto návodu se seznámíte s mnoha nástrojů a dialogových oknech, které můžete použít při vývoji aplikací pomocí sady Visual Studio. Vytvoříte jednoduché "Hello, World"-aplikaci ve stylu přitom získáte zkušenosti s prací v integrovaném vývojovém prostředí (IDE).

 Toto téma obsahuje následující oddíly:

 [Přihlaste se k sadě Visual Studio](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_Configure)

 [Vytvoření jednoduché aplikace](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_CreateApp)

 [Přidejte kód do aplikace](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_AddCode)

 [Ladění a testování aplikace](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_DebugTest)

 [Sestavení verze pro vydání aplikace](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_BuildRelease)

##  <a name="BKMK_Configure"></a> Přihlaste se k sadě Visual Studio
 Při prvním spuštění aplikace Visual Studio, budete mít možnost se přihlásit pomocí účtu Microsoft, jako je Live nebo Outlook. Přihlašování umožňuje nastavení synchronizovat napříč všemi zařízeními. Další informace najdete v tématu [přihlášení k sadě Visual Studio](../ide/signing-in-to-visual-studio.md)

 Obrázek 1: Visual Studio IDE

 ![Integrované vývojové prostředí s Visual C&#43; &#43; nastavení použijí](../ide/media/c-ide-defaultenvironmentlayout.png "IDE_DefaultEnvironmentLayout C ++")

 Po otevření sady Visual Studio se zobrazí tři základní části rozhraní IDE: nástroj oken, nabídek a panelů nástrojů a prostor hlavního okna. Okna nástrojů jsou ukotveny na levé a pravé straně okna aplikace s **Snadné spuštění**, nabídek a běžný panel nástrojů v horní části. Obsahuje střední části okna aplikace **úvodní stránka**. Při otevření řešení nebo projektu, na tomto místě zobrazí editory a návrháře. Při vývoji aplikace strávíte nejvíce času v této centrální oblasti.

##  <a name="BKMK_CreateApp"></a> Vytvoření jednoduché aplikace
 Když vytvoříte aplikaci v sadě Visual Studio, nejprve vytvoříte projekt a řešení. V tomto příkladu vytvoříte konzolovou aplikaci Windows.

#### <a name="to-create-a-console-app"></a>K vytvoření konzolové aplikace

1. V panelu nabídky zvolte **souboru**, **nový**, **projektu**.

    ![Na panelu nabídek zvolte soubor, nový, projekt](../ide/media/exploreide-filenewproject.png "ExploreIDE FileNewProject")

2. V **Visual C++** kategorie, zvolte **Konzolová aplikace Win32** šablony a poté pojmenujte projekt `GreetingsConsoleApp`.

    ![Šablona aplikace konzoly Win32](../ide/media/c-ide-newprojectdlg.png "IDE_NewProjectDlg C ++")

3. Když se objeví v nástroji Průvodce aplikace Win32, klikněte **Dokončit** tlačítko.

    ![Průvodce aplikace konzoly Win32](../ide/media/c-ide-win32consoleappwizard.png "IDE_Win32ConsoleAppWizard C ++")

   GreetingsConsoleApp projektu a řešení, se základní soubory pro aplikace konzoly Win32, jsou vytvořeny a automaticky načtena do **Průzkumníka řešení**. GreetingsConsoleApp.cpp soubor je otevřen v editoru kódu. Následující položky se zobrazí v **Průzkumníka řešení**:

   Obrázek 4: Položky projektu

   ![Soubory řešení v Průzkumníku řešení](../ide/media/c-ide-solutioncontents.png "IDE_SolutionContents C ++")

##  <a name="BKMK_AddCode"></a> Přidejte kód do aplikace
 V dalším kroku přidáte kód, zobrazují slovo "Hello" v okně konzoly.

#### <a name="to-display-hello-in-the-console-window"></a>Chcete-li zobrazit "Hello" v okně konzoly

1.  V souboru GreetingsConsoleApp.cpp zadejte prázdný řádek před řádkem `return 0;` a potom zadejte následující kód:

    ```
    cout << "Hello\n";
    ```

     V části se zobrazí červená vlnovka čára `cout`. Pokud jste na něj Odkažte se zobrazí chybová zpráva.

     ![Text chyby pro cout](../ide/media/c-ide-couterror.png "IDE_CoutError C ++")

     Chybová zpráva se zobrazí také v **seznam chyb** okna. Okno, můžete zobrazit na panelu nabídek, výběrem **zobrazení**, **seznam chyb**.

     [cout](http://msdn.microsoft.com/library/d87db6c3-e4e1-4d09-9ec5-458f55018257) je součástí \<iostream\> hlavičkový soubor.

2.  Pokud chcete zahrnout do hlavičky iostream, zadejte následující kód za `#include "stdafx.h"`:

    ```
    #include \<iostream\>
    using namespace std;
    ```

     Jste si pravděpodobně všimli, že se zobrazil pole jako jste zadali kód, poskytuje návrhy pro znaky, které jste zadali. Toto pole je součástí technologie IntelliSense jazyka C++, který poskytuje kódovací výzvy, včetně seznamu členů třídy nebo rozhraní a informace o parametru. Můžete také použít fragmenty kódu, které jsou předem definovaných bloky kódu. Další informace najdete v tématu [pomocí technologie IntelliSense](../ide/using-intellisense.md) a [fragmenty kódu](../ide/code-snippets.md).

     Červená vlnovka čára pod `cout` po odstranění chyby zmizí.

3.  Uložte změny do souboru.

     ![Kód, který opraví chyby cout](../ide/media/c-ide-coutfix.png "IDE_CoutFix C ++")

##  <a name="BKMK_DebugTest"></a> Ladění a testování aplikace
 Můžete ladit GreetingsConsoleApp chcete zobrazit, zda slovo "Hello" se zobrazí v okně konzoly.

#### <a name="to-debug-the-application"></a>Chcete-li ladit aplikaci

-   Spuštění ladicího programu.

     ![Spuštění ladění příkaz v nabídce ladění](../ide/media/exploreide-startdebugging.png "ExploreIDE StartDebugging")

     Ladicí program se spustí a spouští kód. Okno konzoly (samostatném okně, která vypadá jako příkazového řádku) se zobrazí na několik sekund, ale rychle zavře, když ladicí program se zastaví. Chcete-li zobrazit text, musíte nastavit zarážku pro zastavení provádění programu.

#### <a name="to-add-a-breakpoint"></a>Chcete-li přidat zarážku

1. Přidáte zarážku z panelu nabídky na řádku `return 0;`. Můžete také stačí kliknout na levém okraji nastavit zarážku.

    ![Přepnout zarážku – příkaz v nabídce ladění](../ide/media/exploreide-togglebreakpoint.png "ExploreIDE togglebreakpoint –")

    Na levém okraji okna editoru se vedle řádku kódu zobrazí červený kruh.

2. Stisknutím klávesy F5 spusťte ladění.

    Spustí ladicí program a zobrazí se okno konzoly, zobrazují slovo **Hello**.

    ![Text v okně příkazového řádku Windows Hello](../ide/media/c-ide-hellocommandwindow.png "IDE_HelloCommandWindow C ++")

3. Stiskněte SHIFT + F5, můžete zastavit ladění.

   Další informace najdete v tématu [projekty konzoly](../debugger/debugging-preparation-console-projects.md).

##  <a name="BKMK_BuildRelease"></a> Sestavení verze pro vydání aplikace
 Nyní poté, co jste ověřili, že vše funguje, jak má, lze připravit sestavení pro vydání aplikace.

#### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Vyčištění souborů řešení a sestavení verze pro vydání

1. Na panelu nabídek odstranění pomocných a výstupních souborů, které byly během předchozích sestavení vytvořeny.

    ![Příkaz Vyčistit řešení v nabídce sestavení](../ide/media/exploreide-cleansolution.png "ExploreIDE CleanSolution")

2. Změňte konfiguraci buildu pro GreetingsConsoleApp z **ladění** k **vydání**.

    ![Sestavení verze pro vydání aplikace](../ide/media/c-ide-changingbuildtorelease.png "IDE_ChangingBuildtoRelease C ++")

3. Sestavte řešení.

    ![Sestavit řešení – příkaz v nabídce sestavení](../ide/media/exploreide-buildsolution.png "ExploreIDE BuildSolution")

   Blahopřejeme k dokončení tohoto návodu! Pokud budete chtít projít Další příklady, přečtěte si téma [ukázky sady Visual Studio](../ide/visual-studio-samples.md).

## <a name="see-also"></a>Viz také
 [Návod: Vytvoření jednoduché aplikace](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md) [tipy pro vyšší produktivitu](../ide/productivity-tips-for-visual-studio.md) [Visual Studio – ukázky](../ide/visual-studio-samples.md) [začít s vývojem pomocí sady Visual Studio](../ide/get-started-developing-with-visual-studio.md)
