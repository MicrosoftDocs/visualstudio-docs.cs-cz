---
title: Techniky ladění a související nástroje
description: Pomocí sady Visual Studio můžete napsat lepší kód s méně chybami, aby se opravily výjimky, opravili chyby a vylepšili váš kód.
ms.custom:
- debug-experiment
- seodec18
ms.date: 01/24/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b1fe0a9bb1e966bd1451bb5d816eaab814071fb5
ms.sourcegitcommit: 7825d4163e52d724e59f6c0da209af5fbef673f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72000172"
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

1. Otevřete Visual Studio a vyberte **soubor** > **Nový** **projekt** > . V části **Visual C#** , zvolte **Windows Desktop** nebo **.NET Core**a potom v prostředním podokně vyberte **konzolovou aplikaci**.

    > [!NOTE]
    > Pokud se nezobrazí **konzolovou aplikaci** šablony projektu, klikněte na tlačítko **otevřít instalační program Visual Studio** odkaz v levém podokně **nový projekt** dialogové okno. Spustí se instalační program pro Visual Studio. Zvolte **vývoj desktopových aplikací .NET** nebo **vývoj pro různé platformy .NET Core** úloh, klikněte na tlačítko **změnit**.

2. Do pole **název** zadejte **Console_Parse_JSON** a klikněte na **OK**. Visual Studio vytvoří projekt.

3. Nahraďte výchozí kód v souboru *program.cs* projektu následujícím ukázkovým kódem.

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

Předtím, než se pokusíte spustit ukázkovou aplikaci a spustit ladicí program, zkontrolujte kód v editoru kódu pro červenou a zelenou vlnovkou. Představují chyby a upozornění, které jsou označeny analyzátor kódu rozhraní IDE. Červenou vlnovkou jsou chyby při kompilaci, která je nutné opravit před spuštěním kódu. Zelenou vlnovkou se upozornění. I když často moci spustit vaši aplikaci bez opravy problémů upozornění, je možné příčiny chyb a můžete často ušetřit čas a potíže s zjišťováním je. Tato upozornění a chyby zobrazí také v **seznam chyb** okno, pokud chcete zobrazit seznam.

V ukázkové aplikaci zobrazí se několik červenou vlnovkou, které je potřeba opravit a jednoho zelené, který budete podíváte na. Zde je první chyba.

![Chyba zobrazuje jako červená vlnovka](../debugger/media/write-better-code-red-squiggle.png)

Pokud chcete tuto chybu opravit, budete prohlédněte Další funkcí IDE, reprezentované ikonou žárovky.

## <a name="check-the-light-bulb"></a>Podívejte se, žárovky.

První červená vlnovka představuje chybu v době kompilace. Najeďte myší nad ním a zobrazí se zpráva ```The name `Encoding` does not exist in the current context```.

Všimněte si, že tato chyba zobrazuje ikonou žárovky do levé dolní části. Spolu s ikonu šroubovák ![šroubovák ikonu](../ide/media/screwdriver-icon.png), ikonou žárovky ![ikonou žárovky](../ide/media/light-bulb-icon.png) představuje rychlé akce, které vám pomohou opravit nebo Refaktorujte kód vložený. Představuje žárovky problémy, které *by měl* opravit. Šroubovák se na problémy, které je možné opravit. Použít první navrhované opravy pro vyřešení této chyby kliknutím **pomocí System.Text** na levé straně.

![Oprava kódu pomocí žárovky](../debugger/media/write-better-code-missing-include.png)

Po kliknutí na tuto položku, sada Visual Studio přidá `using System.Text` příkazu v horní části *Program.cs* souboru a červená vlnovka zmizí. (Pokud si nejste jistí, jakou navrhované opravy funkci, zvolte **náhled změn** odkaz na pravé straně před použitím opravy.)

Předchozí chybu je běžné, která obvykle opravit tak, že přidáte nový `using` příkaz do vašeho kódu. Existuje několik běžných podobných chyb, například ```The type or namespace `Name` cannot be found.``` tyto druhy chyb mohou označovat chybějící odkaz na sestavení (klikněte pravým tlačítkem myši na projekt, vyberte možnost **Přidat** **odkaz** > ), nesprávně napsaný název nebo chybějící knihovna, kterou potřebujete. Chcete-li přidat C#(pro, klikněte pravým tlačítkem myši na projekt a vyberte možnost **Spravovat balíčky NuGet**).

## <a name="fix-the-remaining-errors-and-warnings"></a>Oprava zbývajících chyb a upozornění

Existuje několik další podtržení vlnovkou podívat se na tento kód. Tady vidíte běžné Chyba převodu typu. Když najedete myší vlnovka, uvidíte, že se kód pokouší o převedení řetězce na typ int, což není podporováno, není-li přidat explicitní kódu k provedení převodu.

![Chyba převodu typu](../debugger/media/write-better-code-conversion-error.png)

