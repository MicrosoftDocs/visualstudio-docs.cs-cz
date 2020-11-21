---
title: Změna spouštěcího prostředí
description: Naučte se, jak přizpůsobit prostředí pro spouštění, takže se Visual studia otevře s nástroji, které jsou pro vás nejužitečnější.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 827ac67840f272e17cec6a7882a02b58dddbf925
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006260"
---
# <a name="customize-startup"></a>Přizpůsobení spuštění

Prostředí pro spouštění sady Visual Studio můžete přizpůsobit několika různými způsoby, jako je například otevření nejnovějšího řešení nebo pouze prázdného vývojového prostředí.

::: moniker range="vs-2017"

Můžete také zobrazit vlastní úvodní stránku, což je stránka XAML Windows Presentation Foundation (WPF) spuštěná v okně nástroje a lze v rámci ní spouštět interní příkazy sady Visual Studio.

::: moniker-end

## <a name="to-change-the-startup-item"></a>Změna položky po spuštění

1. Na panelu nabídek vyberte **Tools**  >  **Možnosti** nástroje.

2. Rozbalte položku **prostředí** a pak zvolte možnost **po spuštění**.

::: moniker range="vs-2017"

3. V seznamu **při spuštění** vyberte položku, která se má zobrazit po spuštění sady Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

3. V rozevíracím seznamu **při spuštění** vyberte možnost co se má stát po spuštění sady Visual Studio. Můžete zvolit z **okna Start** (což umožňuje otevřít nový nebo existující projekt), nejnovější **řešení** nebo **prázdné prostředí**.

::: moniker-end

::: moniker range="vs-2017"

## <a name="to-show-a-custom-start-page"></a>Zobrazení vlastní úvodní stránky

Pomocí sady Visual Studio SDK můžete [vytvořit vlastní úvodní stránku](../extensibility/creating-a-custom-start-page.md) , nebo ji použít jako jiný uživatel, který již byl vytvořen. Můžete například najít vlastní úvodní stránky na [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Chcete-li nainstalovat vlastní úvodní stránku, otevřete soubor *. vsix* nebo zkopírujte a vložte soubory počáteční stránky do složky *%UserProfile%\Documents\Visual Studio 2017 \ StartPages* na vašem počítači.

### <a name="to-select-which-custom-start-page-to-display"></a>Výběr vlastní úvodní stránky k zobrazení

1. Na panelu nabídek vyberte **Tools** > **Možnosti** nástroje.

1. Rozbalte položku **prostředí** a pak zvolte možnost **po spuštění**.

1. V seznamu **Přizpůsobit úvodní stránku** vyberte požadovanou stránku.

> [!TIP]
> Pokud chyba na vlastní úvodní stránce způsobí selhání sady Visual Studio, můžete otevřít sadu Visual Studio v bezpečném režimu a pak ji nastavit tak, aby používala výchozí úvodní stránku. Viz [/safemode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Viz také

- [Přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md)

::: moniker-end
