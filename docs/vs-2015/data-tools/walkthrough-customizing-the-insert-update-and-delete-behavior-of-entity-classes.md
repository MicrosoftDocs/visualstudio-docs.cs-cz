---
title: 'Návod: Přizpůsobení vložit, aktualizovat a odstraňovat chování tříd entit | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4d8ef69258d9c672bb5deb01b9c2e0972d4e8303
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193541"
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>Návod: Přizpůsobení vložit, aktualizovat a odstraňovat chování tříd entit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[LINQ to SQL nástroje v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) poskytuje vizuální návrhová plocha pro vytváření a úpravu [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] třídy (třídy entity), které jsou založené na objektech v databázi. S použitím [technologie LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655), můžete použít technologii LINQ pro přístup k databázím SQL. Další informace najdete v tématu [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).  
  
 Ve výchozím nastavení, je poskytována logiku pro provádění aktualizací [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] modulu runtime. Modul runtime vytvoří výchozí příkazy Insert, Update a Delete na základě schématu tabulky (definice sloupců a informacemi o primárním klíči). Pokud nechcete použít výchozí chování, můžete nakonfigurovat chování aktualizací a určit konkrétní uložené procedury k provedení potřebné vložení, aktualizace a odstranění vyžadována pro práci s daty v databázi. Můžete také provést generování výchozího chování není, například při mapování tříd entit na zobrazení. Kromě toho můžete přepsat výchozí chování aktualizací databáze vyžaduje přístup k tabulce prostřednictvím uložené procedury. Další informace najdete v tématu [přizpůsobení operací pomocí pomocí uložené procedury](http://msdn.microsoft.com/library/aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a).  
  
> [!NOTE]
>  Tento návod vyžaduje dostupnost služby **InsertCustomer**, **UpdateCustomer**, a **DeleteCustomer** uložené procedury pro databázi Northwind. Podrobnosti o tom, jak vytvořit těchto uložených procedurách najdete v tématu [návod: vytvoření uložené procedury aktualizace pro tabulku zákazníků Northwind](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md).  
  
 Tento názorný postup obsahuje kroky, které musíte provést, chcete-li přepsat výchozí LINQ na SQL modul runtime chování pro ukládání dat zpět do databáze pomocí uložených procedur.  
  
 V tomto návodu se dozvíte, jak provádět následující úlohy:  
  
-   Vytvoření nové aplikace Windows Forms a přidejte [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] souboru k němu.  
  
-   Vytvořte třídu entity, která se mapuje na tabulku zákazníků Northwind.  
  
-   Vytvořte zdroj dat objektu, který odkazuje na LINQ třídy SQL zákazníka.  
  
-   Vytvoření formuláře Windows, který obsahuje <xref:System.Windows.Forms.DataGridView> , který je vázán na třídu zákazníka.  
  
-   Implementace uložit funkce pro daný formulář.  
  
-   Vytvoření <xref:System.Data.Linq.DataContext> metody tak, že přidáte uložené procedury k [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
-   Konfigurovat třídu zákazníka ke vložení, aktualizace a odstranění použít uložené procedury.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující:  
  
-   Přístup k verzi systému SQL Server z ukázkové databáze Northwind. Další informace najdete v tématu [postupy: Instalace ukázkových databází](../data-tools/how-to-install-sample-databases.md).  
  
-   **InsertCustomer**, **UpdateCustomer**, a **DeleteCustomer** uložené procedury pro databázi Northwind. Další informace najdete v tématu [návod: vytvoření uložené procedury aktualizace pro tabulku zákazníků Northwind](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md).  
  
## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Vytvoření aplikace a přidání LINQ na třídy SQL  
 Vzhledem k tomu, že pracujete s [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] třídy a zobrazování dat ve formuláři Windows vytvořit novou aplikaci Windows Forms a přidejte LINQ na třídy SQL soubor.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-new-windows-application-project-that-contains-linq-to-sql-classes"></a>Chcete-li vytvořit nový projekt aplikace Windows, který obsahuje LINQ na třídy SQL  
  
1.  Z **souboru** nabídky, vytvořte nový projekt.  
  
2.  Pojmenujte projekt **UpdatingwithSProcsWalkthrough**.  
  
    > [!NOTE]
    >  [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Je podporována v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] a projekty jazyka C#. Proto vytvořte nový projekt v jednom z těchto jazyků.  
  
3.  Klikněte na tlačítko **formulářová aplikace Windows** šablonu a klikněte na tlačítko **OK**. Další informace najdete v tématu [klientské aplikace](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Je vytvořen a přidán do projektu UpdatingwithSProcsWalkthrough **Průzkumníka řešení**.  
  
4.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
5.  Klikněte na tlačítko **třídy LINQ to SQL** šablonu a zadejte **Northwind.dbml** v **název** pole.  
  
6.  Klikněte na tlačítko **přidat**.  
  
     Prázdný LINQ na třídy SQL soubor (Northwind.dbml) se přidá do projektu a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] otevře.  
  
## <a name="creating-the-customer-entity-class-and-object-data-source"></a>Vytvoření třídy Entity zákazník a zdroj dat objektu  
 Vytvoření [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] třídy, které jsou mapovány na databázových tabulek přetažením tabulek z **Průzkumníka serveru**/**Průzkumník databáze** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Výsledkem je LINQ na třídy SQL entity, které jsou mapovány na tabulky v databázi. Po vytvoření tříd entit, můžete použít jako zdroj dat objektu stejně jako ostatní třídy, které mají veřejné vlastnosti.  
  
#### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Vytvořte třídu entity zákazník a konfigurace zdroje dat s ním  
  
1.  V **Průzkumníka serveru**/**Průzkumník databáze**, vyhledejte v tabulce zákazníků v verze SQL serveru, ukázkové databáze Northwind. Další informace najdete v tématu [postupy: připojení k databázi Northwind](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
2.  Přetáhněte **zákazníkům** uzlu z **Průzkumníka serveru**/**Průzkumník databáze** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] povrchu.  
  
     Třídu entity s názvem **zákazníka** se vytvoří. Obsahuje vlastnosti, které odpovídají sloupcům v tabulce Zákazníci. Název třídy entity **zákazníka** (není **zákazníkům**) protože představuje jednoho zákazníka z tabulky Zákazníci.  
  
    > [!NOTE]
    >  Toto chování přejmenovává se nazývá *pluralizace*. To je možné zapnout nebo vypnout [dialogové okno Možnosti](../ide/reference/options-dialog-box-visual-studio.md). Další informace najdete v tématu [postup: zapnutí a vypnutí (O/R Designer) pluralizace](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).  
  
3.  Na **sestavení** nabídky, klikněte na tlačítko **sestavení UpdatingwithSProcsWalkthrough** k sestavení projektu.  
  
4.  Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.  
  
5.  V **zdroje dat** okna, klikněte na tlačítko **přidat nový zdroj dat**.  
  
6.  Klikněte na tlačítko **objekt** na **zvolte typ zdroje dat** stránce a potom klikněte na tlačítko **Další**.  
  
7.  Rozbalte **UpdatingwithSProcsWalkthrough** uzlu a vyhledejte a vyberte **zákazníka** třídy.  
  
    > [!NOTE]
    >  Pokud **zákazníka** třída není k dispozici, zavřete průvodce, sestavte projekt a spusťte průvodce znovu.  
  
8.  Klikněte na tlačítko **Dokončit** vytvořit zdroj dat a přidat **zákazníka** třídu entity **zdroje dat** okna.  
  
## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Vytvoření prvku DataGridView zobrazíte zákaznická Data ve formuláři Windows  
 Vytvoření ovládacích prvků, které jsou vázány na tříd entit přetažením [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] položky ze zdroje dat **zdroje dat** okna do formuláře Windows.  
  
#### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Chcete-li přidat ovládací prvky, které jsou vázány na tříd entit  
  
1.  V návrhovém zobrazení otevřete Form1.  
  
2.  Z **zdroje dat** okno, přetáhněte **zákazníka** uzlu do formuláře Form1.  
  
    > [!NOTE]
    >  Pro zobrazení **zdroje dat** okna, klikněte na tlačítko **zobrazit zdroje dat** na **Data** nabídky.  
  
3.  Otevřít v editoru kódu Form1.  
  
4.  Přidejte následující kód do formuláře, globální do formuláře, mimo jakoukoli konkrétní metodu, ale uvnitř třídy Form1:  
  
    ```vb  
    Private NorthwindDataContext1 As New NorthwindDataContext  
    ```  
  
    ```csharp  
    private NorthwindDataContext northwindDataContext1  
        = new NorthwindDataContext();  
  
    ```  
  
5.  Vytvořte obslužnou rutinu události pro `Form_Load` událostí a přidejte následující kód do obslužné rutiny:  
  
    ```vb  
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers  
    ```  
  
    ```csharp  
    customerBindingSource.DataSource  
        = northwindDataContext1.Customers;  
  
    ```  
  
## <a name="implementing-save-functionality"></a>Implementace funkce uložení  
 Ve výchozím nastavení toto tlačítko není povoleno a uložit funkce není implementována. Kód se také automaticky přidán změněná data uložte do databáze při vytváření ovládacích prvků vázaných na data pro zdroje dat objektu. Tato část vysvětluje, jak povolit ukládání tlačítko a implementujte funkce pro uložení [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] objekty.  
  
#### <a name="to-implement-save-functionality"></a>K implementaci funkce uložení  
  
1.  V návrhovém zobrazení otevřete Form1.  
  
2.  Vyberte Uložit tlačítko **CustomerBindingNavigator** (tlačítko s ikonou diskety).  
  
3.  V **vlastnosti** okno, nastaveno **povoleno** vlastnost **True**.  
  
4.  Dvojitým kliknutím na tlačítko Uložit vytvořte obslužnou rutinu události a přepněte se do editoru kódu.  
  
5.  Přidejte následující kód do ukládání obslužnou rutinu události:  
  
    ```vb  
    NorthwindDataContext1.SubmitChanges()  
    ```  
  
    ```csharp  
    northwindDataContext1.SubmitChanges();  
    ```  
  
## <a name="overriding-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Přepisování výchozího chování pro provádění aktualizací (vložení, aktualizace a odstranění)  
  
#### <a name="to-override-the-default-update-behavior"></a>Chcete-li přepsat výchozí chování aktualizace  
  
1.  Otevřete souboru LINQ to SQL v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Dvakrát klikněte **Northwind.dbml** ve **Průzkumníka řešení**.)  
  
2.  V **Průzkumníka serveru**/**Průzkumník databáze**, rozbalte databáze Northwind **uložené procedury** uzlu a vyhledejte  **InsertCustomers**, **UpdateCustomers**, a **DeleteCustomers** uložených procedur komponentami TableAdapter.  
  
3.  Přetáhněte všechny tři uložené procedury do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     Uložené procedury jsou přidány do podokna metody jako <xref:System.Data.Linq.DataContext> metody. Další informace najdete v tématu [metod DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Vyberte **zákazníka** třída entity v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
5.  V **vlastnosti** okna, vyberte **vložit** vlastnost.  
  
6.  Klikněte na tlačítko se třemi tečkami (...) vedle **používat Runtime** otevřít **konfigurace chování** dialogové okno.  
  
7.  Vyberte **přizpůsobit**.  
  
8.  Vyberte **InsertCustomers** metodu **vlastní** seznamu.  
  
9. Klikněte na tlačítko **použít** se uložit konfiguraci pro vybranou třídu nebo chování.  
  
    > [!NOTE]
    >  Můžete pokračovat v konfiguraci chování pro každou kombinaci třídy nebo chování, tak dlouho, dokud kliknete **použít** po každé změně. Pokud změníte třídy nebo chování před kliknutím na **použít**, dialogové okno upozornění poskytuje možnost použity všechny změny se zobrazí.  
  
10. Vyberte **aktualizace** v **chování** seznamu.  
  
11. Vyberte **přizpůsobit**.  
  
12. Vyberte **UpdateCustomers** metodu **vlastní** seznamu.  
  
     Prohlédněte si seznam **argumenty metody** a **vlastnosti třídy** a Všimněte si, že jsou dva **argumenty metody** a dva **vlastnosti třídy**pro některé sloupce v tabulce. To usnadňuje sledování změn a vytvořit příkazy, které kontrolují pro porušení souběžnosti.  
  
13. Mapování **Original_CustomerID** argument metody pro výraz **CustomerID (původní)** vlastnost třídy.  
  
    > [!NOTE]
    >  Ve výchozím nastavení bude při názvy odpovídají argumenty metody mapovat na vlastnosti třídy. Pokud názvy vlastností byly změněny a už neodpovídá mezi tabulkou a třídu entity, budete možná muset vybrat možnost vlastnost ekvivalentní třídu pro mapování na, pokud O/R Designer nemůže určit správné mapování. Kromě toho Pokud argumenty metody nemají vlastnosti platnou třídu pro mapování na, můžete nastavit **vlastnosti třídy** hodnota, která se **(žádný)**.  
  
14. Klikněte na tlačítko **použít** se uložit konfiguraci pro vybranou třídu nebo chování.  
  
15. Vyberte **odstranit** v **chování** seznamu.  
  
16. Vyberte **přizpůsobit**.  
  
17. Vyberte **DeleteCustomers** metodu **vlastní** seznamu.  
  
18. Mapování **Original_CustomerID** argument metody pro výraz **CustomerID (původní)** vlastnost třídy.  
  
19. Klikněte na tlačítko **OK**.  
  
> [!NOTE]
>  Ačkoli to není problém pro tento konkrétní názorný postup, je vhodné poznamenat, který [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] zpracovává databáze vygenerovala hodnoty automaticky pro identitu (automatické zvyšování čísla), rowguidcol (GUID databáze vygenerovala) a sloupce časového razítka při vložení a aktualizace. Databáze vygenerovala hodnoty v jiných typech sloupců neočekávaně způsobí hodnotu null. Na návratové hodnoty generovaných databází, měli byste ručně nastavit <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> k `true` a <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> na jednu z následujících akcí: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync>, nebo <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Spusťte aplikaci znovu, aby ověřil, zda **UpdateCustomers** uložená procedura aktualizuje správně záznam zákazníka v databázi.  
  
#### <a name="to-test-the-application"></a>Testování aplikace  
  
1.  Stiskněte klávesu F5.  
  
2.  Úprava záznamu v tabulce k otestování chování aktualizací.  
  
3.  Přidáte nový záznam pro testování vložit chování.  
  
4.  Kliknutím na tlačítko Uložit uložte změny zpět do databáze.  
  
5.  Zavřete formulář.  
  
6.  Stiskněte klávesu F5 a ověřte, že aktualizovaný záznam a nově vložený záznam jako trvalý.  
  
7.  Odstranit nový záznam, kterou jste vytvořili v kroku 3 a otestování chování odstranění.  
  
8.  Klikněte na toto tlačítko k odeslání změn a odebrat odstraněné záznam z databáze  
  
9. Zavřete formulář.  
  
10. Stiskněte klávesu F5 a ověřit, že odstraněný záznam byl odebrán z databáze.  
  
    > [!NOTE]
    >  Pokud vaše aplikace používá SQL Server Express Edition, v závislosti na hodnotu **kopírovat do výstupního adresáře** vlastnost souboru databáze, změny nemusí zobrazit při stisknutí klávesy F5 v kroku 10. Další informace najdete v tématu [jak: Manage Local Data Files in Your Project](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
## <a name="next-steps"></a>Další kroky  
 V závislosti na požadavcích aplikace existuje několik kroků, které můžete chtít provést po vytvoření [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] tříd entit. Mezi vylepšení, která by mohla provést do této aplikace, patří:  
  
-   Implementace souběžnost kontroly během aktualizace. Informace najdete v tématu [optimistického řízení souběžnosti: Přehled](http://msdn.microsoft.com/library/c2e38512-d0c8-4807-b30a-cb7e30338694).  
  
-   Přidání dotazů LINQ jak filtrovat data. Informace najdete v tématu [Úvod do dotazů LINQ (C#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).  
  
## <a name="see-also"></a>Viz také  
 [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Technologie LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Dotazy LINQ to SQL](http://msdn.microsoft.com/library/f4897aaa-7f44-4c20-a471-b948c2971aae)   
 [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Postupy: přiřazení uložených procedur za účelem aktualizace, vložení a odstranění (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Připravte si, co je nového pro vývoj aplikací Data v sadě Visual Studio 2012](http://msdn.microsoft.com/en-us/3d50d68f-5f44-4915-842f-6d42fce793f1)

