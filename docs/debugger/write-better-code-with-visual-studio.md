---
title: Techniky ladění a související nástroje
description: Napište lepší kód s menším početem chyb pomocí sady Visual Studio k opravě výjimek, opravě chyb a vylepšení kódu
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302026"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Ladění techniky a nástroje, které vám pomohou psát lepší kód

Oprava chyb a chyb v kódu může být časově náročná a někdy frustrující úloha. Nějakou dobu trvá, než se naučíte efektivně ladit, ale výkonné ide, jako je Visual Studio, může vaší práci hodně usnadnit. IDE vám může pomoci opravit chyby a ladit kód rychleji, a nejen to, ale může také pomoci napsat lepší kód s menším počtem chyb. Naším cílem v tomto článku je poskytnout vám holistický pohled na proces "oprava chyb", takže budete vědět, kdy použít analyzátor kódu, kdy použít ladicí program, jak opravit výjimky a jak kódovat záměr. Pokud již víte, že potřebujete použít ladicí program, [přečtěte si první pohled na ladicí program](../debugger/debugger-feature-tour.md).

V tomto článku mluvíme o využití ide, aby vaše relace kódování produktivnější. Dotýkáme se několika úkolů, jako jsou:

* Příprava kódu pro ladění využitím analyzátoru kódu ide

* Jak opravit výjimky (chyby za běhu)

* Jak minimalizovat chyby kódováním pro záměr (pomocí assert)

* Kdy použít ladicí program

Chcete-li předvést tyto úkoly, zobrazíme několik nejběžnějších typů chyb a chyb, se kterými se setkáte při pokusu o ladění aplikací. Přestože ukázkový kód je C#, rámcové informace jsou obecně použitelné pro Jazyk C++, Visual Basic, JavaScript a další jazyky podporované visual studio (s výjimkou případů, kdy je uvedeno). Snímky obrazovky jsou v C#.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Vytvoření ukázkové aplikace s některými chybami a chybami

Následující kód má některé chyby, které můžete opravit pomocí ide sady Visual Studio. Aplikace je zde jednoduchá aplikace, která simuluje získání dat JSON z nějaké operace, deserializaci dat na objekt a aktualizaci jednoduchého seznamu s novými daty.

Vytvoření aplikace:

