---
title: Přizpůsobení chování funkce Vložit/aktualizovat/odstranit
description: V tomto návodu Přizpůsobte chování vložení, aktualizace a odstranění tříd entit pomocí LINQ (jazyka integrovaného dotazu) do nástrojů SQL v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 1aba3b1f00ce65b90f61077673a0b88a3bab0f5e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866135"
---
# <a name="walkthrough-customize-the-insert-update-and-delete-behavior-of-entity-classes"></a>Návod: přizpůsobení chování při vložení, aktualizaci a odstranění tříd entit

[Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) poskytují vizuální návrhovou plochu pro vytváření a úpravu LINQ to SQL tříd (třídy entit), které jsou založené na objektech v databázi. Pomocí [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)můžete pro přístup k databázím SQL použít technologii LINQ. Další informace naleznete v tématu [LINQ (jazykově integrovaný dotaz)](/dotnet/csharp/linq/).

Ve výchozím nastavení je logika pro provádění aktualizací poskytována modulem runtime LINQ to SQL. Modul runtime vytvoří výchozí `Insert` `Update` příkazy, a `Delete` v závislosti na schématu tabulky (definice sloupců a informace o primárním klíči). Pokud nechcete použít výchozí chování, můžete nakonfigurovat chování aktualizace a určit konkrétní uložené procedury pro provádění nezbytných vložení, aktualizací a odstranění, které je nutné pro práci s daty v databázi. To lze provést také v případě, že se výchozí chování negeneruje, například když vaše třídy entit budou mapovány na zobrazení. Kromě toho můžete přepsat výchozí chování aktualizace, když databáze vyžaduje přístup k tabulce prostřednictvím uložených procedur. Další informace najdete v tématu [přizpůsobení operací pomocí uložených procedur](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures).

> [!NOTE]
> Tento návod vyžaduje dostupnost uložených procedur **InsertCustomer**, **UpdateCustomer** a **DeleteCustomer** pro databázi Northwind.

Tento názorný postup popisuje kroky, které je nutné provést, chcete-li přepsat výchozí LINQ to SQL běhové chování pro ukládání dat zpět do databáze pomocí uložených procedur.

V tomto návodu se dozvíte, jak provádět následující úlohy:

- Vytvořte novou aplikaci model Windows Forms a přidejte do ní soubor LINQ to SQL.

- Vytvořte třídu entity, která je namapována na `Customers` tabulku Northwind.

- Vytvořte zdroj dat objektu, který odkazuje na `Customer` třídu LINQ to SQL.

- Vytvořte formulář Windows, který obsahuje objekt <xref:System.Windows.Forms.DataGridView> vázaný na `Customer` třídu.

- Implementujte funkci Save pro formulář.

- Vytvořte <xref:System.Data.Linq.DataContext> metody přidáním uložených procedur do **návrháře o/R**.

- Nakonfigurujte `Customer` třídu pro použití uložených procedur k provádění vložení, aktualizací a odstranění.

## <a name="prerequisites"></a>Požadavky

Tento návod používá SQL Server Express LocalDB a ukázkovou databázi Northwind.

