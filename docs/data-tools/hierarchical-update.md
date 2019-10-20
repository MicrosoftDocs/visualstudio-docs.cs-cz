---
title: Hierarchická aktualizace
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, changed data
- data [Visual Basic], hierarchical update
- saving updated data
- datasets [Visual Basic], hierarchical update
- hierarchical update
- saving data, hierarchical update
- modified data saving
- updated data saving
- related tables, saving
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 33ca9f91c9b1105af43af21a91f25be13e153aa9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648451"
---
# <a name="hierarchical-update"></a>Hierarchická aktualizace

*Hierarchická aktualizace* odkazuje na proces ukládání aktualizovaných dat (z datové sady se dvěma nebo více souvisejícími tabulkami) zpátky do databáze a přitom zachovává pravidla referenční integrity. *Referenční integrita* odkazuje na pravidla konzistence poskytnutá omezeními v databázi, která řídí chování při vkládání, aktualizaci a odstraňování souvisejících záznamů. Jedná se například o referenční integritu, která vynutila vytvoření záznamu zákazníka před tím, než umožní vytvořit objednávky pro daného zákazníka.  Další informace o relacích v datových sadách naleznete v tématu [relace v datových sadách](../data-tools/relationships-in-datasets.md).

Funkce hierarchické aktualizace používá `TableAdapterManager` ke správě `TableAdapter`s v typované datové sadě. Komponenta `TableAdapterManager` je třída vygenerovaná v rámci sady Visual Studio, nikoli typ .NET. Když přetáhnete tabulku z okna **zdroje dat** na stránku Windows Form nebo WPF, Visual Studio přidá proměnnou typu TableAdapterManager do formuláře nebo stránky a zobrazí se v návrháři v zásobníku komponent. Podrobné informace o třídě `TableAdapterManager` naleznete v části Reference k TableAdapterManager v tématu [objekty TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Ve výchozím nastavení datová sada zpracovává související tabulky jako "jenom relace", což znamená, že neuplatňuje omezení cizího klíče. Toto nastavení můžete upravit v době návrhu pomocí **Návrhář datových sad**. Vyberte čáru relace mezi dvěma tabulkami a zobrazte tak dialogové okno **relace** . Změny, které zde provedete, určí způsob, jakým se `TableAdapterManager` chová, když odešlou změny v souvisejících tabulkách zpátky do databáze.

## <a name="enable-hierarchical-update-in-a-dataset"></a>Povolit hierarchickou aktualizaci v datové sadě

Ve výchozím nastavení je hierarchická aktualizace povolena pro všechny nové datové sady, které jsou přidány nebo vytvořeny v projektu. Zapnutí nebo vypnutí hierarchické aktualizace nastavením vlastnosti **hierarchické aktualizace** typované datové sady v datové sadě na **hodnotu true** nebo **false**:

![Nastavení hierarchické aktualizace](../data-tools/media/hierarchical-update-setting.png)

## <a name="create-a-new-relation-between-tables"></a>Vytvoření nové relace mezi tabulkami

Chcete-li vytvořit novou relaci mezi dvěma tabulkami, vyberte v Návrhář datových sad záhlaví každé tabulky, klikněte pravým tlačítkem myši a vyberte možnost **Přidat relaci**.

![Nabídka Přidat relaci hierarchické aktualizace](../data-tools/media/hierarchical-update-add-relation-menu.png)

## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Vysvětlení omezení cizího klíče, kaskádových aktualizací a odstraňování

Je důležité pochopit, jak se v generovaném kódu datové sady vytvoří omezení cizího klíče a kaskádové chování v databázi.

Ve výchozím nastavení jsou tabulky dat v datové sadě vygenerovány se vztahy (<xref:System.Data.DataRelation>), které se shodují s relacemi v databázi. Vztah v datové sadě ale není generovaný jako omezení cizího klíče. @No__t_0 je nakonfigurován jako **vztah pouze** bez <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> nebo <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> v platnosti.

Ve výchozím nastavení jsou kaskádové aktualizace a kaskádové odstranění vypnuté i v případě, že je v relaci databáze nastavená kaskádová aktualizace nebo kaskádová odstranění. Například vytvořením nového zákazníka a nové objednávky a následným pokusem o uložení dat může dojít ke konfliktu s omezeními cizího klíče, které jsou definovány v databázi. Další informace najdete v tématu vypnutí [omezení při naplňování datové sady](turn-off-constraints-while-filling-a-dataset.md).

## <a name="set-the-order-to-perform-updates"></a>Nastavení pořadí provádění aktualizací

Nastavení pořadí provádění aktualizací nastaví pořadí jednotlivých vložení, aktualizací a odstranění, které jsou nutné k uložení všech upravených dat ve všech tabulkách datové sady. Pokud je povolena Hierarchická aktualizace, jsou nejprve provedeny příkazy INSERT a pak aktualizace a pak jsou odstraněny. @No__t_0 poskytuje vlastnost `UpdateOrder`, která se dá nastavit tak, aby prováděla aktualizace, a pak vloží a pak odstraní.

> [!NOTE]
> Je důležité si uvědomit, že pořadí aktualizací je všechny zahrnuté. To znamená, že při provádění aktualizací jsou pro všechny tabulky v datové sadě provedeny vložení a pak odstranění.

Chcete-li nastavit vlastnost `UpdateOrder`, poté po přetahování položek z [okna zdroje dat](add-new-data-sources.md#data-sources-window) do formuláře vyberte `TableAdapterManager` v zásobníku součásti a poté nastavte vlastnost `UpdateOrder` v okně **vlastnosti** .

## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>Vytvoření záložní kopie datové sady před provedením hierarchické aktualizace

Při ukládání dat (voláním metody `TableAdapterManager.UpdateAll()`) se `TableAdapterManager` pokusí aktualizovat data pro každou tabulku v jedné transakci. Pokud některá z částí aktualizace jakékoli tabulky selžou, celá transakce se vrátí zpět. Ve většině případů vrácení zpět vrátí aplikaci do původního stavu.

Někdy ale budete chtít datovou sadu obnovit ze záložní kopie. K tomu může dojít v případě, že používáte hodnoty automatického zvýšení. Například pokud operace uložení není úspěšná, hodnoty automatického zvýšení nejsou v datové sadě resetovány a datová sada bude nadále vytvářet hodnoty automatického zvýšení. To zaznamená mezeru v číslování, které nemusí být přijatelné ve vaší aplikaci. V situacích, kde se jedná o problém, `TableAdapterManager` poskytuje vlastnost `BackupDataSetBeforeUpdate`, která nahradí existující datovou sadu záložní kopií, pokud transakce není úspěšná.

> [!NOTE]
> Záložní kopie je v paměti pouze v případě, že je spuštěna metoda `TableAdapterManager.UpdateAll`. Proto neexistuje žádný programový přístup k této datové sadě zálohování, protože buď nahradí původní datovou sadu, nebo se překročí k oboru, jakmile `TableAdapterManager.UpdateAll` metoda dokončí.

## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>Upravte generovaný kód pro uložení, aby se provedla Hierarchická aktualizace.

Uložte změny ze souvisejících tabulek dat v datové sadě do databáze voláním metody `TableAdapterManager.UpdateAll` a předáním názvu datové sady, která obsahuje tabulky v relaci. Například spusťte metodu `TableAdapterManager.UpdateAll(NorthwindDataset)` pro odeslání aktualizací ze všech tabulek v NorthwindDataset do back-endové databáze.

Po vyřazení položek z okna **zdroje dat** je kód automaticky přidán do události `Form_Load` pro naplnění každé tabulky (`TableAdapter.Fill` metody). Pro uložení dat z datové sady zpět do databáze (metoda `TableAdapterManager.UpdateAll`) se na událost <xref:System.Windows.Forms.BindingNavigator> tlačítka **Uložit** přidá i kód.

Generovaný kód pro uložení obsahuje také řádek kódu, který volá metodu `CustomersBindingSource.EndEdit`. Konkrétně volá metodu <xref:System.Windows.Forms.BindingSource.EndEdit%2A> prvního <xref:System.Windows.Forms.BindingSource>that přidané do formuláře. Jinými slovy, tento kód je generován pouze pro první tabulku, která je přetažena z okna **zdroje dat** do formuláře. @No__t_0 volání potvrdí všechny změny, které jsou zpracovávány v rámci všech právě upravovaných ovládacích prvků vázaných na data. Proto pokud ovládací prvek vázaný na data stále obsahuje fokus a kliknete na tlačítko **Uložit** , všechny čekající úpravy v tomto ovládacím prvku se potvrdí před samotným uložením (`TableAdapterManager.UpdateAll` metoda).

> [!NOTE]
> **Návrhář datových sad** přidá pouze `BindingSource.EndEdit` kód první tabulky, která je na formuláři vynechána. Proto je nutné přidat řádek kódu pro volání metody `BindingSource.EndEdit` pro každou tabulku v relaci ve formuláři. Pro tento návod to znamená, že musíte přidat volání metody `OrdersBindingSource.EndEdit`.

### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>Aktualizace kódu pro potvrzení změn v souvisejících tabulkách před uložením

1. Dvojitým kliknutím na tlačítko **Uložit** na <xref:System.Windows.Forms.BindingNavigator> otevřete **Form1** v editoru kódu.

2. Přidejte řádek kódu pro volání metody `OrdersBindingSource.EndEdit` po řádku, který volá metodu `CustomersBindingSource.EndEdit`. Kód v události kliknutí na tlačítko pro **uložení** by měl vypadat přibližně takto:

     [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/VisualBasic/hierarchical-update_1.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/CSharp/hierarchical-update_1.cs)]

Kromě potvrzení změn v související podřízené tabulce před uložením dat do databáze může být také nutné potvrdit nově vytvořené nadřazené záznamy před přidáním nových podřízených záznamů do datové sady. Jinými slovy, možná budete muset přidat nový nadřazený záznam (`Customer`) do datové sady před omezením cizího klíče, aby bylo možné přidat nové podřízené záznamy (`Orders`) do datové sady. K tomu můžete použít podřízenou událost `BindingSource.AddingNew`.

> [!NOTE]
> Bez ohledu na to, jestli je potřeba potvrdit nové nadřazené záznamy, závisí na typu ovládacího prvku, který se používá k vytvoření vazby k vašemu zdroji dat. V tomto návodu použijete jednotlivé ovládací prvky pro svázání s nadřazenou tabulkou. K tomu je potřeba další kód pro potvrzení nového nadřazeného záznamu. Pokud se nadřazené záznamy místo toho zobrazovaly ve složitém ovládacím prvku vazby, jako je <xref:System.Windows.Forms.DataGridView>, nebudete muset toto dodatečné volání <xref:System.Windows.Forms.BindingSource.EndEdit%2A> pro nadřazený záznam. Důvodem je, že základní funkce datové vazby ovládacího prvku zpracovává potvrzení nových záznamů.

### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>Přidání kódu pro potvrzení nadřazených záznamů v datové sadě před přidáním nových podřízených záznamů

1. Vytvořte obslužnou rutinu události pro událost `OrdersBindingSource.AddingNew`.

    - Otevřete **Form1** v zobrazení Návrh, v části zásobník komponent vyberte **OrdersBindingSource** , v okně **vlastnosti** vyberte **události** a potom poklikejte na událost **obsloužíte** .

2. Přidejte řádek kódu do obslužné rutiny události, která volá metodu `CustomersBindingSource.EndEdit`. Kód v obslužné rutině události `OrdersBindingSource_AddingNew` by měl vypadat takto:

     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/VisualBasic/hierarchical-update_2.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/CSharp/hierarchical-update_2.cs)]

