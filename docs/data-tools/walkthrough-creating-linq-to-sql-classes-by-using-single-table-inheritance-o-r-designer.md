---
title: 'Návod: Vytvoření třídy LINQ to SQL s použitím dědičnosti jedné tabulky (Návrhář O-R)'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 943b75c9c5f9c0c32ab02b5e73c07282728e0beb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49864724"
---
# <a name="walkthrough-create-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Návod: Vytvoření tříd LINQ to SQL s použitím dědičnosti jedné tabulky (O/R Designer)
[Technologie LINQ to SQL nástroje v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) podporuje dědičnosti jedné tabulky, jak se zpravidla implementuje v relačních systémech. Tento názorný postup rozšiřují obecných kroků uvedených v [postupy: Konfigurace dědičnosti pomocí Návrháře relací objektů](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) tématu a poskytuje některé reálná data pro demonstraci použití dědičnosti v [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

 V tomto návodu budete provádět následující úlohy:

- Vytvořit tabulku databáze a přidejte do ní data.

- Vytvoření aplikace Windows Forms.

- Přidat [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] soubor do projektu.

- Vytvořte nové entity třídy.

- Nakonfigurujte tříd entit použít dědičnosti.

- Dotazování zděděné třídy.

- Zobrazte data ve formuláři Windows.

## <a name="create-a-table-to-inherit-from"></a>Vytvořte tabulku pro dědí z
 Pokud chcete zjistit, jak funguje dědičnosti, vytvoření malé `Person` tabulky, použijte ho jako základní třídu a pak vytvořte `Employee` objekt, který z něj dědí.

### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Chcete-li vytvořit základní tabulky k předvedení dědičnosti

1.  V **Průzkumníka serveru** nebo **Průzkumník databáze**, klikněte pravým tlačítkem myši **tabulky** uzel a klikněte na tlačítko **přidat novou tabulku**.

    > [!NOTE]
    >  Můžete použít databázi Northwind nebo jakékoli jiné databáze, které můžete přidat tabulku.

2.  V **návrháře tabulky**, přidejte následující sloupce v tabulce:

    |Název sloupce|Datový typ|Povolit hodnoty Null|
    |-----------------|---------------|-----------------|
    |**ID**|**int**|**False**|
    |**Typ**|**int**|**Hodnota TRUE**|
    |**Jméno**|**Nvarchar(200)**|**False**|
    |**LastName**|**Nvarchar(200)**|**False**|
    |**Správce**|**int**|**Hodnota TRUE**|

3.  Sloupec ID nastavte jako primární klíč.

4.  Uložte tabulku a pojmenujte ho **osoba**.

## <a name="add-data-to-the-table"></a>Přidání dat do tabulky
 Tak, aby můžete ověřit, jestli je správně nakonfigurovaný dědičnosti, musí v tabulce některá data pro každou třídu v jedné tabulky dědičnosti.

### <a name="to-add-data-to-the-table"></a>Chcete-li přidat data do tabulky

1.  Otevřete v zobrazení dat v tabulce. (Klikněte pravým tlačítkem myši **osoba** tabulku v **Průzkumníka serveru** nebo **Průzkumník databáze** a klikněte na tlačítko **zobrazit Data tabulky**.)

2.  Zkopírujte následující data do tabulky. (Můžete ho zkopírujte a vložte ho do tabulky tak, že vyberete celý řádek v **výsledky** podokně.)

    ||||||
    |-|-|-|-|-|
    |**ID**|**Typ**|**Jméno**|**LastName**|**Správce**|
    |**1**|**1**|**Anne**|**Wallace**|**HODNOTU NULL**|
    |**2**|**1**|**Carlos**|**Grilo**|**HODNOTU NULL**|
    |**3**|**1**|**Yael**|**Peled**|**HODNOTU NULL**|
    |**4**|**2**|**Gatis**|**Ozolins**|**1**|
    |**5**|**2**|**Andreas**|**Hauser**|**1**|
    |**6**|**2**|**Tiffany**|**Phuvasate**|**1**|
    |**7**|**2**|**Alexey**|**Orekhov**|**2**|
    |**8**|**2**|**Michał**|**Poliszkiewicz**|**2**|
    |**9**|**2**|**Tai**|**Jé**|**2**|
    |**10**|**2**|**Fabricio**|**Noriega**|**3**|
    |**11**|**2**|**Anna**|**Martin**|**3**|
    |**12**|**2**|**Ken**|**Kwok**|**3**|

## <a name="create-a-new-project"></a>Vytvoření nového projektu
 Teď, když jste vytvořili v tabulce, vytvořte nový projekt, na které si předvedeme konfiguraci dědičnosti.

### <a name="to-create-the-new-windows-forms-application"></a>Chcete-li vytvořit novou aplikaci Windows Forms

1. V sadě Visual Studio na **souboru** nabídce vyberte možnost **nový** > **projektu**.

2. Rozbalte buď **Visual C#** nebo **jazyka Visual Basic** v levém podokně vyberte **Windows Desktop**.

3. V prostředním podokně, vyberte **aplikace Windows Forms** typ projektu.

4. Pojmenujte projekt **InheritanceWalkthrough**a klikněte na tlačítko **OK**.

     **InheritanceWalkthrough** projekt je vytvořen a přidán do **Průzkumníka řešení**.

## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Do souboru třídy SQL do projektu přidejte LINQ

### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>Chcete-li přidat LINQ do SQL souboru do projektu

1.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.

2.  Klikněte na tlačítko **třídy LINQ to SQL** šablonu a pak klikněte na tlačítko **přidat**.

     *Dbml* přidá soubor do projektu a **O/R Designer** otevře.

## <a name="create-the-inheritance-by-using-the-or-designer"></a>Vytvoření dědičnosti pomocí Návrháře relací objektů
 Konfigurace dědičnosti přetažením **dědičnosti** objektu z **nástrojů** na návrhovou plochu.

### <a name="to-create-the-inheritance"></a>Chcete-li vytvořit dědičnost

1.  V **Průzkumníka serveru** nebo **Průzkumník databáze**, přejděte **osoba** tabulku, která jste vytvořili dříve.

2.  Přetáhněte **osoba** tabulky do **O/R Designer** návrhovou plochu.

3.  Přetáhněte druhý **osoba** tabulky do **O/R Designer** a změňte její název na **zaměstnance**.

4.  Odstranit **správce** vlastnost z **osoba** objektu.

5.  Odstranit **typ**, **ID**, **FirstName**, a **LastName** vlastnosti z **zaměstnance** objektu. (Jinými slovy, odstraní se všechny vlastnosti s výjimkou **správce**.)

6.  Z **Návrhář relací objektů** karty **nástrojů**, vytvořit **dědičnosti** mezi **osoba** a  **Zaměstnanec** objekty. Chcete-li to provést, klikněte na tlačítko **dědičnosti** položky v **nástrojů** a uvolněte tlačítko myši. Klikněte **zaměstnance** objekt a potom **osoba** objektu v **O/R Designer**. Pak odkazuje na šipku v linii dědičnosti **osoba** objektu.

7.  Klikněte na tlačítko **dědičnosti** řádku na návrhové ploše.

8.  Nastavte **vlastnost diskriminátoru** vlastnost **typ**.

9. Nastavte **hodnota diskriminátoru odvozené třídy** vlastnost **2**.

10. Nastavte **hodnota diskriminátoru základní třídy** vlastnost **1**.

11. Nastavte **výchozí dědičnost** vlastnost **osoba**.

12. Sestavte projekt.

## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Dotaz na zděděné třídu a zobrazení dat ve formuláři
 Nyní přidáte nějaký kód do formuláře, který se dotazuje na určité třídy v objektovém modelu.

### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>Můžete vytvořit dotaz LINQ a zobrazit výsledky ve formuláři

1.  Přetáhněte **ListBox** do **Form1**.

2.  Klikněte dvakrát na formulář pro vytvoření `Form1_Load` obslužné rutiny události.

3.  Přidejte následující kód, který `Form1_Load` obslužné rutiny události:

    ```vb
    Dim dc As New DataClasses1DataContext
    Dim results = From emp In dc.Persons _
        Where TypeOf emp Is Employee _
        Select emp

    For Each Emp As Employee In results
        ListBox1.Items.Add(Emp.LastName)
    Next
    ```

    ```csharp
    NorthwindDataContext dc = new DataClasses1DataContext();
    var results = from emp in dc.Persons
                  where emp is Employee
                  select emp;

    foreach(Employee Emp in results)
    {
        listBox1.Items.Add(Emp.LastName)
    }
    ```

## <a name="test-the-application"></a>Testování aplikace
 Spusťte aplikaci a ověřte, že záznamy zobrazené v seznamu jsou všichni zaměstnanci (záznamy, jejichž hodnota 2 v jejich **typ** sloupec).

### <a name="to-test-the-application"></a>Testování aplikace

1.  Stisknutím klávesy **F5**.

2.  Ověření, který pouze záznamy, které mají hodnotu 2 v jejich **typ** sloupce se zobrazí.

3.  Zavřete formulář. (Na **ladění** nabídky, klikněte na tlačítko **Zastavit ladění**.)

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Návod: Vytvoření LINQ na třídy SQL (Návrhář O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Postupy: generování objektového modelu v jazyce Visual Basic nebo C#](/dotnet/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp)