---
title: Rozhraní API se odebrala v aplikaci Visual Studio 2022 Preview.
description: Přečtěte si o rozhraních API sady VS SDK odebraných v sadě Visual Studio 2022 Preview, aby autoři rozšíření aktualizovali rozšíření pro práci se sadou Visual Studio 2022 Preview.
ms.date: 06/08/2021
ms.topic: reference
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: bed8d0a261f70acb5e842ebeaf0059faae3fc478
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308688"
---
# <a name="visual-studio-2022-sdk-removed-apis"></a>Odebrána rozhraní API sady Visual Studio 2022 SDK

[!INCLUDE [preview-note](../includes/preview-note.md)]

Níže uvedená rozhraní API se odebrala ze sady Visual Studio SDK a už se nedají používat. podrobné informace o tom, jak aktualizovat kód, najdete v každé části.

* [`IVsImageService`](#ivsimageservice)
* [`IBlockContextProvider`](#iblockcontextprovider)
* [`IToolTipProvider`](#itooltipprovider)
* [`IVsTextScanner` ani `IVsFullTextScanner`](#ivstextscanner-and-ivsfulltextscanner)
* [Asynchronní načtení řešení a zjednodušené načtení řešení](#asynchronous-solution-load-and-lightweight-solution-load)
* [`IVsDummy`](#ivsdummy)
* [`Microsoft.VisualStudio.Shell.Task`](#microsoftvisualstudioshelltask)
* [Otevřít ze zdroje v bezpečí](#open-from-source-safe)
* [Nový Návrhář XAML WPF pro .NET Framework](#new-wpf-xaml-designer-for-net-framework)

## <a name="ivsimageservice"></a>IVsImageService

Byl `IVsImageService` odebírán v aplikaci Visual Studio 2022. Všichni uživatelé `IVsImageService` by se měli `IVsImageService2` místo toho přesunout.

### <a name="recommended-updates"></a>Doporučené aktualizace

Používáte-li `IVsImageService` , nahraďte volání jeho metod voláními ekvivalentních metod `IVsImageService2` :

| **Metoda IVsImageService** | **Ekvivalentní metoda IVsImageService2** |
|----------------------------|----------------------------------------|
| Přidání                        | AddCustomImage                         |
| Získat                        | GetImage                               |
| GetIconForFile             | GetImageMonikerForFile                 |
| GetIconForFileEx           | GetImageMonikerForFile                 |

`IVsImageService`metody Add a Get, které jsou odkazovány na vlastní obrázky podle názvu (řetězec), nikoli moniker.  Doporučujeme, abyste svůj kód přepnuli na použití pouze monikerů pro odkazování na vlastní image, ale pokud se to ukáže jako nepraktické, `IVsImageService2` existuje několik metod, které vám umožní přidružit název k monikeru:

* `TryAssociateNameWithMoniker`
* `GetImageMonikerForName`

Pomocí těchto dvou metod můžete pokračovat na referenční obrázky podle názvu.

## <a name="iblockcontextprovider"></a>IBlockContextProvider

`IBlockContextProvider`V aplikaci Visual Studio 2022 jsou odebírány související typy a. Všichni uživatelé `IBlockContextProvider` by se měli `IStructureContextSourceProvider` místo toho přesunout.

### <a name="recommended-updates"></a>Doporučené aktualizace

Uživatelé `IBlockContextProvider` by měli použít `IStructureContextSourceProvider` místo toho ([dokumentace](/dotnet/api/microsoft.visualstudio.text.adornments.istructurecontextsourceprovider)).

## <a name="itooltipprovider"></a>IToolTipProvider

`IToolTipProvider`V aplikaci Visual Studio 2022 jsou odebírány související typy a. Všichni uživatelé `IToolTipProvider` by se měli `IToolTipService` místo toho přesunout.

### <a name="recommended-updates"></a>Doporučené aktualizace

Uživatelé `IToolTipProvider` by měli použít `IToolTipService` místo toho ([dokumentace](/dotnet/api/microsoft.visualstudio.text.adornments.itooltipservice)).

## <a name="ivstextscanner-and-ivsfulltextscanner"></a>IVsTextScanner a IVsFullTextScanner

`IVsTextScanner`A `IVsFullTextScanner` jsou odebírány v aplikaci Visual Studio 2022. Všechny uživatele `IVsTextScanner` nebo `IVsFullTextScanner` by se měly přesunout na `IVsTextLines` místo.

### <a name="recommended-updates"></a>Doporučené aktualizace

`IVsTextScanner` `IVsFullTextScanner` Místo toho by se uživatelé měli použít `IVsTextLines` ([dokumentace](/dotnet/apimicrosoft.visualstudio.textmanager.interop.ivstextlines.getlinetext)).

## <a name="asynchronous-solution-load-and-lightweight-solution-load"></a>Asynchronní načtení řešení a zjednodušené načtení řešení

V aplikaci Visual Studio 2022 jsou odebírány funkce asynchronního načtení řešení (ASL) a zjednodušené načtení řešení (LSL), protože tyto metody jsou odebírány:

### <a name="interfaces"></a>Rozhraní

* `IVsSolution4` -Metody: `IsBackgroundSolutionLoadEnabled` , `EnsureProjectsAreLoaded` , `EnsureProjectIsLoaded` , `EnsureSolutionIsLoaded`
* `IVsSolutionLoadEvents` -Metody: `OnBeforeBackgroundSolutionLoadBegins` , `OnQueryBackgroundLoadProjectBatch` , `OnBeforeLoadProjectBatch` , `OnAfterLoadProjectBatch`
* `IVsSolutionLoadManagerSupport` – Celé rozhraní
* `IVsSolutionLoadManager` – Celé rozhraní
* `IVsSccManager3`  – Celé rozhraní
* `IVsAsynchronousProjectCreate` – Celé rozhraní
* `IVsAsynchronousProjectCreateUI` – Celé rozhraní

### <a name="enums-properties-and-ui-contexts"></a>Výčty, vlastnosti a kontexty uživatelského rozhraní

* `VSHPROPID_ProjectUnloadStatus` Vytváření `UNLOADSTATUS_LoadPendingIfNeeded`
* `VSHPROPID_DemandLoadDependencies`
* `VSHPROPID_IsProjectProvisioned`
* `VSPROPID_IsInBackgroundIdleLoadProjectBatch`
* `VSPROPID_IsInSyncDemandLoadProjectBatch`
* `VSPROPID_ActiveSolutionLoadManager`
* `UICONTEXT_BackgroundProjectLoad`

### <a name="recommended-updates"></a>Doporučené aktualizace

Žádné

## <a name="ivsdummy"></a>IVsDummy

Byl `IVsDummy` odebírán v aplikaci Visual Studio 2022 a nebude nahrazen. 

### <a name="recommended-updates"></a>Doporučené aktualizace

Žádné Nemá ale žádný vliv, protože rozhraní API nefungovalo nic.

## <a name="microsoftvisualstudioshelltask"></a>Microsoft. VisualStudio. Shell. Task

`Microsoft.VisualStudio.Shell.Task`Třída byla přejmenována na `Microsoft.VisualStudio.Shell.TaskListItem` tak, aby nedošlo ke konfliktu s velmi oblíbenou `System.Threading.Tasks.Task` třídou.

## <a name="open-from-source-safe"></a>Otevřít ze zdroje v bezpečí

Odebírá se podpora otevírání řešení ze zdroje bezpečně, protože tyto metody, události a konstanty jsou odebírány.

## <a name="interfaces"></a>Rozhraní

* `IVsSCCProvider3` – Celé rozhraní

### <a name="recommended-updates"></a>Doporučené aktualizace

Žádné

## <a name="new-wpf-xaml-designer-for-net-framework"></a>Nový Návrhář XAML WPF pro .NET Framework

Aktuální Návrhář XAML WPF pro .NET Framework je zastaralá a bude nahrazena novým Návrhář XAML WPF pro .NET Framework, a to na základě stejné architektury, která se používá pro WPF Návrhář XAML pro .NET (.NET Core). To také znamená, že model rozšíření WPF .NET Framework Control na základě .design.dll a Microsoft. Windows. Design. rozšiřitelnost již není podporován. Nový Návrhář XAML WPF pro .NET Framework poskytuje stejný model rozšiřitelnosti jako WPF Návrhář XAML for .NET (.NET Core). Pokud jste již vytvořili rozšíření .designtools.dll pro .NET (.NET Core), stejné rozšíření bude fungovat pro nové Návrhář XAML WPF pro .NET Framework. Další informace o tom, jak migrovat na nový model rozšiřitelnosti pro platformy WPF (.NET Framework a .NET Core) a platformy UWP, najdete v níže uvedeném odkazu migrace. 

### <a name="recommended-updates"></a>Doporučené aktualizace

Viz [migrace rozšíření návrháře XAML](https://github.com/microsoft/xaml-designer-extensibility/blob/main/documents/xaml-designer-extensibility-migration.md).
