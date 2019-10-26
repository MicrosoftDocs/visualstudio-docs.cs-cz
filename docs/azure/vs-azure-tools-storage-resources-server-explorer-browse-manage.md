---
title: Procházení a Správa prostředků úložiště pomocí Průzkumník serveru | Microsoft Docs
description: Procházení a Správa prostředků úložiště pomocí Průzkumník serveru
author: ghogen
manager: jillfra
assetId: 658dc064-4a4e-414b-ae5a-a977a34c930d
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/24/2017
ms.author: ghogen
ms.openlocfilehash: ad7d2ca7738d4ba0e05e3a75a2a4b6b155e46dbd
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911696"
---
# <a name="browse-and-manage-storage-resources-by-using-server-explorer"></a>Procházení a správa prostředků úložiště pomocí Průzkumníka serveru

[!INCLUDE [storage-try-azure-tools](./includes/storage-try-azure-tools.md)]

## <a name="overview"></a>Přehled

Pokud jste nainstalovali nástroje Azure pro Microsoft Visual Studio, můžete zobrazit data objektů blob, front a tabulek z účtů úložiště pro Azure. Uzel **úložiště** Azure v Průzkumník serveru zobrazuje data, která jsou v účtu emulátoru místního úložiště a v dalších účtech úložiště Azure.

