---
title: Instalaci vlastní úvodní stránku nebo změňte položku při spuštění
ms.date: 02/01/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start Page
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e8f09302a459e31406d69596d43b5c39a67c8268
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064044"
---
# <a name="customize-the-start-page-for-visual-studio"></a>Přizpůsobení úvodní stránky pro sadu Visual Studio

Spuštění prostředí pro Visual Studio můžete přizpůsobit v několika různými způsoby, například zobrazením **otevřít projekt** dialogové okno nebo otevřením řešení, který byl načten jako poslední. Můžete také zobrazit vlastní úvodní stránku, což je stránka XAML Windows Presentation Foundation (WPF) spuštěná v okně nástroje a lze v rámci ní spouštět interní příkazy sady Visual Studio.

## <a name="to-change-the-startup-item"></a>Chcete-li změnit položku při spuštění

1. V panelu nabídky zvolte **nástroje** > **možnosti**.

1. Rozbalte **prostředí**a klikněte na tlačítko **spuštění**.

1. V **při spuštění** seznamu, vyberte položku, který se zobrazí po spuštění sady Visual Studio.

## <a name="to-show-a-custom-start-page"></a>Zobrazení vlastní úvodní stránky

Je možné [vytvořit vlastní úvodní stránky](../extensibility/creating-a-custom-start-page.md) pomocí sady Visual Studio SDK, nebo použijte takový, který už někdo jiný vytvořil. Například můžete najít na vlastní úvodní stránky [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Chcete-li nainstalovat vlastní úvodní stránku, otevřete *VSIX* souboru, nebo zkopírujte a vložte soubory úvodní stránky do *%USERPROFILE%\Documents\Visual Studio 2017\StartPages* složky v počítači.

### <a name="to-select-which-custom-start-page-to-display"></a>Chcete-li vybrat kterou vlastní úvodní stránku zobrazení

1. V panelu nabídky zvolte **nástroje** > **možnosti**.

1. Rozbalte **prostředí**a klikněte na tlačítko **spuštění**.

1. V **přizpůsobit úvodní stránku** , zvolte na stránce, který chcete.

> [!NOTE]
> Pokud chyba na vlastní úvodní stránce způsobí chybu sady Visual Studio, můžete sadu Visual Studio spustit v nouzovém režimu a pak ji nastavit tak, aby používala výchozí úvodní stránku. Zobrazit [/safemode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Viz také:

- [Přizpůsobení prostředí IDE sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md)