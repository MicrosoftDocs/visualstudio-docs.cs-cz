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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: fcecafaa36aabf3249bacf0788c2d19f945ad1b1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648479"
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

I když jsou objekty TableAdapter navrhovány pomocí **Návrhář datových sad**, třídy TableAdapter nejsou generovány jako vnořené třídy <xref:System.Data.DataSet>. Jsou umístěny v samostatných oborech názvů, které jsou specifické pro každou datovou sadu. Například pokud máte datovou sadu s názvem `NorthwindDataSet`, objekty TableAdapter přidružené k <xref:System.Data.DataTable>s v `NorthwindDataSet` by byly v oboru názvů `NorthwindDataSetTableAdapters`. Pro programový přístup k určitému typu TableAdapter musíte deklarovat novou instanci typu TableAdapter. Příklad:

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>Přidružené schéma DataTable

Při vytváření TableAdapter můžete použít počáteční dotaz nebo uloženou proceduru k definování schématu přidružených <xref:System.Data.DataTable>ů TableAdapter. Tento počáteční dotaz nebo uloženou proceduru spustíte voláním metody `Fill` TableAdapter (která vyplní <xref:System.Data.DataTable> přidruženou k TableAdapter). Všechny změny provedené v hlavním dotazu TableAdapter se projeví ve schématu přidružené tabulky dat. Například odebrání sloupce z hlavního dotazu také odebere sloupec z přidružené tabulky dat. Pokud všechny další dotazy na TableAdapter používají příkazy SQL, které vracejí sloupce, které nejsou v hlavním dotazu, Návrhář se pokusí synchronizovat změny sloupce mezi hlavním dotazem a dalšími dotazy.

## <a name="tableadapter-update-commands"></a>Příkazy TableAdapter Update

Funkce aktualizace TableAdapter závisí na tom, kolik informací je v hlavním dotazu k dispozici v **Průvodci TableAdapter**. Například objekty TableAdapter, které jsou nakonfigurovány pro načtení hodnot z více tabulek (pomocí `JOIN`), skalární hodnoty, zobrazení nebo výsledky agregačních funkcí nejsou zpočátku vytvořeny s možností odesílat aktualizace zpět do podkladové databáze. V okně **vlastnosti** však můžete ručně nakonfigurovat příkazy `INSERT`, `UPDATE` a `DELETE`.

## <a name="tableadapter-queries"></a>TableAdapter – dotazy

![TableAdapter s více dotazy](../data-tools/media/tableadapter.gif)

Objekty TableAdapter může obsahovat více dotazů, aby bylo možné vyplnit přidružené tabulky dat. Objektu TableAdapter lze definovat tolik dotazů, kolik vyžaduje vaše aplikace, pokud každý dotaz vrací data, která odpovídají stejnému schématu jako jeho přidružená tabulka dat. Tato funkce umožňuje TableAdapter načíst různé výsledky na základě různých kritérií.

Například pokud vaše aplikace obsahuje tabulku s názvy zákazníků, můžete vytvořit dotaz, který tabulku vyplní pomocí každého názvu zákazníka, který začíná určitým písmenem, a další, který tabulku vyplní všemi zákazníky, kteří se nacházejí ve stejném stavu. Chcete-li vyplnit tabulku `Customers` zákazníky v daném stavu, můžete vytvořit dotaz `FillByState`, který převezme parametr pro hodnotu State následujícím způsobem: `SELECT * FROM Customers WHERE State = @State`. Dotaz spustíte voláním metody `FillByState` a předáním hodnoty parametru, jako je toto: `CustomerTableAdapter.FillByState("WA")`.

Kromě přidávání dotazů, které vracejí data stejného schématu jako tabulky dat TableAdapter, můžete přidat dotazy, které vracejí skalární (jednoduché) hodnoty. Například dotaz, který vrací počet zákazníků (`SELECT Count(*) From Customers`) je platný pro `CustomersTableAdapter,` i v případě, že vracená data neodpovídají schématu tabulky.

## <a name="clearbeforefill-property"></a>Vlastnost ClearBeforeFill

