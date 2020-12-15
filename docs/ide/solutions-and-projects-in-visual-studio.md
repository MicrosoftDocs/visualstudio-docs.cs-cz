---
title: Řešení a projekty
description: Seznamte se s projekty a řešeními sady Visual Studio a Naučte se, jak vytvořit nový projekt pomocí nástroje pro Průzkumník řešení.
ms.custom: SEO-VS-2020
ms.date: 12/11/2020
ms.topic: conceptual
f1_keywords:
- vs.addnewitem
- vs.addnewsolutionitem
- vs.openproject
- vs.addexistingitem
- vs.addexistingsolutionitem
- vs.environment.projects
- vs.environment.solutions
- VS.SolutionExplorer
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a24f56d94d470ca5ff04a99f524af3c76df3a15
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524059"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Řešení a projekty v aplikaci Visual Studio

Tato stránka popisuje koncept *projektu* a *řešení* v aplikaci Visual Studio. Také stručně pokrývá okno Průzkumník řešení nástrojů a postup vytvoření nového projektu.

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [projekty a řešení v Visual Studio pro Mac](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Projekty

Při vytváření aplikace nebo webu v aplikaci Visual Studio začnete s *projektem*. V logickém smyslu projekt obsahuje všechny soubory, které jsou zkompilovány do spustitelného souboru, knihovny nebo webu. Tyto soubory mohou zahrnovat zdrojový kód, ikony, obrázky, datové soubory a tak dále. Projekt obsahuje také nastavení kompilátoru a další konfigurační soubory, které mohou být vyžadovány různými službami nebo komponentami, se kterými váš program komunikuje.

### <a name="project-file"></a>Soubor projektu

Visual Studio používá [MSBuild](../msbuild/msbuild.md) k sestavení jednotlivých projektů v řešení a každý projekt obsahuje soubor projektu MSBuild. Přípona souboru odráží typ projektu, například projekt C# (. csproj), Visual Basic projekt (. vbproj) nebo databázový projekt (. dbproj). Soubor projektu je dokument XML, který obsahuje všechny informace a pokyny, které nástroj MSBuild potřebuje k sestavení projektu, včetně obsahu, požadavků na platformu, informací o verzích, webového serveru nebo databázového serveru a úkolů, které mají být provedeny.

Soubory projektu jsou založeny na [schématu XML jazyka MSBuild](../msbuild/msbuild-project-file-schema-reference.md). Chcete-li se podívat na obsah novějších [souborů projektů ve stylu sady SDK v sadě](../msbuild/how-to-use-project-sdk.md) Visual Studio, klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a vyberte možnost **Upravit \<projectname\>**. Chcete-li se podívat na obsah .NET Framework a dalších projektů tohoto stylu, nejprve uvolněte projekt (klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a vyberte **Uvolnit projekt**). Potom klikněte pravým tlačítkem na projekt a zvolte možnost **Upravit \<projectname\>**.

> [!NOTE]
> K úpravám, sestavování a ladění kódu nemusíte používat řešení nebo projekty v aplikaci Visual Studio. Jednoduše otevřete složku, která obsahuje zdrojové soubory v aplikaci Visual Studio, a začněte upravovat. Další informace naleznete v tématu [vývoj kódu v aplikaci Visual Studio bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions"></a>Řešení

Projekt je obsažen v rámci *řešení*. Bez ohledu na jeho název není řešení "Answer". Je to jednoduše kontejner pro jeden nebo více souvisejících projektů, společně s informacemi o sestavení, nastavení okna sady Visual Studio a s dalšími soubory, které nejsou přidružené k určitému projektu. Řešení je popsáno v textovém souboru (s příponou *. sln*) s vlastním jedinečným formátem. není určeno k úpravám rukou.

Visual Studio používá dva typy souborů (*. sln* a *. suo*) k ukládání nastavení řešení:

|Linka|Název|Popis|
|---------------|----------|-----------------|
|. sln|Řešení sady Visual Studio|Uspořádá projekty, položky projektu a položky řešení v řešení.|
|. suo|Možnosti uživatele řešení|Ukládá nastavení a přizpůsobení na úrovni uživatele, například zarážky.|

### <a name="solution-folder"></a>Složka řešení

V tomto kontextu je "Složka řešení" virtuální složkou, která je pouze v **Průzkumník řešení**, kde ji můžete použít k seskupení projektů v řešení. Pokud chcete na počítači najít soubor řešení, přejděte na možnosti **nástroje**  >    >  **projekty a**  >  **umístění** řešení. Další informace najdete v [dialogovém okně Možnosti: projekty a řešení > umístění](./reference/projects-solutions-locations-options.md).

## <a name="create-new-projects"></a>Vytvořit nové projekty

Nejjednodušší způsob, jak vytvořit nový projekt, je začít od šablony projektu pro konkrétní typ aplikace nebo webu. Šablona projektu se skládá ze základní sady předem generovaných souborů kódu, konfiguračních souborů, prostředků a nastavení. Tyto šablony jsou k dispozici v dialogovém okně, kde vytvoříte nový projekt (**soubor**  >  **Nový**  >  **projekt**). Další informace naleznete v tématu [Vytvoření nového projektu v aplikaci Visual Studio](create-new-project.md) a [vytváření řešení a projektů](../ide/creating-solutions-and-projects.md).

Pokud často přizpůsobíte projekty určitým způsobem, můžete vytvořit vlastní šablonu projektu, kterou pak můžete použít k vytvoření nových projektů z. Další informace naleznete v tématu [Create Project and Item Templates](../ide/creating-project-and-item-templates.md).

Když vytvoříte nový projekt, uloží se ve výchozím nastavení na *%USERPROFILE%\source\repos*. Toto umístění můžete změnit v nastavení **umístění projektů** v nabídce **nástroje**  >  **Možnosti**  >  **projekty a**  >  **umístění** řešení. Další informace naleznete na [stránce projekty a řešení, dialogové okno Možnosti](./reference/projects-and-solutions-options-dialog-box.md).

## <a name="solution-explorer"></a>Průzkumník řešení

Po vytvoření nového projektu můžete použít **Průzkumník řešení** k zobrazení a správě projektu a řešení a jejich přidružených položek. Následující ilustrace ukazuje **Průzkumník řešení** s řešením C#, které obsahuje dva projekty:

![Průzkumník řešení](../ide/media/vs2015_solution_explorer.png)

Řada příkazů nabídky je k dispozici v nabídce po kliknutí pravým tlačítkem myši na různých položkách v **Průzkumník řešení**. Mezi tyto příkazy patří sestavení projektu, Správa balíčků NuGet, přidání odkazu, přejmenování souboru a spuštění testů, stačí jenom pár název. Panel nástrojů v horní části **Průzkumník řešení** obsahuje tlačítka pro přepínání ze zobrazení řešení do zobrazení složky, zobrazení skrytých souborů, sbalení všech uzlů a další.

> [!TIP]
> Pokud jste Průzkumník řešení zavřeli a chcete ho znovu otevřít, v řádku nabídek vyberte **okno**  >  **obnovit rozložení okna** .

U ASP.NET Core projektů můžete přizpůsobit, jak jsou soubory vnořené v **Průzkumník řešení**. Další informace najdete v tématu [přizpůsobení vnořování souborů v Průzkumník řešení](file-nesting-solution-explorer.md).

A pokud chcete zobrazit seznam některých ikon, které se zobrazují v Průzkumník řešení, přečtěte si téma [zobrazení tříd a prohlížeč objektů ikony](class-view-and-object-browser-icons.md).

## <a name="see-also"></a>Viz také

- [Integrované vývojové prostředí sady Visual Studio](../get-started/visual-studio-ide.md)
- [Přenos, migrace a upgrade projektů](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Projekty a řešení (Visual Studio pro Mac)](/visualstudio/mac/projects-and-solutions)
- [Přidání a odebrání položek projektu (Visual Studio pro Mac)](/visualstudio/mac/add-and-remove-project-items)
