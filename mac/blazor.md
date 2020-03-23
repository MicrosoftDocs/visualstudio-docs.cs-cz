---
title: Vytvoření webových aplikací Blazor
description: Obsahuje informace o podpoře Blazoru v aplikacích ASP.NET Core ve Visual Studiu for Mac.
author: jongalloway
ms.author: jogallow
ms.date: 12/17/2019
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
ms.openlocfilehash: dbc49a0ea9b4e4fa7880b6226331d447339b6575
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75737584"
---
# <a name="create-blazor-web-apps"></a>Vytvoření webových aplikací Blazor

Tato příručka nabízí úvod do vytváření vaší první webové aplikace Blazor. Podrobnější pokyny naleznete v [tématu Úvod do ASP.NET Core Blazor](/aspnet/core/blazor/index).

Visual Studio pro Mac (počínaje verzí 8.4) zahrnuje podporu pro vývoj a publikování ASP.NET aplikací Core Blazor Server. Blazor je framework pro vytváření interaktivního webového uživatelského rozhraní na straně klienta s rozhraním .NET, které nabízí následujícím výhodám webovým vývojářům:

* Místo JavaScriptu napište kód v jazyce C#.
* Využijte existující ekosystém .NET knihoven .NET.
* Sdílejte logiku aplikace napříč serverem a klientem.
* Využijte výhod . net výkon, spolehlivost a zabezpečení.
* Zůstaňte produktivní díky Visual Studiu na PC, Linuxu a macOS.
* Nazákladě společné sady jazyků, architektur a nástrojů, které jsou stabilní, bohaté na funkce a snadno použitelné.

## <a name="creating-a-new-blazor-project"></a>Vytvoření nového projektu Blazor

1. V **úvodním okně**vyberte **Nový** a vytvořte nový projekt:

   ![Úvodní okno Visual Studia pro Mac se zvýrazněným novým výběrem](media/blazor-new-project.png)
1. V dialogovém okně **Nový projekt** vyberte **aplikaci .NET Core** > **App** > **Blazor Server** app a vyberte **Další**: ![Vyberte šablonu pro nový dialog projektu s vybranou šablonou aplikace Blazor Server](media/blazor-project-template.png)

1. Jako cílovou architekturu vyberte .NET Core 3.1 a pak vyberte **Další**. 
   ![Konfigurace nového dialogového okna aplikace Blazor Server zobrazeného s vybranou možností Target Framework na rozhraní .NET Core 3.1](media/blazor-select-target-framework.png)

1. Vyberte název projektu a v případě potřeby přidejte podporu Gitu. Vyberte **Vytvořit** a vytvořte projekt.
   ![BKonfigurace nového dialogového okna aplikace Blazor Server se zobrazí při zadávání názvu projektu](media/blazor-name-project.png)

   Visual Studio pro Mac otevře projekt v okně rozložení kódu.
1. Chcete-li aplikaci spustit**spustit bez ladění,** vyberte spustit spustit bez ladění. **Run** > 

   Visual Studio spustí [Kestrel](/aspnet/core/fundamentals/servers/kestrel), `https://localhost:5001`otevře prohlížeč na , a zobrazí vaši webovou aplikaci Blazor.

   ![Blazor webová aplikace v Safari](media/blazor-new-app-in-edge.png)

## <a name="blazor-support-in-visual-studio-for-mac"></a>Podpora pro Blazor ve Visual Studiu for Mac

Visual Studio pro Mac (počínaje verzí 8.4) obsahuje nové funkce, které vám pomohou vytvořit nové projekty serveru Blazor. Také vám poskytuje standardní podporu, kterou byste očekávali, jako je vytváření, běh a ladění projektů Blazor. 

V návodu výše jsme viděli, jak vám šablona projektu Blazor Server App pomáhá vytvořit nový projekt Aplikace Blazor Server. Podívejme se na některé další funkce v sadě Visual Studio for Mac, které podporují vývoj projektu serveru Blazor.

### <a name="editor-support-for-razor-files"></a>Podpora editoru pro soubory *.razor*
Visual Studio for Mac obsahuje podporu pro editaci souborů .razor – většinu souborů, které budete používat při vytváření aplikací Blazor. Verze rozhraní IDE pro Windows a Mac sdílejí stejný editor pro soubory .razor. Uvidíte plnou podporu vybarvení a dokončení pro vaše .razor soubory, včetně dokončení komponent Razor deklarované v projektu.

![Okno editoru Visual Studio pro Mac zobrazující Intellisense for Blazor](media/blazor-intellisense.png)

### <a name="publishing-blazor-applications-to-azure-app-service"></a>Publikování aplikací Blazor do služby Azure App Service
Aplikace Blazor můžete také publikovat přímo do služby Azure App Service. Pokud nemáte účet Azure pro spuštění aplikace Blazor v Azure, můžete [si vždy zaregistrovat bezplatnou aplikaci,](https://azure.microsoft.com/free) která také přichází 12 měsíců bezplatných populárních služeb, kreditů Azure ve výši $ 200 a více než 25 vždy bezplatných služeb.

![Visual Studio pro Mac zobrazující prostředí publikování Azure](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>Anatomie projektu

Blazor webové aplikace obsahují několik adresářů a souborů ve výchozím nastavení. Jak začínáte, zde jsou hlavní, které budete muset znát:

### <a name="pages-folder"></a>Složka Stránky

Tato složka obsahuje webové stránky projektu, které používají *příponu .razor.*

### <a name="shared-folder"></a>Sdílená složka

Tato složka obsahuje sdílené součásti, také pomocí *.razor* rozšíření. Uvidíte, že to zahrnuje *MainLayout.razor*, který se používá k definování společné rozložení v celé aplikaci. Obsahuje také sdílenou komponentu *NavMenu.razor,* která se používá na všech stránkách. Pokud vytváříte opakovaně použitelné součásti, přejdou do **sdílené** složky.

### <a name="app-settings"></a>Nastavení aplikace

Soubor *appSettings.json* obsahuje konfigurační data, jako jsou připojovací řetězce.

Další informace o konfiguraci naleznete [v příručce Konfigurace v ASP.NET](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>wwwkořenová složka

Tato složka obsahuje statické soubory, například soubory HTML, JavaScript a CSS. Další informace naleznete [v tématu Statické soubory v ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Tento soubor obsahuje vstupní bod programu. Další informace naleznete [v tématu ASP.NET Core Web Host](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Tento soubor obsahuje kód, který konfiguruje chování aplikace, například zda aplikace vyžaduje souhlas s cookies. Další informace najdete [v tématu spuštění aplikace v ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="summary"></a>Souhrn
V tomto kurzu jste viděli, jak vytvořit novou aplikaci Blazor Server v sadě Visual Studio for Mac, a dozvěděli jste se o některých funkcích, které Visual Studio pro Mac nabízí, aby vám pomohly vytvářet aplikace Blazor.

## <a name="see-also"></a>Viz také

Podrobnější ho průvodce vytvářením webových aplikací Blazor najdete [v tématu Úvod do ASP.NET Core Blazor](/aspnet/core/blazor/index).
