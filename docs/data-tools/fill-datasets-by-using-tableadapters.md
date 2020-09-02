---
title: Vyplnění datových sad pomocí objektů TableAdapter
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 888e2ac47348d7e61d115f51e3ea52d15ea9f447
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282433"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Vyplnění datových sad pomocí objektů TableAdapter

Komponenta TableAdapter vyplní datovou sadu daty z databáze na základě jednoho nebo více dotazů nebo uložených procedur, které zadáte. Objekty TableAdapter může také v databázi provádět přidání, aktualizace a odstranění, aby byly uchovány změny provedené v datové sadě. Můžete také vydávat globální příkazy, které nesouvisí s žádnou konkrétní tabulkou.

> [!NOTE]
> Objekty TableAdapter jsou generovány pomocí návrhářů aplikace Visual Studio. Pokud vytváříte datové sady programově, použijte modul DataAdapter, což je třída rozhraní .NET.

Podrobné informace o operacích TableAdapter můžete přeskočit přímo na jedno z následujících témat:

|Téma|Popis|
|-----------|-----------------|
|[Vytvoření a konfigurace objektů TableAdapter](../data-tools/create-and-configure-tableadapters.md)|Jak používat návrháře k vytváření a konfiguraci objekty TableAdapter|
|[Vytvoření parametrizovaných dotazů TableAdapter](../data-tools/create-parameterized-tableadapter-queries.md)|Jak povolit uživatelům dodávat argumenty TableAdapter procedurám nebo dotazům|
|[Přímý přístup k databázi pomocí objektů TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Jak používat metody DBDirect objekty TableAdapter|
|[Vypnutí omezení při naplňování datové sady](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Jak pracovat s omezeními cizího klíče při aktualizaci dat|
|[Postup rozšiřování funkcí TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Postup přidání vlastního kódu do objekty TableAdapter|
|[Čtení dat XML do datové sady](../data-tools/read-xml-data-into-a-dataset.md)|Jak pracovat s XML|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>TableAdapter – přehled

Objekty TableAdapter jsou komponenty generované návrhářem, které se připojují k databázi, spouštějí dotazy nebo uložené procedury a naplní jejich DataTable daty vrácenými daty. Objekty TableAdapter také odesílají aktualizované údaje z vaší aplikace zpátky do databáze. Můžete spustit libovolný počet dotazů, které chcete mít na TableAdapter, pokud vrátí data, která odpovídají schématu tabulky, ke které je přidružená TableAdapter. Následující diagram ukazuje, jak objekty TableAdapter komunikují s databázemi a dalšími objekty v paměti:

![Tok dat v klientské aplikaci](../data-tools/media/clientdatadiagram.gif)

I když jsou objekty TableAdapter navrhovány pomocí **Návrhář datových sad**, třídy TableAdapter nejsou generovány jako vnořené třídy  <xref:System.Data.DataSet> . Jsou umístěny v samostatných oborech názvů, které jsou specifické pro každou datovou sadu. Například pokud máte datovou sadu s názvem `NorthwindDataSet` , objekty TableAdapter, která jsou asociována s  <xref:System.Data.DataTable> s s, `NorthwindDataSet` by měla být v `NorthwindDataSetTableAdapters` oboru názvů. Pro programový přístup k určitému typu TableAdapter musíte deklarovat novou instanci typu TableAdapter. Příklad:

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>Přidružené schéma DataTable

Při vytváření TableAdapter použijte počáteční dotaz nebo uloženou proceduru k definování schématu asociovaného TableAdapter <xref:System.Data.DataTable> . Tento počáteční dotaz nebo uloženou proceduru spustíte voláním metody TableAdapter `Fill` (která vyplní přidruženého TableAdapter <xref:System.Data.DataTable> ). Všechny změny provedené v hlavním dotazu TableAdapter se projeví ve schématu přidružené tabulky dat. Například odebrání sloupce z hlavního dotazu také odebere sloupec z přidružené tabulky dat. Pokud všechny další dotazy na TableAdapter používají příkazy SQL, které vracejí sloupce, které nejsou v hlavním dotazu, Návrhář se pokusí synchronizovat změny sloupce mezi hlavním dotazem a dalšími dotazy.

## <a name="tableadapter-update-commands"></a>Příkazy TableAdapter Update

Funkce aktualizace TableAdapter závisí na tom, kolik informací je v hlavním dotazu k dispozici v **Průvodci TableAdapter**. Například objekty TableAdapter, které jsou nakonfigurovány pro načtení hodnot z více tabulek (pomocí `JOIN` ), skalární hodnoty, zobrazení nebo výsledky agregačních funkcí nejsou zpočátku vytvořeny s možností odesílat aktualizace zpět do podkladové databáze. Příkazy, a můžete ale nakonfigurovat `INSERT` `UPDATE` `DELETE` ručně v okně **vlastnosti** .

## <a name="tableadapter-queries"></a>TableAdapter – dotazy

![TableAdapter s více dotazy](../data-tools/media/tableadapter.gif)

Objekty TableAdapter může obsahovat více dotazů, aby bylo možné vyplnit přidružené tabulky dat. Objektu TableAdapter lze definovat tolik dotazů, kolik vyžaduje vaše aplikace, pokud každý dotaz vrací data, která odpovídají stejnému schématu jako jeho přidružená tabulka dat. Tato funkce umožňuje TableAdapter načíst různé výsledky na základě různých kritérií.

Například pokud vaše aplikace obsahuje tabulku s názvy zákazníků, můžete vytvořit dotaz, který tabulku vyplní pomocí každého názvu zákazníka, který začíná určitým písmenem, a další, který tabulku vyplní všemi zákazníky, kteří se nacházejí ve stejném stavu. Chcete-li vyplnit `Customers` tabulku zákazníky v daném stavu, můžete vytvořit `FillByState` dotaz, který převezme parametr pro hodnotu stav, následovně: `SELECT * FROM Customers WHERE State = @State` . Spustíte dotaz tak, že zavoláte `FillByState` metodu a předáte hodnotu parametru, například: `CustomerTableAdapter.FillByState("WA")` .

Kromě přidávání dotazů, které vracejí data stejného schématu jako tabulky dat TableAdapter, můžete přidat dotazy, které vracejí skalární (jednoduché) hodnoty. Například dotaz, který vrací počet zákazníků ( `SELECT Count(*) From Customers` ), je platný pro i v případě `CustomersTableAdapter,` , že vrácená data neodpovídají schématu tabulky.

## <a name="clearbeforefill-property"></a>Vlastnost ClearBeforeFill

Ve výchozím nastavení se při každém spuštění dotazu pro vyplnění tabulky dat TableAdapter vymažou stávající data a do tabulky se načtou jenom výsledky dotazu. Nastavte `ClearBeforeFill` vlastnost TableAdapter na, `false` Pokud chcete přidat nebo sloučit data vrácená z dotazu do stávajících dat v tabulce dat. Bez ohledu na to, zda data vymažete, je třeba explicitně odeslat aktualizace zpět do databáze, pokud je chcete zachovat. Nezapomeňte uložit všechny změny dat v tabulce před spuštěním jiného dotazu, který tabulku vyplní. Další informace najdete v tématu [aktualizace dat pomocí TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>TableAdapter dědičnost

Objekty TableAdapter rozšiřuje funkčnost standardních datových adaptérů zapouzdřením nakonfigurované <xref:System.Data.Common.DataAdapter> třídy. Ve výchozím nastavení dědí TableAdapter z <xref:System.ComponentModel.Component> třídy a nemůže být převedena na <xref:System.Data.Common.DataAdapter> třídu. Výsledkem přetypování TableAdapter do <xref:System.Data.Common.DataAdapter> třídy je <xref:System.InvalidCastException> Chyba. Chcete-li změnit základní třídu TableAdapter, můžete určit třídu, která je odvozena z <xref:System.ComponentModel.Component> vlastnosti **základní třídy** TableAdapter v **Návrhář datových sad**.

## <a name="tableadapter-methods-and-properties"></a>Metody a vlastnosti TableAdapter

Třída TableAdapter není typu .NET. To znamená, že ho nemůžete najít v dokumentaci nebo **Prohlížeč objektů**. Je vytvořena v době návrhu při použití některého z průvodců zmíněných výše. Název, který je přiřazen k TableAdapter při jeho vytvoření, je založen na názvu tabulky, se kterou pracujete. Například při vytváření TableAdapter založeného na tabulce v databázi s názvem má `Orders` TableAdapter název `OrdersTableAdapter` . Název třídy TableAdapter lze změnit pomocí vlastnosti **Name** v **Návrhář datových sad**.

Níže jsou uvedené běžně používané metody a vlastnosti objekty TableAdapter:

|Člen|Popis|
|------------|-----------------|
|`TableAdapter.Fill`|Naplní tabulku dat přidruženého k TableAdapter výsledky `SELECT` příkazu TableAdapter.|
|`TableAdapter.Update`|Odešle změny zpět do databáze a vrátí celé číslo představující počet řádků ovlivněných aktualizací. Další informace najdete v tématu [aktualizace dat pomocí TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Vrátí nový <xref:System.Data.DataTable> , který je vyplněn daty.|
|`TableAdapter.Insert`|Vytvoří v tabulce dat nový řádek. Další informace najdete v tématu [vložení nových záznamů do databáze](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|Určuje, zda bude tabulka dat před voláním metody `Fill` vyprázdněna.|

## <a name="tableadapter-update-method"></a>Metoda TableAdapter Update

Objekty TableAdapter používají příkazy pro čtení a zápis dat z databáze. Použijte počáteční `Fill` (hlavní) dotaz TableAdapter jako základ pro vytvoření schématu přidružené datové tabulky a `InsertCommand` `UpdateCommand` příkazů, a, `DeleteCommand` které jsou přidruženy k `TableAdapter.Update` metodě. Voláním metody TableAdapter `Update` se spustí příkazy, které byly vytvořeny při původní konfiguraci TableAdapter, nikoli jeden z dalších dotazů, které jste přidali pomocí **Průvodce konfigurací dotazů TableAdapter**.

Když použijete TableAdapter, efektivně provádí stejné operace s příkazy, které byste obvykle prováděli. Například při volání `Fill` metody adaptéru adaptér spustí datový příkaz ve své `SelectCommand` vlastnosti a pomocí čtečky dat (například <xref:System.Data.SqlClient.SqlDataReader> ) načte sadu výsledků do tabulky dat. Podobně při volání `Update` metody adaptéru spustí příslušný příkaz (ve `UpdateCommand` `InsertCommand` vlastnostech, a `DeleteCommand` ) pro každý změněný záznam v tabulce dat.

> [!NOTE]
> Pokud v hlavním dotazu není k dispozici dostatek informací, příkazy `InsertCommand`, `UpdateCommand` a `DeleteCommand` jsou vytvořeny jako výchozí při generování objektu TableAdapter. Pokud je hlavní dotaz TableAdapter více než jedna tabulka `SELECT` , je možné, že návrhář nebude moci generovat `InsertCommand` , `UpdateCommand` a `DeleteCommand` . Pokud tyto příkazy nejsou vygenerovány, může při spuštění metody dojít k chybě `TableAdapter.Update` .

## <a name="tableadapter-generatedbdirectmethods"></a>Vlastnost GenerateDBDirectMethods třídy TableAdapter

Kromě `InsertCommand` , `UpdateCommand` a `DeleteCommand` jsou vytvořeny objekty TableAdapter pomocí metod, které lze spustit přímo proti databázi. Tyto metody ( `TableAdapter.Insert` , `TableAdapter.Update` a) můžete zavolat `TableAdapter.Delete` přímo k manipulaci s daty v databázi. To znamená, že můžete volat tyto jednotlivé metody z kódu místo volání `TableAdapter.Update` pro zpracování vložení, aktualizace a odstranění, které čekají na přidruženou datovou tabulku.

Pokud nechcete vytvořit tyto přímé metody, nastavte vlastnost **GenerateDBDirectMethods** TableAdapter na `false` (v okně **vlastnosti** ). Další dotazy, které jsou přidány do TableAdapter, jsou samostatné dotazy – negenerují tyto metody.

## <a name="tableadapter-support-for-nullable-types"></a>Podpora TableAdapter pro typy s možnou hodnotou null

Objekty TableAdapter podporuje typy s možnou hodnotou null `Nullable(Of T)` a `T?` . Další informace o typech s možnou hodnotou null v Visual Basic naleznete v tématu [typy hodnot s možnou hodnotou null](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). Další informace o typech s možnou hodnotou null v jazyce C# naleznete v tématu [Use Types Nullable](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>Odkaz na TableAdapterManager

Ve výchozím nastavení vygeneruje třída TableAdapterManager, když vytvoříte datovou sadu, která obsahuje související tabulky. Chcete-li zabránit vygenerování třídy, změňte hodnotu `Hierarchical Update` vlastnosti DataSet na false. Když přetáhnete tabulku, která má relaci, na návrhovou plochu stránky Windows Form nebo WPF, Visual Studio deklaruje členskou proměnnou třídy. Pokud datovou vazbu nepoužíváte, je nutné ručně deklarovat proměnnou.

Třída TableAdapterManager není typu .NET. Proto je nemůžete v dokumentaci vyhledat. Je vytvořena v době návrhu v rámci procesu vytváření datové sady.

Následující jsou často používané metody a vlastnosti `TableAdapterManager` třídy:

|Člen|Popis|
|------------|-----------------|
|Metoda `UpdateAll`|Uloží všechna data ze všech tabulek dat.|
|`BackUpDataSetBeforeUpdate` majetek|Určuje, zda má být před provedením metody vytvořena záložní kopie datové sady `TableAdapterManager.UpdateAll` . Datového.|
|*TableName* `TableAdapter` majetek|Představuje objekt TableAdapter. Vygenerovaná TableAdapterManager obsahuje vlastnost pro každou `TableAdapter` IT správu. Například datová sada s tabulkou Customers and Orders generuje TableAdapterManager, který obsahuje `CustomersTableAdapter` a `OrdersTableAdapter` Vlastnosti.|
|`UpdateOrder` majetek|Určuje pořadí jednotlivých příkazů INSERT, Update a DELETE. Nastavte tuto hodnotu na jednu z hodnot ve `TableAdapterManager.UpdateOrderOption` výčtu.<br /><br /> Ve výchozím nastavení `UpdateOrder` je nastavená na **InsertUpdateDelete**. To znamená, že vložení, následné aktualizace a následné odstranění jsou prováděny pro všechny tabulky v datové sadě.|

## <a name="security"></a>Zabezpečení

Když použijete datové příkazy s vlastností CommandType nastavenou na <xref:System.Data.CommandType.Text> , pečlivě zkontrolujte informace, které se odesílají z klienta, než je předáte do vaší databáze. Uživatelé se zlými úmysly se můžou pokusit odeslat (vložit) upravené nebo další příkazy SQL za účelem získání neoprávněného přístupu nebo poškození databáze. Před přenosem vstupu uživatele do databáze vždy ověřte, zda jsou informace platné. Osvědčeným postupem je vždy použít parametrizované dotazy nebo uložené procedury, pokud je to možné.

## <a name="see-also"></a>Viz také

- [Nástroje datové sady](../data-tools/dataset-tools-in-visual-studio.md)
