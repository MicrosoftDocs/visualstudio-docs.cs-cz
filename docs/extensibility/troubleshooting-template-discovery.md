---
title: Řešení potíží se zjišťováním šablon v aplikaci Visual Studio | Microsoft Docs
description: Naučte se, jak povolit diagnostické protokolování pro řešení potíží s nasazením vlastních projektů a šablon v sadě Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: troubleshooting
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1ea99c1d74c06ab42ff86f07de4cf5c76e95de43
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151321"
---
# <a name="troubleshooting-template-installation"></a>Řešení potíží s instalací šablony

Pokud narazíte na problémy s nasazením šablony projektu nebo položky, můžete povolit protokolování diagnostiky.

::: moniker range="vs-2017"

1. Vytvořte soubor pkgdef ve složce *Common7\IDE\CommonExtensions* pro vaši instalaci. Například *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Vytvořte soubor pkgdef ve složce *Common7\IDE\CommonExtensions* pro vaši instalaci. Například *C:\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. Do souboru pkgdef přidejte následující:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Otevřete [Developer Command Prompt](../ide/reference/command-prompt-powershell.md) pro instalaci a spuštění `devenv /updateConfiguration` .

::: moniker range="vs-2017"

4. Otevřete Visual Studio a spusťte dialogová okna Nový projekt a nová položka k inicializaci obou stromů šablon.

   Protokol šablony se nyní zobrazí v **%localappdata%\Microsoft\VisualStudio\15.0_ [InstanceId] \VsTemplateDiagnosticsList.csv** (InstanceId odpovídá ID instalace vaší instance sady Visual Studio). Každá inicializace stromu šablon připojuje položky do tohoto protokolu.

::: moniker-end

::: moniker range=">=vs-2019"

4. Otevřete Visual Studio a spusťte dialogová okna **vytvořit nový projekt** a **Nová položka** k inicializaci obou stromů šablon.

   Protokol šablony se nyní zobrazí v **%localappdata%\Microsoft\VisualStudio\16.0_ [InstanceId] \VsTemplateDiagnosticsList.csv** (InstanceId odpovídá ID instalace vaší instance sady Visual Studio). Každá inicializace stromu šablon připojuje položky do tohoto protokolu.

::: moniker-end

Soubor protokolu obsahuje následující sloupce:

- **FullPathToTemplate**, která má následující hodnoty:

  - 1 pro nasazení založené na manifestu

  - 0 pro nasazení na základě disku

- **TemplateFileName**

- Vlastnosti jiných šablon

> [!NOTE]
> Pokud chcete protokolování zakázat, buď odeberte soubor pkgdef, nebo změňte hodnotu na a `EnableTemplateDiscoveryLog` `dword:00000000` pak znovu spusťte operaci `devenv /updateConfiguration` .

## <a name="see-also"></a>Viz také

- [Vytváření vlastních šablon projektů a položek](creating-custom-project-and-item-templates.md)
- [Řešení potíží s Visual Studiem](/troubleshoot/visualstudio/welcome-visual-studio/)