Vzhledem k tomu, že nástroj code analyzer nelze odhadl váš záměr, nejsou žádné návrhy, které vám pomůžou této doby. Chcete-li vyřešit tuto chybu, je potřeba vědět záměru kódu. V tomto příkladu není příliš obtížné zjistit, která `points` by měl být číselné (integer) hodnotu, protože se snažíte přidat `points` k `totalpoints`.

Chcete-li tuto chybu vyřešit, změňte `points` člena `User` třídy z tohoto:

```csharp
[DataMember]
internal string points;
```

K tomuto:

```csharp
[DataMember]
internal int points;
```

Červená vlnovka řádků v editoru kódu zmizet.

Dále umístěte ukazatel myši na zelenou vlnovku v deklaraci datového členu `points`. Analyzátor kódu zjistíte, že proměnná nikdy přiřazena hodnota.

![Upozornění pro Nepřiřazené proměnnou](../debugger/media/write-better-code-warning-message.png)

Obvykle to představuje problém, který je potřeba opravit. Ale v ukázkové aplikaci ve skutečnosti ukládáte data do `points` proměnné během procesu serializace a následným přidáním tuto hodnotu `totalpoints` datový člen. V tomto příkladu vědět záměru kódu a můžete upozornění ignorovat. Pokud chcete odstranit toto upozornění, ale můžete nahradit následující kód:

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

Stisknutím klávesy **F5** (**ladit > Spustit ladění**) nebo **spustit ladění** tlačítko ![spustit ladění](../debugger/media/dbg-tour-start-debugging.png "spustit ladění ") na panelu nástrojů ladění.

V tomto okamžiku vyvolá ukázkovou aplikaci `SerializationException` výjimce (Chyba za běhu). To znamená, že aplikace potlačuje na data, která se pokouší serializovat. Protože jste aplikaci spustili v režimu ladění (ladicí program se připojil), pomocníka výjimky ladicího programu přejdete přímo na kód, který vyvolal výjimku a poskytuje užitečné chybovou zprávu.

![Vyvolá SerializationException](../debugger/media/write-better-code-serialization-exception.png)

Dává pokyn chybová zpráva, která hodnota `4o` nelze analyzovat jako celé číslo. Proto v tomto příkladu víte, data je chybný: `4o` by měl být `40`. Nicméně pokud nepoužíváte kontrolu nad daty v reálné scénáře (například získávají z webové služby), co můžete dělat o něm? Jak to můžete vyřešit?

Až se dostanete k výjimce, potřebujete (a odpovědí) několik otázek:

* Tato výjimka je právě chybu, která můžete opravit? nebo,

* Je tato výjimka něco, co vaši uživatelé setkat?

Pokud je první, opravte chyby. (V ukázkové aplikaci, která znamená, že oprava chybná data.) Pokud je to druhá, může být nutné zpracovat výjimku v kódu pomocí bloku `try/catch` (v další části se podíváme na další možné strategie). V ukázkové aplikaci nahraďte následujícím kódem:

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

A `try/catch` blok má některé náklady na výkon, proto je pouze pro jejich použití když ve skutečnosti je budete potřebovat, to znamená, pokud (a), může dojít k ve vydané verzi aplikace a tam, kde (b) v dokumentaci pro metodu označuje, že by měla vyhledávat došlo k výjimce (za předpokladu, že v dokumentaci k dokončení!). V mnoha případech je odpovídajícím způsobem zpracovat výjimku a uživatel nepotřebuje vědět o něm.

Tady je několik důležitých tipů pro zpracování výjimek:

* Vyhněte se použití prázdný blok catch, jako je třeba `catch (Exception) {}`, které nepřijímá odpovídající akci chcete vystavit nebo zpracování chyb. Blok catch prázdný nebo informativní můžete skrýt výjimky a může ztížit váš kód ladit místo snazší.

* Použití `try/catch` bloku kolem konkrétní funkce, která vyvolá výjimku (`ReadObject`, v ukázkové aplikaci). Když ho používáte kolem větší blok kódu, skončíte skrytí umístění chyby. Například nepoužívejte `try/catch` blok po volání funkce nadřazené `ReadToObject`, je vidět tady, nebo vy nepoznáte, ve kterém k výjimce přesně došlo.

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

Ukázkovou aplikaci, opravte `SerializationException` v `GetJsonData` metodu tak, že změníte `4o` k `40`.

## <a name="clarify-your-code-intent-by-using-assert"></a>Upřesněte svůj záměr váš kód s využitím assert

Klikněte na tlačítko **restartovat** ![restartovat aplikaci](../debugger/media/dbg-tour-restart.png "RestartApp") tlačítko na panelu nástrojů ladění (**Ctrl** + **Shift**   +  **F5**). Tím se znovu spustí aplikaci v méně kroků. Zobrazí se následující výstup v okně konzoly.

![Hodnotu Null ve výstupu](../debugger/media/write-better-code-using-assert-null-output.png)

Můžete zobrazit něco tento výstup, který není úplně vpravo. **název** a **lastname** třetí záznamu jsou prázdné.

