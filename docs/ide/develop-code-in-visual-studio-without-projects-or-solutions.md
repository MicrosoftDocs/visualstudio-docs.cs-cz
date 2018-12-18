---
title: Vývoj kódu bez projektů nebo řešení
ms.date: 02/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- open folder [Visual Studio]
- anycode [Visual Studio]
- projects and solutions, develop code without
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5885fc8c62b8da4213446601f37700cc077eda8c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062361"
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>Vývoj kódu v sadě Visual Studio bez projektů nebo řešení

V sadě Visual Studio 2017 můžete otevřít kód z téměř libovolného typu projektu založeného na adresář do sady Visual Studio bez nutnosti soubor řešení nebo projektu. To znamená, že můžete, například naklonování úložiště na Githubu, otevřete ho přímo do sady Visual Studio a začít vyvíjet, bez nutnosti vytvářet řešení nebo projektu. V případě potřeby můžete zadat úkoly vlastního sestavení a spuštění parametry prostřednictvím jednoduché soubory JSON.

Po otevření souborů kódu v sadě Visual Studio **Průzkumníka řešení** zobrazí všechny soubory ve složce. Můžete kliknout na jakýkoli soubor můžete začít s jeho úpravami. Na pozadí spustí aplikace Visual Studio indexování soubory, které chcete povolit technologii IntelliSense, navigace a funkcí refaktoringu. Úpravy, vytváření, přesunout a odstranit soubory, Visual Studio automaticky sleduje změny a průběžně aktualizuje jeho index IntelliSense. Kód se zobrazí s barevné zvýrazňování syntaxe a v mnoha případech zahrnují základní doplňování technologie IntelliSense.

## <a name="open-any-code"></a>Otevřete libovolný kód

Kód do sady Visual Studio můžete otevřít v některém z následujících způsobů:

- Na řádku nabídek sady Visual Studio, zvolte **souboru** > **otevřít** > **složky**a pak přejděte do umístění v kódu.
- V nabídce kontextu (klikněte pravým tlačítkem) složce obsahující kód, zvolte **otevřít v sadě Visual Studio** příkazu.
- Zvolte **otevřít složku** odkaz v sadě Visual Studio **úvodní stránka**.
- Pokud jste uživatelem klávesnice, stiskněte **Ctrl**+**Shift**+**Alt**+**O** ve Vizuálu Studio.
- Otevření kódu z naklonovaného úložiště GitHub.

### <a name="to-open-code-from-a-cloned-github-repo"></a>Chcete-li spustit kód z naklonovaného úložiště GitHub