Ve výchozím nastavení se při každém spuštění dotazu pro vyplnění tabulky dat TableAdapter vymažou stávající data a do tabulky se načtou jenom výsledky dotazu. Nastavte vlastnost `ClearBeforeFill` TableAdapter na `false`, pokud chcete přidat nebo sloučit data vrácená z dotazu do stávajících dat v tabulce dat. Bez ohledu na to, zda data vymažete, je třeba explicitně odeslat aktualizace zpět do databáze, pokud je chcete zachovat. Nezapomeňte uložit všechny změny dat v tabulce před spuštěním jiného dotazu, který tabulku vyplní. Další informace najdete v tématu [aktualizace dat pomocí TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>TableAdapter dědičnost

Objekty TableAdapter rozšiřuje funkčnost standardních datových adaptérů zapouzdřením nakonfigurované třídy <xref:System.Data.Common.DataAdapter>. Ve výchozím nastavení dědí TableAdapter z třídy <xref:System.ComponentModel.Component> a nelze ji přetypovat na <xref:System.Data.Common.DataAdapter> třídu. Výsledkem přetypování TableAdapter do <xref:System.Data.Common.DataAdapter> třídy je chyba <xref:System.InvalidCastException>. Chcete-li změnit základní třídu TableAdapter, můžete určit třídu, která je odvozena z <xref:System.ComponentModel.Component> v vlastnosti **základní třídy** TableAdapter v **Návrhář datových sad**.

## <a name="tableadapter-methods-and-properties"></a>Metody a vlastnosti TableAdapter

Třída TableAdapter není typu .NET. To znamená, že ho nemůžete najít v dokumentaci nebo **Prohlížeč objektů**. Je vytvořena v době návrhu při použití některého z průvodců zmíněných výše. Název, který je přiřazen k TableAdapter při jeho vytvoření, je založen na názvu tabulky, se kterou pracujete. Například při vytváření TableAdapter založeného na tabulce v databázi s názvem `Orders` je TableAdapter pojmenován `OrdersTableAdapter`. Název třídy TableAdapter lze změnit pomocí vlastnosti **Name** v **Návrhář datových sad**.

Níže jsou uvedené běžně používané metody a vlastnosti objekty TableAdapter:

|Člen|Popis|
|------------|-----------------|
|`TableAdapter.Fill`|Naplní tabulku dat přidružené k TableAdapter výsledky příkazu pro `SELECT` TableAdapter.|
|`TableAdapter.Update`|Odešle změny zpět do databáze a vrátí celé číslo představující počet řádků ovlivněných aktualizací. Další informace najdete v tématu [aktualizace dat pomocí TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Vrátí nový <xref:System.Data.DataTable> vyplněný daty.|
|`TableAdapter.Insert`|Vytvoří v tabulce dat nový řádek. Další informace najdete v tématu [vložení nových záznamů do databáze](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|Určuje, zda bude tabulka dat před voláním metody `Fill` vyprázdněna.|

## <a name="tableadapter-update-method"></a>Metoda TableAdapter Update

Objekty TableAdapter používají příkazy pro čtení a zápis dat z databáze. Jako základ pro vytvoření schématu přidružené datové tabulky TableAdapter použijte dotaz počáteční `Fill` (hlavní) a také příkazy `InsertCommand`, `UpdateCommand` a `DeleteCommand`, které jsou spojeny s metodou `TableAdapter.Update`. Voláním metody `Update` TableAdapter spustí příkazy, které byly vytvořeny při původní konfiguraci TableAdapter, nikoli jeden z dalších dotazů, které jste přidali pomocí **Průvodce konfigurací dotazů TableAdapter**.

Když použijete TableAdapter, efektivně provádí stejné operace s příkazy, které byste obvykle prováděli. Když například voláte metodu `Fill` adaptéru, adaptér spustí datový příkaz ve své vlastnosti `SelectCommand` a pomocí čtecího modulu dat (například <xref:System.Data.SqlClient.SqlDataReader>) načte sadu výsledků do tabulky dat. Podobně při volání metody `Update` adaptéru spustí příslušný příkaz (ve vlastnostech `UpdateCommand`, `InsertCommand` a `DeleteCommand`) pro každý změněný záznam v tabulce dat.

> [!NOTE]
> Pokud v hlavním dotazu není k dispozici dostatek informací, příkazy `InsertCommand`, `UpdateCommand` a `DeleteCommand` jsou vytvořeny jako výchozí při generování objektu TableAdapter. Pokud je hlavní dotaz TableAdapter více než jedna tabulka `SELECT` příkaz, je možné, že návrhář nebude moci vygenerovat `InsertCommand`, `UpdateCommand` a `DeleteCommand`. Pokud tyto příkazy nejsou vygenerovány, může při spuštění metody `TableAdapter.Update` dojít k chybě.

## <a name="tableadapter-generatedbdirectmethods"></a>Vlastnost GenerateDBDirectMethods třídy TableAdapter

Kromě `InsertCommand`, `UpdateCommand` a `DeleteCommand` se vytvoří objekty TableAdapter s metodami, které můžete spustit přímo proti databázi. Tyto metody (`TableAdapter.Insert`, `TableAdapter.Update` a `TableAdapter.Delete`) můžete volat přímo k manipulaci s daty v databázi. To znamená, že můžete volat tyto jednotlivé metody z kódu místo volání `TableAdapter.Update` pro zpracování vložení, aktualizace a odstranění, které čekají na přidruženou datovou tabulku.

Pokud nechcete vytvořit tyto přímé metody, nastavte vlastnost **GenerateDBDirectMethods** TableAdapter na hodnotu `false` (v okně **vlastnosti** ). Další dotazy, které jsou přidány do TableAdapter, jsou samostatné dotazy – negenerují tyto metody.

## <a name="tableadapter-support-for-nullable-types"></a>Podpora TableAdapter pro typy s možnou hodnotou null

Objekty TableAdapter podporuje typy s možnou hodnotou null `Nullable(Of T)` a `T?`. Další informace o typech s možnou hodnotou null v Visual Basic naleznete v tématu [typy hodnot s možnou hodnotou null](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). Další informace o typech s možnou C#hodnotou null v najdete v tématu [použití typů s možnou hodnotou null](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>Odkaz na TableAdapterManager

Ve výchozím nastavení vygeneruje třída TableAdapterManager, když vytvoříte datovou sadu, která obsahuje související tabulky. Chcete-li zabránit vygenerování třídy, změňte hodnotu vlastnosti `Hierarchical Update` datové sady na false. Když přetáhnete tabulku, která má relaci, na návrhovou plochu stránky Windows Form nebo WPF, Visual Studio deklaruje členskou proměnnou třídy. Pokud datovou vazbu nepoužíváte, je nutné ručně deklarovat proměnnou.

Třída TableAdapterManager není typu .NET. Proto je nemůžete v dokumentaci vyhledat. Je vytvořena v době návrhu v rámci procesu vytváření datové sady.

Následující jsou často používané metody a vlastnosti `TableAdapterManager` třídy:

|Člen|Popis|
|------------|-----------------|
|`UpdateAll` – metoda|Uloží všechna data ze všech tabulek dat.|
|`BackUpDataSetBeforeUpdate` – vlastnost|Určuje, zda má být před provedením metody `TableAdapterManager.UpdateAll` vytvořena záložní kopie datové sady. Datového.|
|vlastnost *tableName* `TableAdapter`|Představuje objekt TableAdapter. Vygenerovaná TableAdapterManager obsahuje vlastnost pro každý `TableAdapter`, kterou spravuje. Například datová sada s tabulkou Customers and Orders generuje TableAdapterManager, který obsahuje vlastnosti `CustomersTableAdapter` a `OrdersTableAdapter`.|
|`UpdateOrder` – vlastnost|Určuje pořadí jednotlivých příkazů INSERT, Update a DELETE. Nastavte tuto hodnotu na jednu z hodnot ve výčtu `TableAdapterManager.UpdateOrderOption`.<br /><br /> Ve výchozím nastavení je `UpdateOrder` nastavena na **InsertUpdateDelete**. To znamená, že vložení, následné aktualizace a následné odstranění jsou prováděny pro všechny tabulky v datové sadě.|

## <a name="security"></a>Zabezpečení

Když použijete datové příkazy s vlastností CommandType nastavenou na <xref:System.Data.CommandType.Text>, pečlivě zkontrolujte informace, které se odesílají z klienta, než je předáte do vaší databáze. Uživatelé se zlými úmysly se můžou pokusit odeslat (vložit) upravené nebo další příkazy SQL za účelem získání neoprávněného přístupu nebo poškození databáze. Před přenosem vstupu uživatele do databáze vždy ověřte, zda jsou informace platné. Osvědčeným postupem je vždy použít parametrizované dotazy nebo uložené procedury, pokud je to možné.

## <a name="see-also"></a>Viz také:

- [Nástroje datové sady](../data-tools/dataset-tools-in-visual-studio.md)
