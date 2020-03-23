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
ms.openlocfilehash: 5fb521ff1769f1d742dc1ce67080e98aecb417ad
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75944239"
---
# <a name="using-net-4x-in-unity"></a>Používání .NET 4.x v Unity

C# a .NET, technologie, které jsou základem unity skriptování, nadále dostávat aktualizace od microsoft původně vydala v roce 2002. Ale Unity vývojáři nemusí být vědomi stálý proud nových funkcí přidaných do jazyka C# a .NET Framework. Je to proto, že před Unity 2017.1 Unity používá .NET 3.5 ekvivalentní skriptovací runtime, chybějící roky aktualizací.

S vydáním Unity 2017.1, Unity představil experimentální verzi svého skriptovacího runtime upgradovaného na verzi kompatibilní s rozhraním .NET 4.6, C# 6. V Unity 2018.1 .NET 4.x ekvivalentní runtime již není považován za experimentální, zatímco starší .NET 3.5 ekvivalentní runtime je nyní považován za starší verzi. A s vydáním Unity 2018.3 Unity předpokládá, že upgradovaný skriptovací runtime je výchozí výběr a ještě dále aktualizovat na C# 7. Pro více informací a nejnovější aktualizace na tomto plánu, přečtěte si Unity [blog post](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/) nebo navštivte jejich [experimentální skriptování Náhledy forum](https://forum.unity.com/forums/experimental-scripting-previews.107/). Mezitím se podívejte na níže uvedené části, kde se dozvíte více o nových funkcích, které jsou nyní k dispozici s runtime skriptování .NET 4.x.

## <a name="prerequisites"></a>Požadavky

