---
title: Konfigurace řešení | Dokumentace Microsoftu
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
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 53d8e3d33a81e20d553e6a5c97eb6e6f33339079
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801599"
---
# <a name="solution-configuration"></a>Konfigurace řešení
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Konfigurace řešení ukládání vlastností na úrovni řešení. Chování odkazují **Start** klíč (F5) a **sestavení** příkazy. Tyto příkazy ve výchozím nastavení, sestavit a spustit konfiguraci ladění. Oba příkazy se spustí v kontextu konfigurace řešení. To znamená, že uživatel můžete očekávat F5 pro spuštění a sestavení bez ohledu aktivním řešení se konfigurují prostřednictvím nastavení. Prostředí je určená k optimalizaci pro řešení než projektů při rozhodování o vytváření a spouštění.  
  
 Standardní panel nástrojů sady Visual Studio obsahuje tlačítko Start a konfigurace řešení rozevírací seznam napravo od tlačítko Start. Tento seznam umožňuje uživatelům zvolit konfiguraci tak, aby se má spustit při stisknutí klávesy F5, vytvářet své vlastní konfigurace řešení nebo upravit existující konfiguraci.  
  
> [!NOTE]
>  Nejsou žádná rozšíření rozhraní vytvořit nebo upravit konfiguraci řešení. Je nutné použít `DTE.SolutionBuilder`. Existují však rozšiřitelnost rozhraní API pro správu sestavení řešení. Další informace naleznete v tématu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.  
  
 Tady je implementace konfigurace řešení podporována typem projektu:  
  
- Projekt  
  
   Zobrazuje názvy projektů v aktuálním řešení se nenašly.  
  
- Konfigurace  
  
   Zadejte seznam konfigurací podporována typem projektu a zobrazí na stránkách vlastností implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>.  
  
   Konfigurace sloupec zobrazuje název konfigurace projektu k sestavení v této konfiguraci řešení a jsou uvedeny všechny konfigurace projektu po kliknutí na tlačítko se šipkou. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> metoda k vyplnění tohoto seznamu. Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> metoda znamená, že projekt podporuje úpravu konfigurace nové nebo upravit výběry se zobrazují v položce konfigurace. Každá z těchto možností spuštění dialogová okna, které volají metody `IVsCfgProvider2` rozhraní upravit konfigurace projektu.  
  
   Pokud projekt nepodporuje konfigurace, sloupci konfigurace žádný zobrazí a je zakázaná.  
  
- Platforma  
  
   Zobrazí platformu konfiguraci zvoleného projektu pro sestavení a obsahuje seznam všech dostupných platforem pro projekt po kliknutí na tlačítko se šipkou. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> metoda k vyplnění tohoto seznamu. Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> metoda znamená, že projekt podporuje úprav platformy, nové nebo upravit výběry jsou také zobrazeným pod záhlavím platformy. Každá z těchto možností spuštění dialogová okna, které volají `IVsCfgProvider2` metody upravit platformy projektu k dispozici.  
  
   Pokud projekt nepodporuje platformy, sloupci platformy pro daný projekt žádný zobrazí a je zakázaná.  
  
- Sestavení  
  
   Určuje, zda aktuální konfigurace řešení sestavení projektu. Nevybrané projekty nevzniknou při sestavení na úrovni řešení příkazy, které jsou vyvolány bez ohledu na všechny závislosti projektu, které obsahují. Není vybrána k sestavení projektů jsou zahrnuty i v ladění, spouštění, balení a nasazení řešení.  
  
- Nasazení  
  
   Určuje, zda bude projekt nasazen zadáním příkazů Start nebo nasazení s konfigurací sestavení vybrané řešení. Zaškrtněte políčko pro toto pole bude k dispozici, pokud projekt podporuje nasazení implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> rozhraní na jeho <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> objektu.  
  
  Jakmile se přidá nová konfigurace řešení, uživatel může vybrat z rozevíracího seznamu konfigurace řešení na standardním panelu nástrojů k sestavení a/nebo spustit tuto konfiguraci.  
  
## <a name="see-also"></a>Viz také  
 [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)   
 [Konfigurace projektu pro sestavení](../../extensibility/internals/project-configuration-for-building.md)   
 [Objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md)

