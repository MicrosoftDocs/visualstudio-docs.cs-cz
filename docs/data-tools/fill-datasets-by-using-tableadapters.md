---
title: Vyplnění datových sad pomocí objektů TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a79f7b781944bb93a60794e748eefb9375723384
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302236"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Vyplnění datových sad pomocí objektů TableAdapter

Komponenta TableAdapter vyplní datovou sadu daty z databáze na základě jednoho nebo více dotazů nebo uložených procedur, které zadáte. TableAdapters můžete také provádět přidává, aktualizuje a odstraňuje v databázi zachovat změny, které provedete v datové sadě. Můžete také vydat globální příkazy, které nesouvisejí s žádnou konkrétní tabulkou.

> [!NOTE]
> TableAdapters jsou generovány návrháři sady Visual Studio. Pokud vytváříte datové sady programově, použijte DataAdapter, což je třída .NET.

Podrobné informace o operacích TableAdapter můžete přeskočit přímo na jedno z těchto témat:

|Téma|Popis|
|-----------|-----------------|
|[Vytvoření a konfigurace objektů TableAdapter](../data-tools/create-and-configure-tableadapters.md)|Jak pomocí návrhářů vytvořit a nakonfigurovat TableAdapters|
|[Vytvoření parametrizovaných dotazů TableAdapter](../data-tools/create-parameterized-tableadapter-queries.md)|Povolení uživatelům k zadání argumentů procedurám nebo dotazům tableadapter|
|[Přímý přístup k databázi pomocí objektů TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Použití metod Dbdirect tableadapters|
|[Vypnutí omezení při vyplňování datové sady](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Jak pracovat s omezeními cizího klíče při aktualizaci dat|
|[Rozšíření funkcí adaptéru TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Jak přidat vlastní kód do TableAdapters|
|[Čtení dat XML do datové sady](../data-tools/read-xml-data-into-a-dataset.md)|Jak pracovat s XML|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>TableAdapter – přehled

TableAdapters jsou součásti generované návrhářem, které se připojují k databázi, spouštějí dotazy nebo uložené procedury a vyplňují jejich DataTable vrácenými daty. TableAdapters také odesílají aktualizovaná data z vaší aplikace zpět do databáze. Můžete spustit libovolný počet dotazů na TableAdapter tak dlouho, dokud vrátí data, která odpovídá schématu tabulky, ke kterému je přidružen TableAdapter. Následující diagram znázorňuje interakci adaptérů TableAdapter s databázemi a dalšími objekty v paměti:

![Tok dat v klientské aplikaci](../data-tools/media/clientdatadiagram.gif)

Zatímco TableAdapters jsou navrženy s **Návrhářem datové sady**, TableAdapter <xref:System.Data.DataSet>třídy nejsou generovány jako vnořené třídy . Jsou umístěny v samostatných oborech názvů, které jsou specifické pro každou datovou sadu. Například pokud máte datovou `NorthwindDataSet`sadu s názvem , TableAdapters, `NorthwindDataSet` které jsou `NorthwindDataSetTableAdapters` přidruženy s <xref:System.Data.DataTable>v by být v oboru názvů. Pro programový přístup k určitému typu TableAdapter musíte deklarovat novou instanci typu TableAdapter. Například:

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>Přidružené schéma DataTable

Při vytváření TableAdapter, použijte počáteční dotaz nebo uloženou proceduru definovat schéma tableadapter <xref:System.Data.DataTable>přidružené . Spuštění tohoto počátečního dotazu nebo uložené procedury voláním `Fill` metody TableAdapter (která vyplňuje přidružené <xref:System.Data.DataTable>karty TableAdapter). Všechny změny provedené v hlavním dotazu TableAdapter se projeví ve schématu přidružené tabulky dat. Například odebrání sloupce z hlavního dotazu také odebere sloupec z přidružené tabulky dat. Pokud všechny další dotazy na TableAdapter použít příkazy SQL, které vracejí sloupce, které nejsou v hlavním dotazu, návrhář pokusí synchronizovat změny sloupců mezi hlavní dotaz a další dotazy.

## <a name="tableadapter-update-commands"></a>Příkazy aktualizace adaptéru TableAdapter

Funkce aktualizace TableAdapter závisí na tom, kolik informací je k dispozici v hlavním dotazu v **Průvodci adaptérem tableadapter**. Například TableAdapters, které jsou nakonfigurovány pro `JOIN`načtení hodnot z více tabulek (pomocí ), skalární hodnoty, zobrazení nebo výsledky agregačních funkcí nejsou zpočátku vytvořeny s možností odesílat aktualizace zpět do podkladové databáze. V okně **Vlastnosti** `UPDATE`však `DELETE` můžete ručně nakonfigurovat `INSERT`příkazy a příkazy.

## <a name="tableadapter-queries"></a>TableAdapter – dotazy

![TableAdapter s více dotazy](../data-tools/media/tableadapter.gif)

TableAdapters může obsahovat více dotazů k vyplnění jejich přidružené tabulky dat. Objektu TableAdapter lze definovat tolik dotazů, kolik vyžaduje vaše aplikace, pokud každý dotaz vrací data, která odpovídají stejnému schématu jako jeho přidružená tabulka dat. Tato funkce umožňuje TableAdapter načíst různé výsledky na základě různých kritérií.

Pokud například aplikace obsahuje tabulku se jmény zákazníků, můžete vytvořit dotaz, který vyplní tabulku s každým jménem zákazníka, které začíná určitým písmenem, a jiným, který vyplní tabulku všemi zákazníky, kteří jsou umístěni ve stejném stavu. Chcete-li `Customers` vyplnit tabulku se zákazníky v `FillByState` daném stavu, můžete vytvořit dotaz, který `SELECT * FROM Customers WHERE State = @State`přebírá parametr pro hodnotu stavu následujícím způsobem: . Dotaz spustíte voláním `FillByState` metody a předáním hodnoty `CustomerTableAdapter.FillByState("WA")`parametru takto: .

Kromě přidání dotazů, které vracejí data stejného schématu jako tabulka dat tableadapter, můžete přidat dotazy, které vracejí skalární (jediné) hodnoty. Například dotaz, který vrací počet`SELECT Count(*) From Customers`zákazníků ( ) `CustomersTableAdapter,` je platný pro i v případě, že data, která je vrácena neodpovídá schématu tabulky.

## <a name="clearbeforefill-property"></a>ClearBeforeFill, vlastnost

Ve výchozím nastavení při každém spuštění dotazu k vyplnění tabulky dat TableAdapter jsou existující data vymazána a do tabulky jsou načteny pouze výsledky dotazu. Nastavte `ClearBeforeFill` vlastnost TableAdapter na `false` pokud chcete přidat nebo sloučit data, která se vrátila z dotazu na existující data v tabulce dat. Bez ohledu na to, zda vymažete data, je třeba explicitně odeslat aktualizace zpět do databáze, pokud je chcete zachovat. Před spuštěním jiného dotazu, který vyplní tabulku, nezapomeňte tedy uložit všechny změny dat v tabulce. Další informace naleznete v [tématu Aktualizace dat pomocí TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>Dědičnost adaptéru TableAdapter

TableAdapters rozšířit funkce standardních datových adaptérů zapouzdřením nakonfigurované <xref:System.Data.Common.DataAdapter> třídy. Ve výchozím nastavení TableAdapter dědí z <xref:System.ComponentModel.Component> třídy a <xref:System.Data.Common.DataAdapter> nelze přetypovat do třídy. Obsazení TableAdapter do <xref:System.Data.Common.DataAdapter> třídy <xref:System.InvalidCastException> má za následek chybu. Chcete-li změnit základní třídu TableAdapter, můžete zadat <xref:System.ComponentModel.Component> třídu, která je odvozena z vlastnosti **Základní třída** TableAdapter v **Návrháři datové sady**.

## <a name="tableadapter-methods-and-properties"></a>Metody a vlastnosti adaptéru TableAdapter

Třída TableAdapter není typem rozhraní .NET. To znamená, že nemůžete vyhledat v dokumentaci nebo **objekt browser**. Je vytvořen v době návrhu při použití jednoho z průvodců uvedených výše. Název, který je přiřazen k TableAdapter při jeho vytvoření je založen na názvu tabulky, se kterou pracujete. Například při vytváření TableAdapter založené na tabulce v `Orders`databázi s `OrdersTableAdapter`názvem , TableAdapter je pojmenován . Název třídy TableAdapter lze změnit pomocí **name** vlastnost v **Návrhářdatové sady**.

Následují běžně používané metody a vlastnosti tableadapters:

|Člen|Popis|
|------------|-----------------|
|`TableAdapter.Fill`|Naplní přidruženou tabulku dat tableadapter výsledky `SELECT` příkazu TableAdapter.|
|`TableAdapter.Update`|Odešle změny zpět do databáze a vrátí celé číslo, které představuje počet řádků ovlivněných aktualizací. Další informace naleznete v [tématu Aktualizace dat pomocí TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Vrátí nový, <xref:System.Data.DataTable> který je vyplněn daty.|
|`TableAdapter.Insert`|Vytvoří v tabulce dat nový řádek. Další informace naleznete v [tématu Vkládání nových záznamů do databáze](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|Určuje, zda bude tabulka dat před voláním metody `Fill` vyprázdněna.|

## <a name="tableadapter-update-method"></a>Metoda aktualizace adaptéru TableAdapter

Objekty TableAdapter používají příkazy pro čtení a zápis dat z databáze. Použijte `Fill` počáteční (hlavní) dotaz TableAdapter jako základ pro vytvoření schématu přidružené tabulky dat, `InsertCommand`jakož `UpdateCommand`i `DeleteCommand` , a příkazy, které jsou přidruženy k metodě. `TableAdapter.Update` Volání `Update` metody TableAdapter spustí příkazy, které byly vytvořeny při původní konfiguraci tableadapter, nikoli jeden z dalších dotazů, které jste přidali pomocí **Průvodce konfigurací dotazu tableadapter**.

Při použití TableAdapter, efektivně provádí stejné operace s příkazy, které by obvykle provádět. Například při volání `Fill` metody adaptéru adaptér spustí příkaz data `SelectCommand` v jeho vlastnosti a používá <xref:System.Data.SqlClient.SqlDataReader>čtečku dat (například) k načtení sady výsledků do tabulky dat. Podobně při `Update` volání metody adaptéru spustí příslušný příkaz (v `UpdateCommand`, `InsertCommand`a `DeleteCommand` vlastnosti) pro každý změněný záznam v tabulce dat.

> [!NOTE]
> Pokud v hlavním dotazu není k dispozici dostatek informací, příkazy `InsertCommand`, `UpdateCommand` a `DeleteCommand` jsou vytvořeny jako výchozí při generování objektu TableAdapter. Pokud tableAdapter hlavní dotaz je více než `SELECT` jeden příkaz tabulky, je možné, že `InsertCommand`návrhář `UpdateCommand`nebude `DeleteCommand`moci generovat , a . Pokud tyto příkazy nejsou generovány, může se při `TableAdapter.Update` spuštění metody zobrazit chyba.

## <a name="tableadapter-generatedbdirectmethods"></a>Vlastnost GenerateDBDirectMethods třídy TableAdapter

Kromě , `InsertCommand` `UpdateCommand`, `DeleteCommand`a , TableAdapters jsou vytvořeny pomocí metod, které lze spustit přímo proti databázi. Tyto metody (`TableAdapter.Insert`, `TableAdapter.Update`, `TableAdapter.Delete`a ) můžete volat přímo k manipulaci s daty v databázi. To znamená, že můžete volat tyto jednotlivé `TableAdapter.Update` metody z vašeho kódu namísto volání pro zpracování vložení, aktualizace a odstranění, které čekají na vyřízení pro přidružené tabulky dat.

Pokud nechcete vytvářet tyto přímé metody, nastavte vlastnost **GenerateDbDirectMethods** `false` společnosti TableAdapter na (v okně **Vlastnosti).** Další dotazy, které jsou přidány do TableAdapter jsou samostatné dotazy – negenerují tyto metody.

## <a name="tableadapter-support-for-nullable-types"></a>Podpora tableadapter pro typy s možnou hodnotou null

TableAdapters podporují typy `Nullable(Of T)` `T?`s možnou hodnotou null a . Další informace o typech s možnou hodnotou null v jazyce Visual Basic naleznete v [tématu Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). Další informace o typech s možnou hodnotou null v systému C#naleznete v [tématu Použití typů s možnou hodnotou null](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>Reference TableAdapterManager

Ve výchozím nastavení se třída TableAdapterManager generuje při vytváření datové sady, která obsahuje související tabulky. Chcete-li zabránit generování třídy, změňte `Hierarchical Update` hodnotu vlastnosti datové sady na false. Při přetažení tabulky, která má vztah na návrhovou plochu formuláře systému Windows nebo WPF stránky, Visual Studio deklaruje členské proměnné třídy. Pokud nepoužíváte datové vazby, budete muset ručně deklarovat proměnnou.

Třída TableAdapterManager není typem .NET. Proto nelze vyhledat v dokumentaci. Je vytvořen v době návrhu jako součást procesu vytváření datové sady.

Následují často používané metody a vlastnosti `TableAdapterManager` třídy:

|Člen|Popis|
|------------|-----------------|
|Metoda `UpdateAll`|Uloží všechna data ze všech tabulek dat.|
|`BackUpDataSetBeforeUpdate`Vlastnost|Určuje, zda chcete vytvořit záložní kopii datové `TableAdapterManager.UpdateAll` sady před spuštěním metody. Boolean.|
|*vlastnost tableName* `TableAdapter`|Představuje TableAdapter. Generogenovaný TableAdapterManager obsahuje `TableAdapter` vlastnost pro každou spravuje. Například datová sada s tabulka zákazníci a objednávky generuje `CustomersTableAdapter` `OrdersTableAdapter` s TableAdapterManager, který obsahuje a vlastnosti.|
|`UpdateOrder`Vlastnost|Řídí pořadí jednotlivých příkazů vložení, aktualizace a odstranění. Nastavte tuto hodnotu na `TableAdapterManager.UpdateOrderOption` jednu z hodnot ve výčtu.<br /><br /> Ve výchozím `UpdateOrder` nastavení je nastavena na **InsertUpdateDelete**. To znamená, že vloží, pak aktualizace a potom odstraní jsou prováděny pro všechny tabulky v datové sadě.|

## <a name="security"></a>Zabezpečení

Při použití datových příkazů s vlastností <xref:System.Data.CommandType.Text>CommandType nastavenou na , pečlivě zkontrolujte informace odeslané z klienta před jejich předáním do databáze. Uživatelé se zlými úmysly se mohou pokusit odeslat (vložit) upravené nebo další příkazy SQL ve snaze získat neoprávněný přístup nebo poškodit databázi. Před přenosem vstupu uživatele do databáze vždy ověřte, zda jsou informace platné. Osvědčeným postupem je vždy používat parametrizované dotazy nebo uložené procedury, pokud je to možné.

## <a name="see-also"></a>Viz také

- [Nástroje datové sady](../data-tools/dataset-tools-in-visual-studio.md)
