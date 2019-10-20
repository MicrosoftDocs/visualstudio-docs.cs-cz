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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ab2bd92b5636c89027c9c5954567be8048c1b152
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648227"
---
# <a name="save-data-back-to-the-database"></a>Ukládání dat zpět do databáze

Datová sada je kopie dat v paměti. Pokud tato data upravíte, je vhodné tyto změny uložit zpět do databáze. Provedete to jedním ze tří způsobů:

- Voláním jedné z `Update` metod TableAdapter

- Voláním jedné z `DBDirect` metod TableAdapter

- Voláním metody `UpdateAll` v TableAdapterManager, kterou sada Visual Studio generuje za vás, když datová sada obsahuje tabulky, které souvisejí s jinými tabulkami v datové sadě.

Když vytvoříte datovou datovou vazbu tabulek pro ovládací prvky na stránce Windows Form nebo XAML, architektura datových vazeb provede veškerou práci za vás.

Pokud jste obeznámeni s objekty TableAdapter, můžete přejít přímo na jedno z následujících témat:

|Téma|Popis|
|-----------|-----------------|
|[Vkládání nových záznamů do databáze](../data-tools/insert-new-records-into-a-database.md)|Jak provádět aktualizace a vkládat pomocí objektů objekty TableAdapter nebo Command|
|[Aktualizace dat pomocí objektu TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)|Jak provádět aktualizace pomocí objekty TableAdapter|
|[Hierarchická aktualizace](../data-tools/hierarchical-update.md)|Jak provádět aktualizace z datové sady se dvěma nebo více souvisejícími tabulkami|
|[Zpracování výjimky souběžnosti](../data-tools/handle-a-concurrency-exception.md)|Postup zpracování výjimek v případě, že se dva uživatelé pokoušejí změnit stejná data v databázi ve stejnou dobu|
|[Postupy: ukládání dat pomocí transakce](../data-tools/save-data-by-using-a-transaction.md)|Uložení dat v transakci pomocí systému. Obor názvů pro transakce a objekt TransactionScope|
|[Uložení dat do transakce](../data-tools/save-data-in-a-transaction.md)|Návod, který vytváří aplikaci model Windows Forms k předvedení ukládání dat do databáze v rámci transakce|
|[Uložení dat do databáze (více tabulek)](../data-tools/save-data-to-a-database-multiple-tables.md)|Postup úpravy záznamů a uložení změn v několika tabulkách zpět do databáze|
|[Uložení dat z objektu do databáze](../data-tools/save-data-from-an-object-to-a-database.md)|Předání dat z objektu, který není v datové sadě, do databáze pomocí metody DbDirect TableAdapter|
|[Ukládání dat pomocí metod TableAdapter DBDirect](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|Jak používat TableAdapter k posílání dotazů SQL přímo do databáze|
|[Uložení datové sady ve formátu XML](../data-tools/save-a-dataset-as-xml.md)|Uložení datové sady do dokumentu XML|

## <a name="two-stage-updates"></a>Aktualizace se dvěma fázemi

Aktualizace zdroje dat je proces se dvěma kroky. Prvním krokem je aktualizovat datovou sadu o nové záznamy, změněné záznamy nebo odstraněné záznamy. Pokud vaše aplikace tyto změny nikdy neodešle zpět do zdroje dat, budete hotovi s aktualizací.

Pokud změny odešlete zpět do databáze, je vyžadován druhý krok. Pokud nepoužíváte ovládací prvky vázané na data, je nutné ručně zavolat metodu `Update` stejného TableAdapter (nebo datový adaptér), který jste použili k naplnění datové sady. Můžete ale také použít různé adaptéry, například pro přesun dat z jednoho zdroje dat do jiného nebo pro aktualizaci více zdrojů dat. Pokud nepoužíváte datovou vazbu a ukládáte změny v souvisejících tabulkách, je nutné ručně vytvořit instanci proměnné automaticky generované `TableAdapterManager` třídy a pak zavolat metodu `UpdateAll`.

![Koncepční diagram aktualizací datových sad](../data-tools/media/vbdatasetupdates.gif)

Datová sada obsahuje kolekce tabulek, které obsahují kolekce řádků. Pokud máte v úmyslu později aktualizovat příslušný zdroj dat, je nutné při přidávání nebo odebírání řádků použít metody vlastnosti `DataTable.DataRowCollection`. Tyto metody provádějí sledování změn, které je potřeba pro aktualizaci zdroje dat. Pokud zavoláte kolekci `RemoveAt` u vlastnosti Rows, odstranění nebude oznámeno zpět do databáze.

## <a name="merge-datasets"></a>Sloučit datové sady

Obsah datové sady můžete aktualizovat tak, že ji *sloučíte* s jinou datovou sadou. To zahrnuje kopírování obsahu *zdrojové* datové sady do volající datové sady (označované jako *cílová* datová sada). Při sloučení datových sad jsou do cílové sady dat přidány nové záznamy ve zdrojové datové sadě. Kromě toho jsou do cílové sady dat přidány nadbytečné sloupce ve zdrojové datové sadě. Sloučení datových sad je užitečné v případě, že máte místní datovou sadu a druhou datovou sadu získáte z jiné aplikace. Je to také užitečné, když dostanete druhou datovou sadu z komponenty, jako je například webová služba XML, nebo když potřebujete integrovat data z více datových sad.

Při slučování datových sad můžete předat logický argument (`preserveChanges`), který instruuje metodu <xref:System.Data.DataSet.Merge%2A>, zda chcete zachovat existující úpravy v cílové datové sadě. Vzhledem k tomu, že datové sady uchovávají více verzí záznamů, je důležité mít na paměti, že slučuje více než jedna verze záznamů. Následující tabulka ukazuje, jak se sloučí záznam ve dvou datových sadách:

|DataRowVersion|Cílová datová sada|Zdrojová datová sada|
| - | - | - |
|Původně|James Wilson|James C. Wilson|
|Aktivní|Jim Wilson|James C. Wilson|

Volání metody <xref:System.Data.DataSet.Merge%2A> v předchozí tabulce s `preserveChanges=false targetDataset.Merge(sourceDataset)` má za následek následující data:

|DataRowVersion|Cílová datová sada|Zdrojová datová sada|
| - | - | - |
|Původně|James C. Wilson|James C. Wilson|
|Aktivní|James C. Wilson|James C. Wilson|

Volání metody <xref:System.Data.DataSet.Merge%2A> s `preserveChanges = true targetDataset.Merge(sourceDataset, true)` má za následek následující data:

|DataRowVersion|Cílová datová sada|Zdrojová datová sada|
| - | - | - |
|Původně|James C. Wilson|James C. Wilson|
|Aktivní|Jim Wilson|James C. Wilson|

> [!CAUTION]
> Pokud je v `preserveChanges = true` scénáři volána metoda <xref:System.Data.DataSet.RejectChanges%2A> na záznamu v cílové datové sadě, vrátí se původní data ze *zdrojové* datové sady. To znamená, že pokud se pokusíte aktualizovat původní zdroj dat cílovou datovou sadou, nemusí být možné najít původní řádek, který se má aktualizovat. Narušení souběžnosti můžete zabránit tak, že naplníte jinou datovou sadu pomocí aktualizovaných záznamů ze zdroje dat a následným sloučením zabráníte narušení souběžnosti. (K narušení souběžnosti dojde, když jiný uživatel upraví záznam ve zdroji dat poté, co byla datová sada vyplněna.)

## <a name="update-constraints"></a>Aktualizovat omezení

Chcete-li provést změny v existujícím řádku dat, přidejte nebo aktualizujte data v jednotlivých sloupcích. Pokud datová sada obsahuje omezení (například cizí klíče nebo omezení nepovolující hodnotu null), je možné, že záznam bude dočasně v chybovém stavu, když ho aktualizujete. To znamená, že může být v chybovém stavu po dokončení aktualizace jednoho sloupce, ale před tím, než se dostanete k dalšímu.

Aby nedocházelo k předčasnému narušení omezení, můžete dočasně pozastavit omezení aktualizace. To slouží dvěma účelům:

- Zabrání vyvolání chyby po dokončení aktualizace jednoho sloupce, ale nezačala aktualizovat jiný.

- Zabrání tomu, aby se určité události aktualizace vyvolaly (události, které se často používají k ověření).

> [!NOTE]
> V model Windows Forms architektura datové vazby, která je integrována do ovládacího prvku DataGrid, pozastaví kontrolu omezení, dokud se fokus nepřesune mimo řádek, a nemusíte explicitně volat metody <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A> nebo <xref:System.Data.DataRow.CancelEdit%2A>.

Omezení jsou automaticky zakázána, pokud je metoda <xref:System.Data.DataSet.Merge%2A> vyvolána pro datovou sadu. Pokud je sloučení dokončeno, pokud existují nějaká omezení pro datovou sadu, která nemůže být povolena, je vyvolána <xref:System.Data.ConstraintException>. V této situaci je vlastnost <xref:System.Data.DataSet.EnforceConstraints%2A> nastavena na `false,` a před resetováním vlastnosti <xref:System.Data.DataSet.EnforceConstraints%2A> na `true` je nutné vyřešit všechna porušení omezení.

Po dokončení aktualizace můžete znovu povolit kontrolu omezení, která také znovu povolí události aktualizace a vyvolává je.

Další informace o pozastavení událostí naleznete v tématu vypnutí [omezení při naplňování datové sady](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

## <a name="dataset-update-errors"></a>Chyby aktualizace datové sady

Když aktualizujete záznam v datové sadě, existuje možnost chyby. Například může nechtěně zapisovat data nesprávného typu do sloupce nebo data, která jsou příliš dlouhá, nebo data, která mají nějaký problém s integritou. Nebo je možné, že máte kontroly ověřování specifické pro aplikaci, které mohou vyvolat vlastní chyby v jakékoli fázi události aktualizace. Další informace najdete v tématu [ověření dat v datových sadách](../data-tools/validate-data-in-datasets.md).

## <a name="maintain-information-about-changes"></a>Udržovat informace o změnách

Informace o změnách v datové sadě jsou uchovávány dvěma způsoby: pomocí označení řádků, které označují, že se změnily (<xref:System.Data.DataRow.RowState%2A>), a udržováním více kopií záznamu (<xref:System.Data.DataRowVersion>). Pomocí těchto informací můžou procesy zjistit, co se v datové sadě změnilo, a může odesílat příslušné aktualizace ke zdroji dat.

### <a name="rowstate-property"></a>Vlastnost RowState

Vlastnost <xref:System.Data.DataRow.RowState%2A> objektu <xref:System.Data.DataRow> je hodnota, která poskytuje informace o stavu konkrétního řádku dat.

Následující tabulka popisuje možné hodnoty výčtu <xref:System.Data.DataRowState>:

|Hodnota nezměněnou DataRowState|Popis|
| - |-----------------|
|<xref:System.Data.DataRowState.Added>|Řádek byl přidán jako položka do <xref:System.Data.DataRowCollection>. (Řádek v tomto stavu nemá odpovídající původní verzi, protože neexistovala při volání poslední <xref:System.Data.DataRow.AcceptChanges%2A> metody).|
|<xref:System.Data.DataRowState.Deleted>|Řádek byl odstraněn pomocí <xref:System.Data.DataRow.Delete%2A> objektu <xref:System.Data.DataRow>.|
|<xref:System.Data.DataRowState.Detached>|Řádek byl vytvořen, ale není součástí žádného <xref:System.Data.DataRowCollection>. Objekt <xref:System.Data.DataRow> je v tomto stavu bezprostředně po jeho vytvoření, před jeho přidáním do kolekce a poté, co byl odebrán z kolekce.|
|<xref:System.Data.DataRowState.Modified>|Hodnota sloupce v řádku se změnila nějakým způsobem.|
|<xref:System.Data.DataRowState.Unchanged>|Řádek se od posledního volání <xref:System.Data.DataRow.AcceptChanges%2A> nezměnil.|

### <a name="datarowversion-enumeration"></a>Výčet DataRowVersion

Datové sady uchovávají více verzí záznamů. Pole <xref:System.Data.DataRowVersion> se používají při načítání hodnoty nalezené v <xref:System.Data.DataRow> pomocí vlastnosti <xref:System.Data.DataRow.Item%2A> nebo metody <xref:System.Data.DataRow.GetChildRows%2A> objektu <xref:System.Data.DataRow>.

Následující tabulka popisuje možné hodnoty výčtu <xref:System.Data.DataRowVersion>:

|Hodnota DataRowVersion|Popis|
| - |-----------------|
|<xref:System.Data.DataRowVersion.Current>|Aktuální verze záznamu obsahuje všechny změny, které byly provedeny u záznamu od posledního volání <xref:System.Data.DataRow.AcceptChanges%2A>. Pokud byl řádek odstraněn, není k dispozici žádná aktuální verze.|
|<xref:System.Data.DataRowVersion.Default>|Výchozí hodnota záznamu definovaná schématem DataSet nebo zdrojem dat.|
|<xref:System.Data.DataRowVersion.Original>|Původní verze záznamu je kopií záznamu, protože se jednalo o poslední změny, které byly v datové sadě potvrzeny. V praktických případech je to obvykle verze záznamu načtené ze zdroje dat.|
|<xref:System.Data.DataRowVersion.Proposed>|Navrhovaná verze záznamu, která je k dispozici dočasně v průběhu aktualizace, tedy mezi časem, kdy jste volali metodu <xref:System.Data.DataRow.BeginEdit%2A> a metodu <xref:System.Data.DataRow.EndEdit%2A>. Obvykle přistupujete k navržené verzi záznamu v obslužné rutině pro událost, jako je například <xref:System.Data.DataTable.RowChanging>. Vyvolání metody <xref:System.Data.DataRow.CancelEdit%2A> obrátí změny a odstraní navrhovanou verzi řádku dat.|

Původní a aktuální verze jsou užitečné, když jsou informace o aktualizaci přeneseny do zdroje dat. Když se ve zdroji dat pošle aktualizace, jsou nové informace pro databázi v aktuální verzi záznamu. Informace z původní verze slouží k vyhledání záznamu, který chcete aktualizovat.

Například v případě, kdy se změní primární klíč záznamu, potřebujete způsob, jak vyhledat správný záznam ve zdroji dat, aby bylo možné změny aktualizovat. Pokud neexistovala žádná původní verze, záznam by byl pravděpodobně připojen ke zdroji dat, což vedlo nejen k nadbytečnému záznamu, který je nepřesný, ale v jednom záznamu, který je nepřesný a zastaralý. Dvě verze jsou také používány v řízení souběžnosti. Původní verzi můžete porovnat s záznamem ve zdroji dat, abyste zjistili, jestli se záznam změnil od chvíle, kdy byl načten do datové sady.

Navrhovaná verze je užitečná v případě, že je nutné provést ověření před samotným potvrzením změn v datové sadě.

I když se záznamy změnily, neexistují vždy původní nebo aktuální verze daného řádku. Když do tabulky vložíte nový řádek, není k dispozici žádná původní verze, pouze aktuální verze. Podobně platí, že pokud řádek odstraníte voláním metody `Delete` tabulky, bude k dispozici původní verze, ale aktuální verze neexistuje.

V případě, že se dotazuje na metodu <xref:System.Data.DataRow.HasVersion%2A> datového řádku, můžete otestovat, zda existuje konkrétní verze záznamu. Můžete získat přístup k libovolné verzi záznamu předáním <xref:System.Data.DataRowVersion> hodnoty výčtu jako volitelného argumentu při požadavku na hodnotu sloupce.

## <a name="get-changed-records"></a>Získat změněné záznamy

Běžným postupem není aktualizovat všechny záznamy v datové sadě. Uživatel může například pracovat s ovládacím prvkem model Windows Forms <xref:System.Windows.Forms.DataGridView>, který zobrazí mnoho záznamů. Uživatel ale může aktualizovat jenom několik záznamů, odstranit ho a vložit nový. Datové sady a tabulky dat poskytují metodu (`GetChanges`) pro vrácení pouze změněných řádků.

Můžete vytvořit podmnožiny změněných záznamů pomocí metody `GetChanges` buď tabulky dat (<xref:System.Data.DataTable.GetChanges%2A>), nebo samotné datové sady (<xref:System.Data.DataSet.GetChanges%2A>). Pokud voláte metodu pro tabulku dat, vrátí kopii tabulky s pouze změněnými záznamy. Podobně pokud voláte metodu pro datovou sadu, získáte novou datovou sadu s pouze změněnými záznamy.

`GetChanges` sám vrátí všechny změněné záznamy. Na rozdíl od předání požadované <xref:System.Data.DataRowState> jako parametru do metody `GetChanges` můžete určit, jakou podmnožinu změn mají změněné záznamy: nově přidané záznamy, záznamy, které jsou označené k odstranění, odpojené záznamy nebo upravené záznamy.

Získání podmnožiny změněných záznamů je užitečné, pokud chcete odesílat záznamy do jiné komponenty ke zpracování. Místo odeslání celé datové sady můžete snížit režijní náklady na komunikaci s ostatními komponentou tím, že získáte pouze ty záznamy, které součást potřebuje.

## <a name="commit-changes-in-the-dataset"></a>Potvrdit změny v datové sadě

Při provádění změn v datové sadě je nastavena vlastnost <xref:System.Data.DataRow.RowState%2A> změněných řádků. Původní a aktuální verze záznamů jsou zavedeny, udržovány a zpřístupněny pro vás vlastností <xref:System.Data.DataRowView.RowVersion%2A>. Metadata, která jsou uložena ve vlastnostech těchto změněných řádků, jsou nutná k odeslání správných aktualizací ke zdroji dat.

Pokud se změny projeví v aktuálním stavu zdroje dat, nebudete už tyto informace uchovávat. Obvykle existují dvě doby, kdy je datová sada a její zdroj synchronizovány:

- Ihned po načtení informací do datové sady, například při čtení dat ze zdroje.

- Po odeslání změn z datové sady do zdroje dat (ale ne dříve, protože byste ztratili informace o změně, které jsou nutné k odeslání změn do databáze).

Můžete potvrdit nedokončené změny datové sady voláním metody <xref:System.Data.DataSet.AcceptChanges%2A>. Obvykle je <xref:System.Data.DataSet.AcceptChanges%2A> volána v následujících časech:

- Po načtení datové sady. Pokud načtete datovou sadu voláním metody `Fill` TableAdapter, adaptér automaticky potvrdí změny. Pokud však načtete datovou sadu tím, že do ní sloučíte jinou datovou sadu, je nutné změny potvrdit ručně.

    > [!NOTE]
    > Adaptéru můžete zabránit v automatickém potvrzení změn při volání metody `Fill` nastavením vlastnosti `AcceptChangesDuringFill` adaptéru na `false`. Pokud je nastavená na `false`, <xref:System.Data.DataRow.RowState%2A> každého řádku, který je vložený během Fill, se nastaví na <xref:System.Data.DataRowState.Added>.

- Po odeslání změn datové sady do jiného procesu, jako je například webová služba XML.

    > [!CAUTION]
    > Potvrzení změn tímto způsobem smaže všechny informace o změně. Neprovádějte změny, dokud nedokončíte provádění operací, které vyžadují, aby vaše aplikace věděla, jaké změny byly provedeny v datové sadě.

Tato metoda dosahuje následujících kroků:

- Zapíše <xref:System.Data.DataRowVersion.Current> verzi záznamu do jeho <xref:System.Data.DataRowVersion.Original> verze a přepíše původní verzi.

- Odebere všechny řádky, u kterých je vlastnost <xref:System.Data.DataRow.RowState%2A> nastavena na hodnotu <xref:System.Data.DataRowState.Deleted>.

- Nastaví vlastnost <xref:System.Data.DataRow.RowState%2A> záznamu na <xref:System.Data.DataRowState.Unchanged>.

Metoda <xref:System.Data.DataSet.AcceptChanges%2A> je k dispozici na třech úrovních. Můžete ji zavolat na objekt <xref:System.Data.DataRow> a potvrdit tak změny pouze pro daný řádek. Můžete ji také zavolat na objekt <xref:System.Data.DataTable> pro potvrzení všech řádků v tabulce. Nakonec můžete zavolat na objekt <xref:System.Data.DataSet> a potvrdit všechny probíhající změny ve všech záznamech všech tabulek datové sady.

Následující tabulka popisuje, které změny jsou potvrzeny na základě objektu, na kterém je metoda volána:

|Metoda|Výsledek|
|------------|------------|
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Změny jsou potvrzeny pouze na konkrétní řádek.|
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Změny jsou potvrzeny na všech řádcích v konkrétní tabulce.|
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Změny jsou potvrzeny na všech řádcích ve všech tabulkách datové sady.|

> [!NOTE]
> Pokud načtete datovou sadu voláním metody `Fill` TableAdapter, nemusíte explicitně přijímat změny. Ve výchozím nastavení metoda `Fill` volá metodu `AcceptChanges` poté, co dokončí vyplnění tabulky dat.

Související metoda, <xref:System.Data.DataSet.RejectChanges%2A>, vrátí zpět účinek změn kopírováním <xref:System.Data.DataRowVersion.Original> verze zpátky do <xref:System.Data.DataRowVersion.Current> verze záznamů. Také nastaví <xref:System.Data.DataRow.RowState%2A> každého záznamu zpět na <xref:System.Data.DataRowState.Unchanged>.

## <a name="data-validation"></a>Ověření dat

Aby bylo možné ověřit, že data ve vaší aplikaci splňují požadavky procesů, do kterých je předána, často je nutné přidat ověřování. To může zahrnovat kontrolu správnosti vstupu uživatele ve formuláři, ověřování dat odesílaných do vaší aplikace jinou aplikací nebo dokonce kontrola, že informace, které jsou vypočítány v rámci vaší komponenty, spadají do omezení zdroje dat. a požadavky aplikací.

Data můžete ověřit několika způsoby:

- Do obchodní vrstvy přidáním kódu do aplikace pro ověření dat. Tato datová sada je na jednom místě, kterou můžete provést. Datová sada poskytuje některé výhody ověřování back-endu – například schopnost ověřovat změny v případě změny hodnot sloupců a řádků. Další informace najdete v tématu [ověření dat v datových sadách](../data-tools/validate-data-in-datasets.md).

- V prezentační vrstvě přidáním ověřování do formulářů. Další informace najdete v tématu [ověření vstupu uživatele v model Windows Forms](/dotnet/framework/winforms/user-input-validation-in-windows-forms).

- V back-endu dat odesláním dat do zdroje dat, například databáze, a povolením, aby data přijímal nebo odmítal. Pokud pracujete s databází, která má sofistikovaná zařízení pro ověřování dat a poskytování informací o chybách, může to být praktický přístup, protože můžete ověřit data bez ohledu na to, odkud pocházejí. Tento přístup ale nemusí vyhovovat požadavkům na ověření specifickým pro aplikaci. Kromě toho je možné, že se zdrojem dat ověřit data může v závislosti na tom, jak vaše aplikace usnadňuje řešení chyb ověřování vyvolaných back-end, způsobit velký počet cest ke zdroji dat.

   > [!IMPORTANT]
   > Při použití datových příkazů s vlastností <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> nastavenou na hodnotu <xref:System.Data.CommandType.Text> pečlivě zkontrolujte informace, které se odesílají z klienta před předáním do vaší databáze. Uživatelé se zlými úmysly se můžou pokusit odeslat (vložit) upravené nebo další příkazy SQL za účelem získání neoprávněného přístupu nebo poškození databáze. Před přenosem vstupu uživatele do databáze vždy ověřte, zda jsou informace platné. Osvědčeným postupem je vždy použít parametrizované dotazy nebo uložené procedury, pokud je to možné.

## <a name="transmit-updates-to-the-data-source"></a>Odeslání aktualizací do zdroje dat

Po provedení změn v datové sadě můžete přenést změny do zdroje dat. Nejčastěji to provedete tak, že zavoláte metodu `Update` TableAdapter (nebo datového adaptéru). Metoda projde každým záznamem v tabulce dat a určí, jaký typ aktualizace je vyžadován (aktualizace, vložení nebo odstranění), pokud existuje, a potom spustí příslušný příkaz.

Jako příklad toho, jak se provádí aktualizace, Předpokládejme, že vaše aplikace používá datovou sadu, která obsahuje jedinou datovou tabulku. Aplikace načte dva řádky z databáze. Po načtení bude tabulka dat v paměti vypadat takto:

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Unchanged)    c400         Nancy Buchanan    Pending
```

Vaše aplikace změní stav Petra Novák na upřednostňovanou. V důsledku této změny se hodnota vlastnosti <xref:System.Data.DataRow.RowState%2A> pro daný řádek změní z <xref:System.Data.DataRowState.Unchanged> na <xref:System.Data.DataRowState.Modified>. Hodnota vlastnosti <xref:System.Data.DataRow.RowState%2A> pro první řádek zůstane <xref:System.Data.DataRowState.Unchanged>. Tabulka dat teď vypadá takto:

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Modified)     c400         Nancy Buchanan    Preferred
```

Vaše aplikace nyní volá metodu `Update` pro přenos datové sady do databáze. Metoda zkontroluje každý řádek zase. Pro první řádek metoda přenáší do databáze žádné příkazy SQL, protože se tento řádek od původního načtení z databáze nezměnil.

Pro druhý řádek však metoda `Update` automaticky vyvolá správný datový příkaz a přenáší ji do databáze. Konkrétní syntaxe příkazu jazyka SQL závisí na dialektu jazyka SQL, který je podporován podkladovým úložištěm dat. Následující obecné vlastnosti přenášeného příkazu SQL jsou ale zajímavosti:

- Přenesený příkaz SQL je příkaz UPDATE. Adaptér ví, že má použít příkaz UPDATE, protože hodnota vlastnosti <xref:System.Data.DataRow.RowState%2A> je <xref:System.Data.DataRowState.Modified>.

- Přenesený příkaz SQL zahrnuje klauzuli WHERE, která označuje, že cíl příkazu UPDATE je řádek, kde `CustomerID = 'c400'`. Tato část příkazu SELECT odlišuje cílový řádek od všech ostatních, protože `CustomerID` je primárním klíčem cílové tabulky. Informace pro klauzuli WHERE jsou odvozeny z původní verze záznamu (`DataRowVersion.Original`) pro případ, že hodnoty, které jsou požadovány k identifikaci řádku, byly změněny.

- Přenesený příkaz SQL zahrnuje klauzuli SET pro nastavení nových hodnot upravených sloupců.

   > [!NOTE]
   > Pokud byla vlastnost `UpdateCommand` TableAdapter nastavena na název uložené procedury, adaptér nevytvoří příkaz SQL. Místo toho vyvolá uloženou proceduru s příslušnými parametry předanými.

## <a name="pass-parameters"></a>Předat parametry

Obvykle používáte parametry k předání hodnot záznamů, které se budou aktualizovat v databázi. Když `Update` metoda TableAdapter spustí příkaz UPDATE, musí vyplnit hodnoty parametru. Získává tyto hodnoty z kolekce `Parameters` pro příslušný datový příkaz – v tomto případě objekt `UpdateCommand` v TableAdapter.

Pokud jste použili nástroje sady Visual Studio k vygenerování datového adaptéru, objekt `UpdateCommand` obsahuje kolekci parametrů, které odpovídají jednotlivým zástupným symbolům parametrů v příkazu.

Vlastnost <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> každého parametru odkazuje na sloupec v tabulce dat. Například vlastnost `SourceColumn` pro parametry `au_id` a `Original_au_id` je nastavena na libovolný sloupec v tabulce dat obsahuje ID autora. Když se metoda `Update` adaptéru spustí, přečte sloupec ID autora ze záznamu, který se aktualizuje, a vyplní hodnoty do příkazu.

V příkazu UPDATE je nutné zadat jak nové hodnoty (ty, které budou zapsány do záznamu), tak i staré hodnoty (aby se záznam mohl nacházet v databázi). Existují proto dva parametry pro každou hodnotu: jeden pro klauzuli SET a jinou pro klauzuli WHERE. Oba parametry čtou data z aktualizovaného záznamu, ale získají různé verze hodnoty sloupce založené na vlastnosti <xref:System.Data.SqlClient.SqlParameter.SourceVersion> parametru. Parametr klauzule SET získá aktuální verzi a parametr klauzule WHERE získá původní verzi.

> [!NOTE]
> Hodnoty můžete také nastavit v kolekci `Parameters` sami v kódu, což byste obvykle provedete v obslužné rutině události <xref:System.Data.DataTable.RowChanging> události datového adaptéru.

## <a name="see-also"></a>Viz také:

- [Nástroje datových sad v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Vytvoření a konfigurace objektů TableAdapter](create-and-configure-tableadapters.md)
- [Aktualizace dat pomocí objektu TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Ověřit data](validate-data-in-datasets.md)
- [Postupy: přidávání, úpravy a odstraňování entit (WCF Data Services)](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)