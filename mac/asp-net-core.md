---
title: Začínáme s ASP.NET Core
description: Tento článek popisuje, jak začít s ASP.NET v Sadě Visual Studio pro Mac, včetně instalace a vytvoření nového projektu.
author: sayedihashimi
ms.author: sayedha
ms.date: 04/02/2019
ms.assetid: 6E8B0C90-33D6-4546-8207-CE0787584565
ms.custom: video
ms.openlocfilehash: d0e00929de11ff3fd820670be2bb6361cfb5fa6c
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75405006"
---
# <a name="getting-started-with-aspnet-core"></a>Začínáme s ASP.NET Core

 Visual Studio pro Mac usnadňuje vývoj služeb vaší aplikace s podporou nejnovější platformy pro vývoj webu ASP.NET. ASP.NET Core běží na .NET Core, nejnovější vývoj rozhraní .NET Framework a runtime. Byl vyladěn pro rychlý výkon, zohledněn pro malé velikosti instalací a přepracován tak, aby běžel na Linuxu a macOS, stejně jako v systému Windows.

## <a name="installing-net-core"></a>Instalace jádra rozhraní .NET

Rozhraní .NET Core 2.1 se automaticky nainstaluje při instalaci sady Visual Studio for Mac.

## <a name="creating-an-aspnet-core-app-in-visual-studio-for-mac"></a>Vytvoření aplikace ASP.NET Core ve Visual Studiu pro Mac

Otevřete Visual Studio pro Mac. Na úvodní obrazovce vyberte **Nový projekt...**

![Dialogové okno Nový projekt](media/asp-net-core-2019-new-asp-core.png)

Zobrazí se dialogové okno Nový projekt, které vám umožní vybrat šablonu pro vytvoření aplikace.

Existuje celá řada projektů, které vám poskytnou předem vytvořenou šablonu, která vám začne vytvářet ASP.NET základní aplikaci. Jsou to:

- **> jádra .NET prázdné**
- **Rozhraní API > jádra .NET**
- **Základní > webová aplikace .NET**
- **Základní > webová aplikace .NET (Model-View-Controller)**

![možnosti projektu ASP.NET](media/asp-net-core-2019-new-asp-core.png)

Vyberte **ASP.NET jádro prázdné webové aplikace** a stiskněte tlačítko **Další**. Pojmenujte projekt a stiskněte **klávesu Create**. Tím se vytvoří nová aplikace ASP.NET Core. V levém podokně panelu řešení rozbalte druhou šipku a pak vyberte **Startup.cs**. Mělo by to vypadat podobně jako na obrázku níže:

![Nové ASP.NET zobrazení prázdného projektu](media/asp-net-core-2019-empty-project.png)

Šablona ASP.NET Core Empty vytvoří webovou aplikaci se dvěma výchozími soubory: **Program.cs** a **Startup.cs**, které jsou vysvětleny níže. Vytvoří také složku závislostí, která obsahuje závislosti balíčku NuGet vašeho projektu, jako je ASP.NET Core, rozhraní .NET Core a cíle MSBuild, které sestavují projekt:

![Panel řešení zobrazující závislosti](media/asp-net-core-2019-solution-dependencies.png)

### <a name="programcs"></a>Program.cs

Otevřete a zkontrolujte soubor **Program.cs** v projektu. Všimněte si, že `Main` se v metodě děje několik věcí – položka do aplikace:

```csharp
    public class Program
    {
        public static void Main(string[] args)
        {
            CreateWebHostBuilder(args).Build().Run();
        }

        public static IWebHostBuilder CreateWebHostBuilder(string[] args) =>
            WebHost.CreateDefaultBuilder(args)
                .UseStartup<Startup>();
    }
```

Aplikace ASP.NET Core vytvoří webový server ve své hlavní metodě konfigurací [`WebHostBuilder`](/aspnet/core/fundamentals/hosting)a spuštěním hostitele prostřednictvím instance aplikace . Tento tvůrce poskytuje metody, které umožňují konfiguraci hostitele. V šabloně aplikace se používají následující konfigurace:

* `.UseStartup<Startup>()`: Určuje třídu Po spuštění.

