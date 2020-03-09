---
title: Techniky ladění a související nástroje
description: Pomocí sady Visual Studio můžete napsat lepší kód s méně chybami, aby se opravily výjimky, opravili chyby a vylepšili váš kód.
ms.custom:
- debug-experiment
- seodec18
ms.date: 02/14/2020
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ac595098d793e44d65312a09fc8857225f150ef
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409190"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Techniky a nástroje ladění, které vám pomůžou psát lepší kód

Oprava chyb a chyb v kódu může být časově náročná a někdy frustrujícíá. Může zabrat určitý čas zjistěte, jak efektivně ladit, ale výkonné prostředí IDE, jako je Visual Studio může být vaše úloha mnohem snazší. Integrované vývojové prostředí (IDE) vám může pomoct opravovat chyby a ladit kód rychleji a nejen to, ale může také pomoct psát lepší kód s méně chybami. Naším cílem v tomto článku je poskytnout holistický zobrazení procesu "opravování chyb", takže budete znát, kdy použít analyzátor kódu, kdy použít ladicí program, jak opravit výjimky a jak provést kód pro záměr. Pokud už víte, že potřebujete použít ladicí program, přečtěte si téma [první pohled na ladicí program](../debugger/debugger-feature-tour.md).

V tomto článku se seznámíme s využitím integrovaného vývojového prostředí (IDE) k zajištění vyšší produktivity vašich relací kódování. Jsme dotykového ovládání na několik úloh, jako například:

* Připravte váš kód pro ladění s využitím analyzátor kódu rozhraní IDE

* Jak vyřešit výjimky (– chyby za běhu)

* Jak minimalizovat chyby pomocí kódování pro záměr (pomocí vyhodnocení)

* Kdy použít ladicí program

Abychom si předvedli tyto úlohy, vám ukážeme některé z nejběžnějších typů chyb a chyb, ke které dojde při pokusu o ladění aplikací. I když ukázkový kód je C#koncepční informace je obecně platný pro jazyk JavaScript, C++, Visual Basic, a podporuje další jazyky sady Visual Studio (Pokud není uvedeno jinak). Snímky obrazovky jsou v jazyce C#.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Vytvoření ukázkové aplikace s některými chybami a chybami

Následující kód obsahuje chyby, které můžete vyřešit pomocí integrovaného vývojového prostředí sady Visual Studio. Tady aplikace je jednoduchá aplikace, která simuluje získávání dat JSON z některé operace, deserializaci datového objektu a jednoduchý seznam se aktualizuje s novými daty.

Vytvoření aplikace:

