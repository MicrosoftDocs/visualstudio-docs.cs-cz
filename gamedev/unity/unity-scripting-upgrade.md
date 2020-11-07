---
title: Používání .NET 4.x v Unity
description: Naučte se používat .NET 4. x v Unity. Povolte modul runtime skriptování .NET 4. x. Využijte výhod kompatibility .NET. Zkontrolujte nové funkce syntaxe a jazyka.
author: therealjohn
ms.author: johmil
ms.date: 08/29/2018
ms.topic: how-to
ms.assetid: E2C9420F-A5D5-4472-9020-2B63FB27A133
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.workload:
- unity
ms.openlocfilehash: 5b7e36d0f0c29e997b4b39506fb27d73ceb45146
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2020
ms.locfileid: "94341587"
---
# <a name="using-net-4x-in-unity"></a>Používání .NET 4.x v Unity

V jazyce C# a .NET mají tyto technologie i nadále k dispozici aktualizace od společnosti Microsoft, které byly původně vydány v 2002. Vývojáři Unity ale nemusí znát stálý proud nových funkcí přidaných do jazyka C# a .NET Framework. To je z toho 2017,1 důvodu, že Unity používá ekvivalentní skriptovací modul runtime .NET 3,5 a chybějící roky aktualizací.

V případě vydání Unity 2017,1 představila Unity experimentální verzi svého skriptovacího modulu runtime upgradovanou na verzi kompatibilní s platformou .NET 4,6 a C# 6. V Unity 2018,1 se ekvivalentní modul runtime .NET 4. x už nepovažuje za experimentální, zatímco starší modul runtime ekvivalentní .NET 3,5 se teď považuje za starší verzi. A s vydáním Unity 2018,3 se Unity přizpůsobuje, aby byl upgradovaný skriptovací modul runtime výchozím výběrem a aby ještě více aktualizoval C# 7. Pokud chcete získat další informace a nejnovější aktualizace tohoto plánu, přečtěte si [Blogový příspěvek](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/) v Unity nebo navštivte své [experimentální fórum s náhledy pro skriptování](https://forum.unity.com/forums/experimental-scripting-previews.107/). Mezitím se podívejte na následující části, kde se dozvíte další informace o nových funkcích, které jsou teď dostupné s modulem runtime skriptování .NET 4. x.

## <a name="prerequisites"></a>Požadavky

