---
title: 'Návod: vytváření tříd LINQ to SQL pomocí dědičnosti s jednou tabulkou (O-R Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9cf95bd2095d9713d498ddccf68fd1e81e1b1e64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535704"
---
# <a name="walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Návod: Vytvoření tříd LINQ to SQL pomocí dědičnosti jedné tabulky (Návrhář relací objektů)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) podporují dědičnost jedné tabulky, protože je obvykle implementována v relačních systémech. Tento názorný postup se rozšíří na obecný postup, který je k dispozici v tématu [How to: Configure dědičnost pomocí návrháře o/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) a poskytuje některá skutečná data k předvedení použití dědičnosti v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 Během tohoto Názorného postupu budete provádět následující úlohy:

- Vytvořte databázovou tabulku a přidejte do ní data.

- Vytvořte aplikaci model Windows Forms.

- Přidejte [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] soubor do projektu.

- Vytvořte nové třídy entit.

- Nakonfigurujte třídy entit pro použití dědičnosti.

- Dotaz na zděděnou třídu

- Zobrazí data ve formuláři Windows.

## <a name="create-a-table-to-inherit-from"></a>Vytvoření tabulky, ze které se zdědí
 Chcete-li zjistit, jak dědičnost funguje, vytvoříte tabulku malého uživatele, použijete ji jako základní třídu a pak vytvoříte objekt Employee, který z něj dědí.

#### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Vytvoření základní tabulky k demonstraci dědičnosti

1. V **Průzkumník serveru** / **Průzkumníku databáze**klikněte pravým tlačítkem myši na uzel **tabulky** a pak klikněte na **Přidat novou tabulku**.

    > [!NOTE]
    > Můžete použít databázi Northwind nebo jakoukoli jinou databázi, do které můžete přidat tabulku.

2. V Návrháři tabulky přidejte do tabulky následující sloupce:

    |Název sloupce|Typ dat|Povoluje hodnoty null.|
    |-----------------|---------------|-----------------|
    |**ID**|**int**|**False**|
    |**Typ**|**int**|**True**|
    |**FirstName**|**nvarchar (200)**|**False**|
    |**LastName**|**nvarchar (200)**|**False**|
    |**Manager**|**int**|**True**|

3. Nastavte sloupec ID jako primární klíč.

4. Uložte tabulku a pojmenujte ji **Person**.

## <a name="add-data-to-the-table"></a>Přidat data do tabulky
 Aby bylo možné ověřit, že je dědění správně nakonfigurováno, tabulka potřebuje nějaká data pro každou třídu v dědičnosti s jednou tabulkou.

#### <a name="to-add-data-to-the-table"></a>Přidání dat do tabulky

1. Otevřete tabulku v zobrazení dat. (Klikněte pravým tlačítkem myši na tabulku **Person** v **Průzkumník serveru** / **Průzkumník databáze** a klikněte na **Zobrazit data tabulky**.)

2. Zkopírujte do tabulky následující data. (Můžete ho zkopírovat a pak ho vložit do tabulky výběrem celého řádku v podokně výsledků.)

    |**ID**|**Typ**|**FirstName**|**LastName**|**Manager**|
    |-|-|-|-|-|
    |**1**|**1**|**Anne**|**Wallace**|**PLATNOST**|
    |**2**|**1**|**Carlos**|**Grilo**|**PLATNOST**|
    |**3**|**1**|**Yael**|**Peled**|**PLATNOST**|
    |**4**|**2**|**Gatis**|**Ozolins**|**1**|
    |**5**|**2**|**Andreas**|**Hauser**|**1**|
    |**6**|**2**|**Tiffany**|**Phuvasate**|**1**|
    |**7**|**2**|**Alexey**|**Orekhov**|**2**|
    |**8**|**2**|**Michał**|**Poliszkiewicz**|**2**|
    |**9**|**2**|**Černý**|**Yee**|**2**|
    |**10**|**2**|**Fabricio**|**Noriega**|**3**|
    |**11**|**2**|**Mindy**|**Nováková**|**3**|
    |**12**|**2**|**Ken**|**Kwok**|**3**|

## <a name="create-a-new-project"></a>Vytvořit nový projekt
 Teď, když jste vytvořili tabulku, vytvořte nový projekt pro ukázku konfigurace dědičnosti.

#### <a name="to-create-the-new-windows-application"></a>Vytvoření nové aplikace systému Windows

