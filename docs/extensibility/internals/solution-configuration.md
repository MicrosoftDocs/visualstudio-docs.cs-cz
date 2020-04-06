---
title: Konfigurace řešení | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705381"
---
# <a name="solution-configuration"></a>Konfigurace řešení
Konfigurace řešení ukládají vlastnosti na úrovni řešení. Řídí chování klávesy **Start** (F5) a **příkazy Sestavení.** Ve výchozím nastavení tyto příkazy sestavení a spuštění konfigurace ladění. Oba příkazy se spouštějí v kontextu konfigurace řešení. To znamená, že uživatel může očekávat, že F5 spustit a sestavit bez ohledu na aktivní řešení je nakonfigurován prostřednictvím nastavení. Prostředí je navrženo tak, aby optimalizovalo řešení spíše než projekty, pokud jde o vytváření a provoz.

 Standardní panel nástrojů sady Visual Studio obsahuje tlačítko Start a rozevírací název konfigurace řešení napravo od tlačítka Start. Tento seznam umožňuje uživatelům zvolit konfiguraci, která má být spuštěna při stisknutí klávesy F5, vytvořit vlastní konfigurace řešení nebo upravit existující konfiguraci.

> [!NOTE]
> Neexistují žádná rozhraní rozšiřitelnosti k vytvoření nebo úpravě konfigurací řešení. Je nutné `DTE.SolutionBuild`použít . Existují však rozšiřitelnost API pro správu sestavení řešení. Další informace naleznete v tématu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.

 Zde je, jak můžete implementovat konfigurace řešení podporované typu projektu:

- Project

   Zobrazí názvy projektů nalezených v aktuálním řešení.

- Konfigurace

   Chcete-li poskytnout seznam konfigurací podporovaných typem projektu a <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>zobrazených na stránkách vlastností, implementujte .

   Sloupec Konfigurace zobrazuje název konfigurace projektu, kterou chcete sestavit v této konfiguraci řešení, a zobrazí seznam všech konfigurací projektu po klepnutí na tlačítko se šipkou. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> metodu k vyplnění tohoto seznamu. Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> metoda označuje, že projekt podporuje úpravy konfigurace, zobrazí se pod nadpisem Konfigurace také nové nebo upravit výběry. Každý z těchto výběrů spustit dialogová `IVsCfgProvider2` okna, která volají metody rozhraní pro úpravu konfigurace projektu.

   Pokud projekt nepodporuje konfigurace, zobrazí se ve sloupci Konfigurace žádný a je zakázán.

- Platforma

   Zobrazí platformu, pro kterou je vybraná konfigurace projektu vytvářena, a zobrazí seznam všech dostupných platforem pro projekt po klepnutí na tlačítko se šipkou. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> metodu k vyplnění tohoto seznamu. Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> metoda označuje, že projekt podporuje úpravy platformy, nové nebo upravit výběry jsou také zobrazeny pod záhlaví platformy. Každý z těchto výběrů spustí `IVsCfgProvider2` dialogová okna, která volají metody pro úpravu dostupných platforem projektu.

   Pokud projekt nepodporuje platformy, sloupec platformy pro tento projekt zobrazí Žádné a je zakázáno.

- Sestavení

   Určuje, zda je projekt vytvořen aktuální konfigurací řešení. Nevybrané projekty nejsou vytvořeny při vytváření příkazů sestavení na úrovni řešení jsou vyvolány i přes všechny závislosti projektu, které obsahují. Projekty, které nejsou vybrány k vytváření, jsou stále zahrnuty v ladění, spuštění, balení a nasazení řešení.

- Nasazení

   Určuje, zda bude projekt nasazen při použití příkazů Start nebo Deploy s vybranou konfigurací sestavení řešení. Zaškrtávací políčko pro toto pole bude <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> k dispozici, pokud projekt podporuje nasazení implementací rozhraní na jeho <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> objektu.

  Po přidání nové konfigurace řešení může uživatel vybrat z rozevíracího seznamu Konfigurace řešení na standardním panelu nástrojů a vytvořit nebo spustit tuto konfiguraci.

## <a name="see-also"></a>Viz také
- [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurace projektu pro sestavení](../../extensibility/internals/project-configuration-for-building.md)
- [Objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md)
