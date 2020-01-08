---
title: Vytvoření jednoduché datové aplikace pomocí ADO.NET
ms.date: 08/23/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8f35173ded1ba4d52e0c5a9800fa228a7f93b981
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586871"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>Vytvoření jednoduché datové aplikace pomocí ADO.NET

Když vytvoříte aplikaci, která zpracovává data v databázi, provedete základní úlohy, jako je například definování připojovacích řetězců, vkládání dat a spouštění uložených procedur. Podle tohoto tématu můžete zjistit, jak pracovat s databází z jednoduchého "formy nad daty" aplikace Windows Forms pomocí Visual C# nebo Visual Basic a ADO.NET.  Všechna data technologie .NET, včetně datových sad, LINQ to SQL a Entity Framework – nakonec proveďte kroky, které jsou velmi podobné těm, které jsou uvedené v tomto článku.

Tento článek ukazuje jednoduchý způsob, jak získat data z databáze v podobě rychlé. Pokud vaše aplikace potřebuje upravovat data nejsou v netriviálních způsoby a aktualizaci databáze, měli byste zvážit používající nástroj Entity Framework a použití datových vazeb se automaticky synchronizovat ovládacích prvků uživatelského rozhraní na změny v podkladových datech.

> [!IMPORTANT]
> Chcete-li být kód jednoduchý, neměl by zahrnovat zpracování výjimek připravené pro produkční prostředí.

## <a name="prerequisites"></a>Požadavky

Chcete-li vytvořit aplikaci, budete potřebovat:

- Visual Studio.

