---
title: Vytváření Blazor webových aplikací
description: Poskytuje informace o Blazor podpoře v aplikacích ASP.NET Core v Visual Studio pro Mac.
author: jongalloway
ms.author: jogallow
ms.date: 12/17/2019
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
no-loc:
- Blazor
- Blazor WebAssembly
ms.topic: how-to
ms.openlocfilehash: 86a8c35d2a379d6afbbe6cf55f53346223e7c462
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86211593"
---
# <a name="create-no-locblazor-web-apps"></a>Vytváření Blazor webových aplikací

Tato příručka nabízí Úvod k vytvoření první Blazor webové aplikace. Podrobné pokyny najdete v tématu [Úvod do ASP.NET Core Blazor ](/aspnet/core/blazor/index).

ASP.NET Core Blazor podporuje dvě různé možnosti hostování; Blazor Server a Blazor WebAssembly . Visual Studio pro Mac podporuje oba modely hostování. Visual Studio pro Mac 8.4 + podporuje Blazor Server a Visual Studio pro Mac 8.6 a podporuje obě. Další informace o Blazor hostitelských modelech naleznete v tématu [ASP.NET Core Blazor modelech hostování ](https://docs.microsoft.com/aspnet/core/blazor/hosting-models?view=aspnetcore-3.1). Podpora pro Blazor WebAssembly projekty ladění v Visual Studio pro Mac bude pocházet v vydání po 8,6.

Co je to Blazor ? Blazor je rozhraní pro vytváření interaktivního webového uživatelského rozhraní na straně klienta s .NET, které nabízí následující výhody pro webové vývojáře:

* Psát kód v jazyce C# namísto JavaScriptu.
* Využijte stávající ekosystém .NET knihoven .NET.
* Sdílejte logiku aplikace napříč serverem a klientem.
* Využijte výhod. Výkon, spolehlivost a zabezpečení sítě.
* Zajistěte produktivitu pomocí sady Visual Studio na počítačích PC, Linux a macOS.
* Sestavte se na společné sadě jazyků, platforem a nástrojů, které jsou stabilní, funkce s bohatou funkcí a snadno použitelné.

## <a name="creating-a-new-no-locblazor-server-project"></a>Vytvoření nového Blazor projektu serveru

1. V **okně Start**vyberte **Nový** a vytvořte nový projekt:

   ![Visual Studio pro Mac okno Start s zvýrazněným novým výběrem](media/blazor-new-project.png)
1. V dialogovém okně **Nový projekt** vyberte aplikace **.NET Core** > **App** > ** Blazor Server App** a vyberte **Další**: ![ Zvolte šablonu pro dialog Nový projekt::: No-Loc (Blazor)::: Server App Template Selected.](media/blazor-project-template.png)

1. Jako cílovou architekturu vyberte .NET Core 3,1 a pak vyberte **Další**. 
   ![Nakonfigurujte nové dialogová okna aplikace::: No-Loc (Blazor)::: Serverová aplikace zobrazená s cílovým rozhraním, které je vybrané pro .NET Core 3,1.](media/blazor-select-target-framework.png)

1. Vyberte název projektu a v případě potřeby přidejte podporu Gitu. Vyberte **Vytvořit** a vytvořte projekt.
   ![BConfigure vaše nové dialogové okno aplikace::: No-Loc (Blazor)::: Server App se zobrazuje při zadávání názvu projektu.](media/blazor-name-project.png)

   Visual Studio pro Mac otevře projekt v okně rozložení kódu.
1. Pro spuštění aplikace vyberte **Spustit**spustit  >  **bez ladění** .

   Visual Studio spustí [Kestrel](/aspnet/core/fundamentals/servers/kestrel), otevře prohlížeč `https://localhost:5001` a zobrazí vaši Blazor webovou aplikaci.

   ![::: No-Loc (Blazor)::: webová aplikace v Safari](media/blazor-new-app-in-edge.png)

## <a name="no-locblazor-support-in-visual-studio-for-mac"></a>Blazor Podpora v Visual Studio pro Mac

Visual Studio pro Mac (počínaje verzí 8,4) obsahuje nové funkce, které vám pomůžou vytvořit nové Blazor serverové projekty. Také vám poskytuje standardní podporu, kterou byste očekávali, jako je vytváření, spouštění a ladění Blazor projektů. V Visual Studio pro Mac 8,6 Podpora pro vytváření, sestavování a spouštění Blazor WebAssembly projektů bylo přidáno.

V předchozím návodu jsme viděli, jak Blazor Šablona projektu serverových aplikací vám pomůže vytvořit nový Blazor projekt serverových aplikací. Pojďme se podívat na některé z dalších funkcí v Visual Studio pro Mac k podpoře Blazor vývoje projektů.

### <a name="editor-support-for-razor-files"></a>Podpora editoru pro soubory *. Razor*
Visual Studio pro Mac zahrnuje podporu pro úpravy souborů. Razor – většina souborů, které budete používat při vytváření Blazor aplikací. Verze rozhraní IDE pro Windows a Mac sdílí stejný editor pro soubory. Razor. Zobrazí se úplná zabarvení a podpora doplňování pro vaše soubory. Razor, včetně dokončování pro komponenty Razor deklarované v projektu.

![Okno editoru Visual Studio pro Mac znázorňující IntelliSense pro::: No-Loc (Blazor):::](media/blazor-intellisense.png)

### <a name="publishing-no-locblazor-applications-to-azure-app-service"></a>Publikování Blazor aplikací pro Azure App Service
Můžete také publikovat Blazor aplikace přímo na Azure App Service. Pokud nemáte účet Azure ke spuštění vaší Blazor aplikace v Azure, můžete se kdykoli [zaregistrovat zdarma](https://azure.microsoft.com/free) , ale získáte 12 měsíců bezplatných oblíbených služeb, $200 bezplatné kredity Azure a více než 25 bezplatných služeb.

![Visual Studio pro Mac zobrazení prostředí Azure Publishing](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>Anatomie projektu

Blazor ve výchozím nastavení obsahují webové aplikace několik adresářů a souborů. Jak začínáte, tady jsou hlavní ty, které budete muset znát:

### <a name="pages-folder"></a>Složka stránky

Tato složka obsahuje webové stránky projektu, které používají příponu souboru *. Razor* .

### <a name="shared-folder"></a>Sdílená složka

Tato složka obsahuje sdílené součásti, a to i s příponou *. Razor* . Uvidíte, že to zahrnuje *MainLayout. Razor*, který se používá k definování společného rozložení napříč aplikací. Zahrnuje také sdílenou komponentu *NavMenu. Razor* , která se používá na všech stránkách. Pokud vytváříte opakovaně použitelné komponenty, přejdou do **sdílené** složky.

### <a name="app-settings"></a>Nastavení aplikace

*appSettings.jsv* souboru obsahuje konfigurační data, jako jsou připojovací řetězce.

Další informace o konfiguraci najdete v tématu [konfigurace v průvodci ASP.NET](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Složka wwwroot

Tato složka obsahuje statické soubory, jako jsou soubory HTML, JavaScript a CSS. Další informace najdete v tématu [statické soubory v ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Tento soubor obsahuje vstupní bod pro program. Další informace najdete v tématu [ASP.NET Core webového hostitele](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Tento soubor obsahuje kód, který nakonfiguruje chování aplikace, například to, jestli aplikace vyžaduje souhlas s soubory cookie. Další informace najdete v tématu [spuštění aplikace v ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="summary"></a>Shrnutí
V tomto kurzu jste zjistili, jak vytvořit novou Blazor serverovou aplikaci v Visual Studio pro Mac a zjistili jste o některých funkcích, které Visual Studio pro Mac nabídky, které vám pomůžou s vytvářením Blazor aplikací.

## <a name="see-also"></a>Viz také

Komplexnější průvodce vytvářením Blazor webových aplikací najdete v tématu [úvod do ASP.NET Core Blazor ](/aspnet/core/blazor/index).
