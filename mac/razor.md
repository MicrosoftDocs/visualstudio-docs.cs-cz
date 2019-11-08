---
title: Vytváření webových aplikací Razor
description: Poskytuje informace o podpoře Razor v aplikacích ASP.NET Core v Visual Studio pro Mac.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.openlocfilehash: fe9ef921ccfc42b77bd08925805aeac6f4aec777
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73715872"
---
# <a name="create-razor-web-apps"></a>Vytváření webových aplikací Razor

Tato příručka nabízí Úvod k vytvoření první webové aplikace Razor. Podrobné pokyny najdete v tématu [Úvod do Razor Pages v ASP.NET Core](/aspnet/core/razor-pages/index).

Visual Studio pro Mac poskytuje podporu pro úpravy Razor, včetně IntelliSense a zvýrazňování syntaxe v souborech *. cshtml* . Novinka v sadě Visual Studio 2019 pro Mac 8.3 + je schopnost mít v rámci souboru Razor kontextovou technologii IntelliSense, takže dostanete IntelliSense, který odpovídá jazyku, který právě upravujete v rámci dokumentu.

![Úpravy Razor v Visual Studio pro Mac](media/razor-2019.png)

## <a name="creating-a-new-razor-project"></a>Vytvoření nového projektu Razor

1. Na úvodní obrazovce vyberte **Nový** a vytvořte nový projekt:

   ![Visual Studio pro Mac nový projekt](media/razor-new.png)
1. V dialogovém okně **Nový projekt** přejít na **.NET Core** > **App** > **Webová aplikace** a vyberte **Další**:

   ![Šablona projektu Razor](media/razor-new-project1.png)
1. Vyberte cílové rozhraní .NET Core (doporučujeme verzi 2,2 nebo novější) a pak vyberte **Další**. Vyberte název projektu a v případě potřeby přidejte podporu Gitu. Vyberte **vytvořit** a vytvořte projekt.

   ![Název projektu Razor](media/razor-new-project2.png)

   Visual Studio pro Mac otevře projekt v okně rozložení kódu.
1. Spusťte projekt bez ladění pomocí **příkazu Command + Option + F5**.

   Visual Studio spustí [Kestrel](/aspnet/core/fundamentals/servers/kestrel), otevře prohlížeč pro `https://localhost:5001`a zobrazí svou první webovou aplikaci Razor.

   ![Webová aplikace Razor v Safari](media/razor-webapp.png)

## <a name="project-anatomy"></a>Anatomie projektu

Webové aplikace Razor obsahují následující součásti.

### <a name="pages-folder"></a>Složka stránky

Tato složka obsahuje webové stránky projektu spolu s kódem na pozadí pro každý:
   - *\*soubor. cshtml* pro značky HTML a syntaxe Razor.
   - Soubor *\*. cshtml.cs* pro C# kód na pozadí pro zpracování událostí stránky.

Podpůrné soubory mají názvy začínající podtržítkem. Například soubor _Layout. cshtml nakonfiguruje prvky uživatelského rozhraní společné pro všechny stránky. Tento soubor nastaví navigační nabídku v horní části stránky a oznámení o autorských právech dole. Další informace najdete v tématu [rozložení v ASP.NET Core](/aspnet/core/mvc/views/layout).

### <a name="launch-settings"></a>Nastavení spuštění

Soubor *launchSettings. JSON* obsahuje nastavení služby IIS, adresu URL aplikace a další související nastavení.

### <a name="app-settings"></a>Nastavení aplikace

Soubor *appSettings. JSON* obsahuje konfigurační data, jako jsou připojovací řetězce.

Další informace o konfiguraci najdete v tématu [konfigurace v průvodci ASP.NET](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Složka wwwroot

Tato složka obsahuje statické soubory, jako jsou soubory HTML, JavaScript a CSS. Další informace najdete v tématu [statické soubory v ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Tento soubor obsahuje vstupní bod pro program. Další informace najdete v tématu [ASP.NET Core webového hostitele](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Tento soubor obsahuje kód, který nakonfiguruje chování aplikace, například to, jestli aplikace vyžaduje souhlas s soubory cookie. Další informace najdete v tématu [spuštění aplikace v ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="see-also"></a>Viz také:

Komplexnější průvodce vytvářením webových aplikací Razor najdete [v tématu Úvod do Razor Pages v ASP.NET Core](/aspnet/core/razor-pages/index).
