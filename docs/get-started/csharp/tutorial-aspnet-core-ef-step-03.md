---
title: 'Krok 3: práce s daty v aplikaci ASP.NET Core'
description: Pomocí tohoto výukového kurzu a podrobného postupu začněte pracovat s daty pomocí Entity Framework Core v ASP.NET Core webové aplikaci.
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
ms.openlocfilehash: 42bc0442dc5901f92fc8a83b7af41c1fc42f4be4
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2020
ms.locfileid: "88250805"
---
# <a name="step-3-work-with-data-using-entity-framework"></a>Krok 3: práce s daty pomocí Entity Framework

Pomocí následujícího postupu můžete začít pracovat s daty pomocí Entity Framework Core ve webové aplikaci ASP.NET Core.

_Podívejte se na toto video a sledujte, jak přidat data do první ASP.NET Core aplikace._

> [!VIDEO https://www.youtube.com/embed/dulJCwNrqhM]

## <a name="open-your-project"></a>Otevřete projekt

Pokud spolu s těmito videi sledujete, otevřete projekt webové aplikace, který jste vytvořili v předchozí části. Pokud začínáte zde, je nutné vytvořit nový projekt a zvolit **webovou aplikaci ASP.NET** a **webovou aplikaci**. Zbývající možnosti ponechte jako výchozí.

## <a name="add-your-model"></a>Přidání modelu

První věc, kterou potřebujete udělat pro práci s daty v aplikaci ASP.NET Core, je popište, jak by měla vypadat. Voláme, že vytváříme *model* věcí, které se účastní problému, který se snažíme vyřešit. V reálných aplikacích přidáme do těchto modelů vlastní obchodní logiku, aby se mohla chovat určitým způsobem a automatizovat úkoly pro nás. V této ukázce vytvoříme jednoduchý systém pro sledování her na vývěsce. Potřebujeme třídu, která představuje hru, a obsahuje některé vlastnosti, které můžeme chtít nahrávat o této hře, třeba kolik hráčů může podporovat. Tato třída přejde do nové složky, kterou vytvoříme v kořenu webového projektu, který se nazývá *modely*.

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

## <a name="create-the-pages-to-manage-your-game-library"></a>Vytvořit stránky pro správu herní knihovny

Teď jsme připraveni vytvořit stránky, které budeme používat ke správě naší knihovny her. To může být zvuk těžké, ale ve skutečnosti je to úžasné snadné. Nejdřív musíme rozhodnout, kde v naší aplikaci by měla být tato funkce živá. Otevřete složku stránky ve webovém projektu a přidejte do ní novou složku. Zavolejte IT *hry*.

Nyní klikněte pravým tlačítkem na hry a vyberte **Přidat**  >  **novou vygenerované položky**. Vyberte možnost Razor Pages pomocí **Entity Framework (CRUD)** . CRUD představuje možnost vytvořit, číst, aktualizovat, odstranit a tato šablona vytvoří stránky pro každou z těchto operací (včetně stránky seznam všech) a "zobrazení podrobností jedné položky".

![Visual Studio 2019 ASP.NET Core Přidání vygenerovaných stránek](media/vs-2019/vs2019-add-scaffold.png)

Vyberte třídu herního modelu a pomocí ikony + přidejte novou třídu datového kontextu. Pojmenujte ji `AppDbContext`. Nechejte zbývající výchozí hodnoty a klikněte na **Přidat**.

Na složku hry se zobrazí následující Razor Pages:

- Vytvořit. cshtml
- Odstranit. cshtml
- Podrobnosti. cshtml
- Upravit. cshtml
- Soubor Index.cshtml

![Sady Visual Studio 2019 ASP.NET Core vygenerované stránky](media/vs-2019/vs2019-scaffolded-pages.png)

Kromě přidávání stránek ve složce *hry* , operace generování uživatelského rozhraní přidala kód do třídy *Startup.cs* . Při hledání v `ConfigureServices` metodě v této třídě se zobrazí tento kód:

```csharp
services.AddDbContext<AppDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("AppDbContext")));
```

Také najdete připojovací řetězec, který byl `AppDbContext` přidán do *appsettings.jsprojektu v* souboru.

Pokud aplikaci teď spustíte, může selhat, protože se ještě nevytvořila žádná databáze. Aplikaci můžete nakonfigurovat tak, aby v případě potřeby automaticky vytvořila databázi, a to tak, že [do program.cs přidáte nějaký kód](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio#update-main):

```csharp
public static void Main(string[] args)
{
    var host = CreateWebHostBuilder(args).Build();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        try
        {
            var context = services.GetRequiredService<Data.AppDbContext>();
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

Chcete-li přeložit TypeName v předchozím kódu, přidejte následující příkazy using do *program.cs* na konci existujícího bloku using příkaz:

```csharp
using Microsoft.Extensions.DependencyInjection;
using WebApplication1.Models;
```

Nezapomeňte použít název projektu místo WebApplication1 ve vašem kódu.

Většina kódu je jenom pro zpracování chyb a poskytuje přístup k EF Core `AppDbContext` před spuštěním aplikace. Důležitý řádek je ten, který říká `context.Database.EnsureCreated()` , že databáze bude vytvořena, pokud ještě neexistuje. Aplikace je teď připravená ke spuštění.

## <a name="test-it-out"></a>Testování

Spusťte aplikaci a `/Games` v adresním řádku přejděte na adresu. Zobrazí se prázdná stránka seznamu. Kliknutím na **vytvořit novou** přidejte `Game` do kolekce nový. Vyplňte formulář a klikněte na **vytvořit**. Měla by se zobrazit v zobrazení seznamu. Kliknutím na **Podrobnosti** zobrazíte podrobnosti o jednom záznamu.

Přidejte další záznam. Můžete kliknout na *Upravit* a změnit podrobnosti záznamu nebo **Odstranit** , abyste ho odebrali, což vás vyzve k potvrzení před skutečným odstraněním záznamu.

![Sady Visual Studio 2019 ASP.NET Core vygenerované stránky v prohlížeči](media/vs-2019/vs2019-game-list.png)

To je všechno, co trvalo začít pracovat s daty v aplikaci ASP.NET Core pomocí EF Core a sady Visual Studio 2019.

## <a name="next-steps"></a>Další kroky

V dalším videu se dozvíte, jak do vaší aplikace přidat podporu webového rozhraní API.

[Krok 4: zpřístupnění webového rozhraní API z aplikace ASP.NET Core](tutorial-aspnet-core-ef-step-04.md)

## <a name="see-also"></a>Viz také

- [Razor Pages s Entity Framework Core v ASP.NET Core](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio)
- [ASP.NET Core Razor Pages s EF Core](/aspnet/core/data/?view=aspnetcore-2.1)