* [Unity 2017.1 nebo vyšší](https://unity3d.com/) (doporučeno 2018.2)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

## <a name="enabling-the-net-4x-scripting-runtime-in-unity"></a>Povolení runtime skriptování .NET 4.x v jednotě

Chcete-li povolit běhovací hodu skriptování .NET 4.x, postupujte takto:

1. Otevřete PlayerSettings v Inspektoru jednoty výběrem **upravit > nastavení projektu > přehrávač .**

1. Pod nadpisem **Konfigurace** klikněte na rozevírací informace **o verzi za běhu skriptů** a vyberte **možnost .NET 4.x Equivalent**. Budete vyzváni k restartování Unity.

![Vybrat ekvivalent rozhraní .NET 4.x](media/vstu_scripting-runtime-version.png)

## <a name="choosing-between-net-4x-and-net-standard-20-profiles"></a>Výběr mezi profily .NET 4.x a .NET Standard 2.0

Po přepnutí na ekvivalentní skriptovací čas .NET 4.x můžete zadat **úroveň kompatibility rozhraní API** pomocí rozbalovací nabídky v nastavení**přehrávače (Upravit > Nastavení projektu > přehrávač**). Existují dvě možnosti:

* **.NET Standard 2.0**. Tento profil odpovídá [profilu .NET Standard 2.0](https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md) publikovaného nadací .NET Foundation. Unity doporučuje .NET Standard 2.0 pro nové projekty. Je menší než .NET 4.x, což je výhodné pro platformy s omezením velikosti. Kromě toho Unity se zavázala k podpoře tohoto profilu napříč všemi platformami, které podporuje Unity.

* **.NET 4.x**. Tento profil poskytuje přístup k nejnovějšímu rozhraní API .NET 4. Obsahuje veškerý kód, který je k dispozici v knihovnách tříd rozhraní .NET Framework, a podporuje také profily .NET Standard 2.0. Profil .NET 4.x použijte, pokud váš projekt vyžaduje část rozhraní API, která není zahrnuta v profilu .NET Standard 2.0. Některé části tohoto rozhraní API však nemusí být podporovány na všech platformách Unity.

Můžete si přečíst více o těchto možnostech v blogu Unity je [.](https://blogs.unity3d.com/2018/03/28/updated-scripting-runtime-in-unity-2018-1-what-does-the-future-hold/)

### <a name="adding-assembly-references-when-using-the-net-4x-api-compatibility-level"></a>Přidání odkazů na sestavení při použití úrovně kompatibility rozhraní .NET 4.x API

Při použití nastavení .NET Standard 2.0 v rozevíracím **seznamu Úroveň kompatibility rozhraní API** jsou všechna sestavení v profilu rozhraní API odkazována a použitelná. Však při použití větší .NET 4.x profilu, některé sestavení, které unity dodává s nejsou odkazovány ve výchozím nastavení. Chcete-li použít tato api, musíte ručně přidat odkaz na sestavení. Můžete zobrazit sestavení Unity dodává s v **MonoBleedingEdge/lib/mono** instalace editoru Unity:

![Adresář MonoBleedingEdge](media/vstu_monobleedingedge.png)

Pokud například používáte profil .NET 4.x a `HttpClient`chcete jej použít , je nutné přidat odkaz na sestavení pro soubor System.Net.Http.dll. Bez něj bude kompilátor stěžovat, že vám chybí odkaz na sestavení:

![chybějící odkaz na sestavení](media/vstu_missing-reference.png)

Visual Studio regeneruje soubory .csproj a .sln pro projekty Unity při každém jejich otevření. V důsledku toho nelze přidat odkazy na sestavení přímo v sadě Visual Studio, protože budou ztraceny při opětovném otevření projektu. Místo toho musí být použit speciální textový soubor s názvem **mcs.rsp:**

1. Vytvořte nový textový soubor s názvem **mcs.rsp** v adresáři kořenových **datových zdrojů** projektu Unity.

1. Na prvním řádku prázdného textového `-r:System.Net.Http.dll` souboru zadejte: a uložte soubor. Můžete nahradit "System.Net.Http.dll" s všechny zahrnuté sestavení, které může chybět odkaz.

1. Restartujte editor Unity.

## <a name="taking-advantage-of-net-compatibility"></a>Využití kompatibility s rozhraním .NET

Kromě nových syntaxí jazyka C# a jazykových funkcí poskytuje soubor runtime skriptování .NET 4.x uživatelům Unity přístup k obrovské knihovně balíčků .NET, které nejsou kompatibilní se starším systémem skriptování .NET 3.5.

### <a name="add-packages-from-nuget-to-a-unity-project"></a>Přidání balíčků z NuGet do projektu Unity

[NuGet](https://www.nuget.org/) je správce balíčků pro rozhraní .NET. NuGet je integrován do sady Visual Studio. Unity projekty však vyžadují speciální proces pro přidání nuget balíčky. Důvodem je, že při otevření projektu v Unity, jeho soubory projektu sady Visual Studio jsou obnoveny, vrátit zpět nezbytné konfigurace. Chcete-li přidat balíček z NuGet do projektu Unity, postupujte takto:

1. Procházet NuGet vyhledejte kompatibilní balíček, který chcete přidat (.NET Standard 2.0 nebo .NET 4.x). Tento příklad bude demonstrovat přidání [Json.NET](https://www.nuget.org/packages/Newtonsoft.Json/), populární balíček pro práci s JSON, do projektu .NET Standard 2.0.

1. Klikněte na tlačítko **Stáhnout:**

    ![tlačítko stáhnout](media/vstu_nuget-download.png)

1. Vyhledejte stažený soubor a změňte příponu z **.nupkg** na **.zip**.

1. V souboru zip přejděte do adresáře **lib/netstandard2.0** a zkopírujte soubor **Newtonsoft.Json.dll.**

1. Ve složce Root **Assets** projektu Unity vytvořte novou složku s názvem **Pluginy**. Pluginy je zvláštní název složky v Unity. Další informace naleznete v [dokumentaci k unity.](https://docs.unity3d.com/Manual/Plugins.html)

1. Vložte soubor **Newtonsoft.Json.dll** do adresáře **pluginů** projektu Unity.

1. Vytvořte soubor s názvem **link.xml** v adresáři **Assets** projektu Unity a přidejte následující XML.  Tím zajistíte Unity je bytecode odstranění proces neodebere potřebná data při exportu do platformy IL2CPP.  I když tento krok je specifický pro tuto knihovnu, můžete narazit na problémy s jinými knihovnami, které používají reflexe podobným způsobem.  Další informace naleznete [v dokumentech Unity](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html) na toto téma.

    ```xml
    <linker>
      <assembly fullname="System.Core">
        <type fullname="System.Linq.Expressions.Interpreter.LightLambda" preserve="all" />
      </assembly>
    </linker>
    ```

Se vším, co na svém místě, můžete nyní použít Json.NET balíček.

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

Toto je jednoduchý příklad použití knihovny, která nemá žádné závislosti. Když balíčky NuGet spoléhají na jiné balíčky NuGet, budete muset stáhnout tyto závislosti ručně a přidat je do projektu stejným způsobem.

## <a name="new-syntax-and-language-features"></a>Nové funkce syntaxe a jazyka

Pomocí aktualizovaného skriptovacího runtime poskytuje vývojářům Unity přístup k C# 6 a řadu nových jazykových funkcí a syntaxe.

### <a name="auto-property-initializers"></a>Inicializátory automatických vlastností

V unity je .NET 3.5 skriptování runtime, syntaxe automatické vlastnosti usnadňuje rychlé definování neinicializovaných vlastností, ale inicializace musí dojít jinde ve skriptu. Nyní s runtime mat., rozhraní .NET 4.x, je možné inicializovat automatické vlastnosti ve stejném řádku:

```csharp
// .NET 3.5
public int Health { get; set; } // Health has to be initialized somewhere else, like Start()

// .NET 4.x
public int Health { get; set; } = 100;
```

### <a name="string-interpolation"></a>Interpolace řetězců

Se starším runtime mno že .NET 3.5 vyžaduje zřetězení řetězců nepříjemnou syntaxi. Nyní s runtime .NET 4.x umožňuje funkce [ `$` interpolace řetězce](/dotnet/csharp/language-reference/tokens/interpolated) vkládat výrazy do řetězců v přímější a čitelnější syntaxi:

```csharp
// .NET 3.5
Debug.Log(String.Format("Player health: {0}", Health)); // or
Debug.Log("Player health: " + Health);

// .NET 4.x
Debug.Log($"Player health: {Health}");
```

### <a name="expression-bodied-members"></a>Členové tvoření výrazy

S novější syntaxe Jazyka C# k dispozici v běhu .NET 4.x, [lambda výrazy](/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions) mohou nahradit tělo funkcí, aby byly stručnější:

```csharp
// .NET 3.5
private int TakeDamage(int amount)
{
    return Health -= amount;
}

// .NET 4.x
private int TakeDamage(int amount) => Health -= amount;
```

Členy s výrazem můžete také použít ve vlastnostech jen pro čtení:

```csharp
// .NET 4.x
public string PlayerHealthUiText => $"Player health: {Health}";
```

### <a name="task-based-asynchronous-pattern-tap"></a>Asynchronní vzor založený na úlohách (TAP)

[Asynchronní programování](/dotnet/csharp/async) umožňuje časově náročné operace, aniž by došlo k tomu, že vaše aplikace přestane reagovat. Tato funkce také umožňuje kód čekat časově náročné operace dokončit před pokračováním s kódem, který závisí na výsledcích těchto operací. Můžete například počkat na načtení souboru nebo dokončení síťové operace.

V Unity asynchronní programování se obvykle provádí s [korutiny](https://docs.unity3d.com/Manual/Coroutines.html). Nicméně, protože C# 5 upřednostňovanou metodou asynchronního programování ve vývoji rozhraní .NET je [asynchronní vzor založený na úlohách (TAP)](/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap) pomocí klíčových slov `async` a `await` [system.threading.task](/dotnet/api/system.threading.tasks.task). Stručně řečeno, `async` ve funkci `await` můžete dokončení úkolu bez blokování zbytku aplikace z aktualizace:

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

TAP je složité téma, s Unity-specifické nuance vývojáři by měli zvážit. V důsledku toho tap není univerzální náhradou za korutiny v Unity; je to však další nástroj, který lze využít. Rozsah této funkce je nad rámec tohoto článku, ale některé obecné doporučené postupy a tipy jsou uvedeny níže.

#### <a name="getting-started-reference-for-tap-with-unity"></a>Odkaz Začínáme pro TAP s Unity

Tyto tipy vám pomohou začít s tapem v Unity:

* Asynchronní funkce určené k čekání by měly mít návratový typ [`Task`](/dotnet/api/system.threading.tasks.task) nebo [`Task<TResult>`](/dotnet/api/system.threading.tasks.task-1).
* Asynchronní funkce, které vrátí úlohu by měl mít příponu **"Async"** připojené k jejich názvy. Přípona "Async" pomáhá indikovat, že funkce by měla být vždy očekávána.
* Návratový `async void` typ používejte pouze pro funkce, které se ozvou asynchronní funkce z tradičního synchronního kódu. Tyto funkce nemohou být samy o sobě očekávány a neměly by mít příponu "Async" v jejich názvech.
* Unity používá UnitySynchronizationContext k zajištění asynchronní funkce spustit na hlavní vlákno ve výchozím nastavení. Rozhraní API unity není přístupné mimo hlavní vlákno.
* Je možné spouštět úlohy na vláknech na pozadí pomocí metod, jako [`Task.Run`](https://msdn.microsoft.com/library/hh195051.aspx) je a [`Task.ConfigureAwait(false)`](https://msdn.microsoft.com/library/system.threading.tasks.task.configureawait.aspx). Tato technika je užitečná pro snižování zátěže nákladné operace z hlavního vlákna pro zvýšení výkonu. Použití podprocesů na pozadí však může vést k problémům, které je obtížné ladit, jako jsou [například sporné podmínky](https://wikipedia.org/wiki/Race_condition).
* Rozhraní API unity není přístupné mimo hlavní vlákno.
* Úkoly, které používají vlákna nejsou podporovány na Unity WebGL sestavení.

#### <a name="differences-between-coroutines-and-tap"></a>Rozdíly mezi korutinami a TAP

Tam jsou některé důležité rozdíly mezi korutiny a TAP / async-await:

* Korutiny nelze vrátit `Task<TResult>` hodnoty, ale může.
* Nelze umístit `yield` příkaz try-catch, takže zpracování chyb s korutiny. Try-catch však funguje s TAP.
* Funkce korutiny Unity není k dispozici ve třídách, které nejsou odvozeny z MonoBehaviour. TAP je skvělý pro asynchronní programování v těchto třídách.
* V tomto bodě, Unity nenavrhuje TAP jako velkoobchodní náhrada korutin. Profilování je jediný způsob, jak znát konkrétní výsledky jednoho přístupu oproti druhému pro daný projekt.

> [!NOTE]
> Od Unity 2018.2 ladění asynchronních metod s body přerušení není plně podporováno; tato [funkce se však očekává v Unity 2018.3](https://twitter.com/jbevain/status/900043560665235456).

### <a name="nameof-operator"></a>nameof – operátor

Operátor `nameof` získá název řetězce proměnné, typu nebo člena. Některé případy, kdy `nameof` přijde vhod, jsou protokolování chyby a získání názvu řetězce výčtu:

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

### <a name="caller-info-attributes"></a>Atributy informací o volajícím

[Atributy informací o volajícím](/dotnet/csharp/programming-guide/concepts/caller-information) poskytují informace o volajícím metody. Pro každý parametr, který chcete použít s atributem Informace o volajícím, je nutné zadat výchozí hodnotu:

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

### <a name="using-static"></a>Použití statické

[Použití statické](/dotnet/csharp/language-reference/keywords/using-static) umožňuje používat statické funkce bez zadání názvu třídy. Pomocí statické, můžete ušetřit místo a čas, pokud potřebujete použít několik statických funkcí ze stejné třídy:

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

## <a name="il2cpp-considerations"></a>Důležité informace il2CPP

Při exportu vaší hry na platformy, jako je iOS, Unity použije svůj il2cpp modul k "transpile" IL na C++ kód, který je pak kompilován pomocí nativního kompilátoru cílové platformy. V tomto scénáři existuje několik .NET funkce, které nejsou podporovány, `dynamic` jako jsou například části Reflection a použití klíčového slova. Zatímco můžete řídit pomocí těchto funkcí ve vlastním kódu, můžete narazit na problémy pomocí dll třetích stran a sad SDK třetích stran, které nebyly napsány s Unity a IL2CPP v mysli. Další informace o tomto tématu naleznete v dokumentech [omezení skriptování](https://docs.unity3d.com/Manual/ScriptingRestrictions.html) na webu Unity.

Navíc, jak je uvedeno v příkladu Json.NET výše, Unity se pokusí odstranit nepoužívaný kód během procesu exportu IL2CPP.  I když to obvykle není problém, s knihovnami, které používají reflexe, může omylem odstranit vlastnosti nebo metody, které budou volány v době běhu, které nelze určit v době exportu.  Chcete-li tyto problémy vyřešit, přidejte do projektu soubor **link.xml,** který obsahuje seznam sestavení a oborů názvů, proti kterým nelze spustit proces odstraňování.  Podrobné informace naleznete [v dokumentech Unity na odstraňování bajtového kódu](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html).

## <a name="net-4x-sample-unity-project"></a>.NET 4.x Ukázkový projekt Unity

Ukázka obsahuje příklady několika funkcí rozhraní .NET 4.x. Můžete si stáhnout projekt nebo zobrazit zdrojový kód na [GitHubu](https://github.com/Microsoft/unity-scripting-upgrade).

## <a name="additional-resources"></a>Další zdroje

* [Unity Blog - Skriptování vylepšení běhu v Unity 2018.2](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/)
* [Historie C #](/dotnet/csharp/whats-new/csharp-version-history)
* [Co je nového v C# 6](/dotnet/csharp/whats-new/csharp-6)
* [Asynchronní programování v Unity, Použití Coroutine a TAP](/archive/blogs/appconsult/unity-coroutine-tap-en-us)
* [Async-Await Místo corutinv Unity 2017](http://www.stevevermeulen.com/index.php/2017/09/using-async-await-in-unity3d-2017/)
* [Unity Forum - Experimentální skriptování Náhledy](https://forum.unity.com/forums/experimental-scripting-previews.107/)