1. Musíte mít nainstalovanou aplikaci Visual Studio a nainstalovanou aplikaci **.NET Core pro vývoj pro různé platformy** nebo **desktopové vývojové prostředí .NET** v závislosti na typu aplikace, kterou chcete vytvořit.

    Pokud jste ještě nenainstalovali aplikaci Visual Studio, můžete ji nainstalovat zdarma na stránce pro [Stažení sady Visual studio](https://visualstudio.microsoft.com/downloads/) .

    Pokud potřebujete nainstalovat úlohu, ale už máte Visual Studio, klikněte na **nástroje** > **získat nástroje a funkce**. Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoj pro různé platformy .NET Core** nebo **vývoj desktopových aplikací .NET** a pak zvolte **Upravit**.

1. Otevřete sadu Visual Studio.

    ::: moniker range=">=vs-2019"
    V okně Start vyberte možnost **vytvořit nový projekt**. Do vyhledávacího pole zadejte **Console** a pak zvolte buď **Konzolová aplikace (.NET Core)** , nebo **aplikace konzoly (.NET Framework)** . Zvolte **Další**. Zadejte název projektu, například **Console_Parse_JSON** a klikněte na **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**. V levém podokně dialogového okna **Nový projekt** , v části **C#vizuál**zvolte **Konzolová aplikace**a pak v prostředním podokně zvolte buď **Konzolová aplikace (.NET Core)** nebo **aplikace konzoly (.NET Framework)** . Zadejte název, například **Console_Parse_JSON** a klikněte na tlačítko **OK**.
    ::: moniker-end

    Pokud nevidíte šablonu projektu **Konzolová aplikace (.NET Core)** nebo **aplikace konzoly (.NET Framework)** , přejděte do části **nástroje** > **získat nástroje a funkce**, které otevřou instalační program pro Visual Studio. Zvolte buď možnost **vývoj pro různé platformy .NET Core** , nebo **desktopový vývoj** pro platformu .NET a pak zvolte možnost **Upravit**.

    Visual Studio vytvoří projekt konzoly, který se zobrazí v Průzkumník řešení v pravém podokně.

1. Nahraďte výchozí kód v souboru *program.cs* projektu následujícím ukázkovým kódem.

```csharp
using System;
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
using System.Runtime.Serialization;
using System.IO;

namespace Console_Parse_JSON
{
    class Program
    {
        static void Main(string[] args)
        {
            var localDB = LoadRecords();
            string data = GetJsonData();

            User[] users = ReadToObject(data);

            UpdateRecords(localDB, users);

            for (int i = 0; i < users.Length; i++)
            {
                List<User> result = localDB.FindAll(delegate (User u) {
                    return u.lastname == users[i].lastname;
                    });
                foreach (var item in result)
                {
                    Console.WriteLine($"Matching Record, got name={item.firstname}, lastname={item.lastname}, age={item.totalpoints}");
                }
            }

            Console.ReadKey();
        }

        // Deserialize a JSON stream to a User object.
        public static User[] ReadToObject(string json)
        {
            User deserializedUser = new User();
            User[] users = { };
            MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(json));
            DataContractJsonSerializer ser = new DataContractJsonSerializer(users.GetType());

            users = ser.ReadObject(ms) as User[];

            ms.Close();
            return users;
        }

        // Simulated operation that returns JSON data.
        public static string GetJsonData()
        {
            string str = "[{ \"points\":4o,\"firstname\":\"Fred\",\"lastname\":\"Smith\"},{\"lastName\":\"Jackson\"}]";
            return str;
        }

        public static List<User> LoadRecords()
        {
            var db = new List<User> { };
            User user1 = new User();
            user1.firstname = "Joe";
            user1.lastname = "Smith";
            user1.totalpoints = 41;

            db.Add(user1);

            User user2 = new User();
            user2.firstname = "Pete";
            user2.lastname = "Peterson";
            user2.totalpoints = 30;

            db.Add(user2);

            return db;
        }
        public static void UpdateRecords(List<User> db, User[] users)
        {
            bool existingUser = false;

            for (int i = 0; i < users.Length; i++)
            {
                foreach (var item in db)
                {
                    if (item.lastname == users[i].lastname && item.firstname == users[i].firstname)
                    {
                        existingUser = true;
                        item.totalpoints += users[i].points;

                    }
                }
                if (existingUser == false)
                {
                    User user = new User();
                    user.firstname = users[i].firstname;
                    user.lastname = users[i].lastname;
                    user.totalpoints = users[i].points;

                    db.Add(user);
                }
            }
        }
    }

    [DataContract]
    internal class User
    {
        [DataMember]
        internal string firstname;

        [DataMember]
        internal string lastname;

        [DataMember]
        // internal double points;
        internal string points;

        [DataMember]
        internal int totalpoints;
    }
}
```

## <a name="find-the-red-and-green-squiggles"></a>Najdete červenou a zelenou vlnovkou!

Předtím, než se pokusíte spustit ukázkovou aplikaci a spustit ladicí program, zkontrolujte kód v editoru kódu pro červenou a zelenou vlnovkou. Představují chyby a upozornění, které jsou označeny analyzátor kódu rozhraní IDE. Červenou vlnovkou jsou chyby při kompilaci, která je nutné opravit před spuštěním kódu. Zelenou vlnovkou se upozornění. I když často moci spustit vaši aplikaci bez opravy problémů upozornění, je možné příčiny chyb a můžete často ušetřit čas a potíže s zjišťováním je. Tato upozornění a chyby se také zobrazí v okně **Seznam chyb** , pokud dáváte přednost zobrazení seznamu.

V ukázkové aplikaci zobrazí se několik červenou vlnovkou, které je potřeba opravit a jednoho zelené, který budete podíváte na. Zde je první chyba.

![Chyba zobrazuje jako červená vlnovka](../debugger/media/write-better-code-red-squiggle.png)

Pokud chcete tuto chybu opravit, budete prohlédněte Další funkcí IDE, reprezentované ikonou žárovky.

## <a name="check-the-light-bulb"></a>Podívejte se, žárovky.

První červená vlnovka představuje chybu v době kompilace. Najeďte myší na ni a zobrazí se zpráva ```The name `Encoding` does not exist in the current context```.

Všimněte si, že tato chyba zobrazuje ikonou žárovky do levé dolní části. Společně s ikonou Screwdriver ![](../ide/media/screwdriver-icon.png)ikonu Screwdriver, ikona žárovky ![ikona žárovky](../ide/media/light-bulb-icon.png) představuje rychlé akce, které vám pomůžou s opravou nebo refaktorem vloženého kódu. Žárovka představuje problémy, které *byste měli* opravit. Šroubovák se na problémy, které je možné opravit. Pokud chcete tuto chybu vyřešit, použijte první navrhovanou opravu, která se zobrazí po kliknutí na tlačítko **použít System. text** na levé straně.

![Oprava kódu pomocí žárovky](../debugger/media/write-better-code-missing-include.png)

Po kliknutí na tuto položku Visual Studio přidá příkaz `using System.Text` v horní části souboru *program.cs* a červená vlnovka zmizí. (Pokud si nejste jistí, co Navrhovaná oprava udělá, před použitím opravy klikněte na odkaz **Náhled změn** na pravé straně.)

Předchozí chyba je běžně ta, kterou obvykle opravíte přidáním nového příkazu `using` do kódu. Existuje několik běžných podobných chyb, například ```The type or namespace `Name` cannot be found.``` tyto druhy chyb mohou indikovat chybějící odkaz na sestavení (klikněte pravým tlačítkem myši na projekt, vyberte **přidat** > **odkaz**), nesprávně napsaný název nebo chybějící knihovna, kterou potřebujete přidat (pro C#klikněte pravým tlačítkem myši na projekt a vyberte možnost **Spravovat balíčky NuGet**).

## <a name="fix-the-remaining-errors-and-warnings"></a>Oprava zbývajících chyb a upozornění

Existuje několik další podtržení vlnovkou podívat se na tento kód. Tady vidíte běžné Chyba převodu typu. Když najedete myší vlnovka, uvidíte, že se kód pokouší o převedení řetězce na typ int, což není podporováno, není-li přidat explicitní kódu k provedení převodu.

![Chyba převodu typu](../debugger/media/write-better-code-conversion-error.png)

Vzhledem k tomu, že nástroj code analyzer nelze odhadl váš záměr, nejsou žádné návrhy, které vám pomůžou této doby. Chcete-li vyřešit tuto chybu, je potřeba vědět záměru kódu. V tomto příkladu není příliš obtížné zjistit, že `points` by měla být číselná (celočíselná) hodnota, protože se pokoušíte přidat `points` do `totalpoints`.

Chcete-li tuto chybu opravit, změňte `points` člena třídy `User` z tohoto:

```csharp
[DataMember]
internal string points;
```

měli změnit na:

```csharp
[DataMember]
internal int points;
```

Červená vlnovka řádků v editoru kódu zmizet.

Dále najeďte na zelenou vlnovku v deklaraci datového člena `points`. Analyzátor kódu zjistíte, že proměnná nikdy přiřazena hodnota.

![Upozornění pro Nepřiřazené proměnnou](../debugger/media/write-better-code-warning-message.png)

Obvykle to představuje problém, který je potřeba opravit. Nicméně v ukázkové aplikaci, ve které jste ve skutečnosti ukládáte data do proměnné `points` během procesu deserializace a následně přidáte tuto hodnotu do datového členu `totalpoints`. V tomto příkladu vědět záměru kódu a můžete upozornění ignorovat. Pokud chcete odstranit toto upozornění, ale můžete nahradit následující kód:

```csharp
item.totalpoints = users[i].points;
```

tímto kódem:

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

Zelená vlnovku zmizí.

## <a name="fix-an-exception"></a>Oprava výjimky

Pokud byla opravena červenou vlnovkou a vyřešit--nebo alespoň prozkoumat – všechny zelenou vlnovkou, budete chtít spustit ladicí program a spusťte aplikaci.

Stiskněte klávesu **F5** (**ladění > Spustit ladění**) nebo klikněte na tlačítko **Spustit** ladění ![Spustit ladění](../debugger/media/dbg-tour-start-debugging.png "Spustit ladění") na panelu nástrojů ladění.

V tomto okamžiku ukázková aplikace vyvolá výjimku `SerializationException` (Chyba za běhu). To znamená, že aplikace potlačuje na data, která se pokouší serializovat. Protože jste aplikaci spustili v režimu ladění (ladicí program se připojil), pomocníka výjimky ladicího programu přejdete přímo na kód, který vyvolal výjimku a poskytuje užitečné chybovou zprávu.

![Vyvolá SerializationException](../debugger/media/write-better-code-serialization-exception.png)

Chybová zpráva vás instruuje, že `4o` hodnoty nelze analyzovat jako celé číslo. Proto v tomto příkladu víte, že data jsou chybná: `4o` by měl být `40`. Nicméně pokud nepoužíváte kontrolu nad daty v reálné scénáře (například získávají z webové služby), co můžete dělat o něm? Jak to můžete vyřešit?

Až se dostanete k výjimce, potřebujete (a odpovědí) několik otázek:

* Tato výjimka je právě chybu, která můžete opravit? Nebo:

* Je tato výjimka něco, co vaši uživatelé setkat?

Pokud je první, opravte chyby. (V ukázkové aplikaci to znamená opravit chybná data.) Pokud je to ten, může být nutné zpracovat výjimku v kódu pomocí `try/catch` bloku (v další části se podíváme na další možné strategie). V ukázkové aplikaci nahraďte následujícím kódem:

```csharp
users = ser.ReadObject(ms) as User[];
```

s tímto kódem:

```csharp
try
{
    users = ser.ReadObject(ms) as User[];
}
catch (SerializationException)
{
    Console.WriteLine("Give user some info or instructions, if necessary");
    // Take appropriate action for your app
}
```

`try/catch` blok má určité náklady na výkon, takže je budete chtít používat pouze v případě, že je skutečně potřebujete, to znamená, kde (a) mohou nastat ve verzi aplikace a kde (b) dokumentace k metodě označuje, že byste měli vyhledat výjimku (za předpokladu, že je dokumentace dokončena). V mnoha případech je odpovídajícím způsobem zpracovat výjimku a uživatel nepotřebuje vědět o něm.

Tady je několik důležitých tipů pro zpracování výjimek:

* Vyhněte se použití prázdného bloku catch, například `catch (Exception) {}`, který neprovádí odpovídající akci k vystavení nebo zpracování chyby. Blok catch prázdný nebo informativní můžete skrýt výjimky a může ztížit váš kód ladit místo snazší.

* Použijte `try/catch` blok kolem konkrétní funkce, která vyvolá výjimku (`ReadObject`v ukázkové aplikaci). Když ho používáte kolem větší blok kódu, skončíte skrytí umístění chyby. Nepoužívejte například `try/catch` blok kolem volání nadřazené funkce `ReadToObject`, zobrazená zde, nebo neznáte přesně, kde k výjimce došlo.

    ```csharp
    // Don't do this
    try
    {
        User[] users = ReadToObject(data);
    }
    catch (SerializationException)
    {
    }
    ```

* V případě neznámých funkcí, které zahrnete do aplikace, zejména při interakci s externími daty (například webovými požadavky), Projděte si dokumentaci, kde najdete výjimky, které funkce může vyvolat. To může být důležité informace pro zpracování chyb správné a pro ladění vaší aplikace.

Pro ukázkovou aplikaci opravte `SerializationException` v metodě `GetJsonData` změnou `4o` na `40`.

## <a name="clarify-your-code-intent-by-using-assert"></a>Upřesněte svůj záměr váš kód s využitím assert

Klikněte na tlačítko **restartovat** ![aplikaci](../debugger/media/dbg-tour-restart.png "RestartApp") na panelu nástrojů ladění (**CTRL** + **SHIFT** + **F5**). Tím se znovu spustí aplikaci v méně kroků. Zobrazí se následující výstup v okně konzoly.

![Hodnotu Null ve výstupu](../debugger/media/write-better-code-using-assert-null-output.png)

Můžete zobrazit něco tento výstup, který není úplně vpravo. **jméno** a **příjmení** třetího záznamu je prázdné.

To je dobrý čas na komunikaci s užitečným postupem kódování, který je často nevyužitý, což je použití příkazů `assert` ve vašich funkcích. Přidáním následujícího kódu zahrnete kontrolu za běhu, abyste se ujistili, že `firstname` a `lastname` nejsou `null`. V metodě `UpdateRecords` nahraďte následující kód:

```csharp
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

tímto kódem:

```csharp
// Also, add a using statement for System.Diagnostics at the start of the file.
Debug.Assert(users[i].firstname != null);
Debug.Assert(users[i].lastname != null);
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

Přidáním `assert`ch příkazů, jako je to pro vaše funkce během procesu vývoje, můžete určit záměr kódu. V předchozím příkladu jsme zadejte následující informace:

* Platný řetězec pro se vyžaduje jméno
* Platný řetězec pro se vyžaduje příjmení

Zadáním záměr tímto způsobem vynutit vašim požadavkům. Toto je jednoduchý a užitečný metodu, která vám pomůže surface chyb během vývoje. (příkazy`assert` jsou také použity jako hlavní prvek v testování částí.)

Klikněte na tlačítko **restartovat** ![aplikaci](../debugger/media/dbg-tour-restart.png "RestartApp") na panelu nástrojů ladění (**CTRL** + **SHIFT** + **F5**).

> [!NOTE]
> Kód `assert` je aktivní pouze v sestavení ladění.

Po restartování bude ladicí program pozastaven na příkaz `assert`, protože výraz `users[i].firstname != null` vyhodnocen jako `false` namísto `true`.

![Vyhodnocení překládá na hodnotu false](../debugger/media/write-better-code-using-assert.png)

Při `assert` chybě se dozvíte, že došlo k problému, který je třeba prozkoumat. `assert` může pokrývat mnoho scénářů, kde se nemusí nutně zobrazovat výjimka. V tomto příkladu se uživateli nezobrazí výjimka a hodnota `null` se přidá jako `firstname` v seznamu záznamů. Může to způsobit potíže později (například se zobrazí ve výstupu konzoly) a může být obtížnější, chcete-li ladit.

> [!NOTE]
> Ve scénářích, kde zavoláte metodu `null` hodnoty, `NullReferenceException` výsledky. Obvykle se chcete vyhnout použití `try/catch`ho bloku pro obecnou výjimku, tedy výjimku, která není vázána na konkrétní funkci knihovny. Libovolný objekt může vyvolat `NullReferenceException`. Pokud si nejste jisti, naleznete v dokumentaci k funkci knihovny.

Během procesu ladění je vhodné zachovat konkrétní příkaz `assert`, dokud nevíte, že ho nebudete muset nahradit skutečnou opravou kódu. Řekněme, že se že rozhodnete, že uživatel může dojít k výjimce v sestavení pro vydání aplikace. V takovém případě musíte Refaktorovat kód, abyste měli jistotu, že vaše aplikace nebude závažnou výjimku nebo mít za následek některých chyb. Ano tento kód opravit, nahraďte následující kód:

```csharp
if (existingUser == false)
{
    User user = new User();
```

s tímto kódem:

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

Pomocí tohoto kódu splníte požadavky na kód a zajistěte, aby se do dat nepřidal záznam s `firstname` nebo `lastname` hodnota `null`.

V tomto příkladu jsme přidali dva příkazy `assert` do smyčky. Obvykle je při použití `assert`nejvhodnější přidat `assert` příkazy na vstupním bodu (začátek) funkce nebo metody. V tuto chvíli se v ukázkové aplikaci díváte na metodu `UpdateRecords`. V této metodě víte, že máte potíže, pokud je `null`některý z argumentů metody, takže je můžete zaškrtnout jak pomocí příkazu `assert` v vstupním bodě funkce.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

Pro předchozí příkazy je vaším záměrem načíst existující data (`db`) a načíst nová data (`users`) před aktualizací cokoli.

`assert` můžete použít s jakýmkoli druhem výrazu, který se překládá na `true` nebo `false`. Takže můžete například přidat příkaz `assert` podobný tomuto.

```csharp
Debug.Assert(users[0].points > 0);
```

Předchozí kód je užitečné, pokud chcete zadat následující záměr: Nová hodnota bodu větší než nula (0) je potřeba aktualizovat record uživatele.

## <a name="inspect-your-code-in-the-debugger"></a>Kontrola kódu v ladicím programu

Tak dobře teď, když jsme opravili kritické vše, co je problém s ukázkovou aplikací, můžete přejít na další důležité věci!

Jsme vám ukázali, pomocníka výjimky ladicího programu ladicí program je však mnohem výkonnější nástroj, který také vám umožňuje dělat jiné věci jako krokovat kód a kontrolovat své proměnné. Tyto možnosti výkonnější jsou užitečné v případech, zejména následující:

* Chcete izolovat chyby modulu runtime ve vašem kódu, ale nemůžou to udělat pomocí metod a nástroje, které dřív popsané.

* Budete chtít ověřit váš kód, který je, můžete si přehrát při spuštění na Ujistěte se, že se chová způsobem, jakým očekáváte a to, co chcete, aby.

    Je poučné jak váš kód při spuštění. Další informace o váš kód tímto způsobem a lze často určit chyby v dříve, než se manifest jakékoli zřejmé příznaky.

Informace o tom, jak používat základní funkce ladicího programu, najdete v tématu [ladění pro absolutní začátečníky](../debugger/debugging-absolute-beginners.md).

## <a name="fix-performance-issues"></a>Řešení problémů s výkonem

Chyby jiného druhu zahrnují neefektivní kód, který způsobí, že vaše aplikace běží pomalu nebo používá příliš mnoho paměti. Obecně platí optimalizace výkonu je něco, co můžete udělat později v vývoje aplikací. Však můžete spustit do problémy s výkonem již v rané fázi (například vidíte, že některá část aplikace běží pomalu), a možná budete muset raném stádiu testováním aplikace s nástroji pro profilaci. Další informace o nástrojích pro profilaci, jako je nástroj využití CPU a analyzátor paměti, najdete v tématu [první pohled na nástroje pro profilaci](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Další kroky

V tomto článku jste zjistili, jak se vyhnout a opravte mnoho běžných chyb v kódu a kdy použít ladicí program. V dalším kroku Další informace o opravě problémů pomocí ladicího programu sady Visual Studio.

> [!div class="nextstepaction"]
> [Ladění pro absolutní začátečníky](../debugger/debugging-absolute-beginners.md)
