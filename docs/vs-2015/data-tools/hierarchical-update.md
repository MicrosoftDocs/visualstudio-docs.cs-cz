---
title: Hierarchická aktualizace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d0176f203f7decb701d678a110856acdad36750b
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220172"
---
# <a name="hierarchical-update"></a>Hierarchická aktualizace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Hierarchická aktualizace * se vztahuje k procesu ukládání aktualizovaná data (z datové sady s dvěma nebo více souvisejícími tabulkami) do databáze při zachování pravidla referenční integrity. *Referenční integritu* odkazuje na pravidla konzistence poskytované omezení v databázi, která řídí chování vkládání, aktualizaci a odstraňování souvisejících záznamů. Například je referenční integritu, který vynutí vytvoření záznam zákazníka předtím, než pro zákazníka objednávky, který se má vytvořit.  Další informace o relacích v datových sadách najdete v tématu [vztahy v datových sadách](../data-tools/relationships-in-datasets.md)  
  
 Hierarchická aktualizace funkce používá `TableAdapterManager` ke správě `TableAdapter`ve typové datové sady. `TableAdapterManager` Komponenta [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]– vygeneruje třídy, takže není součástí [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Při přetažení tabulky z okna zdrojů dat na formuláři Windows nebo na stránce WPF, Visual Studio přidá proměnnou typu TableAdapterManager do formuláře nebo stránky a vidět ji v Návrháři v panelu komponent. Podrobné informace o `TableAdapterManager` třídy, najdete v části odkaz TableAdapterManager [TableAdapterManager – přehled](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).  
  
 Ve výchozím nastavení datová sada považuje za související tabulky "pouze, vztahy" to znamená, že nebude vynutit omezení cizího klíče. Toto nastavení v době návrhu lze upravit pomocí návrháře datových sad. Vyberte řádek vztah mezi dvěma tabulkami, abyste vyvolali **vztah** dialogové okno. Zde provedené změny se určí, jak TableAdapterManager chová při odeslání změn v souvisejících tabulkách zpět do databáze.  
  
## <a name="enablehierarchical-update-in-a-dataset"></a>Aktualizace Enablehierarchical v datové sadě  
 Hierarchická aktualizace je ve výchozím nastavení povolené pro všechny nové datové sady, které jsou přidány nebo v projektu. Hierarchická aktualizace zapnout nebo vypnout tak, že nastavíte **hierarchické aktualizace** vlastnost typové datové sady v [vytváření a úpravy typované datové sady](../data-tools/creating-and-editing-typed-datasets.md) k **True** nebo **False**:  
  
 ![Hierarchická aktualizace nastavení](../data-tools/media/hierarchical-update-setting.png "nastavení hierarchické aktualizace")  
  
## <a name="create-a-new-relation-between-tables"></a>Vytvořte novou relaci mezi tabulkami  
 Chcete-li vytvořit nový vztah mezi dvěma tabulkami v návrháři datových sad, klikněte do záhlaví každé tabulky, klikněte pravým tlačítkem a vyberte**přidat vztah**.  
  
 ![Hierarchická aktualizace přidat vztah nabídek](../data-tools/media/hierarchical-update-add-relation-menu.png "hierarchické aktualizace přidat vztah nabídek")  
  
## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Principy omezení cizího klíče, šablony aktualizace a odstranění  
 Je důležité pochopit, jak – omezení foreign key a CSS chování v databázi se vytvoří v kódu generované datová sada.  
  
 Ve výchozím nastavení, se generují tabulek dat v datové sady s relací (<xref:System.Data.DataRelation>), které odpovídají vztahy v databázi. Vztah v této datové sadě ale negeneruje jako omezení foreign key. <xref:System.Data.DataRelation> Je nakonfigurovaný jako **vztah pouze** bez <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> nebo <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> v platnosti.  
  
 Ve výchozím nastavení aktualizace šablony a kaskádové odstranění jsou vypnuté i v případě, že relace databáze je nastavena pomocí kaskádových aktualizace nebo odstranění v kaskádě zapnuté. Třeba vytvoření nového zákazníka a nové objednávky a pak se pokusíte použít k ukládání dat může způsobit konflikt s omezeními cizího klíče, které jsou definovány v databázi. Další informace najdete v tématu [postupy: Konfigurace omezení cizí klíče v datové sadě](http://msdn.microsoft.com/library/3954c388-e209-4a67-a34e-5ca106282f8e).  
  
## <a name="set-the-order-to-perform-updates"></a>Nastavení pořadí provádění aktualizací  
 Nastavení pořadí provádění aktualizací sady pořadí jednotlivých vloží, aktualizace a odstranění, které jsou potřeba pro uložení upravených dat ve všech tabulkách datové sady. Když hierarchické aktualizace zapnutý, vloží jsou provést jako první, pak aktualizuje a pak odstraní. `TableAdapterManager` Poskytuje `UpdateOrder` vlastnost, která může být nastavena na provádění nejprve aktualizací, pak vložení a odstranění.  
  
> [!NOTE]
>  Je důležité pochopit, že je vše zahrnuto pořadí aktualizace. To znamená když se aktualizace prováděly, vložení a odstranění jsou prováděny pro všechny tabulky v datové sadě.  
  
 Chcete-li nastavit `UpdateOrder` vlastnost Po přetažení položky z [okna zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) do formuláře, vyberte `TableAdapterManager` v podokně komponent a pak nastavte `UpdateOrder` vlastnost v **vlastnosti** okna. Další informace najdete v tématu [jak: nastavit pořadí při provádění hierarchické aktualizace](http://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83).  
  
## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>Vytvořit záložní kopii datové sady, než se pustíte do hierarchické aktualizace  
 Při ukládání dat (voláním `TableAdapterManager.UpdateAll()` metoda), `TableAdapterManager` pokusí k aktualizaci dat pro každou tabulku v rámci jedné transakce. Pokud žádnou část aktualizace pro jakoukoli tabulku selže, celá transakce vrácena zpět. Ve většině situací vrátí vrácení změn aplikace do původního stavu.  
  
 Ale v některých případech můžete chtít obnovit datové sady ze záložní kopie. Jedním z příkladů může dojít při použití hodnoty automatickým krokem. Pokud k uložení například operace se nezdaří, automatické zvyšování čísla hodnoty nejsou nastaveny v datové sadě a datové sady i nadále vytvářet automatické zvyšování hodnoty. Kvůli tomu mezera v číslování pro identifikátory, které nemusí být přijatelné ve vaší aplikaci. V situacích, kde je to problém `TableAdapterManager` poskytuje `BackupDataSetBeforeUpdate` vlastnost, která nahradí existující datovou sadu záložní kopii. Pokud se transakce nepovede.  
  
> [!NOTE]
>  Záložní kopie je pouze v paměti, zatímco `TableAdapterManager.UpdateAll` metoda běží. Proto neexistuje žádný programový přístup k této datové sadě záloh ho nahradí původní datové sady nebo dostane mimo rozsah poté, co `TableAdapterManager.UpdateAll` metoda ukončení.  
  
## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>Upravte vygenerovaný uložit kód k provedení hierarchické aktualizace  
 Uložit změny z tabulek souvisejících dat v datové sadě k databázi pomocí volání `TableAdapterManager.UpdateAll` metoda a předání názvu datové sady, který obsahuje související tabulky. Například spusťte `TableAdapterManager.UpdateAll(NorthwindDataset)` metody k odeslání aktualizací ze všech tabulek v datové sadě NorthwindDataset do back-end databáze.  
  
 Po přetažení položky z **zdroje dat** okně kód je automaticky přidán do `Form_Load` událostí k naplnění každá tabulka ( `TableAdapter.Fill` metody). Kód je taky přidaný ke **Uložit** události kliknutí na tlačítko <xref:System.Windows.Forms.BindingNavigator> k uložení dat v datové sadě zpět do databáze ( `TableAdapterManager.UpdateAll` metoda).  
  
 Uložit vygenerovaný kód také obsahuje jeden řádek kódu, který volá `CustomersBindingSource.EndEdit` metody. Přesněji řečeno, zavolá <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metoda první <xref:System.Windows.Forms.BindingSource>, který je přidán do formuláře. Jinými slovy, tento kód se generují jenom pro první tabulky, který je přetažen z **zdroje dat** okna do formuláře. <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Volání potvrzení změny, které jsou v procesu ve všech ovládacích prvcích vázaných na data, které jsou právě upravována. Proto, pokud ovládací prvek vázaný na data stále má fokus a klikněte na tlačítko **Uložit** tlačítko všechny čekající změny v tom, že ovládací prvek usilujeme o to před skutečné uložit ( `TableAdapterManager.UpdateAll` metoda).  
  
> [!NOTE]
>  Návrhář Dataset přidá jenom `BindingSource.EndEdit` kódu jako první tabulku přetaženého do formuláře. Proto je nutné přidat řádek kódu pro volání `BindingSource.EndEdit` metoda pro každou související tabulku na formuláři. V tomto návodu, to znamená, je nutné přidat volání `OrdersBindingSource.EndEdit` metody.  
  
#### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>Aktualizovat kód se zapsat změny do tabulky v relaci před uložením.  
  
1. Dvakrát klikněte **Uložit** tlačítko <xref:System.Windows.Forms.BindingNavigator> otevřete **Form1** v editoru kódu.  
  
2. Přidat řádek kódu pro volání `OrdersBindingSource.EndEdit` po řádek, který volá metodu `CustomersBindingSource.EndEdit` metody. Kód v **Uložit** klikněte na tlačítko události by měl vypadat takto:  
  
    [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#1)]
    [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#1)]  
  
   Kromě potvrzení změn v související podřízené tabulce, před uložením dat do databáze, může také mít nadřazené záznamy potvrzení nově vytvořené před přidáním nové podřízené záznamy do datové sady. Jinými slovy budete pravděpodobně nutné přidat nový záznam nadřazené (zákazníka) do datové sady než omezení cizího klíče povolit nové podřízené záznamy (objednávky) mají být přidány do datové sady. K tomu můžete použít podřízené `BindingSource.AddingNew` událostí.  
  
> [!NOTE]
>  Zda je nutné potvrdit nové nadřazené záznamy, závisí na typu ovládacího prvku, který slouží k vytvoření vazby ke zdroji dat. V tomto názorném postupu použijete k připojení k nadřazené tabulky jednotlivých ovládacích prvků. To vyžaduje další kód do nového nadřazeného záznamu o zápisu. Pokud nadřazené záznamy se místo toho zobrazí v ovládacím prvku komplexní vazby <xref:System.Windows.Forms.DataGridView>, tuto další <xref:System.Windows.Forms.BindingSource.EndEdit%2A> volání pro nadřazený záznam by být nutné. Je to proto, že základní funkce datové vazby pro ovládací prvek zpracovává potvrzení nových záznamů.  
  
#### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>Přidat kód pro potvrzení nadřazené záznamy v sadě dat před přidáním nové podřízené záznamy  
  
1.  Vytvořte obslužnou rutinu události pro `OrdersBindingSource.AddingNew` událostí.  
  
    -   Otevřít **Form1** v návrhovém zobrazení, vyberte **OrdersBindingSource** v panelu komponent vyberte **události** v **vlastnosti** okně a dvakrát klikněte **AddingNew** událostí.  
  
2.  Přidat řádek kódu, který volá obslužná rutina události `CustomersBindingSource.EndEdit` metody. Kód v `OrdersBindingSource_AddingNew` obslužné rutiny události by měl vypadat takto:  
  
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#2)]  
  
## <a name="tableadaptermanager-reference"></a>TableAdapterManager odkaz  
 Ve výchozím nastavení `TableAdapterManager` třídy se vygeneruje, když vytvoříte datovou sadu, která obsahuje související tabulky. Abyste zabránili generovaná třída, změňte hodnotu `Hierarchical Update` vlastnosti datové sady na hodnotu false. Při přetažení tabulky, která má vztah na návrhovou plochu formuláře Windows nebo WPF stránku sady Visual Studio deklaruje členské proměnné třídy. Pokud nepoužíváte vázání dat, budete muset ručně deklarovat proměnnou.  
  
 `TableAdapterManager` Třída není součástí [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Proto je nelze vyhledat v dokumentaci. Vytvoří se v době návrhu jako součást procesu vytváření datové sady.  
  
 Toto jsou často používané metody a vlastnosti `TableAdapterManager` třídy:  
  
|Člen|Popis|  
|------------|-----------------|  
|`UpdateAll` – Metoda|Uloží všechna data ze všech dat tabulky.|  
|`BackUpDataSetBeforeUpdate` Vlastnost|Určuje, jestli se má vytvořit záložní kopii datové sady, před spuštěním `TableAdapterManager.UpdateAll` metody. Datový typ Boolean.|  
|*tableName* `TableAdapter` vlastnost|Představuje `TableAdapter`. Vygenerovaný `TableAdapterManager` obsahuje vlastnost pro každý `TableAdapter` spravuje. Například datovou sadu s tabulkou Zákazníci a objednávky generuje s použitím `TableAdapterManager` obsahující `CustomersTableAdapter` a `OrdersTableAdapter` vlastnosti.|  
|`UpdateOrder` Vlastnost|Určuje pořadí jednotlivých insert, update a příkazů delete. Nastavte na jednu z hodnot v `TableAdapterManager.UpdateOrderOption` výčtu.<br /><br /> Ve výchozím nastavení `UpdateOrder` je nastavena na **InsertUpdateDelete**. To znamená, vloží, pak aktualizuje a odstraní se provádí pro všechny tabulky v datové sadě. Další informace najdete v tématu [jak: nastavit pořadí při provádění hierarchické aktualizace](http://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83).|  
  
## <a name="see-also"></a>Viz také  
 [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)

