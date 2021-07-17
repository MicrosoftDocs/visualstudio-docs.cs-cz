---
title: Azure Functions na MacOs
description: začínáme s Azure Functions v Visual Studio pro Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 04/02/2021
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.topic: how-to
ms.openlocfilehash: a91c40d0b6fe09aa88c0f3d72d21abde10621b5e
ms.sourcegitcommit: 879b11112c775a1c1dd9ebd4e59a3d0caec84220
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2021
ms.locfileid: "114397184"
---
# <a name="introduction-to-azure-functions"></a>Úvod do Azure Functions

Azure Functions je způsob, jak vytvořit a spustit fragmenty kódu řízené událostmi – – funkce – – v cloudu, aniž by bylo nutné explicitně zřizovat nebo spravovat infrastrukturu. Další informace o službě Azure Functions najdete v [Dokumentaci ke službě Azure Functions](/azure/azure-functions/).

## <a name="requirements"></a>Požadavky

nástroje funkce Azure functions jsou součástí **Visual Studio pro Mac 7,5** a novějších.

K vytváření a nasazování funkcí budete také potřebovat předplatné Azure. Pokud nemáte účet Azure, můžete si ho zdarma zaregistrovat a obdržet 12 měsíců bezplatné oblíbené služby, $200 bezplatný kredit a 25 + vždy bezplatných služeb – > [https://azure.com/free](https://azure.com/free/dotnet) .

## <a name="creating-your-first-azure-functions-project"></a>Vytvoření prvního projektu Azure Functions

1. v Visual Studio pro Mac vyberte **soubor > nové řešení**.
2. v dialogovém okně nový Project v části **cloudový > obecné** vyberte šablonu Azure Functions a klikněte na **další**:

    ![dialogové okno nový Project zobrazující možnost Azure Functions](media/azure-functions-image1.png)

3. Vyberte šablonu počáteční Azure Functions, kterou chcete použít, zadejte název funkce a klikněte na **Další**.

    ![dialog nové Project zobrazující šablony Azure Functions](media/azure-functions-image2.png)

    > [!TIP]
    > I když jsou v sadě Azure Functions běhové prostředí a šablony (CLI) zachované jako dostupné, nevyhnutelně jsou zastaralé. při vytváření nového projektu functions Visual Studio pro Mac zkontroluje aktualizace rozhraní příkazového řádku a upozorní vás, jak je znázorněno na následujícím obrázku. Stačí kliknout na tlačítko a stáhnout aktualizované šablony.
    > ![K dispozici je dialogové okno Nový projekt zobrazující Azure Functions aktualizace.](media/azure-functions-update.png)

    V závislosti na typu vybrané funkce vás na další stránce zobrazí výzva k zadání podrobností, jako jsou například přístupová práva, jak je znázorněno na následujícím obrázku:

    ![dialog nové Project zobrazující další možnost](media/azure-functions-image3.png)

    Další informace o různých typech šablon Azure Functions a vlastnostech vazby vyžadovaných ke konfiguraci jednotlivých šablon najdete v části [Dostupné šablony funkcí](#available-function-templates) . V tomto příkladu používáme Trigger http s přístupovými právy nastavenou na anonymní.

4. Po nastavení parametrů vyberte umístění projektu a klikněte na **vytvořit**.

Visual Studio pro Mac vytvoří projekt .NET Standard s zahrnutou výchozí funkcí. zahrnuje taky NuGet odkazy na celou řadu balíčků **AzureWebJobs** a také **Newtonsoft.Jsna** balíčku.

![editor Visual Studio pro Mac, který zobrazuje značku nové funkce azure functions ze šablony](media/azure-functions-newproj.png)

Nový projekt obsahuje následující soubory:

* **vaše funkce-Name. cs** – Tato třída obsahuje často používaný kód pro funkci, kterou jste vybrali. Obsahuje atribut **Functions** s názvem funkce a atribut triggeru, který určuje, co aktivuje funkci (např. požadavek HTTP). Další informace o metodě funkce najdete v článku [referenční informace pro vývojáře v jazyce C# Azure Functions](/azure/azure-functions/functions-dotnet-class-library) .
* **host.jszapnutý** – tento soubor popisuje globální možnosti konfigurace pro hostitele Functions. Ukázkový soubor a informace o dostupných nastaveních pro tento soubor najdete v [host.jsv referenčních informacích k Azure Functions](/azure/azure-functions/functions-host-json).
* **local.settings.jszapnuto** – tento soubor obsahuje všechna nastavení pro spouštění funkcí místně. Tato nastavení používá Azure Functions Core Tools. Další informace najdete v tématu [soubor místních nastavení](/azure/azure-functions/functions-run-local#local-settings-file) v Azure Functions Core Tools článku.

teď, když jste vytvořili nový projekt Azure Functions v Visual Studio pro Mac, můžete otestovat výchozí funkci aktivovanou protokolem HTTP z místního počítače.

## <a name="testing-the-function-locally"></a>Místní testování funkce

díky podpoře Azure Functions v Visual Studio pro Mac můžete testovat a ladit funkci na místním počítači pro vývoj.

1. pokud chcete funkci místně otestovat, stiskněte tlačítko **spustit** v Visual Studio pro Mac:

    ![Tlačítko Spustit ladění v aplikaci Visual Studio pro Mac](media/azure-functions-run.png)

1. Spuštěním projektu se spustí místní ladění funkce Azure Function a otevře se nové okno terminálu, jak je znázorněno na následujícím obrázku:

    ![okno terminálu zobrazující výstup funkce](media/azure-functions-terminal.png)

    Zkopírujte adresu URL z výstupu.

3. Vložte adresu URL pro požadavek HTTP do panelu adresy prohlížeče. Přidejte řetězec dotazu `?name=<yourname>` na konec adresy URL a spusťte požadavek. Následující obrázek ukazuje odpověď v prohlížeči na místní požadavek GET vrácený funkcí:

    ![požadavek HTTP v prohlížeči](media/azure-functions-httpreq.png)

## <a name="adding-another-function-to-your-project"></a>Přidání další funkce do projektu

Šablony funkcí umožňují rychle vytvářet nové funkce s použitím nejběžnějších aktivačních událostí a šablon. Chcete-li vytvořit jiný typ funkce, postupujte takto:

1. Chcete-li přidat novou funkci, klikněte pravým tlačítkem myši na název projektu a vyberte **přidat > přidat funkci...**:

    ![akce kontextu pro přidání nové funkce](media/azure-functions-addnew.png)

2. V dialogovém okně **Nová funkce Azure** vyberte požadovanou funkci:

    ![nový dialog Azure Functions](media/azure-functions-image4.png)

    Seznam šablon Azure Functions najdete v části [Dostupné šablony funkcí](#available-function-templates) .

Výše uvedený postup můžete použít k přidání dalších funkcí do projektu Function App. Každá funkce v projektu může mít jinou aktivační událost, ale funkce musí mít právě jednu aktivační událost. Další informace najdete v tématu [Azure Functions triggery a koncepty vazeb](/azure/azure-functions/functions-triggers-bindings).

## <a name="publish-to-azure"></a>Publikování do Azure

1. Klikněte pravým tlačítkem na název projektu a vyberte **publikovat > publikovat do Azure**:  ![ místní nabídka s publikováním > publikování do Azure... možnost zvýraznění](media/azure-functions-image5.png)
2. Pokud jste už účet Azure připojili k Visual Studio pro Mac zobrazí se seznam dostupných služeb App Services. Pokud jste se přihlásili, budete vyzváni k tomu.
3. V dialogovém okně **publikovat do Azure App Service** můžete buď vybrat existující službu App Service, nebo vytvořit novou, kliknutím na **Nový**.
4. V dialogovém okně **vytvořit novou App Service** zadejte nastavení:  ![ Nový App Service dialogové okno s poli pro název služby, předplatné, skupinu prostředků a nastavení plánu služeb.](media/azure-functions-image7.png)

    |Nastavení  |Popis  |
    |---------|---------|
    |**Název App Service**|Globálně jedinečný název, který identifikuje vaši novou aplikaci Function App.|
    |**Předplatné**|Předplatné Azure, které se má použít.|
    |**[Skupina prostředků](/azure/azure-resource-manager/resource-group-overview)**|Název skupiny prostředků, ve které chcete vytvořit aplikaci funkcí. Vyberte **+** vytvořit novou skupinu prostředků.|
    |**[Plán služby](/azure/azure-functions/functions-scale)**|Vyberte existující plán nebo vytvořte vlastní plán. Vyberte umístění v oblasti poblíž nebo v blízkosti jiných služeb, ke kterým máte přístup.|

5. Kliknutím na **Další** vytvořte účet úložiště. Modul runtime Functions vyžaduje účet úložiště Azure. Kliknutím na **vlastní** vytvořte účet úložiště pro obecné účely nebo použijte existující:

    ![Nový dialog App Service s výzvou k zadání názvu účtu úložiště](media/azure-functions-image8.png)

6. Kliknutím na **Vytvořit** vytvořte aplikaci funkce a související prostředky v Azure a nasaďte kód projektu funkce.

7. Můžete být vyzváni k zadání dialogového okna během publikování, které vás informují o verzi funkcí Update v Azure. Klikněte na **Ano**:

    ![Vyzvat k aktualizaci nastavení aplikace Azure tak, aby odpovídalo verzi místní funkce? s možností Ano a ne.](media/azure-functions-image12.png)

## <a name="function-app-settings"></a>Nastavení aplikace funkcí

Všechna nastavení, která jste přidali v local.settings.js, musí být přidána také do aplikace Function App v Azure. Tato nastavení nejsou nahrána automaticky při publikování projektu.

Přístup k nastavení aplikace získáte tak, že přejdete na Azure Portal na adrese [https://ms.portal.azure.com/](https://ms.portal.azure.com/) . V části **aplikace Functions** vyberte **aplikace Function** App a zvýrazněte název vaší funkce:

![Nabídka Azure Functions](media/azure-functions-image9.png)

Na kartě **Přehled** vyberte **nastavení aplikace** v části **nakonfigurované funkce**:

![Karta over funkce Azure Functions](media/azure-functions-image10.png)

tady můžete nastavit Nastavení aplikace pro aplikaci function app, kde můžete přidat nová nastavení aplikace nebo upravit stávající:

![oblast nastavení aplikace Azure Portal](media/azure-functions-image11.png)

Možná budete muset nastavit jedno důležité nastavení `FUNCTIONS_EXTENSION_VERSION` . při publikování z Visual Studio pro Mac by tato hodnota měla být nastavená na **beta**.

## <a name="available-function-templates"></a>Dostupné šablony funkcí

- **GitHub Trigger** – reaguje na události, ke kterým dochází ve vašich GitHubch úložištích. Další informace najdete v [článku o Azure Functions GitHub](/azure/azure-functions/functions-create-github-webhook-triggered-function)
  - GitHub – komentář – tato funkce se spustí, když obdrží GitHub webhook pro problém nebo žádost o přijetí změn a přidá komentář.
  - GitHub webhook – tato funkce se spustí, když přijme GitHub webhook.

- **Http** – aktivovat provádění kódu pomocí požadavku HTTP K dispozici jsou explicitní šablony pro následující aktivační události protokolu HTTP:
  - Aktivační událost http
  - Http získat CRUD
  - Http POST – Metoda CRUD
  - Aktivační událost http s parametry

- **Timer** – provede vyčištění nebo jiné úlohy Batch podle předdefinovaného plánu. Tato šablona má dvě pole: název a plán, což je šestý výraz CRON pole. Další informace najdete v [článku o Azure Functions v čase](/azure/azure-functions/functions-create-scheduled-function) .

- **aktivační událost fronty** – jedná se o funkci, která bude reagovat na zprávy, když dorazí do fronty Azure Storage. Kromě názvu funkce Tato šablona přebírá **cestu** (název fronty, ze které se bude číst zpráva) a **připojení** k účtu úložiště (název nastavení aplikace, které obsahuje připojovací řetězec účtu úložiště). Další informace najdete v [Azure Functions článku o Queue Storage](/azure/azure-functions/functions-create-storage-queue-triggered-function).

- **Trigger objektu blob** – proces Azure Storage objekty blob při přidání do kontejneru Kromě názvu funkce Tato šablona také přebírá cestu a vlastnost připojení. Vlastnost Path (cesta) je cesta v účtu úložiště, kterou bude aktivační událost monitorovat. Účet pro připojení je název nastavení aplikace, které obsahuje připojovací řetězec účtu úložiště. další informace najdete v [článku Azure Functions Blob Storage](/azure/azure-functions/functions-create-storage-blob-triggered-function).

- **Obecný Webhook** – jedná se o jednoduchou funkci, která se spustí pokaždé, když přijme žádost od libovolné služby, která podporuje Webhooky. Další informace najdete v [článku o Azure Functions v tématu Obecné Webhooky](/azure/azure-functions/functions-create-generic-webhook-triggered-function).

- **Orchestrace trvalých funkcí** – Durable Functions umožňuje psát stavové funkce v prostředí bez serveru. Toto rozšíření za vás spravuje stav, kontrolní body a restartování. Další informace najdete v průvodci Azure Functions na [trvalých funkcích](/azure/azure-functions/durable-functions-overview).

- **Změna velikosti obrázku** – Tato funkce vytvoří obrázky se změněnou velikostí pokaždé, když se do kontejneru přidá objekt BLOB. Šablona používá cestu a připojovací řetězec pro aktivační událost, malý výstup obrázku a střední výstup obrázku.

- **token sas** – tato funkce generuje token sas pro daný Azure Storage kontejner a název objektu blob. Kromě názvu funkce Tato šablona také přebírá cestu a vlastnost připojení. Vlastnost Path (cesta) je cesta v účtu úložiště, kterou bude aktivační událost monitorovat. Účet pro připojení je název nastavení aplikace, které obsahuje připojovací řetězec účtu úložiště. Je také potřeba nastavit **přístupová práva** . Úroveň autorizace řídí, jestli funkce vyžaduje klíč rozhraní API a který klíč se má použít; Funkce používá klíč funkce. Správce používá přístupový klíč účtu. Další informace najdete v tématu [funkce C# Azure pro vygenerování UKÁZEK SAS tokenů](https://github.com/Azure-Samples/functions-dotnet-sas-token/) .
