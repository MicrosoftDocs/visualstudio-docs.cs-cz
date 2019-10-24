---
title: Stránky vlastností | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51487b35686da9676f201a157ddb8e47afb75ce8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725060"
---
# <a name="property-pages"></a>Stránky vlastností
Uživatelé mohou zobrazit a změnit konfiguraci projektu závislé a nezávislé vlastnosti pomocí stránek vlastností. Tlačítko **stránky vlastností** je povoleno v okně **vlastnosti** nebo na panelu nástrojů Průzkumník řešení pro objekty, které poskytují zobrazení stránky vlastností vybraného objektu. Stránky vlastností jsou vytvořeny prostředím a jsou k dispozici pro řešení a projekty. Mohou však být zpřístupněny také pro položky projektu, které využívají vlastnosti závislé na konfiguraci. Tato funkce může být použita, pokud soubory v projektu vyžadují pro správné sestavení jiné nastavení přepínače kompilátoru.

## <a name="using-property-pages"></a>Použití stránek vlastností
 Pokud se stránka vlastností už zobrazila a výběr se změní (například z řešení na projekt), informace zobrazené na stránkách se změní tak, aby se zobrazily vlastnosti nového výběru. Pokud neexistují žádné vlastnosti objektu, který podporuje stránky vlastností, stránka vlastností je prázdná.

 Je-li vybráno více objektů, stránka vlastností zobrazí průnik vlastností pro všechny vybrané položky. Pokud vybraná položka neobsahuje vlastnosti závislé na konfiguraci a na panelu nástrojů Průzkumník řešení se klikne na tlačítko **stránky vlastností** , fokus se změní na okno Vlastnosti. Další informace týkající se okno Vlastnosti a výběru najdete v tématu [rozšíření vlastností](../../extensibility/internals/extending-properties.md).

 Pokud jsou pro více objektů zobrazeny vlastnosti a změníte hodnotu na stránce vlastností, všechny hodnoty pro objekty jsou nastaveny na novou hodnotu, i když byly původně odlišné a při zobrazení vlastností jednotlivých objektů byla stránka prázdná.

 V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jsou k dispozici dva obecné typy dialogových oken **stránek ProjectProperty** . V prvním případě Visual Basic projekty například stránky vlastností se zobrazují pomocí formátu pole, jak je znázorněno na následujícím snímku obrazovky. V druhé, jak je uvedeno dále v této části, stránka vlastností hostuje mřížku vlastností podobným způsobem, který najdete v okně Vlastnosti.

 ![Stránky vlastností Visual Basic](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") Dialogové okno stránky vlastností projektu se formátem pole a stromovou strukturou

 Stromová struktura v dialogovém okně stránky vlastností není sestavena pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. Prostředí je na základě názvu úrovně předaného <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> a rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> sestavením.

 Na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ch stránkách vlastností jsou dostupné jenom dvě kategorie nejvyšší úrovně:

- Společné vlastnosti, které zobrazují informace nezávislé na konfiguraci pro vybraný objekt nebo objekty. Výsledkem je, že když je vybraná jedna z kategorií společných vlastností, možnosti konfigurace, platformy a Configuration Manager v horní části dialogového okna nejsou k dispozici.

- Vlastnosti konfigurace, které obsahují informace závislé na konfiguraci týkající se ladění, optimalizace a parametrů sestavení pro řešení nebo projekt.

  Nemůžete vytvořit žádné další kategorie nejvyšší úrovně, ale v implementaci `IVsPropertyPage` můžete zvolit, že se nezobrazuje jedna nebo druhá. Pokud například nemáte žádné vlastnosti nezávislé na konfiguraci pro zobrazení objektu, můžete zvolit možnost nezobrazit kategorii společné vlastnosti. Pokud implementujete `ISpecifyPropertyPages` v objektu Configuration (objekt implementující `IVsCfg`, `IVsProjectCfg` a souvisejících rozhraních), zobrazí se společné vlastnosti, pokud je `ISpecifyPropertyPages` implementována z objektu procházení a vlastností konfigurace položky.

  Každá kategorie zobrazená v kategorii nejvyšší úrovně představuje samostatnou stránku vlastností. Položky kategorie a podkategorie dostupné v dialogovém okně jsou určeny vaší implementací `ISpecifyPropertyPages` a `IVsPropertyPage`.

  `IDispatch` objekty pro položky v kontejneru výběru, které mají vlastnosti, které se mají zobrazit na stránkách vlastností, implementují `ISpecifyPropertyPages` k vytvoření výčtu seznamu ID tříd. Identifikátory třídy jsou předány jako proměnné pro `ISpecifyPropertyPages` a slouží k vytvoření instance stránek vlastností. Seznam identifikátorů třídy je také předán `IVsPropertyPage` k vytvoření stromové struktury na levé straně dialogového okna. Na stránkách vlastností pak předejte informace zpět do objektu `IDispatch`, který implementuje `ISpecifyPropertyPages` a vyplní informace pro každou stránku.

  Vlastnosti objektu procházení jsou načteny pomocí `IDispatch` pro každý objekt v kontejneru výběru.

  Implementace `Help::DisplayTopicFromF1Keyword` v balíčku VSPackage poskytuje funkce pro tlačítko Help.

  Další informace najdete v tématu `IDispatch` a `ISpecifyPropertyPages`in knihovny MSDN.

  Druhý typ stránek vlastností zobrazených v ukázkách hostuje formu mřížky vlastností, jak je znázorněno na následujícím snímku obrazovky.

  ![Stránky vlastností VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") Dialogové okno stránky vlastností s mřížkou vlastností

  Rozhraní `IVSMDPropertyBrowser` a `IVSMDPropertyGrid` (deklarované v vsmanaged. h) slouží k vytvoření a naplnění mřížky vlastností v rámci dialogového okna nebo okna.

  Architektura projektů se podstatně změnila z minulých verzí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Zejména pojem, který projekt aktivní, se změnil. V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] neexistuje koncept aktivního projektu. V předchozích vývojových prostředích byl aktivní projekt projekt, který příkazy sestavení a nasazení budou mít výchozí hodnotu bez ohledu na kontext. Nyní ovládací prvky řešení a arbitrates, které příkazy sestavení a nasazení platí pro které projekty.

  Dříve byl aktivní projekt zachycen jedním ze tří různých způsobů:

- Spouštěný projekt

   Projekt nebo projekty můžete zadat na stránce vlastností řešení, která se spustí, když uživatel stiskne klávesu F5 nebo vybere možnost spustit z nabídky sestavit. Funguje způsobem podobným původnímu aktivnímu projektu v tom smyslu, že se jeho název zobrazuje v Průzkumník řešení s tučným písmem.

   Můžete načíst spouštěcí projekt jako vlastnost v modelu automatizace voláním `DTE.Solution.SolutionBuild.StartupProjects`. V VSPackage zavoláte <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> nebo metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A>. `IVsSolutionBuildManager` je k dispozici jako služba `QueryService` v SID_SVsSolutionBuildManager. Další informace najdete v [tématu Konfigurace a](../../extensibility/internals/solution-configuration.md) [objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md) .

- Konfigurace sestavení aktivních řešení

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] má aktivní konfiguraci řešení, která je k dispozici v modelu automatizace implementací `DTE.Solution.SolutionBuild.ActiveConfiguration`. Konfigurace řešení je kolekce, která obsahuje jednu konfiguraci projektu pro každý projekt v řešení (každý projekt může mít více konfigurací, na více platformách s odlišnými názvy). Další informace o stránkách vlastností řešení najdete v tématu věnovaném [konfiguraci řešení](../../extensibility/internals/solution-configuration.md).

- Aktuálně vybraný projekt

   Implementací metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> načtěte hierarchii projektu a položky projektu nebo vybrané položky. Z DTE byste použili metody `SelectedItems.SelectedItem.Project` a `SelectedItems.SelectedItem.ProjectItem`. V základních [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dokumentech je ukázkový kód v těchto hlavičkách.

## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)
- [Objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md)
- [Konfigurace řešení](../../extensibility/internals/solution-configuration.md)