---
title: 'Kurz: Azure Functions'
description: Použití služby Azure Functions v Visual Studio pro Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 38FD2070-5151-482E-B0A9-993715128736
ms.topic: tutorial
ms.openlocfilehash: 144580b0ebe0eb3615c5cf55c1bee03ff2a614fa
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2020
ms.locfileid: "85938974"
---
# <a name="tutorial-getting-started-with-azure-functions"></a>Kurz: Začínáme s Azure Functions

V tomto testovacím prostředí se naučíte, jak začít sestavovat Azure Functions pomocí Visual Studio pro Mac. Integrujte se také s tabulkami Azure Storage, které reprezentují jeden z mnoha druhů vazeb a triggerů, které jsou k dispozici pro Azure Functions vývojářům.

## <a name="objectives"></a>Cíle

> [!div class="checklist"]
> * Vytvořit a ladit místní Azure Functions
> * Integrace s webovými prostředky a prostředky úložiště Azure
> * Orchestrace pracovního postupu zahrnujícího více Azure Functions

## <a name="requirements"></a>Požadavky

- Visual Studio pro Mac 7,5 nebo vyšší.
- Předplatné Azure (k dispozici zdarma z [https://azure.com/free](https://azure.com/free) ).

## <a name="exercise-1-creating-an-azure-functions-project"></a>Cvičení 1: vytvoření projektu Azure Functions

1. Spusťte **Visual Studio pro Mac**.

2. Vyberte **soubor > nové řešení**.

3. V kategorii **Cloud > obecné** vyberte šablonu **Azure Functions** . Použijete jazyk C# k vytvoření knihovny tříd .NET, která je hostitelem Azure Functions. Klikněte na **Další**.

    ![Výběr šablony Azure Functions](media/azure-functions-lab-image1.png)

4. Nastavte **název projektu** na **"AzureFunctionsLab"** a klikněte na **vytvořit**.

    ![pojmenování a vytvoření projektu funkce Azure Functions](media/azure-functions-lab-image2.png)

5. Rozbalte uzly v **oblast řešení**. Výchozí šablona projektu obsahuje odkazy NuGet na nejrůznější balíčky Azure WebJobs a také Newtonsoft.Jsv balíčku.

     K dispozici jsou také tři soubory:- **host.js** pro popis globálních možností konfigurace pro hostitele- **local.settings.jsv** pro konfiguraci nastavení služby.
        – Šablona projektu také vytvoří výchozí HttpTrigger. V zájmu tohoto testovacího prostředí byste měli soubor **HttpTrigger.cs** odstranit z projektu.

    Otevřete **local.settings.js**. Ve výchozím nastavení má dvě prázdné nastavení připojovacího řetězce.

    ![panel řešení zobrazující local.settings.jsv souboru](media/azure-functions-lab-image3.png)

## <a name="exercise-2-creating-an-azure-storage-account"></a>Cvičení 2: vytvoření účtu služby Azure Storage

1. Přihlaste se k účtu Azure na adrese [https://portal.azure.com](https://portal.azure.com) .

1. V části **Oblíbené** , která se nachází na levé straně obrazovky, vyberte **účty úložiště**:

    ![oddíl oblíbených položek v Azure Portal zobrazení položky účtů úložiště](media/azure-functions-lab-image4.png)

1. Vyberte **Přidat** a vytvořte nový účet úložiště:

    ![Tlačítko pro přidání nového účtu úložiště](media/azure-functions-lab-image5.png)

1. Zadejte globálně jedinečný název pro **název** a znovu ho použijte pro **skupinu prostředků**. Všechny ostatní položky můžete ponechat jako výchozí.

    ![Podrobnosti o novém účtu úložiště](media/azure-functions-lab-image6.png)

1. Klikněte na **Vytvořit**. Vytvoření účtu úložiště může trvat několik minut. Po úspěšném vytvoření oznámení obdržíte oznámení.

    ![oznámení o úspěšném nasazení](media/azure-functions-lab-image7.png)

1. V oznámení vyberte tlačítko **Přejít k prostředku** .

1. Vyberte kartu **přístupové klíče** .

    ![nastavení přístupového klíče](media/azure-functions-lab-image8.png)

1. Zkopírujte první **připojovací řetězec**. Tento řetězec se používá k integraci služby Azure Storage s vaším Azure Functions novějším.

    ![informace pro klíč 1](media/azure-functions-lab-image9.png)

1. Vraťte se do **Visual Studio pro Mac** a vložte úplný připojovací řetězec do nastavení **AzureWebJobsStorage** v **local.settings.js**. Nyní můžete odkazovat na název nastavení v atributech pro funkce, které potřebují přístup ke svým prostředkům.

    ![soubor místních nastavení s zadaným klíčem připojení](media/azure-functions-lab-image10.png)

## <a name="example-3-creating-and-debugging-an-azure-function"></a>Příklad 3: vytvoření a ladění funkce Azure Functions

1. Teď jste připraveni začít přidávat nějaký kód. Při práci s knihovnou tříd .NET jsou Azure Functions přidány jako statické metody. Z **oblast řešení**klikněte pravým tlačítkem myši na uzel projektu **AzureFunctions** a vyberte **Přidat > přidat funkci**:

    ![Přidat možnost funkce](media/azure-functions-lab-image11.png)

1. V dialogovém okně Nový Azure Functions vyberte šablonu obecného Webhooku. Nastavte **název** , který chcete **Přidat** , a kliknutím na tlačítko **OK** vytvořte funkci:

    ![Nový dialog Azure Functions](media/azure-functions-lab-image12.png)

1. V horní části nového souboru přidejte následující direktivy **using** :

    ```csharp
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using System.Web;
    using Microsoft.WindowsAzure.Storage.Table;
    ```

1. Odeberte existující `Run` metodu a přidejte následující metodu do třídy jako funkci Azure Functions:

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

1. Pojďme si projít definicí metody podle kusu.

    První věc, kterou vidíte, je atributem **Function** , který označuje tuto metodu jako funkci Azure Functions. Atribut označuje veřejný název funkce. Název atributu nemusí odpovídat skutečnému názvu metody.

    ![Nová metoda Run s atributem Function byl zvýrazněna.](media/azure-functions-lab-image13.png)

1. Dále je metoda označena jako **veřejná statická** metoda, která je povinná. Všimněte si také, že návratová hodnota je **int**. Pokud není uvedeno jinak pomocí atributů metody, vrátí se klientovi jako text jakákoli návratová hodnota typu Azure Function, která není typu void. Ve výchozím nastavení se vrátí jako **XML**, ale dá se změnit na **JSON**, které budete později dělat v testovacím prostředí.

    ![Nová metoda Run se zvýrazněnou inicializací metody](media/azure-functions-lab-image14.png)

1. První parametr je označen atributem **HttpTrigger** , který označuje, že tato metoda je vyvolána požadavkem http. Atribut také určuje úroveň autorizace metody a také příkazy, které podporuje (v tomto případě pouze **"Get"** ). Volitelně můžete také definovat **trasu** , která přepíše cestu k metodě, a nabízí způsob, jak automaticky extrahovat proměnné z cesty. Vzhledem k tomu, že **trasa** má hodnotu null, cesta k této metodě bude ve výchozím nastavení **/API/Add**.

    ![Nová metoda Run se zvýrazněným parametrem](media/azure-functions-lab-image15.png)

1. Posledním parametrem metody je **TraceWriter** , který lze použít k protokolování zpráv pro diagnostiku a chyby.

    ![Nová metoda Run se zvýrazněnou možností TraceWriter](media/azure-functions-lab-image16.png)

1. Kliknutím na okraj řádku nastavte zarážku na **návratovou** čáru metody:

    ![Zarážka nastavená na řádku vrácení](media/azure-functions-lab-image17.png)

1. Sestavte a spusťte projekt v ladicí relaci stisknutím klávesy **F5** nebo výběrem možnosti **Spustit > spustit ladění**. Případně můžete kliknout na tlačítko **Spustit** . Všechny tyto možnosti provádějí stejnou úlohu. Zbytek tohoto testovacího prostředí se odkazuje na **F5**, ale můžete použít metodu, kterou vyhledáte nejpohodlnější.

    ![Sestavit a spustit projekt](media/azure-functions-lab-image18.png)

1. Při spuštění projektu se automaticky otevře aplikace Terminal.

1. Projekt projde procesem detekce Azure Functions na základě atributů metody a konvencí souborů, která se zabývá dále v tomto článku. V takovém případě detekuje jednu funkci Azure a "vygeneruje" 1 funkci úlohy.

    ![Výstup funkce Azure Functions v terminálu](media/azure-functions-lab-image19.png)

1. V dolní části zpráv po spuštění vypíše hostitel Azure Functions adresy URL všech rozhraní API triggeru protokolu HTTP. Měla by být jenom jedna. Zkopírujte tuto adresu URL a vložte ji na novou kartu prohlížeče.

    ![Adresa URL rozhraní API Azure Functions](media/azure-functions-lab-image20.png)

1. Zarážka by se měla aktivovat okamžitě. Webová žádost byla směrována do funkce a lze ji nyní ladit. Pomocí myši nad proměnnou **x** zobrazíte její hodnotu.

    ![Zarážka spuštěna](media/azure-functions-lab-image21.png)

1. Odeberte zarážku pomocí stejné metody, kterou jste použili k jejímu přidání, a klikněte na okraj nebo vyberte čáru a stiskněte **F9**.

1. Pokračujte v běhu stisknutím klávesy **F5** .

1. V prohlížeči se vykreslí výsledek XML metody. Jak bylo očekáváno, operace sčítání pevně zakódované vytvoří plausible Sum. Všimněte si, že pokud v Safari vidíte pouze "3", přejděte na **safari > předvolby > Upřesnit** a zapište stránku v**nabídce Zobrazit vývoj na řádku nabídek**a znovu ji načtěte.

1. V **Visual Studio pro Mac**kliknutím na tlačítko **zastavit** ukončete ladicí relaci. Chcete-li zajistit, aby byly nové změny vyzvednuty, nezapomeňte restartovat (zastavit a poté spustit) relaci ladění.

    ![Zastavit možnost ladění](media/azure-functions-lab-image22.png)

1. V metodě **Run** nahraďte definice **x** a **y** následujícím kódem. Tento kód extrahuje hodnoty z řetězce dotazu adresy URL tak, aby operace sčítání mohla být provedena dynamicky na základě zadaných parametrů.

    ```csharp
    var query = HttpUtility.ParseQueryString(req.RequestUri.Query);

    int x = int.Parse(query["x"]);

    int y = int.Parse(query["y"]);

    return x + y;
    ```

1. Spusťte aplikaci.

1. Vraťte se do okna prohlížeče a přidejte řetězec `/?x=2&y=3` k adrese URL. Celá adresa URL by teď měla být `http://localhost:7071/api/Add?x=2&y=3` . Přejděte na novou adresu URL.

1. Tentokrát by výsledek měl odrážet nové parametry. Bez obav spusťte projekt s různými hodnotami. Počítejte s tím, že není k dispozici žádná kontrola chyb, takže neplatné nebo chybějící parametry způsobí vyvolání chyby.

1. Zastavte ladicí relaci.

## <a name="exercise-4-working-with-functionjson"></a>Cvičení 4: práce s function.jsna

1. V dřívějším cvičení bylo zmíněno Visual Studio pro Mac "vygenerované" funkce úlohy pro funkci Azure, která je definována v knihovně. Důvodem je to, že Azure Functions ve skutečnosti nepoužívají atributy metody za běhu, ale místo toho používá konvenci systému souborů při kompilaci ke konfiguraci, kde a jakým způsobem Azure Functions k dispozici. Z **oblast řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Zobrazit ve Finderu**.

     ![Zobrazit ve Finderu – možnost nabídky](media/azure-functions-lab-image23.png)

1. Přejděte dolů do systému souborů, dokud nedosáhnete **přihrádky/ladění/netstandard 2.0**. Měla by existovat složka s názvem **Add**. Tato složka byla vytvořena tak, aby odpovídala atributu názvu funkce v kódu jazyka C#. Rozbalte složku přidat, aby se zobrazila jedna **function.jsv** souboru. Tento soubor používá modul runtime k hostování a správě funkce Azure Functions. Pro jiné jazykové modely bez podpory při kompilaci (například skript C# nebo JavaScript) je nutné tyto složky ručně vytvořit a spravovat. Pro vývojáře v jazyce C# jsou automaticky generovány z metadat atributu při sestavení. Kliknutím pravým tlačítkem na **function.jszapnuto** a výběrem ho otevřete v aplikaci Visual Studio.

    ![function.jsv adresáři souborů](media/azure-functions-lab-image24.png)

1. V předchozích krocích tohoto kurzu byste měli mít základní znalosti atributů C#. Tento kód JSON by měl brát v úvahu. Existuje však několik položek, které nebyly pokryty v předchozích cvičeních. Například každá **vazba** musí mít svou **směrovou** sadu. Jak je možné odvodit, **"in"** znamená, že parametr je Input, zatímco **"out"** označuje, že parametr je buď návratovou hodnotou (prostřednictvím **$return**), nebo **výstupním** parametrem metody. Také je nutné zadat **scriptFile** (vzhledem k tomuto konečnému umístění) a metodu **EntryPoint** (Public a static) v rámci sestavení. V několika dalších krocích přidáte vlastní cestu funkce pomocí tohoto modelu, takže zkopírujete obsah tohoto souboru do schránky.

    ![function.jsv souboru otevřeném v aplikaci Visual Studio pro Mac](media/azure-functions-lab-image25.png)

1. V **oblast řešení**klikněte pravým tlačítkem myši na uzel projektu **AzureFunctionsLab** a vyberte **Přidat > nová složka**. Pojmenujte nové **přidávání**složek. Ve výchozím nastavení určuje název této složky cestu k rozhraní API, jako je například **rozhraní API nebo přidávání**.

    ![Možnost nové složky](media/azure-functions-lab-image26.png)

1. Klikněte pravým tlačítkem na složku pro **přidávání** a vyberte **Přidat > nový soubor**.

    ![Možnost Nový soubor](media/azure-functions-lab-image27.png)

1. Vyberte kategorii **Web** a prázdnou šablonu **souboru JSON** . Nastavte **název** na **funkce** a klikněte na **Nový**.

    ![Empty – možnost souboru JSON](media/azure-functions-lab-image28.png)

1. Vložte obsah ostatních **function.jsv** (z kroku 3) do a nahraďte výchozí obsah nově vytvořeného souboru.

1. Z horní části souboru JSON odeberte následující řádky:

    ```json
    "configurationSource":"attributes",
    "generatedBy":"Microsoft.NET.Sdk.Functions-1.0.13",
    ```

1. Na konci první vazby (po řádku **"Name": "REQ"** ) přidejte níže uvedené vlastnosti. Nezapomeňte na předchozí řádek vložit čárku. Tato vlastnost přepisuje výchozí kořen tak, že bude nyní extrahovat parametry typu **int** z cesty a umístit je do parametrů metody, které jsou pojmenovány **x** a **y**.

    ```json
    "direction": "in",
    "route": "Adder/{x:int?}/{y:int?}"
    ```

1. Přidejte další vazbu pod první. Tato vazba zpracovává vrácenou hodnotu funkce. Nezapomeňte na předchozí řádek vložit čárku:

    ```json
    {
    "name": "$return",
    "type": "http",
    "direction": "out"
    }
    ```

1. Aktualizujte také vlastnost **EntryPoint** v dolní části souboru tak, aby používala metodu nazvanou **"Add2"**, například níže. To ukazuje, že rozhraní API pro cestu a přizpůsobování **...** se může namapovat na odpovídající metodu s libovolným názvem (**Add2** ).

    ```json
    "entryPoint": "<project-name>.<function-class-name>.Add2"
    ```

1. Poslední **function.js** souboru by měla vypadat jako v následujícím formátu JSON:

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

1. V posledním kroku, který je potřeba k tomu, aby všechno fungovalo, je dát Visual Studio pro Mac zkopírovat tento soubor do stejné relativní cesty ve výstupním adresáři pokaždé, když se změní. Když je vybraný soubor, zvolte kartu vlastnosti z pravého panelu a pro **Kopírovat do výstupního adresáře** vyberte **Kopírovat, pokud je novější**:

    ![Možnosti vlastností souboru JSON](media/azure-functions-lab-image30.png)

1. V **Add.cs**nahraďte `Run` metodu (včetně atributu) následující metodou pro splnění očekávané funkce. Je velmi podobný jako s `Run` tím rozdílem, že nepoužívá žádné atributy a má explicitní parametry pro **x** a **y**.

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

1. Stisknutím klávesy **F5** Sestavte a spusťte projekt.

1. Vzhledem k tomu, že sestavení se dokončí a platforma se číselníkem, nyní bude znamenat, že je k dispozici Druhá trasa pro požadavky, které se mapují na nově přidanou metodu:

    ![Adresa URL pro funkce http](media/azure-functions-lab-image31.png)

1. Vraťte okno prohlížeče a přejděte na adresu **http://localhost:7071/api/Adder/3/5** .

1. Tentokrát metoda znovu funguje, načítat parametry z cesty a vyprodukuje součet.

1. Vraťte se do **Visual Studio pro Mac** a ukončete relaci ladění.

## <a name="exercise-5-working-with-azure-storage-tables"></a>Cvičení 5: práce s tabulkami služby Azure Storage

Služba, kterou sestavíte, může být často mnohem složitější než ta, kterou jsme zatím sestavili, a vyžádat si značné množství času a/nebo infrastruktury, která se má spustit. V takovém případě může být vhodné přijmout žádosti, které jsou zařazeny do fronty ke zpracování, když budou prostředky k dispozici, což Azure Functions poskytuje podporu pro. V jiných případech budete chtít data ukládat centrálně. Azure Storage tabulky vám to umožní rychle.

1. Do **Add.cs**přidejte třídu níže. Měl by jít dovnitř oboru názvů, ale mimo stávající třídu.

    ```csharp
    public class TableRow : TableEntity
    {
        public int X { get; set; }
        public int Y { get; set; }
        public int Sum { get; set; }
    }
    ```

1. V rámci **Přidat** třídu přidejte následující kód, aby bylo možné zavést další funkci. Všimněte si, že toto je jedinečné, zatím v tom, že nezahrnuje odpověď HTTP. Poslední řádek vrátí nové **TableRow** vyplněné s některými klíčovými informacemi, které usnadňují pozdější načtení (**PartitionKey** a **RowKey**) a také jeho parametry a součet. Kód v rámci metody také používá **TraceWriter** k tomu, aby bylo snazší zjistit, kdy se funkce spouští.

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

1. Stisknutím klávesy **F5** Sestavte a spusťte projekt.

1. Na kartě prohlížeč přejděte na **http://localhost:7071/api/Process/4/6** . Tím se do fronty vloží další zpráva, která by nakonec měla vést k přidání dalšího řádku do tabulky.

1. Vraťte se do **terminálu** a sledujte příchozí požadavek na **4 + 6**.

    ![Výstup terminálu ukazující žádost o přidání](media/azure-functions-lab-image32.png)

1. Vraťte se do prohlížeče, aby se žádost aktualizovala na stejnou adresu URL. Tentokrát se po metodě **procesu** zobrazí chyba. Důvodem je to, že při pokusu o přidání řádku do tabulky Azure Table Storage se používá kombinace klíče oddílu a řádku, která již existuje.

    ```
    System.Private.CoreLib: Exception while executing function: Process. Microsoft.Azure.WebJobs.Host: Error while handling parameter $return after function returned:. Microsoft.Azure.WebJobs.Host: The specified entity already exists.
    ```

1. Ukončete ladicí relaci.

1. Chcete-li tuto chybu zmírnit, přidejte následující parametr do definice metody bezprostředně před parametr **TraceWriter** . Tento parametr instruuje Azure Functions platformu k pokusu o načtení **TableRow** z tabulky **výsledků** na **PartitionKey** , kterou jsme použili k uložení výsledků. Nicméně když si všimnete, že se **RowKey** dynamicky generuje na základě dalších parametrů **x** a **y** pro velmi stejnou metodu, přijdete o reálné rozhraní Magic. Pokud tento řádek již existuje, **tableRow** ho bude mít, když bude metoda začínat bez další práce, kterou vývojář vyžaduje. Pokud řádek neexistuje, bude mít pouze hodnotu null. Tento druh efektivity umožňuje vývojářům soustředit se na důležitou obchodní logiku a ne na infrastrukturu.

    ```csharp
    [Table("Results", "sums", "{x}_{y}")]
    TableRow tableRow,
    ```

1. Přidejte následující kód na začátek metody. Pokud **tableRow** nemá hodnotu null, pak už máme výsledky pro požadovanou operaci a hned ho můžou vrátit. V opačném případě funkce pokračuje stejně jako dřív. I když to nemusí být nejspolehlivější způsob, jak vracet data, ukazuje to, že můžete neuvěřitelně sofistikované operace napříč několika škálovatelnými úrovněmi s velmi malým kódem.

    ```csharp
    if (tableRow != null)
    {
        log.Info($"{x} + {y} already exists");
        return null;
    }
    ```

1. Stisknutím klávesy **F5** Sestavte a spusťte projekt.

1. Na kartě prohlížeč Aktualizujte adresu URL na adrese **http://localhost:7071/api/Process/4/6** . Vzhledem k tomu, že řádek tabulky pro tento záznam existuje, měl by vracet okamžitě a bez chyby. Vzhledem k tomu, že neexistuje žádný výstup HTTP, můžete zobrazit výstup v terminálu.

    ![Výstup terminálu ukazující, že řádek tabulky již existuje](media/azure-functions-lab-image33.png)

1. Aktualizujte adresu URL tak, aby odrážela kombinaci, která ještě není testována, například **http://localhost:7071/api/Process/5/7** . Poznamenejte si zprávu v terminálu, která indikuje, že se řádek tabulky nenašel (podle očekávání).

    ![Výstup terminálu ukazující nový proces](media/azure-functions-lab-image34.png)

1. Vraťte se do **Visual Studio pro Mac** a ukončete relaci ladění.

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

V tomto testovacím prostředí jste se naučili, jak začít sestavovat Azure Functions s využitím Visual Studio pro Mac.
