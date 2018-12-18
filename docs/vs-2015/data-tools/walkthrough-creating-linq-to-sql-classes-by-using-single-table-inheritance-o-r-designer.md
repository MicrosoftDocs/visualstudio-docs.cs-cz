---
title: 'Návod: Vytvoření třídy LINQ to SQL s použitím dědičnosti jedné tabulky (O R Designer) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cd8572900e181da1b33b26638f15aa04845008e3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260725"
---
# <a name="walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Návod: Vytvoření třídy LINQ to SQL s použitím dědičnosti jedné tabulky (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[LINQ to SQL nástroje v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) podporuje dědičnosti jedné tabulky, jak se zpravidla implementuje v relačních systémech. Tento názorný postup rozšiřují obecných kroků uvedených v [postupy: Konfigurace dědičnosti pomocí Návrháře relací objektů](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) tématu a poskytuje některé reálná data pro demonstraci použití dědičnosti v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
 V tomto návodu budete provádět následující úlohy:  
  
-   Vytvořit tabulku databáze a přidejte do ní data.  
  
-   Vytvoření aplikace Windows Forms.  
  
-   Přidat [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] soubor do projektu.  
  
-   Vytvořte nové entity třídy.  
  
-   Nakonfigurujte tříd entit použít dědičnosti.  
  
-   Dotazování zděděné třídy.  
  
-   Zobrazte data ve formuláři Windows.  
  
## <a name="create-a-table-to-inherit-from"></a>Vytvořte tabulku pro dědí z  
 Pokud chcete zjistit, jak funguje dědičnosti, bude vytvoření malé tabulky osoby, použít jako základní třídu a vytvořte zaměstnance objekt, který z něj dědí.  
  
#### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Chcete-li vytvořit základní tabulky k předvedení dědičnosti  
  
1.  V **Průzkumníka serveru**/**Průzkumník databáze**, klikněte pravým tlačítkem myši **tabulky** uzel a klikněte na tlačítko **přidat novou tabulku**.  
  
    > [!NOTE]
    >  Můžete použít databázi Northwind nebo jakékoli jiné databáze, které můžete přidat tabulku.  
  
2.  V Návrháři tabulek přidejte následující sloupce do tabulky:  
  
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
  
#### <a name="to-add-data-to-the-table"></a>Chcete-li přidat data do tabulky  
  
1.  Otevřete v zobrazení dat v tabulce. (Klikněte pravým tlačítkem myši **osoba** tabulku v **Průzkumníka serveru**/**Průzkumník databáze** a klikněte na tlačítko **zobrazit Data tabulky**.)  
  
2.  Zkopírujte následující data do tabulky. (Můžete ho zkopírujte a vložte ho do tabulky tak, že vyberete celý řádek v podokně výsledků.)  
  
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
  
#### <a name="to-create-the-new-windows-application"></a>Chcete-li vytvořit novou aplikaci Windows  
  
1.  Z **souboru** nabídky, vytvořte nový projekt.  
  
2.  Pojmenujte projekt **InheritanceWalkthrough**.  
  
    > [!NOTE]
    >  [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Se podporuje v projektech Visual Basic a C#. Vytvoření nového projektu v jednom z těchto jazyků.  
  
3.  Klikněte na tlačítko **formulářová aplikace Windows** šablonu a pak klikněte na tlačítko **OK**. Další informace najdete v tématu [klientské aplikace](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
4.  Je vytvořen a přidán do projektu InheritanceWalkthrough **Průzkumníka řešení**.  
  
## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Přidat LINQ to SQL třídy soubor do projektu  
  
#### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>Chcete-li přidat LINQ na soubor SQL do projektu  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
2.  Klikněte na tlačítko **třídy LINQ to SQL** šablonu a pak klikněte na tlačítko **přidat**.  
  
     Do projektu se přidá soubor .dbml a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] otevře.  
  
## <a name="create-the-inheritance-by-using-the-or-designer"></a>Vytvoření dědičnosti pomocí Návrháře relací objektů  
 Konfigurace dědičnosti přetažením **dědičnosti** objektu z **nástrojů** na návrhovou plochu.  
  
#### <a name="to-create-the-inheritance"></a>Chcete-li vytvořit dědičnost  
  
1.  V **Průzkumníka serveru**/**Průzkumník databáze**, přejděte **osoba** tabulku, která jste vytvořili dříve.  
  
2.  Přetáhněte **osoba** tabulky do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] návrhovou plochu.  
  
3.  Přetáhněte druhý **osoba** tabulky do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] a změňte její název na **zaměstnance**.  
  
4.  Odstranit **správce** vlastnost z **osoba** objektu.  
  
5.  Odstranit **typ**, **ID**, **FirstName**, a **LastName** vlastnosti z **zaměstnance** objektu. (Jinými slovy, odstraní se všechny vlastnosti s výjimkou **správce**.)  
  
6.  Z **Návrhář relací objektů** karty **nástrojů**, vytvořit **dědičnosti** mezi **osoba** a  **Zaměstnanec** objekty. Chcete-li to provést, klikněte na tlačítko **dědičnosti** položky v **nástrojů** a uvolněte tlačítko myši. Klikněte **zaměstnance** objekt a potom **osoba** objektu v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Bude odkazovat na šipku v linii dědičnosti **osoba** objektu.  
  
7.  Klikněte na tlačítko **dědičnosti** řádku na návrhové ploše.  
  
8.  Nastavte **vlastnost diskriminátoru** vlastnost **typ**.  
  
9. Nastavte **hodnota diskriminátoru odvozené třídy** vlastnost **2**.  
  
10. Nastavte **hodnota diskriminátoru základní třídy** vlastnost **1**.  
  
11. Nastavte **výchozí dědičnost** vlastnost **osoba**.  
  
12. Sestavte projekt.  
  
## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Dotaz na zděděné třídu a zobrazení dat ve formuláři  
 Nyní přidáte nějaký kód do formuláře, který se dotazuje na určité třídy v objektovém modelu.  
  
#### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>Můžete vytvořit dotaz LINQ a zobrazit výsledky ve formuláři  
  
1.  Přetáhněte **ListBox** do formuláře Form1.  
  
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
 Spusťte aplikaci a ověřte, že záznamy zobrazené v seznamu jsou všichni zaměstnanci (záznamy, jejichž hodnota 2 ve sloupci jejich typ).  
  
#### <a name="to-test-the-application"></a>Testování aplikace  
  
1.  Stiskněte klávesu F5.  
  
2.  Ověřte, že se zobrazují pouze záznamy, jejichž hodnota 2 v jejich typ sloupce.  
  
3.  Zavřete formulář. (Na **ladění** nabídky, klikněte na tlačítko **Zastavit ladění**.)  
  
## <a name="see-also"></a>Viz také  
 [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Postupy: Přidání LINQ na třídy SQL do projektů (Návrhář O-R)](http://msdn.microsoft.com/library/7bb184ab-ec54-4cda-b706-604b2b4a3ed6)   
 [Návod: Vytvoření třídy LINQ to SQL (Návrhář O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Postupy: přiřazení uložených procedur za účelem aktualizace, vložení a odstranění (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Technologie LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Postupy: Generování objektového modelu v jazyce Visual Basic nebo C#](http://msdn.microsoft.com/library/a0c73b33-5650-420c-b9dc-f49310c201ee)

