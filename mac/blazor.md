---
title: Vytváření webových aplikací v Blazor
description: Poskytuje informace o podpoře Blazor v aplikacích ASP.NET Core v Visual Studio pro Mac.
author: jongalloway
ms.author: jogallow
ms.date: 12/17/2019
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
ms.openlocfilehash: dbc49a0ea9b4e4fa7880b6226331d447339b6575
ms.sourcegitcommit: d04441e3c5f2eff3a63f7aca35ccf7ecac90fb44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737584"
---
# <a name="create-blazor-web-apps"></a>Vytváření webových aplikací v Blazor

Tato příručka nabízí Úvod k vytvoření první webové aplikace v Blazor. Podrobné pokyny najdete v tématu [Úvod do ASP.NET Core Blazor](/aspnet/core/blazor/index).

Visual Studio pro Mac (počínaje verzí 8,4) zahrnuje podporu pro vývoj a publikování ASP.NET Corech serverových aplikací Blazor. Blazor je architektura pro vytváření interaktivního webového uživatelského rozhraní na straně klienta s .NET, které nabízí následující výhody pro webové vývojáře:

* C# Místo JavaScriptu napište kód.
* Využijte stávající ekosystém .NET knihoven .NET.
* Sdílejte logiku aplikace napříč serverem a klientem.
* Využijte výhod. Výkon, spolehlivost a zabezpečení sítě.
* Zajistěte produktivitu pomocí sady Visual Studio na počítačích PC, Linux a macOS.
* Sestavte se na společné sadě jazyků, platforem a nástrojů, které jsou stabilní, funkce s bohatou funkcí a snadno použitelné.

## <a name="creating-a-new-blazor-project"></a>Vytvoření nového projektu Blazor

1. V **okně Start**vyberte **Nový** a vytvořte nový projekt:

   ![Visual Studio pro Mac okno Start s zvýrazněným novým výběrem](media/blazor-new-project.png)
1. V dialogovém okně **Nový projekt** vyberte **.NET Core** > **App** > **Blazor Server** a vyberte **Další**: ![zvolte šablonu pro dialog nový projekt se zvolenou šablonou aplikace Blazor Server](media/blazor-project-template.png)

1. Jako cílovou architekturu vyberte .NET Core 3,1 a pak vyberte **Další**. 
   ![dialogové okno Konfigurovat novou aplikaci Blazor serveru zobrazené s cílovým rozhraním, které je vybrané na .NET Core 3,1](media/blazor-select-target-framework.png)

1. Vyberte název projektu a v případě potřeby přidejte podporu Gitu. Vyberte **Vytvořit** a vytvořte projekt.
   ![BConfigure dialogové okno nové aplikace Blazor, které se zobrazí při zadávání názvu projektu](media/blazor-name-project.png)

   Visual Studio pro Mac otevře projekt v okně rozložení kódu.
1. Pokud chcete aplikaci spustit, vyberte **spustit** > **Spustit bez ladění** .

   Visual Studio spustí [Kestrel](/aspnet/core/fundamentals/servers/kestrel), otevře prohlížeč pro `https://localhost:5001`a zobrazí vaši webovou aplikaci v Blazor.

   ![Webová aplikace v Blazor v Safari](media/blazor-new-app-in-edge.png)

## <a name="blazor-support-in-visual-studio-for-mac"></a>Podpora Blazor v Visual Studio pro Mac

Visual Studio pro Mac (počínaje verzí 8,4) obsahuje nové funkce, které vám pomůžou vytvořit nové projekty serveru Blazor. Také vám poskytuje standardní podporu, kterou byste očekávali, jako je vytváření, spouštění a ladění projektů Blazor. 

V předchozím návodu jsme viděli, jak šablona projektu aplikace Blazor serveru vám pomůže vytvořit nový projekt aplikace Blazor Server. Pojďme se podívat na některé z dalších funkcí v Visual Studio pro Mac k podpoře vývoje projektu serveru Blazor.

### <a name="editor-support-for-razor-files"></a>Podpora editoru pro soubory *. Razor*
Visual Studio pro Mac zahrnuje podporu pro úpravy souborů. Razor – většina souborů, které budete používat při vytváření aplikací Blazor. Verze rozhraní IDE pro Windows a Mac sdílí stejný editor pro soubory. Razor. Zobrazí se úplná zabarvení a podpora doplňování pro vaše soubory. Razor, včetně dokončování pro komponenty Razor deklarované v projektu.

![Okno editoru Visual Studio pro Mac zobrazující IntelliSense pro Blazor](media/blazor-intellisense.png)

### <a name="publishing-blazor-applications-to-azure-app-service"></a>Publikování Blazorch aplikací pro Azure App Service
Aplikace Blazor můžete publikovat také přímo na Azure App Service. Pokud nemáte účet Azure ke spuštění aplikace Blazor v Azure, můžete se kdykoli [zaregistrovat zdarma](https://azure.microsoft.com/free) , a to i na 12 měsíců bezplatných oblíbených služeb, $200 bezplatných kreditů Azure a více než 25 bezplatných služeb.

![Visual Studio pro Mac zobrazení prostředí Azure Publishing](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>Anatomie projektu

Webové aplikace Blazor ve výchozím nastavení zahrnují několik adresářů a souborů. Jak začínáte, tady jsou hlavní ty, které budete muset znát:

### <a name="pages-folder"></a>Složka stránky

Tato složka obsahuje webové stránky projektu, které používají příponu souboru *. Razor* .

### <a name="shared-folder"></a>Sdílená složka

Tato složka obsahuje sdílené součásti, a to i s příponou *. Razor* . Uvidíte, že to zahrnuje *MainLayout. Razor*, který se používá k definování společného rozložení napříč aplikací. Zahrnuje také sdílenou komponentu *NavMenu. Razor* , která se používá na všech stránkách. Pokud vytváříte opakovaně použitelné komponenty, přejdou do **sdílené** složky.

### <a name="app-settings"></a>Nastavení aplikace

Soubor *appSettings. JSON* obsahuje konfigurační data, jako jsou připojovací řetězce.

Další informace o konfiguraci najdete v tématu [konfigurace v průvodci ASP.NET](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Složka wwwroot

Tato složka obsahuje statické soubory, jako jsou soubory HTML, JavaScript a CSS. Další informace najdete v tématu [statické soubory v ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Tento soubor obsahuje vstupní bod pro program. Další informace najdete v tématu [ASP.NET Core webového hostitele](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Tento soubor obsahuje kód, který nakonfiguruje chování aplikace, například to, jestli aplikace vyžaduje souhlas s soubory cookie. Další informace najdete v tématu [spuštění aplikace v ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="summary"></a>Přehled
V tomto kurzu jste zjistili, jak vytvořit novou aplikaci Blazor serveru v Visual Studio pro Mac a zjistili jste některé z funkcí, které Visual Studio pro Mac nabídky, které vám pomůžou vytvářet Blazor aplikace.

## <a name="see-also"></a>Viz také:

Komplexnější průvodce vytvářením webových aplikací v Blazor najdete v tématu [Úvod do ASP.NET Core Blazor](/aspnet/core/blazor/index).
