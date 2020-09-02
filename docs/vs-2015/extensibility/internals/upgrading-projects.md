---
title: Upgrade projektů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8e838cb02aa1a620356f96d9e77f1752797ac409
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787209"
---
# <a name="upgrading-projects"></a>Upgrade projektů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Změny modelu projektu z jedné verze nástroje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] na další mohou vyžadovat upgrade projektů a řešení, aby mohli běžet v novější verzi. [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]Poskytuje rozhraní, které lze použít k implementaci podpory upgradu ve vašich vlastních projektech.  
  
## <a name="upgrade-strategies"></a>Strategie upgradu  
 Pro podporu upgradu musí vaše implementace systému projektu definovat a implementovat strategii upgradu. Při určování vaší strategie můžete zvolit podporu souběžného zálohování (SxS), zálohování kopírování nebo obojího.  
  
- Záloha SxS znamená, že projekt kopíruje pouze soubory, které vyžadují upgrade, a přidává vhodné přípony názvu souboru, například ". old".  
  
- Příkaz Kopírovat zálohu znamená, že projekt kopíruje všechny položky projektu do umístění zálohy zadaného uživatelem. Příslušné soubory v původním umístění projektu jsou poté upgradovány.  
  
## <a name="how-upgrade-works"></a>Jak funguje upgrade  
 Když je řešení vytvořené v dřívější verzi nástroje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] otevřeno v novější verzi, rozhraní IDE zkontroluje soubor řešení a určí, jestli je potřeba upgradovat. Pokud je nutné upgradovat, **Průvodce upgradem** se automaticky spustí a provede uživatele procesem upgradu.  
  
 Když řešení vyžaduje upgrade, dotazuje se na každý objekt pro vytváření projektů pro strategii upgradu. Strategie určuje, zda objekt pro vytváření projektů podporuje zálohování kopírováním nebo SxS. Informace se odesílají do **Průvodce upgradem**, který shromažďuje informace požadované pro zálohování a prezentuje příslušné možnosti uživateli.  
  
### <a name="multi-project-solutions"></a>Řešení s více projekty  
 Pokud řešení obsahuje více projektů a strategie upgradu se liší, například pokud projekt C++, který podporuje pouze zálohu SxS a webový projekt, který podporuje pouze zálohu kopírování, musí projektové továrny vyjednávat strategii upgradu.  
  
 Řešení se dotazuje na jednotlivé továrny projektu pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> . Pak zavolá, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> zda globální soubory projektu vyžadují upgrade, a určí podporované strategie upgradu. Pak se vyvolá **Průvodce upgradem** .  
  
 Po dokončení průvodce <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> se zavolá na každý objekt pro vytváření projektu, který provede vlastní upgrade. K usnadnění zálohování metody IVsProjectUpgradeViaFactory poskytují <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> službě protokolovat podrobnosti procesu upgradu. Tuto službu nelze uložit do mezipaměti.  
  
 Po aktualizaci všech relevantních globálních souborů může každý objekt pro vytváření projektu zvolit vytvoření instance projektu. Implementace projektu musí podporovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>Metoda je pak volána pro upgrade všech relevantních položek projektu.  
  
> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>Metoda neposkytuje službu SVsUpgradeLogger. Tuto službu lze získat voláním <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> .  
  
## <a name="best-practices"></a>Osvědčené postupy  
 Službu můžete použít <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> ke kontrole, jestli soubor před úpravou nemůžete upravit, a můžete ho před uložením Uložit. To pomůže vašim implementacím zálohování a upgradu zpracovat soubory projektu v rámci správy zdrojového kódu, souborů s nedostatečnými oprávněními a tak dále.  
  
 Službu můžete používat <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> během všech fází zálohování a upgradu a poskytnout tak informace o úspěchu nebo neúspěchu procesu upgradu.  
  
 Další informace o zálohování a upgradu projektů naleznete v tématu poznámky k IVsProjectUpgrade v vsshell2. idl.  
  
## <a name="see-also"></a>Viz také  
 [Projekty](../../extensibility/internals/projects.md)   
 [Upgrade vlastních projektů](../../misc/upgrading-custom-projects.md)   
 [Upgrade položek projektu](../../misc/upgrading-project-items.md)
