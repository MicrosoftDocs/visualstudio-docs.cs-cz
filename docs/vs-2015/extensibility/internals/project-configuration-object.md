---
title: Objekt konfigurace projektu | Dokumentace Microsoftu
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
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 27b64e6b11e6a8d01cd06886d902c8032f8605d2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735281"
---
# <a name="project-configuration-object"></a>Objekt konfigurace projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Objekt konfigurace projektu spravuje zobrazení informací o konfiguraci v uživatelském rozhraní.  
  
 ![Konfigurace projektu Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
Stránky vlastností konfigurace projektu  
  
 Zprostředkovatel konfigurace projektu slouží ke správě konfigurace projektu. Prostředí a další balíčky, k získání přístupu k načtení informací o konfiguraci projektu, volání rozhraní připojené k objektu zprostředkovatele konfigurace projektu.  
  
> [!NOTE]
>  Nejde vytvořit nebo upravit konfigurační soubory řešení prostřednictvím kódu programu. Je nutné použít `DTE.SolutionBuilder`. Zobrazit [konfigurace řešení](../../extensibility/internals/solution-configuration.md) Další informace.  
  
 K publikování zobrazovaný název, který se má použít v konfiguraci, uživatelského rozhraní, by měly implementovat projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, který vrátí seznam hodnot `IVsCfg` ukazatele, které vám umožní získat zobrazované názvy pro konfigurace a platforma informace uvedené v Uživatelském prostředí. Aktivní konfigurace a platforma jsou určeny v konfiguraci aktivního řešení uložit konfiguraci projektu. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> Metodu je možné načíst aktivní konfiguraci projektu.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> Objektu je volitelně možné implementovat na <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> objektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> objektu a umožňuje tak načíst `IVsProjectCfg2` objektu podle název konfigurace projektu canonical.  
  
 Je další způsob, jak poskytnout přístup k projektu konfigurace prostředí a jiné projekty pro projekty poskytnout implementaci položky `IVsCfgProvider2::GetCfgs` metoda vrátí jeden nebo více objektů konfigurace. Projekty mohou také implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, který dědí z `IVsProjectCfg` a tím z `IVsCfg`, poskytnout informace specifické pro konfiguraci. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> podporuje platformy a funkce pro přidání, odstranění a přejmenování konfigurace projektu.  
  
> [!NOTE]
>  Vzhledem k tomu, že Visual Studio už není omezené na dva typy konfigurace, neměl by být zapsaný kód, který zpracovává konfigurace s předpoklady o počet konfigurací ani by měly být za předpokladu zapsány, který projekt, který obsahuje pouze jednu konfigurace je nutně ladění nebo maloobchodního prodeje. Díky použití <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> zastaralé.  
  
 Volání `QueryInterface` objekt vrácený z`IVsGetCfgProvider::GetCfgProvider` načte `IVsCfgProvider2`. Pokud `IVsGetCfgProvider` nebyl nalezen voláním `QueryInterface` na `IVsProject3` objektu projektu, můžete přístup k objektu zprostředkovatele konfigurace voláním `QueryInterface` v prohlížeči hierarchie kořenového objektu pro objekt vrácený pro `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`, nebo prostřednictvím ukazatel na poskytovatele konfigurace pro `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.  
  
 `IVsProjectCfg2` především poskytuje přístup k sestavení, ladění a nasazení správy objektů a umožňuje projekty volného výstupy skupiny. Metody `IVsProjectCfg` a `IVsProjectCfg2` lze použít k implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> ke správě procesu sestavení a <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> ukazatele pro skupiny výstupu konfigurace.  
  
 Projekt musí vracet stejný počet skupin pro každou konfiguraci, která podporuje i v případě, že počet výstupů obsažena ve skupině, které se mohou lišit od konfigurace. Skupiny musí mít také stejný identifikátor informace (název v kanonickém tvaru, zobrazovaný název a informace o skupinách) z konfigurace v rámci projektu. Další informace najdete v tématu [konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md).  
  
 Pokud chcete povolit ladění, by měly implementovat vaše konfigurace <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>. `IVsDebuggableProjectCfg` je volitelný rozhraní implementovaných projekty povolit ladicí program ke spuštění na konfiguraci a se implementuje na objekt konfigurace s `IVsCfg` a `IVsProjectCfg`. Prostředí volá se, když se uživatel rozhodne stisknutím klávesy F5 spusťte ladicí program.  
  
 `ISpecifyPropertyPages` a `IDispatch` se používají ve spojení s použitím stránek vlastností načíst a zobrazit závislé na konfiguraci informace pro uživatele. Další informace najdete v tématu [stránky vlastností](../../extensibility/internals/property-pages.md).  
  
## <a name="see-also"></a>Viz také  
 [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)   
 [Konfigurace projektu pro sestavení](../../extensibility/internals/project-configuration-for-building.md)   
 [Konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md)   
 [Stránky vlastností](../../extensibility/internals/property-pages.md)   
 [Konfigurace řešení](../../extensibility/internals/solution-configuration.md)

