---
title: Ověřování dat v datových sadách
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5a0a8846719c6ad57e65e1e308e9884e81e1997d
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174719"
---
# <a name="validate-data-in-datasets"></a>Ověřování dat v datových sadách
Ověřování dat je proces ověření, hodnot zadaných do datových objektů v souladu s omezeními ve schématu datové sady. Proces ověřování také potvrdí, že jsou tyto hodnoty dle pravidel, které se vytvořily pro vaši aplikaci. Je vhodné ověřit data před odesláním aktualizace do podkladové databáze. Tím se snižuje chyby, jakož i potenciální počet výměn mezi aplikací a databáze.

Si můžete ověřit, že data, která zapisuje do datové sady platný integrováním ověřovacích kontrol do samotné datové sadě. Datové sady dat bez ohledu na to, jak se provádí aktualizace můžete zkontrolovat, zda přímo ovládacími prvky ve formuláři v rámci komponenty, nebo jiným způsobem. Protože tato datová sada je součástí vaší aplikace (na rozdíl od databáze back-end), je logický místo, kde můžete vytvářet ověřování konkrétní aplikace.

Nejlepší místo pro přidání ověřování do aplikace je v souboru částečné třídy datové sady. V [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nebo [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], otevřete **Návrhář Dataset** a poklepejte na sloupec nebo tabulka, pro kterou chcete vytvořit ověřování. Tato akce automaticky vytvoří <xref:System.Data.DataTable.ColumnChanging> nebo <xref:System.Data.DataTable.RowChanging> obslužné rutiny události.

## <a name="validate-data"></a>Ověření dat
 Ověřování v rámci datové sady se provádí následujícími způsoby:

-   Tím, že vytvoříte vlastní ověřování konkrétní aplikace, které můžete zkontrolovat hodnoty v jednotlivých datový sloupec během změny. Další informace najdete v tématu [postupy: ověřování dat během úprav sloupců](validate-data-in-datasets.md).

-   Tím, že vytvoříte vlastní ověření specifické pro aplikace, který můžete zkontrolovat dat na hodnoty během celého datového řádku mění. Další informace najdete v tématu [postupy: ověřování dat během úprav řádků](validate-data-in-datasets.md).

-   Tím, že vytvoříte klíče, unikátních omezení a podobně jako součást definice skutečné schématu datové sady.

-   Nastavením vlastnosti <xref:System.Data.DataColumn> objektu, například <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>, a <xref:System.Data.DataColumn.Unique%2A>.

Několik události jsou vyvolány <xref:System.Data.DataTable> objektu, když probíhá změnu v záznamu:

-   <xref:System.Data.DataTable.ColumnChanging> a <xref:System.Data.DataTable.ColumnChanged> události jsou vyvolány během a po každé změně na jednotlivých sloupců. <xref:System.Data.DataTable.ColumnChanging> Událostí je užitečné, pokud chcete ověřit změny v určité sloupce. Informace o navrhované změny je předán jako argument události.
-   <xref:System.Data.DataTable.RowChanging> a <xref:System.Data.DataTable.RowChanged> události jsou vyvolány během a po všech změn za sebou. <xref:System.Data.DataTable.RowChanging> Je další obecné události. Označuje, že změna dochází jinde v řádku, ale nevíte, který sloupec došlo ke změně.

Ve výchozím nastavení jednotlivé změny do sloupce tedy vyvolává čtyři události. První je <xref:System.Data.DataTable.ColumnChanging> a <xref:System.Data.DataTable.ColumnChanged> události pro určitý sloupec, který mění. Dále jsou <xref:System.Data.DataTable.RowChanging> a <xref:System.Data.DataTable.RowChanged> události. Pokud více změn jsou prováděny na řádek, události, bude vyvolána u každé změny.

> [!NOTE]
>  Řádek dat <xref:System.Data.DataRow.BeginEdit%2A> metoda vypne <xref:System.Data.DataTable.RowChanging> a <xref:System.Data.DataTable.RowChanged> události po každé změně jednotlivých sloupců. V takovém případě není vyvolána událost až <xref:System.Data.DataRow.EndEdit%2A> metoda byla volána, když <xref:System.Data.DataTable.RowChanging> a <xref:System.Data.DataTable.RowChanged> události jsou vyvolány pouze jednou. Další informace najdete v tématu [vypnutí omezení při naplňování datové sady](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

Události, kterou zvolíte, závisí na to, jak podrobné chtějí ověření bude. Pokud je to důležité zachytit chybu, okamžitě při změně sloupce, sestavení pomocí ověření <xref:System.Data.DataTable.ColumnChanging> událostí. Jinak použijte <xref:System.Data.DataTable.RowChanging> událost, což může vést k zachycení několik chyb najednou. Navíc pokud vaše data strukturovaná, aby hodnota jednoho sloupce ověření na základě obsahu jiného sloupce, proveďte ověření během <xref:System.Data.DataTable.RowChanging> událostí.

Při aktualizaci záznamů <xref:System.Data.DataTable> objekt vyvolává události, které může reagovat na změny se vyskytují a po provedení změn.

Pokud vaše aplikace používá typové datové sady, můžete vytvořit obslužné rutiny událostí silného typu. Tento postup přidá čtyři další typu události, pro které můžete vytvořit obslužné rutiny: `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting`, a `dataTableNameRowDeleted`. Tyto obslužné rutiny zadané události předat argument, který obsahuje názvy sloupců tabulky, které usnadňují zápis a čtení kódu.

## <a name="data-update-events"></a>Aktualizace dat události

|Událost|Popis|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|Mění hodnotu ve sloupci. Událost předává řádků a sloupců, spolu s navrhovanou novou hodnotu.|
|<xref:System.Data.DataTable.ColumnChanged>|Změnila se hodnota ve sloupci. Událost předává řádků a sloupců, spolu s navrhovanou hodnotu.|
|<xref:System.Data.DataTable.RowChanging>|Změny, které byly provedeny <xref:System.Data.DataRow> objektu se chystáte potvrzeny zpět do datové sady. Pokud nebyla volána <xref:System.Data.DataRow.BeginEdit%2A> metody <xref:System.Data.DataTable.RowChanging> událost se vyvolá u každé změny do sloupce ihned po <xref:System.Data.DataTable.ColumnChanging> byla vyvolána událost. Pokud jste volali <xref:System.Data.DataRow.BeginEdit%2A> před prováděním změn, <xref:System.Data.DataTable.RowChanging> událost se vyvolá pouze v případě, že zavoláte <xref:System.Data.DataRow.EndEdit%2A> metody.<br /><br /> Událost předává řádku, spolu s hodnotu určující, jaký typ akce (změnu, insert a tak dále) je prováděna.|
|<xref:System.Data.DataTable.RowChanged>|Řádek byl změněn. Událost předává řádku, spolu s hodnotu určující, jaký typ akce (změnu, insert a tak dále) je prováděna.|
|<xref:System.Data.DataTable.RowDeleting>|Řádek se odstraňuje. Událost předává řádku, spolu s hodnotu určující, jaký typ akce (delete) se provádí.|
|<xref:System.Data.DataTable.RowDeleted>|Řádek byl odstraněn. Událost předává řádku, spolu s hodnotu určující, jaký typ akce (delete) se provádí.|

<xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging>, A <xref:System.Data.DataTable.RowDeleting> události jsou vyvolány během procesu aktualizace. Tyto události můžete použít k ověření dat nebo provedení jiných druhů zpracování. Vzhledem k tomu, že během těchto událostí je v procesu aktualizace, můžete je zrušit vyvoláním výjimky, což zabrání aktualizaci z dokončení.

<xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> a <xref:System.Data.DataTable.RowDeleted> události jsou oznámení událostí, které jsou vyvolány při aktualizaci byl úspěšně dokončen. Tyto události jsou užitečné, pokud chcete provádět další akce v závislosti na úspěšná aktualizace.

## <a name="validate-data-during-column-changes"></a>Ověřování dat během úprav sloupců

> [!NOTE]
>  **Návrhář Dataset** vytvoří částečnou třídu, která ověřování lze přidat logiku pro datovou sadu. Datová sada vygenerovaná návrhářem není odstranit ani nezmění žádný kód v dílčí třídě.

Data můžete ověřit při změně hodnoty ve sloupci data reakcí na <xref:System.Data.DataTable.ColumnChanging> událostí. Po vyvolání Tato událost předává argument události (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>), který obsahuje hodnotu, která je právě navrhuje se pro aktuální sloupec. Na základě obsahu z `e.ProposedValue`, můžete:

-   Přijměte navrhovanou hodnotu neprovedením žádné akce.

-   Odmítnout navrhovanou hodnota nastavením chyby sloupce (<xref:System.Data.DataRow.SetColumnError%2A>) z v rámci obslužné rutiny události měnící sloupec.

-   Volitelně můžete použít <xref:System.Windows.Forms.ErrorProvider> ovládací prvek zobrazí uživateli chybovou zprávu. Další informace najdete v tématu [ErrorProvider – komponenta](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

Ověření lze provést také během <xref:System.Data.DataTable.RowChanging> událostí.

## <a name="validate-data-during-row-changes"></a>Ověřování dat během úprav řádků
Můžete napsat kód pro každý sloupec, který chcete ověřit, jestli obsahuje data, která splňují požadavky aplikace. To lze proveďte nastavením sloupec, aby označoval, že obsahuje chybu Pokud navrhovaná hodnota není přijatelná. Následující příklady nastavují chybu sloupce při `Quantity` sloupec je 0 nebo menší. Obslužné rutiny události měnící řádek by měl vypadat podobně jako následující příklady.

### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Ověření dat při řádek změní (Visual Basic)

1.  Otevřete svou datovou sadu v **Návrhář Dataset**. Další informace najdete v tématu [návod: vytvoření datové sady v návrháři datových sad](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Poklepejte na záhlaví tabulky, kterou chcete ověřit. Tato akce automaticky vytvoří <xref:System.Data.DataTable.RowChanging> obslužná rutina události <xref:System.Data.DataTable> v souboru částečné třídy datové sady.

    > [!TIP]
    >  Dvakrát klikněte na panel vlevo od názvu tabulky k vytvoření obslužné rutiny události měnící řádek. Pokud dvakrát kliknete na název tabulky, můžete ho upravit.

     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]

### <a name="to-validate-data-when-a-row-changes-c"></a>Ověření dat při změně řádku (C#)

1.  Otevřete svou datovou sadu v **Návrhář Dataset**. Další informace najdete v tématu [návod: vytvoření datové sady v návrháři datových sad](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Poklepejte na záhlaví tabulky, kterou chcete ověřit. Tato akce vytvoří soubor částečné třídy pro <xref:System.Data.DataTable>.

    > [!NOTE]
    >  **Návrhář Dataset** nevytváří automaticky obslužnou rutinu události pro <xref:System.Data.DataTable.RowChanging> událostí. Je nutné vytvořit metodu ke zpracování <xref:System.Data.DataTable.RowChanging> události a spouštění kódu k připojení události do metody inicializace tabulky.

3.  Zkopírujte následující kód do částečné třídy:

    ```csharp
    public override void EndInit()
    {
        base.EndInit();
        Order_DetailsRowChanging += TestRowChangeEvent;
    }

    public void TestRowChangeEvent(object sender, Order_DetailsRowChangeEvent e)
    {
        if ((short)e.Row.Quantity <= 0)
        {
            e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
        }
        else
        {
            e.Row.SetColumnError("Quantity", "");
        }
    }
    ```

## <a name="to-retrieve-changed-rows"></a>Chcete-li načítání změněných řádků
Má každý řádek v tabulce dat <xref:System.Data.DataRow.RowState%2A> vlastnost, která uchovává informace o aktuálním stavu daného řádku s použitím hodnoty <xref:System.Data.DataRowState> výčtu. Může vrátit změněných řádků z tabulky datovou sadu nebo dat pomocí volání `GetChanges` metodu <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable>. Můžete ověřit, že existují změny před voláním `GetChanges` voláním <xref:System.Data.DataSet.HasChanges%2A> metoda datové sady.

> [!NOTE]
>  Po potvrzení změn do datové sady nebo dat tabulky (voláním <xref:System.Data.DataSet.AcceptChanges%2A> metoda), `GetChanges` metoda nevrátí žádná data. Pokud vaše aplikace potřebuje ke zpracování změněných řádků, je nutné zpracovat změny před voláním `AcceptChanges` metody.

Volání <xref:System.Data.DataSet.GetChanges%2A> metoda datovou sadu nebo data tabulky vrátí novou tabulku datové sady nebo data, která obsahuje pouze záznamy, které se změnily. Pokud chcete získat konkrétních záznamů – například pouze nové záznamy nebo pouze změněné záznamy – můžete předat hodnotu z <xref:System.Data.DataRowState> výčet jako parametr, který se `GetChanges` metody.

Použití <xref:System.Data.DataRowVersion> výčtu pro přístup k různé verze řádku (například původní hodnoty, které byly v řádku před zpracováním).

### <a name="to-get-all-changed-records-from-a-dataset"></a>Chcete-li získat všechny změněné záznamy z datové sady

-   Volání <xref:System.Data.DataSet.GetChanges%2A> metoda datové sady.

     Následující příklad vytvoří novou datovou sadu s názvem `changedRecords` a naplní se všechny změněné záznamy z jiného datovou sadu s názvem `dataSet1`.

     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]

### <a name="to-get-all-changed-records-from-a-data-table"></a>Chcete-li získat všechny změněné záznamy z tabulky dat

-   Volání <xref:System.Data.DataTable.GetChanges%2A> metoda objektu DataTable.

     Následující příklad vytvoří novou tabulku volá `changedRecordsTable` a naplní se všechny změněné záznamy z jiné tabulky dat, volá `dataTable1`.

     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]

### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Chcete-li získat všechny záznamy, které mají stav konkrétní řádek

-   Volání `GetChanges` metoda datová sada nebo tabulka dat a pass <xref:System.Data.DataRowState> hodnota výčtu jako argument.

     Následující příklad ukazuje, jak vytvořit novou datovou sadu s názvem `addedRecords` a přidejte do ní jenom záznamy, které byly přidány do `dataSet1` datové sady.

     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]

     Následující příklad ukazuje, jak vrátit všechny záznamy, které jste nedávno přidali `Customers` tabulky:

     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]

