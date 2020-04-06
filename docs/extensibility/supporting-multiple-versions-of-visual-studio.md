---
title: Podpora více verzí sady Visual Studio | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d571f1be4da45ff5ed6b2538cfb515930bde1de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699478"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Podpora více verzí sady Visual Studio
Termín *vedle sebe* znamená, že můžete nainstalovat a udržovat více verzí produktu ve stejném počítači. Pro VSPackages to znamená, že uživatel může mít několik verzí sady Visual Studio nainstalovaných ve stejném počítači. Však nelze mít vedle sebe verze vspackages načtendo jedné verze sady Visual Studio.

 Před provedením VSPackage lze načíst do souběžné verze sady Visual Studio, zvažte následující:

- Je nutné určit, kterou strategii implementace vedle sebe chcete dodržovat.

   Další informace naleznete [v tématu Výběr mezi sdílenými a s verzemi vspackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- Formáty souborů řešení a projektu musí odpovídat vaší strategii implementace.

   Další informace naleznete [v tématu Upgrade vlastních projektů](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) a registrace [přípon názvů souborů pro souběžná nasazení](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Instalační program musí zpracovat strategii implementace tak, aby verze komponenty a také součásti sdílené ve všech verzích, jsou správně nainstalovány a registrovány.

   Další informace naleznete [v tématu Instalace balíčků VSPackages with Installer systému Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) a také správa [součástí](../extensibility/internals/component-management.md).

  > [!NOTE]
  > Instalace verze sady Visual Studio také nainstaluje odpovídající verzi rozhraní .NET Framework. Například instalace sady Visual Studio 2010 a Visual Studio 2012 do stejného počítače také nainstaluje verze 4.0 a 4.5 rozhraní .NET Framework.

## <a name="in-this-section"></a>V tomto oddílu
- [Výběr mezi sdílenými a s verzemi vsbalíčků](../extensibility/choosing-between-shared-and-versioned-vspackages.md) Vysvětluje, jak vyřešit problémy vedle sebe v balíčku VSPackage.

- [Registrace přípon názvů souborů pro souběžná nasazení](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) Popisuje, jak může váš VSPackage zaregistrovat přidružení souborů v případě souběžných souborů.

## <a name="related-sections"></a>Související oddíly
- [Instalace balíčků VSPackage pomocí Instalační služby systému Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)
