---
title: Procházet a spravovat prostředky úložiště pomocí Průzkumníku serveru | Dokumentace Microsoftu
description: Procházení a Správa prostředků úložiště pomocí Průzkumníka serveru
author: ghogen
manager: jillfra
assetId: 658dc064-4a4e-414b-ae5a-a977a34c930d
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/24/2017
ms.author: ghogen
ms.openlocfilehash: 36b2691525eb66bf946317c1bb5254796d5cd639
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74291234"
---
# <a name="browse-and-manage-storage-resources-by-using-server-explorer"></a>Procházení a správa prostředků úložiště pomocí Průzkumníka serveru

[!INCLUDE [storage-try-azure-tools](./includes/storage-try-azure-tools.md)]

## <a name="overview"></a>Přehled

Pokud jste nainstalovali nástroje Azure pro sadu Microsoft Visual Studio, můžete zobrazit objektů blob, fronty a tabulky dat z účtu úložiště Azure. Uzel **úložiště** Azure v Průzkumník serveru zobrazuje data, která jsou v účtu emulátoru místního úložiště a v dalších účtech úložiště Azure.

Chcete-li zobrazit Průzkumník serveru v aplikaci Visual Studio, vyberte v řádku nabídek možnost **zobrazit** > **Průzkumník serveru**. Uzel **úložiště** zobrazí všechny účty úložiště, které existují v rámci každého předplatného nebo certifikátu Azure, ke kterému jste připojení. Pokud se Váš účet úložiště nezobrazí, můžete ho přidat podle pokynů níže [v tomto článku](#add-storage-accounts-by-using-server-explorer).

Od verze Azure SDK 2.7, můžete také pomocí Průzkumníka cloudu můžete zobrazit a spravovat prostředky Azure. Další informace najdete v tématu [Správa prostředků Azure pomocí Průzkumníka cloudu](vs-azure-tools-resources-managing-with-cloud-explorer.md).

## <a name="view-and-manage-storage-resources-in-visual-studio"></a>Umožňuje zobrazit a spravovat prostředky úložiště v sadě Visual Studio

Průzkumník serveru automaticky zobrazí seznam objektů BLOB, frontám a tabulkám v účtu úložiště emulátoru. Účet emulátoru úložiště je uvedený v části Průzkumník serveru pod uzlem **úložiště** jako **vývojový** uzel.

Prostředky účtu emulátoru úložiště zobrazíte tak, že rozbalíte uzel pro **vývoj** . Pokud se emulátor úložiště nespustí, když rozbalíte **vývojový** uzel, automaticky se spustí. Tento proces může trvat několik sekund. Můžete pokračovat v práci v jiných oblastech sady Visual Studio při spuštění emulátoru úložiště.

Pokud chcete zobrazit prostředky v účtu úložiště, rozbalte uzel účtu úložiště v Průzkumník serveru, kde vidíte uzly **BLOB**, **Queues**a **Tables** .

## <a name="work-with-blob-resources"></a>Pracovat s prostředky objektů blob

Uzel **objekty blob** zobrazuje seznam kontejnerů pro vybraný účet úložiště. Kontejnery objektů BLOB obsahují soubory objektů blob a tyto objekty BLOB můžete uspořádat do složek a podsložek. Další informace najdete v tématu [Jak používat úložiště objektů BLOB z rozhraní .NET](/azure/storage/blobs/storage-dotnet-how-to-use-blobs).

### <a name="to-create-a-blob-container"></a>Chcete-li vytvořit kontejner objektů blob

1. Otevřete místní nabídku uzlu **objekty blob** a pak vyberte **vytvořit kontejner objektů BLOB**.
1. V dialogovém okně **vytvořit kontejner objektů BLOB** zadejte název nového kontejneru.  
1. Vyberte možnost Enter na klávesnici nebo můžete kliknutím nebo klepnutím mimo pole názvu pro uložení objektů blob v kontejneru.

   > [!NOTE]
   > Název kontejneru objektu blob musí začínat číslicí (0-9) nebo malým písmenem (a-z).

### <a name="to-delete-a-blob-container"></a>Chcete-li odstranit kontejner objektů blob

Otevřete místní nabídku pro kontejner objektů blob, který chcete odebrat, a pak vyberte **Odstranit**.

### <a name="to-display-a-list-of-the-items-in-a-blob-container"></a>Chcete-li zobrazit seznam položek v kontejneru objektů blob

Otevřete místní nabídku pro název kontejneru objektů BLOB v seznamu a pak vyberte **otevřít**.

Při zobrazení obsahu kontejneru objektů blob, se zobrazí na kartě označuje jako zobrazení objektů blob v kontejneru.

![Zobrazení kontejneru objektů BLOB](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC749016.png)

Pomocí tlačítka v pravém horním rohu zobrazení objektů blob v kontejneru můžete provádět následující operace pro objekty BLOB:

* Zadejte hodnotu filtru a použijte ji.
* Aktualizujte seznam objektů BLOB v kontejneru.
* Nahrajte soubor.
* Odstraňte objekt blob. (Při odstranění souboru z kontejneru objektů blob nedojde k odstranění základního souboru. Pouze odebere ho z kontejneru objektů blob.)
* Otevřete objekt blob.
* Uložte objekt blob do místního počítače.

### <a name="to-create-a-folder-or-subfolder-in-a-blob-container"></a>Chcete-li vytvořit složku nebo podsložku v kontejneru objektů blob

1. Vyberte kontejner objektů blob v Průzkumníku cloudu. V okně kontejner vyberte tlačítko **nahrát objekt BLOB** .

1. V dialogovém okně **nahrát nový soubor** vyberte tlačítko **Procházet** a zadejte soubor, který chcete odeslat, a potom zadejte název složky do pole **Složka (volitelné)** .

   ![Po nahrání souboru do složky objektů blob](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766037.png)

   Můžete přidat podsložky ve složkách kontejneru pomocí stejného kroku. Pokud nezadáte název složky, nahrání souboru na nejvyšší úrovni kontejneru objektů blob. Soubor se zobrazí v určené složce v kontejneru.

   ![Složka přidá do kontejneru objektů blob](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766038.png)

1. Klikněte dvakrát na složku nebo stisknutím klávesy Enter zobrazit obsah složky. Když jste ve složce kontejneru, můžete se vrátit do kořenového adresáře kontejneru tak, že vyberete tlačítko **Otevřít nadřazený adresář** (šipka).

### <a name="to-delete-a-container-folder"></a>Chcete odstranit nějakou složku kontejneru

Odstraňte všechny soubory ve složce.

Protože složky v kontejnerech objektů blob jsou virtuální složky, nelze vytvořit prázdnou složku. Také nelze odstranit složku, do které odstraňte její obsah souboru, ale místo toho musíte odstranit celý obsah složky odstranit samotné složce.

### <a name="to-filter-blobs-in-a-container"></a>Chcete-li filtrovat objekty BLOB v kontejneru

Můžete filtrovat objekty BLOB, které jsou zobrazeny zadáním běžnou předponu.

Pokud například zadáte předponu **Hello** do textového pole Filter a potom vyberete tlačítko **Spustit** ( **!** ), zobrazí se pouze objekty blob začínající na "Hello".

![Filtrovat textové pole](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC519076.png)

Do textového pole filtru je velká a malá písmena a nepodporuje filtrování se zástupnými znaky. Objekty BLOB se dá filtrovat jenom podle předpony. Předpona, která může zahrnovat oddělovač, pokud používáte oddělovač pro uspořádání objektů BLOB v hierarchii virtuální. Například filtrování na této předponě "HelloFabric /" vrátí všechny objekty BLOB, které začínají tento řetězec.

### <a name="to-download-blob-data"></a>Chcete-li stáhnout data objektů blob

V Průzkumníku cloudu použijte některou z následujících metod:

* Otevřete místní nabídku pro jeden nebo více objektů BLOB a pak vyberte **otevřít**.
* Zvolte název objektu BLOB a potom vyberte tlačítko **otevřít** .
* Dvakrát klikněte na název objektu blob.

Průběh stahování objektů BLOB se zobrazí v okně **protokolu aktivit Azure** .

Objekt blob se otevře v editoru výchozí pro daný typ souboru. Pokud operační systém rozpozná typ souboru, soubor se otevře v lokálně nainstalované aplikace. V opačném případě budete vyzváni k výběru aplikace, která je vhodná pro typ souboru objektu blob. Místní soubor, který je vytvořen při stažení objektu blob je určen jen pro čtení.

Data objektů blob je v místní mezipaměti a porovnávána s časem poslední změny objektu blob v úložišti objektů Blob v Azure. Pokud se objekt blob byl aktualizována mezitím než byla naposledy stažena, je stažen znovu. V opačném případě se načte objekt blob z místního disku.

Ve výchozím nastavení se stáhne objekt blob do dočasného adresáře. Chcete-li stáhnout objekty blob do určitého adresáře, otevřete místní nabídku pro vybrané názvy objektů BLOB a vyberte **Uložit jako**. Při ukládání objektu blob tímto způsobem není otevřený soubor objektu blob a místní soubor se vytvoří s atributy pro čtení a zápis.

### <a name="to-upload-blobs"></a>K nahrání objektů BLOB

Pokud chcete nahrát objekty blob, vyberte tlačítko **nahrát objekt BLOB** , když je kontejner otevřený pro zobrazení v zobrazení kontejneru objektů BLOB.

Můžete vybrat jeden nebo více souborů k nahrání a můžete nahrát soubory libovolného typu. V okně **Protokol aktivit Azure** se zobrazuje průběh nahrávání. Další informace o tom, jak pracovat s daty objektů blob, najdete v tématu [Jak používat úložiště objektů BLOB v Azure v .NET](https://go.microsoft.com/fwlink/p/?LinkId=267911).

### <a name="to-view-logs-transferred-to-blobs"></a>Chcete-li zobrazit protokoly přenosu k objektům BLOB

Pokud používáte Azure Diagnostics protokolování dat z aplikace Azure a jste přenesli protokoly do vašeho účtu úložiště, uvidíte kontejnery, které Azure vytvořilo pro tyto protokoly. Zobrazování těchto protokolů v Průzkumníku serveru je snadný způsob, jak identifikovat problémy s vaší aplikací, zejména v případě, že se nasazuje do Azure.

Další informace o Azure Diagnostics najdete v tématu [shromáždění dat protokolování pomocí Azure Diagnostics](https://msdn.microsoft.com/library/azure/gg433048.aspx).

### <a name="to-get-the-url-for-a-blob"></a>Získat adresu URL pro objekt blob

Otevřete místní nabídku objektu BLOB a pak vyberte **Kopírovat adresu URL**.

### <a name="to-edit-a-blob"></a>Chcete-li upravit objekt blob

Vyberte objekt BLOB a pak klikněte na tlačítko **otevřít objekt BLOB** .

Soubor se stáhnou do dočasného umístění a otevřít v místním počítači. Nahrajte objekt blob znovu po provedení změn.

## <a name="work-with-queue-resources"></a>Pracovat s prostředky fronty

Fronty služby Storage jsou hostované v účtu služby Azure storage. Můžete využít k povolení cloudové rolí služby pro komunikaci mezi sebou a s jinými službami předávání zpráv mechanismem. Fronty můžete přistupovat prostřednictvím kódu programu přes cloudovou službu a přes webovou službu pro externí klienty. Fronty můžete také přistupovat přímo pomocí Průzkumníka serveru v sadě Visual Studio.

Když vyvíjíte cloudovou službu, která používá fronty, můžete chtít použít Visual Studio k vytvoření fronty a s nimi interaktivně pracovat při vývoji a testování kódu.

V Průzkumníku serveru můžete zobrazit fronty v účtu úložiště, vytvářet a odstraňovat fronty, otevření fronty k zobrazení jeho zpráv a přidání zpráv do fronty. Při otevření fronty pro zobrazení můžete zobrazit jednotlivé zprávy a můžete provádět následující akce ve frontě pomocí tlačítek v levém horním rohu:

* Aktualizujte zobrazení fronty.
* Přidání zprávy do fronty.
* Odstranit nejvyššího zprávu z fronty.
* Vymažte celou frontu.

Následující obrázek znázorňuje frontu, která obsahuje dvě zprávy:

![Zobrazení fronty](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC651470.png)

Další informace o frontách služby úložiště najdete v tématu [Začínáme s úložištěm Azure Queue pomocí rozhraní .NET](https://go.microsoft.com/fwlink/?LinkID=264702). Informace o webových službách pro fronty služby úložiště najdete v tématu [Koncepty služby Queue](https://go.microsoft.com/fwlink/?LinkId=264788). Informace o tom, jak odesílat zprávy do fronty služby úložiště pomocí sady Visual Studio, najdete v tématu [posílání zpráv do fronty služby úložiště](/azure/visual-studio/vs-storage-cloud-services-getting-started-queues).

> [!NOTE]
> Fronty služby Storage se liší od fronty Azure Service Bus. Další informace o frontách Service Bus najdete v tématu [Service Bus fronty, témata a předplatná](/azure/service-bus-messaging/service-bus-queues-topics-subscriptions).

## <a name="work-with-table-resources"></a>Pracovat s prostředky tabulky

Azure Table storage ukládá velké objemy strukturovaných dat. Tato služba je úložiště dat typu NoSQL, která přijímá ověřených volání z uvnitř i mimo Azure cloud. Jsou ideální pro ukládání strukturovaných, nerelačních dat tabulky Azure.

### <a name="to-create-a-table"></a>Pokud chcete vytvořit tabulku

1. V Průzkumníku cloudu vyberte uzel **tabulky** účtu úložiště a pak vyberte **vytvořit tabulku**.
1. V dialogovém okně **vytvořit tabulku** zadejte název tabulky.

### <a name="to-view-table-data"></a>Chcete-li zobrazit data tabulky

1. V Průzkumníku cloudu otevřete uzel **Azure** a pak otevřete uzel **úložiště** .
1. Otevřete uzel účtu úložiště, který vás zajímá, a pak otevřete uzel **tabulky** , kde se zobrazí seznam tabulek pro účet úložiště.
1. Otevřete místní nabídku pro tabulku a pak vyberte **Zobrazit tabulku**.

    ![Tabulku Azure v Průzkumníku řešení](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744165.png)

V tabulce jsou uspořádána podle entity (viz řádky) a vlastnosti (zobrazené sloupce). Například následující obrázek znázorňuje entity v Návrháři tabulek.

### <a name="to-edit-table-data"></a>Chcete-li upravit data v tabulce

V Návrháři tabulky otevřete místní nabídku pro entitu (jeden řádek) nebo vlastnost (jediná buňka) a pak vyberte **Upravit**.

![Přidat nebo upravit entitu tabulky](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC656238.png)

Entity v jedné tabulce nejsou musí mít stejnou sadu vlastnosti (sloupce). Mějte na paměti následující omezení pro prohlížení a úpravy dat tabulky:

* Binární data (`type byte[]`) nemůžete zobrazit ani upravit, ale můžete je Uložit do tabulky.
* Nemůžete upravovat hodnoty **PartitionKey** nebo **RowKey** , protože úložiště tabulek v Azure nepodporuje tuto operaci.
* Vlastnost s názvem **timestamp**nelze vytvořit. Služby Azure storage použijte vlastnost s tímto názvem.
* Pokud zadáte hodnotu **DateTime** , musíte dodržovat formát, který je vhodný pro nastavení oblasti a jazyka vašeho počítače (například mm/dd/rrrr hh: mm: ss [am | PM] pro AMERICKou angličtinu).

### <a name="to-add-entities"></a>Přidání entit

1. V Návrháři tabulky vyberte tlačítko **Přidat entitu** .

    ![Přidání tlačítka Entity](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655336.png)

1. V dialogovém okně **Přidat entitu** zadejte hodnoty vlastností **PartitionKey** a **RowKey** .

    ![Přidat entitu – dialogové okno](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655335.png)

    Zadejte hodnoty pečlivě. Nelze je změnit po zavření dialogových oken, není-li odstranit entitu a potom ho znovu přidejte.

### <a name="to-filter-entities"></a>Chcete-li filtrovat entity

Můžete přizpůsobit sadu entit, které se zobrazí v tabulce v případě, že pomocí Tvůrce dotazů.

1. Chcete-li otevřít Tvůrce dotazů, otevřete na tabulku pro zobrazení.
1. Na panelu nástrojů v zobrazení tabulky vyberte tlačítko **Tvůrce dotazů** .

    Zobrazí se dialogové okno **Tvůrce dotazů** . Následující obrázek znázorňuje dotaz, který má být sestaven v editoru dotazů.

    ![Tvůrce dotazů](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC652231.png)
1. Po dokončení sestavení dotazu, zavřete dialogové okno. Výsledný text formulář dotazu se zobrazí v textovém poli jako filtr datových služeb WCF.
1. Spusťte dotaz, vyberte ikonu zelený trojúhelník.

Můžete také filtrovat data entity, které se zobrazí v Návrháři tabulek Pokud zadáte řetězec filtru služeb WCF Data Services přímo do textového pole filtru. Tento typ řetězce je podobná klauzuli WHERE příkazu SQL, ale je odeslána na server jako požadavek HTTP. Informace o tom, jak vytvořit řetězce filtru, naleznete v tématu [konstrukce řetězců filtru pro návrháře tabulky](/azure/vs-azure-tools-table-designer-construct-filter-strings).

Následující obrázek znázorňuje příklad řetězce platný filtr:

![Řetězec filtru](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655337.png)

## <a name="refresh-storage-data"></a>Aktualizace úložiště dat

Pokud Průzkumník serveru se připojí k nebo získá data z účtu úložiště, operace může trvat až jednu minutu na dokončení. Pokud se Průzkumník serveru nemůže připojit, může časový limit operace trvat. Při načítání dat můžete pokračovat v práci v jiných částech sady Visual Studio. Pokud chcete operaci zrušit, pokud trvá moc dlouho, vyberte na panelu nástrojů Průzkumník serveru tlačítko **Zastavit aktualizaci** .

### <a name="to-refresh-blob-container-data"></a>Aktualizovat data objektů blob v kontejneru

* V části **úložiště**vyberte uzel **objekty blob** a pak na panelu nástrojů Průzkumník serveru vyberte tlačítko **aktualizovat** .
* Chcete-li aktualizovat seznam objektů blob, které se zobrazí, vyberte tlačítko **Spustit** .

### <a name="to-refresh-table-data"></a>Chcete-li aktualizovat data v tabulce

* V části **úložiště**vyberte uzel **tabulky** a pak na panelu nástrojů Průzkumník serveru vyberte tlačítko **aktualizovat** .
* Chcete-li aktualizovat seznam entit, které jsou zobrazeny v Návrháři tabulky, vyberte v Návrháři tabulky tlačítko **Spustit** .

### <a name="to-refresh-queue-data"></a>Chcete-li aktualizovat data ve frontě

V části **úložiště**vyberte uzel **fronty** a pak na panelu nástrojů Průzkumník serveru vyberte tlačítko **aktualizovat** .

### <a name="to-refresh-all-items-in-a-storage-account"></a>Chcete-li aktualizovat všechny položky v účtu úložiště

Zvolte název účtu a pak na panelu nástrojů Průzkumník serveru vyberte tlačítko **aktualizovat** .

## <a name="add-storage-accounts-by-using-server-explorer"></a>Přidání účtů úložiště pomocí Průzkumníka serveru

Existují dva způsoby, jak přidat účty úložiště pomocí Průzkumníka serveru. Ve vašem předplatném Azure můžete vytvořit účet úložiště, nebo můžete připojit existující účet úložiště.

### <a name="to-create-a-storage-account-by-using-server-explorer"></a>Vytvoření účtu úložiště pomocí Průzkumníka serveru

1. V Průzkumník serveru otevřete místní nabídku uzlu **úložiště** a pak vyberte **vytvořit účet úložiště**.

1. V dialogovém okně **vytvořit účet úložiště** vyberte nebo zadejte následující informace:

   * Předplatné Azure, ke kterému chcete přidat účet úložiště.
   * Název, který chcete použít pro nový účet úložiště.
   * Oblast nebo skupina vztahů (třeba západní USA nebo jihovýchodní Asie).
   * Typ replikace, kterou chcete použít pro účet úložiště, jako místně redundantní.

   ![Vytvoření účtu služby Azure storage](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744166.png)

1. Vyberte **vytvořit**.

Nový účet úložiště se zobrazí v seznamu **úložiště** v Průzkumník řešení.

### <a name="to-attach-an-existing-storage-account-by-using-server-explorer"></a>Připojit existující účet úložiště pomocí Průzkumníka serveru

1. V Průzkumník serveru otevřete místní nabídku uzlu **úložiště** Azure a pak vyberte **připojit externí úložiště**.

    ![Přidání existující účet úložiště](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766039.png)
1. V dialogovém okně **vytvořit účet úložiště** vyberte nebo zadejte následující informace:

   * Název existující účet úložiště, který chcete připojit.
   * Klíč pro vybraný účet úložiště. Tato hodnota se většinou poskytuje vám při výběru účtu úložiště. Pokud chcete, aby aplikace Visual Studio pamatovala klíč účtu úložiště, zaškrtněte políčko **Zapamatovat si klíč účtu** .
   * Protokol, který se má použít pro připojení k účtu úložiště, jako je například HTTP, HTTPS nebo vlastního koncového bodu. Další informace o vlastních koncových bodech naleznete v tématu [How to Configure Connection Strings](https://msdn.microsoft.com/library/azure/ee758697.aspx).

### <a name="to-view-the-secondary-endpoints"></a>Chcete-li zobrazit sekundární koncových bodů

Pokud jste vytvořili účet úložiště pomocí možnosti **geograficky redundantní replikace s přístupem pro čtení** , můžete zobrazit jeho sekundární koncové body otevřením místní nabídky pro název účtu a pak vybrat **vlastnosti**.

![Sekundární koncových bodů úložiště](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766040.png)

### <a name="to-remove-a-storage-account-from-server-explorer"></a>Chcete-li odebrat účet úložiště z Průzkumníka serveru

V Průzkumník serveru otevřete místní nabídku pro název účtu a pak vyberte **Odstranit**. 

Pokud odstraníte účet úložiště, odeberou se také žádné uložené informace o klíči pro tento účet.

Pokud odstraníte účet úložiště z Průzkumníka serveru, to nemá vliv na váš účet úložiště nebo všechna data, která obsahuje. Jednoduše odebere odkaz z Průzkumníka serveru. Pokud chcete účet úložiště trvale odstranit, použijte [Azure Portal](https://portal.azure.com/).

## <a name="next-steps"></a>Další kroky

Další informace o tom, jak používat služby Azure Storage, najdete v tématu [Úvod do Azure Storage](/azure/storage/common/storage-introduction).
