---
title: Změna spouštěcího prostředí
ms.date: 02/01/2017
ms.topic: conceptual
f1_keywords:
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start Page
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 281a0c43c0163d158151683e9fdc483dfc1709f5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75567213"
---
# <a name="customize-startup"></a>Přizpůsobení spuštění

Prostředí pro spouštění sady Visual Studio můžete přizpůsobit několika různými způsoby, jako je například otevření nejnovějšího řešení nebo pouze prázdného vývojového prostředí.

::: moniker range="vs-2017"

Můžete také zobrazit vlastní úvodní stránku, což je stránka XAML Windows Presentation Foundation (WPF) spuštěná v okně nástroje a lze v rámci ní spouštět interní příkazy sady Visual Studio.

::: moniker-end

## <a name="to-change-the-startup-item"></a>Chcete-li změnit položku při spuštění

1. V panelu nabídky zvolte **nástroje** > **možnosti**.

2. Rozbalte **prostředí**a klikněte na tlačítko **spuštění**.

::: moniker range="vs-2017"

3. V **při spuštění** seznamu, vyberte položku, který se zobrazí po spuštění sady Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

3. V rozevíracím seznamu **při spuštění** vyberte možnost co se má stát po spuštění sady Visual Studio. Můžete zvolit z **okna Start** (což umožňuje otevřít nový nebo existující projekt), nejnovější **řešení**nebo **prázdné prostředí**.

::: moniker-end

::: moniker range="vs-2017"

## <a name="to-show-a-custom-start-page"></a>Zobrazení vlastní úvodní stránky

Je možné [vytvořit vlastní úvodní stránky](../extensibility/creating-a-custom-start-page.md) pomocí sady Visual Studio SDK, nebo použijte takový, který už někdo jiný vytvořil. Například můžete najít na vlastní úvodní stránky [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Chcete-li nainstalovat vlastní úvodní stránku, otevřete *VSIX* souboru, nebo zkopírujte a vložte soubory úvodní stránky do *%USERPROFILE%\Documents\Visual Studio 2017\StartPages* složky v počítači.

### <a name="to-select-which-custom-start-page-to-display"></a>Chcete-li vybrat kterou vlastní úvodní stránku zobrazení

1. Na panelu nabídek vyberte možnost **nástroje** > **Možnosti**.

1. Rozbalte **prostředí**a klikněte na tlačítko **spuštění**.

1. V **přizpůsobit úvodní stránku** , zvolte na stránce, který chcete.

> [!TIP]
> Pokud chyba na vlastní úvodní stránce způsobí selhání sady Visual Studio, můžete otevřít sadu Visual Studio v bezpečném režimu a pak ji nastavit tak, aby používala výchozí úvodní stránku. Zobrazit [/safemode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Viz také:

- [Přizpůsobení prostředí IDE sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md)

::: moniker-end