1. V závislosti na typu aplikace, který chcete vytvořit, musíte mít nainstalovanou visual studio a **vývoj napříč platformami .NET Core** nebo pracovní zátěž **pro vývoj plochy .NET.**

    Pokud jste visual studio ještě nenainstalovali, přejděte na stránku ke stažení sady Visual [Studio](https://visualstudio.microsoft.com/downloads/)a nainstalujte ji zdarma.

    Pokud potřebujete nainstalovat úlohy, ale už máte Visual Studio, klikněte na **nástroje** > **získat nástroje a funkce**. Spustí se instalační program pro Visual Studio. Zvolte **vývoj napříč platformami .NET Core** nebo **úlohu vývoje plochy .NET** a pak zvolte **Změnit**.

1. Otevřete sadu Visual Studio.

    ::: moniker range=">=vs-2019"
    V počátečním okně zvolte **Vytvořit nový projekt**. Do vyhledávacího pole zadejte **konzolu** a pak zvolte **Console App (.NET Core)** nebo **Console App (.NET Framework).** Zvolte **Další**. Zadejte název projektu, **Console_Parse_JSON** a klepněte na **tlačítko Vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **nového** > **projektu**. V levém podokně dialogového okna **Nový projekt** v části **Visual C#** zvolte **Console App**a potom v prostředním podokně zvolte **buď Konzolovou aplikaci (.NET Core)** nebo **Konzolovou aplikaci (.NET Framework).** Zadejte název, **například Console_Parse_JSON** a klepněte na **tlačítko OK**.
    ::: moniker-end

    Pokud nevidíte šablonu projektu **Konzola aplikace (.NET Core)** nebo **Console App (.NET Framework),** přejděte na **nástroje** > **získat nástroje a funkce**, který otevře Instalační službu Sady Visual Studio. Zvolte **vývoj napříč platformami .NET Core** nebo pracovní vytížení **pro vývoj pracovních ploch .NET** a pak zvolte **Změnit**.

    Visual Studio vytvoří projekt konzoly, který se zobrazí v Průzkumníku řešení v pravém podokně.

1. Nahraďte výchozí kód v *Program.cs* souboru projektu ukázkovým kódem níže.

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

## <a name="find-the-red-and-green-squiggles"></a>Najít červené a zelené klikyháky!

Než se pokusíte spustit ukázkovou aplikaci a spustit ladicí program, zkontrolujte kód v editoru kódu pro červené a zelené vlnovky. Ty představují chyby a upozornění, které jsou identifikovány analyzátorem kódu ide. Červené vlnovky jsou chyby v době kompilace, které je nutné opravit před spuštěním kódu. Zelené klikyháky jsou varování. I když můžete často spustit aplikaci bez opravy varování, mohou být zdrojem chyb a často ušetříte čas a potíže tím, že je vyšetřujete. Tato upozornění a chyby se také zobrazí v okně **Seznam chyb,** pokud dáváte přednost zobrazení seznamu.

V ukázkové aplikaci uvidíte několik červených vlnovek, které potřebujete opravit, a jednu zelenou, na kterou se podíváte. Zde je první chyba.

![Při zobrazení jako červené vlnovky došlo k chybě.](../debugger/media/write-better-code-red-squiggle.png)

Chcete-li tuto chybu opravit, podíváte se na jinou funkci rozhraní IDE, která je reprezentována ikonou žárovky.

## <a name="check-the-light-bulb"></a>Zkontrolujte žárovku!

První červená vlnovka představuje chybu v době kompilace. Najeďte nad ním a ```The name `Encoding` does not exist in the current context```uvidíte zprávu .

Všimněte si, že tato chyba zobrazuje ikonu žárovky vlevo dole. Spolu s ikonou ![](../ide/media/screwdriver-icon.png)šroubováku šroubováku ![představuje](../ide/media/light-bulb-icon.png) ikona žárovky ikona žárovky rychlé akce, které vám pomohou opravit nebo refaktorovat kód v řadě. Žárovka představuje problémy, které byste *měli* opravit. Šroubovák je určen pro problémy, které můžete opravit. Pomocí první navrhované opravy tuto chybu vyřešíte kliknutím na **system.text** vlevo.

![Použití žárovky k opravě kódu](../debugger/media/write-better-code-missing-include.png)

Po klepnutí na tuto položku Visual Studio přidá `using System.Text` příkaz v horní části Program.cs souboru a červená vlnovka zmizí. *Program.cs* (Pokud si nejste jisti, co navrhovaná oprava udělá, zvolte před použitím opravy odkaz **Náhled** změn vpravo.)

Předchozí chyba je běžná, kterou obvykle opravíte přidáním nového `using` příkazu do kódu. Existuje několik běžných, podobné chyby, ```The type or namespace `Name` cannot be found.``` jako je například tyto druhy chyb může znamenat chybějící odkaz na sestavení (klikněte pravým tlačítkem myši na projekt, zvolte **Přidat** > **odkaz**), chybně napsaný název nebo chybějící knihovny, které je třeba přidat (pro C#, klikněte pravým tlačítkem myši na projekt a zvolte Spravovat **balíčky NuGet**).

## <a name="fix-the-remaining-errors-and-warnings"></a>Oprava zbývajících chyb a varování

Existuje několik dalších vlnovky se podívat na v tomto kódu. Zde se zobrazí běžná chyba převodu typu. Když najedete na vlnovku, zjistíte, že kód se pokouší převést řetězec na int, který není podporován, pokud nepřidáte explicitní kód pro převod.

![Chyba převodu typu](../debugger/media/write-better-code-conversion-error.png)

Vzhledem k tomu, že analyzátor kódu nemůže uhodnout váš záměr, neexistují žádné žárovky, které by vám tentokrát pomohly. Chcete-li tuto chybu opravit, musíte znát záměr kódu. V tomto příkladu není příliš těžké `points` vidět, že by měla být číselná (celá) `points` `totalpoints`hodnota, protože se pokoušíte přidat do .

Chcete-li tuto chybu `points` opravit, `User` změňte člen třídy z tohoto:

```csharp
[DataMember]
internal string points;
```

měli změnit na:

```csharp
[DataMember]
internal int points;
```

Červené klikaté řádky v editoru kódu zmizí.

Dále najeďte nad zelenou vlnovkou `points` v deklaraci datového člena. Analyzátor kódu vám řekne, že proměnné není nikdy přiřazena hodnota.

![Varovná zpráva pro nepřiřazenou proměnnou](../debugger/media/write-better-code-warning-message.png)

Obvykle to představuje problém, který je třeba opravit. V ukázkové aplikaci však ve skutečnosti ukládáte data do `points` proměnné během procesu deserializace a pak přidáte tuto hodnotu datovému členu. `totalpoints` V tomto příkladu znáte záměr kódu a můžete bezpečně ignorovat upozornění. Pokud však chcete upozornění odstranit, můžete nahradit následující kód:

```csharp
item.totalpoints = users[i].points;
```

tímto kódem:

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

Zelená vlnovka zmizí.

## <a name="fix-an-exception"></a>Oprava výjimky

Když jste opravili všechny červené vlnovky a vyřešili - nebo alespoň zkoumali - všechny zelené vlnovky, jste připraveni spustit ladicí program a spustit aplikaci.

Stiskněte **klávesu F5** (**Ladění > Spuštění ladění)** nebo tlačítko Spustit **ladění** ![Spustit ladění](../debugger/media/dbg-tour-start-debugging.png "Spustit ladění") na panelu nástrojů Ladění.

V tomto okamžiku ukázkové aplikace `SerializationException` vyvolá výjimku (chyba za běhu). To znamená, že aplikace tlumí data, která se pokouší serializovat. Vzhledem k tomu, že jste spustili aplikaci v režimu ladění (připojený ladicí program), pomocník pro výjimky ladicího programu vás přenese přímo na kód, který vyvolal výjimku a poskytuje užitečnou chybovou zprávu.

![Dojde k serializaceException dojde](../debugger/media/write-better-code-serialization-exception.png)

Chybová zpráva vás zobrazí `4o` s pokynem, že hodnotu nelze analyzovat jako celé číslo. Takže v tomto příkladu víte, že `4o` data `40`jsou špatná: měla by být . Pokud však nemáte data pod kontrolou v reálném scénáři (řekněme, že je získáváte z webové služby), co s tím uděláte? Jak to napravíte?

Když narazíte na výjimku, musíte se zeptat (a odpovědět) na několik otázek:

* Je tato výjimka pouze chyba, kterou můžete opravit? Nebo:

* Je tato výjimka něco, co vaši uživatelé mohou setkat?

Pokud je to první, opravte chybu. (V ukázkové aplikaci to znamená opravit chybná data.) Pokud je to druhé, možná budete muset zpracovat výjimku v kódu pomocí `try/catch` bloku (podíváme se na další možné strategie v další části). V ukázkové aplikaci nahraďte následující kód:

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

Blok `try/catch` má určité náklady na výkon, takže je budete chtít použít pouze tehdy, když je opravdu potřebujete, to znamená, kde (a) mohou nastat ve verzi aplikace a kde (b) dokumentace pro metodu znamená, že byste měli zkontrolovat výjimku (za předpokladu, že dokumentace je úplná!). V mnoha případech můžete správně zpracovat výjimku a uživatel o ní nikdy nebude muset vědět.

Zde je několik důležitých tipů pro zpracování výjimek:

* Nepoužívejte prázdný blok catch, například `catch (Exception) {}`, který neprovádí příslušnou akci k odhalení nebo zpracování chyby. Prázdný nebo neinformativní blok catch může skrýt výjimky a může ztížit ladění kódu namísto usnadnění.

* Použijte `try/catch` blok kolem konkrétní funkce, která`ReadObject`vyvolá výjimku ( , v ukázkové aplikaci). Pokud jej použijete kolem větší část kódu, skončíte skrytí umístění chyby. Nepoužívejte například `try/catch` blok kolem volání nadřazené funkce `ReadToObject`, který je zde zobrazen, nebo nebudete přesně vědět, kde došlo k výjimce.

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

* U neznámých funkcí, které do aplikace zahrnete, zejména těch, které interagují s externími daty (například webovým požadavkem), zkontrolujte dokumentaci, abyste zjistili, jaké výjimky bude funkce pravděpodobně vyvolána. To může být důležité informace pro správné zpracování chyb a pro ladění aplikace.

U ukázkové aplikace `SerializationException` upravte `GetJsonData` metodu `4o` `40`změnou na .

## <a name="clarify-your-code-intent-by-using-assert"></a>Vyjasnění záměru kódu pomocí assert

Klepněte na tlačítko **Restartovat** ![aplikaci](../debugger/media/dbg-tour-restart.png "Restartovat aplikaci") na panelu nástrojů Ladění **(Ctrl** + **Shift** + **F5).** Tím se aplikace restartuje v menším počtu kroků. V okně konzoly se zobrazí následující výstup.

![Nulová hodnota ve výstupu](../debugger/media/write-better-code-using-assert-null-output.png)

Můžete vidět něco v tomto výstupu, který není zcela v pořádku. **jméno** a **příjmení** třetího záznamu jsou prázdné!

To je vhodná doba mluvit o užitečné kódování praxe, často `assert` nevyužité, což je použití příkazů ve vašich funkcích. Přidáním následujícího kódu zahrnete runtime `firstname` kontrolu, abyste se ujistili, že a `lastname` nejsou `null`. V metodě `UpdateRecords` nahraďte následující kód:

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

Přidáním `assert` příkazů, jako je tento, do vašich funkcí během procesu vývoje, můžete pomoci určit záměr vašeho kódu. V předchozím příkladu uvádíme následující:

* Pro křestní jméno je vyžadován platný řetězec.
* Pro příjmení je vyžadován platný řetězec.

Zadáním záměru tímto způsobem vynucujete své požadavky. Jedná se o jednoduchou a užitečnou metodu, kterou můžete použít k povrchu chyb během vývoje. (`assert` příkazy se také používají jako hlavní prvek v jednotkových testech.)

Klepněte na tlačítko **Restartovat** ![aplikaci](../debugger/media/dbg-tour-restart.png "Restartovat aplikaci") na panelu nástrojů Ladění **(Ctrl** + **Shift** + **F5).**

> [!NOTE]
> Kód `assert` je aktivní pouze v sestavení ladění.

Při restartování ladicí program pozastaví `assert` na příkaz, `users[i].firstname != null` protože `false` výraz `true`vyhodnotí na místo .

![Assert řeší na false](../debugger/media/write-better-code-using-assert.png)

Chyba `assert` vám řekne, že je problém, který je třeba prozkoumat. `assert`může zahrnovat mnoho scénářů, kde nemusíte nutně vidět výjimku. V tomto příkladu uživatel neuvidí výjimku a `null` hodnota se `firstname` přidá jako v seznamu záznamů. To může způsobit problémy později (například vidíte ve výstupu konzoly) a může být těžší ladit.

> [!NOTE]
> Ve scénářích, kde zavoláte metodu na hodnotu, `null` `NullReferenceException` výsledky. Obvykle se chcete vyhnout `try/catch` použití bloku pro obecnou výjimku, to znamená výjimku, která není vázána na konkrétní funkci knihovny. Libovolný objekt může `NullReferenceException`vyvolat . Pokud si nejste jisti, zkontrolujte dokumentaci k funkci knihovny.

Během procesu ladění je vhodné zachovat konkrétní `assert` příkaz, dokud nebudete vědět, že je třeba jej nahradit skutečnou opravou kódu. Řekněme, že se rozhodnete, že uživatel může dojít k výjimce v sestavení verze aplikace. V takovém případě musíte refaktorovat kód, abyste se ujistili, že vaše aplikace nevyvolá závažnou výjimku nebo nepovede k jiné chybě. Chcete-li tento kód opravit, nahraďte následující kód:

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

Pomocí tohoto kódu splníte požadavky na kód a `firstname` ujistěte se, že záznam s nebo `lastname` hodnotou `null` není přidán do dat.

V tomto příkladu jsme `assert` přidali dva příkazy uvnitř smyčky. Obvykle při použití `assert`je vhodné přidat `assert` příkazy v vstupním bodě (začátku) funkce nebo metody. V současné době se `UpdateRecords` díváte na metodu v ukázkové aplikaci. V této metodě víte, že jste v potížích, pokud je `null`některý `assert` z argumentů metody , proto je zkontrolujte oba s příkazem v vstupním bodě funkce.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

U předchozích příkazů je vaším záměrem načíst existující data`db``users`( ) a načíst nová data ( ) před aktualizací čehokoliv.

Můžete použít `assert` s libovolným výrazem, `true` `false`který se překládá na nebo . Takže například můžete přidat `assert` prohlášení, jako je tento.

```csharp
Debug.Assert(users[0].points > 0);
```

Předchozí kód je užitečný, pokud chcete zadat následující záměr: k aktualizaci záznamu uživatele je vyžadována nová bodová hodnota větší než nula (0).

## <a name="inspect-your-code-in-the-debugger"></a>Kontrola kódu v ladicím programu

OK, teď, když jste opravili vše kritické, co je špatné s ukázkovou aplikací, můžete přejít na další důležité věci!

Ukázali jsme vám pomocníka výjimek ladicího programu, ale ladicí program je mnohem výkonnější nástroj, který vám také umožní dělat jiné věci, jako je krokovat kód a kontrolovat jeho proměnné. Tyto výkonnější funkce jsou užitečné v mnoha scénářích, zejména v následujících následujících případech:

* Pokoušíte se izolovat chybu za běhu v kódu, ale nelze to provést pomocí metod a nástrojů, které byly dříve diskutovány.

* Chcete ověřit kód, to znamená, že sledujte ho při spuštění, abyste se ujistili, že se chová tak, jak očekáváte, a děláte to, co chcete.

    Je poučné sledovat váš kód při jeho spuštění. Můžete se dozvědět více o kódu tímto způsobem a můžete často identifikovat chyby před tím, než projeví všechny zjevné příznaky.

Informace o tom, jak používat základní funkce ladicího programu, naleznete v tématu [Ladění pro úplné začátečníky](../debugger/debugging-absolute-beginners.md).

## <a name="fix-performance-issues"></a>Oprava problémů s výkonem

Chyby jiného druhu zahrnují neefektivní kód, který způsobí, že vaše aplikace běží pomalu nebo používat příliš mnoho paměti. Obecně platí, že optimalizace výkonu je něco, co dělat později ve vývoji aplikací. Můžete však narazit na problémy s výkonem brzy (například zjistíte, že některá část aplikace běží pomalu) a možná budete muset aplikaci otestovat pomocí nástrojů pro profilování v rané fázi. Další informace o nástrojích profilování, jako je například nástroj využití procesoru a analyzátor paměti, naleznete [v tématu První pohled na nástroje profilování](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Další kroky

V tomto článku jste se naučili, jak se vyhnout a opravit mnoho běžných chyb v kódu a kdy použít ladicí program. Další informace o použití ladicího programu sady Visual Studio k opravě chyb.

> [!div class="nextstepaction"]
> [Ladění pro naprosté začátečníky](../debugger/debugging-absolute-beginners.md)