Následující příklad ukazuje, jak naklonujte úložiště GitHub a pak otevřete svůj kód v sadě Visual Studio. Chcete-li provést tento postup, musíte mít účet GitHub a Git pro Windows nainstalovaný ve vašem systému. Zobrazit [zaregistrovat nový účet GitHub](https://help.github.com/articles/signing-up-for-a-new-github-account/) a [Git pro Windows](https://git-for-windows.github.io/) Další informace.

1. Přejděte do úložiště, které chcete naklonovat na Githubu.

1. Zvolte **klonovat nebo stáhnout** tlačítko a klikněte na tlačítko **kopírování do schránky** tlačítko v rozevírací nabídce pro kopírování platnost zabezpečené adresy URL pro úložiště GitHub.

   ![Tlačítko clone Githubu](./media/VSIDE_Code_Clone.png)

1. V sadě Visual Studio, zvolte **Team Exploreru** karty otevřete **Team Exploreru**. Pokud nevidíte kartu, otevřete ho z **zobrazení** > **Team Exploreru**.

1. V Průzkumníku týmových projektů v části **místní úložiště Git** zvolte **klonování** příkaz a vložte adresu URL stránky Githubu do textového pole.

   ![Klonování projektu z](./media/VSIDE_Code_Clone2.png)

1. Zvolte **klonování** tlačítko naklonujte soubory projektu do místního úložiště Git. V závislosti na velikosti úložiště tento proces může trvat několik minut.

1. Po úložiště klonování k vašemu systému, v **Team Exploreru**, zvolte **otevřít** příkaz v nabídce kontextu (klikněte pravým tlačítkem) pro nově naklonované úložiště.

   ![Naklonované úložiště](./media/VSIDE_Code_Clone3.png)

1. Zvolte **zobrazit zobrazení složky** příkaz pro zobrazování souborů v **Průzkumníka řešení**.

   ![Ukázat zobrazení složky](./media/VSIDE_Code_Clone3_show.png)

   Teď můžete procházet složky a soubory do naklonovaného úložiště a zobrazit a vyhledat kód v editoru sady Visual Studio code, s barevné zvýrazňování syntaxe a další funkce.

| | |
|---------|---------|
| ![Ikona fotoaparátu videa pro videa](../install/media/video-icon.png)| [Podívejte se na video](https://mva.microsoft.com/en-us/training-courses/getting-started-with-visual-studio-2017-17798?l=lp3TOKD6D_6711787171) o tom, jak klonovat a otevřít kód z úložiště GitHub v sadě Visual Studio. |

## <a name="run-and-debug-your-code"></a>Spuštění a ladění kódu

Lze ladit kód v sadě Visual Studio bez projektů nebo řešení. Chcete-li ladit některé jazyky, budete muset zadat platné *spouštěcí soubor* v základu kódu, jako je například skript, spustitelný soubor nebo projektu. Pole rozevíracího seznamu vedle položky **Start** tlačítko na panelu nástrojů jsou uvedeny všechny položky po spuštění, které sada Visual Studio zjistí a také položky konkrétně určit. Visual Studio spustí tento kód nejprve při ladění vašeho kódu.

Konfigurace váš kód běžet v sadě Visual Studio se liší v závislosti na tom, jaký kód je a co jsou nástroje pro sestavení.

### <a name="codebases-that-use-msbuild"></a>Základů kódu, které používají nástroje MSBuild

Založené na MSBuild základů kódu může mít více konfigurací sestavení, které se zobrazují v **Start** tlačítka rozevíracího seznamu. Vyberte soubor, který chcete použít jako položku při spuštění a klikněte na tlačítko **Start** spusťte ladění.

> [!NOTE]
> Pro C# a základů kódu jazyka Visual Basic, musíte mít **vývoj desktopových aplikací .NET** nainstalovaná úloha. Pro základů kódu C++, musíte mít **vývoj desktopových aplikací pomocí C++** nainstalovaná úloha.

### <a name="codebases-that-use-custom-build-tools"></a>Základy kódu tohoto použití vlastních sestavovacích nástrojů

Pokud váš kód používá vlastní nástroje pro vytváření, pak je zapotřebí sdělit sady Visual Studio vytvoření kódu pomocí *úlohy sestavení* , která jsou definována v *.json* souboru. Další informace najdete v tématu [přizpůsobení sestavení a ladění úloh](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

### <a name="codebases-that-contain-python-or-javascript-code"></a>Základů kódu, které obsahují kód Python nebo JavaScript

Pokud vašeho základu kódu obsahuje kód Python nebo JavaScript, není nutné ke konfiguraci libovolné *.json* soubory, ale je nutné nainstalovat odpovídající úlohy. Také musíte nakonfigurovat spouštěcí skript:

1. Nainstalujte [vývoj v Node.js](https://visualstudio.microsoft.com/vs/node-js/) nebo [vývoj v jazyce Python](https://visualstudio.microsoft.com/vs/python/) úloh výběrem **nástroje** > **stažení nástrojů a funkcí**, nebo zavření sady Visual Studio a spuštěním instalačního programu sady Visual Studio.

   ![Úlohy související s vývojem Node.js a Pythonu](media/python_nodejs_workloads.png)

1. V **Průzkumníka řešení**, v nabídce klikněte pravým tlačítkem nebo místní soubor jazyka JavaScript nebo Python, zvolte **nastavit jako položku při spuštění** příkazu.

1. Zvolte **Start** spusťte ladění.

### <a name="codebases-that-contain-c-code"></a>Základů kódu, které obsahují kód jazyka C++

Informace o otevření kódu jazyka C++ bez řešení nebo projektů v sadě Visual Studio najdete v tématu [projekty otevřít složku pro jazyk C++](/cpp/ide/non-msbuild-projects).

### <a name="codebases-that-contain-a-visual-studio-project"></a>Základů kódu, které obsahují projekt sady Visual Studio

Pokud váš kód složka obsahuje projekt sady Visual Studio, můžete určit projektu jako položku při spuštění.

![Nastavení projektu jako položku při spuštění](media/customize-set-project-as-startup-item.png)

**Start** změny textu tlačítka tak, aby odrážely, že projekt je položku při spuštění.

![Projekt na tlačítko Start](media/customize-start-button-project.png)

## <a name="see-also"></a>Viz také:

- [Přizpůsobení úloh sestavení a ladění](../ide/customize-build-and-debug-tasks-in-visual-studio.md)
- [Otevřete složku projekty jazyka C++](/cpp/ide/non-msbuild-projects)
- [Projekty CMake v jazyce C++](/cpp/ide/cmake-tools-for-visual-cpp)
- [Psaní kódu v editoru kódu a text](../ide/writing-code-in-the-code-and-text-editor.md)