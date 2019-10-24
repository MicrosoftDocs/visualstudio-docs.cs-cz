---
title: Objekt konfigurace projektu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e3321b70b51d194c67f1deee8ed33e240762b16b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725842"
---
# <a name="project-configuration-object"></a>Objekt konfigurace projektu
Objekt konfigurace projektu spravuje zobrazení informací o konfiguraci uživatelského rozhraní.

 ![Konfigurace projektu sady Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") Stránky vlastností konfigurace projektu

 Poskytovatel konfigurace projektu spravuje konfigurace projektu. Prostředí a další balíčky, pokud chcete získat přístup k informacím o konfiguracích projektu a načíst je, zavolejte rozhraní připojená k objektu poskytovatele konfigurace projektu.

> [!NOTE]
> Konfigurační soubory řešení nelze vytvořit nebo upravit programově. Je nutné použít `DTE.SolutionBuilder`. Další informace najdete v tématu [Konfigurace řešení](../../extensibility/internals/solution-configuration.md) .

 Chcete-li publikovat zobrazovaný název, který se má použít v uživatelském rozhraní konfigurace, projekt by měl implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, které vrátí seznam ukazatelů `IVsCfg`, které můžete použít k získání zobrazovaných názvů pro informace o konfiguraci a platformě, které se mají uvést v uživatelském rozhraní prostředí. Aktivní konfigurace a platforma jsou určeny konfigurací projektu uloženou v aktivní konfiguraci řešení. Metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> lze použít k načtení aktivní konfigurace projektu.

 Objekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> lze volitelně implementovat do objektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> s objektem <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper>, který umožňuje načíst objekt `IVsProjectCfg2` na základě názvu kanonické konfigurace projektu.

 Dalším způsobem, jak poskytnout prostředí a další projekty s přístupem ke konfiguracím projektu, je pro projekty, které poskytují implementaci `IVsCfgProvider2::GetCfgs` metody pro vrácení jednoho nebo více objektů konfigurace. Projekty mohou také implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, které dědí z `IVsProjectCfg` a tak z `IVsCfg`, aby poskytovaly informace specifické pro konfiguraci. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> podporuje platformy a funkce pro přidávání, odstraňování a přejmenování konfigurací projektu.

> [!NOTE]
> Vzhledem k tomu, že Visual Studio již není omezeno na dva typy konfigurace, kód, který zpracovává konfigurace, by neměl být vytvořen pomocí předpokladů o počtu konfigurací, ani by neměl být vytvořen s předpokladem, že projekt má pouze jeden konfigurace je nutně buď ladit, nebo v maloobchodě. To umožňuje použití <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> zastaralých.

 Volání `QueryInterface` objektu vráceného z `IVsGetCfgProvider::GetCfgProvider` načítá `IVsCfgProvider2`. Pokud `IVsGetCfgProvider` nebyl nalezen voláním `QueryInterface` v objektu `IVsProject3` projektu, můžete získat přístup k objektu poskytovatele konfigurace voláním `QueryInterface` na objektu kořenového prohlížeče hierarchie pro objekt vrácený pro `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)` nebo prostřednictvím ukazatele na konfiguraci. Zprostředkovatel byl vrácen pro `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.

 `IVsProjectCfg2` primárně poskytuje přístup k objektům pro správu sestavování, ladění a nasazení a umožňuje projektům volnost v seskupení výstupů. Metody `IVsProjectCfg` a `IVsProjectCfg2` lze použít k implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> pro správu procesu sestavení a <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> ukazatelů pro výstupní skupiny konfigurace.

 Projekt musí vracet stejný počet skupin pro každou konfiguraci, kterou podporuje, i když se počet výstupů obsažených v rámci skupiny může lišit od konfigurace ke konfiguraci. Skupiny musí mít také stejné informace o identifikátoru (kanonický název, zobrazovaný název a informace o skupině) od konfigurace po konfiguraci v rámci projektu. Další informace najdete v tématu [konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md).

 Aby bylo možné ladění povolit, vaše konfigurace by měly implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>. `IVsDebuggableProjectCfg` je volitelné rozhraní implementované projekty, které umožňuje ladicímu programu spustit konfiguraci a je implementováno na objekt konfigurace pomocí `IVsCfg` a `IVsProjectCfg`. Prostředí je volá, když se uživatel rozhodne spustit ladicí program stisknutím klávesy F5.

 `ISpecifyPropertyPages` a `IDispatch` se používají ve spojení se stránkami vlastností k načtení a zobrazení informací závislých na konfiguraci uživateli. Další informace najdete v tématu [stránky vlastností](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Viz také:
- [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurace projektu pro sestavení](../../extensibility/internals/project-configuration-for-building.md)
- [Konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md)
- [Stránky vlastností](../../extensibility/internals/property-pages.md)
- [Konfigurace řešení](../../extensibility/internals/solution-configuration.md)