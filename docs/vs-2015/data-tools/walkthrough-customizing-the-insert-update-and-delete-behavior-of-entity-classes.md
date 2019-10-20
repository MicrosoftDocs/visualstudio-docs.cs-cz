---
title: 'Návod: přizpůsobení chování při vložení, aktualizaci a odstranění tříd entit | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9901d917de2babf4992519ffe6b360454542aad1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602562"
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>Návod: přizpůsobení chování při vložení, aktualizaci a odstranění tříd entit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) poskytují vizuální návrhovou plochu pro vytváření a úpravu [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] tříd (třídy entit), které jsou založené na objektech v databázi. Pomocí [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)můžete pro přístup k databázím SQL použít technologii LINQ. Další informace naleznete v tématu [LINQ (jazykově integrovaný dotaz)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).

 Ve výchozím nastavení je logika pro provádění aktualizací poskytována modulem runtime [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]. Modul runtime vytvoří výchozí příkazy INSERT, Update a DELETE na základě schématu tabulky (definice sloupce a informace o primárním klíči). Pokud nechcete použít výchozí chování, můžete nakonfigurovat chování aktualizace a určit konkrétní uložené procedury pro provádění nezbytných vložení, aktualizací a odstranění, které je nutné pro práci s daty v databázi. To lze provést také v případě, že se výchozí chování negeneruje, například když vaše třídy entit budou mapovány na zobrazení. Kromě toho můžete přepsat výchozí chování aktualizace, když databáze vyžaduje přístup k tabulce prostřednictvím uložených procedur. Další informace najdete v tématu [přizpůsobení operací pomocí uložených procedur](https://msdn.microsoft.com/library/aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a).

> [!NOTE]
> Tento návod vyžaduje dostupnost uložených procedur **InsertCustomer**, **UpdateCustomer**a **DeleteCustomer** pro databázi Northwind.

 Tento návod popisuje kroky, které je nutné provést, chcete-li přepsat výchozí chování modulu runtime LINQ to SQL pro ukládání dat zpět do databáze pomocí uložených procedur.

 V tomto návodu se dozvíte, jak provádět následující úlohy:

- Vytvořte novou aplikaci model Windows Forms a přidejte do ní soubor [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)].

- Vytvořte třídu entity, která je namapována na tabulku zákazníků Northwind.

- Vytvořte zdroj dat objektu, který odkazuje na třídu zákazníka LINQ to SQL.

- Vytvořte formulář Windows, který obsahuje <xref:System.Windows.Forms.DataGridView>, která je vázaná na třídu Customer Customer.

- Implementujte funkci Save pro formulář.

- Vytvořte <xref:System.Data.Linq.DataContext> metody přidáním uložených procedur do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

- Nakonfigurujte zákaznickou třídu pro použití uložených procedur k provádění vložení, aktualizací a odstranění.

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu potřebujete následující:

- Přístup k SQL Server verzi ukázkové databáze Northwind.

- Uložené procedury **InsertCustomer**, **UpdateCustomer**a **DeleteCustomer** pro databázi Northwind.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Vytvoření aplikace a přidání tříd LINQ to SQL
 Vzhledem k tomu, že budete pracovat s [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]mi třídami a chcete zobrazit data ve formuláři Windows, vytvořte novou aplikaci model Windows Forms a přidejte LINQ to SQL souboru tříd.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-a-new-windows-application-project-that-contains-linq-to-sql-classes"></a>Vytvoření nového projektu aplikace pro systém Windows, který obsahuje třídy LINQ to SQL

1. V nabídce **soubor** vytvořte nový projekt.

2. Pojmenujte projekt **UpdatingwithSProcsWalkthrough**.

    > [!NOTE]
    > @No__t_0 je podporován v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] a C# projektech. Proto vytvořte nový projekt v jednom z těchto jazyků.

