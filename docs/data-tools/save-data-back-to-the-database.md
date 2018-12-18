---
title: Ukládání dat zpět do databáze
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], validating data
- data validation, datasets
- data [Visual Studio], saving
- row version
- updating datasets, constraints
- datasets [Visual Basic], about datasets
- datasets [Visual Basic], merging
- updates, constraints in datasets
- saving data, about saving data
- datasets [Visual Basic], constraints
- TableAdapters
ms.assetid: afe6cb8a-dc6a-428b-b07b-903ac02c890b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e33fa9b6047cbe470702cebdbb27f74d074e460e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916904"
---
# <a name="save-data-back-to-the-database"></a>Ukládání dat zpět do databáze

Datová sada je kopie v paměti data. Pokud upravíte, tato data, je vhodné tyto změny uložit zpět do databáze. Můžete to udělat jedním ze tří způsobů:

- Voláním jedné z `Update` metody třídy TableAdapter

- Voláním jedné z `DBDirect` metody TableAdapter

- Při volání `UpdateAll` metodu na TableAdapterManager, který sada Visual Studio generuje pro vás, když je objekt dataset obsahuje tabulek, které jsou spojené s jinými tabulkami v datové sadě

Pokud datová sada tabulky vaše data svázat s ovládacími prvky na formuláři Windows nebo XAML stránce, architektura datové vazby vykonává všechnu práci za vás.

Pokud jste obeznámeni s objekty TableAdapter, můžete přejít přímo na jednu z těchto témat:

