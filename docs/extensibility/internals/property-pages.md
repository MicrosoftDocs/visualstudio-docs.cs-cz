---
title: Stránky vlastností | Microsoft Docs
description: Přečtěte si o práci se stránkami vlastností pro nový typ projektu v sadě Visual Studio SDK, která umožňuje uživatelům zobrazit a změnit vlastnosti projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dd7d1ce463377daa2800d5c3e635adc71935d9d0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883165"
---
# <a name="property-pages"></a>Stránky vlastností
Uživatelé mohou zobrazit a změnit konfiguraci projektu závislé a nezávislé vlastnosti pomocí stránek vlastností. Tlačítko **stránky vlastností** je povoleno v okně **vlastnosti** nebo na panelu nástrojů Průzkumník řešení pro objekty, které poskytují zobrazení stránky vlastností vybraného objektu. Stránky vlastností jsou vytvořeny prostředím a jsou k dispozici pro řešení a projekty. Mohou však být zpřístupněny také pro položky projektu, které využívají vlastnosti závislé na konfiguraci. Tato funkce může být použita, pokud soubory v projektu vyžadují pro správné sestavení jiné nastavení přepínače kompilátoru.

## <a name="using-property-pages"></a>Použití stránek vlastností
 Pokud se stránka vlastností už zobrazila a výběr se změní (například z řešení na projekt), informace zobrazené na stránkách se změní tak, aby se zobrazily vlastnosti nového výběru. Pokud neexistují žádné vlastnosti objektu, který podporuje stránky vlastností, stránka vlastností je prázdná.

 Je-li vybráno více objektů, stránka vlastností zobrazí průnik vlastností pro všechny vybrané položky. Pokud vybraná položka neobsahuje vlastnosti závislé na konfiguraci a na panelu nástrojů Průzkumník řešení se klikne na tlačítko **stránky vlastností** , fokus se změní na okno Vlastnosti. Další informace týkající se okno Vlastnosti a výběru najdete v tématu [rozšíření vlastností](../../extensibility/internals/extending-properties.md).

 Pokud jsou pro více objektů zobrazeny vlastnosti a změníte hodnotu na stránce vlastností, všechny hodnoty pro objekty jsou nastaveny na novou hodnotu, i když byly původně odlišné a při zobrazení vlastností jednotlivých objektů byla stránka prázdná.

 V systému jsou k dispozici dva obecné typy dialogových oken **stránky ProjectProperty** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . V prvním případě Visual Basic projekty například stránky vlastností se zobrazují pomocí formátu pole, jak je znázorněno na následujícím snímku obrazovky. V druhé, jak je uvedeno dále v této části, stránka vlastností hostuje mřížku vlastností podobným způsobem, který najdete v okně Vlastnosti.

 ![Stránky vlastností Visual Basic](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") Dialogové okno stránky vlastností projektu se formátem pole a stromovou strukturou

 Stromová struktura v dialogovém okně stránky vlastností není sestavena pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> . Prostředí je na základě názvu úrovně předaného <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> rozhraním a rozhraním sestavením.

 Na stránkách vlastností jsou k dispozici pouze dvě kategorie nejvyšší úrovně [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] :

- Společné vlastnosti, které zobrazují informace nezávislé na konfiguraci pro vybraný objekt nebo objekty. Výsledkem je, že když je vybraná jedna z kategorií společných vlastností, možnosti konfigurace, platformy a Configuration Manager v horní části dialogového okna nejsou k dispozici.

- Vlastnosti konfigurace, které obsahují informace závislé na konfiguraci týkající se ladění, optimalizace a parametrů sestavení pro řešení nebo projekt.

  Nemůžete vytvořit žádné další kategorie nejvyšší úrovně, ale můžete zvolit, aby se nezobrazovala jedna nebo druhá v implementaci `IVsPropertyPage` . Pokud například nemáte žádné vlastnosti nezávislé na konfiguraci pro zobrazení objektu, můžete zvolit možnost nezobrazit kategorii společné vlastnosti. Společné vlastnosti se zobrazí, pokud `ISpecifyPropertyPages` je implementováno z objektu procházení a vlastností konfigurace při implementaci `ISpecifyPropertyPages` v objektu konfigurace (objekt implementující `IVsCfg` , `IVsProjectCfg` a souvisejících rozhraních).

  Každá kategorie zobrazená v kategorii nejvyšší úrovně představuje samostatnou stránku vlastností. Položky kategorie a podkategorie dostupné v dialogovém okně jsou určeny vaší implementací `ISpecifyPropertyPages` a `IVsPropertyPage` .

  `IDispatch` objekty pro položky v kontejneru výběru, které mají vlastnosti, které mají být zobrazeny na stránkách vlastností, jsou implementovány `ISpecifyPropertyPages` pro vytvoření výčtu seznamu ID tříd. ID třídy se předávají jako proměnné do `ISpecifyPropertyPages` a slouží k vytvoření instance stránek vlastností. Seznam identifikátorů třídy je také předán k `IVsPropertyPage` Vytvoření stromové struktury na levé straně dialogového okna. Stránky vlastností pak předají informace zpět do `IDispatch` objektu, který implementuje `ISpecifyPropertyPages` a vyplní informace pro každou stránku.

  Vlastnosti objektu procházení jsou načteny pomocí `IDispatch` pro každý objekt v kontejneru výběru.

  Implementace `Help::DisplayTopicFromF1Keyword` v balíčku VSPackage poskytuje funkce pro tlačítko Help.

  Další informace najdete v tématech `IDispatch` a `ISpecifyPropertyPages` v knihovně MSDN.

  Druhý typ stránek vlastností zobrazených v ukázkách hostuje formu mřížky vlastností, jak je znázorněno na následujícím snímku obrazovky.

  ![Stránky vlastností VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") Dialogové okno stránky vlastností s mřížkou vlastností

  Rozhraní `IVSMDPropertyBrowser` a `IVSMDPropertyGrid` (deklarované v vsmanaged. h) slouží k vytvoření a naplnění mřížky vlastností v dialogovém okně nebo okně.

  Architektura projektů se podstatně změnila z minulých verzí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Zejména pojem, který projekt aktivní, se změnil. V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] systému neexistuje koncept aktivního projektu. V předchozích vývojových prostředích byl aktivní projekt projekt, který příkazy sestavení a nasazení budou mít výchozí hodnotu bez ohledu na kontext. Nyní ovládací prvky řešení a arbitrates, které příkazy sestavení a nasazení platí pro které projekty.

  Dříve byl aktivní projekt zachycen jedním ze tří různých způsobů:

- Spouštěný projekt

   Projekt nebo projekty můžete zadat na stránce vlastností řešení, která se spustí, když uživatel stiskne klávesu F5 nebo vybere možnost spustit z nabídky sestavit. Funguje způsobem podobným původnímu aktivnímu projektu v tom smyslu, že se jeho název zobrazuje v Průzkumník řešení s tučným písmem.

   Můžete načíst spouštěcí projekt jako vlastnost v modelu automatizace voláním `DTE.Solution.SolutionBuild.StartupProjects` . V VSPackage zavoláte <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> metody nebo. `IVsSolutionBuildManager` je k dispozici jako služba `QueryService` v SID_SVsSolutionBuildManager. Další informace najdete v [tématu Konfigurace a](../../extensibility/internals/solution-configuration.md) [objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md) .

- Konfigurace sestavení aktivních řešení

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] má aktivní konfiguraci řešení, která je k dispozici v modelu automatizace implementací `DTE.Solution.SolutionBuild.ActiveConfiguration` . Konfigurace řešení je kolekce, která obsahuje jednu konfiguraci projektu pro každý projekt v řešení (každý projekt může mít více konfigurací, na více platformách s odlišnými názvy). Další informace o stránkách vlastností řešení najdete v tématu věnovaném [konfiguraci řešení](../../extensibility/internals/solution-configuration.md).

- Aktuálně vybraný projekt

   Implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> metody načtěte hierarchii projektu a položku projektu nebo vybrané položky. Z DTE byste použili `SelectedItems.SelectedItem.Project` `SelectedItems.SelectedItem.ProjectItem` metody a. V těchto hlavičkách základních dokumentů je ukázkový kód [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)
- [Objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md)
- [Konfigurace řešení](../../extensibility/internals/solution-configuration.md)
