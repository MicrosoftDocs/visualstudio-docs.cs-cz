---
title: Objekt konfigurace projektu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 001509b56e3bac6a8fd585eb0efe0bd57018acea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706660"
---
# <a name="project-configuration-object"></a>Objekt konfigurace projektu
Objekt konfigurace projektu spravuje zobrazení informací o konfiguraci do hlavního nastavení.

 ![Konfigurace projektu visual studia](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") Stránky vlastností konfigurace projektu

 Zprostředkovatel konfigurace projektu spravuje konfigurace projektu. Prostředí a další balíčky, chcete-li získat přístup a načíst informace o konfiguraci projektu, volejte rozhraní připojená k objektu zprostředkovatele konfigurace projektu.

> [!NOTE]
> Konfigurační soubory řešení nelze vytvářet ani upravovat programově. Je nutné `DTE.SolutionBuilder`použít . Další informace naleznete v [tématu Konfigurace řešení.](../../extensibility/internals/solution-configuration.md)

 Chcete-li publikovat zobrazovaný název, který má být <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>použit v uživatelském uživatelském nastavení konfigurace, projekt by měl implementovat . Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, který vrátí `IVsCfg` seznam ukazatelů, které můžete použít k získání zobrazované názvy pro informace konfigurace a platformy, které mají být uvedeny v prostředí uj. Aktivní konfigurace a platforma jsou určeny konfigurací projektu uloženou v konfiguraci aktivního řešení. Metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> lze použít k načtení konfigurace aktivního projektu.

 Objekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> může být volitelně <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> implementován <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> na objekt s `IVsProjectCfg2` objektem, který vám umožní načíst objekt na základě názvu konfigurace kanonického projektu.

 Dalším způsobem, jak poskytnout prostředí a dalším projektům přístup ke konfiguracím projektu, je pro projekty, které poskytují implementaci `IVsCfgProvider2::GetCfgs` metody pro vrácení jednoho nebo více objektů konfigurace. Projekty mohou <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>také implementovat `IVsProjectCfg` , který `IVsCfg`dědí od a tím i od , poskytovat informace specifické pro konfiguraci. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>podporuje platformy a funkce pro přidávání, mazání a přejmenování konfigurace projektu.

> [!NOTE]
> Vzhledem k tomu, že Visual Studio již není omezena na dva typy konfigurace, kód, který zpracovává konfigurace by neměl být zapsán s předpoklady o počtu konfigurací, ani by měl být zapsán s předpokladem, že projekt, který má pouze jednu konfiguraci je nutně ladění nebo maloobchod. To umožňuje použití <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> a zastaralé.

 Volání `QueryInterface` na objekt`IVsGetCfgProvider::GetCfgProvider` vrácené `IVsCfgProvider2`z načte . Pokud `IVsGetCfgProvider` není nalezen `QueryInterface` voláním `IVsProject3` objektu projektu, můžete získat přístup `QueryInterface` k objektu zprostředkovatele konfigurace `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`voláním objektu kořenového prohlížeče `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`hierarchie pro objekt vrácený pro aplikaci nebo ukazatelem na zprostředkovatele konfigurace vráceného pro .

 `IVsProjectCfg2`především poskytuje přístup k objektům správy sestavení, ladění a nasazení a umožňuje projektům svobodu seskupit výstupy. Metody `IVsProjectCfg` a `IVsProjectCfg2` lze použít k <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> implementaci ke správě <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> procesu sestavení a ukazatele pro výstupní skupiny konfigurace.

 Projekt musí vrátit stejný počet skupin pro každou konfiguraci, kterou podporuje, i když počet výstupů obsažených ve skupině se může lišit od konfigurace ke konfiguraci. Skupiny musí mít také stejné informace o identifikátoru (kanonický název, zobrazovaný název a informace o skupině) od konfigurace až po konfiguraci v rámci projektu. Další informace naleznete v [tématu Konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md).

 Chcete-li povolit ladění, konfigurace <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>by měly implementovat . `IVsDebuggableProjectCfg`je volitelné rozhraní implementované projekty, které umožňuje ladicímu programu spustit `IVsCfg` `IVsProjectCfg`konfiguraci a je implementováno na objektkonfigurace s a . Prostředí volá, když se uživatel rozhodne spustit ladicí program stisknutím klávesy F5.

 `ISpecifyPropertyPages`a `IDispatch` používají se ve spojení se stránkami vlastností k načtení a zobrazení informací závislých na konfiguraci uživateli. Další informace naleznete v [tématu Stránky vlastností](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Viz také
- [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurace projektu pro sestavení](../../extensibility/internals/project-configuration-for-building.md)
- [Konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md)
- [Stránky vlastností](../../extensibility/internals/property-pages.md)
- [Konfigurace řešení](../../extensibility/internals/solution-configuration.md)