|Téma|Popis|
|-----------|-----------------|
|[Vkládání nových záznamů do databáze](../data-tools/insert-new-records-into-a-database.md)|Provádění aktualizací a vloží pomocí objektů TableAdapter nebo příkaz|
|[Aktualizace dat pomocí objektu TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)|Jak provádět aktualizace pomocí instancí TableAdapter|
|[Hierarchická aktualizace](../data-tools/hierarchical-update.md)|Provádění aktualizací v prvku dataset pomocí dvou nebo více souvisejících tabulek|
|[Zpracování výjimky souběžnosti](../data-tools/handle-a-concurrency-exception.md)|Způsob zpracování výjimek, když dva uživatelé pokoušejí změnit na stejná data v databázi ve stejnou dobu|
|[Postupy: ukládání dat pomocí transakce](../data-tools/save-data-by-using-a-transaction.md)|Jak k uložení dat v transakci pomocí systému. Obor názvů transakcí a objekt TransactionScope|
|[Uložení dat do transakce](../data-tools/save-data-in-a-transaction.md)|Návod, který vytvoří aplikaci Windows Forms k předvedení ukládání dat do databáze v transakci|
|[Uložení dat do databáze (více tabulek)](../data-tools/save-data-to-a-database-multiple-tables.md)|Postup úpravy záznamů a uložit změny do několika tabulek zpět do databáze|
|[Uložení dat z objektu do databáze](../data-tools/save-data-from-an-object-to-a-database.md)|Jak předávat data z objektu, který není v datové sadě k databázi pomocí TableAdapter dbdirect – metody|
|[Ukládání dat pomocí metod TableAdapter DBDirect](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|Jak odesílat dotazy SQL přímo k databázi pomocí TableAdapter|
|[Uložení datové sady ve formátu XML](../data-tools/save-a-dataset-as-xml.md)|Jak uložit datovou sadu do dokumentu XML|

## <a name="two-stage-updates"></a>Dvoufázová aktualizace

Aktualizace zdroje dat je dvoustupňový proces. Prvním krokem je aktualizace datové sady pomocí nové záznamy, změněné záznamy nebo odstraněné záznamy. Pokud vaše aplikace posílá nikdy tyto změny zpět do zdroje dat, pak budete hotovi s aktualizací.

Pokud odešlete změny zpět do databáze, druhý krok je povinný. Pokud nepoužíváte ovládacích prvků vázaných na data, budete muset ručně volat `Update` metoda stejný TableAdapter (nebo datový adaptér), který jste použili při naplnění datové sady. Pro přesun dat z jednoho zdroje dat do jiné nebo aktualizaci více zdrojů dat ale můžete použít také jiný adaptéry, například. Pokud nepoužíváte vytváření datových vazeb a ukládají změny pro tabulky v relaci, budete muset ručně vytvořit instanci proměnné automaticky generovanou `TableAdapterManager` třídy a poté zavolejte jeho `UpdateAll` metoda.

![Koncepční diagram aktualizace datové sady](../data-tools/media/vbdatasetupdates.gif)

Datová sada obsahuje kolekce tabulek, které obsahují kolekce řádků. Pokud chcete později aktualizovat podkladovým zdrojem dat, je nutné použít metody na `DataTable.DataRowCollection` vlastnost při přidávání nebo odstraňování řádků. Tyto metody provádět, který je nezbytný pro aktualizaci zdroje dat řešení change tracking. Při volání `RemoveAt` kolekce řádků vlastnosti, nebude odstranění předávají zpět do databáze.

## <a name="merge-datasets"></a>Sloučení datových sad

Aktualizujete obsah datové sady pomocí *sloučení* ji jinému objektu dataset. To zahrnuje kopírování obsahu *zdroj* datovou sadu do volání datové sady (uvedené jako *cílové* datové sady). Při sloučení datových sad, se přidají nové záznamy v jako zdrojovou datovou sadu do cílový dataset. Kromě toho další sloupce v zdrojová datová sada se přidají do cílový dataset. Sloučení datových sad je užitečné, když máte místní datovou sadu a získání druhé datové sady z jiné aplikace. Je také užitečné při načtení druhé datové sady z komponenty, jako jsou webové služby XML, nebo pokud potřebujete integrovat data z více datových sad.

Při slučování datové sady, můžete předat logický argument (`preserveChanges`), které sděluje, <xref:System.Data.DataSet.Merge%2A> – metoda, jestli se má zachovat existující úpravy v cílové datové sadě. Datové sady spravovat více verzí záznamy, proto je důležité si pamatovat, že se sloučení více než jednu verzi záznamy. Následující tabulka ukazuje, jak je sloučen záznam v dvě datové sady:

|DataRowVersion|Cílový dataset|Zdrojová datová sada|
| - | - | - |
|Původní|James Wilson|James C. Wilson|
|aktuální|Jan Wilson|James C. Wilson|

Volání <xref:System.Data.DataSet.Merge%2A> metoda v předchozí tabulce s `preserveChanges=false targetDataset.Merge(sourceDataset)` má za následek následující data:

|DataRowVersion|Cílový dataset|Zdrojová datová sada|
| - | - | - |
|Původní|James C. Wilson|James C. Wilson|
|aktuální|James C. Wilson|James C. Wilson|

Volání <xref:System.Data.DataSet.Merge%2A> metodu s `preserveChanges = true targetDataset.Merge(sourceDataset, true)` má za následek následující data:

|DataRowVersion|Cílový dataset|Zdrojová datová sada|
| - | - | - |
|Původní|James C. Wilson|James C. Wilson|
|aktuální|Jan Wilson|James C. Wilson|

> [!CAUTION]
> V `preserveChanges = true` scénář, pokud <xref:System.Data.DataSet.RejectChanges%2A> metoda je volána na záznam v datové sadě target a pak vrátí na původní data z *zdroj* datové sady. To znamená, že pokud se pokusíte aktualizovat původní zdroj dat s datovou sadou cíl, nemusí být schopna najít původní řádek aktualizovat. Narušení souběžného zpracování může zabránit tak, že vyplnění jinému objektu dataset pomocí aktualizovaných záznamů ze zdroje dat a potom provádění sloučení, aby se zabránilo narušení souběžného zpracování. (Když jiný uživatel upravuje záznam ve zdroji dat poté, co bylo vyplněno datové sady dojde k narušení souběžného zpracování.)

## <a name="update-constraints"></a>Aktualizovat omezení

Provádět změny existující řádek dat, přidat nebo aktualizovat data v jednotlivých sloupcích. Pokud datová sada obsahuje omezení (jako jsou cizí klíče nebo omezení NULL), je možné, že záznam dočasně lze v chybovém stavu při aktualizaci. To znamená může být v chybovém stavu po dokončení aktualizace jeden sloupec, ale než se ponoříte dalšímu.

Aby se zabránilo narušení předčasné omezení můžete dočasně pozastavit aktualizace omezení. Tato stránka slouží dvěma účelům:

- Chyba zabraňuje vyvolané po dokončení aktualizace jeden sloupec, ale nebyly spuštěny jiné aktualizace.

- Ta brání určitá aktualizace události nebudou vyvolány (události, které se často používají pro ověření).

> [!NOTE]
> Ve Windows Forms, architektuře vazby dat, která je integrována do objektu datagrid pozastaví omezení kontroly až fokus přesunete mimo řádek, a není nutné explicitně volat <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, nebo <xref:System.Data.DataRow.CancelEdit%2A> metody.

Omezení jsou automaticky zakázáno, pokud <xref:System.Data.DataSet.Merge%2A> metoda se vyvolá u datové sady. Po dokončení, pokud existuje jakákoliv omezení u datové sady, který není možné, sloučení <xref:System.Data.ConstraintException> je vyvolána výjimka. V takovém případě <xref:System.Data.DataSet.EnforceConstraints%2A> je nastavena na `false,` a všechna narušení omezení musí být vyřešeny před resetováním <xref:System.Data.DataSet.EnforceConstraints%2A> vlastnost `true`.

Po dokončení aktualizace se můžete znovu povolit kontroly omezení, která také znovu povolí aktualizace události a jejich vyvolá.

Další informace o pozastavení událostí najdete v tématu [vypnutí omezení při naplňování datové sady](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

## <a name="dataset-update-errors"></a>Chyby aktualizace datové sady

Při aktualizaci záznamu v datové sadě je možné k chybě. Například může nechtěně zápisu dat má špatný typ pro sloupec, nebo data, která je příliš dlouhý nebo data, která má nějaký jiný problém integrity. Nebo může být specifické pro aplikaci ověřovací kontroly, které mohou vyvolat vlastní chyby libovolné fázi událost aktualizace. Další informace najdete v tématu [ověření dat v datových sadách](../data-tools/validate-data-in-datasets.md).

## <a name="maintain-information-about-changes"></a>Spravovat informace o změnách

Informace o změnách v datové sadě je udržován dvěma způsoby: označením řádky, které označují, že jste změnili (<xref:System.Data.DataRow.RowState%2A>) a díky uchovávání několika kopií záznamu (<xref:System.Data.DataRowVersion>). Procesy pomocí těchto informací můžete zjistit, co se změnilo v datové sadě a posílat příslušné aktualizace do zdroje dat.

### <a name="rowstate-property"></a>Vlastnost RowState

<xref:System.Data.DataRow.RowState%2A> Vlastnost <xref:System.Data.DataRow> hodnotu, která poskytuje informace o stavu konkrétnímu řádku dat je objekt.

Následující tabulka obsahuje podrobnosti o možných hodnot <xref:System.Data.DataRowState> výčtu:

|Hodnotou DataRowState|Popis|
| - |-----------------|
|<xref:System.Data.DataRowState.Added>|Řádek byl přidán jako položku, která má <xref:System.Data.DataRowCollection>. (Řádek v tomto stavu nemá odpovídající původní verzi, protože neexistovala při poslední <xref:System.Data.DataRow.AcceptChanges%2A> byla volána metoda).|
|<xref:System.Data.DataRowState.Deleted>|Řádek byl odstraněných položek prostřednictvím <xref:System.Data.DataRow.Delete%2A> z <xref:System.Data.DataRow> objektu.|
|<xref:System.Data.DataRowState.Detached>|Řádek byl vytvořen, ale není součástí žádné <xref:System.Data.DataRowCollection>. A <xref:System.Data.DataRow> objektu je v tomto stavu ihned po jeho vytvoření, než byl přidán do kolekce, a poté, co se odebral z kolekce.|
|<xref:System.Data.DataRowState.Modified>|Hodnota sloupce v řádku změnil nějakým způsobem.|
|<xref:System.Data.DataRowState.Unchanged>|Řádek nebyl změněn od <xref:System.Data.DataRow.AcceptChanges%2A> naposledy byla volána.|

### <a name="datarowversion-enumeration"></a>Výčet DataRowVersion

Datové sady spravovat více verzí záznamy. <xref:System.Data.DataRowVersion> Pole se používají při získávání hodnoty najdete v <xref:System.Data.DataRow> pomocí <xref:System.Data.DataRow.Item%2A> vlastnost nebo <xref:System.Data.DataRow.GetChildRows%2A> metodu <xref:System.Data.DataRow> objektu.

Následující tabulka obsahuje podrobnosti o možných hodnot <xref:System.Data.DataRowVersion> výčtu:

|Hodnota DataRowVersion|Popis|
| - |-----------------|
|<xref:System.Data.DataRowVersion.Current>|Aktuální verze záznamu obsahuje všechny změny provedené u záznamu od posledního <xref:System.Data.DataRow.AcceptChanges%2A> byla volána. Pokud řádek byl odstraněn, neexistuje žádná aktuální verze.|
|<xref:System.Data.DataRowVersion.Default>|Výchozí hodnota záznamu, tak jak je definoval zdroj schématu nebo dat datové sady.|
|<xref:System.Data.DataRowVersion.Original>|Původní verze záznamu je kopií záznamu, jako bylo, že byly potvrzeny poslední změny času v datové sadě. V praxi to je obvykle verze záznamu jako přečtená ze zdroje dat.|
|<xref:System.Data.DataRowVersion.Proposed>|Navrhovaná verze záznam, který je k dispozici dočasně, když jste uprostřed aktualizace – tedy mezi časem jste volali <xref:System.Data.DataRow.BeginEdit%2A> metoda a <xref:System.Data.DataRow.EndEdit%2A> metoda. Obvykle přistupujete k navrhovaná verze záznamu v obslužné rutině události, jako <xref:System.Data.DataTable.RowChanging>. Volání <xref:System.Data.DataRow.CancelEdit%2A> metoda vrátí zpět změny a odstraní navrhovaná verze datového řádku.|

Původní a aktuální verze jsou užitečné při ke zdroji dat se přenášejí informace o aktualizacích. Při aktualizaci odeslání do zdroje dat, nové informace o databázi je obvykle v aktuální verze záznamu. Informace z původní verze je používaná k nalezení záznam, který chcete aktualizovat.

Například v případě změnou záznamu primární klíč budete potřebovat způsob, jak najít správný záznam ve zdroji dat za účelem aktualizace provedené změny. Pokud žádná původní verze, pak tento záznam pravděpodobně se připojí ke zdroji dat, což nejen v dalších nežádoucí záznamu, ale jeden záznam, který je nepřesný a aktuální. Dvě verze se používají také v řízení souběžnosti. Můžete porovnat původní verze proti záznamu ve zdroji dat. Chcete-li zjistit, jestli tento záznam se změnila od jeho zavedení do datové sady.

Navrhovaná verze je užitečné, když potřebujete provádět ověření před skutečně potvrzování změn do datové sady.

I v případě, že jste změnili záznamy, nejsou vždy aktuální a původní verzí tohoto řádku. Když vložíte nový řádek do tabulky, neexistuje žádná původní verze na aktuální verzi. Podobně pokud odstraníte řádek v tabulce voláním `Delete` metoda, je původní verze, ale žádná aktuální verze.

Můžete otestovat, jestli existuje konkrétní verze záznamu pomocí dotazu na datovém řádku <xref:System.Data.DataRow.HasVersion%2A> metody. Můžete přistupovat k jedné verze záznamu předáním <xref:System.Data.DataRowVersion> hodnota výčtu jako volitelný argument, pokud požádáte o hodnotě sloupce.

## <a name="get-changed-records"></a>Získejte změněné záznamy

Je běžnou praxí Neaktualizovat každý záznam v datové sadě. Uživatel například může fungovat s formuláři Windows <xref:System.Windows.Forms.DataGridView> ovládací prvek, který zobrazí mnoho záznamů. Ale uživatel může aktualizovat jenom o pár záznamů toku nějaký tok odstranit a vložit nový. Datové sady a data tabulky poskytují metody (`GetChanges`) pro vrácení pouze řádky, které byly změněny.

Můžete vytvořit podmnožiny změněné záznamy pomocí `GetChanges` metoda tabulky dat (<xref:System.Data.DataTable.GetChanges%2A>) nebo datové sady (<xref:System.Data.DataSet.GetChanges%2A>) sám. Pokud volání metody pro tabulku dat vrátí kopii objektu s pouze změněné záznamy v tabulce. Podobně při volání metody u datové sady, získáte novou datovou sadu s pouze změněné záznamy do něj.

`GetChanges` samotným odebráním vrátí všechny změněné záznamy. Naproti tomu předáním požadované <xref:System.Data.DataRowState> jako parametr `GetChanges` metodu, můžete zadat jaké podmnožinou změněné záznamy, které chcete, aby: nově přidána záznamy, záznamy, které jsou označené k odstranění, odpojit záznamy nebo změněné záznamy.

Získání podmnožiny změněné záznamy je užitečné, když chcete odeslat do jiné součásti pro zpracování záznamů. Místo abyste odesílali celou datovou sadu, můžete snížit režijní náklady tím, že získáme pouze záznamy, které je nutné komponentu komunikovat s jinou součástí.

## <a name="commit-changes-in-the-dataset"></a>Potvrzení změn v datové sadě

Jakmile v datové sadě, jsou provedeny změny <xref:System.Data.DataRow.RowState%2A> změněných řádků je nastavena. Navázat, udržovat a můžete podle aktuální a původní verzí záznamů <xref:System.Data.DataRowView.RowVersion%2A> vlastnost. Metadata, která je uložená ve vlastnosti těchto změněných řádků je nezbytné pro odeslání do zdroje dat správné aktualizace.

Pokud se změny odráží aktuální stav zdroje dat, musíte už udržovat tyto informace. Obvykle jsou k dispozici dvakrát když jsou synchronizované datová sada a zdroj:

- Ihned po informace jste načetli do datové sady, například při čtení dat ze zdroje.

- Po odeslání změn do zdroje dat z datové sady (ale ne dřív, protože by přijít o informace o změně, který je potřeba k odeslání změn do databáze).

Můžete potvrdit čekající změny do datové sady pomocí volání <xref:System.Data.DataSet.AcceptChanges%2A> metody. Obvykle <xref:System.Data.DataSet.AcceptChanges%2A> je volána v následujících časech:

- Po načtení datové sady. Načtení datové sady pomocí volání objektu TableAdapter `Fill` metoda pak adaptér pro vás automaticky provádí změny. Ale pokud načíst datovou sadu sloučením jinému objektu dataset do ní, pak budete muset provést změny ručně.

    > [!NOTE]
    > Adaptér můžete zabránit automaticky potvrzování změny při volání `Fill` metodu tak, že nastavíte `AcceptChangesDuringFill` vlastnosti adaptéru `false`. Pokud je nastavena na `false`, pak bude <xref:System.Data.DataRow.RowState%2A> každého řádku, který je vložen během výplň je nastavena na <xref:System.Data.DataRowState.Added>.

- Po odeslání změn datové sady na jiný proces, jako jsou webové služby XML.

    > [!CAUTION]
    > Provádění změn tímto způsobem se odstraní všechny informace o změně. Není změny provést až po můžete dokončit, provádění operací, které vyžadují vaše aplikace vědět, jaké změny byly provedeny v datové sadě.

Tato metoda provede následující akce:

- Zapíše <xref:System.Data.DataRowVersion.Current> verze záznamu do jeho <xref:System.Data.DataRowVersion.Original> verze a přepíše původní verze.

- Odebere všechny řádky kde <xref:System.Data.DataRow.RowState%2A> je nastavena na <xref:System.Data.DataRowState.Deleted>.

- Nastaví <xref:System.Data.DataRow.RowState%2A> vlastnosti záznamu, <xref:System.Data.DataRowState.Unchanged>.

<xref:System.Data.DataSet.AcceptChanges%2A> Metoda je k dispozici ve třech úrovních. Můžete volat na <xref:System.Data.DataRow> změny objektu na potvrzení pro právě tento řádek. Můžete ji volat i na <xref:System.Data.DataTable> objekt potvrďte všechny řádky v tabulce. Nakonec můžete volat na <xref:System.Data.DataSet> objekt potvrďte všechny probíhající změny ve všech záznamech všech tabulek datové sadě.

Následující tabulka popisuje, jaké změny jsou potvrzeny na co objektu, že metoda je volána na základě:

|Metoda|Výsledek|
|------------|------------|
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Změny jsou potvrzeny jenom na konkrétní řádek.|
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Změny jsou potvrzeny při všech řádků v tabulce konkrétní.|
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Změny jsou potvrzeny při všech řádků ve všech tabulkách datové sady.|

> [!NOTE]
> Načtení datové sady pomocí volání objektu TableAdapter `Fill` metody, není nutné explicitně přijetí změn. Ve výchozím nastavení `Fill` volání metody `AcceptChanges` metoda po vyplnění tabulky dat.

Související metody <xref:System.Data.DataSet.RejectChanges%2A>, vrátí zpět změny tak, že zkopírujete <xref:System.Data.DataRowVersion.Original> verze zpět do <xref:System.Data.DataRowVersion.Current> verze záznamů. Také nastaví <xref:System.Data.DataRow.RowState%2A> z každého záznamu zpět a <xref:System.Data.DataRowState.Unchanged>.

## <a name="data-validation"></a>Ověřování dat

Pokud chcete ověřit, jestli data ve vaší aplikaci splňuje požadavky na procesy, které je předáno, často nutné přidat ověřování. To může zahrnovat, ujistěte se, že uživatelský vstup ve formě správné ověřování dat odesílaných do vaší aplikace v jiné aplikaci, nebo dokonce kontroluje se, že informace, které se počítá v rámci vaší komponentě spadá do omezení zdroje dat. a požadavky na aplikace.

Můžete ověřit data několika způsoby:

- V obchodní vrstvě, přidáním kódu do vaší aplikace ověřit data. Tato datová sada je pohromadě, můžete to provést. Datová sada obsahuje některé z výhod back-end ověřování, jako je například schopnost ověřit změny, jak se změna hodnoty řádků a sloupců. Další informace najdete v tématu [ověření dat v datových sadách](../data-tools/validate-data-in-datasets.md).

- V prezentační vrstvě podle Přidání ověření do formuláře. Další informace najdete v tématu [uživatelského vstupu ověřování ve Windows Forms](/dotnet/framework/winforms/user-input-validation-in-windows-forms).

- V datech back-endu, díky odesílání dat do zdroje dat – například databáze a díky kterému jej následně přijímal nebo odmítal data. Při práci s databází, která má pokročilé funkce pro ověřování dat a poskytuje informace o chybě, to může být praktický, protože data bez ohledu na to, odkud můžete ověřit. Tento přístup však nemusí podle požadavků ověřování konkrétní aplikace. Kromě toho s ověření dat zdroje dat může způsobit řadu zpátečních cest ke zdroji dat, v závislosti na tom, jak vaše aplikace usnadňuje řešení chyb ověřování vyvolané back-endu.

   > [!IMPORTANT]
   > Při použití dat příkazech <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> vlastnost, která je nastavena na <xref:System.Data.CommandType.Text>, pečlivě zkontrolujte informace, které se odesílají z klienta před předáním k vaší databázi. Uživatelé se zlými úmysly může pokusu o odeslání (Vložit) změněné nebo další příkazy SQL ve snaze o získání neoprávněného přístupu nebo poškození databáze. Před přenosem vstupu uživatele na databázi vždy ověřte, že informace platné. Je osvědčeným postupem je vždy používejte parametrizovaných dotazů nebo uložených procedur, pokud je to možné.

## <a name="transmit-updates-to-the-data-source"></a>Odesílání aktualizací do zdroje dat.

Po provedení změn v datové sadě, můžete přenést změny do zdroje dat. Nejčastěji to provedete voláním `Update` metody třídy TableAdapter (nebo datový adaptér). Metoda cyklicky projde každý záznam v tabulce dat, určuje, jaký typ aktualizace je povinný (aktualizace, vložení nebo odstranění), pokud existuje, a poté je spuštěn příslušný příkaz.

Jako ilustraci, jak jsou provedeny aktualizace Předpokládejme, že vaše aplikace používá datovou sadu, která obsahuje jednu datovou tabulku. Aplikace načte dva řádky z databáze. Po načtení tabulka v paměti dat vypadá například takto:

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Unchanged)    c400         Nancy Buchanan    Pending
```

Vaše aplikace změní stav Nancy Novák "Preferovaný." V důsledku této změny hodnoty <xref:System.Data.DataRow.RowState%2A> změní vlastnost pro tento řádek z <xref:System.Data.DataRowState.Unchanged> k <xref:System.Data.DataRowState.Modified>. Hodnota <xref:System.Data.DataRow.RowState%2A> vlastnosti prvního řádku zůstává <xref:System.Data.DataRowState.Unchanged>. Tabulka dat nyní vypadá takto:

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Modified)     c400         Nancy Buchanan    Preferred
```

Vaše aplikace teď volá `Update` metoda přenášet datové sady do databáze. Metoda pak zkontroluje každý řádek. Prvního řádku metodu přenáší žádný příkaz SQL na databázi, protože tento řádek se nezměnila, protože byl původně načtených z databáze.

Pro druhý řádek, ale `Update` metoda automaticky vyvolá příkaz správná data a odešle ji do databáze. Určité syntaxe příkazu jazyka SQL, závisí na dialekt SQL, který podporuje základnímu úložišti dat. Ale stojí následující obecné vlastnosti přenášená příkazu SQL:

- Přenášená příkaz jazyka SQL je příkazu UPDATE. Adaptér mohl použít příkazu UPDATE, protože hodnota <xref:System.Data.DataRow.RowState%2A> vlastnost <xref:System.Data.DataRowState.Modified>.

- Přenášená příkaz jazyka SQL obsahuje klauzuli WHERE označující, že je cílem příkazu UPDATE na řádku kde `CustomerID = 'c400'`. Tuto část příkazu SELECT cílový řádek odlišuje od všech ostatních vzhledem k tomu, `CustomerID` je primárním klíčem cílové tabulky. Informace pro klauzuli WHERE je odvozený od původní verze záznamu (`DataRowVersion.Original`), v případě, že jste změnili hodnoty, které jsou nutné k identifikaci řádku.

- Přenášená příkaz jazyka SQL obsahuje klauzuli SET k nastavení nových hodnot položek upravené sloupce.

   > [!NOTE]
   > Pokud objektu TableAdapter `UpdateCommand` vlastnost byla nastavena na název uložené procedury, adaptér konstruovat příkazu SQL. Místo toho volá uloženou proceduru s příslušnými parametry předané.

## <a name="pass-parameters"></a>Předávání parametrů

Obvykle použijete parametry k předání hodnot pro záznamy, které se chystáte aktualizovat v databázi. Při objektu TableAdapter `Update` spuštěním příkazu UPDATE metody, je potřeba zadat hodnoty parametrů. Získá tyto hodnoty z `Parameters` kolekce pro příkaz příslušná data – v takovém případě `UpdateCommand` objekt v objektu TableAdapter.

Pokud jste použili ke generování datový adaptér nástroje sady Visual Studio `UpdateCommand` objekt obsahuje kolekci parametrů, které odpovídají každý parametr zástupný symbol v příkazu.

<xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> Vlastnost každý parametr odkazuje na sloupec v datové tabulce. Například `SourceColumn` vlastnost `au_id` a `Original_au_id` parametrů je nastavena na jakýkoli sloupec v tabulce dat obsahuje id autora. Když adaptéru `Update` spuštěna metoda sloupec id čte Autor z záznam, který se aktualizuje a vyplní hodnot příkazu SELECT.

V příkazu UPDATE musíte zadat oba nové hodnoty (ty, které se zapíšou do záznamu) stejně jako původní hodnoty (tak, aby záznam může být umístěn v databázi). Existují, proto pro každou hodnotu dva parametry: jeden pro klauzuli SET a jinou používat pro klauzuli WHERE. Oba parametry číst data ze záznamu, který se právě aktualizuje, ale získávají různé verze hodnotu ve sloupci podle parametru <xref:System.Data.SqlClient.SqlParameter.SourceVersion> vlastnost. Parametr klauzule SET získá aktuální verzi, a parametrů pro klauzuli WHERE získá původní verze.

> [!NOTE]
> Můžete také nastavit hodnoty `Parameters` kolekce sami v kódu, což by obvykle provést v obslužné rutiny události adaptéru dat <xref:System.Data.DataTable.RowChanging> událostí.

## <a name="see-also"></a>Viz také:

- [Nástroje datových sad v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Vytvoření a konfigurace objektů TableAdapter](create-and-configure-tableadapters.md)
- [Aktualizace dat pomocí objektu TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Ověření dat](validate-data-in-datasets.md)
- [Postupy: Přidání, úpravy a odstranění entit (služeb WCF data services)](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)