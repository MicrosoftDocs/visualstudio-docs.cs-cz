---
title: Začínáme s C++
description: ''
ms.custom: mvc
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
author: corob-msft
ms.author: corob
manager: douge
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: 406b3c24cf3c46b694afc8ab24c0ddca11b434ee
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159994"
---
# <a name="get-started-with-c-in-visual-studio"></a>Začínáme s C++ v sadě Visual Studio

Dokončete tento quickstart se seznámit s mnoha nástrojů a dialogových oken, které lze použít při vývoji aplikací v jazyce C++ v sadě Visual Studio. Vytvořit "Hello, World"-styl aplikace konzoly, zatímco další informace o práci v integrovaném vývojovém prostředí (IDE).

## <a name="prerequisites"></a>Požadavky

Nemusíte znát C++ Chcete-li dokončit tento quickstart, ale měli byste se seznámit s některé obecné programování a ladění koncepty. V dokumentaci sady Visual Studio nebude vás naučí, jak programovat v jazyce C++. Je dobré vodítko k C++ studijních materiálů [začít](https://isocpp.org/get-started) stránku na webu ISO C++.

Sledovat, potřebujete kopii Visual Studio 2017 verze 15.3 nebo novější s **vývoj pro klientské počítače s C++** instalaci pracovního vytížení. Rychlý průvodce instalací, naleznete v [podpory instalace jazyka C++ v sadě Visual Studio](/cpp/build/vscpp-step-0-installation).

## <a name="create-a-console-app"></a>Vytvoření aplikace konzoly

Pokud ještě není spuštěna, spusťte aplikaci Visual Studio.

![Rozhraní IDE s Visual C&#43; &#43; nastavení](../ide/media/get-started-cpp-ide-layout.png)

Po otevření sady Visual Studio se zobrazí tři základní části rozhraní IDE: nástroj oken, nabídek a panelů nástrojů a prostor hlavního okna. Nástroje systému windows jsou ukotveny na levé a pravé straně okna aplikace. **Snadné spuštění** pole, panelu nabídek a panelu nástrojů Standardní se nachází v horní. Obsahuje středu okna **úvodní stránku**. Při otevření řešení nebo projektu, na tomto místě zobrazí editory a návrháře. Když vyvíjíte aplikaci, je strávil většinu času v této centrální oblasti.

Visual Studio používá *projekty* organizaci kódu pro aplikace, a *řešení* k uspořádání vašich projektů. Projekt obsahuje všechny možnosti, konfigurace a pravidla používaná k vytváření aplikací. Spravuje také vztah mezi všechny projektové soubory a soubory s externí. K vytvoření vaší aplikace, nejprve je třeba vytvořit nový projekt a řešení.

### <a name="to-create-a-console-app-project"></a>Vytvoření projektu aplikace konzoly

1. V řádku nabídek zvolte **soubor > Nový > projekt** otevřete **nový projekt** dialogové okno.

   ![V řádku nabídek zvolte Soubor > Nový > Projekt](../ide/media/get-started-cpp-file-new-project-menu.png)

1. V **nový projekt** dialogové okno, vyberte **nainstalované > Visual C++** Pokud není již vybrána. V prostředním podokně vyberte **aplikaci konzoly systému Windows** šablony. V **název** textové pole, zadejte *HelloApp*.

   ![Vytvoření projektu aplikace pomocí dialogového okna Nový projekt](../ide/media/get-started-cpp-new-project-dialog.png)

   Dialogové okno aplikace může mít různé možnosti v závislosti na zatížení Visual Studio a součásti, které jste nainstalovali. Pokud nevidíte šablony projektu Visual C++, je třeba znovu spustit instalační program Visual Studio a nainstalujte **vývoj pro klientské počítače s C++** pracovního vytížení. Lze provést přímo **nový projekt** dialogové okno. Chcete-li spustit instalační program, zvolte **otevřít instalační program Visual Studio** odkaz v dialogovém okně.

1. Zvolte **OK** tlačítko, chcete-li vytvořit projekt aplikace a řešení.

   HelloApp projektu a řešení s základní soubory pro aplikace konzoly systému Windows, vytvoření a automaticky načteny do **Průzkumník řešení**. *HelloApp.cpp* soubor je otevřen v editoru kódu. Tyto položky se zobrazí v **Průzkumník řešení**:

   ![Soubory pro řešení v Průzkumníku řešení](../ide/media/get-started-cpp-solution-explorer.png)

## <a name="add-code-to-the-app"></a>Přidejte kód do aplikace

Dále přidáte kód, který zobrazí slovo "Ahoj" v okně konzoly.

### <a name="to-edit-code-in-the-editor"></a>Chcete-li upravit kód v editoru

1. V *HelloApp.cpp* soubor, zadejte prázdného řádku před řádek `return 0;` a zadejte tento kód:

   ```cpp
   cout << "Hello\n";
   ```

   V části se zobrazí červená vlnovka čára `cout`. Pokud ukazatel myši, zobrazí se chybová zpráva.

   ![Text chybové zprávy pro cour](../ide/media/get-started-cpp-intellisense-error.png)

   Chybová zpráva se zobrazí také v **seznam chyb** okna. Toto okno můžete zobrazit výběrem **zobrazení > Seznam chyb** v panelu nabídek.

   ![Chyby v okně Seznam chyb](../ide/media/get-started-cpp-error-list.png)

   Chybí kód deklarace pro [std::cout](/cpp/standard-library/iostream), který se vyskytuje v  *\<iostream >* soubor hlaviček.

1. Chcete-li zahrnout *iostream* záhlaví, zadejte tento kód po `#include "stdafx.h"`:

   ```cpp
   #include <iostream>
   using namespace std;
   ```

   Pravděpodobně jste zaznamenali, že se nezobrazují pole při zadávání kódu. Toto pole obsahuje návrhy automatického dokončení pro znaky, které zadáte. To je součástí C++ IntelliSense, který poskytuje kódování výzvy, včetně členů třídy nebo rozhraní a informace o parametru. Můžete také použít fragmenty kódu, které jsou předem definovaných bloky kódu. Další informace naleznete v tématu [pomocí technologie IntelliSense](../ide/using-intellisense.md) a [výstřižky kódu](../ide/code-snippets.md).

   ![Dlouhodobého kódu v editoru](../ide/media/get-started-cpp-cout-fix.png)

   Červená vlnovka čára pod `cout` po odstranění chyby zmizí.

1. Chcete-li uložit změny do souboru, stiskněte **kláves Ctrl + S**.

## <a name="build-the-app"></a>Sestavení aplikace

Je snadné sestavení vašeho kódu. V řádku nabídek zvolte **sestavení > Sestavit řešení**. Visual Studio vytvoří řešení HelloApp a zprávy o pokroku v **výstupní** okna.

   ![Sestavte řešení HelloApp](../ide/media/get-started-cpp-build-solution.gif)

## <a name="debug-and-test-the-app"></a>Ladění a testování aplikace

Můžete ladit HelloApp Chcete-li zjistit, zda se zobrazí slovo "Ahoj" v okně konzoly.

### <a name="to-debug-the-app"></a>Chcete-li ladit aplikace

Chcete-li spustit ladicí program, zvolte **ladění > Spustit ladění** v panelu nabídek.

![V nabídce ladění spustit ladění – příkaz](../ide/media/get-started-cpp-start-debugging-menu.png)

Ladicí program se spustí a spouští kód. Okno konzoly (samostatném okně, která vypadá jako příkazového řádku) se zobrazí na několik sekund, ale rychle zavře, když ladicí program se zastaví. Chcete-li zobrazit text, musíte nastavit zarážku pro zastavení provádění programu.

### <a name="to-add-a-breakpoint"></a>Chcete-li přidat zarážku

1. V editoru, umístěte kurzor v řádku `return 0;`. V řádku nabídek zvolte **ladění > Přepnout zarážku**. Můžete také klepnout do levého okraje pro nastavení zarážky.

     ![Přepnout zarážku – příkaz v nabídce ladění](../ide/media/get-started-cpp-toggle-breakpoint-menu.png)

     Na levém okraji okna editoru se vedle řádku kódu zobrazí červený kruh.

     ![Podle okrajů okna zarážky](../ide/media/get-started-cpp-breakpoint-set.png)

1. Chcete-li spustit ladění, stiskněte **F5**.

   Spustí ladicí program a zobrazí se okno konzoly, zobrazují slovo **Hello**.

   ![Ahoj textu v okně konzoly](../ide/media/get-started-cpp-helloapp-window.png)

1. Chcete-li zastavit ladění, stiskněte **Shift + F5**.

Další informace o ladění projektu konzoly naleznete v tématu [konzoly projekty](../debugger/debugging-preparation-console-projects.md).

## <a name="build-a-release-version-of-the-app"></a>Sestavení verze pro vydání aplikace

Teď, když jste ověřili, že vše funguje, si můžete připravit sestavení pro vydání aplikace. Vydaná sestavení dovolené, informace o ladění a použití možnosti optimalizace kompilátor vytvořit menší, rychlejší kód.

### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Vyčištění souborů řešení a sestavení verze pro vydání

1. V řádku nabídek zvolte **sestavit > Vyčistit řešení** odstranění mezilehlé soubory a výstupní soubory, které byly vytvořeny během předchozí sestavení.

   ![Příkaz Vyčistit řešení v nabídce sestavení](../ide/media/get-started-cpp-clean-solution-menu.png)

1. Změňte konfiguraci řešení pro HelloApp z **ladění** k **verze**, v panelu nástrojů vyberte na ovládacím prvku konfigurace řešení rozevíracího seznamu a pak zvolte **verze**.

   ![Sestavení verze pro vydání aplikace](../ide/media/get-started-cpp-set-release-configuration.png)

1. Sestavte řešení. V řádku nabídek zvolte **sestavení > Sestavit řešení**.

Po dokončení toto sestavení vytvořené aplikace, který můžete zkopírovat a spustit v jakémkoli okně příkazového řádku. Jej nemusí provést, ale je brána do větší věci.

Blahopřejeme k dokončení tohoto rychlého startu!

## <a name="see-also"></a>Viz také:

- [Pomocí integrovaného vývojového prostředí sady Visual Studio pro vývoj pro klientské počítače C++](/cpp/ide/using-the-visual-studio-ide-for-cpp-desktop-development)
- [Návod: Vytvoření jednoduché aplikace s C# nebo Visual Basic](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)
- [Tipy pro vyšší produktivitu sady Visual Studio](../ide/productivity-tips-for-visual-studio.md)
