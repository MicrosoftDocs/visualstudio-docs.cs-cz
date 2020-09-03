---
title: Ověřit data v datových sadách | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8d42553fbee6de6a89e16716a191db8a3d9fb883
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72621071"
---
# <a name="validate-data-in-datasets"></a>Ověřování dat v datových sadách
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ověřování dat je proces potvrzení, že hodnoty, které jsou zadány do datových objektů, jsou v souladu s omezeními v rámci schématu datové sady. Proces ověřování také potvrdí, že tyto hodnoty následují pravidla, která byla pro vaši aplikaci vytvořena. Před odesláním aktualizací do podkladové databáze je dobrým zvykem ověřit data. Tím se snižuje počet chyb a také potenciální počet odezvy mezi aplikací a databází.

 Můžete potvrdit, že data, která jsou zapsána do datové sady, jsou platná sestavením kontrol ověření do samotné datové sady. Datová sada může kontrolovat data bez ohledu na to, jak je prováděna aktualizace – ať už přímo ovládacími prvky ve formuláři, v rámci součásti nebo jiným způsobem. Vzhledem k tomu, že datová sada je součástí vaší aplikace (na rozdíl od back-endu databáze), je logické místo pro sestavení ověřování specifického pro aplikaci.

 Nejlepším místem pro přidání ověřování do aplikace je soubor částečné třídy datové sady. V [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../includes/csprcs-md.md)] otevřete **Návrhář datových sad** a dvakrát klikněte na sloupec nebo tabulku, pro které chcete vytvořit ověření. Tato akce automaticky vytvoří <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> obslužnou rutinu události nebo. Další informace naleznete v tématech [How to: Validate data během změny sloupce](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5) nebo [Postupy: ověření dat během změn řádků](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc). Úplný příklad naleznete v tématu [Návod: Přidání ověřování do datové sady](https://msdn.microsoft.com/library/09351fab-d670-45e3-b53a-a944eff717e7).

## <a name="validate-data"></a>Ověření dat
 Ověřování v rámci datové sady lze provést následujícími způsoby:

- Vytvořením vlastního ověřování specifického pro aplikaci, které během změn může kontrolovat hodnoty v jednotlivých datových sloupcích.  Další informace naleznete v tématu [How to: Validate data během změny sloupce](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).

- Vytvořením vlastního ověřování specifického pro aplikaci, které může kontrolovat data na hodnoty v průběhu změny celého řádku dat. Další informace naleznete v tématu [How to: Validate data při změnách řádku](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).

- Vytvořením klíčů, jedinečných omezení a tak dále jako součást skutečné definice schématu pro datovou sadu. Další informace o začlenění ověřování do definice schématu najdete v tématu [omezení DataColumn na zahrnutí jedinečných hodnot](https://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).

- Nastavením vlastností <xref:System.Data.DataColumn> objektu, například, <xref:System.Data.DataColumn.MaxLength%2A> <xref:System.Data.DataColumn.AllowDBNull%2A> a <xref:System.Data.DataColumn.Unique%2A> .

  Několik událostí je vyvoláno <xref:System.Data.DataTable> objektem, když dojde ke změně v záznamu:

- <xref:System.Data.DataTable.ColumnChanging>Události a <xref:System.Data.DataTable.ColumnChanged> jsou vyvolány během a po každé změně do jednotlivého sloupce. <xref:System.Data.DataTable.ColumnChanging>Událost je užitečná v případě, že chcete ověřit změny v konkrétních sloupcích. Informace o navrhované změně jsou předány jako argument s událostí. Další informace naleznete v tématu [How to: Validate data během změny sloupce](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).

- <xref:System.Data.DataTable.RowChanging>Události a <xref:System.Data.DataTable.RowChanged> jsou vyvolány během každé změny řádku a po ní. <xref:System.Data.DataTable.RowChanging>Událost je obecnější. Indikuje, že se na řádku vyskytuje změna, ale nevíte, který sloupec se změnil. Další informace naleznete v tématu [How to: Validate data při změnách řádku](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).

  Ve výchozím nastavení každá změna ve sloupci proto vyvolává čtyři události. První je <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.ColumnChanged> události a pro konkrétní sloupec, který se mění. Další jsou <xref:System.Data.DataTable.RowChanging> události a <xref:System.Data.DataTable.RowChanged> . Je-li na řádku provedeno více změn, události budou vyvolány pro každou změnu.

> [!NOTE]
> Metoda datového řádku <xref:System.Data.DataRow.BeginEdit%2A> vypne <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable.RowChanged> události a po změně každého jednotlivého sloupce. V takovém případě událost není vyvolána, dokud není <xref:System.Data.DataRow.EndEdit%2A> volána metoda <xref:System.Data.DataTable.RowChanging> a <xref:System.Data.DataTable.RowChanged> události a jsou vyvolány pouze jednou. Další informace najdete v tématu vypnutí [omezení při naplňování datové sady](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

 Událost, kterou zvolíte, závisí na tom, jak podrobně chcete ověřování provést. Pokud je důležité zachytit chybu okamžitě při změně sloupce, sestavte ověření pomocí <xref:System.Data.DataTable.ColumnChanging> události. V opačném případě použijte <xref:System.Data.DataTable.RowChanging> událost, která by mohla vést k zachycení několika chyb najednou. Kromě toho, pokud jsou vaše data strukturovaná tak, aby byla hodnota jednoho sloupce ověřená na základě obsahu jiného sloupce, proveďte ověření během <xref:System.Data.DataTable.RowChanging> události.

 Po aktualizaci záznamů <xref:System.Data.DataTable> objekt vyvolá události, na které můžete reagovat, když dojde ke změnám a po provedení změn.

 Pokud vaše aplikace používá typovou datovou sadu, můžete vytvořit obslužné rutiny událostí silného typu. Tím přidáte čtyři další typované události, které můžete vytvořit obslužných rutin pro: `dataTableNameRowChanging` , `dataTableNameRowChanged` , a `dataTableNameRowDeleting` `dataTableNameRowDeleted` . Tyto obslužné rutiny událostí typu předávají argument, který obsahuje názvy sloupců tabulky, které usnadňují zápis a čtení kódu.

## <a name="data-update-events"></a>Události aktualizace dat

|Událost|Popis|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|Změní se hodnota ve sloupci. Událost předá do sebe řádek a sloupec, spolu s navrhovanou novou hodnotou.|
|<xref:System.Data.DataTable.ColumnChanged>|Hodnota ve sloupci byla změněna. Událost předá do sebe řádek a sloupec, společně s navrhovanou hodnotou.|
|<xref:System.Data.DataTable.RowChanging>|Změny provedené u objektu se budou zasílat <xref:System.Data.DataRow> zpátky do datové sady. Pokud jste nevolali <xref:System.Data.DataRow.BeginEdit%2A> metodu, <xref:System.Data.DataTable.RowChanging> událost je vyvolána pro každou změnu sloupce ihned po <xref:System.Data.DataTable.ColumnChanging> vyvolání události. Pokud jste volali <xref:System.Data.DataRow.BeginEdit%2A> před provedením změn, <xref:System.Data.DataTable.RowChanging> událost je vyvolána pouze při volání <xref:System.Data.DataRow.EndEdit%2A> metody.<br /><br /> Událost předá řádek, spolu s hodnotou, která označuje, jaký typ akce (změny, vložení a tak dále) se provádí.|
|<xref:System.Data.DataTable.RowChanged>|Řádek byl změněn. Událost předá řádek, spolu s hodnotou, která označuje, jaký typ akce (změny, vložení a tak dále) se provádí.|
|<xref:System.Data.DataTable.RowDeleting>|Odstraňuje se řádek. Událost předá tento řádek spolu s hodnotou, která označuje, jaký typ akce (odstranění) se provádí.|
|<xref:System.Data.DataTable.RowDeleted>|Řádek byl odstraněn. Událost předá tento řádek spolu s hodnotou, která označuje, jaký typ akce (odstranění) se provádí.|

 <xref:System.Data.DataTable.ColumnChanging>Události, <xref:System.Data.DataTable.RowChanging> a <xref:System.Data.DataTable.RowDeleting> jsou vyvolány během procesu aktualizace. Tyto události můžete použít k ověření dat nebo provádění jiných typů zpracování. Vzhledem k tomu, že aktualizace probíhá během těchto událostí, můžete ji zrušit vyvoláním výjimky, která zabrání dokončení aktualizace.

 <xref:System.Data.DataTable.ColumnChanged> <xref:System.Data.DataTable.RowChanged> <xref:System.Data.DataTable.RowDeleted> Události a jsou události oznámení, které jsou vyvolány po úspěšném dokončení aktualizace. Tyto události jsou užitečné, když chcete provést další akci na základě úspěšné aktualizace.

## <a name="validate-data-during-column-changes"></a>Ověřit data během změny sloupce

> [!NOTE]
> **Návrhář datových sad** vytvoří částečnou třídu, ve které lze ověřovací logiku přidat do datové sady. Datová sada generovaná návrhářem neodstraní ani nezmění žádný kód v dílčí třídě.

 Data můžete ověřit při změně hodnoty v datovém sloupci tím, že odpovíte na <xref:System.Data.DataTable.ColumnChanging> událost. Při vyvolání Tato událost předává argument události ( <xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A> ), který obsahuje hodnotu, která je navržena pro aktuální sloupec. Na základě obsahu `e.ProposedValue` můžete:

- Přijměte navrhovanou hodnotu tím, že nic nedělá.

- Odmítne navrhovanou hodnotu nastavením chyby sloupce ( <xref:System.Data.DataRow.SetColumnError%2A> ) z obslužné rutiny události měnící sloupce.

- Volitelně můžete pomocí <xref:System.Windows.Forms.ErrorProvider> ovládacího prvku zobrazit uživateli chybovou zprávu. Další informace najdete v tématu [Komponenta ErrorProvider](https://msdn.microsoft.com/library/c0f2e231-c5c9-413d-a507-75af2db499b6).

  Ověřování lze také provést během <xref:System.Data.DataTable.RowChanging> události. Další informace naleznete v tématu [How to: Validate data při změnách řádku](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).

## <a name="validate-data-during-row-changes"></a>Ověřit data během změny řádku
 Můžete napsat kód pro ověření, že každý sloupec, který chcete ověřit, obsahuje data, která splňují požadavky vaší aplikace. Provedete to tak, že nastavíte sloupec tak, aby označoval, že obsahuje chybu, pokud navrhovaná hodnota nesouhlasí. Následující příklady nastavují chybu sloupce, pokud `Quantity` je sloupec 0 nebo menší. Obslužné rutiny události měnící řádky by měly vypadat podobně jako v následujících příkladech.

#### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Ověření dat při změně řádku (Visual Basic)

1. Otevřete datovou sadu v **Návrhář datových sad**. Další informace najdete v tématu [Postup: otevření datové sady v Návrhář datových sad](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Dvakrát klikněte na záhlaví tabulky, kterou chcete ověřit. Tato akce automaticky vytvoří <xref:System.Data.DataTable.RowChanging> obslužnou rutinu události <xref:System.Data.DataTable> v souboru částečné třídy datové sady.

    > [!TIP]
    > Dvojitým kliknutím nalevo od názvu tabulky vytvoříte obslužnou rutinu události měnící řádek. Pokud dvakrát kliknete na název tabulky, můžete ho upravit.

     [!code-vb[VbRaddataValidating#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataValidating/VB/NorthwindDataSet.vb#3)]

#### <a name="to-validate-data-when-a-row-changes-c"></a>Ověření dat při změně řádku (C#)

1. Otevřete datovou sadu v **Návrhář datových sad**. Další informace najdete v tématu [Postup: otevření datové sady v Návrhář datových sad](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Dvakrát klikněte na záhlaví tabulky, kterou chcete ověřit. Tato akce vytvoří soubor částečné třídy pro <xref:System.Data.DataTable> .

    > [!NOTE]
    > **Návrhář datových sad** nevytváří automaticky obslužnou rutinu události pro <xref:System.Data.DataTable.RowChanging> událost. Je nutné vytvořit metodu pro zpracování <xref:System.Data.DataTable.RowChanging> události a spustit kód pro zapojení události do inicializační metody tabulky.

3. Zkopírujte následující kód do částečné třídy:

    ```
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

## <a name="to-retrieve-changed-rows"></a>Načtení změněných řádků
 Každý řádek v tabulce dat má <xref:System.Data.DataRow.RowState%2A> vlastnost, která sleduje aktuální stav tohoto řádku pomocí hodnot ve <xref:System.Data.DataRowState> výčtu. Můžete vrátit změněné řádky z datové sady nebo tabulky dat voláním `GetChanges` metody <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable> . Můžete ověřit, zda existují změny před voláním `GetChanges` voláním <xref:System.Data.DataSet.HasChanges%2A> metody datové sady. Další informace o najdete <xref:System.Data.DataSet.HasChanges%2A> v tématu [Postup: Vyhledání změněných řádků](https://msdn.microsoft.com/library/af160d20-472b-4c13-8f15-75480c39a653).

> [!NOTE]
> Po potvrzení změn v datové sadě nebo tabulce dat (voláním <xref:System.Data.DataSet.AcceptChanges%2A> metody) `GetChanges` nevrátí metoda žádná data. Pokud vaše aplikace potřebuje zpracovat změněné řádky, je nutné před voláním metody zpracovat změny `AcceptChanges` .

 Volání <xref:System.Data.DataSet.GetChanges%2A> metody datové sady nebo tabulky dat vrátí novou datovou sadu nebo datovou tabulku, která obsahuje pouze záznamy, které byly změněny. Pokud chcete získat konkrétní záznamy, například pouze nové záznamy nebo pouze změněné záznamy, můžete předat hodnotu z <xref:System.Data.DataRowState> výčtu jako parametr `GetChanges` metodě.

 Použijte <xref:System.Data.DataRowVersion> výčet pro přístup k různým verzím řádku (například původní hodnoty, které byly v řádku před jeho zpracováním).

#### <a name="to-get-all-changed-records-from-a-dataset"></a>Získání všech změněných záznamů z datové sady

- Zavolejte <xref:System.Data.DataSet.GetChanges%2A> metodu datové sady.

     Následující příklad vytvoří novou datovou sadu `changedRecords` s názvem a naplní ji všemi změněnými záznamy z jiné datové sady s názvem `dataSet1` .

     [!code-csharp[VbRaddataEditing#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#14)]
     [!code-vb[VbRaddataEditing#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#14)]

#### <a name="to-get-all-changed-records-from-a-data-table"></a>Získání všech změněných záznamů z tabulky dat

- Zavolejte <xref:System.Data.DataTable.GetChanges%2A> metodu objektu DataTable.

     Následující příklad vytvoří novou tabulku dat `changedRecordsTable` s názvem a naplní ji všemi změněnými záznamy z jiné tabulky dat s názvem `dataTable1` .

     [!code-csharp[VbRaddataEditing#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#15)]
     [!code-vb[VbRaddataEditing#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#15)]

#### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Získání všech záznamů, které mají určitý stav řádku

- Zavolejte `GetChanges` metodu datové sady nebo tabulky dat a předejte <xref:System.Data.DataRowState> hodnotu výčtu jako argument.

     Následující příklad ukazuje, jak vytvořit novou datovou sadu `addedRecords` s názvem a naplnit ji pouze záznamy, které byly přidány do `dataSet1` datové sady.

     [!code-csharp[VbRaddataEditing#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#16)]
     [!code-vb[VbRaddataEditing#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#16)]

- Následující příklad ukazuje, jak vrátit všechny záznamy, které byly nedávno přidány do `Customers` tabulky:

     [!code-csharp[VbRaddataEditing#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#17)]
     [!code-vb[VbRaddataEditing#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#17)]

## <a name="access-the-original-version-of-a-datarow"></a>Přístup k původní verzi objektu DataRow
 Pokud jsou provedeny změny v řádcích dat, datová sada si uchová původní ( <xref:System.Data.DataRowVersion> ) a nové ( <xref:System.Data.DataRowVersion> ) verze řádku. Například před voláním `AcceptChanges` metody může vaše aplikace přistupovat k různým verzím záznamu (jak je definováno ve <xref:System.Data.DataRowVersion> výčtu) a odpovídajícím způsobem zpracovat změny.

> [!NOTE]
> Různé verze řádku existují až po úpravě a před `AcceptChanges` voláním metody. Po `AcceptChanges` volání metody jsou aktuální a původní verze stejné.

 Předání <xref:System.Data.DataRowVersion> hodnoty spolu s indexem sloupce (nebo názvem sloupce jako řetězce) vrátí hodnotu z verze konkrétního řádku daného sloupce. Změněný sloupec se identifikuje během <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.ColumnChanged> událostí a. To je dobrý čas pro kontrolu různých verzí řádků pro účely ověření. Pokud jste však dočasně pozastavili omezení, tyto události nebudou vyvolány a budete muset programově určit, které sloupce se změnily. To můžete provést tak, že provedete iteraci <xref:System.Data.DataTable.Columns%2A> kolekce a porovnáváte různé <xref:System.Data.DataRowVersion> hodnoty.

#### <a name="to-get-the-original-version-of-a-record"></a>Získání původní verze záznamu

- Přejděte k hodnotě sloupce předáním na <xref:System.Data.DataRowVersion> řádku, který chcete vrátit.

     Následující příklad ukazuje, jak použít <xref:System.Data.DataRowVersion> hodnotu k získání původní hodnoty `CompanyName` pole v <xref:System.Data.DataRow> :

     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]

## <a name="access-the-current-version-of-a-datarow"></a>Přístup k aktuální verzi objektu DataRow

#### <a name="to-get-the-current-version-of-a-record"></a>Získání aktuální verze záznamu

- Přistoupit k hodnotě sloupce a poté přidejte parametr do indexu, který označuje, která verze řádku má být vrácena.

     Následující příklad ukazuje, jak použít <xref:System.Data.DataRowVersion> hodnotu k získání aktuální hodnoty `CompanyName` pole v <xref:System.Data.DataRow> :

     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]

## <a name="see-also"></a>Viz také

- [Postupy: Ověřování dat v ovládacím prvku Windows Forms DataGridView](https://msdn.microsoft.com/library/d10aef35-701e-4a3c-a684-2a2ed1aeaca6)
- [Postupy: Zobrazení ikon chyby pro ověřování formuláře pomocí komponenty Windows Forms ErrorProvider](https://msdn.microsoft.com/library/3b681a32-9db4-497b-a34b-34980eabee46)