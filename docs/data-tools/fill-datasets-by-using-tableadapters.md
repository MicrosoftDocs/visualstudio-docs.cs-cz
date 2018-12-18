---
title: Vyplnění datové sady s použitím objektů TableAdapter
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 673c364c1750afbaa4b319c40550be7cfac3b53b
ms.sourcegitcommit: 7a11a094a353f2e2a2077ad863ca4c0fb97f7ec5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/18/2018
ms.locfileid: "39131970"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Vyplnění datové sady s použitím objektů TableAdapter

Komponenty TableAdapter vyplní datovou sadu s daty z databáze, na základě jednoho nebo více dotazů nebo uložených procedur, které zadáte. Objekty TableAdapter lze provést také přidání, aktualizace a odstranění v databázi, a zachovat změny provedené do datové sady. Také můžete použít globální příkazy, které nesouvisí s jakoukoli konkrétní tabulku.

> [!NOTE]
> Objekty TableAdapter jsou generovány pomocí návrháře sady Visual Studio. Pokud vytvoříte datové sady prostřednictvím kódu programu, použijte vlastnost DataAdapter, což je třída rozhraní .NET Framework.

Podrobné informace o operacích TableAdapter můžete přeskočit přímo na jednu z těchto témat:

|Téma|Popis|
|-----------|-----------------|
|[Vytvoření a konfigurace objektů TableAdapter](../data-tools/create-and-configure-tableadapters.md)|Jak používat návrháře k vytvoření a konfigurace objektů TableAdapter|
|[Vytvoření parametrizovaných dotazů TableAdapter](../data-tools/create-parameterized-tableadapter-queries.md)|Jak povolit uživatelům zadat argumenty procedur TableAdapter nebo dotazy|
|[Přímý přístup k databázi pomocí objektů TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Jak používat objekty TableAdapter dbdirect – metody|
|[Vypnutí omezení při naplňování datové sady](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Jak pracovat s omezeními cizího klíče při aktualizaci dat|
|[Rozšíření funkcí objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Přidání vlastního kódu do prvků TableAdapters|
|[Čtení dat XML do datové sady](../data-tools/read-xml-data-into-a-dataset.md)|Jak pracovat s XML|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>TableAdapter – přehled

Objekty TableAdapter jsou návrhářem vygenerované komponenty, které připojení k databázi, spouštění dotazů nebo uložených procedur a zadat jejich objekt DataTable s vrácenými daty. Objekty TableAdapter také odeslat aktualizovaná data z aplikace zpět do databáze. Můžete spouštět tolik dotazů, kolik chcete na objektu typu TableAdapter tak dlouho, dokud vrátí data, která odpovídají schématu tabulky, se kterým je spojen TableAdapter. Následující diagram znázorňuje, jak objekty TableAdapter komunikovat s databází a jiných objektů v paměti:

![Tok dat v klientských aplikacích](../data-tools/media/clientdatadiagram.gif)

Zatímco objekty TableAdapter jsou navrženy s **Návrhář Dataset**, třídy TableAdapter nejsou generovány jako vnořené třídy typu <xref:System.Data.DataSet>. Jsou umístěny v samostatných oborech názvů, které jsou specifické pro jednotlivé datové sady. Například, pokud máte datovou sadu s názvem `NorthwindDataSet`, objekty TableAdapter, které jsou přidružené k <xref:System.Data.DataTable>ve `NorthwindDataSet` by byla `NorthwindDataSetTableAdapters` oboru názvů. Pro programový přístup k určitému typu TableAdapter musíte deklarovat novou instanci typu TableAdapter. Příklad:

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>Přidružené schéma objektu DataTable

Při vytváření objektu typu TableAdapter, použijte počáteční dotaz nebo uloženou proceduru pro definování schématu objektu TableAdapter přidružené k <xref:System.Data.DataTable>. Spustit tento počáteční dotaz nebo uloženou proceduru voláním objektu TableAdapter `Fill` – metoda (která naplní TableAdapter přidružené k <xref:System.Data.DataTable>). Všechny změny provedené v hlavním dotazu objektu TableAdapter se projeví ve schématu přidružené tabulky dat. Také například odebráním sloupce z hlavního dotazu odeberete sloupec z přidružené tabulky dat. Pokud jakékoliv další dotazy na TableAdapter používají příkazy SQL vracející sloupce, které nejsou v hlavním dotazu, pokusí se Návrhář synchronizovat změny ve sloupcích mezi hlavním dotazem a dalších dotazů.

## <a name="tableadapter-update-commands"></a>Příkazy aktualizace objektu TableAdapter

Funkce aktualizace objektu TableAdapter je závislá na tom, kolik informací je k dispozici v hlavním dotazu v **Průvodce TableAdapter**. Například objekty TableAdapter, které jsou nakonfigurovány k načtení hodnoty z více tabulek (použití `JOIN`), skalárních hodnot, zobrazení nebo výsledků agregačních funkcí nejsou původně vytvořeny s možností odesílat aktualizace zpět do podkladové databáze. Ale můžete nakonfigurovat `INSERT`, `UPDATE`, a `DELETE` ručně v příkazy **vlastnosti** okna.

## <a name="tableadapter-queries"></a>TableAdapter – dotazy

![TableAdapter s více dotazy](../data-tools/media/tableadapter.gif)

Objekty TableAdapter mohou obsahovat několik dotazů k vyplnění přidružených datových tabulek. Objektu TableAdapter lze definovat tolik dotazů, kolik vyžaduje vaše aplikace, pokud každý dotaz vrací data, která odpovídají stejnému schématu jako jeho přidružená tabulka dat. Tato možnost umožňuje objektu typu TableAdapter načíst různé výsledky založené na odlišná kritéria.

Například pokud vaše aplikace obsahuje tabulku s názvy zákazníka, můžete vytvořit dotaz, který vyplňuje tabulku s každou jméno zákazníka, který začíná určitým písmenem a druhý, který vyplňuje tabulku s všem zákazníkům, kteří se nacházejí ve stejném státě. K vyplnění `Customers` tabulky se zákazníky v daném státě, můžete vytvořit `FillByState` dotaz, který přijímá parametr pro hodnotu státu následujícím způsobem: `SELECT * FROM Customers WHERE State = @State`. Dotaz spustíte voláním `FillByState` metoda a předáním hodnoty parametru tímto způsobem: `CustomerTableAdapter.FillByState("WA")`.

Kromě přidání dotazy, které vracejí data stejného schématu jako tabulka dat objektu TableAdapter, lze přidat dotazy, které vracejí skalární hodnoty. Například dotaz, který vrací počet zákazníků (`SELECT Count(*) From Customers`) je platný pro `CustomersTableAdapter,` i v případě, že data, která je vrácena neodpovídají schématu příslušné tabulky.

## <a name="clearbeforefill-property"></a>Vlastnost ClearBeforeFill

Ve výchozím nastavení při každém spuštění dotazu k vyplnění tabulky dat objektu TableAdapter existující data odstraněna a jsou načteny pouze výsledky dotazu do tabulky. Nastavit TableAdapter `ClearBeforeFill` vlastnost `false` Pokud budete chtít přidat nebo sloučit data vrácená z dotazu k existujícím datům v datové tabulce. Bez ohledu na to, zda tato data odstraníte budete muset explicitní odeslání aktualizací zpět do databáze, pokud chcete, aby je uchoval. Proto nezapomeňte před spuštěním dalšího dotazu, který vyplňuje tabulku, uložte změny dat v tabulce. Další informace najdete v tématu [aktualizace dat pomocí TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>Dědičnost třídy TableAdapter

Objekty TableAdapter rozšiřují funkce standardních datových adaptérů zapouzdřením nakonfigurovaného <xref:System.Data.Common.DataAdapter> třídy. Ve výchozím nastavení, zdědí objektu TableAdapter <xref:System.ComponentModel.Component> třídy a nelze ji převést na <xref:System.Data.Common.DataAdapter> třídy. Přetypování objektu typu TableAdapter na <xref:System.Data.Common.DataAdapter> třídy za následek <xref:System.InvalidCastException> chyby. Chcete-li změnit základní třídu třídy TableAdapter, můžete zadat třídu, která je odvozena z <xref:System.ComponentModel.Component> v **základní třídy** vlastnost objektu TableAdapter v **Návrhář Dataset**.

## <a name="tableadapter-methods-and-properties"></a>Vlastnosti a metody třídy TableAdapter

Třída TableAdapter není součástí [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. To znamená, že je nelze vyhledat v dokumentaci nebo **prohlížeče objektů**. Vytvoří se v době návrhu, když použijete jednu z výše uvedených průvodců. Název, který je přiřazen objektu typu TableAdapter při jeho vytvoření vychází z názvu tabulky, ve které pracujete. Například při vytváření objektu typu TableAdapter na základě tabulky v databázi s názvem `Orders`, má název TableAdapter `OrdersTableAdapter`. Název třídy TableAdapter lze změnit pomocí **název** vlastnost **Návrhář Dataset**.

Tady jsou běžně používané metody a vlastnosti třídy TableAdapter:

|Člen|Popis|
|------------|-----------------|
|`TableAdapter.Fill`|Naplní objektu TableAdapter datovou tabulku přidruženou objektu TableAdapter výsledky `SELECT` příkazu.|
|`TableAdapter.Update`|Odešle změny zpět do databáze a vrátí celé číslo představující počet řádků aktualizací ovlivněny. Další informace najdete v tématu [aktualizace dat pomocí TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Vrátí nový <xref:System.Data.DataTable> , který je naplněný daty.|
|`TableAdapter.Insert`|Vytvoří v tabulce dat nový řádek. Další informace najdete v tématu [vkládání nových záznamů do databáze](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|Určuje, zda bude tabulka dat před voláním metody `Fill` vyprázdněna.|

## <a name="tableadapter-update-method"></a>Metoda aktualizace třídy TableAdapter

Objekty TableAdapter používají příkazy pro čtení a zápis dat z databáze. Pomocí objektu TableAdapter počáteční `Fill` (hlavní) dotaz jako základ pro vytvoření schématu přidružené tabulky dat., stejně jako `InsertCommand`, `UpdateCommand`, a `DeleteCommand` příkazy, které jsou přidružené k `TableAdapter.Update` metody. Volání objektu TableAdapter `Update` metoda provede příkazy, které byly vytvořeny při konfiguraci objektu TableAdapter, není jednou z další dotazy, které jste přidali pomocí **Průvodce nastavením dotazu TableAdapter**.

Při použití objektu typu TableAdapter efektivně provede stejné operace s příkazy, které by obvykle provádí. Například při volání adaptéru `Fill` metody adaptér spustí příkaz data jeho `SelectCommand` vlastnost a použije čtečku dat (například <xref:System.Data.SqlClient.SqlDataReader>) k načtení sady výsledků do tabulky data. Podobně při volání adaptéru `Update` metody spuštěn příslušný příkaz (v `UpdateCommand`, `InsertCommand`, a `DeleteCommand` vlastnosti) pro jednotlivé změněné záznamy v datové tabulce.

> [!NOTE]
> Pokud v hlavním dotazu není k dispozici dostatek informací, příkazy `InsertCommand`, `UpdateCommand` a `DeleteCommand` jsou vytvořeny jako výchozí při generování objektu TableAdapter. Pokud hlavní TableAdapter dotazu je více než jedné tabulky `SELECT` příkaz, je možné, Návrhář nebude možné generovat `InsertCommand`, `UpdateCommand`, a `DeleteCommand`. Pokud tyto příkazy nejsou vygenerovány, budete k chybě může dojít při spuštění `TableAdapter.Update` metody.

## <a name="tableadapter-generatedbdirectmethods"></a>Vlastnost GenerateDBDirectMethods třídy TableAdapter

Kromě `InsertCommand`, `UpdateCommand`, a `DeleteCommand`, jsou objekty TableAdapter vytvořeny metodami, které můžete spustit přímo proti databázi. Můžete volat tyto metody (`TableAdapter.Insert`, `TableAdapter.Update`, a `TableAdapter.Delete`) přímo pro manipulaci s daty v databázi. To znamená, že tyto metody lze volat z vašeho kódu namísto volání metody `TableAdapter.Update` zpracování vložení, aktualizace a odstranění, které čekají na vyřízení pro přidružená data tabulky.

Pokud tyto přímé metody vytvořit nechcete, nastavte TableAdapter **GenerateDbDirectMethods** vlastnost `false` (v **vlastnosti** okno). Další dotazy, které jsou přidány do objektu TableAdapter jsou samostatné dotazy – není generovaných tyto metody.

## <a name="tableadapter-support-for-nullable-types"></a>Třída TableAdapter podporuje typy s možnou hodnotou Null

Třída TableAdapter podporuje typy s možnou hodnotou Null `Nullable(Of T)` a `T?`. Další informace o typech s povolenou hodnotou Null v jazyce Visual Basic najdete v tématu [hodnotové typy s možnou hodnotou Null](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). Další informace o typech s povolenou hodnotou Null v jazyce C# najdete v tématu [použití typů s povolenou hodnotou Null](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>TableAdapterManager odkaz

Ve výchozím nastavení vygeneruje třídu TableAdapterManager při vytváření datové sady, který obsahuje související tabulky. Abyste zabránili generovaná třída, změňte hodnotu `Hierarchical Update` vlastnosti datové sady na hodnotu false. Při přetažení tabulky, která má vztah na návrhovou plochu formuláře Windows nebo WPF stránku sady Visual Studio deklaruje členské proměnné třídy. Pokud nepoužíváte vázání dat, budete muset ručně deklarovat proměnnou.

Třída TableAdapterManager není součástí [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Proto je nelze vyhledat v dokumentaci. Vytvoří se v době návrhu jako součást procesu vytváření datové sady.

Toto jsou často používané metody a vlastnosti `TableAdapterManager` třídy:

|Člen|Popis|
|------------|-----------------|
|`UpdateAll` – Metoda|Uloží všechna data ze všech dat tabulky.|
|`BackUpDataSetBeforeUpdate` Vlastnost|Určuje, jestli se má vytvořit záložní kopii datové sady, před spuštěním `TableAdapterManager.UpdateAll` metody. Datový typ Boolean.|
|*tableName* `TableAdapter` vlastnost|Reprezentuje TableAdapter. Vygenerovaný komponenta TableAdapterManager neobsahuje vlastnost pro každý `TableAdapter` spravuje. Například generuje datovou sadu s tabulkou Zákazníci a objednávky pomocí vlastnosti TableAdapterManager, který obsahuje `CustomersTableAdapter` a `OrdersTableAdapter` vlastnosti.|
|`UpdateOrder` Vlastnost|Určuje pořadí jednotlivých insert, update a příkazů delete. Nastavte na jednu z hodnot v `TableAdapterManager.UpdateOrderOption` výčtu.<br /><br /> Ve výchozím nastavení `UpdateOrder` je nastavena na **InsertUpdateDelete**. To znamená, vloží, pak aktualizuje a odstraní se provádí pro všechny tabulky v datové sadě.|

## <a name="security"></a>Zabezpečení

Při použití datové příkazy se vlastnost CommandType nastavena na <xref:System.Data.CommandType.Text>, pečlivě zkontrolujte informace, které se odesílají z klienta před předáním k vaší databázi. Uživatelé se zlými úmysly může pokusu o odeslání (Vložit) změněné nebo další příkazy SQL ve snaze o získání neoprávněného přístupu nebo poškození databáze. Před přenosem vstupu uživatele na databázi vždy ověřte, že informace platné. Osvědčeným postupem je vždycky potřeba použít parametrizovaných dotazů nebo uložených procedur, pokud je to možné.

## <a name="see-also"></a>Viz také:

- [Nástroje datové sady](../data-tools/dataset-tools-in-visual-studio.md)
