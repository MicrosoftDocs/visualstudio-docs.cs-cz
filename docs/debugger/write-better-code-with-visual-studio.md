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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5fd3d8e17d90cde50f583dfc0393debf460de7f6
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2021
ms.locfileid: "101684074"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Techniky a nástroje ladění, které vám pomůžou psát lepší kód

Oprava chyb a chyb v kódu může být časově náročná a někdy frustrujícíá. Se dozvíte, jak efektivně ladit, ale výkonné integrované vývojové prostředí (IDE), jako je Visual Studio, může mít za úkol mnohem jednodušší. Integrované vývojové prostředí (IDE) vám může pomoct opravovat chyby a ladit kód rychleji a nejen to, ale může také pomoct psát lepší kód s méně chybami. Naším cílem v tomto článku je poskytnout holistický zobrazení procesu "opravování chyb", takže budete znát, kdy použít analyzátor kódu, kdy použít ladicí program, jak opravit výjimky a jak provést kód pro záměr. Pokud už víte, že potřebujete použít ladicí program, přečtěte si téma [první pohled na ladicí program](../debugger/debugger-feature-tour.md).

V tomto článku se seznámíme s využitím integrovaného vývojového prostředí (IDE) k zajištění vyšší produktivity vašich relací kódování. Porozumíme vám několik úkolů, například:

* Příprava kódu pro ladění využitím analyzátoru kódu v integrovaném vývojovém prostředí

* Oprava výjimek (běhové chyby)

* Jak minimalizovat chyby pomocí kódování pro záměr (pomocí vyhodnocení)

* Kdy použít ladicí program

Abychom předvedli tyto úkoly, zobrazujeme několik nejběžnějších typů chyb a chyb, ke kterým dojde při pokusu o ladění aplikací. I když je ukázkový kód C#, koncepční informace se obecně vztahují na C++, Visual Basic, JavaScript a další jazyky, které Visual Studio podporuje (s výjimkou případů, kdy se uvádí). Snímky obrazovky jsou v jazyce C#.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Vytvoření ukázkové aplikace s některými chybami a chybami

Následující kód obsahuje některé chyby, které můžete opravit pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio. Tady je jednoduchá aplikace, která simuluje získávání dat JSON z nějaké operace, deserializaci dat do objektu a aktualizaci jednoduchého seznamu s novými daty.

Vytvoření aplikace:

1. Musíte mít nainstalovanou aplikaci Visual Studio a nainstalovanou úlohu **vývoje .NET Core pro různé platformy** .

    Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/) a nainstalujte si ji zdarma.

    Pokud potřebujete nainstalovat úlohu, ale už máte Visual Studio, klikněte na **nástroje**  >  **získat nástroje a funkce**. Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoje .NET Core pro různé platformy** a pak zvolte **změnit**.

1. Otevřete sadu Visual Studio.

    ::: moniker range=">=vs-2019"
    V okně Start vyberte možnost **vytvořit nový projekt**. Do vyhledávacího pole zadejte **Console** a pak zvolte buď **Konzolová aplikace** pro .NET Core. Zvolte **Další**. Zadejte název projektu, například **Console_Parse_JSON** , a klikněte na tlačítko **Další** nebo **vytvořit**, podle toho, jaká možnost je k dispozici.

    V případě .NET Core zvolte Doporučené cílové rozhraní (.NET Core 3,1) nebo .NET 5 a pak zvolte **vytvořit**.

    Pokud nevidíte šablonu projektu **aplikace konzoly** pro .NET Core, přejděte do části **nástroje**  >  **získat nástroje a funkce**, které otevřou instalační program pro Visual Studio. Zvolte úlohu **vývoje .NET Core pro různé platformy** a pak zvolte **změnit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek vyberte **soubor**  >  **Nový**  >  **projekt**. V levém podokně dialogového okna **Nový projekt** , v části **Visual C#** zvolte **Konzolová aplikace** a pak v prostředním podokně zvolte **Konzolová aplikace (.NET Core)**. Zadejte název, například **Console_Parse_JSON** a klikněte na tlačítko **OK**.

    Pokud nevidíte šablonu projektu **Konzolová aplikace (.NET Core)** , přejděte do části **nástroje**  >  **získat nástroje a funkce**, které otevřou instalační program pro Visual Studio. Zvolte úlohu **vývoje .NET Core pro různé platformy** a pak zvolte **změnit**.
    ::: moniker-end

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

