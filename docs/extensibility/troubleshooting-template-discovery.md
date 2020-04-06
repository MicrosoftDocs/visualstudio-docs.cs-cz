---
title: Poradce při potížích s zjišťováním šablony v sadě Visual Studio | Dokumenty společnosti Microsoft
ms.date: 01/02/2018
ms.topic: conceptual
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 078d06c797c3b228c1ea5b1d836dceb0394b3174
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698938"
---
# <a name="troubleshooting-template-installation"></a>Poradce při potížích s instalací šablony

Pokud narazíte na problémy s nasazením šablon projektu nebo položek, můžete povolit protokolování diagnostiky.

::: moniker range="vs-2017"

1. Vytvořte soubor pkgdef ve složce *Common7\IDE\CommonExtensions* pro vaši instalaci. Například *C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Vytvořte soubor pkgdef ve složce *Common7\IDE\CommonExtensions* pro vaši instalaci. Například *C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. Do souboru pkgdef přidejte následující:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Otevřete [příkazový řádek pro vývojáře](/dotnet/framework/tools/developer-command-prompt-for-vs) pro instalaci a spuštění `devenv /updateConfiguration`.

::: moniker range="vs-2017"

4. Otevřete Visual Studio a spusťte dialogové okna Nový projekt a Nová položka pro inicializaci obou stromů šablon.

   Protokol šablony se nyní zobrazí v **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instance odpovídá ID instalace instance sady Visual Studio). Každá inicializace stromu šablony připojí položky k tomuto protokolu.

::: moniker-end

::: moniker range=">=vs-2019"

4. Otevřete Visual Studio a spusťte dialogové **okna Vytvořit nový projekt** a Nová **položka** pro inicializaci obou stromů šablon.

   Protokol šablony se nyní zobrazí v **%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instance odpovídá ID instalace instance sady Visual Studio). Každá inicializace stromu šablony připojí položky k tomuto protokolu.

::: moniker-end

Soubor protokolu obsahuje následující sloupce:

- **FullPathToTemplate**, který má následující hodnoty:

  - 1 pro nasazení založené na manifestu

  - 0 pro nasazení na disku

- **Název souboru šablony**

- Další vlastnosti šablony

> [!NOTE]
> Chcete-li protokolování zakázat, odeberte soubor `EnableTemplateDiscoveryLog` pkgdef nebo změňte hodnotu položky `dword:00000000`na položku a spusťte jej `devenv /updateConfiguration` znovu.

## <a name="see-also"></a>Viz také

- [Vytváření vlastních šablon projektů a položek](creating-custom-project-and-item-templates.md)
