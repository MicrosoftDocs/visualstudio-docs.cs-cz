---
title: Podpora více verzí sady Visual Studio | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699478"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Podpora více verzí sady Visual Studio
Termín *vedle sebe* znamená, že můžete nainstalovat a udržovat více verzí produktu ve stejném počítači. Pro VSPackage, to znamená, že uživatel může mít na stejném počítači nainstalovanou několik verzí sady Visual Studio. Nicméně nemůžete mít nahrané souběžné verze vašich VSPackage do jediné verze sady Visual Studio.

 Před tím, než bude možné sadu VSPackage načíst do souběžných verzí sady Visual Studio, vezměte v úvahu následující:

- Musíte určit, kterou souběžnou implementační strategii chcete sledovat.

   Další informace najdete v tématu [Výběr mezi sdílenými a verzemi VSPackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- Vaše formáty souborů řešení a projektu musí vyhovovat vaší strategii implementace.

   Další informace naleznete v tématu [Upgrade vlastních projektů](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) a [registrace přípon názvů souborů pro souběžná nasazení](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Váš instalační program musí zpracovat strategii implementace, aby se součásti se správou verzí a také součásti sdílené ve všech verzích byly správně nainstalovány a registrovány.

   Další informace najdete v tématu [Instalace VSPackage pomocí Instalační služba systému Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) a také v rámci [správy součástí](../extensibility/internals/component-management.md).

  > [!NOTE]
  > Instalace verze sady Visual Studio nainstaluje také odpovídající verzi .NET Framework. Například instalace sady Visual Studio 2010 a sady Visual Studio 2012 na stejném počítači nainstaluje také verze 4,0 a 4,5 .NET Framework v uvedeném pořadí.

## <a name="in-this-section"></a>V tomto oddílu
- [Volba mezi sdílenými a Sesprávou verzí VSPackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md) Vysvětluje, jak vyřešit souběžné problémy v balíčku VSPackage.

- [Registrace přípon názvů souborů pro souběžná nasazení](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) Popisuje, jak může VSPackage registrovat přidružení souborů v souběžném scénáři.

## <a name="related-sections"></a>Související oddíly
- [Instalace balíčků VSPackage pomocí Instalační služby systému Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)
