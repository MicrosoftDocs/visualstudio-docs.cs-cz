---
title: Konfigurace pro vytvoření projektu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4d78ac1cabc356db162639d3eb19d0bff71e295e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133300"
---
# <a name="project-configuration-for-building"></a>Konfigurace projektu pro vytváření
Dialogové okno konfigurace řešení spravuje seznam konfigurace řešení pro danou řešení.  
  
 Uživatel může vytvořit konfigurace další řešení, každý s svůj vlastní jedinečný název. Když uživatel vytvoří novou konfiguraci řešení, tak IDE výchozí odpovídající název konfigurace ve projekty nebo ladění, pokud neexistuje žádný odpovídající název. Uživatel může změnit výběr podle specifických požadavků v případě potřeby. Jedinou výjimku toto chování je Pokud projekt podporuje konfigurace, která odpovídá názvu novou konfiguraci řešení. Předpokládejme například, že řešení obsahuje Project1 a projektu2. Project1 má konfigurace projektu ladění, prodejní verze a MyConfig1. Projektu2 má konfigurace projektu ladění, prodejní verze a MyConfig2.  
  
 Pokud uživatel vytvoří novou konfiguraci řešení s názvem MyConfig2, Project1 sváže jeho konfiguraci ladění konfigurace řešení ve výchozím nastavení. Projektu2 také sváže konfiguraci MyConfig2 konfigurace řešení ve výchozím nastavení.  
  
> [!NOTE]
>  Vazba nerozlišuje velká a malá písmena.  
  
 Když uživatel vybere **vícenásobný výběr** položky v rozevíracím seznamu konfigurace prostředí zobrazí dialogové okno, které poskytuje seznam dostupné konfigurace.  
  
 ![Více konfigurací](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs")  
Více konfigurací  
  
 V rámci toto dialogové okno kterého uživatel může vybrat jednu nebo více konfigurací. Po výběru, hodnoty vlastností zobrazí v dialogovém okně Vlastnosti stránky projeví průnik hodnot pro vybrané konfigurace.  
  
 V tématu [konfigurace řešení](../../extensibility/internals/solution-configuration.md) informace týkající se přidání a přejmenování konfigurace pro projekty a řešení.  
  
 Závislosti projektu a sestavení pořadí jsou konfigurace řešení, které jsou nezávislé: tedy můžete pouze nastavit stromu závislostí pro všechny projekty v řešení. Pravým tlačítkem myši na řešení nebo projekt a výběrem buď **závislosti projektu** nebo **pořadí sestavení projektu** možnost otevře **závislosti projektu** dialogové okno. Můžete otevřít také z **projektu** nabídky.  
  
 ![Závislosti projektu](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")  
Závislosti projektu  
  
 Závislosti projektu určete pořadí, ve kterém sestavení projektů. Na kartě sestavení pořadí v dialogovém okně můžete zobrazit přesný pořadí, ve kterém projekty v řešení bude sestavovat a na kartě závislosti lze upravit pořadí sestavení.  
  
> [!NOTE]
>  Projekty v seznamu, které mají jejich políček vybrána, ale zašedlé přidal prostředí z důvodu explicitní závislosti určeného <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> rozhraní a nedá se změnit. Například přidání odkazu na projekt z [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] automaticky přidá závislost sestavení, který lze odebrat pouze odstraněním odkaz na projekt do jiného projektu. Projekty jejichž zaškrtávací políčka zřetelné a zašedlé nelze vybrat, protože díky tomu by vytvořily smyčku závislosti (například Project1 by závisí na projektu2 a projektu2 by závisí na Project1), který by stalace sestavení.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sestavení procesy zahrnují typické kompilace a odkaz operací, které jsou spuštěny se jeden příkaz sestavení. Dva další procesy sestavení může také podporovat: operace vyčištění odstranit všechny položky výstup z předchozího sestavení a aktuální kontroly k určení, pokud došlo ke změně výstupní položku v konfiguraci.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> objekty vrátit odpovídající <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> (vrácená z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>) ke správě jejich procesy sestavení. Zaznamenat stav operace sestavení probíhající, se provedené konfigurace volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>, rozhraní implementované prostředí a druhý objekt zajímá událostí stav sestavení.  
  
 Po nastavení konfigurace slouží k určení, zda lze spustit pod kontrolou ladicího programu. Konfigurace implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> pro podporu ladění.  
  
 Po implementaci závislosti projektu, můžete upravit prostřednictvím kódu programu závislosti prostřednictvím modelu automatizace. Volání <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> v modelu automatizace. Neexistují žádné dostupné rozhraní VSIP úrovni rozhraní API umožňujících přímá manipulace s Správce konfigurace sestavení řešení a jejich vlastnosti.  
  
 Kromě toho můžete zadat mřížky v okně závislosti projektu. Další informace najdete v tématu [vlastnosti zobrazení mřížky](../../extensibility/internals/properties-display-grid.md).  
  
## <a name="see-also"></a>Viz také  
 [Správa možnosti konfigurace](../../extensibility/internals/managing-configuration-options.md)   
 [Konfigurace projektu pro správu nasazení](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [Konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md)