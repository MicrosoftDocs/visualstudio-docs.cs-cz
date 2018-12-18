---
title: 'Návod: Přizpůsobení vložit, aktualizovat a odstraňovat chování tříd entit'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f665d860597bc99d7c9e496c115a82a60d596e09
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305530"
---
# <a name="walkthrough-customize-the-insert-update-and-delete-behavior-of-entity-classes"></a>Návod: Přizpůsobení insert, update a chování při odstraňování tříd entit

[Technologie LINQ to SQL nástroje v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) poskytuje vizuální návrhová plocha pro vytváření a úpravu LINQ na třídy SQL (tříd entit), které jsou založené na objektech v databázi. S použitím [technologie LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index), můžete použít technologii LINQ pro přístup k databázím SQL. Další informace najdete v tématu [LINQ (Language-Integrated query)](/dotnet/csharp/linq/).

Ve výchozím nastavení logiku pro provádění aktualizací poskytuje LINQ to SQL modulu runtime. Modul runtime vytvoří výchozí `Insert`, `Update`, a `Delete` příkazy na základě schématu tabulky (definice sloupců a informacemi o primárním klíči). Pokud nechcete použít výchozí chování, můžete nakonfigurovat chování aktualizací a určit konkrétní uložené procedury k provedení potřebné vložení, aktualizace a odstranění vyžadována pro práci s daty v databázi. Můžete také provést generování výchozího chování není, například při mapování tříd entit na zobrazení. Kromě toho můžete přepsat výchozí chování aktualizací databáze vyžaduje přístup k tabulce prostřednictvím uložené procedury. Další informace najdete v tématu [přizpůsobení operací pomocí uložených procedur](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures).

> [!NOTE]
> Tento návod vyžaduje dostupnost služby **InsertCustomer**, **UpdateCustomer**, a **DeleteCustomer** uložené procedury pro databázi Northwind.

Tento názorný postup obsahuje kroky, které musíte provést, chcete-li přepsat výchozí LINQ na SQL modul runtime chování pro ukládání dat zpět do databáze pomocí uložených procedur.

V tomto návodu se dozvíte, jak provádět následující úlohy:

-   Vytvoření nové aplikace Windows Forms a do souboru SQL do ní přidejte LINQ.

-   Vytvořte třídu entity, která je namapovaná na Northwind `Customers` tabulky.

-   Vytvořit zdroj dat objektu, který odkazuje na LINQ to SQL `Customer` třídy.

-   Vytvoření formuláře Windows, který obsahuje <xref:System.Windows.Forms.DataGridView> , který je vázán `Customer` třídy.

-   Implementace uložit funkce pro daný formulář.

-   Vytvoření <xref:System.Data.Linq.DataContext> metody tak, že přidáte uložené procedury k **O/R Designer**.

-   Konfigurace `Customer` třídy provádět pouze pomocí uložených procedur vloží, aktualizace a odstraní.

## <a name="prerequisites"></a>Požadavky

Tento návod používá SQL Server Express LocalDB a ukázkové databáze Northwind.

