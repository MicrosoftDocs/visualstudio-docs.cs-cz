---
title: Začínáme s ASP.NET Core
description: Tento článek popisuje, jak začít pracovat s technologií ASP.NET v sadě Visual Studio pro Mac, včetně instalace a vytvoření nového projektu.
author: conceptdev
ms.author: crdun
ms.date: 07/13/2017
ms.assetid: 6E8B0C90-33D6-4546-8207-CE0787584565
ms.openlocfilehash: 9576048cb6a62f7a4e8c93456154997af359a711
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296473"
---
# <a name="getting-started-with-aspnet-core"></a>Začínáme s ASP.NET Core

 Visual Studio pro Mac usnadňuje vývoj vaší aplikace služby s jeho podporu pro nejnovější platformy vývoj webové aplikace ASP.NET Core. ASP.NET Core běží na .NET Core, nejnovější vývoj rozhraní .NET Framework a modulu runtime. Má se vše vyladěno pro rychlý výkon, dostaneme pro malé instalace velikosti a znovu si představit ke spuštění na systému Linux a macOS i Windows.

## <a name="installing-net-core"></a>Instalace .NET Core

.NET core 1.1 se automaticky nainstaluje při instalaci sady Visual Studio pro Mac.

## <a name="creating-an-aspnet-core-app-in-visual-studio-for-mac"></a>Vytvoření aplikace ASP.NET Core v sadě Visual Studio pro Mac

Otevřít Visual Studio pro Mac. Na úvodní stránce vyberte **nový projekt...**

![Dialogové okno nového projektu](media/asp-net-core-image1.png)

Zobrazí se dialogové okno Nový projekt, což vám umožní vybrat šablonu pro vytvoření vaší aplikace.

Existuje mnoho projektů, které vám poskytne předem připravené šablony, abyste mohli začít vytvářet vaše aplikace ASP.NET Core. Toto jsou:

- **.NET core > prázdná webová aplikace ASP.NET Core**
- **.NET core > webové aplikace ASP.NET Core**
- **.NET core > webového rozhraní API ASP.NET Core**
- **Multiplatformní > aplikace > připojené aplikace**

![Možnosti projektu ASP.NET](media/asp-net-core-image11.png)

Vyberte **prázdná webová aplikace ASP.NET Core** a stiskněte klávesu **Další**. Dejte projektu název a stiskněte klávesu **vytvořit**. Tím se vytvoří nové aplikace ASP.NET Core, který by měl vypadat podobně jako na následujícím obrázku:

![Nové zobrazení prázdný projekt ASP.NET Core](media/asp-net-core-image4.png)

ASP.NET Core prázdná webová aplikace vytvoří webovou aplikaci se dvěma soubory výchozí: **Program.cs** a **Startup.cs**, což je vysvětleno níže. Také vytvoří složku, závislosti, která obsahuje závislosti balíčku NuGet projektu, jako je ASP.NET Core, .NET Core framework a cíle nástroje MSBuild, které se projekt sestavil:

![Zobrazení závislostí oblasti řešení](media/asp-net-core-image12.png)

### <a name="programcs"></a>Program.cs

Otevřít a zkontrolovat **Program.cs** souboru ve vašem projektu. Všimněte si, že se dějí dvě věci v `Main` metoda – záznam do vaší aplikace:

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
Aplikace ASP.NET Core vytvoří webový server v jeho hlavní metoda konfigurací a spuštění hostitele prostřednictvím instance [ `WebHostBuilder` ](/aspnet/core/fundamentals/hosting). Tato Tvůrce poskytuje metody, které umožňují hostitele nakonfigurovat. V aplikaci šablony jsou použité následující konfigurace:

* `UseKestrel`: Určuje, že Kestrel server budou používat aplikaci
* `UseContentRoot(Directory.GetCurrentDirectory())`: Používá kořenové složce webového projektu jako uživatel root obsahu aplikace při spuštění aplikace z této složky
* `.UseIISIntegration()`: Určuje, že aplikace by měla fungovat se službou IIS. Použití služby IIS s ASP.NET Core `UseKestrel` a `UseIISIntegration` musí být zadána.
* `.UseStartup<Startup>()`: Určuje třídu pro spuštění.

  Metody sestavení a spuštění sestavení IWebHost, který bude hostitelem aplikace a spusťte ji naslouchá příchozím požadavkům HTTP.

### <a name="startupcs"></a>Startup.cs

Třída po spuštění pro vaše aplikace je určena `UseStartup()` metodu `WebHostBuilder`. Je v této třídě, kterou specifikujete požadavku zpracování kanálu, a kde konfigurovat všechny služby.

Otevřít a zkontrolovat **Startup.cs** soubor v projektu:

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

Tato třída při spuštění musí vždycky dodržovat následující pravidla:

 - Vždy musí být veřejné
 - Musí obsahovat dvě veřejné metody: `ConfigureServices` a `Configure`

`ConfigureServices` Metoda definuje služby, které budou používat vaši aplikaci.

`Configure` Lze sestavit pomocí kanálu požadavku [Middleware](/aspnet/core/fundamentals/middleware). Toto jsou komponenty použité v rámci kanálu určité aplikace technologie ASP.NET pro zpracování požadavků a odpovědí. HTTP kanál se skládá z počtu požadavek delegátů, volá se v sekvenci. Všem delegátům možné zpracovat žádost o samotné nebo předat do další delegáta.

Delegáty lze nakonfigurovat pomocí `Run`,`Map`, a `Use` metody `IApplicationBuilder`, ale `Run` metoda se nikdy neměl volat další delegáta a musí použít značka na konci vašeho kanálu.

