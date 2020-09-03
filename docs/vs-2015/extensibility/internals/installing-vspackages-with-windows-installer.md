---
title: Instalace VSPackage pomocí Instalační služba systému Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 35942f6babf18967e11f268ef0412acb4cc8edf7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687468"
---
# <a name="installing-vspackages-with-windows-installer"></a>Instalace balíčků VSPackage pomocí Instalační služby systému Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Integrace sady VSPackage do systému [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] vyžaduje více než pouze kopírování souborů do počítače uživatele. Instalační program VSPackage musí nainstalovat rozhraní VSPackage a jeho závislé soubory a zaregistrovat je a integrovat je do nástroje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Rozhraní VSPackage může využít výhod integračních funkcí, jako je například zobrazení ikony na [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] úvodní obrazovce a dialogového okna o aplikaci.  
  
 Soubory Microsoft Instalační služba systému Windows jsou doporučeným způsobem pro distribuci VSPackage. Snadno použitelné balíčky Instalační služba systému Windows lze spustit na jakémkoli operačním systému Windows, který podporuje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Další informace najdete v tématu [Instalační služba systému Windows](https://msdn.microsoft.com/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Základní informace o Instalační službě systému Windows](../../extensibility/internals/windows-installer-basics.md)  
 Poskytuje přehled Instalační služba systému Windows.  
  
 [Scénáře instalace balíčku VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)  
 Popisuje různé způsoby, jak můžete podporovat souběžné instalace svých VSPackage a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Vytvoření balíčku Instalační služby systému Windows](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 V této části najdete přehled typických instalačních programů, které následují ke správné instalaci a integraci VSPackage do nástroje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Zjištění požadavků na systém](../../extensibility/internals/detecting-system-requirements.md)  
 Popisuje, jak může instalační program zjistit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a jeho součásti a zrušit instalaci, pokud nejsou splněny požadavky VSPackage.  
  
 [Správa komponent](../../extensibility/internals/component-management.md)  
 Popisuje, jak vyvíjet instalační program, který bude udržovat integritu předchozích verzí produktu.  
  
 [Výběr instalačního adresáře pro balíček VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Shrnuje možnosti pro hledání VSPackage.  
  
 [Registrace balíčku VSPackage](../../extensibility/internals/vspackage-registration.md)  
 Popisuje, jak jsou sady VSPackage registrovány v době instalace a proč je samoobslužná registrace špatná nápad.  
  
 [Nasazování typů projektů](../../extensibility/internals/deploying-project-types.md)  
 Popisuje použití nového Agregátoru typu projektu pro typy projektů spravovaného kódu.  
  
 [Postupy: Vygenerování informací registru pro instalační program ](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Vysvětluje, jak použít RegPkg.exe k vygenerování registračního manifestu pro spravovaný VSPackage.  
  
 [Příkazy, které se musí spustit po instalaci](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Vysvětluje, jak spustit příkazy po instalaci pro integraci VSPackage do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Odinstalace balíčku VSPackage pomocí Instalační služby systému Windows](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 Popisuje kroky, které instalační program musí provést, když uživatelé odinstalují VSPackage.  
  
## <a name="related-sections"></a>Související oddíly  
 [Instalace VSPackage](../../misc/installing-vspackages.md)  
 Popisuje, jak vytvářet a instalovat sady VSPackage a jak podporovat uživatele, kteří používají více verzí nástroje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ve stejnou dobu.
