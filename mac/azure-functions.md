---
title: Úvod do Azure Functions
description: Používání funkcí Azure ve Visual Studiu pro Mac.
author: sayedihashimi
ms.author: sayedha
ms.date: 04/02/2019
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.openlocfilehash: dac6a1c53cea8982a75c7b12661c98f2feb37f83
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "73189656"
---
# <a name="introduction-to-azure-functions"></a>Úvod do Azure Functions

Funkce Azure je způsob, jak vytvořit a spustit fragmenty kódu založené na událostech –– funkce – v cloudu, aniž byste museli explicitně zřizovali nebo spravovali infrastrukturu. Další informace o funkcích Azure najdete v [dokumentaci k funkcím Azure](/azure/azure-functions/).

## <a name="requirements"></a>Požadavky

Nástroje funkce Azure jsou součástí **Visual Studia pro Mac 7.5** a novější.

K vytváření a nasazování funkcí potřebujete také předplatné Azure. Pokud nemáte účet Azure, můžete se zaregistrovat ještě dnes zdarma a získat 12 měsíců bezplatných populárních služeb, $ [https://azure.com/free](https://azure.com/free/dotnet)200 bezplatný kredit a 25 + vždy bezplatné služby -> .

## <a name="creating-your-first-azure-functions-project"></a>Vytvoření prvního projektu Azure Functions

1. V Visual Studiu pro Mac vyberte **Soubor > nové řešení**.
2. V dialogovém okně Nový projekt vyberte šablonu Azure Functions v části **Obecné cloudové >** a klikněte na **Další**:

    ![Dialogové okno Nový projekt zobrazující možnost funkcí Azure](media/azure-functions-image1.png)

3. Vyberte počáteční šablonu Funkce Azure, kterou chcete použít, zadejte název funkce a klepněte na tlačítko **Další**.

    ![Dialogové okno Nový projekt zobrazující šablony funkcí Azure](media/azure-functions-image2.png)

    > [!TIP]
    > Zatímco přibalené Azure Functions runtime a šablony (CLI) jsou udržovány jako aktuální, jak je to možné, nevyhnutelně získat zastaralé. Při vytváření nového projektu Functions Visual Studio for Mac zkontroluje aktualizace příkazového příkazu a upozorní vás, jak je znázorněno na obrázku níže. Stačí kliknout na tlačítko pro stažení aktualizovaných šablon.
    > ![K dispozici je dialogové okno Nový projekt zobrazující aktualizace funkcí Azure](media/azure-functions-update.png)

    V závislosti na typu funkce, kterou vyberete, vás další stránka vyzve k zadání podrobností, například přístupových práv, jak je znázorněno na následujícím obrázku:

    ![Dialogové okno Nový projekt zobrazující další možnost](media/azure-functions-image3.png)

    Další informace o různých typech šablon Azure Functions a vlastnostech vazby, které jsou nutné ke konfiguraci jednotlivých šablon, najdete v části [Dostupné šablony funkcí.](#available-function-templates) V tomto příkladu používáme aktivační událost Http s přístupovými právy nastavenými na anonymní.

4. Po nastavení parametrů zvolte umístění projektu a klepněte na **tlačítko Vytvořit**.

Visual Studio pro Mac vytvoří projekt .NET Standard s výchozí funkcí v ceně. Obsahuje také odkazy NuGet na různé balíčky **AzureWebJobs,** stejně jako balíček **Newtonsoft.Json.**

![Editor Visual Studia pro Mac zobrazující zcela novou funkci Azure ze šablony](media/azure-functions-newproj.png)

Nový projekt obsahuje následující soubory:

* **your-function-name.cs** – Tato třída obsahuje často používaný kód pro vybranou funkci. Obsahuje atribut **FunctionName** s názvem funkce a atribut triggeru, který určuje, co spustí funkci (např. požadavek HTTP). Další informace o metodě funkce najdete v [článku s odkazem na vývojáře Azure Functions C#.](/azure/azure-functions/functions-dotnet-class-library)
* **host.json** – tento soubor popisuje možnosti globální konfigurace hostitele Functions. Ukázkový soubor a informace o dostupných nastaveních pro tento soubor naleznete v [odkazu host.json pro funkce Azure](/azure/azure-functions/functions-host-json).
* **local.settings.json** – Tento soubor obsahuje všechna nastavení pro místní spouštění funkcí. Tato nastavení používají nástroje Azure Functions Core Tools. Další informace najdete v [tématu Místní nastavení souboru](/azure/azure-functions/functions-run-local#local-settings-file) v článku Nástroje jádra azure.

Teď, když jste vytvořili nový projekt Azure Functions ve Visual Studiu pro Mac, můžete otestovat výchozí funkci aktivovanou HTTP z místního počítače.

## <a name="testing-the-function-locally"></a>Testování funkce místně

S podporou Azure Functions ve Visual Studiu for Mac můžete testovat a ladit svou funkci v místním vývojovém počítači.

1. Chcete-li svou funkci otestovat místně, stiskněte tlačítko **Spustit** v Sadě Visual Studio pro Mac:

    ![Tlačítko Zahájit ladění ve visual studiu pro Mac](media/azure-functions-run.png)

1. Spuštění projektu spustí místní ladění funkce Azure a otevře nové okno terminálu, jak je znázorněno na následujícím obrázku:

    ![okno terminálu zobrazující výstup funkce](media/azure-functions-terminal.png)

    Zkopírujte adresu URL z výstupu.

3. Vložte adresu URL pro požadavek HTTP do panelu adresy prohlížeče. Přidejte řetězec `?name=<yourname>` dotazu na konec adresy URL a proveďte požadavek. Následující obrázek znázorňuje odpověď v prohlížeči na místní požadavek GET vrácený funkcí:

    ![http požadavek v prohlížeči](media/azure-functions-httpreq.png)

## <a name="adding-another-function-to-your-project"></a>Přidání další funkce do projektu

Šablony funkcí umožňují rychle vytvářet nové funkce s použitím nejběžnějších aktivačních událostí a šablon. Chcete-li vytvořit jiný typ funkce, postupujte takto:

1. Chcete-li přidat novou funkci, klikněte pravým tlačítkem myši na název projektu a vyberte **přidat > přidat funkci...**:

    ![kontextová akce pro přidání nové funkce](media/azure-functions-addnew.png)

2. V dialogovém okně **Nová funkce Azure** vyberte funkci, kterou požadujete:

    ![dialogové okno nové funkce azure](media/azure-functions-image4.png)

    Seznam šablon funkcí Azure je k dispozici v části [Dostupné šablony funkcí.](#available-function-templates)

Pomocí výše uvedeného postupu můžete přidat další funkce do projektu aplikace funkce. Každá funkce v projektu může mít jinou aktivační událost, ale funkce musí mít přesně jednu aktivační událost. Další informace najdete v [tématu Azure Functions aktivační události a vazby koncepty](/azure/azure-functions/functions-triggers-bindings).

## <a name="publish-to-azure"></a>Publikování aplikací do Azure

1. Klikněte pravým tlačítkem myši na název projektu ![a vyberte Publikovat > publikovat do **Azure:** Publikovat do nabídky Azure](media/azure-functions-image5.png)
2. Pokud jste už svůj účet Azure připojili k Visual Studiu for Mac, zobrazí se seznam dostupných aplikačních služeb. Pokud jste se nepřihlásili, budete k tomu vyzváni.
3. V dialogovém okně **Publikovat do služby Azure App Service** můžete buď vybrat existující službu aplikace, nebo vytvořit novou kliknutím na **Nový**.
4. V dialogovém okně **Vytvořit novou službu App Service** zadejte nastavení: ![Publikovat do nabídky Azure.](media/azure-functions-image7.png)

    |Nastavení  |Popis  |
    |---------|---------|
    |**Název služby App Service**|Globálně jedinečný název, který identifikuje vaši novou aplikaci funkcí.|
    |**Předplatné**|Předplatné Azure, které se má použít.|
    |**[Skupina prostředků](/azure/azure-resource-manager/resource-group-overview)**|Název skupiny prostředků, ve které chcete vytvořit aplikaci funkcí. Zvolte, **+** zda chcete vytvořit novou skupinu prostředků.|
    |**[Plán služeb](/azure/azure-functions/functions-scale)**|Zvolte existující plán nebo vytvořte vlastní plán. Zvolte umístění v oblasti ve vašem okolí nebo v blízkosti jiných služeb, ke které vaše funkce přistupují.|

5. Kliknutím na **Další** vytvořte účet úložiště. Modul runtime Functions vyžaduje účet úložiště Azure. Kliknutím na **Vlastní** vytvořte účet úložiště pro obecné účely nebo použijte existující účet:

    ![Možnost publikovat do nabídky Azure](media/azure-functions-image8.png)

6. Kliknutím na **Vytvořit** vytvořte aplikaci funkce a související prostředky v Azure a nasaďte kód projektu funkce.

7. Během publikování se může zobrazit výzva s dialogovým oknem, které vás informuje o "aktualizaci verze funkcí v Azure". Klepněte na tlačítko **Ano**:

    ![Možnost publikovat do nabídky Azure](media/azure-functions-image12.png)

## <a name="function-app-settings"></a>Nastavení aplikace funkcí

Všechna nastavení, která jste přidali v local.settings.json, musí být také přidána do aplikace funkce v Azure. Tato nastavení se při publikování projektu nenahrají automaticky.

Pokud chcete získat přístup k nastavení [https://ms.portal.azure.com/](https://ms.portal.azure.com/)aplikace, přejděte na portál Azure na adrese . V části **Functions Apps**vyberte **Function Apps** a zvýrazněte název funkce:

![nabídka azure functions](media/azure-functions-image9.png)

Na kartě **Přehled** vyberte **nastavení aplikace** v části **Nakonfigurované funkce**:

![Karta Přes funkci azure](media/azure-functions-image10.png)

Zde můžete nastavit nastavení aplikace pro aplikaci funkce, kde můžete přidat nové nastavení aplikace nebo upravit stávající:

![Oblast nastavení aplikace na portálu Azure](media/azure-functions-image11.png)

Jedním z důležitých nastavení, `FUNCTIONS_EXTENSION_VERSION`které budete muset nastavit, je . Při publikování z Visual Studio for Mac by tato hodnota měla být nastavena na **beta**verzi .

## <a name="available-function-templates"></a>Dostupné šablony funkcí

- **GitHub Trigger** – reagujte na události, ke kterým dochází ve vašich úložištích GitHub. Další informace najdete v [článku Funkce Azure na GitHubu.](/azure/azure-functions/functions-create-github-webhook-triggered-function)
  - GitHub komentátor – Tato funkce se spustí, když obdrží github webhook pro problém nebo žádost o přijetí a přidá komentář.
  - GitHub WebHook – Tato funkce se spustí, když obdrží webhook GitHub.

- **HTTP** – Aktivace spuštění kódu pomocí požadavku HTTP. Existují explicitní šablony pro následující aktivační události PROTOKOLU HTTP:
  - Aktivační událost http
  - Http ZÍSKAT CRUD
  - Http POST CRUD
  - Http Trigger s parametry

- **Časovač** – spusťte vyčištění nebo jiné dávkové úlohy podle předdefinovaného plánu. Tato šablona má dvě pole: Název a plán, což je šestičlenný výraz CRON pole. Další informace najdete v [článku funkce Azure na čas](/azure/azure-functions/functions-create-scheduled-function)

- **Fronttrigger** – Toto je funkce, která bude reagovat na zprávy, jakmile dorazí do fronty Azure Storage. Kromě názvu funkce tato šablona přebírá **cestu** (název fronty, ze které bude zpráva číst) a účet úložiště **Připojení** (název nastavení aplikace obsahující připojovací řetězec účtu úložiště). Další informace najdete v [článku funkce Azure na frontové úložiště](/azure/azure-functions/functions-create-storage-queue-triggered-function).

- **Aktivační událost objektu blob** – zpracování objektů BLOB azure při jejich přidání do kontejneru. Kromě názvu funkce tato šablona také přebírá vlastnost cesta a připojení. Vlastnost cesta je cesta v rámci účtu úložiště, který bude monitorovat aktivační událost. Účet připojení je název nastavení aplikace obsahující připojovací řetězec účtu úložiště. Další informace najdete v [článku Azure functions Blob Storage](/azure/azure-functions/functions-create-storage-blob-triggered-function).

- **Obecný WebHook** – Jedná se o jednoduchou funkci, která bude spuštěna vždy, když obdrží požadavek z libovolné služby, která podporuje webhooky. Další informace najdete v [článku funkce Azure na obecné webhooky](/azure/azure-functions/functions-create-generic-webhook-triggered-function).

- **Trvalá orchestrace funkcí** – trvalé funkce umožňují psát stavové funkce v prostředí bez serveru. Toto rozšíření za vás spravuje stav, kontrolní body a restartování. Další informace najdete v příručkách funkcí Azure [na funkce durable](/azure/azure-functions/durable-functions-overview).

- **Resizer obrazu** – Tato funkce vytvoří velikost iobrazek při každém přidání objektu blob do kontejneru. Šablona přebírá cestu a připojovací řetězec pro aktivační událost, výstup malého obrazu a střední výstup obrazu.

- **Token SAS** – tato funkce generuje token SAS pro daný kontejner úložiště Azure a název objektu blob. Kromě názvu funkce tato šablona také přebírá vlastnost cesta a připojení. Vlastnost cesta je cesta v rámci účtu úložiště, který bude monitorovat aktivační událost. Účet připojení je název nastavení aplikace obsahující připojovací řetězec účtu úložiště. **Přístupová práva** je také třeba nastavit. Úroveň autorizace určuje, zda funkce vyžaduje klíč rozhraní API a který klíč má být používán. Funkce používá funkční klávesu; Správce používá váš hlavní klíč. Další informace naleznete v [c# Azure funkce pro generování tokenů SAS](https://github.com/Azure-Samples/functions-dotnet-sas-token/) ukázku.