## <a name="find-the-red-and-green-squiggles"></a>Najde červené a zelené vlnovky!

Než se pokusíte spustit ukázkovou aplikaci a spustit ladicí program, podívejte se do kódu v editoru kódu pro červené a zelené vlnovky. Tyto představují chyby a upozornění, která jsou identifikována analyzátorem kódu IDE. Červené vlnovky jsou chyby při kompilaci, které je nutné před spuštěním kódu opravit. Zelené vlnovky jsou upozornění. I když aplikaci můžete často spouštět bez opravy upozornění, může se jednat o zdroj chyb a často šetříte čas a problémy tím, že je prozkoumáte. Tato upozornění a chyby se také zobrazí v okně **Seznam chyb** , pokud dáváte přednost zobrazení seznamu.

V ukázkové aplikaci vidíte několik červených vlnovek, které je třeba opravit, a jednu zelenou barvu, kterou si podíváte na. Toto je první chyba.

![Chyba zobrazená jako červená vlnovka](../debugger/media/write-better-code-red-squiggle.png)

Chcete-li tuto chybu opravit, Prohlédněte si jinou funkci integrovaného vývojového prostředí (IDE) reprezentovanou ikonou žárovky.

## <a name="check-the-light-bulb"></a>Podívejte se na žárovku!

První červená vlnovka představuje chybu při kompilaci. Najeďte myší na ni a zobrazí se zpráva ```The name `Encoding` does not exist in the current context``` .

Všimněte si, že tato chyba zobrazuje ikonu žárovky vlevo dole. Společně s ikonou Screwdriver ikony Screwdriver ikona žárovky ikony žárovky ![ ](../ide/media/screwdriver-icon.png) ![ ](../ide/media/light-bulb-icon.png) představuje rychlé akce, které vám pomůžou s opravou nebo refaktorem vloženého kódu. Žárovka představuje problémy, které *byste měli* opravit. Screwdriver je pro problémy, se kterými se můžete rozhodnout opravit. Pokud chcete tuto chybu vyřešit, použijte první navrhovanou opravu, která se zobrazí po kliknutí na tlačítko **použít System. text** na levé straně.

![Odstranění kódu pomocí žárovky](../debugger/media/write-better-code-missing-include.png)

Po kliknutí na tuto položku Visual Studio přidá `using System.Text` příkaz v horní části souboru *program.cs* a červená vlnovka zmizí. (Pokud si nejste jistí, co Navrhovaná oprava udělá, před použitím opravy klikněte na odkaz **Náhled změn** na pravé straně.)