1. V nabídce **soubor** vytvořte nový projekt.

2. Pojmenujte projekt **InheritanceWalkthrough**.

    > [!NOTE]
    > [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Je podporován v projektech Visual Basic a C#. Vytvořte nový projekt v jednom z těchto jazyků.

3. Klikněte na šablonu **aplikace model Windows Forms** a potom klikněte na tlačítko **OK**. Další informace najdete v tématu [klientské aplikace](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

4. Projekt InheritanceWalkthrough je vytvořen a přidán do **Průzkumník řešení**.

## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Přidání souboru tříd LINQ to SQL do projektu

#### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>Přidání souboru LINQ to SQL do projektu

1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

2. Klikněte na šablonu **třídy LINQ to SQL** a pak klikněte na **Přidat**.

     Soubor. dbml se přidá do projektu a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] otevře se.

## <a name="create-the-inheritance-by-using-the-or-designer"></a>Vytvoření dědičnosti pomocí návrháře O/R
 Nastavte dědičnost přetažením objektu **dědičnosti** z **panelu nástrojů** na návrhovou plochu.

#### <a name="to-create-the-inheritance"></a>Vytvoření dědičnosti

1. V **Server Explorer** / **Průzkumníku Průzkumník serveru Database**přejděte do tabulky **Person** , kterou jste vytvořili dříve.

2. Přetáhněte tabulku **Person** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] návrhovou plochu.

3. Přetáhněte druhou tabulku **Person** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] a změňte její název na **Zaměstnanec**.

4. Odstraňte vlastnost **správce** z objektu **Person** .

5. Z objektu **Employee** odstraňte vlastnosti **Type**, **ID**, **FirstName**a **LastName** . (Jinými slovy, odstraňte všechny vlastnosti s výjimkou **manažera**.)

6. Na kartě **Návrhář relací objektů** **panelu nástrojů**vytvořte **Dědičnost** mezi objekty **Person** a **Employee** . Provedete to tak, že kliknete na položku **Dědičnost** v **sadě nástrojů** a uvolníte tlačítko myši. Potom klikněte na objekt **zaměstnance** a pak na objekt **osoba** v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Šipka na čáře dědičnosti bude ukazovat na objekt **Person** .

7. Klikněte na čáru **dědičnosti** na návrhové ploše.

8. Nastavte vlastnost **vlastnosti diskriminátoru** na **typ**.

9. Vlastnost **hodnoty diskriminátoru odvozené třídy** nastavte na **2**.

10. Nastavte vlastnost **hodnoty diskriminátoru základní třídy na hodnotu** **1**.

11. Nastavte vlastnost **Default dědičnosti** na **Person**.

12. Sestavte projekt.

## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Dotaz na zděděnou třídu a zobrazení dat ve formuláři
 Nyní do formuláře přidáte nějaký kód, který se dotazuje na konkrétní třídu v objektovém modelu.

#### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>Vytvoření dotazu LINQ a zobrazení výsledků ve formuláři

1. Přetáhněte **seznam** na Form1.

2. Dvojitým kliknutím na formulář vytvoříte `Form1_Load` obslužnou rutinu události.

3. Do `Form1_Load` obslužné rutiny události přidejte následující kód:

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

## <a name="test-the-application"></a>Test aplikace
 Spusťte aplikaci a ověřte, že záznamy zobrazené v seznamu jsou všichni zaměstnanci (záznamy, které mají ve sloupci Typ hodnotu 2).

#### <a name="to-test-the-application"></a>Testování aplikace

1. Stiskněte klávesu F5.

2. Ověřte, zda jsou zobrazeny pouze záznamy, které mají ve sloupci Typ hodnotu 2.

3. Zavřete formulář. (V nabídce **ladění** klikněte na položku **Zastavit ladění**.)

## <a name="see-also"></a>Viz také
 [LINQ to SQL nástroje v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [: Přidání LINQ to SQL tříd do projektu (o-r Designer)](https://msdn.microsoft.com/library/7bb184ab-ec54-4cda-b706-604b2b4a3ed6) [Návod: vytváření tříd LINQ to SQL (o-r Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [Postupy: přiřazení uložených procedur k provádění aktualizací, vkládání a odstraňování (o/r Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [Postupy: generování objektového modelu v Visual Basic nebo C#](https://msdn.microsoft.com/library/a0c73b33-5650-420c-b9dc-f49310c201ee)
