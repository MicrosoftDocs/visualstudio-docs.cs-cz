---
title: Konfigurace projektu pro správu nasazení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d5b16c3392e9432ba540130d45f6907de15b51ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62429948"
---
# <a name="project-configuration-for-managing-deployment"></a>Konfigurace projektu pro správu nasazení
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nasazení je činnost fyzického přesunu výstupních položek z procesu sestavení do očekávaného umístění pro ladění a instalaci. Například webová aplikace může být postavená na místním počítači a pak umístěna na server.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] podporuje dva způsoby, jak můžou být projekty součástí nasazení:  
  
- Jako předmět procesu nasazení.  
  
- Jako vedoucí procesu nasazení.  
  
  Před nasazením řešení je nutné nejprve přidat projekt nasazení a nakonfigurovat možnosti nasazení. Pokud projekt nasazení ještě neexistuje, zobrazí se dotaz, jestli ho chcete vytvořit, když v nabídce **sestavení** vyberete **nasadit řešení** nebo kliknete pravým tlačítkem na řešení. Kliknutím na **Ano** se otevře dialogové okno **Přidat nový projekt** s vybraným projektem **Průvodce vzdáleným nasazením** .  
  
  Průvodce vzdáleným nasazením vás vyzve k zadání typu aplikace (Windows nebo webu), skupin výstupu projektu, které mají být zahrnuty, všech dalších souborů, které chcete zahrnout, a vzdáleného počítače, do kterého chcete nasadit. Poslední stránka Průvodce zobrazí souhrn vybraných možností.  
  
  Projekty, které jsou předmětem procesu nasazení, vytváří výstupní položky, které je nutné přesunout do alternativního prostředí. Tyto výstupní položky jsou popsány jako parametry pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> rozhraní, jejichž primární účel, pokud chcete, aby projekty mohly seskupit výstupy. Další informace týkající se implementace `IVsProjectCfg2` naleznete v tématu [konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md).  
  
  Projekty nasazení, které spravují proces nasazení, povolují příkaz nasadit a reagují při výběru tohoto příkazu. Projekty nasazení implementují <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> rozhraní pro provedení nasazení a volají volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> rozhraní k nahlášení událostí stavu nasazení.  
  
  Konfigurace mohou určovat závislosti, které mají vliv na jejich operace sestavení nebo nasazení. Závislosti sestavení nebo nasazení jsou projekty, které musí být sestaveny nebo nasazeny před nebo po samotných konfiguracích nebo jejich nasazení. Závislosti sestavení mezi projekty jsou popsány pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> rozhraní a nasazují závislosti s <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> rozhraním. Další informace najdete v tématu [konfigurace projektu pro sestavování](../../extensibility/internals/project-configuration-for-building.md).  
  
## <a name="see-also"></a>Viz také  
 [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)   
 [Konfigurace projektu pro sestavení](../../extensibility/internals/project-configuration-for-building.md)   
 [Konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md)
