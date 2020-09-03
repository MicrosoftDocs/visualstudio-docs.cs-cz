---
title: 'Krok 4: zpřístupnění webového rozhraní API z aplikace ASP.NET Core'
description: Pomocí tohoto výukového kurzu a podrobného postupu přidejte do své ASP.NET Core webové aplikace webové rozhraní API.
ms.custom: get-started
ms.date: 02/13/2020
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
ms.openlocfilehash: 5ea9468bdf86986ab542fb1cabc873c9aeb75fd6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77580047"
---
# <a name="step-4-expose-a-web-api-from-your-aspnet-core-app"></a>Krok 4: vystavení webového rozhraní API z aplikace ASP.NET Core

Pomocí těchto kroků přidáte webové rozhraní API do existující aplikace ASP.NET Core.

_Podívejte se na toto video a sledujte společně a přidejte podporu webového rozhraní API do vaší první ASP.NET Core aplikace._

> [!VIDEO https://www.youtube.com/embed/o_fYPOsAXts]

## <a name="open-your-project"></a>Otevřete projekt

Otevřete aplikaci ASP.NET Core v aplikaci Visual Studio 2019. Aplikace by už měla používat EF Core ke správě typů modelů, jak je nakonfigurované v [kroku 3 této série kurzů](tutorial-aspnet-core-ef-step-03.md).

## <a name="add-an-api-controller"></a>Přidat kontroler rozhraní API

Klikněte pravým tlačítkem na projekt a přidejte novou složku s názvem *rozhraní API*. Pak klikněte pravým tlačítkem na tuto složku a zvolte **Přidat**  >  **novou vygenerované položky**. **Pomocí Entity Framework vyberte možnost kontroler API s akcemi.** Nyní vyberte existující třídu modelu a klikněte na **Přidat**.

![Visual Studio 2019 ASP.NET Core vygenerovaného kontroleru rozhraní API](media/vs-2019/vs2019-add-scaffold-api.png)

## <a name="reviewing-the-generated-controller"></a>Kontrola vygenerovaného kontroleru

Vygenerovaný kód zahrnuje novou třídu kontroleru. V horní části definice třídy jsou dva atributy.

```csharp
[Route("api/[controller]")]
[ApiController]
public class GamesController : ControllerBase
```

První z nich určuje trasu pro akce v tomto kontroleru, `api/[controller]` což znamená, že pokud se kontroler nazývá, `GamesController` bude se jednat o trasu `api/Games` .

Druhý atribut, `[ApiController]` , přidá do třídy několik užitečných ověření, jako je například zajistěte, aby každá metoda Action zahrnovala vlastní `[Route]` atribut.

```csharp
public class GamesController : ControllerBase
{
    private readonly AppDbContext _context;

    public GamesController(AppDbContext context)
    {
        _context = context;
    }
```

Kontroler použije existující `AppDbContext` předaný do svého konstruktoru. Každá akce použije toto pole pro práci s daty aplikace.

```csharp
// GET: api/Games
[HttpGet]
public IEnumerable<Game> GetGame()
{
    return _context.Game;
}
```

První metoda je jednoduchý požadavek GET, jak je uvedeno pomocí `[HttpGet]` atributu. Nepřijímá žádné parametry a vrací seznam všech her v databázi.

```csharp
// GET: api/Games/5
[HttpGet("{id}")]
public async Task<IActionResult> GetGame([FromRoute] int id)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    var game = await _context.Game.FindAsync(id);

    if (game == null)
    {
        return NotFound();
    }

    return Ok(game);
}
```

Následující metoda určuje `{id}` trasu, která bude přidána do trasy následující po, `/` takže úplná trasa bude vypadat `api/Games/5` jako v komentáři v horní části. `id`Vstup je namapován na `id` parametr v metodě. V případě, že je model neplatný, je v rámci metody `BadRequest` vrácen výsledek. V opačném případě se EF pokusí najít záznam, který odpovídá poskytnutému `id` . Pokud `NotFound` není výsledek vrácen, v opačném případě `Game` se vrátí příslušný záznam.

```csharp
// PUT: api/Games/5
[HttpPut("{id}")]
public async Task<IActionResult> PutGame([FromRoute] int id, [FromBody] Game game)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    if (id != game.Id)
    {
        return BadRequest();
    }

    _context.Entry(game).State = EntityState.Modified;

    try
    {
        await _context.SaveChangesAsync();
    }
    catch (DbUpdateConcurrencyException)
    {
        if (!GameExists(id))
        {
            return NotFound();
        }
        else
        {
            throw;
        }
    }

    return NoContent();
}
```

V dalším kroku `[HttpPut]` se k provádění aktualizací používá požadavek na rozhraní API. Nový `Game` záznam je uveden v těle žádosti. Provede se kontrola ověřování a chyb a pokud je vše úspěšné, záznam v databázi se aktualizuje o hodnoty uvedené v těle žádosti. V opačném případě se vrátí vhodná chybová odpověď.

```csharp
// POST: api/Games
[HttpPost]
public async Task<IActionResult> PostGame([FromBody] Game game)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    _context.Game.Add(game);
    await _context.SaveChangesAsync();

    return CreatedAtAction("GetGame", new { id = game.Id }, game);
}
```

`[HttpPost]`Požadavek se používá k přidání nových záznamů do systému. Stejně jako u se `[HttpPut]` záznam přidá do těla žádosti. Pokud je platný, EF Core přidá záznam do databáze a akce vrátí aktualizovaný záznam (s vygenerovaným ID databáze) a odkaz na záznam v rozhraní API.

```csharp
// DELETE: api/Games/5
[HttpDelete("{id}")]
public async Task<IActionResult> DeleteGame([FromRoute] int id)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    var game = await _context.Game.FindAsync(id);
    if (game == null)
    {
        return NotFound();
    }

    _context.Game.Remove(game);
    await _context.SaveChangesAsync();

    return Ok(game);
}
```

Nakonec se k `[HttpDelete]` odstranění záznamu používá trasa s ID. Pokud je požadavek platný a záznam s daným ID existuje, EF Core jej odstranit z databáze.

## <a name="adding-swagger"></a>Přidává se Swagger.

Swagger je dokumentace a nástroj pro testování rozhraní API, které je možné přidat jako sadu služeb a middlewaru do ASP.NET Core aplikace. Provedete to tak, že kliknete pravým tlačítkem na projekt a zvolíte **Spravovat balíčky NuGet**. Pak klikněte na **Procházet**, vyhledejte `Swashbuckle.AspNetCore` a nainstalujte verzi 4.0.1.

![Visual Studio 2019 přidání swashbuckle z NuGet](media/vs-2019/vs2019-nuget-swashbuckle.png)

Po instalaci otevřete `Startup.cs` a na konec metody přidejte následující `ConfigureServices` :

```csharp
services.AddSwaggerGen(c =>
{
    c.SwaggerDoc("v1", new Info { Title = "My API", Version = "v1" });
});
```

Budete také muset přidat `using Swashbuckle.AspNetCore.Swagger;` na začátek souboru.

Dále do metody přidejte následující `Configure` příkaz těsně před `UseMvc` :

```csharp
// Enable middleware to serve generated Swagger as a JSON endpoint.
app.UseSwagger();

// Enable middleware to serve swagger-ui (HTML, JS, CSS, etc.), 
// specifying the Swagger JSON endpoint.
app.UseSwaggerUI(c =>
{
    c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
});
```

Nyní byste měli být schopni sestavit a spustit vaši aplikaci. V prohlížeči přejděte na `/swagger` adresu v adresním řádku. Měl by se zobrazit seznam koncových bodů a modelů rozhraní API vaší aplikace. 

![Stránka Swagger sady Visual Studio 2019 v prohlížeči](media/vs-2019/vs2019-swagger-browser.png)

V části hry klikněte na koncový bod, `Try it out` a pokud `Execute` chcete zjistit, jak se chovají různé koncové body.

## <a name="next-steps"></a>Další kroky

V dalším videu se naučíte, jak nasadit aplikaci do Azure.

[Krok 5: nasazení aplikace ASP.NET Core do Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="see-also"></a>Viz také

- [Začínáme s swashbuckle a ASP.NET Core](/aspnet/core/tutorials/getting-started-with-swashbuckle?view=aspnetcore-2.2&tabs=visual-studio)
- [Stránky s OpenAPI s webovým rozhraním API pomocí Swagger/ASP.NET Core](/aspnet/core/tutorials/web-api-help-pages-using-swagger?view=aspnetcore-2.2)