Chcete-li zobrazit Průzkumník serveru v aplikaci Visual Studio, vyberte v řádku nabídek možnost **zobrazit** > **Průzkumník serveru**. Uzel **úložiště** zobrazí všechny účty úložiště, které existují v rámci každého předplatného nebo certifikátu Azure, ke kterému jste připojení. Pokud se Váš účet úložiště nezobrazí, můžete ho přidat podle pokynů níže [v tomto článku](#add-storage-accounts-by-using-server-explorer).

Od verze Azure SDK 2,7 můžete použít také Průzkumníka cloudu k zobrazení a správě prostředků Azure. Další informace najdete v tématu [Správa prostředků Azure pomocí Průzkumníka cloudu](vs-azure-tools-resources-managing-with-cloud-explorer.md).

## <a name="view-and-manage-storage-resources-in-visual-studio"></a>Zobrazení a Správa prostředků úložiště v aplikaci Visual Studio

Průzkumník serveru automaticky zobrazuje seznam objektů blob, front a tabulek v účtu emulátoru úložiště. Účet emulátoru úložiště je uvedený v části Průzkumník serveru pod uzlem **úložiště** jako **vývojový** uzel.

Prostředky účtu emulátoru úložiště zobrazíte tak, že rozbalíte uzel pro **vývoj** . Pokud se emulátor úložiště nespustí, když rozbalíte **vývojový** uzel, automaticky se spustí. Tento proces může trvat několik sekund. Během spouštění emulátoru úložiště můžete pokračovat v práci v jiných oblastech sady Visual Studio.

Pokud chcete zobrazit prostředky v účtu úložiště, rozbalte uzel účtu úložiště v Průzkumník serveru, kde vidíte uzly **BLOB**, **Queues**a **Tables** .

## <a name="work-with-blob-resources"></a>Práce s prostředky objektů BLOB

Uzel **objekty blob** zobrazuje seznam kontejnerů pro vybraný účet úložiště. Kontejnery objektů BLOB obsahují soubory objektů BLOB a tyto objekty blob můžete uspořádat do složek a podsložek. Další informace najdete v tématu [Jak používat úložiště objektů BLOB z rozhraní .NET](/azure/storage/blobs/storage-dotnet-how-to-use-blobs).

### <a name="to-create-a-blob-container"></a>Vytvoření kontejneru objektů BLOB

1. Otevřete místní nabídku uzlu **objekty blob** a pak vyberte **vytvořit kontejner objektů BLOB**.
1. V dialogovém okně **vytvořit kontejner objektů BLOB** zadejte název nového kontejneru.
1. Na své klávesnici vyberte Enter nebo můžete kliknutím nebo klepnutím mimo pole název Uložit kontejner objektů BLOB.

   > [!NOTE]
   > Název kontejneru objektů BLOB musí začínat číslicí (0-9) nebo malým písmenem (a-z).

### <a name="to-delete-a-blob-container"></a>Odstranění kontejneru objektů BLOB

Otevřete místní nabídku pro kontejner objektů blob, který chcete odebrat, a pak vyberte **Odstranit**.

### <a name="to-display-a-list-of-the-items-in-a-blob-container"></a>Zobrazení seznamu položek v kontejneru objektů BLOB

Otevřete místní nabídku pro název kontejneru objektů BLOB v seznamu a pak vyberte **otevřít**.

Když zobrazíte obsah kontejneru objektů blob, zobrazí se na kartě, která se označuje jako zobrazení kontejneru objektů BLOB.

![Zobrazení kontejneru objektů BLOB](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC749016.png)

Pomocí tlačítek v pravém horním rohu zobrazení kontejneru objektů blob můžete v objektech blob provádět následující operace:

* Zadejte hodnotu filtru a použijte ji.
* Aktualizuje seznam objektů BLOB v kontejneru.
* Nahrajte soubor.
* Odstraní objekt BLOB. (Odstranění souboru z kontejneru objektů BLOB neodstraní příslušný soubor. Odebere ho jenom z kontejneru objektů BLOB.)
* Otevřete objekt BLOB.
* Uložte objekt blob do místního počítače.

### <a name="to-create-a-folder-or-subfolder-in-a-blob-container"></a>Vytvoření složky nebo podsložky v kontejneru objektů BLOB

1. V Průzkumníku cloudu vyberte kontejner objektů BLOB. V okně kontejner vyberte tlačítko **nahrát objekt BLOB** .

1. V dialogovém okně **nahrát nový soubor** vyberte tlačítko **Procházet** a zadejte soubor, který chcete odeslat, a potom zadejte název složky do pole **Složka (volitelné)** .

   ![Nahrání souboru do složky objektů BLOB](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766037.png)

   Podsložky můžete přidat do složek kontejneru pomocí stejného kroku. Pokud nezadáte název složky, soubor se nahraje na nejvyšší úroveň kontejneru objektů BLOB. Soubor se zobrazí v zadané složce v kontejneru.

   ![Složka přidaná do kontejneru objektů BLOB](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766038.png)

1. Dvojím kliknutím na složku nebo výběrem Enter zobrazíte obsah složky. Když jste ve složce kontejneru, můžete se vrátit do kořenového adresáře kontejneru tak, že vyberete tlačítko **Otevřít nadřazený adresář** (šipka).

### <a name="to-delete-a-container-folder"></a>Odstranění složky kontejneru

Odstraňte všechny soubory ve složce.

Vzhledem k tomu, že složky v kontejnerech objektů BLOB jsou virtuálními složkami, nemůžete vytvořit prázdnou složku. Nemůžete také odstranit složku pro odstranění jejího obsahu, ale místo toho je nutné odstranit celý obsah složky, aby se odstranila samotná složka.

### <a name="to-filter-blobs-in-a-container"></a>Filtrování objektů BLOB v kontejneru

Můžete filtrovat objekty blob, které se zobrazí, zadáním společné předpony.

Pokud například zadáte předponu **Hello** do textového pole Filter a potom vyberete tlačítko **Spustit** ( **!** ), zobrazí se pouze objekty blob začínající na "Hello".

![Filtrovat textové pole](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC519076.png)

Textové pole filtru rozlišuje velká a malá písmena a nepodporuje filtrování se zástupnými znaky. Objekty blob lze filtrovat pouze pomocí předpony. Předpona může obsahovat oddělovač, pokud používáte oddělovač k uspořádání objektů BLOB ve virtuální hierarchii. Například filtrování předpony "HelloFabric/" vrátí všechny objekty blob, které začínají daným řetězcem.

### <a name="to-download-blob-data"></a>Stažení dat objektu BLOB

V Průzkumníku cloudu použijte některou z následujících metod:

* Otevřete místní nabídku pro jeden nebo více objektů BLOB a pak vyberte **otevřít**.
* Zvolte název objektu BLOB a potom vyberte tlačítko **otevřít** .
* Dvakrát klikněte na název objektu BLOB.

Průběh stahování objektů BLOB se zobrazí v okně **protokolu aktivit Azure** .

Objekt BLOB se otevře ve výchozím editoru pro daný typ souboru. Pokud operační systém rozpoznává typ souboru, otevře se soubor v lokálně nainstalované aplikaci. Jinak budete vyzváni k výběru aplikace, která je vhodná pro typ souboru objektu BLOB. Místní soubor, který se vytvoří při stažení objektu blob, je označený jen pro čtení.

Data objektů BLOB se ukládají do mezipaměti místně a v úložišti objektů BLOB v Azure se zkontrolují s časem poslední změny objektu BLOB. Pokud se objekt BLOB od posledního stažení aktualizoval, stáhne se znovu. V opačném případě je objekt BLOB načten z místního disku.

Ve výchozím nastavení je objekt BLOB stažený do dočasného adresáře. Chcete-li stáhnout objekty blob do určitého adresáře, otevřete místní nabídku pro vybrané názvy objektů BLOB a vyberte **Uložit jako**. Při ukládání objektu BLOB tímto způsobem není otevřen soubor BLOB a místní soubor je vytvořen s atributy pro čtení a zápis.

### <a name="to-upload-blobs"></a>Nahrání objektů BLOB

Pokud chcete nahrát objekty blob, vyberte tlačítko **nahrát objekt BLOB** , když je kontejner otevřený pro zobrazení v zobrazení kontejneru objektů BLOB.

Můžete vybrat jeden nebo více souborů, které chcete nahrát, a můžete nahrát soubory libovolného typu. V okně **Protokol aktivit Azure** se zobrazuje průběh nahrávání. Další informace o tom, jak pracovat s daty objektů blob, najdete v tématu [Jak používat úložiště objektů BLOB v Azure v .NET](/azure/storage/blobs/storage-quickstart-blobs-dotnet).

### <a name="to-view-logs-transferred-to-blobs"></a>Zobrazení protokolů přenesených do objektů BLOB

Pokud používáte Azure Diagnostics k protokolování dat z aplikace Azure a přenesli jste protokoly do svého účtu úložiště, zobrazí se kontejnery, které Azure vytvořil pro tyto protokoly. Zobrazení těchto protokolů v Průzkumník serveru představuje snadný způsob, jak identifikovat problémy s vaší aplikací, zejména v případě, že je nasazená do Azure.

Další informace o Azure Diagnostics najdete v tématu [shromáždění dat protokolování pomocí Azure Diagnostics](https://msdn.microsoft.com/library/azure/gg433048.aspx).

### <a name="to-get-the-url-for-a-blob"></a>Získání adresy URL pro objekt BLOB

Otevřete místní nabídku objektu BLOB a pak vyberte **Kopírovat adresu URL**.

### <a name="to-edit-a-blob"></a>Úprava objektu BLOB

Vyberte objekt BLOB a pak klikněte na tlačítko **otevřít objekt BLOB** .

Soubor se stáhne do dočasného umístění a otevře se v místním počítači. Po provedení změn znovu nahrajte objekt BLOB.

## <a name="work-with-queue-resources"></a>Práce s prostředky ve frontě

Fronty služby Storage se hostují v účtu úložiště Azure. Můžete je použít k tomu, aby mohly vaše role cloudové služby vzájemně komunikovat a s jinými službami pomocí mechanismu předávání zpráv. Ke frontě se můžete dostat programově prostřednictvím cloudové služby a přes webovou službu pro externí klienty. K frontě můžete přistupovat také přímo pomocí Průzkumník serveru v aplikaci Visual Studio.

Když vyvíjíte cloudovou službu, která používá fronty, můžete pomocí sady Visual Studio vytvořit fronty a interaktivně pracovat s nimi během vývoje a testování kódu.

V Průzkumník serveru můžete zobrazit fronty v účtu úložiště, vytvořit a odstranit fronty, otevřít frontu a zobrazit tak jejich zprávy a přidat zprávy do fronty. Když otevřete frontu pro zobrazení, můžete zobrazit jednotlivé zprávy a ve frontě můžete provádět následující akce pomocí tlačítek v levém horním rohu:

* Aktualizuje zobrazení fronty.
* Přidejte do fronty zprávu.
* Odřadí zprávu nejvyšší úrovně.
* Vymažte celou frontu.

Následující obrázek ukazuje frontu, která obsahuje dvě zprávy:

![Zobrazení fronty](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC651470.png)

Další informace o frontách služby úložiště najdete v tématu [Začínáme s úložištěm Azure Queue pomocí rozhraní .NET](/azure/storage/queues/storage-dotnet-how-to-use-queues). Informace o webových službách pro fronty služby úložiště najdete v tématu [Koncepty služby Queue](/rest/api/storageservices/Queue-Service-Concepts). Informace o tom, jak odesílat zprávy do fronty služby úložiště pomocí sady Visual Studio, najdete v tématu [posílání zpráv do fronty služby úložiště](/azure/visual-studio/vs-storage-cloud-services-getting-started-queues).

> [!NOTE]
> Fronty služby Storage se liší od Azure Service Busch front. Další informace o frontách Service Bus najdete v tématu [Service Bus fronty, témata a předplatná](/azure/service-bus-messaging/service-bus-queues-topics-subscriptions).

## <a name="work-with-table-resources"></a>Práce s prostředky tabulky

Služba Azure Table Storage ukládá velké objemy strukturovaných dat. Služba je úložiště dat NoSQL, které přijímá ověřená volání zevnitř i mimo cloud Azure. Tabulky Azure jsou ideální pro ukládání strukturovaných, nerelačních dat.

### <a name="to-create-a-table"></a>Vytvoření tabulky

1. V Průzkumníku cloudu vyberte uzel **tabulky** účtu úložiště a pak vyberte **vytvořit tabulku**.
1. V dialogovém okně **vytvořit tabulku** zadejte název tabulky.

### <a name="to-view-table-data"></a>Zobrazení dat tabulky

1. V Průzkumníku cloudu otevřete uzel **Azure** a pak otevřete uzel **úložiště** .
1. Otevřete uzel účtu úložiště, který vás zajímá, a pak otevřete uzel **tabulky** , kde se zobrazí seznam tabulek pro účet úložiště.
1. Otevřete místní nabídku pro tabulku a pak vyberte **Zobrazit tabulku**.

    ![Tabulka Azure v Průzkumník řešení](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744165.png)

Tabulka je uspořádána podle entit (zobrazených v řádcích) a vlastnosti (zobrazené ve sloupcích). Například následující ilustrace znázorňuje entity uvedené v Návrháři tabulky.

### <a name="to-edit-table-data"></a>Úprava dat tabulky

V Návrháři tabulky otevřete místní nabídku pro entitu (jeden řádek) nebo vlastnost (jediná buňka) a pak vyberte **Upravit**.

![Přidat nebo upravit entitu tabulky](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC656238.png)

Entity v jedné tabulce nemusejí mít stejnou sadu vlastností (sloupců). Mějte na paměti následující omezení pro zobrazení a úpravy tabulkových dat:

* Binární data (`type byte[]`) nemůžete zobrazit ani upravit, ale můžete je Uložit do tabulky.
* Nemůžete upravovat hodnoty **PartitionKey** nebo **RowKey** , protože úložiště tabulek v Azure nepodporuje tuto operaci.
* Vlastnost s názvem **timestamp**nelze vytvořit. Služby Azure Storage používají vlastnost s tímto názvem.
* Pokud zadáte hodnotu **DateTime** , musíte dodržovat formát, který je vhodný pro nastavení oblasti a jazyka vašeho počítače (například mm/dd/rrrr hh: mm: ss [am | PM] pro AMERICKou angličtinu).

### <a name="to-add-entities"></a>Přidání entit

1. V Návrháři tabulky vyberte tlačítko **Přidat entitu** .

    ![Tlačítko Přidat entitu](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655336.png)

1. V dialogovém okně **Přidat entitu** zadejte hodnoty vlastností **PartitionKey** a **RowKey** .

    ![Přidání entity – dialogové okno](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655335.png)

    Zadejte hodnoty pečlivě. Po zavření dialogového okna je nemůžete změnit, pokud entitu neodstraníte a znovu přidáte.

### <a name="to-filter-entities"></a>Filtrování entit

Pokud používáte Tvůrce dotazů, můžete přizpůsobit sadu entit, které se zobrazí v tabulce.

1. Chcete-li otevřít Tvůrce dotazů, otevřete tabulku pro zobrazení.
1. Na panelu nástrojů v zobrazení tabulky vyberte tlačítko **Tvůrce dotazů** .

    Zobrazí se dialogové okno **Tvůrce dotazů** . Následující ilustrace znázorňuje dotaz, který je sestaven v Tvůrci dotazů.

    ![Tvůrce dotazů](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC652231.png)
1. Až budete hotovi s vytvářením dotazu, zavřete dialogové okno. Výsledný text formuláře dotazu se zobrazí v textovém poli jako filtr WCF Data Services.
1. Chcete-li spustit dotaz, vyberte ikonu zeleného trojúhelníku.

Můžete také filtrovat data entity, která se zobrazí v Návrháři tabulky, pokud zadáte řetězec filtru WCF Data Services přímo do textového pole Filtr. Tento druh řetězce je podobný klauzuli WHERE SQL, ale pošle se na server jako požadavek HTTP. Informace o tom, jak vytvořit řetězce filtru, naleznete v tématu [konstrukce řetězců filtru pro návrháře tabulky](vs-azure-tools-table-designer-construct-filter-strings.md).

Následující ilustrace znázorňuje příklad platného řetězce filtru:

![Řetězec filtru](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655337.png)

## <a name="refresh-storage-data"></a>Aktualizovat data úložiště

Když se Průzkumník serveru připojí k účtu úložiště nebo získá data, může trvat až minutu, než se operace dokončí. Pokud se Průzkumník serveru nemůže připojit, může časový limit operace trvat. Při načítání dat můžete pokračovat v práci v jiných částech sady Visual Studio. Pokud chcete operaci zrušit, pokud trvá moc dlouho, vyberte na panelu nástrojů Průzkumník serveru tlačítko **Zastavit aktualizaci** .

### <a name="to-refresh-blob-container-data"></a>Aktualizace dat kontejneru objektů BLOB

* V části **úložiště**vyberte uzel **objekty blob** a pak na panelu nástrojů Průzkumník serveru vyberte tlačítko **aktualizovat** .
* Chcete-li aktualizovat seznam objektů blob, které se zobrazí, vyberte tlačítko **Spustit** .

### <a name="to-refresh-table-data"></a>Aktualizace dat tabulky

* V části **úložiště**vyberte uzel **tabulky** a pak na panelu nástrojů Průzkumník serveru vyberte tlačítko **aktualizovat** .
* Chcete-li aktualizovat seznam entit, které jsou zobrazeny v Návrháři tabulky, vyberte v Návrháři tabulky tlačítko **Spustit** .

### <a name="to-refresh-queue-data"></a>Aktualizace dat fronty

V části **úložiště**vyberte uzel **fronty** a pak na panelu nástrojů Průzkumník serveru vyberte tlačítko **aktualizovat** .

### <a name="to-refresh-all-items-in-a-storage-account"></a>Aktualizace všech položek v účtu úložiště

Zvolte název účtu a pak na panelu nástrojů Průzkumník serveru vyberte tlačítko **aktualizovat** .

## <a name="add-storage-accounts-by-using-server-explorer"></a>Přidání účtů úložiště pomocí Průzkumník serveru

Existují dva způsoby, jak přidat účty úložiště pomocí Průzkumník serveru. V předplatném Azure můžete vytvořit účet úložiště, nebo můžete připojit existující účet úložiště.

### <a name="to-create-a-storage-account-by-using-server-explorer"></a>Vytvoření účtu úložiště pomocí Průzkumník serveru

1. V Průzkumník serveru otevřete místní nabídku uzlu **úložiště** a pak vyberte **vytvořit účet úložiště**.

1. V dialogovém okně **vytvořit účet úložiště** vyberte nebo zadejte následující informace:

   * Předplatné Azure, do kterého chcete přidat účet úložiště.
   * Název, který chcete použít pro nový účet úložiště.
   * Oblast nebo skupina vztahů (například Západní USA nebo Východní Asie).
   * Typ replikace, kterou chcete použít pro účet úložiště, například místně redundantní.

   ![Vytvoření účtu služby Azure Storage](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744166.png)

1. Vyberte **vytvořit**.

Nový účet úložiště se zobrazí v seznamu **úložiště** v Průzkumník řešení.

### <a name="to-attach-an-existing-storage-account-by-using-server-explorer"></a>Připojení existujícího účtu úložiště pomocí Průzkumník serveru

1. V Průzkumník serveru otevřete místní nabídku uzlu **úložiště** Azure a pak vyberte **připojit externí úložiště**.

    ![Přidává se existující účet úložiště.](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766039.png)
1. V dialogovém okně **vytvořit účet úložiště** vyberte nebo zadejte následující informace:

   * Název existujícího účtu úložiště, který chcete připojit.
   * Klíč pro vybraný účet úložiště Tato hodnota je obvykle k dispozici při výběru účtu úložiště. Pokud chcete, aby aplikace Visual Studio pamatovala klíč účtu úložiště, zaškrtněte políčko **Zapamatovat si klíč účtu** .
   * Protokol, který se má použít pro připojení k účtu úložiště, například HTTP, HTTPS nebo vlastní koncový bod. Další informace o vlastních koncových bodech naleznete v tématu [How to Configure Connection Strings](https://msdn.microsoft.com/library/azure/ee758697.aspx).

### <a name="to-view-the-secondary-endpoints"></a>Zobrazení sekundárních koncových bodů

Pokud jste vytvořili účet úložiště pomocí možnosti **geograficky redundantní replikace s přístupem pro čtení** , můžete zobrazit jeho sekundární koncové body otevřením místní nabídky pro název účtu a pak vybrat **vlastnosti**.

![Sekundární koncové body úložiště](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766040.png)

### <a name="to-remove-a-storage-account-from-server-explorer"></a>Odebrání účtu úložiště z Průzkumník serveru

V Průzkumník serveru otevřete místní nabídku pro název účtu a pak vyberte **Odstranit**.

Když odstraníte účet úložiště, odeberou se taky všechny uložené informace o klíči pro tento účet.

Pokud odstraníte účet úložiště z Průzkumník serveru, nebude to mít vliv na váš účet úložiště ani na žádná data, která obsahuje. Jednoduše odebere odkaz z Průzkumník serveru. Pokud chcete účet úložiště trvale odstranit, použijte [Azure Portal](https://portal.azure.com/).

## <a name="next-steps"></a>Další kroky

Další informace o tom, jak používat služby Azure Storage, najdete v tématu [přístup ke službám Azure Storage](/azure/storage/common/storage-introduction).