Můžete však také přidat další konfigurace, například:

* `UseKestrel`: Určuje, že server Kestrel bude aplikace používat.
* `UseContentRoot(Directory.GetCurrentDirectory())`: Používá kořenovou složku webového projektu jako kořenový obsah aplikace při spuštění aplikace z této složky.
* `.UseIISIntegration()`: Určuje, že aplikace by měla pracovat se selstou. Chcete-li používat iis `UseKestrel` `UseIISIntegration` s ASP.NET Core a je třeba zadat.

### <a name="startupcs"></a>Startup.cs

Třída Startup pro vaši aplikaci `UseStartup()` je `CreateWebHostBuilder`určena v metodě na . V této třídě zadáte kanál zpracování požadavků a kde nakonfigurujete všechny služby.

Otevřete a zkontrolujte soubor **Startup.cs** v projektu:

```csharp
    public class Startup
    {
        // This method gets called by the runtime. Use this method to add services to the container.
        // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
        public void ConfigureServices(IServiceCollection services)
        {
        }

        // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
        public void Configure(IApplicationBuilder app, IHostingEnvironment env)
        {
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

Tato třída Startup musí vždy dodržovat následující pravidla:

- Musí být vždy veřejné
- Musí obsahovat dvě veřejné `ConfigureServices` metody: a`Configure`

Metoda `ConfigureServices` definuje služby, které bude vaše aplikace používat.

Umožňuje `Configure` sestavit váš požadavek potrubí pomocí [Middleware](/aspnet/core/fundamentals/middleware). Jedná se o součásti používané v rámci kanálu aplikace ASP.NET pro zpracování požadavků a odpovědí. Kanál HTTP se skládá z několika delegátů požadavků, které jsou volány postupně. Každý delegát může buď zpracovat požadavek sám, nebo předat dalšímu delegátovi.

Delegáty můžete nakonfigurovat `Run``Map`pomocí `Use` aplikace `IApplicationBuilder`, a `Run` metody na aplikaci , ale metoda nikdy nezavolá dalšího delegáta a měla by být vždy použita na konci kanálu.

Metoda `Configure` předem sestavené šablony je vytvořena tak, aby dělala několik věcí. Nejprve konfiguruje stránku zpracování výjimek pro použití během vývoje. Poté odešle odpověď na žádající webovou stránku s jednoduchým "Hello World".

Tento jednoduchý Hello, World projekt lze spustit nyní bez přidání dalšího kódu. Chcete-li aplikaci spustit, můžete buď vybrat prohlížeč, který chcete aplikaci spustit, pomocí rozbalovacího okna vpravo od tlačítka Přehrát, nebo jednoduše stisknete tlačítko Přehrát (trojúhelníkové) a použijete výchozí prohlížeč:

![Spuštění prohlížeče](media/asp-net-web-picker.png)

Visual Studio pro Mac používá náhodný port ke spuštění webového projektu. Chcete-li zjistit, o jaký port se jedná, otevřete výstup aplikace, který je uveden v části **Zobrazit > podložky**. Měli byste najít výstup podobný tomu, který je uveden níže:

![Výstup aplikace zobrazující naslouchací port](media/asp-net-core-image6.png)

Jakmile je projekt spuštěn, výchozí webový prohlížeč by se měl spustit a připojit se k adrese URL uvedené ve výstupu aplikace. Případně můžete otevřít libovolný prohlížeč podle vašeho `http://localhost:5000/`výběru a `5000` zadat a nahradit port, který visual studio výstup ve výstupu aplikace. Měli byste vidět `Hello World!`text :

![prohlížeč zobrazující text](media/asp-net-core-image7.png)

## <a name="adding-a-controller"></a>Přidání kontroleru

ASP.NET základní aplikace používají model-view-controller (MVC) návrh vzoru poskytnout logické oddělení odpovědnosti pro každou část aplikace. MVC se skládá z následujících:

- **Model**: Třída, která představuje data aplikace.
- **Zobrazení**: Zobrazí uživatelské rozhraní aplikace (což jsou často data modelu).
- **Řadič**: Třída, která zpracovává požadavky prohlížeče, reaguje na vstup uživatele a interakci.