## <a name="tableadaptermanager-reference"></a>Odkaz na TableAdapterManager

Ve výchozím nastavení se třída `TableAdapterManager` generuje, když vytvoříte datovou sadu, která obsahuje tabulky v relaci. Chcete-li zabránit vygenerování třídy, změňte hodnotu vlastnosti `Hierarchical Update` datové sady na false. Když přetáhnete tabulku, která má relaci, na návrhovou plochu stránky Windows Form nebo WPF, Visual Studio deklaruje členskou proměnnou třídy. Pokud datovou vazbu nepoužíváte, je nutné ručně deklarovat proměnnou.

Třída `TableAdapterManager` není typu .NET. Proto se v dokumentaci nemůžete podívat. Je vytvořena v době návrhu v rámci procesu vytváření datové sady.

Následující jsou často používané metody a vlastnosti `TableAdapterManager` třídy:

|Člen|Popis|
|------------|-----------------|
|`UpdateAll` – metoda|Uloží všechna data ze všech tabulek dat.|
|`BackUpDataSetBeforeUpdate` – vlastnost|Určuje, zda má být před provedením metody `TableAdapterManager.UpdateAll` vytvořena záložní kopie datové sady. Datového.|
|vlastnost *tableName* `TableAdapter`|Představuje `TableAdapter`. Vygenerovaná `TableAdapterManager` obsahuje vlastnost pro každý `TableAdapter`, která spravuje. Například datová sada s tabulkou Customers and Orders je vygenerována s `TableAdapterManager`, která obsahuje vlastnosti `CustomersTableAdapter` a `OrdersTableAdapter`.|
|`UpdateOrder` – vlastnost|Určuje pořadí jednotlivých příkazů INSERT, Update a DELETE. Nastavte tuto hodnotu na jednu z hodnot ve výčtu `TableAdapterManager.UpdateOrderOption`.<br /><br /> Ve výchozím nastavení je `UpdateOrder` nastavena na **InsertUpdateDelete**. To znamená, že vložení, následné aktualizace a následné odstranění jsou prováděny pro všechny tabulky v datové sadě.|

## <a name="see-also"></a>Viz také:

- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)
