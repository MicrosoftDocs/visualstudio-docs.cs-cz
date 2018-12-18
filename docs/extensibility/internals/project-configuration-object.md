---
title: Objekt konfigurace projektu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7385a5f7768a57fd1a3d9688df152fd60a1ea130
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136026"
---
# <a name="project-configuration-object"></a>Objekt konfigurace projektu
Objekt konfigurace projektu spravuje zobrazení informací o konfiguraci na rozhraní.  
  
 ![Konfigurace projektu Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
Stránky vlastností konfigurace projektu  
  
 Poskytovatel konfigurace projektu spravuje konfigurace projektu. Prostředí a další balíčky, k získání přístupu k a načíst informace o konfigurace projektu, volání rozhraní připojený k objektu zprostředkovatele konfigurace projektu.  
  
> [!NOTE]
>  Nelze vytvořit nebo upravit konfigurační soubory řešení prostřednictvím kódu programu. Je nutné použít `DTE.SolutionBuilder`. V tématu [konfigurace řešení](../../extensibility/internals/solution-configuration.md) Další informace.  
  
 Pokud chcete publikovat zobrazovaný název, který se má použít v konfiguraci uživatelského rozhraní, by měla implementovat projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. Volání prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, který vrátí seznam hodnot `IVsCfg` ukazatele, které můžete použít pro získání zobrazovaných názvů pro informace o konfiguraci a platformě uveden v uživatelském rozhraní v prostředí. Konfigurace projektu, které jsou uložené v aktivním řešení konfigurace jsou určeny aktivní konfigurace a platformy. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> Metoda slouží k načtení konfigurace aktivního projektu.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> Objektu může být implementováno volitelně na <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> objektu s <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> objektu a umožní vám načíst `IVsProjectCfg2` objektu podle názvu konfigurace kanonický projektu.  
  
 Je také možné poskytnout přístup k konfigurace projektu prostředí a další projekty pro projekty tak, aby zadejte implementaci `IVsCfgProvider2::GetCfgs` metoda vrátí jeden nebo více objektů konfigurace. Může také implementovat projektů <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, který dědí z `IVsProjectCfg` a tím z `IVsCfg`, poskytovat informace specifické pro konfiguraci. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> podporuje platformy a funkce pro přidání, odstranění a přejmenování konfigurace projektu.  
  
> [!NOTE]
>  Vzhledem k tomu, že Visual Studio je již omezena na dva typy konfigurace, kód, který zpracovává konfigurace nemá zapisovat s předpoklady o zadaný počet konfigurací ani ho budou zasílány s předpokladem, který projekt, který obsahuje pouze jednu konfigurace je nutně ladění nebo maloobchodní verze. Díky použití <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> zastaralé.  
  
 Volání metody `QueryInterface` pro objekt vrácený z`IVsGetCfgProvider::GetCfgProvider` načte `IVsCfgProvider2`. Pokud `IVsGetCfgProvider` nebyl nalezen voláním `QueryInterface` na `IVsProject3` objektu projektu, se zobrazí objekt zprostředkovatele konfigurace po volání metody `QueryInterface` na objekt hierarchie kořenové prohlížeče pro objekt vrácený pro `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`, nebo pomocí ukazatel na poskytovatel konfigurace pro vrátit `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.  
  
 `IVsProjectCfg2` především poskytuje přístup k sestavení, ladění a objekty pro správu nasazení a umožňuje projekty volného výstupy skupiny. Metody `IVsProjectCfg` a `IVsProjectCfg2` lze použít k implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> ke správě procesu sestavení a <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> ukazatele pro skupiny výstupu konfigurace.  
  
 Projekt musí vrátit stejný počet skupin pro každé konfiguraci, kterou podporuje i v případě, že počet výstupů obsažena ve skupině se může lišit od konfigurace. Skupiny musí také mít stejný identifikátor informace (název v kanonickém tvaru, zobrazovaný název a informace skupiny) z konfigurace v rámci projektu. Další informace najdete v tématu [konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md).  
  
 Pokud chcete povolit ladění, by měla implementovat vaše konfigurace <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>. `IVsDebuggableProjectCfg` je volitelné rozhraní implementované projekty umožňující ladicí program ke spuštění konfigurace a se implementuje na objekt konfigurace s `IVsCfg` a `IVsProjectCfg`. Prostředí nazve je, pokud se uživatel rozhodne spuštění ladicího programu stisknutím klávesy F5.  
  
 `ISpecifyPropertyPages` a `IDispatch` se používají ve spojení s použitím stránek vlastností načíst a zobrazit informace závislá na konfiguraci pro uživatele. Další informace najdete v tématu [stránky vlastností](../../extensibility/internals/property-pages.md).  
  
## <a name="see-also"></a>Viz také  
 [Správa možnosti konfigurace](../../extensibility/internals/managing-configuration-options.md)   
 [Konfigurace projektu pro vytváření](../../extensibility/internals/project-configuration-for-building.md)   
 [Konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md)   
 [Stránky vlastností](../../extensibility/internals/property-pages.md)   
 [Konfigurace řešení](../../extensibility/internals/solution-configuration.md)