Další informace o používání MVC naleznete v [přehledu ASP.NET Core MVC](/aspnet/core/mvc/overview) průvodce.

Chcete-li přidat ovladač, postupujte takto:

1. Klikněte pravým tlačítkem myši na název projektu a vyberte **přidat > nové soubory**. Vyberte **Obecné > Prázdná třída**a zadejte název řadiče:

    ![Dialogové okno Nový soubor](media/asp-net-core-image8.png)

2. Do nového řadiče přidejte následující kód:

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

3. Přidejte `Microsoft.AspNetCore.Mvc` závislost do projektu tak, že kliknete pravým tlačítkem myši na složku **Závislost** a vyberete **přidat balíček...**.

4. Pomocí pole Hledat procházejte knihovnu `Microsoft.AspNetCore.Mvc`NuGet a vyberte **Přidat balíček**. Instalace může trvat několik minut a může být vyzvána k přijetí různých licencí pro požadované závislosti:

    ![Přidat Nuget](media/asp-net-core-image9.png)

5. Ve třídě Startup odeberte `app.Run` lambdu a nastavte logiku směrování adres URL používanou mvc k určení kódu, který by měl vyvolat na následující:

    ```csharp
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=HelloWorld}/{action=Index}/{id?}");
    });
    ```

    Ujistěte se, `app.Run` že odebrat lambda, protože to bude přepsat logiku směrování.

    MVC používá následující formát k určení, který kód spustit:

    `/[Controller]/[ActionName]/[Parameters]`

    Když přidáte fragment kódu výše, říkáte aplikaci výchozí `HelloWorld` řadič a metodu `Index` akce.

6. Přidejte `services.AddMvc();` volání `ConfigureServices` k metodě, jak je znázorněno níže:

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
    }
    ```

    Informace o parametrech můžete také předat z adresy URL do řadiče.

7. Přidejte další metodu do HelloWorldController, jak je znázorněno níže:

    ```csharp
    public string Xamarin(string name)
    {
        return HtmlEncoder.Default.Encode($"Hello {name}, welcome to Visual Studio for Mac");
    }
    ```

8. Pokud aplikaci spustíte nyní, měla by automaticky otevřít prohlížeč:

    ![Spuštění aplikace v prohlížeči](media/asp-net-core-image13.png)

9. Zkuste přejít `http://localhost:xxxx/HelloWorld/Xamarin?name=Amy` na `xxxx` (nahrazení správným portem), měli byste vidět následující:

    ![Spuštění aplikace v prohlížeči s argumenty](media/asp-net-core-image10.png)

## <a name="troubleshooting"></a>Řešení potíží

Pokud potřebujete nainstalovat rozhraní .NET Core ručně na Mac OS 10.12 (Sierra) a vyšší, postupujte takto:

1. Než začnete instalovat .NET Core, ujistěte se, že jste aktualizovali všechny aktualizace operačního systému na nejnovější stabilní verzi. Můžete to zkontrolovat tak, že přejdete do aplikace App Store a vyberete kartu Aktualizace.

2. Postupujte podle kroků uvedených na [webu .NET Core](https://www.microsoft.com/net/core#macos).

Ujistěte se, že úspěšně provést všechny kroky, aby bylo zajištěno, že .NET Core je nainstalován úspěšně.

## <a name="summary"></a>Souhrn

Tato příručka poskytla úvod do ASP.NET Core. Popisuje, co to je, kdy ji použít a za předpokladu, informace o jeho použití v sadě Visual Studio for Mac.
Další informace o dalších krocích zde naleznete v následujících průvodcích:
- [ASP.NET hlavní](/aspnet/core/?view=aspnetcore-2.1#build-web-apis-and-web-ui-using-aspnet-core-mvc) dokumenty.
- [Vytváření back-endových služeb pro nativní mobilní aplikace](/aspnet/core/mobile/native-mobile-backend), které ukazují, jak vytvořit službu REST pomocí ASP.NET Core pro aplikaci Xamarin.Forms.
- [ASP.NET základní praktickou laboratoř](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started).

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Build-Your-First-App/player]
