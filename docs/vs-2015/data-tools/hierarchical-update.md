---
title: Hierarchická aktualizace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99e19bce34c2bc8578a062c87aaef10302589075
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670025"
---
# <a name="hierarchical-update"></a>Hierarchická aktualizace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hierarchická aktualizace * odkazuje na proces ukládání aktualizovaných dat (z datové sady se dvěma nebo více souvisejícími tabulkami) zpátky do databáze a přitom zachovává pravidla referenční integrity. *Referenční integrita* odkazuje na pravidla konzistence poskytnutá omezeními v databázi, která řídí chování při vkládání, aktualizaci a odstraňování souvisejících záznamů. Jedná se například o referenční integritu, která vynutila vytvoření záznamu zákazníka před tím, než umožní vytvořit objednávky pro daného zákazníka.  Další informace o relacích v datových sadách najdete v tématu [relace v datových sadách](../data-tools/relationships-in-datasets.md) .

 Funkce hierarchické aktualizace používá `TableAdapterManager` ke správě sady `TableAdapter` s v typované datové sadě. `TableAdapterManager`Komponenta je [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vygenerovaná třídou, takže není součástí [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Když přetáhnete tabulku z okna zdroje dat na stránku Windows Form nebo WPF, Visual Studio přidá proměnnou typu TableAdapterManager do formuláře nebo stránky a zobrazí se v návrháři v zásobníku komponent. Podrobné informace o `TableAdapterManager` třídě naleznete v části TableAdapterManager reference tématu [TableAdapterManager Overview](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).

 Ve výchozím nastavení datová sada zpracovává související tabulky jako "jenom relace", což znamená, že neuplatňuje omezení cizího klíče. Toto nastavení můžete upravit v době návrhu pomocí Návrhář datových sad. Vyberte čáru relace mezi dvěma tabulkami a zobrazte tak dialogové okno **relace** . Změny, které zde provedete, určí způsob, jakým se TableAdapterManager chová, když odešlou změny v souvisejících tabulkách zpátky do databáze.

## <a name="enablehierarchical-update-in-a-dataset"></a>Aktualizace Enablehierarchical v datové sadě
 Ve výchozím nastavení je hierarchická aktualizace povolena pro všechny nové datové sady, které jsou přidány nebo vytvořeny v projektu. Zapnutí nebo vypnutí hierarchické aktualizace nastavením vlastnosti **hierarchické aktualizace** typované datové sady v Návrháři DataSet na **hodnotu true** nebo **false**:

 ![Nastavení hierarchické aktualizace](../data-tools/media/hierarchical-update-setting.png "Nastavení hierarchické aktualizace")

## <a name="create-a-new-relation-between-tables"></a>Vytvoření nové relace mezi tabulkami
 Chcete-li vytvořit novou relaci mezi dvěma tabulkami, vyberte v Návrhář datových sad záhlaví každé tabulky, klikněte pravým tlačítkem myši a vyberte možnost**Přidat relaci**.

 ![Nabídka Přidat relaci hierarchické aktualizace](../data-tools/media/hierarchical-update-add-relation-menu.png "Nabídka Přidat relaci hierarchické aktualizace")

## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Vysvětlení omezení cizího klíče, kaskádových aktualizací a odstraňování
 Je důležité pochopit, jak se v generovaném kódu datové sady vytvoří omezení cizího klíče a kaskádové chování v databázi.

 Ve výchozím nastavení jsou tabulky dat v datové sadě vygenerovány se vztahy ( <xref:System.Data.DataRelation> ), které odpovídají vztahům v databázi. Vztah v datové sadě ale není generovaný jako omezení cizího klíče. <xref:System.Data.DataRelation>Je konfigurována jako **vztah pouze** bez použití <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> nebo <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> v platnost.

 Ve výchozím nastavení jsou kaskádové aktualizace a kaskádové odstranění vypnuté i v případě, že je v relaci databáze nastavená kaskádová aktualizace nebo kaskádová odstranění. Například vytvořením nového zákazníka a nové objednávky a následným pokusem o uložení dat může dojít ke konfliktu s omezeními cizího klíče, které jsou definovány v databázi. Další informace naleznete v tématu [How to: Configure omezení cizího klíče v datové sadě](https://msdn.microsoft.com/library/3954c388-e209-4a67-a34e-5ca106282f8e).

## <a name="set-the-order-to-perform-updates"></a>Nastavení pořadí provádění aktualizací
 Nastavení pořadí provádění aktualizací nastaví pořadí jednotlivých vložení, aktualizací a odstranění, které jsou nutné k uložení všech upravených dat ve všech tabulkách datové sady. Pokud je povolena Hierarchická aktualizace, jsou nejprve provedeny příkazy INSERT a pak aktualizace a pak jsou odstraněny. `TableAdapterManager`Poskytuje `UpdateOrder` vlastnost, kterou je možné nastavit tak, aby prováděla aktualizace, a pak vloží a pak odstraní.

> [!NOTE]
> Je důležité si uvědomit, že pořadí aktualizací je všechny zahrnuté. To znamená, že když se provádějí aktualizace, vloží a pak odstraní pro všechny tabulky v datové sadě.

 Chcete-li nastavit `UpdateOrder` vlastnost po přetahování položek z [okna zdroje dat](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) do formuláře, vyberte v části `TableAdapterManager` zásobník součásti a pak nastavte `UpdateOrder` vlastnost v okně **vlastnosti** . Další informace najdete v tématu [Postup: nastavení pořadí při provádění hierarchické aktualizace](https://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83).

## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>Vytvoření záložní kopie datové sady před provedením hierarchické aktualizace
 Při ukládání dat (voláním `TableAdapterManager.UpdateAll()` metody) se `TableAdapterManager` pokusí aktualizovat data pro každou tabulku v jedné transakci. Pokud některá z částí aktualizace jakékoli tabulky selžou, celá transakce se vrátí zpět. Ve většině případů vrácení zpět vrátí aplikaci do původního stavu.

 Někdy ale budete chtít datovou sadu obnovit ze záložní kopie. K tomu může dojít v případě, že používáte hodnoty automatického zvýšení. Například pokud operace uložení není úspěšná, hodnoty automatického zvýšení nejsou v datové sadě resetovány a datová sada bude nadále vytvářet hodnoty automatického zvýšení. To zaznamená mezeru v číslování, které nemusí být přijatelné ve vaší aplikaci. V situacích, kde se jedná o problém, `TableAdapterManager` poskytuje `BackupDataSetBeforeUpdate` vlastnost, která nahradí existující datovou kopii záložní kopií, pokud transakce není úspěšná.

> [!NOTE]
> Záložní kopie je při běhu metody pouze v paměti `TableAdapterManager.UpdateAll` . Proto neexistuje žádný programový přístup k této datové sadě zálohování, protože buď nahradí původní datovou sadu, nebo se překročí k oboru, jakmile bude `TableAdapterManager.UpdateAll` Metoda dokončí běhu.

## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>Upravte generovaný kód pro uložení, aby se provedla Hierarchická aktualizace.
 Uložte změny ze souvisejících tabulek dat v datové sadě do databáze tak, že zavoláte `TableAdapterManager.UpdateAll` metodu a předáte název datové sady, která obsahuje tabulky v relaci. Například spusťte `TableAdapterManager.UpdateAll(NorthwindDataset)` metodu pro odeslání aktualizací ze všech tabulek v NorthwindDataSet do back-endové databáze.

 Po vyřazení položek z okna **zdroje dat** je kód automaticky přidán do `Form_Load` události k naplnění každé tabulky ( `TableAdapter.Fill` metody). Kód je také přidán do události kliknutí na tlačítko pro **uložení** <xref:System.Windows.Forms.BindingNavigator> dat z datové sady zpět do databáze ( `TableAdapterManager.UpdateAll` Metoda).

 Generovaný kód pro uložení obsahuje také řádek kódu, který volá `CustomersBindingSource.EndEdit` metodu. Konkrétně volá <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodu prvního <xref:System.Windows.Forms.BindingSource> , která je přidána do formuláře. Jinými slovy, tento kód je generován pouze pro první tabulku, která je přetažena z okna **zdroje dat** do formuláře. <xref:System.Windows.Forms.BindingSource.EndEdit%2A>Volání potvrdí všechny změny, které jsou zpracovávány v rámci všech ovládacích prvků vázaných na data, které jsou právě upravovány. Proto pokud ovládací prvek vázaný na data stále obsahuje fokus a kliknete na tlačítko **Uložit** , všechny čekající úpravy v tomto ovládacím prvku budou potvrzeny před samotným uložením ( `TableAdapterManager.UpdateAll` Metoda).

> [!NOTE]
> Návrhář datových sad přidá pouze `BindingSource.EndEdit` kód první tabulky, která je na formuláři vynechána. Proto je nutné přidat řádek kódu pro volání `BindingSource.EndEdit` metody pro každou tabulku v relaci ve formuláři. Pro tento návod to znamená, že musíte přidat volání `OrdersBindingSource.EndEdit` metody.

#### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>Aktualizace kódu pro potvrzení změn v souvisejících tabulkách před uložením

1. Dvakrát klikněte na tlačítko **Uložit** na stránce <xref:System.Windows.Forms.BindingNavigator> pro otevření **Form1** v editoru kódu.

2. Přidejte řádek kódu pro volání `OrdersBindingSource.EndEdit` metody za řádek, který volá `CustomersBindingSource.EndEdit` metodu. Kód v události kliknutí na tlačítko pro **uložení** by měl vypadat přibližně takto:

    [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#1)]
    [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#1)]

   Kromě potvrzení změn v související podřízené tabulce před uložením dat do databáze může být také nutné potvrdit nově vytvořené nadřazené záznamy před přidáním nových podřízených záznamů do datové sady. Jinými slovy, možná budete muset před omezením cizího klíče přidat nový nadřazený záznam (Customer) do datové sady, aby bylo možné přidat nové podřízené záznamy (objednávky) do datové sady. K tomu můžete použít podřízenou `BindingSource.AddingNew` událost.

> [!NOTE]
> Bez ohledu na to, jestli je potřeba potvrdit nové nadřazené záznamy, závisí na typu ovládacího prvku, který se používá k vytvoření vazby k vašemu zdroji dat. V tomto návodu použijete jednotlivé ovládací prvky pro svázání s nadřazenou tabulkou. K tomu je potřeba další kód pro potvrzení nového nadřazeného záznamu. Pokud byly nadřazené záznamy zobrazeny v komplexním ovládacím prvku vazby jako <xref:System.Windows.Forms.DataGridView> , toto další <xref:System.Windows.Forms.BindingSource.EndEdit%2A> volání nadřazeného záznamu by nebylo nutné. Důvodem je, že základní funkce datové vazby ovládacího prvku zpracovává potvrzení nových záznamů.

#### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>Přidání kódu pro potvrzení nadřazených záznamů v datové sadě před přidáním nových podřízených záznamů

1. Vytvořte obslužnou rutinu události pro `OrdersBindingSource.AddingNew` událost.

    - Otevřete **Form1** v zobrazení Návrh, v části zásobník komponent vyberte **OrdersBindingSource** , v okně **vlastnosti** vyberte **události** a potom poklikejte na událost **obsloužíte** .

2. Přidejte řádek kódu do obslužné rutiny události, která volá `CustomersBindingSource.EndEdit` metodu. Kód v `OrdersBindingSource_AddingNew` obslužné rutině události by měl vypadat takto:

     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#2)]

## <a name="tableadaptermanager-reference"></a>Odkaz na TableAdapterManager
 Ve výchozím nastavení `TableAdapterManager` je třída generována při vytvoření datové sady, která obsahuje tabulky v relaci. Chcete-li zabránit vygenerování třídy, změňte hodnotu `Hierarchical Update` vlastnosti DataSet na false. Když přetáhnete tabulku, která má relaci, na návrhovou plochu stránky Windows Form nebo WPF, Visual Studio deklaruje členskou proměnnou třídy. Pokud datovou vazbu nepoužíváte, je nutné ručně deklarovat proměnnou.

 `TableAdapterManager`Třída není součástí [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Proto je nemůžete v dokumentaci vyhledat. Je vytvořena v době návrhu v rámci procesu vytváření datové sady.

 Následující jsou často používané metody a vlastnosti `TableAdapterManager` třídy:

|Člen|Popis|
|------------|-----------------|
|Metoda `UpdateAll`|Uloží všechna data ze všech tabulek dat.|
|`BackUpDataSetBeforeUpdate` majetek|Určuje, zda má být před provedením metody vytvořena záložní kopie datové sady `TableAdapterManager.UpdateAll` . Datového.|
|*TableName* `TableAdapter` majetek|Představuje `TableAdapter` . Vygenerovaná `TableAdapterManager` vlastnost obsahuje vlastnost pro každý `TableAdapter` IT správu. Například datová sada s tabulkou Customers and Orders je vygenerována s `TableAdapterManager` vlastnostmi, které obsahují `CustomersTableAdapter` a `OrdersTableAdapter` Vlastnosti.|
|`UpdateOrder` majetek|Určuje pořadí jednotlivých příkazů INSERT, Update a DELETE. Nastavte tuto hodnotu na jednu z hodnot ve `TableAdapterManager.UpdateOrderOption` výčtu.<br /><br /> Ve výchozím nastavení `UpdateOrder` je nastavená na **InsertUpdateDelete**. To znamená, že vložení, následné aktualizace a následné odstranění jsou prováděny pro všechny tabulky v datové sadě. Další informace najdete v tématu [Postup: nastavení pořadí při provádění hierarchické aktualizace](https://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83).|

## <a name="see-also"></a>Viz také
 [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)
