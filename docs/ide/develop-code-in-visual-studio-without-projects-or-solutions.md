---
title: Vývoj kódu bez projektů nebo řešení
ms.date: 06/22/2020
ms.topic: how-to
helpviewer_keywords:
- open folder [Visual Studio]
- anycode [Visual Studio]
- projects and solutions, develop code without
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68665acfcc3ea00f118dc19cf155cb3e6f5d1b36
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85769655"
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>Vývoj kódu v sadě Visual Studio bez projektů nebo řešení

Můžete otevřít kód prakticky z jakéhokoli typu projektu založeného na adresáři do sady Visual Studio, aniž by bylo nutné pro řešení nebo soubor projektu. To znamená, že můžete například klonovat úložiště na GitHubu, otevřít ho přímo do sady Visual Studio a začít vyvíjet, aniž byste museli vytvářet řešení nebo projekt. V případě potřeby můžete zadat vlastní úkoly sestavení a spustit parametry pomocí jednoduchých souborů JSON.

Po otevření souborů kódu v aplikaci Visual Studio **Průzkumník řešení** zobrazí všechny soubory ve složce. Můžete kliknout na libovolný soubor a začít ho upravovat. Na pozadí spustí Visual Studio indexování souborů, aby bylo možné povolit funkce IntelliSense, navigace a refaktoringu. Při úpravách, vytváření, přesouvání nebo odstraňování souborů aplikace Visual Studio automaticky sleduje změny a průběžně aktualizuje její index IntelliSense. Kód se zobrazí se zabarvení syntaxe a v mnoha případech zahrnuje základní dokončování příkazů IntelliSense.

## <a name="open-any-code"></a>Otevřít libovolný kód

Kód můžete otevřít do sady Visual Studio následujícími způsoby:

- V panelu nabídek sady Visual Studio zvolte **soubor**  >  **otevřít**  >  **složku**a pak přejděte do umístění kódu.

- V nabídce kontextu (klikněte pravým tlačítkem myši) složky obsahující kód vyberte příkaz **otevřít v aplikaci Visual Studio** .

::: moniker range="vs-2017"
- Klikněte na odkaz **Otevřít složku** na **úvodní stránce**sady Visual Studio.

    > [!IMPORTANT]
    > Ne všechny kódy lze otevřít pomocí odkazu **Otevřít složku** na **úvodní stránce**sady Visual Studio. Například pokud byl soubor kódu uložen jako součást řešení &mdash; jinými slovy, v souboru. sln je &mdash; nutné použít jednu z dalších možností, které jsou zde uvedeny, pro otevření kódu.

::: moniker-end

::: moniker range=">=vs-2019"
- V okně Start klikněte na odkaz **Otevřít složku** .

    > [!IMPORTANT]
    > Ne všechny kódy lze otevřít pomocí odkazu **Otevřít složku** z okna Start sady Visual Studio. Například pokud byl soubor kódu uložen jako součást řešení &mdash; jinými slovy, v souboru. sln je &mdash; nutné použít jednu z dalších možností, které jsou zde uvedeny, pro otevření kódu.

::: moniker-end

- Pokud jste uživatel s klávesnicí, stiskněte **kombinaci kláves CTRL** + **SHIFT** + **ALT** + **O** v aplikaci Visual Studio.

- Otevřete kód z klonovaného úložiště GitHub.

### <a name="to-open-code-from-a-cloned-github-repo"></a>Otevření kódu z klonovaného úložiště GitHub

