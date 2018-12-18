---
title: 'Kurz: Služba Azure Functions'
description: Pomocí Azure functions v sadě Visual Studio pro Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 38FD2070-5151-482E-B0A9-993715128736
ms.openlocfilehash: d6a0683405340d479fb3289540ffde2c5e7a4f78
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296434"
---
# <a name="tutorial-getting-started-with-azure-functions"></a>Kurz: Začínáme s Azure Functions

V tomto testovacím prostředí budete zjistěte, jak začít vytvářet funkce Azure pomocí sady Visual Studio pro Mac. Budete také integrovat tabulky v úložišti Azure, které představují jeden z mnoha typů vazeb a aktivačních událostí, které jsou k dispozici pro vývojáře Azure Functions.

## <a name="objectives"></a>Cíle

> [!div class="checklist"]
> * Vytvářet a ladit místní Azure Functions
> * Integrace s web a prostředků úložiště Azure storage
> * Řídit tok zahrnující více funkcí Azure

## <a name="requirements"></a>Požadavky

- Visual Studio pro Mac 7.5 a novější.
- Předplatné Azure (k dispozici bez [ https://azure.com/free ](https://azure.com/free)).

## <a name="exercise-1-creating-an-azure-functions-project"></a>Cvičení 1: Vytvoření projektu Azure Functions

1. Spuštění **Visual Studio for Mac**.

2. Vyberte **soubor > Nový řešení**.

3. Z **Cloud > Obecné** kategorii, vyberte **Azure Functions** šablony. Použijete C# k vytvoření knihovny tříd .NET, který je hostitelem Azure Functions. Klikněte na tlačítko **Další**.

    ![Výběr šablony Azure functions](media/azure-functions-lab-image1.png)

4. Nastavte **název projektu** k **"AzureFunctionsLab"** a klikněte na tlačítko **vytvořit**.

    ![pojmenování a vytvoření projektu funkce azure functions](media/azure-functions-lab-image2.png)

5. Rozbalte uzly v **oblasti řešení**. Výchozí šablona projektu zahrnuje NuGet odkazy na celou řadu balíčky Azure WebJobs, jakož i balíček Newtonsoft.Json.

     Jsou také tři soubory:- **host.json** pro popis globální možnosti konfigurace pro hostitele - **local.settings.json** ke konfiguraci nastavení služby.
        - Šablona projektu také vytvoří výchozí HttpTrigger. Pro účely tohoto testovacího prostředí, měli byste odstranit **HttpTrigger.cs** soubor z projektu.

    Otevřít **local.settings.json**. Použije se výchozí s tím, že dvě nastavení prázdný připojovacího řetězce.

    ![zobrazení souboru local.settings.json řešení panel](media/azure-functions-lab-image3.png)

## <a name="exercise-2-creating-an-azure-storage-account"></a>Cvičení 2: Vytvoření účtu služby Azure storage

1. Přihlaste se k účtu Azure na [ https://portal.azure.com ](https://portal.azure.com).

1. V části **Oblíbené** části se nachází na levé straně obrazovky vyberte **účty úložiště**:

    ![sekce Oblíbené položky účty úložiště Azure Portalu zobrazující](media/azure-functions-lab-image4.png)

1. Vyberte **přidat** k vytvoření nového účtu úložiště:

    ![Tlačítko pro přidání nového účtu úložiště](media/azure-functions-lab-image5.png)

1. Zadejte globálně jedinečný název pro **název** a znovu ji použít **skupiny prostředků**. Všechny ostatní položky můžete ponechat jako výchozí.

    ![Podrobnosti o novém účtu úložiště](media/azure-functions-lab-image6.png)

1. Klikněte na tlačítko **vytvořit**. Může trvat několik minut pro vytvoření účtu úložiště. Jakmile byla úspěšně vytvořena, dostanete oznámení.

    ![oznámení o úspěchu nasazení](media/azure-functions-lab-image7.png)

1. Vyberte **přejít k prostředku** tlačítko oznámení.

1. Vyberte **přístupové klíče** kartu.

    ![nastavení přístupového klíče](media/azure-functions-lab-image8.png)

1. Zkopírujte první **připojovací řetězec**. Tento řetězec se používá k integraci služby Azure storage s využitím Azure Functions později.

    ![informace pro klíč 1](media/azure-functions-lab-image9.png)

1. Vraťte se na **Visual Studio for Mac** a vložte úplný připojovací řetězec jako **AzureWebJobsStorage** nastavení **local.settings.json**. Teď můžete odkazovat na název nastavení v atributech pro funkce, které potřebují přístup k jeho prostředkům.

    ![Nastavení místní soubor s zadaný klíč připojení](media/azure-functions-lab-image10.png)

## <a name="example-3-creating-and-debugging-an-azure-function"></a>Příklad 3: Vytváření a ladění funkce Azure functions

1. Nyní jste připraveni začít přidávat nějaký kód. Při práci s knihovnou tříd rozhraní .NET, Azure Functions jsou přidány jako statické metody. Z **oblasti řešení**, klikněte pravým tlačítkem myši **AzureFunctions** uzel projektu a vyberte **Přidat > přidat funkci**:

    ![Přidat možnost – Funkce](media/azure-functions-lab-image11.png)

1. V dialogovém okně Nová funkce Azure vyberte šablonu obecným webhookem. Nastavte **název** k **přidat** a klikněte na tlačítko **Ok** k vytvoření funkce:

    ![Dialogové okno Nová služba azure functions](media/azure-functions-lab-image12.png)

1. V horní části stránky nový soubor, přidejte **pomocí** direktivy níže:

    ```csharp
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using System.Web;
    using Microsoft.WindowsAzure.Storage.Table;
    ```
1. Odeberte existující `Run` metoda a přidejte metodu pod třídu jako funkce Azure:

    ```csharp
    [FunctionName("Add")]
    public static int Run(
    [HttpTrigger(AuthorizationLevel.Function, "get", Route = null)]
    HttpRequestMessage req,
    TraceWriter log)
    {
        int x = 1;
        int y = 2;

        return x + y;
    }
    ```
1. Projděme si definici metody jeden po druhém.

    První věc, kterou uvidíte je **FunctionName** atribut, který označí tuto metodu jako funkce Azure functions. Atribut označí veřejného názvu funkce. Název nemusí odpovídat názvu skutečné metoda.

    ![Nové spuštění metodu s atributem FunctionName zvýrazněnou](media/azure-functions-lab-image13.png)

1. V dalším kroku metoda je označena jako **veřejných statických** metodu, která je povinný. Uvidíte také, že vrácená hodnota je **int**. Pokud není stanoveno jinak pomocí atributy metody, libovolný typ jiný než void návratová hodnota funkce Azure se vrátí do klienta jako text. Ve výchozím nastavení se vrátí jako **XML**, můžete ji však změnit na **JSON**, které můžete udělat později v testovacím prostředí.

    ![Nové spuštění metody se zvýrazněnou inicializace – metoda](media/azure-functions-lab-image14.png)

1. První parametr je označen **HttpTrigger** atribut, který označuje, že tato metoda vyvolá požadavek HTTP. Úroveň autorizace metodu, jakož i příkazy podporuje také určuje tento atribut (pouze **"GET"** v tomto případě). Také v případě potřeby můžete definovat **trasy** , která přepíše cestu k metodě a nabízí způsob, jak automaticky extrahovat proměnné z cesty. Protože **trasy** má hodnotu null, bude jako výchozí cestu k této metodě **/api/přidat**.

    ![Nové spuštění metody s parametrem zvýrazněnou](media/azure-functions-lab-image15.png)

1. Poslední parametr metody **TraceWriter** , který slouží k protokolování zpráv pro diagnostiku a chyby.

    ![Nové spuštění metody s TraceWriter zvýrazněnou](media/azure-functions-lab-image16.png)

1. Nastavit zarážku na **vrátit** řádek metody kliknutím u okraje řádku:

    ![Zarážka nastavila na návratové řádku](media/azure-functions-lab-image17.png)

1. Sestavení a spuštění projektu během relace ladění stisknutím kombinace kláves **F5** nebo jeho výběru **spuštění > Spustit ladění**. Můžete také kliknout **spustit** tlačítko. Všechny tyto možnosti provádějí stejné úkoly. Zbývající část tohoto testovacího prostředí se odkazuje **F5**, ale můžete použít metodu vás nejpohodlnější.

    ![Sestavení a spuštění projektu](media/azure-functions-lab-image18.png)

1. Spuštění projektu se automaticky otevře terminálu aplikace.

1. Projekt prochází proces zjišťování Azure Functions na základě atributů metoda a soubor konvence, které se věnujeme dále v tomto článku. V takovém případě zjistí jedné funkce Azure functions a "generuje" 1 pracovní funkci.

    ![Výstupní funkci Azure, v terminálu](media/azure-functions-lab-image19.png)

1. V dolní části zprávy při spuštění Azure Functions hostitele vytiskne adresy URL libovolný trigger HTTP rozhraní API. By měla existovat pouze jeden. Zkopírujte tuto adresu URL a vložte ho na nové kartě prohlížeče.

    ![Adresa URL rozhraní API funkce Azure](media/azure-functions-lab-image20.png)

1. Zarážka by měly aktivovat okamžitě. Webový požadavek prochází funkce a se teď dají ladit. Najedete myší **x** proměnnou můžete zobrazit její hodnotu.

    ![Zarážka spuštěna](media/azure-functions-lab-image21.png)

1. Odebrat narážku použít stejnou metodu používá k přidání dříve (klikněte na okraj nebo vyberte řádku a stiskněte klávesu **F9**).

1. Stisknutím klávesy **F5** dál běžet.

1. V prohlížeči bude vykreslen XML výsledek metody. Podle očekávání, vytvoří operaci sčítání pevně zakódované přesvědčivého součet. Mějte na paměti, pokud se zobrazí jenom "3" v prohlížeči Safari, přejděte k **Safari > Předvolby > Upřesnit** a osové "**nabídky Zobrazit vyvíjet v řádku nabídek**" zaškrtávací políčko a načtěte tuto stránku.

1. V **Visual Studio for Mac**, klikněte na tlačítko **Zastavit** tlačítko pro ukončení relace ladění. Pokud chcete mít jistotu, že se vybírají nových změn, nezapomeňte ladicí relaci restartujte (ukončete a spusťte).

    ![Zastavit ladění – možnost](media/azure-functions-lab-image22.png)

1. V **spustit** metoda, nahraďte **x** a **y** definice s následujícím kódem. Tento kód extrahuje hodnoty z adresy URL řetězec dotazu tak, že lze provést operaci sčítání dynamicky podle zadaných parametrů.

    ```csharp
    var query = HttpUtility.ParseQueryString(req.RequestUri.Query);

    int x = int.Parse(query["x"]);

    int y = int.Parse(query["y"]);

    return x + y;
    ```
1. Spusťte aplikaci.

1. Vraťte se do okna prohlížeče a připojte řetězec `/?x=2&y=3` na adresu URL. Celá adresa URL by měla nyní být `http://localhost:7071/api/Add?x=2&y=3`. Přejděte na novou adresu URL.

1. Tentokrát výsledek by měl odrážet nové parametry. Můžete spustit projekt s různými hodnotami. Všimněte si, že není k dispozici žádné kontroly chyb, neplatné nebo chybějící parametry vyvolá chybu.

1. Zastavte relaci ladění.


## <a name="exercise-4-working-with-functionjson"></a>Cvičení 4: Práce s function.json

1.  V předchozích cvičení jsme zmínili, že Visual Studio for Mac "generována" pracovní funkci pro funkci Azure, které jsou definovány v knihovně. Toto je vzhledem k tomu, že Azure Functions nepoužívá ve skutečnosti atributy metody za běhu, ale místo toho používá konvence systému kompilace souboru Pokud chcete nakonfigurovat umístění, kde a jak se Azure Functions jsou k dispozici. Z **oblasti řešení**klikněte pravým tlačítkem na uzel projektu a vyberte **zobrazit ve Finderu**.

     ![Zobrazit ve Finderu nabídky](media/azure-functions-lab-image23.png)

1. Přejděte dolů v systému souborů, dokud se nedostanete **bin/Debug/netstandard2.0**. Měla by existovat složka s názvem **přidat**. Tato složka byla vytvořena tak, aby odpovídaly s atributem název funkce v kódu jazyka C#. Přidat složku zobrazí jeden **function.json** souboru. Tento soubor používá modul runtime, hostovat a spravovat funkce Azure functions. Pro další jazykové modely bez podpory za kompilace (například skript jazyka C# nebo JavaScript) těchto složek musí ručně vytvořit a udržovat. Pro C# vývojáře vygenerují automaticky z atributu metadat na sestavení. Klikněte pravým tlačítkem na **function.json** a vyberte a otevřete ho v sadě Visual Studio.

    ![v adresáři souboru Function.JSON](media/azure-functions-lab-image24.png)

1. Zadaný předchozích kroků v tomto kurzu, by měl mít základní znalost jazyka C# atributy. Který s ohledem na účtu, tento dokument JSON by měla vypadat povědomě. Existují však několik položek, které nebyly pokryty ve starší cvičení. Například každá **vazby** musí mít jeho **směr** nastavit. Jak můžou odvodit, **"in"** znamená, že je parametr vstup, zatímco **"out"** znamená, že parametr je návratová hodnota (prostřednictvím **$return**) nebo **si** parametr metody. Budete taky muset zadat **Soubor_skriptu** (vzhledem k této konečné umístění) a **entryPoint** – metoda (veřejná a statická) v rámci sestavení. V následujících několik kroků přidáte vlastní funkci cesty pomocí tohoto modelu, tak kopírovat obsah tohoto souboru do schránky.

    ![soubor Function.JSON otevřít v sadě visual studio pro mac](media/azure-functions-lab-image25.png)

1. V **oblasti řešení**, klikněte pravým tlačítkem myši **AzureFunctionsLab** uzel projektu a vyberte **Přidat > Nová složka**. Název nové složky **přidávání**. Výchozí konvencí název této složky budou definovat cesty k rozhraní API, jako **rozhraní api/přidávání**.

    ![Možnost Nová složka](media/azure-functions-lab-image26.png)

1. Klikněte pravým tlačítkem myši **přidávání** a pak zvolte položku **Přidat > Nový soubor**.

    ![Možnost Nový soubor](media/azure-functions-lab-image27.png)

1. Vyberte **webové** kategorie a **prázdný soubor JSON** šablony. Nastavte **název** k **funkce** a klikněte na tlačítko **nový**.

    ![Možnost soubor prázdný objekt json](media/azure-functions-lab-image28.png)

1. Umožňuje vložit obsah jiných **function.json** (z kroku 3) v nahraďte výchozí obsah nově vytvořený soubor.

1. Odeberte tyto řádky z horní části souboru json:

    ```json
    "configurationSource":"attributes",
    "generatedBy":"Microsoft.NET.Sdk.Functions-1.0.13",
    ```

1. Na konci prvního vazby (až **"name": "no"** řádek), přidejte následující vlastnosti. Nezapomeňte zahrnout čárku na předchozí řádek. Tato vlastnost přepíše výchozí kořen tak, aby se nyní extrahovat **int** parametry z cesty a umístí je do parametrů metody, které jsou pojmenovány **x** a **y**.

    ```json
    "direction": "in",
    "route": "Adder/{x:int?}/{y:int?}"
    ```

1. Přidáte jiné vazbě pod první. Tato vazba zpracuje návratovou hodnotu funkce. Nezapomeňte zahrnout čárku na předchozí řádek:

    ```json
    {
    "name": "$return",
    "type": "http",
    "direction": "out"
    }
    ```

1. Také aktualizovat **entryPoint** vlastnost v dolní části souboru, který chcete použít metodu s názvem **"Add2"**, tak jak je znázorněno níže. Toto je pro ilustraci, že cesta **rozhraní api/přidávání...**  namapovat na odpovídající metodu s názvem (**Add2** tady).

    ```json
    "entryPoint": "<project-name>.<function-class-name>.Add2"
    ```

1. Výsledná **function.json** soubor by měl vypadat podobně jako následující kód json:

    ```json
    {
    "bindings": [
        {
        "type": "httpTrigger",
        "methods": [
            "get"
        ],
        "authLevel": "function",
        "direction": "in",
        "name": "req",
        "route": "Adder/{x:int?}/{y:int?}"
        },
        {
        "name": "$return",
        "type": "http",
        "direction": "out"
        }
    ],
    "disabled": false,
    "scriptFile": "../bin/AzureFunctionsProject.dll",
    "entryPoint": "AzureFunctionsProject.Add.Add2"
    }
    ```

1. Jeden poslední krok požadovat, aby to veškerá práce je dáte pokyn, aby Visual Studio for Mac zkopírujte tento soubor do stejné relativní cesty ve výstupním adresáři pokaždé, když se změní. Vybraný soubor, zvolte na kartě Vlastnosti v pravém panelu a pro **kopírovat do výstupního adresáře** vyberte **kopírovat, pokud je novější**:

    ![Vlastnosti možnosti pro soubor json](media/azure-functions-lab-image30.png)

1. V **Add.cs**, nahraďte `Run` – metoda (včetně atributu) pomocí následujících metod ke splnění očekávala se funkce. Je velmi podobný `Run`, s tím rozdílem, že žádné atributy používá a má explicitní parametry pro **x** a **y**.

    ```csharp
    public static int Add2(
        HttpRequestMessage req,
        int x,
        int y,
        TraceWriter log)
    {
        return x + y;
    }
    ```
1. Stisknutím klávesy **F5** sestavte a spusťte projekt.

1. Dokončení sestavení a spuštění platformu, budou teď ukazují, že je k dispozici pro požadavky, které se mapují na nově přidaných metodu Druhá trasa:

    ![Adresa URL pro funkce protokolu Http](media/azure-functions-lab-image31.png)

1. Vrátí okno prohlížeče a přejděte do **http://localhost:7071/api/Adder/3/5**.

1. Znovu, tentokrát metoda funguje, aktivní parametry z cesty a vytváření součet.

1. Vraťte se na **Visual Studio for Mac** a ukončení relace ladění.

## <a name="exercise-5-working-with-azure-storage-tables"></a>Cvičení 5: Práce s tabulkami Azure storage

Služby, které vytváříte často, může být mnohem složitější než co jsme dosud vytvořili a vyžadují značné množství času a/nebo infrastrukturu pro spuštění. V tom případě možná pro vás bude platit tak, aby přijímal požadavky, které jsou zařazeny do fronty pro zpracování, jakmile budou k dispozici prostředky, které Azure Functions poskytuje podporu pro. V jiných případech budete chtít ukládat data centrálně. Tabulky Azure Storage umožňují udělat rychle.

1. Přidat třídu níže **Add.cs**. Má přejít v oboru názvů, ale mimo existující třídy.

    ```csharp
    public class TableRow : TableEntity
    {
        public int X { get; set; }
        public int Y { get; set; }
        public int Sum { get; set; }
    }
    ```
1. V rámci **přidat** třídy, přidejte kód uvedený níže zavést jiné funkci. Upozorňujeme, že tato jedinečná zatím, nezahrnuje odpověď HTTP. Vrátí poslední řádek nový **řádků tabulky** vyplní klíčových informací, které budou usnadňují načíst později (**PartitionKey** a **RowKey**), stejně jako jeho parametry a součet. Kód v metodě také používá **TraceWriter** aby bylo snadnější zjistit, kdy je funkce spuštěná.

    ```csharp
    [FunctionName("Process")]
    [return: Table("Results")]
    public static TableRow Process(
        [HttpTrigger(AuthorizationLevel.Function, "get",
            Route = "Process/{x:int}/{y:int}")]
        HttpRequestMessage req,
        int x,
        int y,
        TraceWriter log)
    {
        log.Info($"Processing {x} + {y}");

        return new TableRow()
        {
            PartitionKey = "sums",
            RowKey = $"{x}_{y}",
            X = x,
            Y = y,
            Sum = x + y
        };
    }
    ```
1. Stisknutím klávesy **F5** sestavte a spusťte projekt.

1. Na záložce prohlížeče, přejděte na **http://localhost:7071/api/Process/4/6**. To další zprávu zařadí do fronty, který by nakonec vést další řádek přidán do tabulky.

1. Vraťte se na **terminálu** a podívejte se na příchozí žádosti pro **4 + 6**.

    ![Žádost o přidání zobrazující terminálu výstupu](media/azure-functions-lab-image32.png)

1. Vraťte se do prohlížeče aktualizovat žádost pro stejnou adresu URL. Tentokrát uvidíte chybu **procesu** metody. Je to proto, že kód se pokouší přidat řádek do tabulky Azure Table Storage pomocí oddílu a řádku kombinace kláves, která již existuje.

    ```
    System.Private.CoreLib: Exception while executing function: Process. Microsoft.Azure.WebJobs.Host: Error while handling parameter $return after function returned:. Microsoft.Azure.WebJobs.Host: The specified entity already exists.
    ```

1. Ukončení relace ladění.

1. Ke zmírnění chyby, přidejte následující parametr k definici metody bezprostředně před **TraceWriter** parametru. Tento parametr nastaví platformy Azure Functions, abychom pokoušejí o načtení **řádků tabulky** z **výsledky** tabulky na **PartitionKey** používáme k ukládání výsledky. Nicméně některé skutečné Kouzlo vstupu do play když zjistíte, že **RowKey** dynamicky generovaná vychází z druhé **x** a **y** parametry stejné Metoda. Pokud tento řádek již existuje, pak **řádků tabulky** budou mít ji, pokud metoda začíná bez další práce potřebné vývojářem. Pokud řádek neexistuje, pak budete mít pouze hodnotu null. Tento druh efektivitu vývojářům dovoluje soustředit na důležité obchodní logiku a ne na infrastrukturu.

    ```csharp
    [Table("Results", "sums", "{x}_{y}")]
    TableRow tableRow,
    ```
1. Na začátek metody přidejte následující kód. Pokud **řádků tabulky** není null, pak jsme již byly výsledky pro požadovanou operaci a může vrátit okamžitě. V opačném případě funkce stejně jako dřív dál. To nemusí být nejrobustnější způsob, jak vrátit data, ukazuje bodu, můžete orchestrovat mimořádně složité operace napříč několika úrovněmi škálovatelné s velmi malým množstvím kódu.

    ```csharp
    if (tableRow != null)
    {
        log.Info($"{x} + {y} already exists");
        return null;
    }
    ```
1. Stisknutím klávesy **F5** sestavte a spusťte projekt.

1. Na záložce prohlížeče, aktualizujte adresu URL na **http://localhost:7071/api/Process/4/6**. Vzhledem k tomu, že řádek tabulky pro tento záznam neexistuje, měla by vrátit okamžitě a bez chyb. Protože neexistuje žádný výstup protokolu HTTP, zobrazí se výstup, v terminálu.

    ![Existuje terminálu výstup už zobrazuje řádek tabulky](media/azure-functions-lab-image33.png)

1. Aktualizace adresy URL tak, aby odrážely kombinaci není dosud neotestovali, jako například **http://localhost:7071/api/Process/5/7**. Všimněte si zpráv, v terminálu, což znamená, že řádek tabulky nebyl nalezen (podle očekávání).

    ![Terminálu výstup zobrazuje nový proces](media/azure-functions-lab-image34.png)

1. Vraťte se na **Visual Studio for Mac** a ukončení relace ladění.

<!--
1. Finally, let's take a look at what it's like to work with multiple input records. Rather than specify a specific **TableRow**, you can request an **IQueryable<TableRow>** using the same attributes, and the runtime will fill it with the appropriate resource you need. Add the code below to create a **List** function that lists all items that currently exist in the Azure table we've been working with. Also note that we're specifying that the MIME type of the response is **application/json**, so the runtime will automatically render as JSON.

    ```csharp
    [FunctionName("List")]
    public static HttpResponseMessage List(
        [HttpTrigger(AuthorizationLevel.Function, "get", Route = null)]
        HttpRequestMessage req,
        [Table("Results", "sums")]
        IQueryable<TableRow> table,
        TraceWriter log)
    {
        return req.CreateResponse(HttpStatusCode.OK, table, "application/json");
    }
    ```
1. Press **F5** to build and run the project.

1. In the browser tab, navigate to **http://localhost:7071/api/List**. This should pull down the list of all items in the Azure table and render it as JSON.

    ![](https://user-images.githubusercontent.com/3944468/29033725-be9d5a5e-7b4a-11e7-8b55-df0a200b6320.png)
-->

## <a name="summary"></a>Souhrn

V tomto testovacím prostředí jste zjistili, jak začít sestavovat Azure Functions pomocí sady Visual Studio pro Mac.

