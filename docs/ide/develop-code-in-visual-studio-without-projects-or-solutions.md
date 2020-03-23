---
title: Vývoj kódu bez projektů nebo řešení
ms.date: 02/21/2018
ms.topic: conceptual
helpviewer_keywords:
- open folder [Visual Studio]
- anycode [Visual Studio]
- projects and solutions, develop code without
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7a9459868d569a7466dccf92e4b548c0500bf80
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596291"
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>Vývoj kódu v sadě Visual Studio bez projektů nebo řešení

Můžete otevřít kód z téměř libovolného typu projektu založeného na adresáři do sady Visual Studio bez nutnosti řešení nebo souboru projektu. To znamená, že můžete například klonovat úložiště na GitHubu, otevřít ho přímo do sady Visual Studio a začít vyvíjet, aniž byste museli vytvářet řešení nebo projekt. V případě potřeby můžete zadat vlastní úlohy sestavení a parametry spuštění prostřednictvím jednoduchých souborů JSON.

Po otevření souborů kódu v sadě Visual Studio **průzkumník řešení** zobrazí všechny soubory ve složce. Můžete kliknout na libovolný soubor a začít jej upravovat. Na pozadí visual studio spustí indexování souborů, aby povolilo funkce Technologie IntelliSense, navigace a refaktoringu. Při úpravách, vytváření, přesouvání nebo odstraňování souborů aplikace Visual Studio automaticky sleduje změny a průběžně aktualizuje svůj index Technologie IntelliSense. Kód se zobrazí s vybarvení syntaxe a v mnoha případech zahrnout základní intelliSense prohlášení dokončení.

## <a name="open-any-code"></a>Otevřít libovolný kód

Kód do sady Visual Studio můžete otevřít libovolným z následujících způsobů:

- Na panelu nabídek Sady Visual Studio zvolte Složka > **otevření** > **Folder** **souboru**a pak přejděte na umístění kódu.

- V kontextové nabídce (po klepnutí pravým tlačítkem myši) složky obsahující kód zvolte příkaz **Otevřít v sadě Visual Studio.**

::: moniker range="vs-2017"
- Zvolte odkaz **Otevřít složku** na **úvodní stránce**sady Visual Studio .
::: moniker-end

::: moniker range=">=vs-2019"
- V úvodním okně zvolte odkaz **Otevřít složku.**
::: moniker-end

- Pokud jste uživatel klávesnice, stiskněte v sadě Visual Studio **kombinaci kláves Ctrl**+**Shift**+**Alt**+**O.**

- Otevřete kód z klonovaného úložiště GitHub.

### <a name="to-open-code-from-a-cloned-github-repo"></a>Otevření kódu z klonovaného úložiště GitHub

