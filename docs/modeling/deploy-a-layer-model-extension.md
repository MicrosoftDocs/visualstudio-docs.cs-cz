---
title: Nasazení rozšíření pro modelování vrstev
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 98697642135627173c5a6f31e90bf1dd1d0caeaf
ms.sourcegitcommit: 8cdc6e2ad2341f34bd6b02859a7c975daa0c9320
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2018
ms.locfileid: "53307749"
---
# <a name="deploy-a-layer-model-extension"></a>Nasazení rozšíření pro modelování vrstev

Ostatní uživatelé sady Visual Studio můžete nainstalovat rozšíření, které vytvoříte pomocí sady Visual Studio modelování vrstev.

## <a name="install-your-extension"></a>Instalace rozšíření

Rozšíření je kompilováno do souboru VSIX, který si můžete nainstalovat na jiných počítačích. Také ho můžete nainstalovat na svém vývojovém počítači, aby bylo rozšíření k dispozici v instanci hlavní aplikace Visual Studio.

### <a name="to-install-the-extension"></a>Chcete-li nainstalovat rozšíření

1. V projektu, který obsahuje **source.vsix.manifest**, otevřete *bin* adresáře v Průzkumníku souborů.

2. Kopírovat  **\*VSIX** soubor do počítače, na kterém chcete nainstalovat rozšíření.

3. V cílovém počítači dvakrát klikněte na soubor *.vsix v Průzkumníku Windows.

    Otevře se instalátor VSIX.

### <a name="to-uninstall-the-extension"></a>Chcete-li odinstalovat rozšíření

1.  V sadě Visual Studio na **nástroje** nabídky, klikněte na tlačítko **rozšíření a aktualizace**.

2.  Klikněte na název rozšíření a pak klikněte na tlačítko **odinstalovat**.

## <a name="install-an-extension-on-team-foundation-server"></a>Nainstalovat rozšíření serveru Team Foundation Server

Servery Team Foundation Server, obvykle nemají nainstalovanou sadu Visual Studio, a proto nelze nainstalovat VSIX poklepáním. Je nutné nainstalovat rozšíření ručně.

### <a name="to-install-your-layer-extension-on-a-team-foundation-server-server"></a>Instalace rozšíření vrstvy na serveru Team Foundation Server

1.  Kopírování. *vsix* soubory z vývojového počítače do počítače Team Foundation Server (TFS).

     Uložte soubor VSIX v jednom z následujících umístění:

    -   Instalace pro všechny uživatele a služby:

         \Common7\IDE\Extensions\Microsoft %ProgramFiles%\Microsoft visual Studio [verze]

    -   Instalace pouze pro síťovou službu, který spouští sestavení:

         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft

    -   Pokud jste nakonfigurovali sestavení ke spuštění v interaktivním režimu jako určitý uživatel, můžete nainstalovat pouze pro tohoto uživatele:

         %LocalAppData%\Microsoft\VisualStudio\\[version]\Extensions\Microsoft

2.  Každý soubor VSIX rozbalte do složky ve stejném umístění:

    1.  Změna přípony názvu souboru z **VSIX** k **ZIP**.

    2.  Extrahujte obsah souboru .zip do složky.

    3.  Smazat soubor .zip

3.  Restartování serveru TFS.
