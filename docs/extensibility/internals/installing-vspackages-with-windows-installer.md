---
title: Instalace balíčků VSPackages s Instalační službou systému Windows | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2eb90dbffa9f04cd17afa70d2bdfc59205bc99cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707466"
---
# <a name="installing-vspackages-with-windows-installer"></a>Instalace balíčků VSPackage pomocí Instalační služby systému Windows
Integrace vspackage do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vyžaduje více než jen kopírování souborů do počítače uživatele. Instalační program vspackage musí nainstalovat VSPackage a jeho závislé soubory a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zaregistrovat a integrovat je do . VSPackage můžete využít funkce integrace, jako je například zobrazení ikony na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] úvodní obrazovce a o dialogovém okně.

 Soubory Instalační služby systému Microsoft Windows jsou doporučeným způsobem distribuce balíčků VSPackages. Snadno použitelné balíčky Instalační služby systému Windows lze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]spustit v libovolném operačním systému Windows podporovaném programem . Další informace naleznete v [instalační službě systému Windows](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).

## <a name="in-this-section"></a>V tomto oddílu
- [Základní informace o Instalační službě systému Windows](../../extensibility/internals/windows-installer-basics.md)

 Obsahuje přehled Instalační služby systému Windows.

- [Scénáře instalace balíčku VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)

 Popisuje různé způsoby, jak můžete podporovat souběžné instalace vspackages a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [Vytvoření balíčku Instalační služby systému Windows](../../extensibility/internals/authoring-a-windows-installer-package.md)

 Obsahuje přehled typických kroků, kterými instalační programy postupují [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]pro správnou instalaci a integraci balíčků VSPackages do aplikace .

- [Zjištění požadavků na systém](../../extensibility/internals/detecting-system-requirements.md)

 Popisuje, jak instalační program [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] může zjistit a jeho součásti a zrušit instalaci, pokud nejsou splněny požadavky VSPackage.

- [Správa komponent](../../extensibility/internals/component-management.md)

 Popisuje, jak vyvinout instalační program, který bude udržovat integritu předchozích verzí produktu.

- [Výběr instalačního adresáře pro balíček VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)

 Shrnuje možnosti pro vyhledání VSPackages.

- [Registrace balíčku VSPackage](../../extensibility/internals/vspackage-registration.md)

 Popisuje, jak jsou v době instalace registrovány vbalíčcích VSPackages a proč je vlastní registrace špatný nápad.

- [Nasazování typů projektů](../../extensibility/internals/deploying-project-types.md)

 Popisuje, jak použít nový agregátor typu projektu pro typy projektů spravovaného kódu.

- [Postupy: Vygenerování informací registru pro instalační program ](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)

 Vysvětluje, jak použít RegPkg.exe generovat manifest registrace pro spravované VSPackage.

- [Příkazy, které se musí spustit po instalaci](../../extensibility/internals/commands-that-must-be-run-after-installation.md)

 Vysvětluje, jak spustit příkazy po instalaci integrovat [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackages do aplikace .

- [Odinstalace balíčku VSPackage pomocí Instalační služby systému Windows](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)

 Popisuje kroky, které musí instalační program provést při odinstalaci balíčku VSPackage uživateli.
