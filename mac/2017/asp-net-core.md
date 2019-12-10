---
title: Začínáme s ASP.NET Core
description: Tento článek popisuje, jak začít s ASP.NET v Visual Studio pro Mac, včetně instalace a vytvoření nového projektu.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/13/2017
ms.assetid: 6E8B0C90-33D6-4546-8207-CE0787584565
ms.custom: video
ms.openlocfilehash: b1e29e4df6ea31d99a99590f3e56ed6feac791e1
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74984892"
---
# <a name="getting-started-with-aspnet-core"></a>Začínáme s ASP.NET Core

 Visual Studio pro Mac usnadňuje vývoj služby vaší aplikace pomocí podpory nejnovější ASP.NET Core webové vývojové platformy. ASP.NET Core běží na .NET Core, což je nejnovější vývoj .NET Framework a modulu runtime. Je vyladěná z hlediska rychlého výkonu, faktoringu pro menší velikosti instalace a opětovné představy pro spuštění v systémech Linux a macOS a také ve Windows.

## <a name="installing-net-core"></a>Instalace .NET Core

Rozhraní .NET Core 1,1 se automaticky nainstaluje při instalaci Visual Studio pro Mac.

## <a name="creating-an-aspnet-core-app-in-visual-studio-for-mac"></a>Vytvoření aplikace ASP.NET Core v Visual Studio pro Mac

Otevřete Visual Studio pro Mac. Na úvodní stránce vyberte **Nový projekt...**

![Dialogové okno Nový projekt](media/asp-net-core-image1.png)

Tím se zobrazí dialogové okno Nový projekt, ve kterém můžete vybrat šablonu pro vytvoření aplikace.

K dispozici je řada projektů, které vám poskytnou předem vytvořenou šablonu pro zahájení sestavování aplikace ASP.NET Core. Toto jsou:

- **Rozhraní .NET Core > ASP.NET Core prázdné webové aplikace**
- **Webová aplikace .NET Core > ASP.NET Core**
- **Rozhraní .NET Core > ASP.NET Core webového rozhraní API**
- **Aplikace > pro více platforem > propojená aplikace**

![Možnosti projektu ASP.NET](media/asp-net-core-image11.png)

Vyberte **ASP.NET Core prázdné webové aplikace** a klikněte na tlačítko **Další**. Zadejte název projektu a stiskněte **vytvořit**. Tím se vytvoří nová aplikace ASP.NET Core, která by měla vypadat podobně jako na následujícím obrázku:

![Nové ASP.NET Core prázdné zobrazení projektu](media/asp-net-core-image4.png)

Prázdná webová aplikace ASP.NET Core vytvoří webovou aplikaci se dvěma výchozími soubory: **program.cs** a **Startup.cs**, které jsou vysvětleny níže. Vytvoří také složku závislosti, která obsahuje závislosti balíčku NuGet vašeho projektu, například ASP.NET Core, rozhraní .NET Core Framework a cíle MSBuild, které sestavují projekt:

![Oblast řešení zobrazení závislostí](media/asp-net-core-image12.png)

### <a name="programcs"></a>Program.cs

Otevřete soubor **program.cs** a prozkoumejte ho v projektu. Všimněte si, že v metodě `Main` se děje dvě věci – vstup do vaší aplikace:

```csharp
public static void Main(string[] args)
{
    var host = new WebHostBuilder()
        .UseKestrel()
        .UseContentRoot(Directory.GetCurrentDirectory())
        .UseIISIntegration()
        .UseStartup<Startup>()
        .Build();

    host.Run();
}
```

ASP.NET Core aplikace vytvoří webový server v jeho hlavní metodě konfigurací a spuštěním hostitele prostřednictvím instance [`WebHostBuilder`](/aspnet/core/fundamentals/hosting). Tento tvůrce poskytuje metody, které umožňují konfigurovat hostitele. V aplikaci šablon se používají následující konfigurace:

