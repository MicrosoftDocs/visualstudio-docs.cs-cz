---
title: Stránky vlastností | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 74da0df2939b08615f3a659dfca70b1cea0e495d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759863"
---
# <a name="property-pages"></a>Stránky vlastností
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Uživatelé mohou zobrazit a změnit závislé na konfiguraci a - nezávisle vlastnosti projektu pomocí stránky vlastností. A **stránky vlastností** tlačítko je dostupné v **vlastnosti** okně nebo na panelu nástrojů Průzkumník řešení pro objekty, které poskytují zobrazení stránky vlastností vybraného objektu. Stránky vlastností jsou vytvořeny pomocí prostředí a jsou k dispozici pro projekty a řešení. Může, ale také být k dispozici pro položky projektu, které používají závislé na konfiguraci vlastností. Tato funkce mohou být použity, pokud soubory v rámci projektu vyžadují různé přepínače kompilátor správně sestavila.  
  
## <a name="using-property-pages"></a>Použití stránek vlastností  
 Pokud už se zobrazí stránku vlastností a změní výběr (např. z řešení do projektu), informace zobrazí na stránkách se změny zobrazily vlastnosti pro nový výběr. Pokud nejsou žádné vlastnosti v objektu, které podporují stránky vlastností, na stránce vlastností je prázdná.  
  
 Pokud je vybraných víc objektů, zobrazí na stránce vlastností je určena průsečíkem vlastnosti pro všechny vybrané položky. Pokud vybraná položka neobsahuje závislé na konfiguraci vlastností a **stránky vlastností** po kliknutí na tlačítko na panelu nástrojů Průzkumníka řešení, změně fokusu v okně Vlastnosti. Další informace týkající se do okna vlastností a výběr najdete v tématu [vlastnosti rozšíření](../../extensibility/internals/extending-properties.md).  
  
 Pokud se zobrazí vlastnosti pro více objektů a změnit hodnotu na stránce vlastností, všechny hodnoty pro objekty jsou nastaveny na novou hodnotu i v případě, že byl zpočátku různých a na stránce byl prázdný, když se zobrazovaly vlastnosti jednotlivého objektu.  
  
 Existují dva hlavní typy **ProjectProperty stránky** dialogová okna k dispozici v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. V prvním pro projekty jazyka Visual Basic například stránky vlastností se zobrazí pole formátu, jak je znázorněno na následujícím snímku obrazovky. Ve druhém uvedena dále v této části, vlastnost stránky hostitelé mřížku vlastností podobný tomu najdete v okně Vlastnosti.  
  
 ![Stránky vlastností jazyka Visual Basic](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
Dialogové okno stránky vlastností projektu s pole formátu a stromové struktury  
  
 Stromové struktury v dialogovém okně stránky vlastností není vyvíjené <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. Prostředí, podle názvu úrovně předat ji <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> rozhraní, vytvoří se.  
  
 K dispozici pouze dvě kategorie nejvyšší úrovně na [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] stránky vlastností:  
  
- Společná nastavení, které zobrazuje informace o nezávislé na konfiguraci pro vybraný objekt nebo objekty. V důsledku toho pokud je vybrána jedna společná nastavení podkategorie, možnosti konfigurace, platformy a nástroje Configuration Manager v horní části dialogového okna nejsou k dispozici.  
  
- Vlastnosti konfigurace, který obsahuje informace o závislé na konfiguraci s parametry sestavení, ladění a optimalizace pro řešení nebo projektu.  
  
  Nelze vytvořit žádné další kategorie nejvyšší úrovně, ale nechcete zobrazit jeden z nich ve vaší implementaci můžete `IVsPropertyPage`. Pokud například nemáte žádné vlastnosti nezávislé na konfiguraci pro zobrazení objektu, můžete nechcete zobrazit společná nastavení kategorie. Zobrazit společná nastavení, pokud `ISpecifyPropertyPages` je implementována z objektu položky Procházet a vlastnosti konfigurace, Pokud implementujete `ISpecifyPropertyPages` v konfigurační objekt (objekt implementace `IVsCfg`, `IVsProjectCfg`a související rozhraní).  
  
  Každá kategorie zobrazeným pod kategorií nejvyšší úrovně představuje stránku samostatné vlastnost. Kategorie a podkategorie položky k dispozici v dialogovém okně se určují podle vaší implementace `ISpecifyPropertyPages` a `IVsPropertyPage`.  
  
  `IDispatch` objekty pro položky v zásobník pro výběr, které mají vlastnosti, který se má zobrazit na implementace stránky vlastností `ISpecifyPropertyPages` výčet seznam ID tříd. ID třídy jsou předány jako proměnné `ISpecifyPropertyPages` a slouží k vytvoření instance na stránkách vlastností. Seznam ID třídy je předán také `IVsPropertyPage` vytvořit strukturu stromu na levé straně dialogového okna. Stránky vlastností pak předejte informace zpět `IDispatch` objekt, který implementuje `ISpecifyPropertyPages` a vyplní informace pro každou stránku.  
  
  Vlastnosti objektu procházení se načítají pomocí `IDispatch` pro každý objekt v zásobník pro výběr.  
  
  Implementace `Help::DisplayTopicFromF1Keyword` ve vaší VSPackage poskytuje funkce pro tlačítko Nápověda.  
  
  Další informace najdete v tématu `IDispatch` a `ISpecifyPropertyPages`v knihovně MSDN.  
  
  Druhého typu stránky vlastností zobrazí hostitelů ukázky formuláře mřížky vlastností, jak je znázorněno na následujícím snímku obrazovky.  
  
  ![VC určeno stránky](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
  Dialogové okno stránky vlastností pomocí mřížky vlastností  
  
  Rozhraní `IVSMDPropertyBrowser` a `IVSMDPropertyGrid` (deklarované v vsmanaged.h) slouží k vytvoření a naplnění mřížky vlastností v rámci dialogového okna nebo okno.  
  
  Architektura projekty podstatně změnila od minulých verzí nástroje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Zejména je aktivní pojem kterého projektu se změnil. V [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], neexistuje žádný koncept aktivního projektu. V předchozím vývojových prostředích aktivní projekt je projekt, který sestavovat a nasazovat příkazy by ve výchozím nastavení bez ohledu na kontextu. Nyní, řešení ovládací prvky a řeší, která sestavení a nasazení příkazy platí pro projekty, které.  
  
  Co byla dříve aktivní projekt je nyní zaznamenána v jednom ze tří způsobů:  
  
- Spouštěný projekt  
  
   Můžete zadat projekt nebo projekty z řešení vlastností, který bude spuštěn, když uživatel stiskne klávesu F5 nebo vybere spuštění v nabídce sestavení. Toto funguje ve staré aktivní projekt v tom smyslu, že její název se zobrazí v Průzkumníku řešení tučné písmo s podobným způsobem.  
  
   Projekt po spuštění můžete načíst jako vlastnost v modelu automatizace voláním `DTE.Solution.SolutionBuild.StartupProjects`. V sadě VSPackage zavoláte <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> metody. `IVsSolutionBuildManager` je dostupný jako služba ve `QueryService` na SID_SVsSolutionBuildManager. Další informace najdete v tématu [objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md) a [konfigurace řešení](../../extensibility/internals/solution-configuration.md).  
  
- Konfigurace aktivního řešení sestavení  
  
   [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] má konfiguraci aktivního řešení, k dispozici v modelu automatizace implementací `DTE.Solution.SolutionBuild.ActiveConfiguration`. Konfigurace řešení je kolekce, která obsahuje jednu konfiguraci projektu pro každý projekt v řešení (každý projekt může mít více konfigurací na více platforem s odlišnými názvy). Další informace týkající se stránky vlastností tohoto řešení najdete v tématu [konfigurace řešení](../../extensibility/internals/solution-configuration.md).  
  
- Aktuálně vybraný projekt  
  
   Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> metodu pro načtení hierarchie projektu a položky projektu nebo vybraných položek. Z DTE, můžete využít `SelectedItems.SelectedItem.Project` a `SelectedItems.SelectedItem.ProjectItem` metody. Zde je ukázkový kód v rámci těchto položek v samotném [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dokumenty.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)   
 [Objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md)   
 [Konfigurace řešení](../../extensibility/internals/solution-configuration.md)

