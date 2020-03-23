---
title: Změna prostředí při spuštění
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567213"
---
# <a name="customize-startup"></a>Přizpůsobení spuštění

Prostředí pro spuštění sady Visual Studio můžete přizpůsobit několika různými způsoby, například otevřením nejnovějšího řešení nebo pouze prázdným vývojovém prostředí.

::: moniker range="vs-2017"

Můžete také zobrazit vlastní úvodní stránku, což je stránka XAML Windows Presentation Foundation (WPF) spuštěná v okně nástroje a lze v rámci ní spouštět interní příkazy sady Visual Studio.

::: moniker-end

## <a name="to-change-the-startup-item"></a>Změna položky po spuštění

1. Na řádku nabídek zvolte**Možnosti** **nástrojů** > .

2. Rozbalte **možnost Prostředí**a pak zvolte **Možnost Spustit**.

::: moniker range="vs-2017"

3. V seznamu **Při spuštění** vyberte položku, která se má zobrazit po spuštění sady Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

3. V **seznamu Při spuštění otevřete,** zvolte, co chcete, aby se stalo po spuštění sady Visual Studio. Můžete si vybrat z **okna Start** (které umožňuje otevřít nový nebo existující projekt), **Nejnovější řešení**nebo Prázdné **prostředí**.

::: moniker-end

::: moniker range="vs-2017"

## <a name="to-show-a-custom-start-page"></a>Zobrazení vlastní úvodní stránky

Můžete [vytvořit vlastní úvodní stránku](../extensibility/creating-a-custom-start-page.md) pomocí sady Visual Studio SDK nebo použít tu, kterou už vytvořil někdo jiný. Vlastní úvodní stránky najdete například na [webu Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Chcete-li nainstalovat vlastní úvodní stránku, otevřete soubor *.vsix* nebo zkopírujte a vložte soubory úvodní stránky do složky *%USERPROFILE%\Documents\Visual Studio 2017\StartPages* v počítači.

### <a name="to-select-which-custom-start-page-to-display"></a>Výběr vlastní úvodní stránky, která se má zobrazit

1. Na řádku nabídek zvolte **Možnosti** **nástrojů** > .

1. Rozbalte **možnost Prostředí**a pak zvolte **Možnost Spustit**.

1. V seznamu **Přizpůsobit úvodní stránku** vyberte požadovanou stránku.

> [!TIP]
> Pokud chyba na vlastní úvodní stránce způsobí selhání sady Visual Studio, můžete aplikaci Visual Studio otevřít v nouzovém režimu a nastavit ji tak, aby používala výchozí úvodní stránku. Viz [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Viz také

- [Přizpůsobení prostředí IDE sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md)

::: moniker-end
