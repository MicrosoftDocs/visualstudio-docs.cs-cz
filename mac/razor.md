---
title: Vytváření webových aplikací Razor
description: Obsahuje informace o podpoře Razor v aplikacích ASP.NET Core ve Visual Studiu for Mac.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.openlocfilehash: fe9ef921ccfc42b77bd08925805aeac6f4aec777
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "73715872"
---
# <a name="create-razor-web-apps"></a>Vytváření webových aplikací Razor

Tato příručka nabízí úvod do vytváření své první webové aplikace Razor. Podrobnější pokyny naleznete v [tématu Úvod do stránek Razor pages v ASP.NET jádru](/aspnet/core/razor-pages/index).

Visual Studio for Mac poskytuje podporu pro úpravy Razor, včetně Technologie IntelliSense a zvýraznění syntaxe v souborech *.cshtml.* Novinkou ve Visual Studiu 2019 pro Mac 8.3+ je možnost mít kontextově uvědomující se Technologie IntelliSense v souboru Razor, takže obdržíte technologie IntelliSense, která odpovídá jazyku, který právě upravujete v dokumentu.

![Úpravy holicí strojek v Visual Studiu pro Mac](media/razor-2019.png)

## <a name="creating-a-new-razor-project"></a>Vytvoření nového projektu Razor

1. Na úvodní obrazovce vyberte **Nový** a vytvořte nový projekt:

   ![Visual Studio pro Mac nový projekt](media/razor-new.png)
1. V dialogovém okně **Nový projekt** přejděte na**webovou aplikaci** **.NET Core** > **App** > a vyberte **Další**:

   ![Šablona projektu Razor](media/razor-new-project1.png)
1. Vyberte cílovou architekturu .NET Core (doporučujeme verzi 2.2 nebo novější) a pak vyberte **Další**. Vyberte název projektu a v případě potřeby přidejte podporu Gitu. Vyberte **Vytvořit** a vytvořte projekt.

   ![Razor název projektu](media/razor-new-project2.png)

   Visual Studio pro Mac otevře projekt v okně rozložení kódu.
1. Spusťte projekt bez ladění pomocí **příkazu Command+Option+F5**.

   Visual Studio spustí [Kestrel](/aspnet/core/fundamentals/servers/kestrel), `https://localhost:5001`otevře prohlížeč na , a zobrazí první Razor webové aplikace.

   ![Holicí strojek webová aplikace v Safari](media/razor-webapp.png)

## <a name="project-anatomy"></a>Anatomie projektu

Holicí strojek webové aplikace obsahují následující komponenty.

### <a name="pages-folder"></a>Složka Stránky

Tato složka obsahuje webové stránky projektu spolu s kódem na pozadí pro každou z nich:
   - Soubor * \*.cshtml* pro značku HTML a syntaxi Razor.
   - Soubor * \*.cshtml.cs* pro váš kód C# pro zpracování událostí stránky.

Podpůrné soubory mají názvy, které začínají podtržítkem. Například soubor _Layout.cshtml konfiguruje prvky uživatelského rozhraní společné pro všechny stránky. Tento soubor nastaví navigační nabídku v horní části stránky a oznámení o autorských právech v dolní části. Další informace naleznete [v tématu Layout v ASP.NET Core](/aspnet/core/mvc/views/layout).

### <a name="launch-settings"></a>Nastavení spuštění

Soubor *launchSettings.json* obsahuje nastavení služby IIS, adresu URL aplikace a další související nastavení.

### <a name="app-settings"></a>Nastavení aplikace

Soubor *appSettings.json* obsahuje konfigurační data, jako jsou připojovací řetězce.

Další informace o konfiguraci naleznete [v příručce Konfigurace v ASP.NET](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>wwwkořenová složka

Tato složka obsahuje statické soubory, například soubory HTML, JavaScript a CSS. Další informace naleznete [v tématu Statické soubory v ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Tento soubor obsahuje vstupní bod programu. Další informace naleznete [v tématu ASP.NET Core Web Host](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Tento soubor obsahuje kód, který konfiguruje chování aplikace, například zda aplikace vyžaduje souhlas s cookies. Další informace najdete [v tématu spuštění aplikace v ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="see-also"></a>Viz také

Podrobnější ho průvodce vytvářením webových aplikací Razor najdete [v tématu Úvod do stránek Razor ve ASP.NET Core](/aspnet/core/razor-pages/index).
