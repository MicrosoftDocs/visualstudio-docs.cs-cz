---
title: Používání .NET 4.x v Unity
author: therealjohn
ms.author: johmil
ms.date: 08/29/2018
ms.topic: conceptual
ms.assetid: E2C9420F-A5D5-4472-9020-2B63FB27A133
ms.technology: vs-unity-tools
ms.workload:
- unity
ms.openlocfilehash: 01f604de756ca86e40426a97776f1a1d43b024f1
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916856"
---
# <a name="using-net-4x-in-unity"></a>Používání .NET 4.x v Unity

C# a .NET, technologie základní skriptování v Unity, mít nadále dostávat aktualizace, protože Microsoft původně vydal v roce 2002 je. Ale vývojářům Unity nemusí být vědomi nepřetržitý proud nových funkcí jazyka C# a rozhraní .NET Framework. Důvodem je, než Unity 2017.1 Unity pomocí .NET 3.5 ekvivalentní skriptovací modul runtime, chybí let aktualizací.

S vydáním Unity 2017.1 zavedené Unity experimentální verzi jeho skriptovací modul runtime upgradovat na .NET 4.6, C# 6 kompatibilní verzi. V Unity 2018.1 ekvivalentní runtime .NET 4.x je nelze nadále považovat za experimentální při starší rozhraní .NET 3.5 ekvivalentní runtime se teď považuje za starší verze. A verze Unity 2018.3 je Unity projekci to usnadňuje upgradovaný skriptovací modul runtime výchozí výběr a aktualizovat i dál C# 7. Další informace a nejnovějších aktualizací v rámci tohoto plánu, najdete v Unity a [blogový příspěvek](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/) nebo navštivte jejich [experimentální skriptování náhledy fórum](https://forum.unity.com/forums/experimental-scripting-previews.107/). Do té doby projděte si níže uvedených částech Další informace o nových funkcích, které jsou nyní dostupné s modulem runtime skriptovací .NET 4.x.

## <a name="prerequisites"></a>Požadavky

