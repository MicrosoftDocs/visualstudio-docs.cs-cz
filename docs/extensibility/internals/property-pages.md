---
title: Stránky vlastností | Microsoft Docs
description: Přečtěte si o práci se stránkami vlastností nového typu projektu v sadě SDK Visual Studio, která uživatelům umožňuje zobrazit a změnit vlastnosti projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 88ebf99ef2361a232c4a5c4c02b9a140155d66e9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903408"
---
# <a name="property-pages"></a>Stránky vlastností
Uživatelé mohou zobrazit a změnit vlastnosti závislé na konfiguraci projektu a nezávislé na projektu pomocí stránek vlastností. Tlačítko **Stránky vlastností** je povolené v **okně** Vlastnosti nebo na Průzkumník řešení panelu nástrojů pro objekty, které poskytují zobrazení stránky vlastností vybraného objektu. Stránky vlastností jsou vytvořeny prostředím a jsou dostupné pro řešení a projekty. Mohou však být také k dispozici pro položky projektu, které používají vlastnosti závislé na konfiguraci. Tato funkce se může použít, když soubory v projektu vyžadují ke správnému sestavení různá nastavení přepínače kompilátoru.

## <a name="using-property-pages"></a>Použití stránek vlastností
 Pokud je stránka vlastností už zobrazená a výběr se změní (například z řešení na projekt), změní se informace zobrazené na stránkách, aby se zobrazí vlastnosti pro nový výběr. Pokud objekt nepodporuje stránky vlastností, nejsou žádné vlastnosti, je stránka vlastností prázdná.

 Pokud je vybráno více objektů, na stránce vlastností se zobrazí průnik vlastností všech vybraných položek. Pokud vybraná položka neobsahuje vlastnosti závislé  na konfiguraci a kliknete na tlačítko Stránky vlastností na Průzkumník řešení panelu nástrojů, fokus se změní na okno Vlastnosti. Další informace týkající se nastavení a okno Vlastnosti najdete v tématu [Rozšíření vlastností](../../extensibility/internals/extending-properties.md).

 Pokud se vlastnosti zobrazují pro více objektů a změníte hodnotu na stránce vlastností, nastaví se všechny hodnoty pro objekty na novou hodnotu, i když se zpočátku liší a stránka byla při zobrazení vlastností jednotlivých objektů prázdná.

 V systému jsou k dispozici dva obecné typy dialogových oken **ProjectProperty** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Pages. V prvním příkladu se Visual Basic projektů například stránky vlastností zobrazují ve formátu pole, jak je znázorněno na následujícím snímku obrazovky. V druhé části, kterou jsme si ukázali dále v této části, hostuje stránka vlastností mřížku vlastností podobnou mřížce, která se nachází v okně Vlastnosti.

 ![Visual Basic vlastností](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") Dialogové okno Stránky vlastností projektu s formátem pole a stromovou strukturou

 Stromová struktura v dialogovém okně Stránky vlastností není sestavená pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> . Prostředí na základě názvu úrovně předané rozhraním a <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> ho sestaví.

 Na stránkách vlastností jsou k dispozici pouze dvě kategorie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nejvyšší úrovně:

- Společné vlastnosti, které zobrazují informace nezávislé na konfiguraci pro vybraný objekt nebo objekty. V důsledku toho nejsou při výběru jedné z podkategorií Společných vlastností dostupné možnosti Konfigurace, Platforma a Správce konfigurace v horní části dialogového okna.

- Vlastnosti konfigurace, které obsahují informace závislé na konfiguraci související s parametry Ladění, Optimalizace a Sestavení pro řešení nebo projekt.

  Nemůžete vytvořit žádné další kategorie nejvyšší úrovně, ale můžete se rozhodnout nezobrazovat jednu nebo druhou v implementaci `IVsPropertyPage` . Pokud například nemáte žádné vlastnosti nezávislé na konfiguraci k zobrazení pro objekt, můžete se rozhodnout nezobrazovat kategorii Společné vlastnosti. Při implementaci v objektu konfigurace (objekt, který implementuje rozhraní , a související rozhraní) se zobrazí běžné vlastnosti, pokud jsou implementovány z objektu procházení položky a vlastností `ISpecifyPropertyPages` `ISpecifyPropertyPages` `IVsCfg` `IVsProjectCfg` konfigurace.

  Každá kategorie zobrazená v kategorii nejvyšší úrovně představuje samostatnou stránku vlastností. Položky kategorií a podkategorií, které jsou k dispozici v dialogovém okně, jsou určeny implementací a `ISpecifyPropertyPages` `IVsPropertyPage` .

  `IDispatch` Objekty pro položky v kontejneru výběru, které mají vlastnosti, které se mají zobrazit na stránkách vlastností, implementují za účelem vytvoření `ISpecifyPropertyPages` výčtu seznamu ID tříd. ID tříd se předá jako proměnné do a slouží k vytvoření instance `ISpecifyPropertyPages` stránek vlastností. Seznam ID tříd je také předán do k `IVsPropertyPage` vytvoření stromové struktury na levé straně dialogového okna. Stránky vlastností pak předá informace zpět objektu, který implementuje a vyplní `IDispatch` `ISpecifyPropertyPages` informace pro každou stránku.

  Vlastnosti objektu browse se načítá pomocí `IDispatch` pro každý objekt v kontejneru výběru.

  Implementace `Help::DisplayTopicFromF1Keyword` balíčku VSPackage poskytuje funkce pro tlačítko Nápovědy.

  Další informace najdete v knihovně MSDN v části a `IDispatch` `ISpecifyPropertyPages` .

  Druhý typ stránek vlastností zobrazený v ukázky je hostitelem formuláře mřížky vlastností, jak je znázorněno na následujícím snímku obrazovky.

  ![Stránky vlastností VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") Dialogové okno Stránky vlastností s mřížkou vlastností

  Rozhraní `IVSMDPropertyBrowser` a (deklarované v souboru vsmanaged.h) se používají k vytvoření a naplnění mřížky vlastností v `IVSMDPropertyGrid` dialogovém okně nebo okně.

  Architektura projektů se výrazně změnila od minulých verzí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Konkrétně se změnil mysl, který projekt je aktivní. V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] neexistuje žádný koncept aktivního projektu. V předchozích vývojových prostředích byl aktivním projektem, který sestaví a nasadí příkazy bez ohledu na kontext. Řešení teď řídí a určuje, které příkazy sestavení a nasazení se vztahují na které projekty.

  To, co bylo dříve aktivním projektem, je teď zachyceno jedním ze tří různých způsobů:

- Spouštěný projekt

   Projekt nebo projekty můžete zadat ze stránky vlastností řešení, které se spustí, když uživatel stiskne klávesu F5 nebo vybere Spustit v nabídce Sestavení. Funguje to podobným způsobem jako starý aktivní projekt v tom smyslu, že jeho název se zobrazuje Průzkumník řešení tučným písmem.

   Spouštěný projekt můžete načíst jako vlastnost v modelu automatizace voláním `DTE.Solution.SolutionBuild.StartupProjects` . V balíčky VSPackage zavoláte <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> metody nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> . `IVsSolutionBuildManager` je k dispozici jako služba `QueryService` na SID_SVsSolutionBuildManager. Další informace najdete v tématu [Objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md) a Konfigurace [řešení.](../../extensibility/internals/solution-configuration.md)

- Konfigurace sestavení aktivního řešení

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] má aktivní konfiguraci řešení, která je dostupná v modelu automatizace implementací `DTE.Solution.SolutionBuild.ActiveConfiguration` . Konfigurace řešení je kolekce, která obsahuje jednu konfiguraci projektu pro každý projekt v řešení (každý projekt může mít více konfigurací na více platformách s odlišnými názvy). Další informace týkající se stránek vlastností řešení najdete v tématu [Konfigurace řešení.](../../extensibility/internals/solution-configuration.md)

- Aktuálně vybraný projekt

   Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> metodu , která načte vybranou hierarchii projektu a položku projektu nebo položky. Z DTE byste měli použít `SelectedItems.SelectedItem.Project` metody `SelectedItems.SelectedItem.ProjectItem` a . V základních dokumentech je pod těmito nadpisy ukázkový [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kód.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)
- [Objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md)
- [Konfigurace řešení](../../extensibility/internals/solution-configuration.md)
