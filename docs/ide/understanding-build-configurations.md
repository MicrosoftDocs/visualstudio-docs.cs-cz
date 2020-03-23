---
title: Vysvětlení konfigurací sestavení
ms.date: 01/20/2020
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a37d4fa5dc92253b94dc64590c9df5fec7703ceb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77904162"
---
# <a name="understand-build-configurations"></a>Vysvětlení konfigurací sestavení

Konfigurace sestavení potřebujete, když potřebujete vytvářet projekty s různými nastaveními. Například **Ladění** a **vydání** jsou konfigurace a různé možnosti kompilátoru se používají odpovídajícím způsobem při jejich vytváření.  Jedna konfigurace je aktivní a je uvedena v panelu příkazů v horní části ide.

![Aktivní konfigurace](media/understanding-build-configurations/active-config.png)

> [!NOTE]
> Toto téma platí pro Visual Studio v systému Windows. Visual Studio pro Mac najdete [v tématu Vytváření konfigurací ve Visual Studiu pro Mac](/visualstudio/mac/configurations).

Konfigurace a řízení platformy, kde jsou uloženy vytvořené výstupní soubory. Za normálních okolností při Visual Studio vytvoří projekt, výstup je umístěn v podsložce projektu s názvem s aktivní konfigurací (například *bin/Debug/x86*), ale můžete to změnit.

Můžete vytvořit vlastní konfigurace sestavení na úrovni řešení a projektu. Konfigurace řešení určuje, které projekty jsou zahrnuty v sestavení, když je tato konfigurace aktivní. Budou vytvořeny pouze projekty, které jsou zadány v konfiguraci aktivního řešení. Pokud je v nástroji Configuration Manager vybráno více cílových platforem, budou vytvořeny všechny projekty, které se na tuto platformu vztahují. Konfigurace projektu určuje, jaké nastavení sestavení a možnosti kompilátoru se používají při vytváření projektu.

Chcete-li vytvořit, vybrat, upravit nebo odstranit konfiguraci, můžete použít **nástroj Configuration Manager**. Chcete-li ji otevřít, zvolte na řádku nabídek možnost **Vytvořit** > **nástroj Pro nástroj Konfigurace nebo**stačí zadat **položku Konfigurace** do vyhledávacího pole. Pomocí seznamu **Konfigurace řešení** na panelu nástrojů **Standardní** můžete také vybrat konfiguraci nebo otevřít Nástroj **pro konfiguraci**.

![Configuration Manager](media/understanding-build-configurations/config-manager.png)

> [!NOTE]
> Pokud nemůžete najít nastavení konfigurace řešení na panelu nástrojů a nemáte [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] přístup ke **Správci konfigurace**, může být použito nastavení vývoje. Další informace naleznete v [tématu Postup: Správa konfigurací pomocí použitého nastavení pro vývojáře jazyka Visual Basic](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).

Ve výchozím nastavení ladění **a** **vydání** konfigurace jsou zahrnuty [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] v projektech, které jsou vytvořeny pomocí šablon. Konfigurace **ladění** podporuje ladění aplikace a **konfigurace vydání** vytvoří verzi aplikace, kterou lze nasadit. Další informace naleznete v [tématu How to: Set debug and release configurations](../debugger/how-to-set-debug-and-release-configurations.md). Můžete také vytvořit vlastní konfigurace řešení a konfigurace projektu. Další informace naleznete v [tématu Postup: Vytváření a úpravy konfigurací](../ide/how-to-create-and-edit-configurations.md).

## <a name="solution-configurations"></a>Konfigurace řešení

Konfigurace řešení určuje, jak mají být vytvořeny a nasazeny projekty v řešení. Chcete-li upravit konfiguraci řešení nebo definovat novou, zvolte v **nástroji Configuration Manager**v části Konfigurace **aktivního řešení**možnost **Upravit** nebo **Nový**.

Každá položka v poli **Kontexty aplikace Project** v konfiguraci řešení představuje projekt v řešení. Pro každou kombinaci **konfigurace aktivního řešení** a **aktivní platformy řešení**můžete nastavit způsob použití každého projektu. (Další informace o platformách řešení naleznete [v tématu Principy platformy sestavení](../ide/understanding-build-platforms.md).)

Když definujete novou konfiguraci řešení a zaškrtnete [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] políčko Vytvořit nové konfigurace **projektu,** automaticky přiřadí novou konfiguraci všem projektům. Podobně když definujete novou platformu řešení a zaškrtnete [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] políčko Vytvořit nové **platformy projektu,** automaticky přiřadí novou platformu všem projektům. Také pokud přidáte projekt, který se zaměřuje na novou platformu, Visual Studio přidá tuto platformu do seznamu platformy řešení a přiřadí ji ke všem projektům. Stále můžete upravit nastavení pro každý projekt.

