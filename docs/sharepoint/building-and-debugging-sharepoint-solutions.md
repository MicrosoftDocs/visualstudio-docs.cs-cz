---
title: Sestavování a ladění řešení služby SharePoint | Microsoft Docs
description: Naučte se sestavovat a ladit řešení služby SharePoint a porozumět tomu, jak se liší od vytváření a ladění jiných typů projektů v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c16414e6a49d727cf6b2113184c507feb7a73569
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955785"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Sestavování a ladění řešení služby SharePoint
  Obecně platí, že sestavování a ladění řešení služby SharePoint je stejné jako sestavení a ladění jiných typů projektů v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Témata v této části vysvětlují rozdíly, které existují.

## <a name="project-output-for-sharepoint-solutions"></a>Výstup projektu pro řešení služby SharePoint
 Sestavování řešení SharePoint vytvoří sestavení a soubor balíčku řešení (*. wsp*). V následující tabulce jsou uvedena umístění těchto souborů během sestavení.

|Položka sestavení|Výstupní složka|
|----------------|-------------------|
|Sestavení, databáze programu (*PDB*) a soubory *. wsp* .|*\<ProjectName> \bin\debug* nebo *\<ProjectName> \bin\Release*|
|Soubory položek projektu služby SharePoint.|*\<ProjectName> \pkg\debug* nebo *\<ProjectName> \pkg\release*|
|Sestavujte mezilehlé soubory.|*\<ProjectName> \obj\debug* nebo *\<ProjectName> \obj\release*|
|Balíčky zprostředkujících souborů.|*\<ProjectName> \pkgobj\debug* nebo *\<ProjectName> \pkgobj\release*|

## <a name="build-sharepoint-solutions"></a>Sestavení řešení pro SharePoint
 Aby bylo možné sestavovat řešení služby SharePoint, musí mít vývojový počítač nainstalovanou správnou verzi SharePoint serveru. V opačném případě sestavování řešení služby SharePoint je stejné jako vytváření dalších typů projektů v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Další informace najdete v tématu [Postupy: sestavení řešení služby SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).

## <a name="debug-and-test-sharepoint-solutions"></a>Ladění a testování řešení služby SharePoint
 Před laděním [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] zkopíruje balíček *. wsp* na server služby SharePoint, aktivuje web a funkce v oboru webu a v některých případech spustí projekt. V jiných případech může být nutné projekt otevřít ručně. Další informace najdete v tématu [řešení potíží s řešeními služby SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md) a [ladění řešení služby SharePoint](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Ladění a ověření řešení služby SharePoint pomocí Azure DevOps Servicesch funkcí
 Azure DevOps Services funkce jako testování částí a IntelliTrace vám umožní přesněji určit problémy v řešeních služby SharePoint. Profilace umožňuje vyhledat a identifikovat oblasti problémů s výkonem v řešeních služby SharePoint. Další informace naleznete v tématu [ověřování a ladění kódu služby SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) a [profilace výkonu aplikací služby SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).

## <a name="security-during-the-build-process"></a>Zabezpečení během procesu sestavení
 Aby bylo možné zabalit nebo nasadit řešení služby SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] musí mít oprávnění ke kopírování souborů na server SharePoint. Musíte spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] jako proces se zvýšenými oprávněními a váš uživatelský účet musí být správcem kolekcí webů na sharepointovém serveru. Kromě toho musíte určit, jestli je váš projekt řešení v izolovaném prostoru nebo řešení farmy. Další informace najdete v tématu [rozdíly mezi řešeními v izolovaném prostoru a ve farmách](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="using-the-clean-command"></a>Použití příkazu vyčistit
 Pokud je řešení služby SharePoint nainstalováno na serveru SharePoint pro ladění, příkaz **vyčistit** neprovádí odinstalaci řešení. Místo toho je nutné funkce deaktivovat prostřednictvím konfigurace služby SharePoint.

## <a name="see-also"></a>Viz také
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Procházení připojení služby SharePoint pomocí Průzkumník serveru](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
