---
title: Objekt konfigurace projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 32e4d34ec3d1fbe8753b4185cab76caa77038bd1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64820309"
---
# <a name="project-configuration-object"></a>Objekt konfigurace projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Objekt konfigurace projektu spravuje zobrazení informací o konfiguraci uživatelského rozhraní.  
  
 ![Konfigurace projektu sady Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
Stránky vlastností konfigurace projektu  
  
 Poskytovatel konfigurace projektu spravuje konfigurace projektu. Prostředí a další balíčky, pokud chcete získat přístup k informacím o konfiguracích projektu a načíst je, zavolejte rozhraní připojená k objektu poskytovatele konfigurace projektu.  
  
> [!NOTE]
> Konfigurační soubory řešení nelze vytvořit nebo upravit programově. Je nutné použít `DTE.SolutionBuilder` . Další informace najdete v tématu [Konfigurace řešení](../../extensibility/internals/solution-configuration.md) .  
  
 K publikování zobrazovaného názvu, který se má použít v uživatelském rozhraní konfigurace, by měl projekt implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A> . Volání prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> , která vrací seznam `IVsCfg` ukazatelů, které lze použít k získání zobrazovaných názvů pro informace o konfiguraci a platformě, které budou uvedeny v uživatelském rozhraní prostředí. Aktivní konfigurace a platforma jsou určeny konfigurací projektu uloženou v aktivní konfiguraci řešení. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>Metodu lze použít k načtení aktivní konfigurace projektu.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>Objekt může být volitelně implementován pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> objekt s <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> objektem, který umožňuje načíst `IVsProjectCfg2` objekt na základě kanonického názvu konfigurace projektu.  
  
 Dalším způsobem, jak poskytnout prostředí a další projekty s přístupem ke konfiguracím projektu, je pro projekty, které poskytují implementaci `IVsCfgProvider2::GetCfgs` metody pro vrácení jednoho nebo více objektů konfigurace. Projekty mohou také implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> , které dědí z `IVsProjectCfg` a tak z `IVsCfg` , aby poskytovaly informace specifické pro konfiguraci. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> podporuje platformy a funkce pro přidávání, odstraňování a přejmenování konfigurací projektu.  
  
> [!NOTE]
> Vzhledem k tomu, že Visual Studio již není omezeno na dva typy konfigurace, kód, který zpracovává konfigurace, by neměl být napsán s předpoklady o počtu konfigurací, ani by neměl být vytvořen s předpokladem, že projekt, který má pouze jednu konfiguraci, je nutně buď ladit, nebo maloobchodní. To umožňuje použití <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> zastaralé.  
  
 Volání `QueryInterface` objektu vráceného z `IVsGetCfgProvider::GetCfgProvider` načtení `IVsCfgProvider2` . Pokud `IVsGetCfgProvider` se nenalezne voláním `QueryInterface` `IVsProject3` objektu projektu, můžete získat přístup k objektu poskytovatele konfigurace voláním `QueryInterface` na objekt kořenového prohlížeče hierarchie pro objekt, který se vrátil pro `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)` , nebo prostřednictvím ukazatele na poskytovatele konfigurace vráceného pro `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)` .  
  
 `IVsProjectCfg2` primárně poskytuje přístup k objektům pro správu sestavení, ladění a nasazení a umožňuje projektům volnost v seskupení výstupů. Metody `IVsProjectCfg` a `IVsProjectCfg2` lze použít k implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> ke správě procesu sestavení a <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> ukazatelů pro výstupní skupiny konfigurace.  
  
 Projekt musí vracet stejný počet skupin pro každou konfiguraci, kterou podporuje, i když se počet výstupů obsažených v rámci skupiny může lišit od konfigurace ke konfiguraci. Skupiny musí mít také stejné informace o identifikátoru (kanonický název, zobrazovaný název a informace o skupině) od konfigurace po konfiguraci v rámci projektu. Další informace najdete v tématu [konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md).  
  
 Aby bylo možné ladění povolit, vaše konfigurace by měly implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> . `IVsDebuggableProjectCfg` je volitelné rozhraní implementované projekty, které umožňuje ladicímu programu spustit konfiguraci a je implementováno na objektu konfigurace pomocí `IVsCfg` a `IVsProjectCfg` . Prostředí je volá, když se uživatel rozhodne spustit ladicí program stisknutím klávesy F5.  
  
 `ISpecifyPropertyPages` a `IDispatch` se používají ve spojení se stránkami vlastností k načtení a zobrazení informací o konfiguraci, které jsou závislé na uživateli. Další informace najdete v tématu [stránky vlastností](../../extensibility/internals/property-pages.md).  
  
## <a name="see-also"></a>Viz také  
 [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)   
 [Konfigurace projektu pro sestavení](../../extensibility/internals/project-configuration-for-building.md)   
 [Konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md)   
 [Stránky vlastností](../../extensibility/internals/property-pages.md)   
 [Konfigurace řešení](../../extensibility/internals/solution-configuration.md)
