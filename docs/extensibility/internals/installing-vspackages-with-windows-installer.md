---
title: Instalace VSPackage pomocí Instalační služba systému Windows | Microsoft Docs
description: Naučte se používat Microsoft Instalační služba systému Windows k instalaci VSPackage a jeho závislých souborů a jejich registraci a integraci do sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1638f6d041dda28ca79492ba2c8e6ef772ce8bc7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074662"
---
# <a name="installing-vspackages-with-windows-installer"></a>Instalace balíčků VSPackage pomocí Instalační služby systému Windows
Integrace sady VSPackage do systému [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vyžaduje více než pouze kopírování souborů do počítače uživatele. Instalační program VSPackage musí nainstalovat rozhraní VSPackage a jeho závislé soubory a zaregistrovat je a integrovat je do nástroje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Rozhraní VSPackage může využít výhod integračních funkcí, jako je například zobrazení ikony na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] úvodní obrazovce a dialogového okna o aplikaci.

 Soubory Microsoft Instalační služba systému Windows jsou doporučeným způsobem pro distribuci VSPackage. Snadno použitelné balíčky Instalační služba systému Windows lze spustit na jakémkoli operačním systému Windows, který podporuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Další informace najdete v tématu [Instalační služba systému Windows](/previous-versions/2kt85ked(v=vs.120)).

## <a name="in-this-section"></a>V tomto oddílu
- [Základní informace o Instalační službě systému Windows](../../extensibility/internals/windows-installer-basics.md)

 Poskytuje přehled Instalační služba systému Windows.

- [Scénáře instalace balíčku VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)

 Popisuje různé způsoby, jak můžete podporovat souběžné instalace svých VSPackage a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Vytvoření balíčku Instalační služby systému Windows](../../extensibility/internals/authoring-a-windows-installer-package.md)

 V této části najdete přehled typických instalačních programů, které následují ke správné instalaci a integraci VSPackage do nástroje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Zjištění požadavků na systém](../../extensibility/internals/detecting-system-requirements.md)

 Popisuje, jak může instalační program zjistit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a jeho součásti a zrušit instalaci, pokud nejsou splněny požadavky VSPackage.

- [Správa komponent](../../extensibility/internals/component-management.md)

 Popisuje, jak vyvíjet instalační program, který bude udržovat integritu předchozích verzí produktu.

- [Výběr instalačního adresáře pro balíček VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)

 Shrnuje možnosti pro hledání VSPackage.

- [Registrace balíčku VSPackage](../../extensibility/internals/vspackage-registration.md)

 Popisuje, jak jsou sady VSPackage registrovány v době instalace a proč je samoobslužná registrace špatná nápad.

- [Nasazování typů projektů](../../extensibility/internals/deploying-project-types.md)

 Popisuje použití nového Agregátoru typu projektu pro typy projektů spravovaného kódu.

- [Postupy: Vygenerování informací registru pro instalační program ](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)

 Vysvětluje, jak použít RegPkg.exe k vygenerování registračního manifestu pro spravovaný VSPackage.

- [Příkazy, které se musí spustit po instalaci](../../extensibility/internals/commands-that-must-be-run-after-installation.md)

 Vysvětluje, jak spustit příkazy po instalaci pro integraci VSPackage do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Odinstalace balíčku VSPackage pomocí Instalační služby systému Windows](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)

 Popisuje kroky, které instalační program musí provést, když uživatelé odinstalují VSPackage.