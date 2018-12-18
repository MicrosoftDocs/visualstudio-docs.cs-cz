---
title: Principy konfigurací sestavení
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
f1_keywords:
- SolutionProperties.ActiveConfig
- vs.build.newprojectconfiguration
- vc.proj.configurationsctrl.multipleconfigs
- vs.build.editsolutionconfigurations
- vs.build.editprojectconfigurations
- vs.multipleconfigurations
- vs.build.newsolutionconfiguration
- VS.ConfigurationManager
- VS.MultipleConfig
helpviewer_keywords:
- solution build configurations, about build configurations
- build configurations
- project build configurations
- build configurations, advanced
- projects [Visual Studio], build configuration
- solutions [Visual Studio], build configuration
ms.assetid: 934c727d-3a22-429c-bd13-3552cecf2e24
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3e361b407d013f27f3cf76d1ff0da98aa36c3c8
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349046"
---
# <a name="understand-build-configurations"></a>Principy konfigurací sestavení

Můžete ukládat různé konfigurace vlastností řešení a projektu pro použití v různé druhy sestavení. Chcete-li vytvořit, vyberte, upravit nebo odstranit konfiguraci, můžete použít **nástroje Configuration Manager**. Pokud chcete soubor otevřít, v řádku nabídek, zvolte **sestavení** > **nástroje Configuration Manager**, nebo zadejte **konfigurace** v **Snadné spuštění**pole. Můžete také použít **konfigurace řešení** seznamu **standardní** panelu nástrojů vyberte konfiguraci nebo otevřít **nástroje Configuration Manager**.

> [!NOTE]
> Toto téma se vztahuje k sadě Visual Studio ve Windows. Visual Studio pro Mac, najdete v části [konfigurace v sadě Visual Studio pro Mac sestavení](/visualstudio/mac/configurations).

> [!NOTE]
> Pokud nemůže najít řešení, konfigurace nastavení na panelu nástrojů a nemůžou přistupovat **nástroje Configuration Manager**, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] můžou vztahovat. vývojové nastavení. Další informace najdete v tématu [postupy: Správa konfigurací s použitými nastaveními vývojáře jazyka Visual Basic](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).

Ve výchozím nastavení, ladění a konfiguraci vydání jsou zahrnuté v projektech, které jsou vytvářeny instalační sadou [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] šablony. Konfigurace ladění podporuje ladění aplikace a konfiguraci vydané verze sestavení na verzi aplikace, který je možné nasadit. Další informace najdete v tématu [postupy: nastavení ladění a vydání konfigurace](../debugger/how-to-set-debug-and-release-configurations.md). Můžete také vytvořit vlastní řešení konfigurace a konfigurace projektu. Další informace najdete v tématu [postupy: vytvoření a úprava konfigurací](../ide/how-to-create-and-edit-configurations.md).

## <a name="solution-configurations"></a>Konfigurace řešení

Konfigurace řešení určuje, jak jsou projekty v řešení sestaveny a nasazeny. K úpravě konfigurace řešení nebo definovat novou, v **nástroje Configuration Manager**v části **konfigurace aktivního řešení**, zvolte **upravit** nebo **nový** .

Každá položka **projektu kontexty** pole v konfiguraci řešení představuje projekt v řešení. Pro každou kombinaci **konfigurace aktivního řešení** a **platformou aktivního řešení**, můžete nastavit, jak každý projekt používá. (Další informace o platformy řešení najdete v tématu [platformy sestavení porozumění](../ide/understanding-build-platforms.md).)