1.  Pokud nemáte SQL Server Express LocalDB, nainstalujte ji z [SQL Server Express stránku pro stažení](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program sady Visual Studio**. V **instalační program sady Visual Studio**, jako součást můžete nainstalovat SQL Server Express LocalDB **ukládání a zpracování dat** úlohy, nebo jako jednotlivých komponent.

2.  Instalace ukázkové databáze Northwind pomocí následujících kroků:

    1. V sadě Visual Studio, otevřete **Průzkumník objektů systému SQL Server** okna. (**Průzkumník objektů systému SQL Server** nainstaluje jako součást **ukládání a zpracování dat** zatížení **instalační program sady Visual Studio**.) Rozbalte **systému SQL Server** uzlu. Klikněte pravým tlačítkem na instanci LocalDB a vyberte **nový dotaz**.

       Otevře se okno editor dotazů.

    2. Kopírovat [Northwind příkazů jazyka Transact-SQL skriptů](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind úplně od začátku a naplní daty.

    3. Vložte skript T-SQL do editoru dotazů a klikněte na tlačítko **Execute** tlačítko.

       Po chvilce dotaz doběhnutí a vytvořit databázi Northwind.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Vytvoření aplikace a přidání LINQ na třídy SQL

Protože jsou práce s jazykem LINQ na třídy SQL a zobrazení dat ve formuláři Windows Forms, vytvořte novou aplikaci Windows Forms a přidat LINQ na třídy SQL soubor.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>Chcete-li vytvořit nový projekt aplikace Windows Forms, který obsahuje LINQ na třídy SQL

1. V sadě Visual Studio na **souboru** nabídce vyberte možnost **nový** > **projektu**.

2. Rozbalte buď **Visual C#** nebo **jazyka Visual Basic** v levém podokně vyberte **Windows Desktop**.

3. V prostředním podokně, vyberte **aplikace Windows Forms** typ projektu.

4. Pojmenujte projekt **UpdatingWithSProcsWalkthrough**a klikněte na tlačítko **OK**.

     **UpdatingWithSProcsWalkthrough** projekt je vytvořen a přidán do **Průzkumníka řešení**.

4.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.

5.  Klikněte na tlačítko **třídy LINQ to SQL** šablonu a zadejte **Northwind.dbml** v **název** pole.

6.  Klikněte na tlačítko **přidat**.

     Prázdný LINQ na třídy SQL soubor (**Northwind.dbml**) se přidá do projektu a **O/R Designer** otevře.

## <a name="create-the-customer-entity-class-and-object-data-source"></a>Vytvoření zákazníka entity třídy a objekt zdroje dat

Vytvoření LINQ na třídy SQL, které jsou mapovány na databázových tabulek přetažením tabulek z **Průzkumníka serveru** nebo **Průzkumník databáze** na **O/R Designer**. Výsledkem je LINQ na třídy SQL entity, které jsou mapovány na tabulky v databázi. Po vytvoření tříd entit, můžete použít jako zdroj dat objektu stejně jako ostatní třídy, které mají veřejné vlastnosti.

### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Vytvořte třídu entity zákazník a konfigurace zdroje dat s ním

1.  V **Průzkumníka serveru** nebo **Průzkumník databáze**, vyhledejte **zákazníka** tabulky v SQL serveru verzi ukázkové databáze Northwind.

2.  Přetáhněte **zákazníkům** uzlu z **Průzkumníka serveru** nebo **Průzkumník databáze** na **O/R Designer* povrchu.

     Třídu entity s názvem **zákazníka** se vytvoří. Obsahuje vlastnosti, které odpovídají sloupcům v tabulce Zákazníci. Název třídy entity **zákazníka** (není **zákazníkům**) protože představuje jednoho zákazníka z tabulky Zákazníci.

    > [!NOTE]
    > Toto chování přejmenovává se nazývá *pluralizace*. To je možné zapnout nebo vypnout [dialogové okno Možnosti](../ide/reference/options-dialog-box-visual-studio.md). Další informace najdete v tématu [postup: zapnutí a vypnutí (O/R Designer) pluralizace](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3.  Na **sestavení** nabídky, klikněte na tlačítko **sestavení UpdatingwithSProcsWalkthrough** k sestavení projektu.

4.  Chcete-li otevřít **zdroje dat** okno na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.

5.  V **zdroje dat** okna, klikněte na tlačítko **přidat nový zdroj dat**.

6.  Klikněte na tlačítko **objekt** na **zvolte typ zdroje dat** stránce a potom klikněte na tlačítko **Další**.

7.  Rozbalte **UpdatingwithSProcsWalkthrough** uzlu a vyhledejte a vyberte **zákazníka** třídy.

    > [!NOTE]
    > Pokud **zákazníka** třída není k dispozici, zavřete průvodce, sestavte projekt a spusťte průvodce znovu.
8.  Klikněte na tlačítko **Dokončit** vytvořit zdroj dat a přidat **zákazníka** třídu entity **zdroje dat** okna.

## <a name="create-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Vytvoření prvku DataGridView zobrazíte zákaznická data ve formuláři Windows

Vytvořit ovládací prvky vázané na tříd entit přetažením položky zdroje dat SQL z LINQ **zdroje dat** okna do formuláře Windows.

### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Chcete-li přidat ovládací prvky, které jsou vázány na tříd entit

1.  Otevřít **Form1** v návrhovém zobrazení.

2.  Z **zdroje dat** okno, přetáhněte **zákazníka** uzlu na **Form1**.

    > [!NOTE]
    > Pro zobrazení **zdroje dat** okna, klikněte na tlačítko **zobrazit zdroje dat** na **Data** nabídky.

3.  Otevřít **Form1** v editoru kódu.

4.  Přidejte následující kód do formuláře, globální do formuláře, mimo konkrétní metody, ale uvnitř `Form1` třídy:

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

## <a name="implement-save-functionality"></a>Implementace funkce uložení

Ve výchozím nastavení toto tlačítko není povoleno a uložit funkce není implementována. Kód se také automaticky přidán změněná data uložte do databáze při vytváření ovládacích prvků vázaných na data pro zdroje dat objektu. Tato část vysvětluje, jak povolit ukládání tlačítko a implementujte funkce uložení pro funkci LINQ na objekty SQL.

### <a name="to-implement-save-functionality"></a>K implementaci funkce uložení

1.  Otevřít **Form1** v návrhovém zobrazení.

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

## <a name="override-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Přepsat výchozí chování pro provádění aktualizací (vložení, aktualizace a odstranění)

### <a name="to-override-the-default-update-behavior"></a>Chcete-li přepsat výchozí chování aktualizace

1.  Otevřete souboru LINQ to SQL v **O/R Designer**. (Dvakrát klikněte **Northwind.dbml** ve **Průzkumníka řešení**.)

2.  V **Průzkumníka serveru** nebo **Průzkumník databáze**, rozbalte databáze Northwind **uložené procedury** uzlu a vyhledejte **InsertCustomers**, **UpdateCustomers**, a **DeleteCustomers** uložených procedur komponentami TableAdapter.

3.  Přetáhněte všechny tři uložené procedury do **O/R Designer**.

     Uložené procedury jsou přidány do podokna metody jako <xref:System.Data.Linq.DataContext> metody. Další informace najdete v tématu [metod DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4.  Vyberte **zákazníka** třída entity v **O/R Designer**.

5.  V **vlastnosti** okna, vyberte **vložit** vlastnost.

6.  Klikněte na tlačítko se třemi tečkami (**...** ) vedle položky **používat Runtime** otevřít **konfigurace chování** dialogové okno.

7.  Vyberte **přizpůsobit**.

8.  Vyberte **InsertCustomers** metodu **vlastní** seznamu.

9. Klikněte na tlačítko **použít** se uložit konfiguraci pro vybranou třídu nebo chování.

    > [!NOTE]
    > Můžete pokračovat v konfiguraci chování pro každou kombinaci třídy nebo chování, tak dlouho, dokud kliknete **použít** po každé změně. Pokud změníte třídy nebo chování před kliknutím na **použít**, dialogové okno upozornění poskytuje možnost použity všechny změny se zobrazí.

10. Vyberte **aktualizace** v **chování** seznamu.

11. Vyberte **přizpůsobit**.

12. Vyberte **UpdateCustomers** metodu **vlastní** seznamu.

     Prohlédněte si seznam **argumenty metody** a **vlastnosti třídy** a Všimněte si, že jsou dva **argumenty metody** a dva **vlastnosti třídy**pro některé sloupce v tabulce. To usnadňuje sledování změn a vytvořit příkazy, které kontrolují pro porušení souběžnosti.

13. Mapování **Original_CustomerID** argument metody pro výraz **CustomerID (původní)** vlastnost třídy.

    > [!NOTE]
    > Ve výchozím nastavení bude při názvy odpovídají argumenty metody mapovat na vlastnosti třídy. Pokud názvy vlastností byly změněny a už neodpovídá mezi tabulkou a třídu entity, budete muset vybrat vlastnost ekvivalentní třídy k mapování, když **O/R Designer** nelze určit správné mapování. Kromě toho Pokud argumenty metody nemají vlastnosti platnou třídu pro mapování na, můžete nastavit **vlastnosti třídy** hodnota, která se **(žádný)**.

14. Klikněte na tlačítko **použít** se uložit konfiguraci pro vybranou třídu nebo chování.

15. Vyberte **odstranit** v **chování** seznamu.

16. Vyberte **přizpůsobit**.

17. Vyberte **DeleteCustomers** metodu **vlastní** seznamu.

18. Mapování **Original_CustomerID** argument metody pro výraz **CustomerID (původní)** vlastnost třídy.

19. Klikněte na tlačítko **OK**.

> [!NOTE]
> Ačkoli to není problém pro tento konkrétní návod, je vhodné poznamenat, že technologie LINQ to SQL zpracovává databáze vygenerovala hodnoty automaticky pro identitu (automatické zvyšování čísla), rowguidcol (GUID databáze vygenerovala) a sloupce časového razítka během operace vložení a aktualizace. Databáze vygenerovala hodnoty v jiných typech sloupců neočekávaně způsobí hodnotu null. Na návratové hodnoty generovaných databází, měli byste ručně nastavit <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> k `true` a <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> na jednu z následujících akcí: [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync.OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>), nebo [AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="test-the-application"></a>Testování aplikace

Spusťte aplikaci znovu, aby ověřil, zda **UpdateCustomers** uložená procedura aktualizuje správně záznam zákazníka v databázi.

1.  Stisknutím klávesy **F5**.

2.  Úprava záznamu v tabulce k otestování chování aktualizací.

3.  Přidáte nový záznam pro testování vložit chování.

4.  Kliknutím na tlačítko Uložit uložte změny zpět do databáze.

5.  Zavřete formulář.

6.  Stisknutím klávesy **F5** a ověřte, že aktualizovaný záznam a nově vložený záznam jako trvalý.

7.  Odstranit nový záznam, kterou jste vytvořili v kroku 3 a otestování chování odstranění.

8.  Klikněte na toto tlačítko k odeslání změn a odebrat odstraněné záznam z databáze.

9. Zavřete formulář.

10. Stisknutím klávesy **F5** a ověřit, že odstraněný záznam byl odebrán z databáze.

    > [!NOTE]
    > Pokud vaše aplikace používá SQL Server Express Edition, v závislosti na hodnotu **kopírovat do výstupního adresáře** vlastnost souboru databáze, změny nemusí zobrazit při stisknutí **F5** v kroku 10.

## <a name="next-steps"></a>Další kroky

V závislosti na požadavcích aplikace existuje několik kroků, které můžete chtít provést po vytvoření LINQ na třídy SQL entity. Mezi vylepšení, která by mohla provést do této aplikace, patří:

- Implementace souběžnost kontroly během aktualizace. Informace najdete v tématu [optimistického řízení souběžnosti: Přehled](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview).

- Přidání dotazů LINQ jak filtrovat data. Informace najdete v tématu [Úvod do dotazů LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metody DataContext](../data-tools/datacontext-methods-o-r-designer.md)
- [Postupy: přiřazení uložených procedur za účelem aktualizace, vložení a odstranění](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Dotazy LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)