Konfigurace aktivní řešení také poskytuje kontext pro ide. Pokud například pracujete na projektu a konfigurace určuje, že bude vytvořen pro mobilní zařízení, **panel nástrojů** zobrazí pouze položky, které lze použít v projektu mobilního zařízení.

## <a name="project-configurations"></a>Konfigurace projektu

Konfigurace a platforma, které cíle projektu se používají společně k určení nastavení sestavení a možnosti kompilátoru použít při jeho sestavení. Projekt může mít různá nastavení pro každou kombinaci konfigurace a platformy. Chcete-li upravit vlastnosti projektu, otevřete místní nabídku projektu v **Průzkumníku řešení**a zvolte **Vlastnosti**.  V horní části karty **Sestavení** návrháře projektu zvolte aktivní konfiguraci a upravte jeho nastavení sestavení.

![Konfigurace návrháře projektu](media/understanding-build-configurations/project-designer-configuration.png)

## <a name="building-multiple-configurations"></a>Vytváření více konfigurací

Při vytváření řešení pomocí příkazu **sestavení** > **sestavení řešení,** Visual Studio pouze vytvoří aktivní konfiguraci. Všechny projekty, které jsou zadány v této konfiguraci řešení jsou sestaveny a jedinou konfigurací projektu, která je sestavena, je konfigurace aktivního řešení a aktivní platformy řešení, která je zobrazena na panelu nástrojů v sadě Visual Studio. Například **Ladění** a **x86**. Jiné definované konfigurace a platformy nejsou vytvořeny.

Pokud chcete vytvořit více konfigurací a platforem v jedné akci, můžete použít možnost **sestavení** > **dávky sestavení** v sadě Visual Studio. Chcete-li získat přístup k této funkci, otevřete vyhledávací pole stisknutím **klávesctrl**+**q** a zadejte . `Batch build` Dávkové sestavení není k dispozici pro všechny typy projektů. Viz [Postup: Vytvoření více konfigurací současně](how-to-build-multiple-configurations-simultaneously.md).

## <a name="how-visual-studio-assigns-project-configurations"></a>Jak Visual Studio přiřazuje konfigurace projektů

Když definujete novou konfiguraci řešení a nekopírujete nastavení z existující, Visual Studio použije následující kritéria pro přiřazení výchozích konfigurací projektu. Kritéria jsou vyhodnocena v uvedeném pořadí.

1. Pokud projekt má název konfigurace (*\<název konfigurace> \<název platformy>), *který přesně odpovídá názvu nové konfigurace řešení, je tato konfigurace přiřazena. Názvy konfigurací nejsou rozlišována malá a velká písmena.

1. Pokud projekt má název konfigurace, ve kterém součást název konfigurace odpovídá nové konfiguraci řešení, je tato konfigurace přiřazena, bez ohledu na to, zda část platformy odpovídá nebo ne.

1. Pokud stále neexistuje žádná shoda, je přiřazena první konfigurace uvedená v projektu.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Jak Visual Studio přiřazuje konfigurace řešení

Když vytvoříte konfiguraci projektu (ve **Správci konfigurace**, výběrem **nové** v rozevírací nabídce ve **sloupci Konfigurace** pro tento projekt) a zaškrtnete políčko Vytvořit nové **konfigurace řešení,** Visual Studio vyhledá konfiguraci řešení s označením like pro sestavení projektu na každé platformě, kterou podporuje. V některých případech Visual Studio přejmenuje existující konfigurace řešení nebo definuje nové.

Visual Studio používá následující kritéria pro přiřazení konfigurace řešení.

- Pokud konfigurace projektu neurčuje platformu nebo určuje pouze jednu platformu, pak konfigurace řešení, jehož název odpovídá názvu nové konfigurace projektu je nalezen nebo přidán. Výchozí název této konfigurace řešení neobsahuje název platformy; přebírá název * \<konfigurace projektu *formuláře>.

- Pokud projekt podporuje více platforem, konfigurace řešení je nalezena nebo přidána pro každou podporovanou platformu. Název každé konfigurace řešení zahrnuje název konfigurace projektu a název platformy a má název konfigurace projektu formuláře * \<> \<název platformy>*.

## <a name="see-also"></a>Viz také

- [Návod: Sestavení aplikace](../ide/walkthrough-building-an-application.md)
- [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)
- [Řešení a projekty](../ide/solutions-and-projects-in-visual-studio.md)
- [Referenční informace k sestavením v C/C++](/cpp/build/reference/c-cpp-building-reference)
- [Principy platforem sestavení](understanding-build-platforms.md)
- [Konfigurace sestavení (Visual Studio pro Mac)](/visualstudio/mac/configurations)
