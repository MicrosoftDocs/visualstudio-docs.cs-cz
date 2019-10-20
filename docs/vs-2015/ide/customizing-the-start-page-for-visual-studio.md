---
title: Přizpůsobení úvodní stránky | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: 48
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f1c3dfb145e70665156c921cc9a6f740539bc4e6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665841"
---
# <a name="customizing-the-start-page-for-visual-studio"></a>Přizpůsobení úvodní stránky pro sadu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Úvodní stránku sady Visual Studio můžete přizpůsobit několika výchozími způsoby, jako je například zobrazení dialogového okna **Otevřít projekt** nebo otevření řešení, které bylo načteno v poslední době. Můžete také zobrazit vlastní úvodní stránku, což je stránka XAML Windows Presentation Foundation (WPF) spuštěná v okně nástroje a lze v rámci ní spouštět interní příkazy sady Visual Studio.

## <a name="customizing-the-default-start-page"></a>Přizpůsobení výchozí úvodní stránky

1. Na řádku nabídek klikněte na **nástroje**, **Možnosti**.

2. Rozbalte položku **prostředí**a pak zvolte možnost **po spuštění**.

3. V seznamu **při spuštění** vyberte položku, kterou chcete upravit.

## <a name="show-a-custom-start-page"></a>Zobrazení vlastní úvodní stránky

1. Vlastní úvodní stránku nainstalujte jedním z následujících způsobů:

    - Nainstalujte ji z [Visual Studio Marketplace](https://marketplace.visualstudio.com/), jiného webu nebo stránky v místním intranetu.

        > [!NOTE]
        > Pokud se vám líbí stránka, která je určena pro starší verzi sady Visual Studio, můžete stránku upgradovat pomocí sady Visual Studio SDK. Viz [Postupy: upgrade vlastní úvodní stránky sady Visual Studio](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).

         Otevřete soubor. vsix, který obsahuje vlastní úvodní stránku, nebo zkopírujte a vložte soubory Start-Page do složky **% USERPROFILE% \My Documents\Visual Studio 2015 \ StartPages** na vašem počítači.

    - Vytvořte si vlastní úvodní stránku, pokud jste nainstalovali sadu Visual Studio SDK.

         Další informace najdete v tématu [Vytvoření vlastní úvodní stránky](../misc/creating-your-own-start-page.md).

2. Na řádku nabídek klikněte na **nástroje**, **Možnosti**.

3. Rozbalte položku **prostředí**a pak zvolte možnost **po spuštění**.

4. V seznamu **Přizpůsobit úvodní stránku** vyberte požadovanou stránku.

> [!NOTE]
> Pokud chyba na vlastní úvodní stránce způsobí chybu sady Visual Studio, můžete sadu Visual Studio spustit v nouzovém režimu a pak ji nastavit tak, aby používala výchozí úvodní stránku. Viz [/safemode (devenv. exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Viz také
 [Přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [Vytvoření vlastní úvodní stránky](../misc/creating-your-own-start-page.md)