Následující příklad ukazuje, jak klonovat úložiště GitHub a pak otevřít jeho kód v sadě Visual Studio. Chcete-li postupovat podle tohoto postupu, musíte mít v systému nainstalovaný účet GitHub a Git pro Windows. Další informace najdete [v tématu Registrace nového účtu GitHub](https://help.github.com/articles/signing-up-for-a-new-github-account/) a [Git u Windows.](https://git-for-windows.github.io/)

1. Přejděte do úložiště, které chcete naklonovat na GitHubu.

1. Zvolte tlačítko **Klonovat nebo Stáhnout** a pak v rozevírací nabídce zvolte tlačítko **Kopírovat do schránky,** chcete-li zkopírovat zabezpečenou adresu URL úložiště GitHub.

   ![Tlačítko klonování GitHubu](./media/VSIDE_Code_Clone.png)

1. V Sadě Visual Studio zvolte kartu **Průzkumník týmu** a otevřete **Průzkumníka týmu**. Pokud kartu nevidíte, otevřete ji v **Aplikaci View** > **Team Explorer**.

1. V Průzkumníkovi týmu vyberte v části **Místní úložiště Git** příkaz **Clone** a pak do textového pole vložte adresu URL stránky GitHub.

   ![Klonovat projekt](./media/VSIDE_Code_Clone2.png)

1. Zvolte tlačítko **Klonování,** chcete-li klonovat soubory projektu do místního úložiště Git. V závislosti na velikosti repo může tento proces trvat několik minut.

1. Po naklonování repo do vašeho systému zvolte v **Průzkumníkovi týmu**příkaz **Otevřít** v kontextové nabídce (po kliknutí pravým tlačítkem myši) nově klonovaného repo.

   ![Klonované repo](./media/VSIDE_Code_Clone3.png)

1. Chcete-li soubory zobrazit v **Průzkumníku řešení**, zvolte příkaz **Zobrazit zobrazení složky** .

   ![Zobrazit zobrazení složky](./media/VSIDE_Code_Clone3_show.png)

   Nyní můžete procházet složky a soubory v klonovaném repo a prohlížet a prohledávat kód v editoru kódu sady Visual Studio, doplněný o vybarvení syntaxe a další funkce.

## <a name="run-and-debug-your-code"></a>Spuštění a ladění kódu

Můžete ladit kód v sadě Visual Studio bez projektu nebo řešení! Chcete-li ladit některé jazyky, bude pravděpodobně nutné zadat platný *spouštěcí soubor* v základu kódu, například skript, spustitelný soubor nebo projekt. V rozevíracím seznamu vedle tlačítka **Start** na panelu nástrojů jsou uvedeny všechny položky po spuštění, které aplikace Visual Studio zjistí, a také položky, které určíte. Visual Studio spustí tento kód jako první při ladění kódu.

Konfigurace kódu pro spuštění v sadě Visual Studio se liší v závislosti na tom, jaký druh kódu je a jaké jsou nástroje sestavení.

### <a name="codebases-that-use-msbuild"></a>Základy kódu, které používají MSBuild

Základy kódu založené na msbuildu mohou mít více konfigurací sestavení, které se zobrazí v rozevíracím seznamu tlačítka **Start.** Vyberte soubor, který chcete použít jako položku po spuštění, a pak zvolte tlačítko **Start** a začněte ladění.

> [!NOTE]
> Pro c# a Visual Basic codebases musíte mít nainstalovanou pracovní zátěž pro vývoj pracovních prostředí **.NET.** Pro základy kódu jazyka C++ musíte mít nainstalovaný vývoj plochy s úlohami **Jazyka C++.**

### <a name="codebases-that-use-custom-build-tools"></a>Základy kódu, které používají vlastní nástroje sestavení

Pokud váš základ kódu používá vlastní nástroje sestavení, musíte aplikaci Visual Studio sdělit, jak vytvořit kód pomocí *úloh sestavení,* které jsou definovány v souboru *JSON.* Další informace naleznete v [tématu Customize build and debug tasks](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

### <a name="codebases-that-contain-python-or-javascript-code"></a>Základy kódu, které obsahují kód Pythonu nebo JavaScriptu

Pokud váš kódovací systém obsahuje kód Pythonu nebo JavaScriptu, není nutné konfigurovat žádné *soubory JSON,* ale musíte nainstalovat odpovídající úlohu. Je také nutné nakonfigurovat spouštěcí skript:

1. Nainstalujte [úlohu vývoje Node.js](https://visualstudio.microsoft.com/vs/node-js/) nebo [Pythonu](https://visualstudio.microsoft.com/vs/python/) výběrem **nástroje** > **získat nástroje a funkce**nebo zavřením sady Visual Studio a spuštěním Instalační služby sady Visual Studio.

   ![Vývojové úlohy Node.js a Pythonu](media/python_nodejs_workloads.png)

1. V **Průzkumníku řešení**zvolte v Průzkumníku řešení v nabídce javascriptu nebo pythonu v nabídce pravého tlačítka nebo kontextového příkazu Nastavit jako **položku po spuštění.**

1. Chcete-li zahájit ladění, zvolte tlačítko **Start.**

### <a name="codebases-that-contain-c-code"></a>Základy kódu, které obsahují kód jazyka C++

Informace o otevření kódu jazyka C++ bez řešení nebo projektů v sadě Visual Studio naleznete v [tématu Open Folder projects for C++](/cpp/build/open-folder-projects-cpp).

### <a name="codebases-that-contain-a-visual-studio-project"></a>Základy kódu, které obsahují projekt sady Visual Studio

Pokud složka kódu obsahuje projekt sady Visual Studio, můžete projekt označit jako položku po spuštění.

![Nastavit projekt jako položku po spuštění](media/customize-set-project-as-startup-item.png)

Text tlačítka **Start** se změní tak, aby odrážel, že projekt je položkou po spuštění.

![Tlačítko Projekt na začátku](media/customize-start-button-project.png)

## <a name="see-also"></a>Viz také

- [Přizpůsobení úloh sestavení a ladění](../ide/customize-build-and-debug-tasks-in-visual-studio.md)
- [Projekty Otevřít složku pro C++](/cpp/build/open-folder-projects-cpp)
- [CMake projekty v jazyce C++](/cpp/build/cmake-projects-in-visual-studio)
- [Psaní kódu v kódu a textovém editoru](../ide/writing-code-in-the-code-and-text-editor.md)