Toto je vhodná doba mluvit o užitečné způsobem kódování, často nevyužité, který je určený `assert` příkazy ve vašich funkcí. Přidáním následujícího kódu zahrnete kontrolu za běhu programu, abyste měli jistotu, že `firstname` a `lastname` nejsou `null`. Nahraďte následující kód `UpdateRecords` metody:

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

Přidáním `assert` příkazy takto vašich funkcí během procesu vývoje, vám může pomoct určit záměr kódu. V předchozím příkladu jsme zadejte následující informace:

* Platný řetězec pro se vyžaduje jméno
* Platný řetězec pro se vyžaduje příjmení

Zadáním záměr tímto způsobem vynutit vašim požadavkům. Toto je jednoduchý a užitečný metodu, která vám pomůže surface chyb během vývoje. (`assert` příkazy slouží také jako hlavní prvek při testech jednotek.)

Klikněte na tlačítko **restartovat** ![restartovat aplikaci](../debugger/media/dbg-tour-restart.png "RestartApp") tlačítko na panelu nástrojů ladění (**Ctrl** + **Shift**   +  **F5**).

> [!NOTE]
> `assert` Kódu je aktivní jenom v sestavení pro ladění.

Po restartování, ladicí program pozastaví na `assert` příkaz, protože výraz `users[i].firstname != null` vyhodnotí jako `false` místo `true`.

![Vyhodnocení překládá na hodnotu false](../debugger/media/write-better-code-using-assert.png)

`assert` Chyby se říká, že dojde k nějakému problému, které potřebujete k prozkoumání. `assert` můžete pokrývají množství scénářů, ve kterém se nutně výjimku. V tomto příkladu uživatel neuvidí výjimku a `null` přidá hodnotu jako `firstname` v seznamu záznamů. Může to způsobit potíže později (například se zobrazí ve výstupu konzoly) a může být obtížnější, chcete-li ladit.

> [!NOTE]
> V situacích, kdy zavoláte metodu na `null` hodnotu, `NullReferenceException` výsledky. Obvykle chcete se vyhnout použití `try/catch` bloku pro obecné výjimky, to znamená, výjimku, která se neváže na konkrétní knihovnu funkce. Libovolný objekt může vyvolat `NullReferenceException`. Pokud si nejste jisti, naleznete v dokumentaci k funkci knihovny.

Během procesu ladění, je vhodné zachovat konkrétní `assert` příkaz, dokud nebude vědět, budete muset nahraďte skutečný kód opravy. Řekněme, že se že rozhodnete, že uživatel může dojít k výjimce v sestavení pro vydání aplikace. V takovém případě musíte Refaktorovat kód, abyste měli jistotu, že vaše aplikace nebude závažnou výjimku nebo mít za následek některých chyb. Ano tento kód opravit, nahraďte následující kód:

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

Pomocí tohoto kódu splnění požadavků na kód a ujistěte se, že záznam s `firstname` nebo `lastname` hodnotu `null` není přidaná k datům.

V tomto příkladu jsme přidali dvě `assert` příkazy uvnitř smyčka. Obvykle při použití `assert`, je vhodné přidat `assert` příkazy ve vstupním bodu (od), funkce nebo metody. Aktuálně sledujete `UpdateRecords` metoda v ukázkové aplikaci. V této metodě znáte, jste v potíže, pokud platí některá z argumentů metody `null`, proto zkontrolujte jejich obě `assert` příkazu na vstupní bod funkce.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

Předchozí příkazy vaším záměrem je, že můžete načíst existující data (`db`) a načítání nových dat (`users`) před aktualizací cokoli.

Můžete použít `assert` s jakýmkoli výraz, který se přeloží na `true` nebo `false`. Takže například můžete přidat `assert` příkaz následujícím způsobem.

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

Naučte se používat základní funkce ladicího programu, najdete v článku [ladění pro naprosté začátečníky](../debugger/debugging-absolute-beginners.md).

## <a name="fix-performance-issues"></a>Řešení problémů s výkonem

Chyby jiného druhu zahrnují neefektivní kód, který způsobí, že vaše aplikace běží pomalu nebo používá příliš mnoho paměti. Obecně platí optimalizace výkonu je něco, co můžete udělat později v vývoje aplikací. Však můžete spustit do problémy s výkonem již v rané fázi (například vidíte, že některá část aplikace běží pomalu), a možná budete muset raném stádiu testováním aplikace s nástroji pro profilaci. Další informace o profilování nástroje, jako je nástroj využití CPU a kontejner analyzátoru paměti najdete v tématu [nejdřív se podívejte na nástrojů pro profilaci](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Další kroky

V tomto článku jste zjistili, jak se vyhnout a opravte mnoho běžných chyb v kódu a kdy použít ladicí program. V dalším kroku Další informace o opravě problémů pomocí ladicího programu sady Visual Studio.

> [!div class="nextstepaction"]
> [Ladění pro naprosté začátečníky](../debugger/debugging-absolute-beginners.md)
