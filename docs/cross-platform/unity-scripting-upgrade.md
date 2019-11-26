---
title: Pomocí rozhraní .NET 4.x v Unity
author: therealjohn
ms.author: johmil
ms.date: 08/29/2018
ms.topic: conceptual
ms.assetid: E2C9420F-A5D5-4472-9020-2B63FB27A133
ms.technology: vs-unity-tools
ms.workload:
- unity
ms.openlocfilehash: 01363ab1588507f31dc74800c85b159039c9bab6
ms.sourcegitcommit: 9c7d8693108ecd2042a70c04cebe3c44af657baf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74239430"
---
# <a name="using-net-4x-in-unity"></a>Pomocí rozhraní .NET 4.x v Unity

C# a .NET, technologie základní skriptování v Unity, mít nadále dostávat aktualizace, protože Microsoft původně vydal v roce 2002 je. Ale vývojářům Unity nemusí být vědomi nepřetržitý proud nových funkcí jazyka C# a rozhraní .NET Framework. Důvodem je, než Unity 2017.1 Unity pomocí .NET 3.5 ekvivalentní skriptovací modul runtime, chybí let aktualizací.

S vydáním Unity 2017.1 zavedené Unity experimentální verzi jeho skriptovací modul runtime upgradovat na .NET 4.6, C# 6 kompatibilní verzi. V Unity 2018.1 ekvivalentní runtime .NET 4.x je nelze nadále považovat za experimentální při starší rozhraní .NET 3.5 ekvivalentní runtime se teď považuje za starší verze. A verze Unity 2018.3 je Unity projekci to usnadňuje upgradovaný skriptovací modul runtime výchozí výběr a aktualizovat i dál C# 7. Pokud chcete získat další informace a nejnovější aktualizace tohoto plánu, přečtěte si [Blogový příspěvek](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/) v Unity nebo navštivte své [experimentální fórum s náhledy pro skriptování](https://forum.unity.com/forums/experimental-scripting-previews.107/). Do té doby projděte si níže uvedených částech Další informace o nových funkcích, které jsou nyní dostupné s modulem runtime skriptovací .NET 4.x.

## <a name="prerequisites"></a>Požadavky

