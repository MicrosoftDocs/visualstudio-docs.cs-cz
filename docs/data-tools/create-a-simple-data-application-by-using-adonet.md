---
title: Vytvoření jednoduché datové aplikace pomocí ADO.NET
description: Naučte se vytvářet jednoduché aplikace založené na datových formulářích pomocí model Windows Forms a ADO.NET v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 44205f7f8f12d453a7c1d93ec8fee6ed1a3c1765
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436794"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>Vytvoření jednoduché datové aplikace pomocí ADO.NET

Když vytváříte aplikaci, která pracuje s daty v databázi, provádíte základní úkoly, jako je definování připojovacích řetězců, vkládání dat a spouštění uložených procedur. Podle tohoto tématu můžete zjistit, jak pracovat s databází z jednoduchého model Windows Forms aplikace "Forms over data" pomocí jazyka Visual C# nebo Visual Basic a ADO.NET.  Všechny datové technologie .NET, včetně datových sad, LINQ to SQL a Entity Framework, nakonec provádějí kroky, které jsou velmi podobné těm, které jsou uvedené v tomto článku.

Tento článek ukazuje jednoduchý způsob, jak rychle získat data z databáze. Pokud vaše aplikace potřebuje upravovat data v netriviálních způsobech a aktualizovat databázi, měli byste zvážit použití Entity Framework a použití datových vazeb k automatické synchronizaci ovládacích prvků uživatelského rozhraní se změnami v podkladových datech.

> [!IMPORTANT]
> Aby byl kód jednoduchý, nezahrnuje zpracování výjimek připravené pro produkční prostředí.

## <a name="prerequisites"></a>Předpoklady

Chcete-li vytvořit aplikaci, budete potřebovat:

- Visual Studio

- SQL Server Express LocalDB. Pokud nemáte SQL Server Express LocalDB, můžete si ho nainstalovat ze [stránky pro stažení SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express).