* `UseKestrel`: Určuje, že aplikace bude používat server Kestrel.
* `UseContentRoot(Directory.GetCurrentDirectory())`: používá kořenovou složku webového projektu jako kořen obsahu aplikace při spuštění aplikace z této složky.
* `.UseIISIntegration()`: Určuje, zda má aplikace spolupracovat se službou IIS. Chcete-li použít službu IIS s ASP.NET Core `UseKestrel` a `UseIISIntegration` je nutné zadat.
* `.UseStartup<Startup>()`: Určuje třídu po spuštění.

  Metody sestavení a spuštění sestavují IWebHost, která bude hostovat aplikaci a spustí naslouchání pro příchozí požadavky HTTP.

### <a name="startupcs"></a>Startup.cs

Spouštěcí třída vaší aplikace je určena v metodě `UseStartup()` `WebHostBuilder`. Je v této třídě, kterou určíte kanál pro zpracování požadavků a kde nakonfigurujete nějaké služby.

Otevřete a zkontrolujte soubor **Startup.cs** v projektu:

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
    }

    public void Configure(IApplicationBuilder app, IHostingEnvironment env, ILoggerFactory loggerFactory)
    {
        loggerFactory.AddConsole();

        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }

        app.Run(async (context) =>
        {
            await context.Response.WriteAsync("Hello World!");
        });
    }
}
```

Tato spouštěcí třída musí vždy splňovat následující pravidla:

- Musí být vždycky veřejné.
- Musí obsahovat dvě veřejné metody: `ConfigureServices` a `Configure`

Metoda `ConfigureServices` definuje služby, které bude aplikace používat.

`Configure` umožňuje vytvořit kanál požadavků pomocí [middlewaru](/aspnet/core/fundamentals/middleware). Jedná se o komponenty, které se používají v kanálu aplikace ASP.NET ke zpracování požadavků a odpovědí. Kanál HTTP se skládá z několika delegátů požadavků, které se nazývají v sekvenci. Každý delegát může zvolit buď zpracování samotného požadavku, nebo ho předat dalšímu delegátovi.

Delegáty lze konfigurovat pomocí metod `Run`,`Map`a `Use` na `IApplicationBuilder`, ale metoda `Run` nikdy nebude volat dalšího delegáta a měla by být vždy použita na konci vašeho kanálu.

Metoda `Configure` předem sestavené šablony je sestavena tak, aby procházela několik věcí. Nejprve nakonfiguruje stránku zpracování výjimek pro použití během vývoje. Pak pošle odpověď na žádající webovou stránku pomocí jednoduchého "Hello Worldho".

Tento jednoduchý Hello, World Project může běžet hned bez dalšího přidávaného kódu. Pokud chcete aplikaci spustit a zobrazit ji v prohlížeči, stiskněte tlačítko Přehrát (trojúhelník) na panelu nástrojů:

![Spustit aplikaci](media/asp-net-core-image5.png)

Visual Studio pro Mac používá náhodný port pro spuštění webového projektu. Chcete-li zjistit, jaký port je to, otevřete výstup aplikace, který je uveden v části **zobrazit > panely**. Výsledek by měl vypadat podobně jako v následujícím příkladu:

![Výstup aplikace zobrazující port naslouchání](media/asp-net-core-image6.png)

Otevřete prohlížeč podle vlastního výběru a zadejte `http://localhost:5000/`a nahraďte `5000` portem, který Visual Studio Output ve výstupu aplikace. Měl by se zobrazit `Hello World!`textu:

![prohlížeč zobrazující text](media/asp-net-core-image7.png)

## <a name="adding-a-controller"></a>Přidání kontroleru

ASP.NET Core aplikace používají vzor návrhu MVC (Model-View-Controller) k poskytnutí logického oddělení zodpovědností pro každou část aplikace. MVC se skládá z následujících:

- **Model**: třída, která představuje data aplikace.
- **Zobrazit**: zobrazí uživatelské rozhraní aplikace (což jsou často data modelu).
- **Kontroler**: třída, která zpracovává požadavky prohlížeče, reaguje na vstupy a interakce uživatele.

Další informace o použití MVC najdete v tématu [přehled ASP.NET Core příručka MVC](/aspnet/core/mvc/overview) .

Chcete-li přidat kontroler, postupujte následovně:

1. Klikněte pravým tlačítkem myši na název projektu a vyberte **přidat > nové soubory**. Vyberte **obecné > prázdnou třídu**a zadejte název kontroleru:

    ![Dialogové okno Nový soubor](media/asp-net-core-image8.png)

2. Do nového kontroleru přidejte následující kód:

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using System.Text.Encodings.Web;

    namespace Hello_ASP
    {
        public class HelloWorldController : Controller
        {
            //
            // GET: /HelloWorld/

            public string Index()
            {
                return "This is my default action...";
            }

        }
    }
    ```

3. Přidejte do projektu závislost `Microsoft.AspNetCore.Mvc` tak, že kliknete pravým tlačítkem na složku **závislosti** a vyberete **Přidat balíček...** .

4. Pomocí vyhledávacího pole vyhledejte knihovnu NuGet pro `Microsoft.AspNetCore.Mvc`a vyberte **Přidat balíček**. Instalace může trvat několik minut a může se vám zobrazit výzva, abyste přijali různé licence na požadované závislosti:

    ![Přidat NuGet](media/asp-net-core-image9.png)

5. Ve spouštěcí třídě odeberte `app.Run` lambda a nastavte logiku směrování adres URL, kterou používá MVC, abyste zjistili, který kód by měl vyvolat následující:

    ```csharp
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=HelloWorld}/{action=Index}/{id?}");
    });
    ```

    Nezapomeňte odebrat `app.Run` lambda, protože tato akce přepíše logiku směrování.

    MVC používá následující formát pro určení kódu, který se má spustit:

    `/[Controller]/[ActionName]/[Parameters]`

    Když přidáte fragment kódu výše, oznamujete aplikaci výchozímu kontroleru `HelloWorld` a metodě `Index` akci.

6. Přidejte `services.AddMvc();` volání do metody `ConfigureServices`, jak je znázorněno níže:

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
    }
    ```

    Můžete také předat informace o parametrech z adresy URL do kontroleru.

7. Přidejte další metodu do HelloWorldController, jak je znázorněno níže:

    ```csharp
    public string Xamarin(string name)
    {
        return HtmlEncoder.Default.Encode($"Hello {name}, welcome to Visual Studio for Mac");
    }
    ```

8. Pokud teď aplikaci spustíte, měla by se automaticky otevřít v prohlížeči:

    ![Běžící aplikace v prohlížeči](media/asp-net-core-image13.png)

9. Zkuste přejít na `http://localhost:xxxx/HelloWorld/Xamarin?name=Amy` (nahrazení `xxxx` správným portem), měli byste vidět následující:

    ![Spuštění aplikace v prohlížeči s argumenty](media/asp-net-core-image10.png)

## <a name="troubleshooting"></a>Odstraňování problémů

Pokud potřebujete .NET Core nainstalovat ručně na Mac OS 10,11 (El Capitan) a vyšší, udělejte toto:

1. Než začnete s instalací .NET Core, ujistěte se, že jste aktualizovali všechny aktualizace operačního systému na nejnovější stabilní verzi. Můžete to vrátit tak, že v aplikaci App Storu kliknete na kartu aktualizace a vyberete kartu aktualizace.

2. Postupujte podle kroků uvedených na [webu .NET Core](https://www.microsoft.com/net/core#macos).

Ujistěte se, že jste úspěšně dokončili všechny čtyři kroky, abyste se ujistili, že je instalace .NET Core úspěšná.

## <a name="summary"></a>Přehled

Tento průvodce vám poskytl Úvod do ASP.NET Core. Popisuje, co je, kdy se používá, a poskytuje informace o jeho použití v Visual Studio pro Mac.
Další informace o dalších krocích odsud najdete v následujících příručkách:
- [ASP.NET Core](/aspnet/core/#build-web-apis-and-web-ui-using-aspnet-core-mvc) docs.
- [Vytváření back-end služeb pro nativní mobilní aplikace](/aspnet/core/mobile/native-mobile-backend), které ukazují, jak vytvořit službu REST pomocí ASP.NET Core pro aplikaci Xamarin. Forms.
- [ASP.NET Core praktické laboratorní prostředí](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started).

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Build-Your-First-App/player]