* [Unity 2017,1 nebo vyšší](https://unity3d.com/) (doporučeno 2018,2)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

## <a name="enabling-the-net-4x-scripting-runtime-in-unity"></a>Povolení skriptovací runtime .NET 4.x v Unity

Pokud chcete povolit skriptování runtime .NET 4.x, proveďte následující kroky:

1. Otevřete PlayerSettings v inspektoru Unity tak, že vyberete **upravit > nastavení projektu > Player**.

1. Pod hlavičkou **Konfigurace** klikněte na rozevírací seznam **verze skriptovacího modulu runtime** a vyberte **ekvivalent .NET 4. x**. Jste vyzváni k restartování Unity.

![Vyberte ekvivalent .NET 4.x](media/vstu_scripting-runtime-version.png)

## <a name="choosing-between-net-4x-and-net-standard-20-profiles"></a>Volba mezi .NET 4.x a profily rozhraní .NET Standard 2.0

Po přepnutí na ekvivalentní skriptovací modul runtime .NET 4. x můžete určit **úroveň kompatibility API** pomocí rozevírací nabídky v PlayerSettings (**Upravit > nastavení projektu > Player**). Existují dvě možnosti:

* **.NET Standard 2,0**. Tento profil se shoduje s [profilem .NET Standard 2,0](https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md) zveřejněným rozhraním .NET Foundation. Unity doporučuje pro nové projekty .NET Standard 2.0. Je menší než .NET 4.x. to je výhodné pro velikosti omezen platforem. Kromě toho Unity zavázal k podpoře tohoto profilu na všech platformách, které podporuje Unity.

* **.NET 4. x**. Tento profil poskytuje přístup k nejnovější rozhraní API .NET 4. Zahrnuje veškerý kód, který je k dispozici v knihovnách tříd rozhraní .NET Framework a podporuje také profily rozhraní .NET Standard 2.0. Profil .NET 4.x použijte, pokud váš projekt vyžaduje část rozhraní API není součástí profilu .NET Standard 2.0. Některé části tohoto rozhraní API, ale nemusí být podporované na všech platformách Unity a.

Další informace o těchto možnostech si můžete přečíst v [příspěvku na blogu](https://blogs.unity3d.com/2018/03/28/updated-scripting-runtime-in-unity-2018-1-what-does-the-future-hold/)v Unity.

### <a name="adding-assembly-references-when-using-the-net-4x-api-compatibility-level"></a>Přidání odkazů na sestavení pomocí .NET 4.x úroveň kompatibility rozhraní Api

Při použití nastavení .NET Standard 2,0 v rozevíracím seznamu **úroveň kompatibility rozhraní API** jsou odkazována a použitelná všechna sestavení v profilu rozhraní API. Ale při použití větší profilu .NET 4.x, některá sestavení, která se dodává s Unity nemají ve výchozím nastavení. Chcete-li použít tato rozhraní API, je třeba ručně přidat odkaz na sestavení. Sestavení Unity se dodává s použitím v adresáři **MonoBleedingEdge/lib/mono** instalace editoru Unity:

![MonoBleedingEdge adresáře](media/vstu_monobleedingedge.png)

Například pokud používáte profil .NET 4. x a chcete použít `HttpClient`, je nutné přidat odkaz na sestavení pro System. NET. http. dll. Bez toho kompilátor bude stěžovat si, že chybí odkaz na sestavení:

![Chybí odkaz na sestavení](media/vstu_missing-reference.png)

Visual Studio obnoví soubory .csproj a .sln pro projekty Unity pokaždé, když máte otevřené. V důsledku toho nelze přidat odkazy na sestavení přímo v sadě Visual Studio, protože budou ztraceny znovu otevřít projekt. Místo toho je nutné použít speciální textový soubor s názvem **MCS. rsp** :

1. Vytvořte nový textový soubor s názvem **MCS. rsp** v adresáři kořenových **assetů** vašeho projektu Unity.

1. Do prvního řádku v prázdném textovém souboru zadejte: `-r:System.Net.Http.dll` a pak soubor uložte. "System.Net.Http.dll" můžete nahradit všechny součástí sestavení, které může být chybějící odkaz.

1. Restartujte Unity editor.

## <a name="taking-advantage-of-net-compatibility"></a>Využití výhod kompatibilitu s rozhraním .NET

Kromě nové funkce C# syntaxe a jazyk, modul .NET runtime skriptovací 4.x Unity uživatelům nabízí přístup k obrovské knihovně .NET balíčky, které nejsou kompatibilní s starší verze skriptovací modul runtime rozhraní .NET 3.5.

### <a name="add-packages-from-nuget-to-a-unity-project"></a>Přidání balíčků z NuGet do projektu Unity

[NuGet](https://www.nuget.org/) je správce balíčků pro .NET. NuGet je integrované do sady Visual Studio. Projekty Unity však vyžaduje speciální postup přidání balíčků NuGet. Je to proto když otevřete projekt v Unity, budou znovu vygenerovány jeho soubory projektu sady Visual Studio, vrácení zpět nezbytné konfigurace. Přidání balíčku z NuGet do vašich projektů Unity postupujte takto:

1. Procházet NuGet najděte kompatibilní balíček, který chcete přidat (.NET Standard 2.0 nebo .NET 4.x). Tento příklad předvádí přidání [JSON.NET](https://www.nuget.org/packages/Newtonsoft.Json/), oblíbeného balíčku pro práci s JSON, pro projekt .NET Standard 2,0.

1. Klikněte na tlačítko **Stáhnout** :

    ![tlačítko pro stažení](media/vstu_nuget-download.png)

1. Vyhledejte stažený soubor a změňte jeho příponu z **. nupkg** na **. zip**.

1. V souboru ZIP přejděte do adresáře **lib/netstandard 2.0** a zkopírujte soubor **Newtonsoft. JSON. dll** .

1. Ve složce Root **assets** vašeho projektu Unity vytvořte novou složku s názvem **pluginy**. Moduly plug-in je název speciální složky v Unity. Další informace najdete v [dokumentaci k Unity](https://docs.unity3d.com/Manual/Plugins.html) .

1. Vložte soubor **Newtonsoft. JSON. dll** do adresáře **modulů plug-in** vašeho projektu Unity.

1. V adresáři **assetů** projektu Unity vytvořte soubor s názvem **Link. XML** a přidejte následující kód XML.  Tím se zajistí, že proces vypuzovacího Unity a bajtového kódu při exportu do platformu endem IL2CPP neodebere potřebná data.  Tento krok je sice specifické pro tuto knihovnu, můžete jej spustit do problémy s dalšími knihovnami, které používají reflexi podobným způsobem.  Další informace najdete v dokumentaci k [Unity](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html) v tomto tématu.

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

Zřetězení řetězců s starší modul runtime rozhraní .NET 3.5, vyžaduje nevhodnou syntaxe. Nyní s modulem runtime .NET 4. x umožňuje funkce [interpolace`$` řetězců](https://docs.microsoft.com/dotnet/csharp/language-reference/tokens/interpolated) vkládat do řetězců výrazy v přímější a čitelné syntaxi:

```csharp
// .NET 3.5
Debug.Log(String.Format("Player health: {0}", Health)); // or
Debug.Log("Player health: " + Health);

// .NET 4.x
Debug.Log($"Player health: {Health}");
```

### <a name="expression-bodied-members"></a>Členové tvoření výrazy

V případě, C# že je k dispozici novější syntaxe v modulu runtime .NET 4. x, mohou [výrazy lambda](https://docs.microsoft.com/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions) nahradit tělo funkcí a vytvořit tak stručnější:

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

[Asynchronní programování](https://docs.microsoft.com/dotnet/csharp/async) umožňuje provádět časově náročné operace, aniž by došlo k tomu, že aplikace přestane reagovat. Tato funkce také umožňuje kódu počkejte na dokončení, než budete pokračovat s kódem, který závisí na výsledky těchto operací časově operací. Je třeba počkat soubor do zatížení nebo na dokončení operace sítě.

V Unity je asynchronní programování obvykle provedeno s [korutinami](https://docs.unity3d.com/Manual/Coroutines.html). Od C# 5 ale upřednostňovaná metoda asynchronního programování při vývoji .NET byla [asynchronním vzorem založeným na úlohách (klepnutím)](https://docs.microsoft.com/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap) pomocí `async` a `await` klíčová slova with [System. Threading. Task](https://docs.microsoft.com/dotnet/api/system.threading.tasks.task). V souhrnu ve `async` funkce můžete `await` dokončení úkolu bez blokování, že zbytek aplikace neblokuje aktualizace:

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

* Asynchronní funkce, které mají být očekávány, by měly mít návratový typ [`Task`](https://docs.microsoft.com/dotnet/api/system.threading.tasks.task) nebo [`Task<TResult>`](https://docs.microsoft.com/dotnet/api/system.threading.tasks.task-1).
* Asynchronní funkce, které vracejí úlohu, by měly mít ke svým názvům připojené příponu **"Async"** . Přípony "Async" pomáhá určit, že funkce by měla vždy ní použít operátor await.
* Pro funkce, které aktivují asynchronní funkce z tradičního synchronního kódu, použijte pouze `async void` návratový typ. Takové funkce nelze sami ní použít operátor await a by neměl mají přípony "Async" v názvu.
* Unity UnitySynchronizationContext používá k zajištění, že asynchronní funkce ve výchozím nastavení spouští na hlavním vlákně. Rozhraní API Unity není přístupná mimo hlavního vlákna.
* Je možné spouštět úlohy na vláknech na pozadí s metodami, jako jsou [`Task.Run`](https://msdn.microsoft.com/library/hh195051.aspx) a [`Task.ConfigureAwait(false)`](https://msdn.microsoft.com/library/system.threading.tasks.task.configureawait.aspx). Tato technika je užitečná pro snižování zátěže nákladný provoz z hlavního vlákna, které zlepšují výkon. Nicméně použití vláken na pozadí může vést k problémům, které je obtížné ladit, jako jsou třeba [Konflikty časování](https://wikipedia.org/wiki/Race_condition).
* Rozhraní API Unity není přístupná mimo hlavního vlákna.
* Úlohy, že se nepodporují použití vlákna na Unity WebGL sestavení.

#### <a name="differences-between-coroutines-and-tap"></a>Rozdíly v korutinách a klepněte na

Existují některé důležité rozdíly mezi korutin a klepněte na tlačítko / async-await:

* Korutiny nemůžou vracet hodnoty, ale `Task<TResult>` můžou.
* Nelze vložit `yield` do příkazu try-catch, což ztěžuje zpracování chyb pomocí korutiny. Try-catch však funguje jedním klepnutím.
* Unity a pomocné rutiny funkce není k dispozici ve třídách, které není odvozen od třídy MonoBehaviour. Klepněte na se skvěle hodí pro asynchronní programování v těchto tříd.
* V tuto chvíli není Unity navrhnout klepněte na složité místo korutin. Profilace je jediný způsob, jak zjistit, konkrétní výsledky jedním z přístupů a druhou pro každého projektu.

> [!NOTE]
> Od Unity 2018,2 není ladění asynchronních metod s body přerušení plně podporováno; [Tato funkce se však očekává v Unity 2018,3](https://twitter.com/jbevain/status/900043560665235456).

### <a name="nameof-operator"></a>operátor nameof

Operátor `nameof` Získá název řetězce proměnné, typu nebo členu. Některé případy, kdy `nameof` jsou užitečné, jsou chyby protokolování a získání názvu řetězce výčtu:

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

[Atributy informace o volajícím](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/caller-information) poskytují informace o volajícím metody. Musíte zadat výchozí hodnotu pro každý parametr, který chcete použít s atributem informace o volajícím:

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

[Použití static](https://docs.microsoft.com/dotnet/csharp/language-reference/keywords/using-static) umožňuje použití statických funkcí bez zadání názvu jeho třídy. S použitím statické, můžete uložit místo a čas, pokud je potřeba použít několik statické funkce ze stejné třídy:

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

Při exportu svoji hru do platformy, jako je iOS, bude používat Unity jeho endem IL2CPP modul "transpiluje" IL pro kód jazyka C++, který je poté zkompilován pomocí nativního kompilátoru cílovou platformu. V tomto scénáři je k dispozici několik funkcí rozhraní .NET, které nejsou podporovány, například části reflexe a použití klíčového slova `dynamic`. Při použití těchto funkcí ve svém vlastním kódu, můžete řídit, můžete jej spustit do problémy pomocí 3. stran knihovny DLL a sady SDK, které nebyly vytvořeny pomocí nástrojů Unity a endem IL2CPP v úvahu. Další informace o tomto tématu najdete v dokumentaci k [omezením skriptování](https://docs.unity3d.com/Manual/ScriptingRestrictions.html) na webu Unity.

Kromě toho jak je uvedeno ve výše uvedeném příkladu Json.NET Unity pokusí odstranit nepoužívané kódu během procesu exportu endem IL2CPP.  Přestože se obvykle nejedná o problém s knihovnami, které používají reflexi, může dojít k náhodnému vystavení vlastností nebo metod, které budou volány za běhu, které nelze určit v době exportu.  Chcete-li tyto problémy vyřešit, přidejte do projektu soubor **Link. XML** , který obsahuje seznam sestavení a oborů názvů pro nespuštění procesu odstranění proti.  Úplné podrobnosti najdete v [dokumentaci k odstraňování kódu v Unity](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html).

## <a name="net-4x-sample-unity-project"></a>.NET 4.x ukázkový projekt v Unity

Ukázka obsahuje příklady několik funkcí .NET 4.x. Můžete si stáhnout projekt nebo zobrazit zdrojový kód na [GitHubu](https://github.com/Microsoft/unity-scripting-upgrade).

## <a name="additional-resources"></a>Další zdroje informací:

* [Blog Unity – vylepšení prostředí pro skriptování v Unity 2018,2](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/)
* [HistorieC#](https://docs.microsoft.com/dotnet/csharp/whats-new/csharp-version-history)
* [Co je nového v C# 6](https://docs.microsoft.com/dotnet/csharp/whats-new/csharp-6)
* [Asynchronní programování v Unity, použití korutiny a klepnutí](https://blogs.msdn.microsoft.com/appconsult/2017/09/01/unity-coroutine-tap)
* [Async-await místo korutin v Unity 2017](http://www.stevevermeulen.com/index.php/2017/09/using-async-await-in-unity3d-2017/)
* [Fórum Unity – experimentální náhledy skriptů](https://forum.unity.com/forums/experimental-scripting-previews.107/)