`Configure` Metoda předem připravené šablony je vytvořená tak udělat několik věcí. Nejprve nastaví výjimku zpracování stránky pro použití během vývoje. Pak odešle odpověď na žádost o webovou stránku s jednoduchou "Hello World".

Tento jednoduchý text Hello, World projektu můžete nyní spustit bez jakékoli další přidávaný kód. Spusťte aplikaci a zobrazit v prohlížeči, kliknutím na tlačítko Přehrát (triangulace) na panelu nástrojů:

![Spuštění aplikace](media/asp-net-core-image5.png)

Visual Studio pro Mac používá náhodný port spustit webový projekt. Chcete-li zjistit, co je to port je, otevřete výstup aplikace, která je uvedená v části **zobrazení > panely**. Výstup by měl najít podobný tomu vidíte níže:

![Výstup aplikace zobrazení port pro naslouchání](media/asp-net-core-image6.png)

Otevřete prohlížeč zvolíte a zadejte `http://localhost:5000/`a nahraďte `5000` s portem, který výstupu sady Visual Studio ve výstupu aplikace. Měli byste vidět text `Hello World!`:

![prohlížeč zobrazující text](media/asp-net-core-image7.png)

## <a name="adding-a-controller"></a>Přidání kontroleru

Aplikace ASP.NET Core pomocí vzoru návrhu Model-View-Controller (MVC) k poskytování logické rozdělení povinností mezi jednotlivé části aplikace. MVC se skládá z následujících akcí:

- **Model**: třída, která představuje data aplikace.
- **Zobrazení**: zobrazí aplikace uživatelské rozhraní (což se často stává datový model).
- **Kontroler**: třída, která zpracovává požadavky na prohlížeč, odpoví na vstup uživatele a interakce.

Další informace o používání MVC najdete [přehled ASP.NET Core MVC](/aspnet/core/mvc/overview) průvodce.

Chcete-li přidat kontroler, postupujte takto:

1. Klikněte pravým tlačítkem na název projektu a vyberte **Přidat > Nová soubory**. Vyberte **Obecné > prázdná třída**a zadejte název kontroleru:

    ![Dialogové okno Nový soubor](media/asp-net-core-image8.png)

2. Přidejte následující kód do nového řadiče:

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

3. Přidat `Microsoft.AspNetCore.Mvc` závislostí do projektu kliknutím pravým tlačítkem myši **závislost** složky a výběru **přidat balíček...** .

4. Pomocí vyhledávacího pole procházet NuGet knihovny pro `Microsoft.AspNetCore.Mvc`a vyberte **přidat balíček**. To může trvat několik minut, než instalace a můžete být vyzváni tak, aby přijímal různých licencí pro požadované závislosti:

    ![Přidat Nuget](media/asp-net-core-image9.png)

5. Ve třídě spuštění odebrat `app.Run` lambda a logiku směrování URL MVC používá k určení, která kódu by měla vyvolat pro následující nastavení:

    ```csharp
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=HelloWorld}/{action=Index}/{id?}");
    });
    ```

    Ujistěte se, že chcete odebrat `app.Run` lambda, protože se přepíše logiku směrování.

    Chcete-li určit, jaký kód ke spuštění aplikace MVC používá následující formát:

    `/[Controller]/[ActionName]/[Parameters]`

    Když přidáte výše uvedeném fragmentu kódu, oznamujete tím aplikaci výchozí nastavení `HelloWorld` Kontroleru a `Index` metody akce.

6. Přidat `services.AddMvc();` volání `ConfigureServices` způsob, jak je znázorněno níže:

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
    }
    ```

    Můžete také předat parametr informace z adresy URL ke kontroleru.

7. Přidejte jinou metodu HelloWorldController, jak je znázorněno níže:

    ```csharp
    public string Xamarin(string name)
    {
        return HtmlEncoder.Default.Encode($"Hello {name}, welcome to Visual Studio for Mac");
    }
    ```

8. Pokud nyní spustíte aplikaci, by měl automaticky otevře prohlížeč:

    ![Běžící aplikaci v prohlížeči](media/asp-net-core-image13.png)

9. Zkuste přejít ke `http://localhost:xxxx/HelloWorld/Xamarin?name=Amy` (nahrazení `xxxx` s správný port), měli byste vidět následující:

    ![Běžící aplikaci v prohlížeči s argumenty](media/asp-net-core-image10.png)


## <a name="troubleshooting"></a>Poradce při potížích

Pokud je potřeba nainstalovat sadu .NET Core ručně v Mac OS 10.11 (El Capitan) a vyšší, postupujte takto:

1. Před zahájením instalace .NET Core, ujistěte se, že jste aktualizovali všechny aktualizace operačního systému na nejnovější stabilní verzi. Můžete to zkontrolovat, že přejdete do aplikace pro App Store a vyberete kartu aktualizace.

2. Postupujte podle kroků uvedených v [webu .NET Core](https://www.microsoft.com/net/core#macos).

Ujistěte se, že všechny čtyři kroky úspěšně zajistit úspěšné instalaci .NET Core.

## <a name="summary"></a>Souhrn

Tato příručka poskytl úvod do ASP.NET Core. Popisuje, je, kdy se má použít a poskytuje informace o používání v aplikaci Visual Studio pro Mac.
Další informace o dalších krocích odsud najdete v následujících příručkách:
- [ASP.NET Core](/aspnet/core/?view=aspnetcore-2.1#build-web-ui-and-web-apis-using-aspnet-core-mvc) dokumentace.
- [Vytváření back-endových služeb pro nativní mobilní aplikace](/aspnet/core/mobile/native-mobile-backend), který ukazuje, jak sestavit služby REST pro aplikace na platformě Xamarin.Forms pomocí ASP.NET Core.
- [ASP.NET Core praktických cvičení](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started).