Následující příklad ukazuje, jak klonovat úložiště GitHub a pak otevřít jeho kód v aplikaci Visual Studio. Pokud chcete postupovat podle tohoto postupu, musíte mít v systému nainstalovaný účet GitHub a Git pro Windows. Další informace najdete v tématu [Registrace nového účtu GitHubu](https://help.github.com/articles/signing-up-for-a-new-github-account/) a [Gitu pro Windows](https://git-for-windows.github.io/) .

1. Přejít do úložiště, které chcete klonovat na GitHubu.

1. Zvolte tlačítko **klonovat nebo stáhnout** a pak v rozevírací nabídce vyberte tlačítko **Kopírovat do schránky** a zkopírujte tak zabezpečenou adresu URL pro úložiště GitHub.

   ![Tlačítko klonování GitHubu](./media/VSIDE_Code_Clone.png)

1. V aplikaci Visual Studio vyberte kartu **Team Explorer** a otevřete **Team Explorer**. Pokud kartu nevidíte, otevřete ji ze **zobrazení**  >  **Team Explorer**.

1. V Team Explorer v části **místní úložiště Git** zvolte příkaz **klonování** a vložte do textového pole adresu URL stránky GitHubu.

   ![Klonování projektu](./media/VSIDE_Code_Clone2.png)

1. Klikněte na tlačítko **klonovat** a naklonujte soubory projektu do místního úložiště Git. V závislosti na velikosti úložiště může tento proces trvat několik minut.

1. Po naklonování úložiště do svého systému v **Team Explorer**vyberte v nabídce kontextu (klikněte pravým tlačítkem myši) v nově klonovaném úložišti příkaz **otevřít** .

   ![Klonované úložiště](./media/VSIDE_Code_Clone3.png)

1. Kliknutím na příkaz **Zobrazit složku** zobrazíte soubory v **Průzkumník řešení**.

   ![Zobrazit zobrazení složky](./media/VSIDE_Code_Clone3_show.png)

   Nyní můžete procházet složky a soubory v klonovaném úložišti a zobrazit a vyhledat kód v editoru kódu sady Visual Studio, dokončit se zabarvení syntaxe a další funkce.

## <a name="run-and-debug-your-code"></a>Spuštění a ladění kódu

Svůj kód můžete ladit v aplikaci Visual Studio bez projektu nebo řešení. Chcete-li ladit některé jazyky, možná budete muset zadat platný *spouštěcí soubor* v základu kódu, jako je například skript, spustitelný soubor nebo projekt. Rozevírací seznam vedle tlačítka **Start** na panelu nástrojů uvádí všechny položky po spuštění, které Visual Studio detekuje, a také položky, které výslovně určíte. Visual Studio spustí tento kód jako první při ladění kódu.

Konfigurace kódu pro běh v aplikaci Visual Studio se liší v závislosti na tom, jaký druh kódu je a jaké jsou nástroje sestavení.

### <a name="codebases-that-use-msbuild"></a>Základy použití nástroje MSBuild

Základy kódu založené na MSBuildu můžou mít více konfigurací sestavení, které se zobrazují v rozevíracím seznamu tlačítka **Start** . Vyberte soubor, který chcete použít jako položku po spuštění, a pak kliknutím na tlačítko **Start** spusťte ladění.

> [!NOTE]
> U základů kódu pro C# a Visual Basic musíte mít nainstalovanou úlohu **vývoj desktopových** aplikací pro .NET. V případě základů kódu C++ musíte mít nainstalovanou úlohu **vývoj desktopových aplikací pomocí C++** .

### <a name="codebases-that-use-custom-build-tools"></a>Základy kódu, které používají vlastní nástroje sestavení

Pokud váš základ kódu používá vlastní nástroje sestavení, je nutné sdělit aplikaci Visual Studio, jak sestavit kód pomocí *úloh sestavení* , které jsou definovány v souboru *. JSON* . Další informace najdete v tématu [přizpůsobení úloh sestavení a ladění](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

### <a name="codebases-that-contain-python-or-javascript-code"></a>Základ kódu, který obsahuje kód Python nebo JavaScript

Pokud váš základ kódu obsahuje kód Python nebo JavaScript, nemusíte konfigurovat žádné soubory *. JSON* , ale musíte nainstalovat odpovídající úlohu. Také je nutné nakonfigurovat spouštěcí skript:

1. Pomocí **nástrojů** [Python development](https://visualstudio.microsoft.com/vs/python/) [Node.js development](https://visualstudio.microsoft.com/vs/node-js/)  >  **získat nástroje a funkce**nebo zavřením sady Visual Studio a spuštěním instalační program pro Visual Studio nainstalujte úlohu vývoj pro vývojNode.js nebo Python.

   ![Úlohy vývoje Node.js a Pythonu](media/python_nodejs_workloads.png)

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši nebo v místní nabídce souboru JavaScriptu nebo Pythonu na příkaz **nastavit jako položku při spuštění** .

1. Spusťte ladění kliknutím na tlačítko **Start** .

### <a name="codebases-that-contain-c-code"></a>Základy kódu, které obsahují kód jazyka C++

Informace o otevření kódu C++ bez řešení nebo projektů v aplikaci Visual Studio naleznete v tématu [Otevřít složku projekty pro jazyk C++](/cpp/build/open-folder-projects-cpp).

### <a name="codebases-that-contain-a-visual-studio-project"></a>Základy kódu, které obsahují projekt sady Visual Studio

Pokud složka kódu obsahuje projekt sady Visual Studio, můžete projekt označit jako položku po spuštění.

![Nastavit projekt jako položku při spuštění](media/customize-set-project-as-startup-item.png)

Text tlačítka **Start** se změní tak, aby odrážel, že projekt je položka po spuštění.

![Tlačítko projekt na začátku](media/customize-start-button-project.png)

## <a name="see-also"></a>Viz také

- [Přizpůsobení úloh sestavení a ladění](../ide/customize-build-and-debug-tasks-in-visual-studio.md)
- [Projekty Otevřít složku pro C++](/cpp/build/open-folder-projects-cpp)
- [Projekty CMake v jazyce C++](/cpp/build/cmake-projects-in-visual-studio)
- [Psaní kódu v editoru kódu a textovém editoru](../ide/writing-code-in-the-code-and-text-editor.md)
