---
title: Úvod do služby Azure Functions
description: Pomocí Azure functions v sadě Visual Studio pro Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.openlocfilehash: eaf6f82cdc40b174dcd1ca8deb12c412fe675d70
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295940"
---
# <a name="introduction-to-azure-functions"></a>Úvod do služby Azure Functions

Azure functions je způsob, jak vytvářet a spouštět založený na událostech fragmenty kódu – – funkce – – v cloudu, aniž byste museli explicitně zřizovat nebo spravovat infrastrukturu. Další informace o službě Azure Functions najdete v tématu [dokumentaci ke službě Azure Functions](/azure/azure-functions/).

## <a name="requirements"></a>Požadavky

Jsou součástí nástroje Azure Function **Visual Studio pro Mac 7.5**.

Vytvoření a nasazení služby functions budete potřebovat předplatné Azure, která je k dispozici bezplatně [ https://azure.com/free ](https://azure.com/free).

## <a name="creating-your-first-azure-functions-project"></a>Vytvoření prvního projektu Azure Functions

1. V sadě Visual Studio pro Mac, vyberte **soubor > Nový řešení**.
2. V dialogu Nový projekt, vyberte šablonu Azure Functions v části **Cloud > Obecné** a klikněte na tlačítko **Další**:

    ![Dialogové okno nového projektu s možností Azure functions](media/azure-functions-image1.png)

3. Vyberte počáteční šablonu Azure Functions, kterou chcete použít, zadejte název vaší funkce a klikněte na tlačítko **Další**.

    ![Dialogové okno Nový projekt zobrazuje šablony Azure functions](media/azure-functions-image2.png)

    V závislosti na typu funkce, do které jste vybrali na další stránku vás vyzve k zadejte podrobnosti, jako je například přístupová práva, jak je znázorněno na následujícím obrázku:

    ![Dialogové okno Nový projekt zobrazuje další možnosti](media/azure-functions-image3.png)

    Další informace o různých typech šablon Azure Functions a vazby vlastnosti požadované pro konfiguraci každé šablony najdete v tématu [dostupné funkce šablony](#available-function-templates) oddílu. V tomto příkladu používáme triggeru Http s přístupem oprávnění nastavena na hodnotu anonymní.

4. Jakmile jednou nastavíte parametry, zvolte umístění pro projekt a klikněte na tlačítko **vytvořit**.

Visual Studio pro Mac vytvoří projekt .NET Standard s výchozí funkce zahrnuté. Zahrnuje také odkazy na NuGet pro širokou škálu **AzureWebJobs** balíčky, jakož i **Newtonsoft.Json** balíčku.

![Visual Studio pro Mac editor zobrazení úplně nové funkce azure ze šablony](media/azure-functions-newproj.png)

Nový projekt obsahuje následující soubory:

* **vaše funkce name.cs** – Tato třída obsahuje často používaný kód pro funkci, kterou jste vybrali. Obsahuje **FunctionName** atribut s názvem funkce a aktivační události atribut, který určuje, co spustí – funkce (např.) požadavek HTTP). Další informace o funkci metodu, najdete [referenční informace pro vývojáře Azure Functions C#](/azure/azure-functions/functions-dotnet-class-library) článku.
* **Host.JSON** – tento soubor popisuje možnosti globální konfiguraci pro hostitele funkce. Příklad souboru a informace o dostupných nastaveních pro tento soubor najdete v tématu [referenční materiály k host.json pro Azure Functions](/azure/azure-functions/functions-host-json).
* **Local.Settings.JSON** – tento soubor obsahuje veškeré nastavení spouštění služby functions místně. Tato nastavení jsou používány nástrojů Azure Functions Core. Další informace najdete v tématu [souboru místní nastavení](/azure/azure-functions/functions-run-local#local-settings-file) v článku o Azure Functions Core Tools.

Teď, když jste vytvořili nový projekt Azure Functions v sadě Visual Studio pro Mac, můžete otestovat na výchozí funkci aktivovanou protokolem HTTP z místního počítače.

## <a name="testing-the-function-locally"></a>Testuje se funkce místně

Díky podpoře Azure Functions v sadě Visual Studio for Mac můžete testovat a ladit vaši funkci ve vašem místním vývojovém počítači.

1. Chcete-li funkci lokálně otestovat, stiskněte **spustit** tlačítko v sadě Visual Studio pro Mac:

    ![Spuštění ladění tlačítko v sadě visual studio pro mac](media/azure-functions-run.png)

1. Spuštění projektu spustí místní ladění funkce Azure functions a otevře se nové okno terminálu, jak je znázorněno na následujícím obrázku:

    ![výstup v okně terminálu zobrazující – funkce](media/azure-functions-terminal.png)

    Zkopírujte adresu URL z výstupu.

3. Vložte adresu URL pro požadavek HTTP do panelu Adresa prohlížeče. Přidat řetězec dotazu `?name=<yourname>` na konec adresy URL a proveďte požadavek. Následující obrázek ukazuje odpověď v prohlížeči na místní požadavek GET vrácené funkcí:

    ![požadavek protokolu HTTP v prohlížeči](media/azure-functions-httpreq.png)

## <a name="adding-another-function-to-your-project"></a>Přidání další funkce do vašeho projektu

Šablony funkcí umožňují rychle vytvářet nové funkce s použitím nejběžnějších aktivačních událostí a šablon. Pokud chcete vytvořit jiný typ funkce, postupujte takto:

1. Pokud chcete přidat novou funkci, klikněte pravým tlačítkem na název projektu a vyberte **Přidat > přidat funkci...** :

    ![kontext akce pro přidání nové funkce](media/azure-functions-addnew.png)

2. Z **novou funkci Azure Functions** dialogového okna, vyberte funkci, potřebujete:

    ![Dialogové okno nové funkce azure functions](media/azure-functions-image4.png)

    Seznam šablon funkce Azure Functions jsou součástí [dostupné funkce šablony](#available-function-templates) oddílu.

Výše uvedený postup slouží k přidání dalších funkcí pro váš projekt aplikace funkcí. Každá funkce v projektu může mít jinou aktivační událost, ale funkce musí mít přesně jeden trigger. Další informace najdete v tématu [aktivace Azure Functions a vazby koncepty](/azure/azure-functions/functions-triggers-bindings).

## <a name="publish-to-azure"></a>Publikování do Azure

1. Klikněte pravým tlačítkem na název projektu a vyberte **publikovat > Publikovat do Azure**: ![publikovat v nabídce azure možnost](media/azure-functions-image5.png)
2. Pokud už jste připojili Azure účtu sady Visual Studio pro Mac seznam dostupných aplikací, služeb se zobrazují. Pokud jste ještě přihlášeni, budete vyzváni k tomu.
3. Z **publikovat do služby Azure App Service** dialogového okna, můžete vybrat stávající službu app service nebo vytvořte novou kliknutím **nový**.
4. V **vytvořit novou službu App Service** dialogovém okně nastavení: ![publikovat v nabídce azure možnost](media/azure-functions-image7.png)

    |Nastavení  |Popis  |
    |---------|---------|
    |**Název služby App Service**|Globálně jedinečný název identifikující novou aplikaci function app.|
    |**Předplatné**|Předplatné Azure používat.|
    |**[Skupina prostředků](/azure/azure-resource-manager/resource-group-overview)**|Název skupiny prostředků, ve kterém chcete vytvořit aplikaci function app. Zvolte **+** vytvořit novou skupinu prostředků.|
    |**[Plán služby](/azure/azure-functions/functions-scale)**|Vybrat existující plán nebo vytvořte vlastní plán. Vyberte umístění v oblasti vaší blízkosti nebo v blízkosti jiných služeb vaší funkce přístupu.|

    > [!CAUTION]
    > Je chyba v 7.6 verzi sady Visual Studio for Mac, která způsobí, že publikování nezdaří s chybou zřizování při pokusu vytvořit plán s vlastní službu **ceny** nastavena na **spotřeby**. Tato chyba bude opravena v další vydané verzi služby.

5. Klikněte na tlačítko **Další** k vytvoření účtu úložiště. Modul runtime služby Functions vyžaduje účet úložiště Azure. Klikněte na tlačítko **vlastní** vytvořit účet úložiště pro obecné účely, nebo použijte již existující:

    ![Publikování nabídky azure](media/azure-functions-image8.png)

6. Klikněte na tlačítko **vytvořit** k vytvoření aplikace function app a související prostředky v Azure s těmito nastaveními a nasadí kód projektu funkce.

7. Můžete být vyzváni se dialogové okno během publikování informací do "Aktualizace funkcí verze na Azure". Klikněte na tlačítko **Ano**:

    ![Publikování nabídky azure](media/azure-functions-image12.png)

> [!CAUTION]
> Je chyba v 7.6 verzi sady Visual Studio for Mac ve kterém `FUNCTIONS_EXTENSION_VERSION` není správně nastavená na "Beta verze", což znamená, že vaše funkce se možná nespustí. Tento problém můžete přejít na vaše [fungovat nastavení aplikace](#function-app-settings) a nastavte `FUNCTIONS_EXTENSION_VERSION` z "-1" na "Beta verze".

## <a name="function-app-settings"></a>Nastavení aplikace Function app

Všechna nastavení, které jste přidali v kroku local.settings.json musí být rovněž přidán do aplikace function app v Azure. Tato nastavení nejsou automaticky nahraje při publikování tohoto projektu.

Pro přístup k nastavení aplikace, přejděte na webu azure portal na [ https://ms.portal.azure.com/ ](https://ms.portal.azure.com/). V části **aplikace Function App**vyberte **aplikace Function App** a upozornit na název vaší funkce:

![nabídky Azure functions](media/azure-functions-image9.png)

Z **přehled** kartě vyberte **nastavení aplikace** pod **nakonfigurování funkcí**:

![Prostřednictvím karty funkce azure functions](media/azure-functions-image10.png)

Odsud můžete nastavit nastavení aplikace pro aplikaci function app, ve kterém můžete přidat nové nastavení aplikace nebo upravte stávající:

![oblast nastavení aplikace pro web azure portal](media/azure-functions-image11.png)

Je jedním z důležitých nastavení budete muset nastavit `FUNCTIONS_EXTENSION_VERSION`. Při publikování ze sady Visual Studio pro Mac, je třeba tuto hodnotu nastavit na **beta**.

## <a name="available-function-templates"></a>K dispozici funkce šablon

- **Aktivační událost Githubu** – reakce na události, ke kterým dochází ve svých úložištích Githubu. Další informace najdete v tématu [Azure Functions článku na Githubu](/azure/azure-functions/functions-create-github-webhook-triggered-function)
    - Komentátor Githubu – tato funkce se spustí, když přijme webhook Githubu pro problém nebo o přijetí změn žádost a přidá komentář.
    - WebHook Githubu – tato funkce se spustí, když přijme webhook Githubu.

- **HTTP** – aktivace provádění kódu pomocí požadavku HTTP. Existují explicitní šablony pro následující aktivační události HTTP:
    - Http Trigger
    - CRUD GET protokolu HTTP
    - HTTP POST CRUD
    - Aktivační událost HTTP s parametry


- **Časovač** – provádění úkolů čištění nebo jiných dávkových úkolů podle předdefinovaného plánu. Tato šablona má dvě pole: název a plánu, což je výraz CRONU pole. Další informace najdete v tématu [Azure functions článek na čas](/azure/azure-functions/functions-create-scheduled-function)


- **Aktivační událost fronty** – to je funkce, která bude reagovat na zprávy přicházející do fronty Azure Storage. Kromě názvu funkce přebírá Tato šablona **cesta** (název fronty, ze kterého se bude číst zpráva) a účet úložiště **připojení** (název nastavení aplikace s úložiště připojovací řetězec účtu). Další informace najdete v tématu [článek funkce Azure Queue Storage](/azure/azure-functions/functions-create-storage-queue-triggered-function).

- **Aktivační události služby blob** – když se přidají do kontejneru objektů BLOB Azure Storage procesu. Kromě názvu funkce přijímá tato šablona také vlastnost cesty a připojení. Vlastnost path je cesta v účtu úložiště, kterou bude trigger monitorovat. Účet připojení je název nastavení aplikace, které obsahuje připojovací řetězec účtu úložiště. Další informace najdete v tématu [článku úložiště objektů Blob v Azure functions](/azure/azure-functions/functions-create-storage-blob-triggered-function).

- **Obecný WebHook** – Toto je jednoduchá funkce, která se spustí pokaždé, když přijme požadavek z jakékoli služby, která podporuje webhooky. Další informace najdete v tématu [Azure functions článek na obecný webhook](/azure/azure-functions/functions-create-generic-webhook-triggered-function).

- **Odolná služba functions Orchestrace** – Durable Functions umožňují napsat stavové funkce v prostředí bez serveru. Rozšíření spravuje stav, kontrolní body a restartuje za vás. Další informace najdete v tématu příručky Azure functions na [Durable functions](/azure/azure-functions/durable-functions-overview).

- **Změnu velikosti obrázků** – tato funkce vytvoří Image změněnou velikostí pokaždé, když se do kontejneru přidá objekt blob. Šablona má cestu a připojovací řetězec pro aktivační událost, malý obrázek výstupu a výstup střední image.

- **SAS token** – tato funkce generuje token SAS pro daný název kontejneru a objektu blob služby Azure Storage. Kromě názvu funkce přijímá tato šablona také vlastnost cesty a připojení. Vlastnost path je cesta v účtu úložiště, kterou bude trigger monitorovat. Účet připojení je název nastavení aplikace, které obsahuje připojovací řetězec účtu úložiště. **Přístupová práva** také muset nastavit. Úroveň autorizace určuje, jestli funkce vyžaduje klíč rozhraní API a klávesy, která se použije. Funkce používá klíč funkce; Správce používá váš hlavní klíč. Další informace najdete v tématu [funkce C# Azure generuje tokeny SAS](https://azure.microsoft.com/resources/samples/functions-dotnet-sas-token/) vzorku.