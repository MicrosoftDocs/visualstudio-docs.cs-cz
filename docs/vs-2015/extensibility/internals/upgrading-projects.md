---
title: Upgrade projektů | Dokumentace Microsoftu
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
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a3f045d947f968655923df16de8c02aafc12a34b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783757"
---
# <a name="upgrading-projects"></a>Upgrade projektů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

K modelu projektu se změní z jedné verze [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] na další může vyžadovat, že projekty a řešení upgradovat tak, aby mohli spouštět na novější verzi. [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Poskytuje rozhraní, které lze použít k implementaci podporu upgradu v svoje vlastní projekty.  
  
## <a name="upgrade-strategies"></a>Strategie upgradu  
 Implementace systému projektu pro podporu upgradu, musíte definovat a implementovat upgradu strategie. Při určování strategie, můžete pro podporu side-by-side (SxS) zálohování nebo zálohování kopírováním.  
  
-   Zálohování SxS znamená, že projekt zkopíruje pouze soubory, které potřebují upgrade na místě, přidání vhodný název příponu souboru, například "old".  
  
-   Zálohování kopírováním znamená, že projekt zkopíruje všechny položky projektu do uživatelem zadaného umístění zálohy. Relevantní soubory do původního umístění projektu jsou potom upgradovat.  
  
## <a name="how-upgrade-works"></a>Jak upgradovat funguje  
 Při řešení vytvořené v dřívější verzi [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] je otevřít v novější verzi, integrované vývojové prostředí kontroly souborů řešení Chcete-li zjistit, jestli je potřeba upgradovat. Je-li upgrade vyžadováno, **Průvodce upgradem** se automaticky spustí, aby vás uživatel provede procesem.  
  
 Při řešení potřebuje upgrade, vyžádá si každý projektu pro vytváření pro své strategie upgradu. Strategie určí, zda objekt pro vytváření projektů podporuje zálohování kopírováním nebo SxS zálohování. Informace odeslány **Průvodce upgradem**, který shromažďuje informace potřebné pro zálohování a zobrazí příslušné možnosti pro uživatele.  
  
### <a name="multi-project-solutions"></a>Řešení vícenásobného projektu  
 Pokud řešení obsahuje více projektů a upgradu strategie liší, jako když projektu jazyka C++, který podporuje pouze SxS zálohování, webový projekt, který podporuje jenom zálohování kopírováním objektů pro vytváření projektů musí si vyjednat strategie upgradu.  
  
 Každý projekt pro vytváření pro dotazy řešení <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Poté zavolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> zobrazíte potřebujete globální projektových souborů, upgrade a na zjištění podporované upgradu strategie. **Průvodce upgradem** následně vyvolány.  
  
 Po dokončení průvodce, uživatel <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> je volána na objektu pro vytváření každý projekt skutečné upgradu. Pro usnadnění zálohování, IVsProjectUpgradeViaFactory metody poskytují <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> služby protokolovat podrobnosti o procesu upgradu. Tato služba nejde udržovat v mezipaměti.  
  
 Po aktualizaci všechny relevantní soubory globální, každý objekt pro vytváření projektu můžete vytvořit instanci projektu. Implementace projektu musí podporovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Metoda je volána poté upgradovat všechny položky příslušného projektu.  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Metoda neposkytuje SVsUpgradeLogger službu. Tato služba lze získat voláním <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.  
  
## <a name="best-practices"></a>Doporučené postupy  
 Použití <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> služby zkontrolujte, jestli můžete upravit soubor začnete upravovat a můžete ji uložit před uložením. To vám pomůže zálohování a upgradu implementace zpracovat soubory projektu pod správou zdrojových kódů, soubory s dostatečná oprávnění a tak dále.  
  
 Použití <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> služby během všech fází zálohování a upgradovat na poskytují informace o úspěchu nebo selhání procesu upgradu.  
  
 Další informace o zálohování a upgrade projektů naleznete v tématu komentáře IVsProjectUpgrade v vsshell2.idl.  
  
## <a name="see-also"></a>Viz také  
 [Projekty](../../extensibility/internals/projects.md)   
 [Upgrade vlastních projektů](../../misc/upgrading-custom-projects.md)   
 [Upgrade položky projektu](../../misc/upgrading-project-items.md)