> [!NOTE]
> Při definování nové konfigurace řešení a vyberte **vytvořit nové konfigurace projektu** zaškrtávací políčko [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticky přiřadí novou konfiguraci pro všechny projekty. Podobně když definovat nová platforma řešení a vyberete **vytvořit nové platformy projektu** zaškrtávací políčko [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticky přiřadí novou platformu pro všechny projekty. Také pokud chcete přidat projekt, který cílí na novou platformu, Visual Studio přidá tuto platformu na seznam platformy řešení a přiřadí ji do všech projektů.
>
> Pořád můžete upravit nastavení pro každý projekt.

Konfigurace aktivního řešení také poskytuje kontext do rozhraní IDE. Například pokud pracujete na projektu a konfigurace určuje, že dojde k jeho sestavení pro mobilní zařízení, **nástrojů** zobrazí pouze položky, které lze použít v projektu mobilních zařízení.

## <a name="project-configurations"></a>Konfigurace projektu
 Konfigurace a platformy, které projekt cílí na se používají společně k určení vlastností pro použití při systém orchard je založen. Projekt může mít jinou sadu definice vlastností pro každou kombinaci konfigurace a platforma. Chcete-li změnit vlastnosti projektu, můžete použít stránky s jejími vlastnostmi. (V **Průzkumníka řešení**, otevřete místní nabídku pro projekt a klikněte na tlačítko **vlastnosti**.)

 Pro každou konfiguraci projektu můžete definovat vlastnosti závislé na konfiguraci podle potřeby. Například pro konkrétní sestavení, můžete nastavit, položky projektu, které budou zahrnuty, a co výstupní soubory budou vytvořeny, kde budou umístěny, a jak bude optimalizované.

 Konfigurace projektu se může značně lišit. Vlastnosti jedné konfigurace může například zadat, že jeho výstupní soubor optimalizovat tak, aby obsadily minimální volné místo, zatímco jiné konfigurace může být spouštěna, že její spustitelný soubor maximální rychlostí.

 Konfigurace projektu jsou uloženy řešením – není uživatelem, tak, aby může být sdílen týmem.

 I když závislosti projektu jsou nezávislé na konfiguraci, bude vytvořen pouze projekty, které jsou určené v konfiguraci aktivního řešení.

## <a name="how-visual-studio-assigns-project-configurations"></a>Přiřazování konfigurace projektu v sadě Visual Studio
 Při definování nové konfigurace řešení a nekopírujte nastavení z existující aplikace Visual Studio používá následující kritéria přiřadit výchozí konfigurace projektu. Kritéria jsou vyhodnocovány v uvedeném pořadí.

1.  Pokud projekt obsahuje název konfigurace (*\<název konfigurace > \<název platformy >*), je přiřazen přesně odpovídá názvu nová konfigurace řešení, tuto konfiguraci. Názvy konfigurace nejsou malá a velká písmena.

2.  Pokud projekt obsahuje název konfigurace, ve kterých části název konfigurace odpovídá nová konfigurace řešení, tato konfigurace je přiřazen, zda odpovídá platforma část nebo ne.

3.  Pokud ještě není nalezena žádná shoda, přiřadí se první konfigurace, který je uveden v projektu.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Přiřazování konfigurace řešení v sadě Visual Studio
 Při vytváření konfigurace projektu (v **nástroje Configuration Manager**, výběrem **nový** v rozevírací nabídce v **konfigurace** sloupce pro tento projekt) a Vyberte **vytvořit nové konfigurace řešení** zaškrtávací políčko, Visual Studio vyhledá konfigurace s názvem jako řešení pro sestavení projektu na jednotlivých platformách podporuje. V některých případech může Visual Studio přejmenuje existující konfigurace řešení nebo definuje nové značky.

 Visual Studio používá následující kritéria pro přiřazení konfigurací řešení.

-   Pokud konfigurace projektu neurčuje platformu nebo určuje jenom jednu platformu, pak konfigurace řešení, jehož název se shoduje s novou konfiguraci projektu je najít nebo přidat. Výchozí název této konfigurace řešení neobsahuje název platformy. má podobu  *\<název konfigurace projektu >*.

-   Pokud projekt podporuje více platforem, konfigurace řešení je najít nebo přidat pro každou podporovanou platformu. Název každé konfigurace řešení obsahuje název konfigurace projektu a název platformy a má tvar  *\<název konfigurace projektu > \<název platformy >*.

## <a name="see-also"></a>Viz také:

- [Návod: Sestavení aplikace](../ide/walkthrough-building-an-application.md)
- [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)
- [Řešení a projekty](../ide/solutions-and-projects-in-visual-studio.md)
- [Reference sestavení C/C++](/cpp/build/reference/c-cpp-building-reference)
- [Přepínače příkazového řádku nástroje devenv](../ide/reference/devenv-command-line-switches.md)
- [Sestavení konfigurací (Visual Studio for Mac)](/visualstudio/mac/configurations)