- SQL Server Express LocalDB. Pokud nemáte SQL Server Express LocalDB, můžete ho nainstalovat [SQL Server Express stránku pro stažení](https://www.microsoft.com/sql-server/sql-server-editions-express).

Toto téma předpokládá, že ovládáte základní funkce integrovaného vývojového prostředí sady Visual Studio a můžete vytvořit aplikaci Windows Forms, přidat formuláře do projektu, Vložit tlačítka a další ovládací prvky ve formulářích, nastavte vlastnosti ovládacích prvků a kódovat jednoduché události. Pokud si nejste seznámení s těmito úkoly, doporučujeme provést [Začínáme s Vizuálem C# a Visual Basic](../ide/quickstart-visual-basic-console.md) tématu před zahájením tohoto návodu.

## <a name="set-up-the-sample-database"></a>Vytvoření ukázkové databáze

Vytvoření ukázkové databáze pomocí následujících kroků:

1. V sadě Visual Studio, otevřete **Průzkumníka serveru** okna.

2. Klikněte pravým tlačítkem na **datová připojení** a zvolte **vytvořit novou databázi SQL serveru**.

3. V **název serveru** textové pole, zadejte **(localdb) \mssqllocaldb**.

4. V **nového názvu databázového** textové pole, zadejte **Sales**, klikněte na tlačítko **OK**.

     Prázdné **Sales** databáze je vytvořen a přidán do uzlu datového připojení v Průzkumníku serveru.

5. Klikněte pravým tlačítkem na **Sales** datové připojení a vyberte **nový dotaz**.

     Otevře se okno editor dotazů.

6. Kopírovat [Sales příkazů jazyka Transact-SQL skriptů](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/data-tools/samples/sales.sql) do schránky.

7. Vložte skript T-SQL do editoru dotazů a klikněte na tlačítko **Execute** tlačítko.

     Po chvilce dotaz doběhnutí a databázové objekty jsou vytvořeny. Databáze obsahuje dvě tabulky: Customer a Orders. Tyto tabulky zpočátku neobsahují žádná data, ale přidáte data při spuštění aplikace, kterou vytvoříte. Databáze také obsahuje čtyři jednoduchých uložených procedur.

## <a name="create-the-forms-and-add-controls"></a>Vytvoření formulářů a přidání ovládacích prvků

1. Vytvořte projekt aplikace Windows Forms a pojmenujte jej **SimpleDataApp**.

    Visual Studio vytvoří projekt a několik souborů, včetně prázdný formulář Windows s názvem **Form1**.

2. Přidejte do projektu dva formuláře Windows, tak, aby měl tři formuláře a dejte jim následující názvy:

   - **Navigace**

   - **NewCustomer**

   - **FillOrCancel**

3. U každého formuláře přidejte textová pole, tlačítka a další ovládací prvky, které se zobrazují na následujících obrázcích. Pro každý ovládací prvek nastavte vlastnosti, které jsou popsány v tabulce.

   > [!NOTE]
   > Skupinový rámeček a ovládací prvky popisku přehlednosti, ale nepoužívají se v kódu.

   **Navigační formulář**

   ![Dialogové okno navigace](../data-tools/media/simpleappnav.png)

|Ovládací prvky formuláře Navigation|Vlastnosti|
| - |----------------|
|Tlačítko|Název = btnGoToAdd|
|Tlačítko|Název = btnGoToFillOrCancel|
|Tlačítko|Název = btnExit|

**Formulář NewCustomer**

![Přidání nového odběratele a objednávky](../data-tools/media/simpleappnewcust.png)

|Ovládací prvky formuláře NewCustomer|Vlastnosti|
| - |----------------|
|TextBox|Název = txtCustomerName|
|TextBox|Název = txtCustomerID<br /><br /> Jen pro čtení = True|
|Tlačítko|Název = btnCreateAccount|
|NumericUpdown|Počet desetinných míst = 0<br /><br /> Maximální = 5000<br /><br /> Název = numOrderAmount|
|Ovládacího prvku DateTimePicker|Formát = krátké<br /><br /> Název = dtpOrderDate|
|Tlačítko|Název = btnPlaceOrder|
|Tlačítko|Název = btnAddAnotherAccount|
|Tlačítko|Název = btnAddFinish|

**Formulář FillOrCancel**

![vyplnit nebo zrušit objednávky](../data-tools/media/simpleappcancelfill.png)

|Ovládací prvky formuláře FillOrCancel|Vlastnosti|
| - |----------------|
|TextBox|Název = txtOrderID|
|Tlačítko|Název = btnFindByOrderID|
|Ovládacího prvku DateTimePicker|Formát = krátké<br /><br /> Název = dtpFillDate|
|Ovládací prvek DataGridView|Název = dgvCustomerOrders<br /><br /> Jen pro čtení = True<br /><br /> RowHeadersVisible = False|
|Tlačítko|Název = btnCancelOrder|
|Tlačítko|Název = btnFillOrder|
|Tlačítko|Název = btnFinishUpdates|

## <a name="store-the-connection-string"></a>Store připojovací řetězec
Když vaše aplikace se pokusí otevřít připojení k databázi, musí mít vaše aplikace přístup k připojovací řetězec. Aby se zabránilo ručním zadáním řetězce na každém formuláři, uložte řetězec v *App.config* souborů ve vašem projektu a vytvořte metodu, která vrátí řetězec, když je volána metoda z libovolného formuláře v aplikaci.

Připojovací řetězec můžete najít kliknutím pravým tlačítkem na **Sales** datové připojení v **Průzkumníka serveru** a zvolíte **vlastnosti**. Vyhledejte **ConnectionString** vlastnost, pak použijte **Ctrl**+**A**, **Ctrl**+**C**  vyberte a zkopírujte řetězec do schránky.

1. Pokud používáte C#v **Průzkumníka řešení**, rozbalte **vlastnosti** uzlu v rámci projektu a potom otevřete **Settings.settings** souboru.
    Pokud používáte Visual Basic v **Průzkumníka řešení**, klikněte na tlačítko **zobrazit všechny soubory**, rozbalte **Můj projekt** uzlu a pak otevřete **Settings.settings** souboru.

2. V **název** sloupce, zadejte `connString`.

3. V **typ** seznamu vyberte **(připojovací řetězec)** .

4. V **oboru** seznamu vyberte **aplikace**.

5. V **hodnotu** sloupce, zadejte svůj připojovací řetězec (bez jakékoli mimo uvozovky) a pak uložte provedené změny.

> [!NOTE]
> V reálné aplikaci byste měli uložit připojovací řetězec bezpečně, jak je popsáno v [připojovací řetězce a konfigurační soubory](/dotnet/framework/data/adonet/connection-strings-and-configuration-files).

## <a name="write-the-code-for-the-forms"></a>Napište kód pro formuláře

Tato část obsahuje stručný přehled, co dělá každý formulář. Také poskytuje kód, který definuje logiku, když dojde ke kliknutí na tlačítko na formuláři.

### <a name="navigation-form"></a>Navigační formulář

Navigační formulář se otevře při spuštění aplikace. **Přidat účet** tlačítko k otevření formuláře NewCustomer. **Vyplnit nebo zrušit objednávku** tlačítko k otevření formuláře FillOrCancel. **Ukončovací** tlačítko slouží k ukončení aplikace.

#### <a name="make-the-navigation-form-the-startup-form"></a>Vytvořit formulář změna formuláře úvodního formuláře navigace

Pokud používáte C#v **Průzkumníka řešení**, otevřete **Program.cs**a potom změňte `Application.Run` řádek, který toto: `Application.Run(new Navigation());`

Pokud používáte Visual Basic v **Průzkumníka řešení**, otevřete **vlastnosti** okna, vyberte **aplikace** kartu a potom vyberte  **SimpleDataApp.Navigation** v **úvodní formulář** seznamu.

#### <a name="create-auto-generated-event-handlers"></a>Vytváření obslužných rutin událostí automaticky generované

Dvakrát klikněte na tři tlačítka na formuláři navigace k vytvoření obslužné rutiny události prázdný. Dvojitým kliknutím na tlačítka také přidá automaticky generovaný kód v souboru kódu návrháře, který umožňuje tlačítko k vyvolání události.

#### <a name="add-code-for-the-navigation-form-logic"></a>Přidejte kód pro logiku formuláře navigace

Na stránce kódu pro formulář navigace dokončení těla metod pro tři tlačítka obslužné rutiny události kliknutí jak je znázorněno v následujícím kódu.

[!code-csharp[Navigation#1](../data-tools/codesnippet/CSharp/SimpleDataApp/Navigation.cs#1)]
[!code-vb[Navigation#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/Navigation.vb#1)]

### <a name="newcustomer-form"></a>Formulář NewCustomer

Když zadáte název zákazníka a pak vyberete **vytvořit účet** tlačítko, formulář NewCustomer vytvoří účet zákazníka a SQL Server vrátí hodnotu IDENTITY jako nové ID zákazníka. Můžete poté pošlete objednávku nového účtu zadáním částku a data objednávky a výběrem **objednat** tlačítko.

#### <a name="create-auto-generated-event-handlers"></a>Vytváření obslužných rutin událostí automaticky generované

Vytvořit prázdný klikněte na obslužnou rutinu události pro každé tlačítko na formulář NewCustomer dvojitým kliknutím na každý ze čtyř tlačítek. Dvojitým kliknutím na tlačítka také přidá automaticky generovaný kód v souboru kódu návrháře, který umožňuje tlačítko k vyvolání události.

#### <a name="add-code-for-the-newcustomer-form-logic"></a>Přidejte kód pro logiku formuláře NewCustomer

Dokončete logiky formuláře NewCustomer postupujte podle těchto kroků.

1. Převést `System.Data.SqlClient` oboru názvů do oboru, takže není nutné plně kvalifikovat názvy z jejích členů.

     ```csharp
     using System.Data.SqlClient;
     ```

     ```vb
     Imports System.Data.SqlClient
     ```

2. Přidejte několik proměnných a pomocné metody pro třídu, jak je znázorněno v následujícím kódu.

     [!code-csharp[NewCustomer#1](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#1)]
     [!code-vb[NewCustomer#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#1)]

3. Kompletní těla metod pro čtyři tlačítka obslužné rutiny události kliknutí jak je znázorněno v následujícím kódu.

     [!code-csharp[NewCustomer#2](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#2)]
     [!code-vb[NewCustomer#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#2)]

### <a name="fillorcancel-form"></a>Formulář FillOrCancel

Formulář FillOrCancel spustí dotaz a vrátit objednávku, když zadejte ID objednávky a potom klikněte na tlačítko **vyhledat objednávku** tlačítko. Vrácený řádek se zobrazí v mřížce dat jen pro čtení. Můžete označit objednávku jako zrušenou (X), pokud jste vybrali **zrušit objednávku** tlačítko, nebo můžete označit objednávku jako vyplněnou (F) Pokud jste vybrali **vyplnit objednávku** tlačítko. Pokud vyberete **vyhledat objednávku** tlačítko znovu, zobrazí se aktualizovaný řádek.

#### <a name="create-auto-generated-event-handlers"></a>Vytváření obslužných rutin událostí automaticky generované

Vytvořit prázdné obslužné rutiny události pro čtyři tlačítka do formuláře FillOrCancel kliknutí dvojitým kliknutím na tlačítka. Dvojitým kliknutím na tlačítka také přidá automaticky generovaný kód v souboru kódu návrháře, který umožňuje tlačítko k vyvolání události.

#### <a name="add-code-for-the-fillorcancel-form-logic"></a>Přidejte kód pro logiku formuláře FillOrCancel

Dokončete logiky formuláře FillOrCancel postupujte podle těchto kroků.

1. Následující dva obory názvů převeďte do rozsahu, takže není nutné k plnému určení jména jejich členů.

     ```csharp
     using System.Data.SqlClient;
     using System.Text.RegularExpressions;
     ```

     ```vb
     Imports System.Data.SqlClient
     Imports System.Text.RegularExpressions
     ```

2. Přidejte proměnnou a pomocné metody do třídy, jak je znázorněno v následujícím kódu.

     [!code-csharp[FillOrCancel#1](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#1)]
     [!code-vb[FillOrCancel#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#1)]

3. Kompletní těla metod pro čtyři tlačítka obslužné rutiny události kliknutí jak je znázorněno v následujícím kódu.

     [!code-csharp[FillOrCancel#2](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#2)]
     [!code-vb[FillOrCancel#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#2)]

## <a name="test-your-application"></a>Testování aplikace

Vyberte **F5** klíče pro sestavení a testování vaší aplikace po kódu každé obslužné rutiny události kliknutí a potom můžete po dokončení kódování.

## <a name="see-also"></a>Viz také:

- [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
