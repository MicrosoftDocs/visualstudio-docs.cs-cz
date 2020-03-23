---
title: 'Krok 3: Práce s daty ve vaší aplikaci ASP.NET Core'
description: Začněte pracovat s daty pomocí entity Framework Core ve vašem ASP.NET Core Web App s tímto instruktážním videu a podrobnými pokyny.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: cef0db7e5615d08fb5b22c38604a24124c853ebd
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580064"
---
# <a name="step-3-work-with-data-using-entity-framework"></a>Krok 3: Práce s daty pomocí entity Framework

Podle těchto kroků začněte pracovat s daty pomocí entity Framework Core ve vašem ASP.NET Core Web App.

_Podívejte se na toto video a postupujte podle pokynů a přidejte data do první aplikace ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/dulJCwNrqhM]

## <a name="open-your-project"></a>Otevření projektu

Pokud sledujete tato videa, otevřete projekt webové aplikace, který jste vytvořili v předchozí části. Pokud začínáte tady, musíte vytvořit nový projekt a zvolit **ASP.NET webovou aplikaci** a pak **webovou aplikaci**. Zbývající možnosti ponechejte jako výchozí.

## <a name="add-your-model"></a>Přidání modelu

První věc, kterou musíte udělat pro práci s daty v aplikaci ASP.NET Core, je popsat, jak by měla data vypadat. Říkáme tomu vytvoření *modelu* věcí, které se týkají problému, který se snažíme vyřešit. V reálných aplikacích přidáme k těmto modelům vlastní obchodní logiku, aby se mohly určitým způsobem chovat a automatizovat úkoly. Pro tuto ukázku vytvoříme jednoduchý systém pro sledování deskových her. Potřebujeme třídu, která představuje hru a obsahuje některé vlastnosti, které bychom mohli chtít zaznamenat o této hře, jako kolik hráčů může podporovat. Tato třída přejde do nové složky, kterou vytvoříme v kořenovém adresáři webového projektu s názvem *Modely*.

```csharp
public class Game
{
    public int Id { get; set; }
    public string Title { get; set; }
    public int PublicationYear { get; set; }
    public int MinimumPlayers { get; set; }
    public int MaximumPlayers { get; set; }
}
```

## <a name="create-the-pages-to-manage-your-game-library"></a>Vytvoření stránek pro správu knihovny her

Nyní jsme připraveni vytvořit stránky, které použijeme ke správě naší knihovny her. To může znít skličující, ale je to vlastně úžasně snadné. Nejprve se musíme rozhodnout, kde v naší aplikaci by tato funkce měla žít. Otevřete složku Stránky ve webovém projektu a přidejte tam novou složku. Nazvěme to *hry*.

Nyní klikněte pravým tlačítkem myši na hry a zvolte **Přidat** > **nový scaffolded položky**. Zvolte volbu Razor Pages using **Entity Framework (CRUD).** CRUD je zkratka pro "Vytvořit, Číst, Aktualizovat, Odstranit" a tato šablona vytvoří stránky pro každou z těchto operací (včetně stránky "seznam všech" a stránky "zobrazit podrobnosti o jedné položce").

![Visual Studio 2019 ASP.NET Základní Přidat scaffolded stránky](media/vs-2019/vs2019-add-scaffold.png)

Vyberte třídu herního modelu a pomocí ikony +přidejte novou třídu kontextu Dat. Pojmenujte ji `AppDbContext`. Zbytek ponechejte jako výchozí a klepněte na **tlačítko Přidat**.

Do složky Hry se zobrazí následující stránky Razor:

- Vytvořit.cshtml
- Odstranit.cshtml
- Details.cshtml
- Upravit.cshtml
- Soubor Index.cshtml

![Visual Studio 2019 ASP.NET stránky s kládaným vzorem](media/vs-2019/vs2019-scaffolded-pages.png)

Kromě přidání stránek do složky *Hry* přidala operace lešení kód do mé *třídy Startup.cs.* Při pohledu na metodu `ConfigureServices` v této třídě uvidíte, že tento kód byl přidán:

```csharp
services.AddDbContext<AppDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("AppDbContext")));
```

Najdete zde také `AppDbContext` připojení řetězec byl přidán do projektu *appsettings.json* souboru.

Pokud spustíte aplikaci nyní, může selhat, protože zatím nebyla vytvořena žádná databáze. Aplikaci můžete nakonfigurovat tak, aby v případě potřeby automaticky vytvářela databázi [přidáním nějakého kódu, který Program.cs](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio#update-main):

```csharp
public static void Main(string[] args)
{
    var host = CreateWebHostBuilder(args).Build();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        try
        {
            var context = services.GetRequiredService<AppDbContext>();
            context.Database.EnsureCreated();
        }
        catch (Exception ex)
        {
            var logger = services.GetRequiredService<ILogger<Program>>();
            logger.LogError(ex, "An error occurred creating the DB.");
        }
    }

    host.Run();
}
```

Chcete-li přeložit názvy typů v předchozím kódu, přidejte následující příkazy using, které *Program.cs* na konci existujícího bloku using statements:

```csharp
using Microsoft.Extensions.DependencyInjection;
using WebApplication1.Models;
```

Ujistěte se, že použít název projektu namísto WebApplication1 v kódu.

Většina kódu je pouze pro zpracování chyb a `AppDbContext` poskytnout přístup k EF Core před spuštěním aplikace. Důležitý řádek je ten, `context.Database.EnsureCreated()`který říká , který vytvoří databázi, pokud již neexistuje. Nyní je aplikace připravena ke spuštění.

## <a name="test-it-out"></a>Testování

Spusťte aplikaci `/Games` a přejděte na adresu v panelu Adresa. Zobrazí se prázdná stránka se seznamem. Kliknutím na **Vytvořit** nový `Game` přidejte do kolekce nové. Vyplňte formulář a klepněte na **tlačítko Vytvořit**. Měli byste ji vidět v zobrazení seznamu. Kliknutím na **Podrobnosti** zobrazíte podrobnosti o jednom záznamu.

Přidejte další záznam. Kliknutím na *Upravit* můžete změnit podrobnosti záznamu nebo **odstranit** a odebrat ho, což vás vyzve k potvrzení před jeho skutečně odstraněním záznamu.

![Visual Studio 2019 ASP.NET v prohlížeči stránky s kládaným vzorem](media/vs-2019/vs2019-game-list.png)

To je vše, co bylo třeba začít pracovat s daty v aplikaci ASP.NET Core pomocí EF Core a Visual Studio 2019.

## <a name="next-steps"></a>Další kroky

V dalším videu se dozvíte, jak do aplikace přidat podporu webového rozhraní API.

[Krok 4: Vystavení webového rozhraní API z aplikace ASP.NET Core](tutorial-aspnet-core-ef-step-04.md)

## <a name="see-also"></a>Viz také

- [Razor stránky s jádrem entity frameworku v ASP.NET jádru](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio)
- [ASP.NET jádro holicí strojek stránky s EF Core](/aspnet/core/data/?view=aspnetcore-2.1)
