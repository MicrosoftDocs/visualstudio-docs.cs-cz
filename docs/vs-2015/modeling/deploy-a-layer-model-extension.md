---
title: Nasazení rozšíření modelu vrstvy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5c11c952223854ff1b4b963e24615e7abe831496
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669866"
---
# <a name="deploy-a-layer-model-extension"></a>Nasazení rozšíření pro modelování vrstev
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jiní uživatelé sady Visual Studio mohou instalovat rozšíření modelování vrstev, které vytvoříte pomocí sady Visual Studio.

## <a name="installing-your-extension"></a>Instalace rozšíření
 Vaše rozšíření je zkompilováno do souboru VSIX, který můžete nainstalovat do jiných počítačů. Můžete ji také nainstalovat na vývojový počítač, aby bylo rozšíření k dispozici v hlavní instanci aplikace Visual Studio.

#### <a name="to-install-the-extension"></a>Instalace rozšíření

1. V projektu, který obsahuje **source. VSIX. manifest**, otevřete **přihrádku \\ \\ *** v Průzkumníkovi souborů.

2. Zkopírujte soubor ** \* . vsix** do počítače, do kterého chcete nainstalovat rozšíření.

3. V cílovém počítači poklikejte na soubor *. vsix v Průzkumníkovi Windows.

    Otevře se instalační program VSIX.

#### <a name="to-uninstall-the-extension"></a>Odinstalace rozšíření

1. V aplikaci Visual Studio v nabídce **nástroje** klikněte na možnost **rozšíření a aktualizace**.

2. Klikněte na název rozšíření a pak klikněte na **odinstalovat**.

## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Instalace rozšíření na server Team Foundation Build
 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] na serverech není normálně nainstalována aplikace Visual Studio, takže nemůžete nainstalovat VSIX dvojitým kliknutím na něj. Instalace nástroje [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] zahrnuje některé součásti, které umožňují spuštění rozšíření VSIX, ale je nutné nainstalovat rozšíření ručně.

#### <a name="to-install-your-layer-extension-on-a-esprbuild-server"></a>Instalace rozšíření vrstvy na [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] Server

1. Zkopírujte soubory **. vsix** z vývojového počítače do [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] počítače.

     Soubor VSIX umístěte do jednoho z následujících umístění:

    - Instalace pro všechny uživatele a služby:

         %ProgramFiles%\Microsoft Visual Studio [verze] \Common7\IDE\Extensions\Microsoft

    - Pro instalaci jenom pro síťovou službu, která běží [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] :

         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio \\ [verze] \Extensions\Microsoft

    - Pokud jste nakonfigurovali, [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] aby se spouštěla v interaktivním režimu jako konkrétní uživatel, můžete pro tohoto uživatele nainstalovat jenom:

         %LocalAppData%\Microsoft\VisualStudio \\ [verze] \Extensions\Microsoft

        > [!NOTE]
        > % LocalAppData% je obvykle *jednotka*: uživatel*uživatelské_jméno*AppDataLocal.

2. Rozbalte jednotlivé soubory VSIX do složky ve stejném umístění:

    1. Změňte příponu názvu souboru z **. vsix** na **. zip**.

    2. Extrahujte obsah souboru. zip do složky.

    3. Odstraňte soubor. zip.

3. Restartujte [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] .
