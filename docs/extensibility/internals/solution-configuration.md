---
title: Konfigurace řešení | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c96b73747ef8b136a74a7256cde7fef8d1c42de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705381"
---
# <a name="solution-configuration"></a>Konfigurace řešení
Konfigurace řešení ukládají vlastnosti na úrovni řešení. Nasměrují chování klávesy **Spustit** (F5) a příkazu **sestavení** . Ve výchozím nastavení tyto příkazy sestaví a spustí konfiguraci ladění. Oba příkazy jsou spouštěny v kontextu konfigurace řešení. To znamená, že uživatel může očekávat, že F5 spustí a sestaví jakékoli aktivní řešení, které se nakonfiguruje prostřednictvím nastavení. Prostředí je navrženo pro optimalizaci pro řešení spíše než při sestavování a spouštění.

 Standardní panel nástrojů sady Visual Studio obsahuje tlačítko Start a rozevírací seznam konfigurace řešení napravo od tlačítka Start. Tento seznam umožňuje uživatelům zvolit konfiguraci, která se má spustit při stisknutí klávesy F5, vytvořit vlastní konfigurace řešení nebo upravit existující konfiguraci.

> [!NOTE]
> Nejsou k dispozici žádná rozhraní rozšíření pro vytvoření nebo úpravu konfigurace řešení. Je nutné použít `DTE.SolutionBuild` . Existují však rozhraní API rozšíření pro správu sestavení řešení. Další informace naleznete v tématu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.

 Tady je postup, jak můžete implementovat konfigurace řešení podporované vaším typem projektu:

- Project

   Zobrazuje názvy projektů nalezených v aktuálním řešení.

- Konfigurace

   Chcete-li poskytnout seznam konfigurací podporovaných typem projektu a zobrazených na stránkách vlastností, implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> .

   Sloupec konfigurace zobrazuje název konfigurace projektu, který se má sestavit v této konfiguraci řešení, a seznam všech konfigurací projektu po kliknutí na tlačítko se šipkou. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> metodu pro vyplnění tohoto seznamu. Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> Metoda označuje, že projekt podporuje úpravy konfigurace, zobrazí se také nové nebo upravit výběry pod hlavičkou konfigurace. Každé z těchto výběrů spouští dialogová okna, která volají metody `IVsCfgProvider2` rozhraní pro úpravu konfigurací projektu.

   Pokud projekt nepodporuje konfigurace, zobrazí se ve sloupci konfigurace možnost žádný a je zakázán.

- Platforma

   Zobrazí platformu, pro kterou vybraná konfigurace projektu vytváří sestavení, a zobrazí seznam všech dostupných platforem pro projekt po kliknutí na tlačítko se šipkou. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> metodu pro vyplnění tohoto seznamu. Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> Metoda označuje, že projekt podporuje editaci platforem, nové nebo editační výběry se zobrazí také pod nadpisem platformy. Každé z těchto výběrů spouští dialogová okna, která volají `IVsCfgProvider2` metody pro úpravu dostupných platforem projektu.

   Pokud projekt nepodporuje platformy, zobrazí se ve sloupci platforma pro daný projekt možnost žádný a je zakázán.

- Sestavení

   Určuje, jestli je projekt sestavený aktuální konfigurací řešení nebo ne. Nevybrané projekty nejsou sestaveny, když jsou příkazy sestavení na úrovni řešení vyvolány bez ohledu na závislosti projektu, které obsahují. Projekty, které nejsou vybrány pro sestavení, jsou stále zahrnuty do ladění, spuštění, balení a nasazení řešení.

- Nasazení

   Určuje, zda bude projekt nasazen, pokud jsou použity příkazy spustit nebo nasadit s vybranou konfigurací sestavení řešení. Zaškrtávací políčko pro toto pole bude k dispozici, pokud projekt podporuje nasazení implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> objektu.

  Po přidání nové konfigurace řešení ji uživatel může vybrat z rozevíracího seznamu konfigurace řešení na panelu nástrojů Standardní a sestavit nebo spustit tuto konfiguraci.

## <a name="see-also"></a>Viz také
- [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurace projektu pro sestavení](../../extensibility/internals/project-configuration-for-building.md)
- [Objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md)