1. Pokud nemáte SQL Server Express LocalDB, nainstalujte ji buď ze [stránky pro stažení SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program pro Visual Studio**. V **instalační program pro Visual Studio** můžete nainstalovat SQL Server Express LocalDB jako součást úlohy **ukládání a zpracování dat** nebo jako jednotlivé komponenty.

2. Nainstalujte ukázkovou databázi Northwind pomocí následujících kroků:

    1. V aplikaci Visual Studio otevřete okno **Průzkumník objektů systému SQL Server** . (**Průzkumník objektů systému SQL Server** se instalují jako součást úlohy **ukládání a zpracování dat** v **instalační program pro Visual Studio**.) Rozbalte uzel **SQL Server** . Klikněte pravým tlačítkem na instanci LocalDB a vyberte **Nový dotaz**.

       Otevře se okno editoru dotazů.

    2. Zkopírujte [skript Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind od začátku a naplní ji daty.

    3. Vložte skript T-SQL do editoru dotazů a pak klikněte na tlačítko **Spustit** .

       Po krátké době se dotaz dokončí a vytvoří se databáze Northwind.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Vytvoření aplikace a přidání tříd LINQ to SQL

Vzhledem k tomu, že pracujete se LINQ to SQLmi třídami a zobrazujete data ve formuláři Windows, vytvořte novou aplikaci model Windows Forms a přidejte LINQ to SQL souboru tříd.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>Vytvoření nového projektu aplikace model Windows Forms, který obsahuje LINQ to SQL třídy

1. V aplikaci Visual Studio v nabídce **soubor** vyberte **Nový**  >  **projekt**.

2. V levém podokně rozbalte možnost **Visual C#** nebo **Visual Basic** a pak vyberte možnost **desktopová plocha systému Windows**.

3. V prostředním podokně vyberte typ projektu **aplikace model Windows Forms** .

4. Pojmenujte projekt **UpdatingWithSProcsWalkthrough** a klikněte na **tlačítko OK**.

     Vytvoří se projekt **UpdatingWithSProcsWalkthrough** a přidá se do **Průzkumník řešení**.

4. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

5. Klikněte na šablonu **třídy LINQ to SQL** a do pole **název** zadejte **Northwind. dbml** .

6. Klikněte na **Přidat**.

     Do projektu se přidá prázdný soubor tříd LINQ to SQL (**Northwind. dbml**) a otevře se **Návrhář o/R** .

## <a name="create-the-customer-entity-class-and-object-data-source"></a>Vytvoření třídy entity zákazníka a zdroje dat objektu

Vytvořte LINQ to SQL třídy, které jsou namapovány na tabulky databáze, přetažením tabulek z **Průzkumník serveru** nebo **Průzkumníka databáze** do **návrháře o/R**. Výsledkem je LINQ to SQL třídy entit, které jsou mapovány na tabulky v databázi. Po vytvoření tříd entit je lze použít jako zdroje dat objektů stejně jako jiné třídy, které mají veřejné vlastnosti.

### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Vytvoření třídy entity zákazníka a konfigurace zdroje dat

1. V **Průzkumník serveru** nebo **Průzkumníku databáze** vyhledejte tabulku **Customer** v SQL Server verzi ukázkové databáze Northwind.

2. Přetáhněte uzel **Customers** z **Průzkumník serveru** nebo **Průzkumníka databáze** na plochu *Návrháře * O/R* .

     Vytvoří se Třída entity s názvem **Zákazník** . Obsahuje vlastnosti, které odpovídají sloupcům v tabulce Customers. Třída entity se nazývá **Customer** (ne **zákazníci**), protože představuje jednoho zákazníka z tabulky Customers.

    > [!NOTE]
    > Chování při přejmenování se nazývá *plural*. Dá se zapnout nebo vypnout v [dialogovém okně Možnosti](../ide/reference/options-dialog-box-visual-studio.md). Další informace najdete v tématu [Postup: zapnutí a vypnutí funkce plural (o/R Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3. V nabídce **sestavení** klikněte na **sestavit UpdatingwithSProcsWalkthrough** a sestavte projekt.

4. Chcete-li otevřít okno **zdroje dat** , klikněte v nabídce **data** na možnost **Zobrazit zdroje dat**.

5. V okně **zdroje dat** klikněte na tlačítko **Přidat nový zdroj dat**.

6. Klikněte na **objekt** na stránce **Zvolte typ zdroje dat** a potom klikněte na tlačítko **Další**.

7. Rozbalte uzel **UpdatingwithSProcsWalkthrough** a vyhledejte a vyberte třídu **Customer** .

    > [!NOTE]
    > Pokud třída **zákazníka** není k dispozici, ukončete průvodce, sestavte projekt a spusťte průvodce znovu.
8. Kliknutím na tlačítko **Dokončit** vytvořte zdroj dat a přidejte třídu entity **zákazníka** do okna **zdroje dat** .

## <a name="create-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Vytvoření ovládacího prvku DataGridView pro zobrazení zákaznických dat ve formuláři Windows

Vytvořte ovládací prvky, které jsou vázány na třídy entit přetažením LINQ to SQL položky zdroje dat z okna **zdroje dat** do formuláře Windows Form.

### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Chcete-li přidat ovládací prvky, které jsou vázány na třídy entit

1. Otevřete **Form1** v zobrazení Návrh.

2. V okně **zdroje dat** Přetáhněte uzel **Zákazník** na **Form1**.

    > [!NOTE]
    > Chcete-li zobrazit okno **zdroje dat** , klikněte na možnost **Zobrazit zdroje dat** v nabídce **data** .

3. Otevřete **Form1** v editoru kódu.

4. Přidejte následující kód do formuláře, globální do formuláře, mimo jakoukoliv konkrétní metodu, ale uvnitř `Form1` třídy:

    ```vb
    Private NorthwindDataContext1 As New NorthwindDataContext
    ```

    ```csharp
    private NorthwindDataContext northwindDataContext1
        = new NorthwindDataContext();
    ```

5. Vytvořte obslužnou rutinu události pro `Form_Load` událost a přidejte následující kód do obslužné rutiny:

    ```vb
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers
    ```

    ```csharp
    customerBindingSource.DataSource
        = northwindDataContext1.Customers;
    ```

## <a name="implement-save-functionality"></a>Implementace funkce Save

Ve výchozím nastavení není tlačítko Uložit povoleno a funkce Uložit nejsou implementovány. Také není automaticky přidán kód pro uložení změněných dat do databáze, když jsou vytvořeny ovládací prvky vázané na data pro zdroje dat objektu. V této části se dozvíte, jak povolit tlačítko Uložit a implementovat ukládání funkcí pro LINQ to SQL objekty.

### <a name="to-implement-save-functionality"></a>Implementace funkce Uložit

1. Otevřete **Form1** v zobrazení Návrh.

2. Vyberte tlačítko Uložit na **CustomerBindingNavigator** (tlačítko s ikonou na disketě).

3. V okně **vlastnosti** nastavte vlastnost **Enabled** na **hodnotu true**.

4. Dvakrát klikněte na tlačítko Uložit a vytvořte obslužnou rutinu události a přepněte do editoru kódu.

5. Do obslužné rutiny události tlačítko Save přidejte následující kód:

    ```vb
    NorthwindDataContext1.SubmitChanges()
    ```

    ```csharp
    northwindDataContext1.SubmitChanges();
    ```

## <a name="override-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Přepsat výchozí chování pro provádění aktualizací (vložení, aktualizace a odstranění)

### <a name="to-override-the-default-update-behavior"></a>Přepsání výchozího chování aktualizace

1. Otevřete soubor LINQ to SQL v **Návrháři o/R**. (V **Průzkumník řešení** dvakrát klikněte na soubor **Northwind. dbml** .)

2. V **Průzkumník serveru** nebo **Průzkumníku databáze** rozbalte uzel **uložené procedury** databáze Northwind a vyhledejte uložené procedury **InsertCustomers**, **UpdateCustomers** a **DeleteCustomers** .

3. Přetáhněte všechny tři uložené procedury do **návrháře o/R**.

     Uložené procedury jsou přidány do podokna metody jako <xref:System.Data.Linq.DataContext> metody. Další informace naleznete v tématu [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. V **Návrháři o/R** vyberte třídu entity **zákazníka** .

5. V okně **vlastnosti** vyberte vlastnost **Vložit** .

6. Kliknutím na tlačítko se třemi tečkami (**...**) vedle pole **použít modul runtime** otevřete dialogové okno **Konfigurovat chování** .

7. Vyberte **Přizpůsobit**.

8. V seznamu **přizpůsobit** vyberte metodu **InsertCustomers** .

9. Kliknutím na **použít** uložte konfiguraci pro vybranou třídu a chování.

    > [!NOTE]
    > Můžete pokračovat v konfiguraci chování pro každou kombinaci třídy/chování, pokud kliknete na **použít** po provedení každé změny. Pokud změníte třídu nebo chování předtím, než kliknete na **použít**, zobrazí se dialogové okno s upozorněním, které vám poskytne možnost použít všechny změny.

10. V seznamu **chování** vyberte **aktualizovat** .

11. Vyberte **Přizpůsobit**.

12. V seznamu **přizpůsobit** vyberte metodu **UpdateCustomers** .

     Zkontrolujte seznam **argumentů metody** a **vlastností třídy** a Všimněte si, že existují dva **argumenty metody** a dvě **vlastnosti třídy** pro některé sloupce v tabulce. Díky tomu je snazší sledovat změny a vytvářet příkazy, které kontrolují porušení souběžnosti.

13. Namapujte argument **Original_CustomerID** metody na vlastnost **CustomerID (původní)** Class.

    > [!NOTE]
    > Ve výchozím nastavení budou argumenty metody namapovány na vlastnosti třídy, pokud se názvy shodují. Pokud se změní názvy vlastností a již se neshodují mezi tabulkou a třídou entity, může být nutné vybrat vlastnost ekvivalentní třídy, která má být mapována, pokud **Návrhář relací v/R** nemůže určit správné mapování. Kromě toho, pokud argumenty metody nemají platné vlastnosti třídy pro mapování, můžete nastavit **vlastnost třídy** na hodnotu **(žádný)**.

14. Kliknutím na **použít** uložte konfiguraci pro vybranou třídu a chování.

15. V seznamu **chování** vyberte **Odstranit** .

16. Vyberte **Přizpůsobit**.

17. V seznamu **přizpůsobit** vyberte metodu **DeleteCustomers** .

18. Namapujte argument **Original_CustomerID** metody na vlastnost **CustomerID (původní)** Class.

19. Klikněte na **OK**.

> [!NOTE]
> I když se u tohoto konkrétního návodu nejedná o problém, znamená to, že LINQ to SQL zpracovává hodnoty generované databázemi automaticky pro identitu (automatické zvýšení), ROWGUIDCOL (GUID generovaný identifikátor GUID) a sloupce časového razítka během vkládání a aktualizace. Hodnoty generované databází v jiných typech sloupců neočekávaně způsobí hodnotu null. Chcete-li vrátit hodnoty generované databází, je třeba ručně nastavit <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> na `true` <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> jednu z následujících možností: [AutoSync. Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync. při vložení](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)nebo [AutoSync. inupdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="test-the-application"></a>Testování aplikace

Spusťte aplikaci znovu, abyste ověřili, že uložená procedura **UpdateCustomers** správně aktualizuje záznam zákazníka v databázi.

1. Stiskněte klávesu **F5**.

2. Úpravou záznamu v mřížce otestujete chování aktualizace.

3. Přidejte nový záznam pro otestování chování při vkládání.

4. Kliknutím na tlačítko Uložit uložte změny zpět do databáze.

5. Zavřete formulář.

6. Stiskněte klávesu **F5** a ověřte, že aktualizovaný záznam a nově vložený záznam jsou trvalé.

7. Odstraňte nový záznam, který jste vytvořili v kroku 3, abyste otestovali chování při odstraňování.

8. Klikněte na tlačítko Uložit a odešlete změny a odstraňte odstraněný záznam z databáze.

9. Zavřete formulář.

10. Stiskněte klávesu **F5** a ověřte, že odstraněný záznam byl odebrán z databáze.

    > [!NOTE]
    > Pokud vaše aplikace používá edici SQL Server Express, v závislosti na hodnotě vlastnosti **Kopírovat do výstupního adresáře** souboru databáze se změny nemusí zobrazit, když stisknete klávesu **F5** v kroku 10.

## <a name="next-steps"></a>Další kroky

V závislosti na požadavcích vaší aplikace existuje několik kroků, které můžete chtít provést po vytvoření LINQ to SQL třídy entit. Mezi vylepšení, která jste mohli udělat v této aplikaci, patří následující:

- Implementovat kontrolu souběžnosti během aktualizací. Informace naleznete v tématu [Optimistická souběžnost: Přehled](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview).

- Přidejte dotazy LINQ pro filtrování dat. Informace najdete v tématu [Úvod do dotazů LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="see-also"></a>Viz také

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metody DataContext](../data-tools/datacontext-methods-o-r-designer.md)
- [Postupy: přiřazení uložených procedur pro provádění aktualizací, vkládání a odstraňování](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [Technologie LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [LINQ to SQL dotazy](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)