Předchozí chyba je běžně ta, kterou obvykle opravíte přidáním nového `using` příkazu do kódu. Existuje několik běžných podobných chyb, například ```The type or namespace `Name` cannot be found.``` tyto druhy chyb mohou označovat chybějící odkaz na sestavení (klikněte pravým tlačítkem myši na projekt, vyberte možnost **Přidat**  >  **odkaz**), nesprávně napsaný název nebo chybějící knihovnu, kterou potřebujete přidat (pro C# klikněte pravým tlačítkem myši na projekt a vyberte možnost **Spravovat balíčky NuGet**).

## <a name="fix-the-remaining-errors-and-warnings"></a>Oprava zbývajících chyb a upozornění

V tomto kódu se můžete podívat v několika dalších vlnovích. Tady se zobrazí chyba převodu běžného typu. Když najedete myší na vlnovku, uvidíte, že se kód pokouší převést řetězec na int, což není podporováno, pokud pro převod nepřidáte explicitní kód.

![Chyba převodu typu](../debugger/media/write-better-code-conversion-error.png)

Vzhledem k tomu, že analyzátor kódu nemůže odhadnout svůj záměr, nejsou k dispozici žádné žárovky, které by vám pomohly tento čas. Chcete-li tuto chybu opravit, je nutné znát účel kódu. V tomto příkladu není příliš obtížné zjistit, že `points` by měla být číselná (celočíselná) hodnota, protože se pokoušíte přidat `points` do `totalpoints` .

Chcete-li tuto chybu opravit, změňte `points` člena `User` třídy z tohoto:

```csharp
[DataMember]
internal string points;
```

měli změnit na:

```csharp
[DataMember]
internal int points;
```

Červené klikaté čáry v editoru kódu odcházejí.

Dále najeďte na zelenou vlnovku v deklaraci `points` datového členu. Analyzátor kódu oznamuje, že proměnné není nikdy přiřazena hodnota.

![Zpráva upozornění pro nepřiřazenou proměnnou](../debugger/media/write-better-code-warning-message.png)

Obvykle to představuje problém, který je třeba opravit. Nicméně v ukázkové aplikaci, ve které jste ve skutečnosti ukládáte data do `points` proměnné během procesu deserializace a následně přidáte tuto hodnotu `totalpoints` datovému členu. V tomto příkladu znáte záměr kódu a můžete upozornění bezpečně ignorovat. Pokud však chcete upozornění odstranit, můžete nahradit následující kód:

```csharp
item.totalpoints = users[i].points;
```

tímto kódem:

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

Zelená vlnovka zmizí.

## <a name="fix-an-exception"></a>Opravit výjimku

Když jste opravili všechny červené vlnovky a vyřešené, nebo alespoň prošetřené – všechny zelené vlnovky jste připraveni ke spuštění ladicího programu a spuštění aplikace.

Stiskněte klávesu **F5** (**ladění > spustit ladění**) nebo klikněte na tlačítko **Spustit** ladění ![Spustit ladění](../debugger/media/dbg-tour-start-debugging.png "Spustit ladění") na panelu nástrojů ladění.

V tomto okamžiku ukázková aplikace vyvolá `SerializationException` výjimku (Chyba za běhu). To znamená, že se aplikace v datech, která se pokouší serializovat, potlačuje. Vzhledem k tomu, že jste aplikaci spustili v režimu ladění (ladicí program byl připojen), Pomocník pro výjimky ladicího programu převezme přímo do kódu, který výjimku vyvolal, a zobrazí vám pomocnou chybovou zprávu.

![Dojde k SerializationException](../debugger/media/write-better-code-serialization-exception.png)

Chybová zpráva vás instruuje, že hodnotu `4o` nelze analyzovat jako celé číslo. Proto v tomto příkladu víte, že data jsou chybná: `4o` měla by být `40` . Pokud ale neovládáte data ve skutečném scénáři (řekněme, že ho získáváte z webové služby), co s tím uděláte? Jak to opravíte?

Když dojde k výjimce, musíte požádat o několik otázek (a odpovědět na ně):

* Je tato výjimka jenom chyba, kterou můžete opravit? Nebo:

* Je tato výjimka taková, že se uživatelé mohou setkat?

V případě, že je dřívější, opravte chybu. (V ukázkové aplikaci to znamená opravit chybná data.) Pokud je to druhá, může být nutné zpracovat výjimku v kódu pomocí `try/catch` bloku (v další části se podíváme na další možné strategie). V ukázkové aplikaci nahraďte následující kód:

```csharp
users = ser.ReadObject(ms) as User[];
```

tímto kódem:

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

`try/catch`Blok má určité náklady na výkon, takže je budete chtít používat pouze v případě, že je skutečně potřebujete, to znamená, kde (a) mohou nastat ve verzi aplikace a kde (b) dokumentace k metodě označuje, že byste měli vyhledat výjimku (za předpokladu, že je dokumentace dokončena). V mnoha případech můžete zpracovat výjimku odpovídajícím způsobem a uživatel nikdy o něm nebude mít žádné informace.

Zde je několik důležitých tipů pro zpracování výjimek:

* Vyhněte se použití prázdného bloku catch, například `catch (Exception) {}` , který neprovádí odpovídající akci k vystavení nebo zpracování chyby. Prázdný nebo Neinformativní blok catch může skrývat výjimky a může tak ztížit ladění kódu místo jednoduššího ladění.

* Použijte `try/catch` blok kolem konkrétní funkce, která vyvolá výjimku ( `ReadObject` v ukázkové aplikaci). Pokud ji použijete kolem většího bloku kódu, skončíte tím, že se skryje umístění chyby. Například Nepoužívejte `try/catch` blok kolem volání nadřazené funkce, jak je `ReadToObject` znázorněno zde, nebo nevíte přesně, kde k výjimce došlo.

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

* V případě neznámých funkcí, které zahrnete do aplikace, zejména při interakci s externími daty (například webovými požadavky), Projděte si dokumentaci, kde najdete výjimky, které funkce může vyvolat. Může se jednat o důležité informace pro správné zpracování chyb a ladění aplikace.

Pro ukázkovou aplikaci opravte `SerializationException` `GetJsonData` metodu v metodě změnou `4o` na `40` .

## <a name="clarify-your-code-intent-by-using-assert"></a>Vyjasnění záměru kódu pomocí kontrolního výrazu

Klikněte na tlačítko **restartovat** ![aplikaci](../debugger/media/dbg-tour-restart.png "RestartApp") na panelu nástrojů ladění (**CTRL**  +  **SHIFT**  +  **F5**). Tím se aplikace restartuje za méně kroků. V okně konzoly se zobrazí následující výstup.

![Hodnota null ve výstupu](../debugger/media/write-better-code-using-assert-null-output.png)

V tomto výstupu vidíte něco, co není úplně pravé. **jméno** a **příjmení** třetího záznamu je prázdné.

To je dobrý čas na komunikaci s užitečným postupem kódování, který je často nevyužitý, což je použití `assert` příkazů ve vašich funkcích. Přidáním následujícího kódu zahrnete kontrolu za běhu, abyste se ujistili, že `firstname` a `lastname` nejsou `null` . Nahraďte následující kód v `UpdateRecords` metodě:

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

Přidáním `assert` příkazů, jako je to pro vaše funkce během procesu vývoje, můžete přispět k určení záměru kódu. V předchozím příkladu určíme následující:

* Pro křestní jméno je vyžadován platný řetězec.
* Pro příjmení se vyžaduje platný řetězec.

Tím, že zadáte záměr tímto způsobem, vynutili své požadavky. Toto je jednoduchá a praktická metoda, kterou můžete použít k obdoby chyb během vývoje. ( `assert` příkazy se používají také jako hlavní prvek v testování částí.)

Klikněte na tlačítko **restartovat** ![aplikaci](../debugger/media/dbg-tour-restart.png "RestartApp") na panelu nástrojů ladění (**CTRL**  +  **SHIFT**  +  **F5**).

> [!NOTE]
> `assert`Kód je aktivní pouze v sestavení ladění.

Po restartování se ladicí program zastaví na `assert` příkazu, protože výraz se `users[i].firstname != null` vyhodnocuje jako `false` místo `true` .

![Vyhodnocení výrazu se překládá na hodnotu false.](../debugger/media/write-better-code-using-assert.png)

Tato `assert` Chyba oznamuje, že došlo k problému, který je třeba prozkoumat. `assert` může pokrývat mnoho scénářů, ve kterých se nemusí nutně zobrazovat výjimka. V tomto příkladu se uživateli nezobrazí výjimka a v `null` seznamu záznamů se přidá hodnota `firstname` . To může způsobit problémy později (například ve výstupu konzoly) a může být těžší je ladit.

> [!NOTE]
> Ve scénářích, kde zavoláte metodu na `null` hodnotu, `NullReferenceException` výsledek. Obvykle se chcete vyhnout použití `try/catch` bloku pro obecnou výjimku, tedy výjimku, která není vázána na konkrétní funkci knihovny. Libovolný objekt může vyvolat `NullReferenceException` . Pokud si nejste jistí, podívejte se do dokumentace k funkci knihovny.

Během procesu ladění je vhodné zachovat konkrétní `assert` příkaz, dokud nevíte, že ho nebudete muset nahradit skutečnou opravou kódu. Řekněme, že se rozhodnete, že uživatel může zaznamenat výjimku v sestavení verze aplikace. V takovém případě je nutné Refaktorovat kód, aby se zajistilo, že vaše aplikace nevyvolává závažnou výjimku, nebo kvůli nějaké chybě. Chcete-li tento kód opravit, nahraďte následující kód:

```csharp
if (existingUser == false)
{
    User user = new User();
```

tímto kódem:

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

Pomocí tohoto kódu splníte požadavky na kód a zajistěte, aby se `firstname` `lastname` `null` do dat nepřidal záznam s hodnotou nebo.

V tomto příkladu jsme přidali dva `assert` příkazy uvnitř smyčky. Obvykle je při použití `assert` vhodné přidat `assert` příkazy na vstupní bod (začátek) funkce nebo metody. V tuto chvíli se díváte na `UpdateRecords` metodu v ukázkové aplikaci. V této metodě se dozvíte, že máte potíže, pokud je jeden z argumentů metody `null` , takže je můžete zaškrtnout pomocí `assert` příkazu v vstupním bodě funkce.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

V předchozích příkazech je vaším záměrem načíst existující data ( `db` ) a načíst nová data ( `users` ) před aktualizací jakéhokoli.

Můžete použít `assert` s jakýmkoli druhem výrazu, který se překládá na `true` nebo `false` . Například můžete přidat `assert` příkaz podobný tomuto.

```csharp
Debug.Assert(users[0].points > 0);
```

Předchozí kód je užitečný, pokud chcete zadat následující záměr: k aktualizaci záznamu uživatele se vyžaduje nová hodnota bodu větší než nula (0).

## <a name="inspect-your-code-in-the-debugger"></a>Kontrola kódu v ladicím programu

Teď, když jste opravili vše důležité, co je u ukázkové aplikace chybné, můžete přejít na jiné důležité věci.

Zjistili jsme pomocníka s výjimkou ladicího programu, ale ladicí program je mnohem výkonnější nástroj, který také umožňuje provádět další věci, jako je například krokovat kód a kontrolovat jeho proměnné. Tyto výkonnější funkce jsou užitečné v mnoha scénářích, zejména v následujících případech:

* Pokoušíte se izolovat chybu za běhu v kódu, ale nelze ji provést pomocí dříve popsaných metod a nástrojů.

* Chcete ověřit kód, to znamená, že je sledován při jeho spuštění, aby se zajistilo, že se chová podle toho, jak očekáváte a co chcete.

    Při spuštění kódu se dá sledovat. Můžete získat další informace o kódu tímto způsobem a často identifikovat chyby předtím, než budou manifestovat zjevné příznaky.

Informace o tom, jak používat základní funkce ladicího programu, najdete v tématu [ladění pro absolutní začátečníky](../debugger/debugging-absolute-beginners.md).

## <a name="fix-performance-issues"></a>Řešení problémů s výkonem

Chyby jiného druhu zahrnují neefektivní kód, který způsobí, že vaše aplikace běží pomalu nebo má příliš mnoho paměti. Obecně platí, že optimalizace výkonu je něco, co budete dělat později ve vývoji aplikací. K problémům s výkonem ale můžete v brzkém provozu (například vidíte, že některá část aplikace je spuštěná pomalu) a možná budete muset otestovat aplikaci pomocí nástrojů pro profilaci na začátku. Další informace o nástrojích pro profilaci, jako je nástroj využití CPU a analyzátor paměti, najdete v tématu [první pohled na nástroje pro profilaci](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Další kroky

V tomto článku jste se naučili, jak se vyhnout a opravovat mnoho běžných chyb v kódu a kdy použít ladicí program. V dalším kroku se dozvíte další informace o použití ladicího programu sady Visual Studio k opravě chyb.

> [!div class="nextstepaction"]
> [Ladění pro naprosté začátečníky](../debugger/debugging-absolute-beginners.md)