3. Klikněte na šablonu **aplikace model Windows Forms** a klikněte na tlačítko **OK**. Další informace najdete v tématu [klientské aplikace](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Projekt UpdatingwithSProcsWalkthrough je vytvořen a přidán do **Průzkumník řešení**.

4. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

5. Klikněte na šablonu **třídy LINQ to SQL** a do pole **název** zadejte **Northwind. dbml** .

6. Klikněte na tlačítko **Přidat**.

     Do projektu se přidá prázdný soubor tříd LINQ to SQL (Northwind. dbml) a otevře se [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

## <a name="creating-the-customer-entity-class-and-object-data-source"></a>Vytvoření třídy entity zákazníka a zdroje dat objektu
 Vytvořte [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] třídy, které jsou namapované na tabulky databáze, přetažením tabulek z **Průzkumník serveru** /**průzkumníku databáze** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Výsledkem je LINQ to SQL třídy entit, které jsou mapovány na tabulky v databázi. Po vytvoření tříd entit je lze použít jako zdroje dat objektů stejně jako jiné třídy, které mají veřejné vlastnosti.

#### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Vytvoření třídy entity zákazníka a konfigurace zdroje dat

1. V **Průzkumník serveru** /**Průzkumníku databáze**vyhledejte tabulku Customer v SQL Server verzi ukázkové databáze Northwind.

2. Přetáhněte uzel **zákazníci** z **Průzkumník serveru** /**Průzkumníku databáze** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] plochu.

     Vytvoří se Třída entity s názvem **Zákazník** . Obsahuje vlastnosti, které odpovídají sloupcům v tabulce Customers. Třída entity se nazývá **Customer** (ne **zákazníci**), protože představuje jednoho zákazníka z tabulky Customers.

    > [!NOTE]
    > Chování při přejmenování se nazývá *plural*. Dá se zapnout nebo vypnout v [dialogovém okně Možnosti](../ide/reference/options-dialog-box-visual-studio.md). Další informace najdete v tématu [Postup: zapnutí a vypnutí funkce plural (o/R Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3. V nabídce **sestavení** klikněte na **sestavit UpdatingwithSProcsWalkthrough** a sestavte projekt.

4. V nabídce **data** klikněte na možnost **Zobrazit zdroje dat**.

5. V okně **zdroje dat** klikněte na tlačítko **Přidat nový zdroj dat**.

6. Klikněte na **objekt** na stránce **Zvolte typ zdroje dat** a potom klikněte na tlačítko **Další**.

7. Rozbalte uzel **UpdatingwithSProcsWalkthrough** a vyhledejte a vyberte třídu **Customer** .

    > [!NOTE]
    > Pokud třída **zákazníka** není k dispozici, ukončete průvodce, sestavte projekt a spusťte průvodce znovu.

8. Kliknutím na tlačítko **Dokončit** vytvořte zdroj dat a přidejte třídu entity **zákazníka** do okna **zdroje dat** .

## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Vytvoření ovládacího prvku DataGridView pro zobrazení zákaznických dat ve formuláři Windows
 Vytvořte ovládací prvky, které jsou vázány na třídy entit přetažením [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] položky zdroje dat z okna **zdroje dat** do formuláře Windows Form.

#### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Chcete-li přidat ovládací prvky, které jsou vázány na třídy entit

1. Otevřete Form1 v zobrazení Návrh.

2. V okně **zdroje dat** Přetáhněte uzel **Zákazník** na Form1.

    > [!NOTE]
    > Chcete-li zobrazit okno **zdroje dat** , klikněte na možnost **Zobrazit zdroje dat** v nabídce **data** .

3. Otevřete Form1 v editoru kódu.

4. Přidejte následující kód do formuláře, globální do formuláře, mimo jakoukoliv konkrétní metodu, ale uvnitř třídy Form1:

    ```vb
    Private NorthwindDataContext1 As New NorthwindDataContext
    ```

    ```csharp
    private NorthwindDataContext northwindDataContext1
        = new NorthwindDataContext();

    ```

5. Vytvořte obslužnou rutinu události pro událost `Form_Load` a přidejte následující kód do obslužné rutiny:

    ```vb
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers
    ```

    ```csharp
    customerBindingSource.DataSource
        = northwindDataContext1.Customers;

    ```

## <a name="implementing-save-functionality"></a>Implementace funkce Save
 Ve výchozím nastavení není tlačítko Uložit povoleno a funkce Uložit nejsou implementovány. Také není automaticky přidán kód pro uložení změněných dat do databáze, když jsou vytvořeny ovládací prvky vázané na data pro zdroje dat objektu. V této části se dozvíte, jak povolit tlačítko Uložit a implementovat ukládání funkcí pro [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] objekty.

#### <a name="to-implement-save-functionality"></a>Implementace funkce Uložit

1. Otevřete Form1 v zobrazení Návrh.

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

## <a name="overriding-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Přepsání výchozího chování pro provádění aktualizací (vložení, aktualizace a odstranění)

#### <a name="to-override-the-default-update-behavior"></a>Přepsání výchozího chování aktualizace

1. Otevřete LINQ to SQL soubor v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (V **Průzkumník řešení**dvakrát klikněte na soubor **Northwind. dbml** .)

2. V **Průzkumník serveru** /**Průzkumníku databáze**rozbalte uzel **uložené procedury** databáze Northwind a vyhledejte uložené procedury **InsertCustomers**, **UpdateCustomers**a **DeleteCustomers** .

3. Přetáhněte všechny tři uložené procedury do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Uložené procedury jsou přidány do podokna metody jako metody <xref:System.Data.Linq.DataContext>. Další informace naleznete v tématu [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. Vyberte třídu entity **zákazníka** v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

5. V okně **vlastnosti** vyberte vlastnost **Vložit** .

6. Kliknutím na tlačítko se třemi tečkami (...) vedle pole **použít modul runtime** otevřete dialogové okno **Konfigurovat chování** .

7. Vyberte **přizpůsobit**.

8. V seznamu **přizpůsobit** vyberte metodu **InsertCustomers** .

9. Kliknutím na **použít** uložte konfiguraci pro vybranou třídu a chování.

    > [!NOTE]
    > Můžete pokračovat v konfiguraci chování pro každou kombinaci třídy/chování, pokud kliknete na **použít** po provedení každé změny. Pokud změníte třídu nebo chování předtím, než kliknete na **použít**, zobrazí se dialogové okno s upozorněním, které vám nabídne možnost použít změny.

10. V seznamu **chování** vyberte **aktualizovat** .

11. Vyberte **přizpůsobit**.

12. V seznamu **přizpůsobit** vyberte metodu **UpdateCustomers** .

     Zkontrolujte seznam **argumentů metody** a **vlastností třídy** a Všimněte si, že existují dva **argumenty metody** a dvě **vlastnosti třídy** pro některé sloupce v tabulce. Díky tomu je snazší sledovat změny a vytvářet příkazy, které kontrolují porušení souběžnosti.

13. Namapujte argument **Original_CustomerID** metody na vlastnost **KódZákazníka (původní)** Class.

    > [!NOTE]
    > Ve výchozím nastavení budou argumenty metody namapovány na vlastnosti třídy, pokud se názvy shodují. Pokud se změní názvy vlastností a již se neshodují mezi tabulkou a třídou entity, může být nutné vybrat vlastnost ekvivalentní třídy, která má být mapována, pokud Návrhář relací v/R nemůže určit správné mapování. Kromě toho, pokud argumenty metody nemají platné vlastnosti třídy pro mapování, můžete nastavit **vlastnost třídy** na hodnotu **(žádný)** .

14. Kliknutím na **použít** uložte konfiguraci pro vybranou třídu a chování.

15. V seznamu **chování** vyberte **Odstranit** .

16. Vyberte **přizpůsobit**.

17. V seznamu **přizpůsobit** vyberte metodu **DeleteCustomers** .

18. Namapujte argument **Original_CustomerID** metody na vlastnost **KódZákazníka (původní)** Class.

19. Klikněte na tlačítko **OK**.

> [!NOTE]
> I když se pro tento konkrétní návod nejedná o problém, je vhodné poznamenat, že [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] zpracovává hodnoty generované databázemi automaticky pro identitu (automatické zvýšení), ROWGUIDCOL (GUID generovaný identifikátor GUID) a sloupce časového razítka během vkládání a Aktualizovány. Hodnoty generované databází v jiných typech sloupců neočekávaně způsobí hodnotu null. Chcete-li vrátit hodnoty generované databází, je třeba ručně nastavit <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> `true` a <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> na jednu z následujících možností: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> nebo <xref:System.Data.Linq.Mapping.AutoSync>.

## <a name="testing-the-application"></a>Testování aplikace
 Spusťte aplikaci znovu, abyste ověřili, že uložená procedura **UpdateCustomers** správně aktualizuje záznam zákazníka v databázi.

#### <a name="to-test-the-application"></a>Testování aplikace

1. Stiskněte klávesu F5.

2. Úpravou záznamu v mřížce otestujete chování aktualizace.

3. Přidejte nový záznam pro otestování chování při vkládání.

4. Kliknutím na tlačítko Uložit uložte změny zpět do databáze.

5. Zavřete formulář.

6. Stiskněte klávesu F5 a ověřte, že aktualizovaný záznam a nově vložený záznam jsou trvalé.

7. Odstraňte nový záznam, který jste vytvořili v kroku 3, abyste otestovali chování při odstraňování.

8. Kliknutím na tlačítko Uložit změny odešlete a odstraníte odstraněný záznam z databáze.

9. Zavřete formulář.

10. Stiskněte klávesu F5 a ověřte, že odstraněný záznam byl odebrán z databáze.

    > [!NOTE]
    > Pokud vaše aplikace používá edici SQL Server Express, v závislosti na hodnotě vlastnosti **Kopírovat do výstupního adresáře** souboru databáze se změny nemusí zobrazit, když stisknete klávesu F5 v kroku 10.

## <a name="next-steps"></a>Další kroky
 V závislosti na požadavcích vaší aplikace existuje několik kroků, které můžete chtít provést po vytvoření [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] třídy entit. Mezi vylepšení, která jste mohli udělat v této aplikaci, patří následující:

- Implementovat kontrolu souběžnosti během aktualizací. Informace naleznete v tématu [Optimistická souběžnost: Přehled](https://msdn.microsoft.com/library/c2e38512-d0c8-4807-b30a-cb7e30338694).

- Přidejte dotazy LINQ pro filtrování dat. Informace najdete v tématu [Úvod do dotazů LINQ (C#)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).

## <a name="see-also"></a>Viz také
 [LINQ to SQL nástroje v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [LINQ to SQL dotazy](https://msdn.microsoft.com/library/f4897aaa-7f44-4c20-a471-b948c2971aae) na [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md) [Postupy: přiřazení uložených procedur pro provádění aktualizací, vkládání a odstraňování (o/r designeru) Pave,](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [co je nového pro Vývoj aplikací pro data v aplikaci Visual Studio 2012](https://msdn.microsoft.com/3d50d68f-5f44-4915-842f-6d42fce793f1)
