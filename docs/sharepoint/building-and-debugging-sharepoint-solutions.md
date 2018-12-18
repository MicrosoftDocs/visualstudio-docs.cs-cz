---
title: Sestavování a ladění řešení služby SharePoint | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 82733a8d3e908e82ad8f841857aa70374495e556
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283532"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Sestavování a ladění řešení služby SharePoint
  Obecně platí, sestavování a ladění řešení služby SharePoint je shodný sestavování a ladění ostatních typů projektů v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Témata v této části popisují, které existují rozdíly.  
  
## <a name="project-output-for-sharepoint-solutions"></a>Výstup projektu pro řešení služby SharePoint
 Vytváření řešení služby SharePoint vytvoří sestavení a balíček řešení (*.wsp*) soubor. Následující tabulka uvádí umístění těchto souborů během sestavování.  
  
|Vytvoření položky|Výstupní složka|  
|----------------|-------------------|  
|Sestavení, databázi programu (*PDB*), a *.wsp* soubory.|*\<ProjectName > \bin\debug* nebo  *\<ProjectName > \bin\release*|  
|Soubory položek Sharepointového projektu.|*\<ProjectName > \pkg\debug* nebo  *\<ProjectName > \pkg\release*|  
|Zprostředkující soubory sestavení.|*\<ProjectName > \obj\debug* nebo  *\<ProjectName > \obj\release*|  
|Zprostředkující soubory balíčku.|*\<ProjectName > \pkgobj\debug* nebo  *\<ProjectName > \pkgobj\release*|  
  
## <a name="build-sharepoint-solutions"></a>Sestavení řešení služby SharePoint
 K sestavení řešení služby SharePoint, musí mít vývojovém počítači správnou verzi serveru SharePoint server nainstalovaný. V opačném případě sestavení řešení služby SharePoint je stejné jako vytvoření jiných typů projektů v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Další informace najdete v tématu [postupy: řešení služby SharePoint sestavení](../sharepoint/how-to-build-sharepoint-solutions.md).  
  
## <a name="debug-and-test-sharepoint-solutions"></a>Ladění a testování řešení služby SharePoint
 Před laděním, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] kopie *.wsp* balíček na server SharePoint, aktivuje na webu a rozsahem webové funkce a v některých případech se spustí projekt. V jiných případech budete muset otevřít projekt ručně. Další informace najdete v tématu [řešení potíží s SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md) a [řešení ladění služby SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Ladění a ověření řešení služby SharePoint pomocí funkce služby Azure DevOps
 Azure DevOps služby funkce, jako je IntelliTrace a testování vám umožní a další přesně přesně problémy v řešení služby SharePoint. Profilace umožňuje vyhledat a identifikovat problémová výkonu v řešení služby SharePoint. Další informace najdete v tématu [ověření a ladění kódu pro SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) a [profilace výkonu aplikací služby SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).  
  
## <a name="security-during-the-build-process"></a>Zabezpečení během procesu sestavení
 Balíček nebo nasazení řešení služby SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] musí mít oprávnění ke kopírování souborů na server SharePoint. Je nutné spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] jako proces se zvýšenými a uživatel účet musí být správcem kolekce webů na serveru SharePoint. Kromě toho musíte zadat, jestli je váš projekt řešení v izolovaném prostoru nebo řešení farmy. Další informace najdete v tématu [rozdíly mezi řešeními v izolovaném prostoru a řešení ve farmách](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="using-the-clean-command"></a>Pomocí příkazu vyčistit  
 Při instalaci řešení služby SharePoint na server SharePoint pro ladění, **Vyčistit** příkaz neodinstaluje řešení. Místo toho je nutné deaktivovat funkce prostřednictvím konfigurace služby SharePoint.  
  
## <a name="see-also"></a>Viz také:
 [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Procházet připojení služby SharePoint pomocí Průzkumníka serveru](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
 
