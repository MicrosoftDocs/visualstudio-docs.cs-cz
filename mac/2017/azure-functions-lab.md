---
title: 'Kurz: Azure Functions'
description: Používání funkcí Azure ve Visual Studiu pro Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 38FD2070-5151-482E-B0A9-993715128736
ms.openlocfilehash: 43720947d36fec1ee64c81a48f7bc3eb7466d034
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983361"
---
# <a name="tutorial-getting-started-with-azure-functions"></a>Kurz: Začínáme s funkcemi Azure

V tomto testovacím prostředí se dozvíte, jak začít vytvářet funkce Azure pomocí Visual Studia pro Mac. Budete také integrovat s tabulkami úložiště Azure, které představují jeden z mnoha druhů vazeb a aktivačních událostí, které jsou k dispozici vývojářům Azure Functions.

## <a name="objectives"></a>Cíle

> [!div class="checklist"]
> * Vytváření a ladění místních funkcí Azure
> * Integrace s webovými a virtuálními úložnými prostředky a prostředky Azure
> * Orchestrace pracovního postupu zahrnujícího více funkcí Azure

## <a name="requirements"></a>Požadavky

- Visual Studio pro Mac 7.5 nebo vyšší.
- Předplatné Azure (dostupné [https://azure.com/free](https://azure.com/free)zdarma).

## <a name="exercise-1-creating-an-azure-functions-project"></a>Cvičení 1: Vytvoření projektu Azure Functions

1. Spusťte **Visual Studio pro Mac**.

2. Vyberte **možnost Soubor > nové řešení**.

3. V kategorii **Cloud > Obecné** vyberte šablonu Azure **Functions.** Pomocí jazyka C# vytvoříte knihovnu tříd .NET, která je hostitelem funkcí Azure. Klikněte na **Další**.

    ![výběr šablony azure functions](media/azure-functions-lab-image1.png)

4. Nastavte **název projektu** na **"AzureFunctionsLab"** a klepněte na tlačítko **Vytvořit**.

    ![pojmenování a vytvoření projektu funkce Azure](media/azure-functions-lab-image2.png)

5. Rozbalte uzly v **panelu řešení**. Výchozí šablona projektu obsahuje odkazy NuGet na různé balíčky Azure WebJobs a také balíček Newtonsoft.Json.

     Existují také tři soubory: - **host.json** pro popis možností globální konfigurace hostitele - **local.settings.json** pro konfiguraci nastavení služby.
        - Šablona projektu také vytvoří výchozí HttpTrigger. V zájmu tohoto testovacího prostředí byste měli odstranit **soubor HttpTrigger.cs** z projektu.

    Otevřete **soubor local.settings.json**. Ve výchozím nastavení má dvě prázdná nastavení připojovacího řetězce.

    ![panel řešení zobrazující soubor local.settings.json](media/azure-functions-lab-image3.png)

## <a name="exercise-2-creating-an-azure-storage-account"></a>Cvičení 2: Vytvoření účtu úložiště Azure

1. Přihlaste se ke [https://portal.azure.com](https://portal.azure.com)svému účtu Azure na adrese .

1. V části **Oblíbené položky,** která se nachází na levé straně obrazovky, vyberte **Účty úložiště**:

    ![část oblíbených položek na webu Azure Portal zobrazující položku účtů úložiště](media/azure-functions-lab-image4.png)

1. Chcete-li vytvořit nový účet úložiště, vyberte **Přidat:**

    ![Tlačítko pro přidání nového účtu úložiště](media/azure-functions-lab-image5.png)

1. Zadejte globálně jedinečný název **názvu** a znovu jej použijte pro **skupinu Prostředků**. Všechny ostatní položky můžete ponechat jako výchozí.

    ![podrobnosti o novém účtu úložiště](media/azure-functions-lab-image6.png)

1. Klikněte na **Vytvořit**. Vytvoření účtu úložiště může trvat několik minut. Jakmile bude úspěšně vytvořeno, zobrazí se oznámení.

    ![oznámení o úspěšném nasazení](media/azure-functions-lab-image7.png)

1. V oznámení vyberte tlačítko **Přejít na prostředek.**

1. Vyberte kartu **Přístupové klávesy.**

    ![nastavení přístupového klíče](media/azure-functions-lab-image8.png)

1. Zkopírujte první **připojovací řetězec**. Tento řetězec se používá k integraci úložiště Azure s azure funkce později.

    ![informace pro klíč 1](media/azure-functions-lab-image9.png)

1. Vraťte se do **Visual Studia pro Mac** a vložte úplný připojovací řetězec jako nastavení **AzureWebJobsStorage** v **local.settings.json**. Nyní můžete odkazovat na název nastavení v atributech pro funkce, které potřebují přístup k jeho prostředkům.

    ![soubor místního nastavení se zadaným tlačítkem připojení](media/azure-functions-lab-image10.png)

## <a name="example-3-creating-and-debugging-an-azure-function"></a>Příklad 3: Vytvoření a ladění funkce Azure

1. Nyní jste připraveni začít přidávat nějaký kód. Při práci s knihovnou tříd .NET jsou funkce Azure přidány jako statické metody. Na **panelu řešení**klikněte pravým tlačítkem myši na uzel projektu **AzureFunctions** a vyberte **přidat > přidat funkci**:

    ![Přidat možnost funkce](media/azure-functions-lab-image11.png)

1. V dialogovém okně Nové funkce Azure vyberte obecnou šablonu webhooku. Chcete-li vytvořit funkci, nastavte **název** na **Přidat** a klepněte na **ok:**

    ![Dialogové okno Nové funkce azure](media/azure-functions-lab-image12.png)

1. V horní části nového souboru přidejte níže uvedené direktivy **using:**

    ```csharp
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using System.Web;
    using Microsoft.WindowsAzure.Storage.Table;
    ```

1. Odeberte `Run` existující metodu a přidejte níže uvedenou metodu do třídy jako funkci Azure:

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

1. Pojďme projít definici metody kousek po kousku.

    První věc, kterou uvidíte, je atribut **FunctionName,** který označí tuto metodu jako funkci Azure. Atribut označuje veřejný název funkce. Název atributu nemusí odpovídat názvu skutečné metody.

    ![Nová metoda run se zvýrazněným atributem FunctionName](media/azure-functions-lab-image13.png)

1. Dále je metoda označena jako **veřejná statická** metoda, která je požadována. Všimněte si také, že vrácená hodnota je **int**. Pokud není uvedeno jinak pomocí atributů metody, všechny neanulové vrácená hodnota Funkce Azure je vrácena klientovi jako text. Ve výchozím nastavení je vrácena jako **XML**, ale může být změněna na **JSON**, což budete dělat později v testovacím prostředí.

    ![Nová metoda spuštění se zvýrazněnou inicializací metody](media/azure-functions-lab-image14.png)

1. První parametr je označen atributem **HttpTrigger,** což znamená, že tato metoda je vyvolána požadavkem HTTP. Atribut také určuje úroveň autorizace metody, stejně jako slovesa, která podporuje (pouze **"GET"** v tomto případě). Můžete také volitelně definovat **Route,** která přepíše cestu k metodě a nabízí způsob, jak automaticky extrahovat proměnné z cesty. Vzhledem k **tomu, že route** je zde null, cesta k této metodě bude výchozí **/api/Add**.

    ![Nová metoda spuštění se zvýrazněným parametrem](media/azure-functions-lab-image15.png)

1. Konečný parametr metody je **TraceWriter,** který lze použít k protokolování zpráv pro diagnostiku a chyby.

    ![Nová metoda spuštění se zvýrazněnou položkou TraceWriter](media/azure-functions-lab-image16.png)

1. Kliknutím na okraj řádku nastavte zarážku na **vratné** čáře metody:

    ![Zarážka nastavená na řádku návratu](media/azure-functions-lab-image17.png)

1. Sestavení a spuštění projektu v relaci ladění stisknutím **klávesy F5** nebo výběrem **možnosti Spustit > Spustit ladění**. Můžete také klepnout na tlačítko **Spustit.** Všechny tyto možnosti provádějí stejný úkol. Zbytek této laboratoře odkazuje **F5**, ale můžete použít metodu, kterou najdete nejpohodlnější.

    ![Sestavení a spuštění projektu](media/azure-functions-lab-image18.png)

1. Spuštěním projektu se automaticky otevře aplikace Terminál.

1. Projekt prochází procesem zjišťování funkcí Azure na základě atributů metody a konvence souboru, která je popsána dále v tomto článku. V tomto případě zjistí jednu funkci Azure a "generuje" 1 funkce úlohy.

    ![Výstup funkce Azure v terminálu](media/azure-functions-lab-image19.png)

1. V dolní části spouštěcí zprávy Azure Functions hostitel vytiskne adresy URL všech aktivačních api http aktivační. Měl by tu být jen jeden. Zkopírujte tuto adresu URL a vložte ji na novou kartu prohlížeče.

    ![Adresa URL rozhraní API pro azure](media/azure-functions-lab-image20.png)

1. Zarážka by měla být aktivační okamžitě. Webový požadavek byl směrován do funkce a nyní může být laděn. Najeďte myší na proměnnou **x,** abyste viděli její hodnotu.

    ![Aktivovaná zarážka](media/azure-functions-lab-image21.png)

1. Odeberte zarážku stejnou metodou, která byla použita k jeho přidání dříve (klikněte na okraj nebo vyberte čáru a stiskněte **klávesu F9**).

1. Chcete-li pokračovat v běhu, stiskněte **klávesu F5.**

1. V prohlížeči bude vykreslen výsledek XML metody. Podle očekávání vytvoří operace pevně zakódované hodování věrohodnou částku. Všimněte si, že pokud se v Safari zobrazuje pouze "3", přejděte na **předvolby safari > > Pokročilé** a zaškrtněte**políčko "Zobrazit vývoj v řádku nabídek"** a znovu načtěte stránku.

1. V **sadě Visual Studio for Mac**ukončete relaci ladění klepnutím na tlačítko **Zastavit.** Chcete-li zajistit, že nové změny jsou zvedl, nezapomeňte restartovat (zastavit a spustit) relace ladění.

    ![Zastavit ladění, volba](media/azure-functions-lab-image22.png)

1. V **Run** metoda, nahradit **x** a **y** definice s níže uvedený kód. Tento kód extrahuje hodnoty z řetězce dotazu adresy URL tak, aby operace sčítání lze provádět dynamicky na základě zadaných parametrů.

    ```csharp
    var query = HttpUtility.ParseQueryString(req.RequestUri.Query);

    int x = int.Parse(query["x"]);

    int y = int.Parse(query["y"]);

    return x + y;
    ```

1. Spusťte aplikaci.

1. Vraťte se do okna prohlížeče `/?x=2&y=3` a připojte řetězec k adrese URL. Celá adresa URL `http://localhost:7071/api/Add?x=2&y=3`by nyní měla být . Přejděte na novou adresu URL.

1. Tentokrát by měl výsledek odrážet nové parametry. Nebojte se spustit projekt s různými hodnotami. Všimněte si, že neexistuje žádná kontrola chyb, takže neplatné nebo chybějící parametry způsobí chybu.

1. Zastavte relaci ladění.

## <a name="exercise-4-working-with-functionjson"></a>Cvičení 4: Práce s function.json

1. V dřívějším cvičení bylo zmíněno, že Visual Studio pro Mac "vygeneroval" funkce úlohy pro funkci Azure definované v knihovně. Důvodem je, že Azure Functions ve skutečnosti nepoužívá atributy metody za běhu, ale místo toho používá konvence systému souborů v době kompilace ke konfiguraci, kde a jak jsou funkce Azure k dispozici. V **panelu řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte **příkaz Odhalit ve Finderu**.

     ![Možnost Nabídka Odhalit ve Finderu](media/azure-functions-lab-image23.png)

1. Přejděte dolů v systému souborů, dokud nedosáhnete **bin/Debug/netstandard2.0**. Měla by existovat složka s názvem **Přidat**. Tato složka byla vytvořena tak, aby odpovídala atributu název funkce v kódu C#. Rozbalte složku Přidat a odhalte jeden soubor **function.json.** Tento soubor používá runtime k hostování a správě funkce Azure. Pro ostatní jazykové modely bez podpory kompilace (například skript jazyka C# nebo JavaScript) musí být tyto složky vytvořeny a udržovány ručně. Pro vývojáře Jazyka C# jsou automaticky generovány z metadat atributu při sestavení. Klikněte pravým tlačítkem myši na **soubor function.json** a vyberte jej otevřete v sadě Visual Studio.

    ![function.json v adresáři souborů](media/azure-functions-lab-image24.png)

1. Vzhledem k předchozím krokům tohoto kurzu byste měli mít základní znalostatributy jazyka C#. Vezmeme-li to v úvahu, tento JSON by měl vypadat povědomě. Existuje však několik položek, které nebyly zahrnuty v dřívějších cvičeních. Například každá **vazba** musí mít nastaven **směr.** Jak můžete odvodit, **"in"** znamená, že parametr je vstup, zatímco **"out"** označuje, že parametr je buď vrácená hodnota (přes **$return**) nebo **out** parametr metody. Je také nutné zadat **scriptFile** (vzhledem k tomuto konečnému umístění) a **entryPoint** metoda (veřejné a statické) v rámci sestavení. V následujících několika krocích přidáte vlastní cestu funkce pomocí tohoto modelu, takže zkopírujte obsah tohoto souboru do schránky.

    ![function.json soubor otevřený v visual studiu pro mac](media/azure-functions-lab-image25.png)

1. V **panelu řešení**klepněte pravým tlačítkem myši na uzel projektu **AzureFunctionsLab** a vyberte **přidat > novou složku**. Pojmenujte novou složku **Adder**. Ve výchozím nastavení konvence název této složky definuje cestu k rozhraní API, například **api/Adder**.

    ![Nová možnost složky](media/azure-functions-lab-image26.png)

1. Klepněte pravým tlačítkem myši na složku **Zmije** a vyberte **přidat > nový soubor**.

    ![Nový soubor, volba](media/azure-functions-lab-image27.png)

1. Vyberte **kategorii Web** a šablonu Prázdný soubor **JSON.** Nastavte **funkci** **function** Název a klepněte na tlačítko **Nový**.

    ![Prázdný soubor json, volba](media/azure-functions-lab-image28.png)

1. Vložte obsah jiné **ho souboru function.json** (od kroku 3) a nahraďte výchozí obsah nově vytvořeného souboru.

1. Odstraňte z horní části souboru json následující řádky:

    ```json
    "configurationSource":"attributes",
    "generatedBy":"Microsoft.NET.Sdk.Functions-1.0.13",
    ```

1. Na konci první vazby (za řádek **"název": "req"** přidejte níže uvedené vlastnosti. Nezapomeňte na předchozí řádek uvést čárku. Tato vlastnost přepíše výchozí kořen tak, že bude nyní extrahovat parametry **int** z cesty a umístit je do parametrů metody, které jsou pojmenovány **x** a **y**.

    ```json
    "direction": "in",
    "route": "Adder/{x:int?}/{y:int?}"
    ```

1. Přidejte další vazbu pod první. Tato vazba zpracovává vrácenou hodnotu funkce. Nezapomeňte na předchozí řádek uvést čárku:

    ```json
    {
    "name": "$return",
    "type": "http",
    "direction": "out"
    }
    ```

1. Také aktualizujte vlastnost **entryPoint** v dolní části souboru a použijte metodu nazvanou **"Add2"**, například, jak je uvedeno níže. To je pro ilustraci, že cesta **api/ Adder ...** mohl mapovat na vhodnou metodu s libovolným názvem (**Add2** zde).

    ```json
    "entryPoint": "<project-name>.<function-class-name>.Add2"
    ```

1. Konečný soubor **function.json** by měl vypadat jako následující soubor json:

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

1. Posledním krokem, který je nutný k tomu, aby to vše fungovalo, je pokyn visual studio pro Mac zkopírovat tento soubor do stejné relativní cesty ve výstupním adresáři při každé změně. S vybraným souborem zvolte kartu vlastností z pravého pruhu a pro **kopírovat do výstupního adresáře** vyberte **Kopírovat, pokud je novější**:

    ![Možnosti vlastností souboru json](media/azure-functions-lab-image30.png)

1. V **Add.cs**nahraďte metodu `Run` (včetně atributu) následující metodou pro splnění očekávané funkce. Je velmi podobný `Run`, kromě toho, že nepoužívá žádné atributy a má explicitní parametry pro **x** a **y**.

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

1. Stisknutím **klávesy F5** sestavíte a spusťte projekt.

1. Jak sestavení dokončí a platforma se točí nahoru, bude nyní znamenat, že je k dispozici druhá trasa pro požadavky, které mapuje na nově přidanou metodu:

    ![Adresa URL pro funkce http](media/azure-functions-lab-image31.png)

1. Vraťte okno prohlížeče **http://localhost:7071/api/Adder/3/5**a přejděte na .

1. Tentokrát metoda funguje znovu, tahání parametry z cesty a produkovat součet.

1. Vraťte se do **Visual Studia pro Mac** a ukončete relaci ladění.

## <a name="exercise-5-working-with-azure-storage-tables"></a>Cvičení 5: Práce s tabulkami úložišť Azure

Služba, kterou vytváříte, může být často mnohem složitější než to, co jsme doposud vytvořili, a vyžaduje značné množství času a/nebo infrastruktury. V takovém případě může být efektivní přijímat požadavky, které jsou zařazeny do fronty pro zpracování, když jsou k dispozici prostředky, které Azure Functions poskytuje podporu. V ostatních případech budete chtít data ukládat centrálně. Tabulky Azure Storage vám to umožní rychle.

1. Do **Add.cs**přidejte níže uvedenou třídu . Měl by přejít do oboru názvů, ale mimo existující třídu.

    ```csharp
    public class TableRow : TableEntity
    {
        public int X { get; set; }
        public int Y { get; set; }
        public int Sum { get; set; }
    }
    ```

1. V rámci **Add** třídy přidejte níže uvedený kód a zaveďte jinou funkci. Všimněte si, že tento je jedinečný tak daleko v tom, že nezahrnuje odpověď HTTP. Poslední řádek vrátí nový **TableRow** naplněný některé klíčové informace, které usnadní načtení později (**PartitionKey** a **RowKey**), jakož i jeho parametry a součet. Kód v rámci metody také používá **TraceWriter,** aby bylo snazší vědět, kdy je funkce spuštěna.

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

1. Stisknutím **klávesy F5** sestavíte a spusťte projekt.

1. Na kartě prohlížeče **http://localhost:7071/api/Process/4/6**přejděte na . To bude klást další zprávu do fronty, což by mělo nakonec za následek další řádek, který je přidán do tabulky.

1. Vraťte se do **terminálu** a sledujte příchozí požadavek na **4 + 6**.

    ![Terminálový výstup zobrazující požadavek na přidání](media/azure-functions-lab-image32.png)

1. Vraťte se do prohlížeče a aktualizujte požadavek na stejnou adresu URL. Tentokrát se zobrazí chyba po **Process** metoda. Důvodem je, že kód se pokouší přidat řádek do tabulky Azure Table Storage pomocí kombinace klíče oddílu a řádku, která již existuje.

    ```
    System.Private.CoreLib: Exception while executing function: Process. Microsoft.Azure.WebJobs.Host: Error while handling parameter $return after function returned:. Microsoft.Azure.WebJobs.Host: The specified entity already exists.
    ```

1. Ukončite relaci ladění.

1. Chcete-li chybu zmírnit, přidejte následující parametr do definice metody bezprostředně před parametr **TraceWriter.** Tento parametr instruuje platformu Azure Functions, aby se pokusila načíst **TableRow** z tabulky **Výsledky** na **partitionkey,** který používáme k ukládání výsledků. Některé skutečné kouzlo však vstoupí do hry, když zjistíte, že **RowKey** je dynamicky generován na základě jiných parametrů **x** a **y** pro stejnou metodu. Pokud tento řádek již existuje, pak **tableRow** bude mít, když metoda začíná bez další práce vyžadované vývojářem. Pokud řádek neexistuje, bude mít hodnotu null. Tento druh efektivity umožňuje vývojářům zaměřit se na důležitou obchodní logiku a ne na infrastrukturu.

    ```csharp
    [Table("Results", "sums", "{x}_{y}")]
    TableRow tableRow,
    ```

1. Přidejte níže uvedený kód na začátek metody. Pokud **tableRow** není null, pak již máme výsledky pro požadovanou operaci a můžete jej okamžitě vrátit. V opačném případě funkce pokračuje jako dříve. I když to nemusí být nejrobustnější způsob, jak vrátit data, ilustruje bod, který můžete organizovat neuvěřitelně sofistikované operace napříč více škálovatelných vrstev s velmi malým kódem.

    ```csharp
    if (tableRow != null)
    {
        log.Info($"{x} + {y} already exists");
        return null;
    }
    ```

1. Stisknutím **klávesy F5** sestavíte a spusťte projekt.

1. Na kartě prohlížeče aktualizujte **http://localhost:7071/api/Process/4/6**adresu URL na adrese . Vzhledem k tomu, že řádek tabulky pro tento záznam existuje, měl by se vrátit okamžitě a bez chyby. Vzhledem k tomu, že neexistuje žádný výstup HTTP, můžete vidět výstup v terminálu.

    ![Výstup terminálu zobrazující řádek tabulky již existuje.](media/azure-functions-lab-image33.png)

1. Aktualizujte adresu URL tak, aby odrážela **http://localhost:7071/api/Process/5/7**kombinaci, která ještě nebyla testována, například . Všimněte si zprávy v terminálu, která označuje, že řádek tabulky nebyl nalezen (podle očekávání).

    ![Výstup terminálu zobrazující nový proces](media/azure-functions-lab-image34.png)

1. Vraťte se do **Visual Studia pro Mac** a ukončete relaci ladění.

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

V tomto testovacím prostředí jste se naučili, jak začít vytvářet funkce Azure pomocí Visual Studia pro Mac.
