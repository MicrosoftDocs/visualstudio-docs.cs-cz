---
title: Třídy LINQ to SQL s děděním jednou tabulkou (Návrhář O-R)
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7ab33c2e77de183b5c916fbcfe60843c47c4f83f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648059"
---
# <a name="walkthrough-create-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Návod: vytvoření tříd LINQ to SQL pomocí dědičnosti s jednou tabulkou (O/R Designer)
[Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) podporují dědičnost jedné tabulky, protože je obvykle implementována v relačních systémech. Tento názorný postup se rozšíří na obecný postup, který je k dispozici v tématu [How to: Configure dědičnost pomocí návrháře o/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) a poskytuje některá skutečná data k předvedení použití dědičnosti v [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

Během tohoto Názorného postupu provedete následující úlohy:

- Vytvořte databázovou tabulku a přidejte do ní data.

- Vytvořte aplikaci model Windows Forms.

- Přidejte soubor [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] do projektu.

- Vytvořte nové třídy entit.

- Nakonfigurujte třídy entit pro použití dědičnosti.

- Dotaz na zděděnou třídu

- Zobrazí data ve formuláři Windows.

## <a name="create-a-table-to-inherit-from"></a>Vytvoření tabulky, ze které se zdědí
Chcete-li zjistit, jak dědičnost funguje, vytvořte malou `Person`ovou tabulku, použijte ji jako základní třídu a pak vytvořte objekt `Employee`, který z něj dědí.

### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Vytvoření základní tabulky k demonstraci dědičnosti

1. V **Průzkumník serveru** nebo **Průzkumníku databáze**klikněte pravým tlačítkem myši na uzel **tabulky** a pak klikněte na **Přidat novou tabulku**.

    > [!NOTE]
    > Můžete použít databázi Northwind nebo jakoukoli jinou databázi, do které můžete přidat tabulku.

2. V **Návrháři tabulky**přidejte do tabulky následující sloupce:

    |Název sloupce|Datový typ|Povoluje hodnoty null.|
    |-----------------|---------------|-----------------|
    |**ÚČET**|**int**|**Chybné**|
    |**Textový**|**int**|**Podmínka**|
    |**FirstName**|**nvarchar (200)**|**Chybné**|
    |**Polím**|**nvarchar (200)**|**Chybné**|
    |**Programu**|**int**|**Podmínka**|

3. Nastavte sloupec ID jako primární klíč.

4. Uložte tabulku a pojmenujte ji **Person**.

## <a name="add-data-to-the-table"></a>Přidat data do tabulky
Aby bylo možné ověřit, že je dědění správně nakonfigurováno, tabulka potřebuje nějaká data pro každou třídu v dědičnosti s jednou tabulkou.

### <a name="to-add-data-to-the-table"></a>Přidání dat do tabulky

1. Otevřete tabulku v zobrazení dat. (Klikněte pravým tlačítkem myši na tabulku **osob** v **Průzkumník serveru** nebo v **Průzkumníku databáze** a klikněte na **Zobrazit data tabulky**.)

2. Zkopírujte do tabulky následující data. (Můžete ho zkopírovat a pak ho vložit do tabulky výběrem celého řádku v podokně **výsledků** .)

    ||||||
    |-|-|-|-|-|
    |**ÚČET**|**Textový**|**FirstName**|**Polím**|**Programu**|
    |**první**|**první**|**Anne**|**Wallace**|**PLATNOST**|
    |**odst**|**první**|**Carlos**|**Grilo**|**PLATNOST**|
    |**1**|**první**|**Yael**|**Peled**|**PLATNOST**|
    |**4**|**odst**|**Gatis**|**Ozolins**|**první**|
    |**čl**|**odst**|**Andreas**|**Hauser**|**první**|
    |**6**|**odst**|**Tiffany**|**Phuvasate**|**první**|
    |**čl**|**odst**|**Alexey**|**Orekhov**|**odst**|
    |**8**|**odst**|**Michał**|**Poliszkiewicz**|**odst**|
    |**9**|**odst**|**Černý**|**Yee**|**odst**|
    |**10pruhový**|**odst**|**Fabricio**|**Noriega**|**1**|
    |**odst**|**odst**|**Mindy**|**Nováková**|**1**|
    |**12,5**|**odst**|**Ken**|**Kwok**|**1**|

## <a name="create-a-new-project"></a>Vytvoření nového projektu
Teď, když jste vytvořili tabulku, vytvořte nový projekt pro ukázku konfigurace dědičnosti.

### <a name="to-create-the-new-windows-forms-application"></a>Vytvoření nové aplikace model Windows Forms

1. V aplikaci Visual Studio v nabídce **soubor** vyberte **Nový**  > **projekt**.

2. V levém podokně rozbalte buď **vizuál C#**  , nebo **Visual Basic** a pak vyberte **Desktop Windows**.

3. V prostředním podokně vyberte typ projektu **aplikace model Windows Forms** .

4. Pojmenujte projekt **InheritanceWalkthrough**a klikněte na **tlačítko OK**.

     Vytvoří se projekt **InheritanceWalkthrough** a přidá se do **Průzkumník řešení**.

## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Přidání souboru tříd LINQ to SQL do projektu

### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>Přidání souboru LINQ to SQL do projektu

1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

2. Klikněte na šablonu **třídy LINQ to SQL** a pak klikněte na **Přidat**.

     Soubor *. dbml* se přidá do projektu a otevře se **Návrhář o/R** .

## <a name="create-the-inheritance-by-using-the-or-designer"></a>Vytvoření dědičnosti pomocí návrháře O/R
Nastavte dědičnost přetažením objektu **dědičnosti** z **panelu nástrojů** na návrhovou plochu.

### <a name="to-create-the-inheritance"></a>Vytvoření dědičnosti

1. V **Průzkumník serveru** nebo **Průzkumníku databáze**přejděte do tabulky **Person** , kterou jste vytvořili dříve.

2. Přetáhněte tabulku **Person** na návrhovou plochu **návrháře o/R** .

3. Přetáhněte druhou tabulku **Person** do **návrháře o/R** a změňte její název na **Zaměstnanec**.

4. Odstraňte vlastnost **správce** z objektu **Person** .

5. Z objektu **Employee** odstraňte vlastnosti **Type**, **ID**, **FirstName**a **LastName** . (Jinými slovy, odstraňte všechny vlastnosti s výjimkou **manažera**.)

6. Na kartě **Návrhář relací objektů** **panelu nástrojů**vytvořte **Dědičnost** mezi objekty **Person** a **Employee** . Provedete to tak, že kliknete na položku **Dědičnost** v **sadě nástrojů** a uvolníte tlačítko myši. Potom klikněte na objekt **zaměstnance** a pak na objekt **Person** v **Návrháři o/R**. Šipka na čáře dědičnosti pak odkazuje na objekt **Person** .

7. Klikněte na čáru **dědičnosti** na návrhové ploše.

8. Nastavte vlastnost **vlastnosti diskriminátoru** na **typ**.

9. Vlastnost **hodnoty diskriminátoru odvozené třídy** nastavte na **2**.

10. Nastavte vlastnost **hodnoty diskriminátoru základní třídy na hodnotu** **1**.

11. Nastavte vlastnost **Default dědičnosti** na **Person**.

12. Sestavte projekt.

## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Dotaz na zděděnou třídu a zobrazení dat ve formuláři
Nyní do formuláře přidáte nějaký kód, který se dotazuje na konkrétní třídu v objektovém modelu.

### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>Vytvoření dotazu LINQ a zobrazení výsledků ve formuláři

1. Přetáhněte **seznam** na **Form1**.

2. Dvojitým kliknutím na formulář vytvoříte obslužnou rutinu události `Form1_Load`.

3. Do obslužné rutiny události `Form1_Load` přidejte následující kód:

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
Spusťte aplikaci a ověřte, že záznamy zobrazené v seznamu jsou všichni zaměstnanci (záznamy, které mají ve sloupci **typ** hodnotu 2).

### <a name="to-test-the-application"></a>Testování aplikace

1. Stiskněte klávesu **F5**.

2. Ověřte, zda jsou zobrazeny pouze záznamy, které mají ve sloupci **typ** hodnotu 2.

3. Zavřete formulář. (V nabídce **ladění** klikněte na položku **Zastavit ladění**.)

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Návod: vytváření tříd LINQ to SQL (Návrhář O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Postupy: generování objektového modelu v Visual Basic neboC#](/dotnet/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp)