## <a name="access-the-original-version-of-a-datarow"></a>Přístup k původní verzi objektu DataRow
Při změně na řádky dat, datová sada zachová původní (<xref:System.Data.DataRowVersion.Original>) i novou (<xref:System.Data.DataRowVersion.Current>) verzi řádku. Například před voláním `AcceptChanges` metoda, vaše aplikace můžou přistupovat k různé verze záznamu (jak je definováno ve <xref:System.Data.DataRowVersion> výčet) a odpovídajícím způsobem zpracovávat změny.

> [!NOTE]
>  Různé verze řádku existují pouze poté, co byl upraven a před ní `AcceptChanges` byla volána metoda. Po `AcceptChanges` byla volána metoda, aktuální a původní verze jsou stejné.

Předání <xref:System.Data.DataRowVersion> hodnotu spolu indexem sloupce (nebo název sloupce jako řetězce) vrátí hodnotu z verze konkrétního řádku tohoto sloupce. Změněný sloupec je rozpoznán během <xref:System.Data.DataTable.ColumnChanging> a <xref:System.Data.DataTable.ColumnChanged> události. Toto je vhodná doba ke kontrole verze různých řádků pro účely ověření. Pokud jste dočasně pozastavili omezení, tyto události nebudou vyvolány a budete muset programově Identifikujte však sloupce, které se změnily. Uděláte to tak iterace <xref:System.Data.DataTable.Columns%2A> kolekce a porovnáním různých <xref:System.Data.DataRowVersion> hodnoty.

### <a name="to-get-the-original-version-of-a-record"></a>Získání původní verze záznamu

-   Přístup k hodnotě sloupce předáním <xref:System.Data.DataRowVersion> řádku, který chcete vrátit.

     Následující příklad ukazuje způsob použití <xref:System.Data.DataRowVersion> hodnotu k získání původní hodnoty `CompanyName` pole <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]

## <a name="access-the-current-version-of-a-datarow"></a>Přístup k aktuální verzi objektu DataRow

### <a name="to-get-the-current-version-of-a-record"></a>Chcete-li získat aktuální verze záznamu

-   Přístup k hodnotě sloupce a pak přidejte parametr do indexu, která určuje, kterou verzi řádku chcete vrátit.

     Následující příklad ukazuje způsob použití <xref:System.Data.DataRowVersion> hodnotu k získání aktuální hodnoty `CompanyName` pole <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]

## <a name="see-also"></a>Viz také:

- [Nástroje datové sady v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Postupy: ověřování dat v ovládacím prvku Windows Forms DataGridView](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)
- [Postupy: zobrazení ikon chyb pro ověřování formuláře pomocí komponenty Windows Forms ErrorProvider](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)