Toto téma předpokládá, že jste obeznámeni se základními funkcemi integrovaného vývojového prostředí (IDE) sady Visual Studio a můžete vytvořit aplikaci model Windows Forms, přidat formuláře do projektu, umístit tlačítka a další ovládací prvky do formulářů, nastavit vlastnosti ovládacích prvků a kódovat jednoduché události. Pokud s těmito úlohami nejste spokojeni, doporučujeme, abyste před zahájením tohoto návodu dokončili téma [Začínáme s jazykem Visual C# a Visual Basic](../ide/quickstart-visual-basic-console.md) .

## <a name="set-up-the-sample-database"></a>Vytvoření ukázkové databáze

Vytvořte ukázkovou databázi pomocí následujících kroků:

1. V aplikaci Visual Studio otevřete okno **Průzkumník serveru** .

2. Klikněte pravým tlačítkem na **datová připojení** a vyberte **vytvořit novou SQL Server databázi**.

3. Do textového pole **název serveru** zadejte **(LocalDB) \mssqllocaldb**.

4. Do textového pole **nový název databáze** zadejte **Sales** a pak zvolte **OK**.

     Prázdná **prodejní** databáze je vytvořena a přidána do uzlu datová připojení v Průzkumník serveru.

5. Klikněte pravým tlačítkem na připojení dat **prodeje** a vyberte **Nový dotaz**.

     Otevře se okno editoru dotazů.

6. Zkopírujte [prodejní skript Transact-SQL](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/data-tools/samples/sales.sql) do schránky.

7. Vložte skript T-SQL do editoru dotazů a pak klikněte na tlačítko **Spustit** .

     Po krátké době se dotaz dokončí a vytvoří se objekty databáze. Databáze obsahuje dvě tabulky: zákazník a objednávky. Tyto tabulky zpočátku neobsahují žádná data, ale při spuštění aplikace, kterou vytvoříte, můžete přidat data. Databáze obsahuje také čtyři jednoduché uložené procedury.

## <a name="create-the-forms-and-add-controls"></a>Vytvoření formulářů a přidání ovládacích prvků

1. Vytvořte projekt pro aplikaci model Windows Forms a pojmenujte ji **SimpleDataApp**.

    Visual Studio vytvoří projekt a několik souborů, včetně prázdného formuláře Windows s názvem **Form1**.

2. Přidejte do projektu dva formuláře Windows, aby měly tři formuláře, a pak jim přidělte tyto názvy:

   - **Navigace**

   - **NewCustomer**

   - **FillOrCancel**

3. U každého formuláře přidejte textová pole, tlačítka a další ovládací prvky, které se zobrazí na následujících obrázcích. Pro každý ovládací prvek nastavte vlastnosti, které tabulky popisují.

   > [!NOTE]
   > Pole skupiny a ovládací prvky Label přidávají přehlednost, ale nepoužívají se v kódu.

   **Navigační formulář**

   ![Navigační dialogové okno](../data-tools/media/simpleappnav.png)

|Ovládací prvky pro navigační formulář|Vlastnosti|
| - |----------------|
|Tlačítko|Název = btnGoToAdd|
|Tlačítko|Název = btnGoToFillOrCancel|
|Tlačítko|Název = btnExit|

**Formulář NewCustomer**

![Přidat nového zákazníka a umístit objednávku](../data-tools/media/simpleappnewcust.png)

|Ovládací prvky pro formulář NewCustomer|Vlastnosti|
| - |----------------|
|TextBox|Název = txtCustomerName|
|TextBox|Název = txtCustomerID<br /><br /> ReadOnly = true|
|Tlačítko|Název = btnCreateAccount|
|NumericUpdown|Počet desetinných míst = 0<br /><br /> Maximum = 5000<br /><br /> Název = numOrderAmount|
|DateTimePicker|Formát = krátký<br /><br /> Název = dtpOrderDate|
|Tlačítko|Název = btnPlaceOrder|
|Tlačítko|Název = btnAddAnotherAccount|
|Tlačítko|Název = btnAddFinish|

**Formulář FillOrCancel**

![vyplnit nebo zrušit objednávky](../data-tools/media/simpleappcancelfill.png)

|Ovládací prvky pro formulář FillOrCancel|Vlastnosti|
| - |----------------|
|TextBox|Název = txtOrderID|
|Tlačítko|Název = btnFindByOrderID|
|DateTimePicker|Formát = krátký<br /><br /> Název = dtpFillDate|
|DataGridView|Název = dgvCustomerOrders<br /><br /> ReadOnly = true<br /><br /> RowHeadersVisible = false|
|Tlačítko|Název = btnCancelOrder|
|Tlačítko|Název = btnFillOrder|
|Tlačítko|Název = btnFinishUpdates|

## <a name="store-the-connection-string"></a>Uložení připojovacího řetězce
Když se aplikace pokusí otevřít připojení k databázi, aplikace musí mít přístup k připojovacímu řetězci. Chcete-li se vyhnout zadávání řetězce ručně na každém formuláři, uložte řetězec do souboru *App.config* v projektu a vytvořte metodu, která vrátí řetězec, pokud je metoda volána z libovolného formuláře v aplikaci.

Připojovací řetězec můžete najít tak, že kliknete pravým tlačítkem na připojení k datům **prodeje** v **Průzkumník serveru** a zvolíte **vlastnosti**. Vyhledejte vlastnost **ConnectionString** a pak pomocí **kombinace kláves CTRL** + **a** , **CTRL** + **C** vyberte a zkopírujte řetězec do schránky.

1. Pokud používáte jazyk C#, v **Průzkumník řešení** rozbalte uzel **vlastnosti** v projektu a pak otevřete soubor **Settings. Settings** .
    Pokud používáte Visual Basic, klikněte v **Průzkumník řešení** na **Zobrazit všechny soubory** , rozbalte uzel **můj projekt** a pak otevřete soubor **Settings. Settings** .

2. Do sloupce **název** zadejte `connString` .

3. V seznamu **typ** vyberte **(připojovací řetězec)**.

4. V seznamu **Rozsah** vyberte možnost **aplikace**.

5. Ve sloupci **hodnota** zadejte připojovací řetězec (bez žádných vnějších uvozovek) a pak změny uložte.

> [!NOTE]
> V reálné aplikaci byste měli připojovací řetězec bezpečně ukládat, jak je popsáno v části [připojovací řetězce a konfigurační soubory](/dotnet/framework/data/adonet/connection-strings-and-configuration-files).

## <a name="write-the-code-for-the-forms"></a>Zápis kódu pro formuláře

Tato část obsahuje Stručné přehledy o tom, co jednotlivé formuláře dělá. Poskytuje také kód, který definuje základní logiku při kliknutí na tlačítko na formuláři.

### <a name="navigation-form"></a>Navigační formulář

Navigační formulář se otevře při spuštění aplikace. Tlačítko **Přidat účet** otevře formulář NewCustomer. Tlačítko **vyplnit nebo zrušit objednávky** otevře formulář FillOrCancel. Tlačítko **ukončit** ukončí aplikaci.

#### <a name="make-the-navigation-form-the-startup-form"></a>Nastavit navigační formulář jako úvodní formulář

Pokud používáte jazyk C#, v **Průzkumník řešení** otevřete **program.cs** a potom změňte `Application.Run` řádek na toto: `Application.Run(new Navigation());`

Pokud používáte Visual Basic, v **Průzkumník řešení** otevřete okno **vlastnosti** , vyberte kartu **aplikace** a pak v seznamu **spouštěcí formulář** vyberte **SimpleDataApp. Navigation** .

#### <a name="create-auto-generated-event-handlers"></a>Vytváření automaticky generovaných obslužných rutin událostí

Dvojím kliknutím na tři tlačítka v navigačním formuláři Vytvořte prázdné metody obslužné rutiny události. Dvojím kliknutím na tlačítka se do souboru kódu návrháře přidá automaticky generovaný kód, který umožňuje vyvolat událost kliknutím na tlačítko.

#### <a name="add-code-for-the-navigation-form-logic"></a>Přidat kód pro logiku pro navigační formulář

Na kódové stránce pro navigační formulář dokončete tělo metody pro tři obslužné rutiny události kliknutí na tlačítko, jak je znázorněno v následujícím kódu.

[!code-csharp[Navigation#1](../data-tools/codesnippet/CSharp/SimpleDataApp/Navigation.cs#1)]
[!code-vb[Navigation#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/Navigation.vb#1)]

### <a name="newcustomer-form"></a>Formulář NewCustomer

Když zadáte název zákazníka a pak vyberete tlačítko **vytvořit účet** , vytvoří formulář NewCustomer účet zákazníka SQL Server a jako nové ID zákazníka vrátí hodnotu identity. Pak můžete umístit objednávku nového účtu zadáním částky a data objednávky a výběrem tlačítka **objednat místo** .

#### <a name="create-auto-generated-event-handlers"></a>Vytváření automaticky generovaných obslužných rutin událostí

Vytvořte prázdnou obslužnou rutinu události Click pro každé tlačítko ve formuláři NewCustomer dvojitým kliknutím na každé ze čtyř tlačítek. Dvojím kliknutím na tlačítka se do souboru kódu návrháře přidá automaticky generovaný kód, který umožňuje vyvolat událost kliknutím na tlačítko.

#### <a name="add-code-for-the-newcustomer-form-logic"></a>Přidání kódu pro logiku formuláře NewCustomer

Chcete-li dokončit logiku formuláře NewCustomer, postupujte podle těchto kroků.

1. Přiřaďte `System.Data.SqlClient` obor názvů do oboru, abyste nemuseli plně kvalifikovat názvy svých členů.

     ```csharp
     using System.Data.SqlClient;
     ```

     ```vb
     Imports System.Data.SqlClient
     ```

2. Přidejte do třídy některé proměnné a pomocné metody, jak je znázorněno v následujícím kódu.

     [!code-csharp[NewCustomer#1](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#1)]
     [!code-vb[NewCustomer#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#1)]

3. Dokončete tělo metody pro čtyři obslužné rutiny události kliknutí na tlačítko, jak je znázorněno v následujícím kódu.

     [!code-csharp[NewCustomer#2](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#2)]
     [!code-vb[NewCustomer#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#2)]

### <a name="fillorcancel-form"></a>Formulář FillOrCancel

Formulář FillOrCancel spustí dotaz, který vrátí objednávku, když zadáte ID objednávky a kliknete na tlačítko **najít objednávku** . Vrácený řádek se zobrazí v mřížce dat, která je jen pro čtení. Pokud vyberete tlačítko pro **zrušení objednávky** , můžete objednávku označit jako zrušenou (X), nebo objednávku označit jako vyplněnou (F), pokud vyberete tlačítko **pořadí výplně** . Pokud znovu vyberete tlačítko **najít objednávku** , zobrazí se aktualizovaný řádek.

#### <a name="create-auto-generated-event-handlers"></a>Vytváření automaticky generovaných obslužných rutin událostí

Vytvořte prázdné obslužné rutiny události Click pro čtyři tlačítka ve formuláři FillOrCancel dvojitým kliknutím na tlačítka. Dvojím kliknutím na tlačítka se do souboru kódu návrháře přidá automaticky generovaný kód, který umožňuje vyvolat událost kliknutím na tlačítko.

#### <a name="add-code-for-the-fillorcancel-form-logic"></a>Přidání kódu pro logiku formuláře FillOrCancel

Chcete-li dokončit logiku formuláře FillOrCancel, postupujte podle těchto kroků.

1. Přeneste následující dva obory názvů do oboru, takže nemusíte plně kvalifikovat názvy jejich členů.

     ```csharp
     using System.Data.SqlClient;
     using System.Text.RegularExpressions;
     ```

     ```vb
     Imports System.Data.SqlClient
     Imports System.Text.RegularExpressions
     ```

2. Přidejte proměnnou a pomocnou metodu do třídy, jak je znázorněno v následujícím kódu.

     [!code-csharp[FillOrCancel#1](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#1)]
     [!code-vb[FillOrCancel#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#1)]

3. Dokončete tělo metody pro čtyři obslužné rutiny události kliknutí na tlačítko, jak je znázorněno v následujícím kódu.

     [!code-csharp[FillOrCancel#2](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#2)]
     [!code-vb[FillOrCancel#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#2)]

## <a name="test-your-application"></a>Testování aplikace

Vyberte klávesu **F5** pro sestavení a otestování aplikace po kódu každé obslužné rutiny události Click a poté po dokončení kódování.

## <a name="see-also"></a>Viz také

- [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
