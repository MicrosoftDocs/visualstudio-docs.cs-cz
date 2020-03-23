---
title: 'Krok 4: Vystavení webového rozhraní API z aplikace ASP.NET Core'
description: Přidejte webové rozhraní API do ASP.NET Core Web App s tímto instruktážním videu a podrobnými pokyny.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580047"
---
# <a name="step-4-expose-a-web-api-from-your-aspnet-core-app"></a>Krok 4: Vystavení webového rozhraní API z aplikace ASP.NET Core

Podle těchto kroků přidáte webové rozhraní API do stávající aplikace ASP.NET Core.

_Podívejte se na toto video a postupujte podle pokynů a přidejte podporu webového rozhraní API do první aplikace ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/o_fYPOsAXts]

## <a name="open-your-project"></a>Otevření projektu

Otevřete aplikaci ASP.NET Core ve Visual Studiu 2019. Aplikace by již měla používat EF Core ke správě typů modelů, jak je nakonfigurováno v [kroku 3 této série kurzů](tutorial-aspnet-core-ef-step-03.md).

## <a name="add-an-api-controller"></a>Přidání řadiče rozhraní API

Klikněte pravým tlačítkem myši na projekt a přidejte novou složku s názvem *Api*. Poté klikněte pravým tlačítkem myši na tuto složku a zvolte **Přidat** > **novou scaffolded položku**. Zvolte **řadič rozhraní API s akcemi pomocí entity Framework.** Nyní zvolte existující třídu modelu a klepněte na **tlačítko Přidat**.

![Visual Studio 2019 ASP.NET core scaffolded řadič rozhraní API](media/vs-2019/vs2019-add-scaffold-api.png)

## <a name="reviewing-the-generated-controller"></a>Kontrola generovaného řadiče

Generovaný kód obsahuje novou třídu kontroleru. V horní části definice třídy jsou dva atributy.

```csharp
[Route("api/[controller]")]
[ApiController]
public class GamesController : ControllerBase
```

První určuje trasu pro akce v tomto `api/[controller]` řadiči jako což `GamesController` znamená, `api/Games`že pokud je řadič pojmenován, trasa bude .

Druhý atribut `[ApiController]`, přidá některé užitečné ověření třídy, jako je například `[Route]` zajištění, že každá metoda akce obsahuje svůj vlastní atribut.

```csharp
public class GamesController : ControllerBase
{
    private readonly AppDbContext _context;

    public GamesController(AppDbContext context)
    {
        _context = context;
    }
```

Řadič používá existující `AppDbContext`, předán do jeho konstruktoru. Každá akce použije toto pole pro práci s daty aplikace.

```csharp
// GET: api/Games
[HttpGet]
public IEnumerable<Game> GetGame()
{
    return _context.Game;
}
```

První metoda je jednoduchý požadavek GET, `[HttpGet]` jak je určeno pomocí atributu. Nepřijímá žádné parametry a vrátí seznam všech her v databázi.

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

Další metoda určuje `{id}` v trase, která bude přidána `/` do trasy po, `api/Games/5` takže úplná trasa bude něco jako v komentáři v horní části. Vstup `id` je mapován `id` na parametr metody. Uvnitř metody, pokud je model `BadRequest` neplatný, je vrácen výsledek. V opačném případě se EF pokusí najít `id`záznam odpovídající poskytnutému souboru . Pokud nelze `NotFound` výsledek je vrácena, jinak `Game` je vrácen příslušný záznam.

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

Dále požadavek `[HttpPut]` na rozhraní API se používá k provádění aktualizací. Nový `Game` záznam je k dispozici v textu požadavku. Některé ověření a kontrola chyb se provádí a pokud je vše úspěšné, záznam v databázi je aktualizován s hodnotami v těle požadavku. V opačném případě je vrácena příslušná odpověď na chybu.

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

Požadavek `[HttpPost]` se používá k přidání nových záznamů do systému. Stejně `[HttpPut]`jako v oblasti , je záznam přidán do těla požadavku. Pokud je platný, EF Core přidá záznam do databáze a akce vrátí aktualizovaný záznam (s jeho databáze generované ID) a odkaz na záznam v rozhraní API.

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

Nakonec se `[HttpDelete]` k odstranění záznamu používá trasa s ID. Pokud je požadavek platný a existuje záznam s daným ID, EF Core jej odstraní z databáze.

## <a name="adding-swagger"></a>Přidání Swagger

Swagger je nástroj pro dokumentaci a testování rozhraní API, který lze přidat jako sadu služeb a middlewaru do aplikace ASP.NET Core. Chcete-li tak učinit, klepněte pravým tlačítkem myši na projekt a zvolte **Spravovat balíčky NuGet**. Potom klepněte na `Swashbuckle.AspNetCore` **tlačítko Procházet**, vyhledejte a nainstalujte verzi 4.0.1.

![Visual Studio 2019 Přidat swashbuckle z Nuget](media/vs-2019/vs2019-nuget-swashbuckle.png)

Po instalaci `Startup.cs` otevřete a přidejte na `ConfigureServices` konec metody následující:

```csharp
services.AddSwaggerGen(c =>
{
    c.SwaggerDoc("v1", new Info { Title = "My API", Version = "v1" });
});
```

Budete také muset přidat `using Swashbuckle.AspNetCore.Swagger;` v horní části souboru.

Dále přidejte do `Configure` metody následující: `UseMvc`

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

Nyní byste měli být schopni vytvořit a spustit aplikaci. V prohlížeči přejděte na `/swagger` panelu Adresa. Měli byste vidět seznam koncových bodů rozhraní API a modelů vaší aplikace. 

![Visual Studio 2019 Swagger Page v prohlížeči](media/vs-2019/vs2019-swagger-browser.png)

Potom klikněte na koncový `Try it out` `Execute` bod v části Hry a podívejte se, jak se chovají různé koncové body.

## <a name="next-steps"></a>Další kroky

V dalším videu se dozvíte, jak nasadit aplikaci do Azure.

[Krok 5: Nasazení aplikace ASP.NET Core do Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="see-also"></a>Viz také

- [Začínáme s Swashbuckle a ASP.NET Core](/aspnet/core/tutorials/getting-started-with-swashbuckle?view=aspnetcore-2.2&tabs=visual-studio)
- [ASP.NET Stránky nápovědy pro webové rozhraní API s Swagger / OpenAPI](/aspnet/core/tutorials/web-api-help-pages-using-swagger?view=aspnetcore-2.2)