* [Unity 2017.1 nebo vyšší](https://unity3d.com/) (2018.2 doporučeno)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

## <a name="enabling-the-net-4x-scripting-runtime-in-unity"></a>Povolení skriptovací runtime .NET 4.x v Unity

Pokud chcete povolit skriptování runtime .NET 4.x, proveďte následující kroky:

1. Výběrem otevřete PlayerSettings v Unity inspektoru **Upravit > Nastavení projektu > Player**.

1. V části **konfigurace** záhlaví, klikněte na tlačítko **skriptování verze modulu Runtime** rozevírací seznam a vyberte **.NET 4.x ekvivalent**. Jste vyzváni k restartování Unity.

![Vyberte ekvivalent .NET 4.x](media/vstu_scripting-runtime-version.png)

## <a name="choosing-between-net-4x-and-net-standard-20-profiles"></a>Volba mezi .NET 4.x a profily rozhraní .NET Standard 2.0

Po přepnutí .NET 4.x ekvivalentní skriptovacího modulu runtime, můžete zadat **úroveň kompatibility Api** v rozevírací nabídce PlayerSettings (**Upravit > Nastavení projektu > Player**). Existují dvě možnosti:

* **.NET standard 2.0**. Tento profil odpovídá [profilu .NET Standard 2.0](https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md) publikoval(a) .NET Foundation. Unity doporučuje pro nové projekty .NET Standard 2.0. Je menší než .NET 4.x. to je výhodné pro velikosti omezen platforem. Kromě toho Unity zavázal k podpoře tohoto profilu na všech platformách, které podporuje Unity.

* **.NET 4.x**. Tento profil poskytuje přístup k nejnovější rozhraní API .NET 4. Zahrnuje veškerý kód, který je k dispozici v knihovnách tříd rozhraní .NET Framework a podporuje také profily rozhraní .NET Standard 2.0. Profil .NET 4.x použijte, pokud váš projekt vyžaduje část rozhraní API není součástí profilu .NET Standard 2.0. Některé části tohoto rozhraní API, ale nemusí být podporované na všech platformách Unity a.

Můžete si přečíst další informace o těchto možností v Unity a [blogový příspěvek](https://blogs.unity3d.com/2018/03/28/updated-scripting-runtime-in-unity-2018-1-what-does-the-future-hold/).

### <a name="adding-assembly-references-when-using-the-net-4x-api-compatibility-level"></a>Přidání odkazů na sestavení pomocí .NET 4.x úroveň kompatibility rozhraní Api

Při použití nastavení .NET Standard 2.0 **úroveň kompatibility Api** rozevírací seznam, všechna sestavení v rozhraní API profilu jsou odkazovaná a dá se použít. Ale při použití větší profilu .NET 4.x, některá sestavení, která se dodává s Unity nemají ve výchozím nastavení. Chcete-li použít tato rozhraní API, je třeba ručně přidat odkaz na sestavení. Můžete zobrazit Unity se dodává s v sestavení **MonoBleedingEdge/lib/mono** adresář instalace Unity editoru:

![MonoBleedingEdge adresáře](media/vstu_monobleedingedge.png)

Například, pokud používáte profil .NET 4.x a chcete použít `HttpClient`, je nutné přidat odkaz na sestavení pro System.Net.Http.dll. Bez toho kompilátor bude stěžovat si, že chybí odkaz na sestavení:

![Chybí odkaz na sestavení](media/vstu_missing-reference.png)

Visual Studio obnoví soubory .csproj a .sln pro projekty Unity pokaždé, když máte otevřené. V důsledku toho nelze přidat odkazy na sestavení přímo v sadě Visual Studio, protože budou ztraceny znovu otevřít projekt. Místo toho zvláštní textový soubor s názvem **mcs.rsp** musí použít:

1. Vytvořte nový textový soubor s názvem **mcs.rsp** v kořenovém adresáři projektu Unity **prostředky** adresáře.

1. Na prvním řádku v prázdný textový soubor, zadejte: `-r:System.Net.Http.dll` a pak soubor uložte. "System.Net.Http.dll" můžete nahradit všechny součástí sestavení, které může být chybějící odkaz.

1. Restartujte Unity editor.

## <a name="taking-advantage-of-net-compatibility"></a>Využití výhod kompatibilitu s rozhraním .NET

Kromě nové funkce C# syntaxe a jazyk, modul .NET runtime skriptovací 4.x Unity uživatelům nabízí přístup k obrovské knihovně .NET balíčky, které nejsou kompatibilní s starší verze skriptovací modul runtime rozhraní .NET 3.5.

### <a name="add-packages-from-nuget-to-a-unity-project"></a>Přidání balíčků z NuGet do projektu Unity

[NuGet](https://www.nuget.org/) je Správce balíčků pro .NET. NuGet je integrované do sady Visual Studio. Projekty Unity však vyžaduje speciální postup přidání balíčků NuGet. Je to proto když otevřete projekt v Unity, budou znovu vygenerovány jeho soubory projektu sady Visual Studio, vrácení zpět nezbytné konfigurace. Přidání balíčku z NuGet do vašich projektů Unity postupujte takto:

1. Procházet NuGet najděte kompatibilní balíček, který chcete přidat (.NET Standard 2.0 nebo .NET 4.x). V tomto příkladu bude prokázat přidání [Json.NET](https://www.nuget.org/packages/Newtonsoft.Json/), oblíbeného balíčku pro práci s JSON, do projektu .NET Standard 2.0.

1. Klikněte na tlačítko **Stáhnout** tlačítka:

    ![tlačítko pro stažení](media/vstu_nuget-download.png)

1. Vyhledejte stažený soubor a změňte rozšíření z **.nupkg** k **ZIP**.

1. V souboru zip, přejděte **lib/netstandard2.0** adresáře a zkopírujte **soubor newtonsoft.JSON.dll, který** souboru.

1. V kořenovém adresáři projektu Unity **prostředky** složku, vytvořte novou složku s názvem **moduly plug-in**. Moduly plug-in je název speciální složky v Unity. Zobrazit [dokumentace k Unity](https://docs.unity3d.com/Manual/Plugins.html) Další informace.

1. Vložit **souboru Newtonsoft.Json.dll** souboru ve vašem Unity projektu **moduly plug-in** adresáře.

1. Vytvořte soubor s názvem **link.xml** ve vašem Unity projektu **prostředky** adresáře a přidejte následující kód XML.  Tím se zajistí, že proces vypuzovacího Unity a bajtového kódu při exportu do platformu endem IL2CPP neodebere potřebná data.  Tento krok je sice specifické pro tuto knihovnu, můžete jej spustit do problémy s dalšími knihovnami, které používají reflexi podobným způsobem.  Další informace najdete v tématu [Unity a dokumentace](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html) v tomto tématu.

    ```xml
    <linker>
      <assembly fullname="System.Core">
        <type fullname="System.Linq.Expressions.Interpreter.LightLambda" preserve="all" />
      </assembly>
    </linker>
    ```

Všechno v místě můžete nyní použít balíček Json.NET.

```csharp
using Newtonsoft.Json;
using UnityEngine;

public class JSONTest : MonoBehaviour
{
    class Enemy
    {
        public string Name { get; set; }
        public int AttackDamage { get; set; }
        public int MaxHealth { get; set; }
    }
    private void Start()
    {
        string json = @"{
            'Name': 'Ninja',
            'AttackDamage': '40'
            }";

        var enemy = JsonConvert.DeserializeObject<Enemy>(json);

        Debug.Log($"{enemy.Name} deals {enemy.AttackDamage} damage.");
        // Output:
        // Ninja deals 40 damage.
    }
}
```

Toto je jednoduchý příklad použití knihovny, které nemají žádné závislosti. Spolehněte se na dalších balíčcích NuGet pro balíčky NuGet, by musíte ručně stáhnout tyto závislosti a jejich přidání do projektu stejným způsobem.

## <a name="new-syntax-and-language-features"></a>Nové funkce syntaxe a jazyk

Pomocí aktualizované skriptovací modul runtime poskytuje přístup vývojáře Unity a celou řadu nových funkcí jazyka a syntaxe jazyka C# 6.

### <a name="auto-property-initializers"></a>Inicializátory automatickou vlastnost

V Unity a rozhraní .NET 3.5 skriptovací modul runtime automatickou vlastnost syntaxe usnadňuje k rychlému definování neinicializovaných vlastností, ale má inicializace nestane jinde ve skriptu. S modulem runtime .NET 4.x, je nyní možné inicializovat automatické vlastnosti na jednom řádku:

```csharp
// .NET 3.5
public int Health { get; set; } // Health has to be initialized somewhere else, like Start()

// .NET 4.x
public int Health { get; set; } = 100;
```

### <a name="string-interpolation"></a>Interpolace řetězců

Zřetězení řetězců s starší modul runtime rozhraní .NET 3.5, vyžaduje nevhodnou syntaxe. Teď pomocí modulu runtime .NET 4.x [ `$` interpolace](/dotnet/csharp/language-reference/tokens/interpolated) funkce umožňuje výrazů má být vložen do řetězce v s přímým přístupem a čitelnější syntaxi:

```csharp
// .NET 3.5
Debug.Log(String.Format("Player health: {0}", Health)); // or
Debug.Log("Player health: " + Health);

// .NET 4.x
Debug.Log($"Player health: {Health}");
```

### <a name="expression-bodied-members"></a>Členové tvoření výrazy

Syntaxí novější C# k dispozici v modulu runtime .NET 4.x [výrazy lambda](/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions) můžete nahradit tělo funkce, aby se daly stručnější:

```csharp
// .NET 3.5
private int TakeDamage(int amount)
{
    return Health -= amount;
}

// .NET 4.x
private int TakeDamage(int amount) => Health -= amount;
```

Můžete také použít s výrazem v těle členy ve vlastnosti jen pro čtení:

```csharp
// .NET 4.x
public string PlayerHealthUiText => $"Player health: {Health}";
```

### <a name="task-based-asynchronous-pattern-tap"></a>Asynchronní vzor založený na úlohách (TAP)

[Asynchronní programování](/dotnet/csharp/async) umožňuje časově náročná operace k provedení aniž by vaše aplikace přestane reagovat. Tato funkce také umožňuje kódu počkejte na dokončení, než budete pokračovat s kódem, který závisí na výsledky těchto operací časově operací. Je třeba počkat soubor do zatížení nebo na dokončení operace sítě.

V Unity, se obvykle provádí asynchronní programování s [korutin](https://docs.unity3d.com/Manual/Coroutines.html). Nicméně od C# 5, upřednostňovanou metodou asynchronní programování v .NET development byla [úkolově orientovanou asynchronní vzor (TAP)](/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap) pomocí `async` a `await` klíčová slova, [ System.Threading.Task](/dotnet/api/system.threading.tasks.task). Stručně řečeno v `async` funkce můžete `await` dokončení úkolu bez blokování zbytek aplikace z aktualizace:

```csharp
// Unity coroutine
using UnityEngine;
public class UnityCoroutineExample : MonoBehaviour
{
    private void Start()
    {
        StartCoroutine(WaitOneSecond());
        DoMoreStuff(); // This executes without waiting for WaitOneSecond
    }
    private IEnumerator WaitOneSecond()
    {
        yield return new WaitForSeconds(1.0f);
        Debug.Log("Finished waiting.");
    }
}
```

```csharp
// .NET 4.x async-await
using UnityEngine;
using System.Threading.Tasks;
public class AsyncAwaitExample : MonoBehaviour
{
    private async void Start()
    {
        Debug.Log("Wait.");
        await WaitOneSecondAsync();
        DoMoreStuff(); // Will not execute until WaitOneSecond has completed
    }
    private async Task WaitOneSecondAsync()
    {
        await Task.Delay(TimeSpan.FromSeconds(1));
        Debug.Log("Finished waiting.");
    }
}
```

TAP je komplexní problematika, s drobné rozdíly specifické pro Unity, které vývojáři měli zvážit. V důsledku toho TAP není univerzální náhražkou korutiny v Unity; je však jiný nástroj pro využití. Rozsah této funkce je nad rámec tohoto článku, ale některé obecné osvědčené postupy a tipy, které jsou uvedeny níže.

#### <a name="getting-started-reference-for-tap-with-unity"></a>Získat odkaz na Začínáme pro TAP pomocí Unity

Tyto tipy, pomůže vám začít s klepněte v Unity:

* Asynchronní funkce určené k ní použít operátor await by měla mít návratový typ [ `Task` ](/dotnet/api/system.threading.tasks.task) nebo [ `Task<TResult>` ](/dotnet/api/system.threading.tasks.task-1).
* Asynchronní funkce, které vrátí úkol by měl mít příponu **"Asynchronní"** připojenou k jejich názvy. Přípony "Async" pomáhá určit, že funkce by měla vždy ní použít operátor await.
* Použít pouze `async void` návratový typ pro funkce, které zahajte asynchronních funkcí z tradičních synchronního kódu. Takové funkce nelze sami ní použít operátor await a by neměl mají přípony "Async" v názvu.
* Unity UnitySynchronizationContext používá k zajištění, že asynchronní funkce ve výchozím nastavení spouští na hlavním vlákně. Rozhraní API Unity není přístupná mimo hlavního vlákna.
* Je možné ke spouštění úloh na pozadí podprocesů pomocí metody, jako je [ `Task.Run` ](https://msdn.microsoft.com/library/hh195051.aspx) a [ `Task.ConfigureAwait(false)` ](https://msdn.microsoft.com/library/system.threading.tasks.task.configureawait.aspx). Tato technika je užitečná pro snižování zátěže nákladný provoz z hlavního vlákna, které zlepšují výkon. Nicméně použití vlákna na pozadí může vést k problémům, které je obtížné ladit, jako například [na konflikty časování](https://wikipedia.org/wiki/Race_condition).
* Rozhraní API Unity není přístupná mimo hlavního vlákna.
* Úlohy, že se nepodporují použití vlákna na Unity WebGL sestavení.

#### <a name="differences-between-coroutines-and-tap"></a>Rozdíly v korutinách a klepněte na

Existují některé důležité rozdíly mezi korutin a klepněte na tlačítko / async-await:

* Korutiny nemůže vrátit hodnoty, ale `Task<TResult>` může.
* Nelze vložit `yield` v příkazu try-catch, ztěžuje zpracování chyb u korutin. Try-catch však funguje jedním klepnutím.
* Unity a pomocné rutiny funkce není k dispozici ve třídách, které není odvozen od třídy MonoBehaviour. Klepněte na se skvěle hodí pro asynchronní programování v těchto tříd.
* V tuto chvíli není Unity navrhnout klepněte na složité místo korutin. Profilace je jediný způsob, jak zjistit, konkrétní výsledky jedním z přístupů a druhou pro každého projektu.

> [!NOTE]
> Od verze Unity 2018.2 asynchronní metody s body přerušení není podporováno ladění plně; ale [tato funkce se očekává v Unity 2018.3](https://twitter.com/jbevain/status/900043560665235456).

### <a name="nameof-operator"></a>nameof – operátor

`nameof` Operátor získá název řetězce objektu proměnnou, typ nebo člen. Některé případech, kdy `nameof` se hodí protokolování chyb a získávání názvu řetězec výčtu:

```csharp
// Get the string name of an enum:
enum Difficulty {Easy, Medium, Hard};
private void Start()
{
    Debug.Log(nameof(Difficulty.Easy));
    RecordHighScore("John");
    // Output:
    // Easy
    // playerName
}
// Validate parameter:
private void RecordHighScore(string playerName)
{
    Debug.Log(nameof(playerName));
    if (playerName == null) throw new ArgumentNullException(nameof(playerName));
}
```

### <a name="caller-info-attributes"></a>Atributy informace o volajícím

[Atributy informace o volajícím](/dotnet/csharp/programming-guide/concepts/caller-information) poskytují informace o volajícím metody. Musíte zadat výchozí hodnotu pro každý parametr, který chcete použít s atributem informace o volajícím:

```csharp
private void Start ()
{
    ShowCallerInfo("Something happened.");
}
public void ShowCallerInfo(string message,
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)
{
    Debug.Log($"message: {message}");
    Debug.Log($"member name: {memberName}");
    Debug.Log($"source file path: {sourceFilePath}");
    Debug.Log($"source line number: {sourceLineNumber}");
}
// Output:
// Something happened
// member name: Start
// source file path: D:\Documents\unity-scripting-upgrade\Unity Project\Assets\CallerInfoTest.cs
// source line number: 10
```

### <a name="using-static"></a>Pomocí statické

[Pomocí statické](/dotnet/csharp/language-reference/keywords/using-static) umožňuje použít statistické funkce bez zadávání názvu třídy. S použitím statické, můžete uložit místo a čas, pokud je potřeba použít několik statické funkce ze stejné třídy:

```csharp
// .NET 3.5
using UnityEngine;
public class Example : MonoBehaviour
{
    private void Start ()
    {
        Debug.Log(Mathf.RoundToInt(Mathf.PI));
        // Output:
        // 3
    }
}
```

```csharp
// .NET 4.x
using UnityEngine;
using static UnityEngine.Mathf;
public class UsingStaticExample: MonoBehaviour
{
    private void Start ()
    {
        Debug.Log(RoundToInt(PI));
        // Output:
        // 3
    }
}
```

## <a name="il2cpp-considerations"></a>Důležité informace o endem IL2CPP

Při exportu svoji hru do platformy, jako je iOS, bude používat Unity jeho endem IL2CPP modul "transpiluje" IL pro kód jazyka C++, který je poté zkompilován pomocí nativního kompilátoru cílovou platformu. V tomto scénáři se několik funkcí .NET, které nejsou podporovány, jako je například součástí reflexe a využití `dynamic` – klíčové slovo. Při použití těchto funkcí ve svém vlastním kódu, můžete řídit, můžete jej spustit do problémy pomocí 3. stran knihovny DLL a sady SDK, které nebyly vytvořeny pomocí nástrojů Unity a endem IL2CPP v úvahu. Další informace o tomto tématu najdete v tématu [skriptování omezení](https://docs.unity3d.com/Manual/ScriptingRestrictions.html) dokumentace na webu společnosti Unity.

Kromě toho jak je uvedeno ve výše uvedeném příkladu Json.NET Unity pokusí odstranit nepoužívané kódu během procesu exportu endem IL2CPP.  Přestože se obvykle nejedná o problém s knihovnami, které používají reflexi, může dojít k náhodnému vystavení vlastností nebo metod, které budou volány za běhu, které nelze určit v době exportu.  Chcete-li tyto problémy vyřešit, přidejte **link.xml** soubor pro váš projekt, který obsahuje seznam sestavení a obory názvů a nebudou tedy spuštěny procesu vypuzovacího proti.  Úplné podrobnosti najdete v tématu [Unity a dokumentace na odstranění bajtového kódu](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html).

## <a name="net-4x-sample-unity-project"></a>.NET 4.x ukázkový projekt v Unity

Ukázka obsahuje příklady několik funkcí .NET 4.x. Můžete stáhnout projekt nebo zobrazit zdrojový kód na [Githubu](https://github.com/Microsoft/unity-scripting-upgrade).

## <a name="additional-resources"></a>Další materiály a zdroje informací

* [Blog Unity – vylepšení modulu Runtime v Unity 2018.2 skriptování](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/)
* [Historie jazyka C#](/dotnet/csharp/whats-new/csharp-version-history)
* [Co je nového v jazyce C# 6](/dotnet/csharp/whats-new/csharp-6)
* [Asynchronní programování v Unity, použití pomocné rutiny a klepněte na](https://blogs.msdn.microsoft.com/appconsult/2017/09/01/unity-coroutine-tap)
* [Async-Await namísto Korutiny v Unity 2017](http://www.stevevermeulen.com/index.php/2017/09/using-async-await-in-unity3d-2017/)
* [Fórum Unity - experimentální skriptovací verze Preview](https://forum.unity.com/forums/experimental-scripting-previews.107/)
