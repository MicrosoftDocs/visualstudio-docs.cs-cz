---
title: Stránky vlastností | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac788f51bcdc52cd39469a272909890333c5016b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706060"
---
# <a name="property-pages"></a>Stránky vlastností
Uživatelé mohou zobrazit a změnit vlastnosti závislé na konfiguraci projektu a nezávislé pomocí stránek vlastností. Tlačítko **Stránky vlastností** je povoleno v okně **Vlastnosti** nebo na panelu nástrojů Průzkumník řešení pro objekty, které poskytují zobrazení stránky vlastností vybraného objektu. Stránky vlastností jsou vytvářeny prostředím a jsou k dispozici pro řešení a projekty. Mohou však být také k dispozici pro položky projektu, které využívají vlastnosti závislé na konfiguraci. Tato funkce může být použita v případě, že soubory v rámci projektu vyžadují různá nastavení přepínače kompilátoru, aby se správně vytvořily.

## <a name="using-property-pages"></a>Použití stránek vlastností
 Pokud je stránka vlastností již zobrazena a výběr se změní (například z řešení na projekt), informace zobrazené na stránkách se změní a zobrazí vlastnosti nového výběru. Pokud na objektu nejsou žádné vlastnosti, které podporují stránky vlastností, stránka vlastností je prázdná.

 Pokud je vybráno více objektů, stránka vlastností zobrazí průsečík vlastností pro všechny vybrané položky. Pokud vybraná položka neobsahuje vlastnosti závislé na konfiguraci a klepne se na tlačítko **Stránky vlastností** na panelu nástrojů Průzkumník řešení, změní se fokus na okno Vlastnosti. Další informace týkající se okna vlastností a výběru naleznete v [tématu Rozšíření vlastností](../../extensibility/internals/extending-properties.md).

 Pokud jsou vlastnosti zobrazeny pro více objektů a změníte hodnotu na stránce vlastností, všechny hodnoty objektů jsou nastaveny na novou hodnotu, i když byly zpočátku odlišné a stránka byla prázdná, když byly zobrazeny vlastnosti jednotlivého objektu.

 V aplikaci jsou k dispozici dva [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]obecné typy dialogových oken **Stránek vlastností aplikace ProjectProperty** . V prvním pro projekty jazyka, například stránky vlastností jsou zobrazeny pomocí formátu pole, jak je znázorněno na následujícím snímku obrazovky. Ve druhém, který je uveden dále v této části, stránka vlastností hostí mřížku vlastností podobnou té, která se nachází v okně Vlastnosti.

 ![Stránky vlastností jazyka Visual Basic](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") Dialogové okno Stránky vlastností projektu s formátem pole a stromovou strukturou

 Stromová struktura v dialogovém okně Stránky <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>vlastností není vytvořena pomocí aplikace . Prostředí, na základě názvu úrovně, který <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> mu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> předal a rozhraní, jej vytvoří.

 Na stránkách [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vlastností jsou k dispozici pouze dvě kategorie nejvyšší úrovně:

- Společné vlastnosti, které zobrazují informace nezávislé na konfiguraci pro vybraný objekt nebo objekty. V důsledku toho, pokud je vybrána jedna z podkategorií Common Properties, nejsou k dispozici možnosti Konfigurace, Platforma a Správce konfigurace v horní části dialogového okna.

- Vlastnosti konfigurace, který obsahuje informace závislé na konfiguraci týkající se ladění, optimalizace a sestavení parametry pro řešení nebo projektu.

  Nelze vytvořit žádné další kategorie nejvyšší úrovně, ale můžete se rozhodnout, `IVsPropertyPage`že nezobrazí temi jeden nebo druhý v implementaci aplikace . Pokud například nemáte žádné vlastnosti nezávislé na konfiguraci, které by bylo možné zobrazit pro objekt, můžete se rozhodnout, že kategorii Společné vlastnosti nezobrazíte. Při `ISpecifyPropertyPages` implementaci `ISpecifyPropertyPages` objektu v konfiguračním objektu (implementující `IVsCfg`objekt , `IVsProjectCfg`a souvisejících rozhraní) se zobrazí společné vlastnosti.

  Každá kategorie zobrazená v kategorii nejvyšší úrovně představuje samostatnou stránku vlastností. Položky kategorií a podkategorií dostupné v dialogovém okně `ISpecifyPropertyPages` `IVsPropertyPage`jsou určeny implementací aplikace a .

  `IDispatch`objekty pro položky v kontejneru výběru, které `ISpecifyPropertyPages` mají vlastnosti, které mají být zobrazeny na stránkách vlastností implementovat výčet seznamu ID třídy. ID třídy jsou předány `ISpecifyPropertyPages` jako proměnné a slouží k vytvoření instance stránky vlastností. Seznam ID třídy je také `IVsPropertyPage` předán k vytvoření stromové struktury na levé straně dialogového okna. Stránky vlastností pak předat `IDispatch` informace zpět `ISpecifyPropertyPages` do objektu, který implementuje a vyplňuje informace pro každou stránku.

  Vlastnosti objektu procházení jsou `IDispatch` načteny pomocí pro každý objekt v kontejneru výběru.

  Implementace `Help::DisplayTopicFromF1Keyword` v balíčku VSPackage poskytuje funkce pro tlačítko nápovědy.

  Další informace naleznete `IDispatch` `ISpecifyPropertyPages`v knihovně MSDN a v její knihovně.

  Druhý typ stránek vlastností zobrazených ve vzorcích hostuje formu mřížky vlastností, jak je znázorněno na následujícím snímku obrazovky.

  ![Stránky vlastností VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") Dialogové okno Stránky vlastností s mřížkou vlastností

  Rozhraní `IVSMDPropertyBrowser` a `IVSMDPropertyGrid` (deklarované v vsmanaged.h) se používají k vytvoření a naplnění mřížky vlastností v dialogovém okně nebo okně.

  Architektura projektů se výrazně změnila oproti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]minulým verzím . Zejména se změnila představa, který projekt je aktivní. V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]aplikaci neexistuje žádný koncept aktivního projektu. V předchozích vývojových prostředích byl aktivním projektem projekt, který by sestavoval a nasazoval příkazy bez ohledu na kontext. Nyní ovládací prvky řešení a rozhodčí, které sestavení a nasazení příkazů platí pro které projekty.

  To, co bylo dříve aktivním projektem, je nyní zachyceno jedním ze tří různých způsobů:

- Projekt spuštění

   Můžete zadat projekt nebo projekty ze stránky vlastností řešení, která bude spuštěna, když uživatel stiskne klávesu F5 nebo vybere spustit z nabídky Sestavení. To funguje podobným způsobem jako starý aktivní projekt v tom smyslu, že jeho název je zobrazen v Průzkumníku řešení s tučným písmem.

   Projekt spuštění můžete načíst jako vlastnost v `DTE.Solution.SolutionBuild.StartupProjects`modelu automatizace voláním . V VSPackage, volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> metody. `IVsSolutionBuildManager`je k dispozici `QueryService` jako služba v SID_SVsSolutionBuildManager. Další informace naleznete v [tématu Project Configuration Object](../../extensibility/internals/project-configuration-object.md) and [Solution Configuration](../../extensibility/internals/solution-configuration.md).

- Konfigurace sestavení aktivního řešení

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]má aktivní konfiguraci řešení, která je `DTE.Solution.SolutionBuild.ActiveConfiguration`k dispozici v modelu automatizace implementací . Konfigurace řešení je kolekce, která obsahuje jednu konfiguraci projektu pro každý projekt v řešení (každý projekt může mít více konfigurací, na více platformách, s odlišnými názvy). Další informace týkající se stránek vlastností řešení naleznete v tématu [Konfigurace řešení](../../extensibility/internals/solution-configuration.md).

- Aktuálně vybraný projekt

   Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> metodu pro načtení hierarchie projektu a vybrané položky projektu nebo položek. Z DTE byste použít `SelectedItems.SelectedItem.Project` `SelectedItems.SelectedItem.ProjectItem` a metody. Pod těmito nadpisy je v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] základních dokumentech ukázkový kód.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)
- [Objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md)
- [Konfigurace řešení](../../extensibility/internals/solution-configuration.md)