* [Unity 2017,1 nebo vyšší](https://unity3d.com/) (doporučeno 2018,2)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

## <a name="enabling-the-net-4x-scripting-runtime-in-unity"></a>Povolení skriptovacího modulu runtime .NET 4. x v Unity

Pokud chcete povolit modul runtime skriptování .NET 4. x, proveďte následující kroky:

1. Otevřete PlayerSettings v inspektoru Unity tak, že vyberete **upravit > nastavení projektu > Player**.

1. Pod hlavičkou **Konfigurace** klikněte na rozevírací seznam **verze skriptovacího modulu runtime** a vyberte **ekvivalent .NET 4. x**. Zobrazí se výzva k restartování Unity.

![Vybrat ekvivalent .NET 4. x](media/vs/vstu-scripting-runtime-version.png)

## <a name="choosing-between-net-4x-and-net-standard-20-profiles"></a>Volba mezi profily .NET 4. x a .NET Standard 2,0

Po přepnutí na ekvivalentní skriptovací modul runtime .NET 4. x můžete určit **úroveň kompatibility API** pomocí rozevírací nabídky v PlayerSettings ( **Upravit > nastavení projektu > Player** ). Existují dvě možnosti:

* **.NET Standard 2,0**. Tento profil se shoduje s [profilem .NET Standard 2,0](https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md) zveřejněným rozhraním .NET Foundation. Unity doporučuje .NET Standard 2,0 pro nové projekty. Je menší než .NET 4. x, což je výhodné pro platformy s omezením velikosti. V Unity se navíc zavázala podporovat tento profil napříč všemi platformami, které podporuje Unity.

* **.NET 4. x**. Tento profil poskytuje přístup k nejnovějšímu rozhraní API .NET 4. Zahrnuje veškerý kód, který je k dispozici v knihovnách tříd .NET Framework a podporuje také profily .NET Standard 2,0. Použijte profil .NET 4. x, pokud váš projekt vyžaduje součást rozhraní API, která není obsažena v profilu .NET Standard 2,0. Některé části tohoto rozhraní API ale nemusí být podporované na všech platformách Unity.

Další informace o těchto možnostech si můžete přečíst v [příspěvku na blogu](https://blogs.unity3d.com/2018/03/28/updated-scripting-runtime-in-unity-2018-1-what-does-the-future-hold/)v Unity.

### <a name="adding-assembly-references-when-using-the-net-4x-api-compatibility-level"></a>Přidávání odkazů na sestavení při použití úrovně kompatibility rozhraní .NET 4. x

Při použití nastavení .NET Standard 2,0 v rozevíracím seznamu **úroveň kompatibility rozhraní API** jsou odkazována a použitelná všechna sestavení v profilu rozhraní API. Pokud však používáte větší profil rozhraní .NET 4. x, některá sestavení, na kterých se Unity dodává, nejsou ve výchozím nastavení odkazována. Chcete-li použít tato rozhraní API, je nutné ručně přidat odkaz na sestavení. Sestavení Unity se dodává s použitím v adresáři **MonoBleedingEdge/lib/mono** instalace editoru Unity:

![Adresář MonoBleedingEdge](media/vs/vstu-monobleedingedge.png)

Například pokud používáte profil .NET 4. x a chcete použít `HttpClient` , je nutné přidat odkaz na sestavení pro System.Net.Http.dll. Bez něj kompilátor bude stěžovateli, že nechybí odkaz na sestavení:

![chybějící odkaz na sestavení](media/vs/vstu-missing-reference.png)

Visual Studio znovu generuje soubory. csproj a. sln pro projekty Unity pokaždé, když jsou otevřené. V důsledku toho nebudete moci přidat odkazy na sestavení přímo v sadě Visual Studio, protože budou po opětovném otevření projektu ztraceny. Místo toho je nutné použít speciální textový soubor s názvem **MCS. rsp** :

1. Vytvořte nový textový soubor s názvem **MCS. rsp** v adresáři kořenových **assetů** vašeho projektu Unity.

1. Do prvního řádku v prázdném textovém souboru zadejte: `-r:System.Net.Http.dll` a uložte soubor. "System.Net.Http.dll" můžete nahradit případným zahrnutým sestavením, které by mohlo chybět odkaz.

1. Restartujte Editor Unity.

## <a name="taking-advantage-of-net-compatibility"></a>Využití výhod kompatibility .NET

Kromě nových funkcí syntaxe a jazyka C# modul runtime skriptování .NET 4. x poskytuje uživatelům Unity přístup k obrovský knihovně balíčků .NET, které nejsou kompatibilní se staršími moduly runtime skriptování .NET 3,5.

### <a name="add-packages-from-nuget-to-a-unity-project"></a>Přidání balíčků z NuGet do projektu Unity

[NuGet](https://www.nuget.org/) je správce balíčků pro .NET. NuGet je integrovaný do sady Visual Studio. Projekty Unity však vyžadují speciální proces pro přidání balíčků NuGet. Důvodem je to, že když otevřete projekt v Unity, jejich soubory projektu sady Visual Studio se znovu vygenerují a zrušením potřebných konfigurací. Chcete-li přidat balíček ze sady NuGet do projektu Unity, postupujte následovně:

1. Procházet NuGet a vyhledat kompatibilní balíček, který chcete přidat (.NET Standard 2,0 nebo .NET 4. x). Tento příklad předvádí přidání [JSON.NET](https://www.nuget.org/packages/Newtonsoft.Json/), oblíbeného balíčku pro práci s JSON, pro projekt .NET Standard 2,0.

1. Klikněte na tlačítko **Stáhnout** :

    ![tlačítko Stáhnout](media/vs/vstu-nuget-download.png)

1. Vyhledejte stažený soubor a změňte jeho příponu z **. nupkg** na **. zip**.

1. V souboru ZIP přejděte do adresáře **lib/netstandard 2.0** a zkopírujte soubor **Newtonsoft.Json.dll** .

1. Ve složce Root **assets** vašeho projektu Unity vytvořte novou složku s názvem **pluginy**. Moduly plug-in jsou speciálním názvem složky v Unity. Další informace najdete v [dokumentaci k Unity](https://docs.unity3d.com/Manual/Plugins.html) .

1. Vložte soubor **Newtonsoft.Json.dll** do adresáře **modulů plug-in** vašeho projektu Unity.

1. V adresáři **assetů** projektu Unity vytvořte soubor s názvem **link.xml** a přidejte následující kód XML.  Tím zajistíte, že proces odstranění kódu Unity při exportování na IL2CPP platformu neodstraní potřebná data.  I když je tento krok specifický pro tuto knihovnu, můžete narazit na problémy s jinými knihovnami, které používají reflexi podobným způsobem.  Další informace najdete v dokumentaci k [Unity](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html) v tomto tématu.

    ```xml
    <linker>
      <assembly fullname="System.Core">
        <type fullname="System.Linq.Expressions.Interpreter.LightLambda" preserve="all" />
      </assembly>
    </linker>
    ```

Díky všechno, co je na místě, teď můžete použít balíček Json.NET.

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

Toto je jednoduchý příklad použití knihovny, která nemá žádné závislosti. Pokud se balíčky NuGet spoléhají na jiné balíčky NuGet, je nutné tyto závislosti stáhnout ručně a přidat je do projektu stejným způsobem.

## <a name="new-syntax-and-language-features"></a>Nové funkce syntaxe a jazyka

Použití aktualizovaného skriptovacího modulu runtime poskytuje vývojářům Unity přístup k jazyku C# 6 a k hostování nových funkcí jazyka a syntaxe.

### <a name="auto-property-initializers"></a>Inicializátory automatických vlastností

V modulu runtime skriptování .NET 3,5 v Unity umožňuje syntaxe automatických vlastností snadno rychle definovat neinicializované vlastnosti, ale inicializace musí probíhat jinde ve vašem skriptu. Nyní s modulem runtime .NET 4. x je možné inicializovat automatické vlastnosti na stejném řádku:

```csharp
// .NET 3.5
public int Health { get; set; } // Health has to be initialized somewhere else, like Start()

// .NET 4.x
public int Health { get; set; } = 100;
```

### <a name="string-interpolation"></a>Interpolace řetězců

Se starším modulem runtime .NET 3,5 vyžaduje zřetězení řetězců nevhodný syntax. Nyní s modulem runtime .NET 4. x umožňuje funkce [ `$` interpolace řetězců](/dotnet/csharp/language-reference/tokens/interpolated) vkládat do řetězců výrazy v přímější a čitelné syntaxi:

```csharp
// .NET 3.5
Debug.Log(String.Format("Player health: {0}", Health)); // or
Debug.Log("Player health: " + Health);

// .NET 4.x
Debug.Log($"Player health: {Health}");
```

### <a name="expression-bodied-members"></a>Členové tvoření výrazy

V případě, že je k dispozici novější syntaxe jazyka C# v modulu runtime .NET 4. x, mohou [výrazy lambda](/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions) nahradit tělo funkcí a vytvořit tak stručnější:

```csharp
// .NET 3.5
private int TakeDamage(int amount)
{
    return Health -= amount;
}

// .NET 4.x
private int TakeDamage(int amount) => Health -= amount;
```

Můžete také použít členy Expression-těle ve vlastnostech jen pro čtení:

```csharp
// .NET 4.x
public string PlayerHealthUiText => $"Player health: {Health}";
```

### <a name="task-based-asynchronous-pattern-tap"></a>Asynchronní vzor založený na úlohách (TAP)

[Asynchronní programování](/dotnet/csharp/async) umožňuje provádět časově náročné operace, aniž by došlo k tomu, že aplikace přestane reagovat. Tato funkce také umožňuje vašemu kódu počkat na dokončení operací, které jsou časově náročné, než budete pokračovat v kódu, který závisí na výsledcích těchto operací. Můžete například počkat na dokončení souboru nebo síťové operace.

V Unity je asynchronní programování obvykle provedeno s [korutinami](https://docs.unity3d.com/Manual/Coroutines.html). Od verze C# 5 však upřednostňovaná metoda asynchronního programování při vývoji v .NET byla [asynchronním vzorem založeným na úlohách (klepnutím)](/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap) pomocí `async` `await` klíčových slov a s parametrem [System. Threading. Task](/dotnet/api/system.threading.tasks.task). V souhrnu ve `async` funkci můžete `await` dokončit úkol bez blokování, že zbytek aplikace neblokuje aktualizace:

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

Klepněte na složitý předmět. vývojáři drobné odlišnosti specifické pro Unity by si měli zvážit. V důsledku toho není v Unity klepněte na univerzální náhradu za korutiny. je však možné využít jiný nástroj. Rozsah této funkce je nad rámec tohoto článku, ale níže jsou uvedeny některé obecné osvědčené postupy a tipy.

#### <a name="getting-started-reference-for-tap-with-unity"></a>Úvodní odkaz na použití s Unity

Tyto tipy vám pomůžou začít s klepnutím v Unity:

* Asynchronní funkce, které mají být očekávány, by měly mít návratový typ [`Task`](/dotnet/api/system.threading.tasks.task) nebo [`Task<TResult>`](/dotnet/api/system.threading.tasks.task-1) .
* Asynchronní funkce, které vracejí úlohu, by měly mít ke svým názvům připojené příponu **"Async"** . Přípona "Async" pomáhá označovat, že by měla být funkce vždy očekávána.
* `async void`Pro funkce, které aktivují asynchronní funkce z tradičního synchronního kódu, použijte pouze návratový typ. Takové funkce se nedají očekávat sami a neměla by mít v názvu "Async" příponu.
* Unity používá UnitySynchronizationContext k zajištění toho, aby se asynchronní funkce spouštěly v hlavním vlákně ve výchozím nastavení. Rozhraní API Unity není přístupné mimo hlavní vlákno.
* Je možné spouštět úlohy na vláknech na pozadí s metodami [`Task.Run`](/dotnet/api/system.threading.tasks.task.run) , jako jsou a [`Task.ConfigureAwait(false)`](/dotnet/api/system.threading.tasks.task.configureawait) . Tato technika je užitečná pro snižování zátěže náročných operací z hlavního vlákna za účelem zvýšení výkonu. Nicméně použití vláken na pozadí může vést k problémům, které je obtížné ladit, jako jsou třeba [Konflikty časování](https://wikipedia.org/wiki/Race_condition).
* Rozhraní API Unity není přístupné mimo hlavní vlákno.
* Úlohy, které používají vlákna, nejsou v WebGL sestaveních Unity podporovány.

#### <a name="differences-between-coroutines-and-tap"></a>Rozdíly mezi korutinami a klepnutím

Existují některé důležité rozdíly mezi korutinami a klepnutím/Async-await:

* Korutiny nemohou vracet hodnoty, ale `Task<TResult>` mohou.
* Nelze vložit `yield` do příkazu try-catch, což ztěžuje zpracování chyb pomocí korutiny. Ale try-catch funguje s klepnutím.
* Funkce korutiny Unity není k dispozici ve třídách, které se neodvozují z MonoBehaviour. Klepněte skvěle na asynchronní programování v těchto třídách.
* V tuto chvíli není Unity navržený jako velkoobchodní náhrada za spolurutiny. Profilace je jediným způsobem, jak zjistit konkrétní výsledky jednoho přístupu oproti druhému pro každý daný projekt.

> [!NOTE]
> Od Unity 2018,2 není ladění asynchronních metod s body přerušení plně podporováno; [Tato funkce se však očekává v Unity 2018,3](https://twitter.com/jbevain/status/900043560665235456).

### <a name="nameof-operator"></a>nameof – operátor

`nameof`Operátor Získá název řetězce proměnné, typu nebo členu. Některé případy `nameof` , kdy je to užitečné, jsou chyby protokolování a získání názvu řetězce výčtu:

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

[Atributy informace o volajícím](/dotnet/csharp/programming-guide/concepts/caller-information) poskytují informace o volajícím metody. Je nutné zadat výchozí hodnotu pro každý parametr, který chcete použít s atributem informace o volajícím:

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

### <a name="using-static"></a>Použití static

[Použití static](/dotnet/csharp/language-reference/keywords/using-static) umožňuje použití statických funkcí bez zadání názvu jeho třídy. Když použijete statickou funkci, můžete ušetřit místo a čas, pokud potřebujete použít několik statických funkcí ze stejné třídy:

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

## <a name="il2cpp-considerations"></a>IL2CPP požadavky

Při exportování hry na platformy, jako je iOS, Unity použije svůj modul IL2CPP k přepracovávání "IL" na kód C++, který se pak zkompiluje pomocí nativního kompilátoru cílové platformy. V tomto scénáři je k dispozici několik funkcí rozhraní .NET, které nejsou podporovány, například části reflexe a použití `dynamic` klíčového slova. I když můžete pomocí těchto funkcí řídit vlastní kód, může dojít k potížím s použitím knihoven DLL a sad SDK třetích stran, které nebyly zapsány v Unity a IL2CPP na vědomí. Další informace o tomto tématu najdete v dokumentaci k [omezením skriptování](https://docs.unity3d.com/Manual/ScriptingRestrictions.html) na webu Unity.

Kromě toho, jak je uvedeno v předchozím příkladu Json.NET, Unity se pokusí vydělit nepoužitý kód během procesu exportu IL2CPP.  Přestože se obvykle nejedná o problém s knihovnami, které používají reflexi, může dojít k náhodnému vystavení vlastností nebo metod, které budou volány za běhu, které nelze určit v době exportu.  Chcete-li tyto problémy vyřešit, přidejte do projektu soubor **link.xml** , který obsahuje seznam sestavení a oborů názvů pro nespuštění procesu odstranění proti.  Úplné podrobnosti najdete v [dokumentaci k odstraňování kódu v Unity](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html).

## <a name="net-4x-sample-unity-project"></a>Ukázkový projekt Unity .NET 4. x

Ukázka obsahuje příklady několika funkcí rozhraní .NET 4. x. Můžete si stáhnout projekt nebo zobrazit zdrojový kód na [GitHubu](https://github.com/Microsoft/unity-scripting-upgrade).

## <a name="additional-resources"></a>Další zdroje informací

* [Blog Unity – vylepšení prostředí pro skriptování v Unity 2018,2](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/)
* [Historie jazyka C #](/dotnet/csharp/whats-new/csharp-version-history)
* [Co je nového v C# 6](/dotnet/csharp/whats-new/csharp-6)
* [Asynchronní programování v Unity, použití korutiny a klepnutí](/archive/blogs/appconsult/unity-coroutine-tap-en-us)
* [Async-await místo korutin v Unity 2017](http://www.stevevermeulen.com/index.php/2017/09/using-async-await-in-unity3d-2017/)
* [Fórum Unity – experimentální náhledy skriptů](https://forum.unity.com/forums/experimental-scripting-previews.107/)