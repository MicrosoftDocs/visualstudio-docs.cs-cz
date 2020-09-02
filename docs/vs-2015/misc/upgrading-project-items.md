---
title: Upgrade položek projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- upgrading project items
- projects [Visual Studio SDK], upgrading items
- project items [Visual Studio], upgrading
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: eb3619e187c7856cf03ee60c8a04cbe527bf0a69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698689"
---
# <a name="upgrading-project-items"></a>Upgrade položek projektu
Pokud přidáte nebo spravujete položky v rámci projektové systémy, které neimplementujete, může být nutné se zapojit do procesu upgradu projektu. Crystal Reports je příkladem položky, kterou lze přidat do systému projektu.  
  
 Implementací položek projektu obvykle chtějí využít již plně sestavený a upgradovaný projekt, protože potřebují znát, co jsou odkazy na projekt a jaké další vlastnosti projektu jsou k dispozici pro rozhodnutí o upgradu.  
  
### <a name="to-get-the-project-upgrade-notification"></a>Získání oznámení o upgradu projektu  
  
1. Nastavte <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> příznak (definovaný v vsshell80. idl) v implementaci položky projektu. To způsobí, že se položka projektu VSPackage automaticky načte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , když prostředí určí, že systém projektu je v procesu upgradu.  
  
2. Poraďte <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> rozhraní prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> metody.  
  
3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>Rozhraní se aktivuje poté, co implementace systému projektu dokončí operace upgradu a vytvoří se nový upgradovaný projekt. V závislosti na scénáři <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> je rozhraní vyvolána za <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> metodami, nebo.  
  
### <a name="to-upgrade-the-project-item-files"></a>Upgrade souborů položek projektu  
  
1. Je nutné pečlivě spravovat proces zálohování souborů v implementaci položky projektu. To platí zejména pro souběžné zálohování, kde `fUpgradeFlag` parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metody je nastaven na <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> , kde jsou umístěny soubory, které byly zálohovány společně umístěné soubory, které jsou označeny jako ". old". Zálohované soubory starší než systémový čas, kdy byl projekt upgradován, mohou být označeny jako zastaralé. Kromě toho mohou být přepsány, Pokud neprovedete konkrétní kroky k tomu, aby se zabránilo.  
  
2. V okamžiku, kdy položka projektu získá oznámení o upgradu projektu, je stále zobrazen **Průvodce převodem sady Visual Studio** . Proto byste měli použít metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> rozhraní k poskytnutí zpráv upgradu do uživatelského rozhraní průvodce.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce převodem sady Visual Studio](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Upgrade vlastních projektů](../misc/upgrading-custom-projects.md)