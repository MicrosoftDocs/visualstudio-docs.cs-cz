---
title: Zpracování výjimky souběžnosti
description: Zpracování výjimky souběžnosti (System. data. DBConcurrencyException –), která je vyvolána, když se dva uživatelé pokusí změnit stejná data v databázi ve stejnou chvíli.
ms.custom: SEO-VS-2020
ms.date: 09/11/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: f84fbaae3273b8830cce1c39cc3e42b62e487d3e
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216238"
---
# <a name="handle-a-concurrency-exception"></a>Zpracování výjimky souběžnosti

Výjimky souběžnosti ( <xref:System.Data.DBConcurrencyException?displayProperty=fullName> ) jsou vyvolány, když se dva uživatelé pokusí změnit stejná data v databázi ve stejnou chvíli. V tomto návodu vytvoříte aplikaci pro Windows, která ukazuje, jak zachytit <xref:System.Data.DBConcurrencyException> , najít řádek, který způsobil chybu, a Naučte se, jak ho zpracovat.

Tento návod vás provede následujícím procesem:

1. Vytvořte nový projekt **aplikace model Windows Forms** .

2. Vytvořte novou datovou sadu založenou na tabulce Northwind Customers.

3. Vytvořte formulář s a <xref:System.Windows.Forms.DataGridView> zobrazíte data.

4. Naplňte datovou sadu daty z tabulky Customers v databázi Northwind.

5. Použijte funkci **Zobrazit data tabulky** v **Průzkumník serveru** pro přístup k datům tabulky Customers – tabulka a změnu záznamu.

6. Změňte stejný záznam na jinou hodnotu, aktualizujte datovou sadu a pokuste se provést zápis změn do databáze, což vede k tomu, že dojde k chybě souběžnosti.

7. Zachyťte chybu a pak zobrazte různé verze záznamu, aby uživatel mohl určit, jestli se má pokračovat a aktualizovat databázi, nebo zrušit aktualizaci.

## <a name="prerequisites"></a>Požadavky

Tento návod používá SQL Server Express LocalDB a ukázkovou databázi Northwind.

1. Pokud nemáte SQL Server Express LocalDB, nainstalujte ji buď ze [stránky pro stažení SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program pro Visual Studio**. V **instalační program pro Visual Studio** můžete nainstalovat SQL Server Express LocalDB jako součást úlohy **ukládání a zpracování dat** nebo jako jednotlivé komponenty.

2. Nainstalujte ukázkovou databázi Northwind pomocí následujících kroků:

    1. V aplikaci Visual Studio otevřete okno **Průzkumník objektů systému SQL Server** . (Průzkumník objektů systému SQL Server je nainstalován v rámci úlohy **úložiště dat a zpracování** v instalační program pro Visual Studio.) Rozbalte uzel **SQL Server** . Klikněte pravým tlačítkem na instanci LocalDB a vyberte **Nový dotaz**.

       Otevře se okno editoru dotazů.

    2. Zkopírujte [skript Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind od začátku a naplní ji daty.

    3. Vložte skript T-SQL do editoru dotazů a pak klikněte na tlačítko **Spustit** .

       Po krátké době se dotaz dokončí a vytvoří se databáze Northwind.

## <a name="create-a-new-project"></a>Vytvoření nového projektu

Začněte vytvořením nové aplikace model Windows Forms:

1. V aplikaci Visual Studio v nabídce **soubor** vyberte **Nový**  >  **projekt**.

2. V levém podokně rozbalte možnost **Visual C#** nebo **Visual Basic** a pak vyberte možnost **desktopová plocha systému Windows**.

3. V prostředním podokně vyberte typ projektu **aplikace model Windows Forms** .

4. Pojmenujte projekt **ConcurrencyWalkthrough** a klikněte na **tlačítko OK**.

     Projekt **ConcurrencyWalkthrough** je vytvořen a přidán do **Průzkumník řešení** a otevře se nový formulář v návrháři.

## <a name="create-the-northwind-dataset"></a>Vytvoření datové sady Northwind

Dále vytvořte datovou sadu s názvem **NorthwindDataSet**:

1. V nabídce **data** klikněte na tlačítko **Přidat nový zdroj dat**.

   Otevře se Průvodce konfigurací zdroje dat.

2. Na obrazovce **Vybrat typ zdroje dat** vyberte **databáze**.

   ![Průvodce konfigurací zdroje dat v aplikaci Visual Studio](media/data-source-configuration-wizard.png)

3. Vyberte připojení k ukázkové databázi Northwind ze seznamu dostupných připojení. Pokud připojení není v seznamu připojení k dispozici, vyberte **nové připojení**.

    > [!NOTE]
    > Pokud se připojujete k místnímu databázovému souboru, po zobrazení výzvy vyberte možnost **ne** , pokud chcete soubor přidat do projektu.

4. Na obrazovce **Uložit připojovací řetězec do konfiguračního souboru aplikace** vyberte **Další**.

5. Rozbalte uzel **tabulky** a vyberte tabulku **zákazníci** . Výchozí název pro datovou sadu by měl být **NorthwindDataSet**.

6. Vyberte **Dokončit** a přidejte datovou sadu do projektu.

## <a name="create-a-data-bound-datagridview-control"></a>Vytvoření ovládacího prvku DataGridView vázaného na data

V této části vytvoříte <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> přetažením položky **Customers (zákazníci** ) z okna **zdroje dat** do formuláře Windows.

1. Chcete-li otevřít okno **zdroje dat** , v nabídce **data** vyberte možnost **Zobrazit zdroje dat**.

2. V okně **zdroje dat** rozbalte uzel **NorthwindDataSet** a pak vyberte tabulku **zákazníci** .

3. Vyberte šipku dolů v uzlu tabulka a pak v rozevíracím seznamu vyberte **ovládací prvek DataGridView** .

4. Přetáhněte tabulku do prázdné oblasti formuláře.

     <xref:System.Windows.Forms.DataGridView>Ovládací prvek s názvem **customersDataGridView** a <xref:System.Windows.Forms.BindingNavigator> pojmenovaný **CustomersBindingNavigator** se přidá do formuláře vázaného na <xref:System.Windows.Forms.BindingSource> . To je zase vázané na tabulku Customers v NorthwindDataSet.

## <a name="test-the-form"></a>Testování formuláře

Nyní můžete testovat formulář, abyste se ujistili, že se chová podle očekávání do tohoto bodu:

1. Pro spuštění aplikace vyberte **F5** .

     Formulář se zobrazí s <xref:System.Windows.Forms.DataGridView> ovládacím prvkem, který je vyplněn daty z tabulky Customers.

2. V nabídce **Ladit** vyberte **Zastavit ladění**.

## <a name="handle-concurrency-errors"></a>Zpracování chyb souběžnosti

Způsob zpracování chyb závisí na konkrétním obchodním pravidla, která řídí vaši aplikaci. V tomto návodu použijeme následující strategii jako příklad, jak zpracovat chybu souběžnosti.

Aplikace prezentuje uživateli tři verze záznamu:

- Aktuální záznam v databázi

- Původní záznam načtený do datové sady

- Navrhované změny v datové sadě

Uživatel pak může přepsat databázi pomocí navržené verze, nebo aktualizaci zrušit a obnovit datovou sadu o nové hodnoty z databáze.

### <a name="to-enable-the-handling-of-concurrency-errors"></a>Povolení zpracování chyb souběžnosti

1. Vytvořte vlastní obslužnou rutinu chyb.

2. Umožňuje zobrazit volby pro uživatele.

3. Zpracujte reakci uživatele.

4. Znovu odešlete aktualizaci nebo obnovte data v datové sadě.

### <a name="add-code-to-handle-the-concurrency-exception"></a>Přidat kód pro zpracování výjimky souběžnosti

Při pokusu o provedení aktualizace a vyvolání výjimky je obecně vhodné provést něco s informacemi, které jsou poskytnuty vyvolanou výjimkou. V této části přidáte kód, který se pokusí aktualizovat databázi. Také můžete zpracovat všechny <xref:System.Data.DBConcurrencyException> , které mohou být vyvolány, a také všechny další výjimky.

> [!NOTE]
> `CreateMessage`Metody a `ProcessDialogResults` jsou přidány později v tomto návodu.

1. Do metody přidejte následující kód `Form1_Load` :

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet1":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet1":::

2. Nahraďte `CustomersBindingNavigatorSaveItem_Click` metodu pro volání `UpdateDatabase` metody, aby vypadala takto:

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet2":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet2":::

### <a name="display-choices-to-the-user"></a>Zobrazit možnosti pro uživatele

Kód, který jste právě napsal, volá `CreateMessage` proceduru, která uživateli zobrazí informace o chybě. V tomto návodu použijete okno se zprávou k zobrazení různých verzí záznamu pro uživatele. To uživateli umožňuje zvolit, jestli se má záznam přepsat, nebo zrušit úpravy. Jakmile uživatel vybere možnost (klikne na tlačítko) v okně se zprávou, odpověď je předána `ProcessDialogResult` metodě.

Vytvořte zprávu přidáním následujícího kódu do **editoru kódu**. Zadejte tento kód pod `UpdateDatabase` metodu:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet4":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet4":::

### <a name="process-the-users-response"></a>Zpracovat reakci uživatele

Také potřebujete kód pro zpracování reakce uživatele na okno se zprávou. Možnosti jsou buď k přepsání aktuálního záznamu v databázi navrhovanou změnou, nebo k opuštění místních změn a aktualizaci datové tabulky záznamem, který je aktuálně v databázi. Pokud uživatel zvolí **Ano**, je <xref:System.Data.DataTable.Merge%2A> metoda volána s argumentem *PreserveChanges* nastaveným na **hodnotu true**. Tím dojde k úspěšnému pokusu o aktualizaci, protože původní verze záznamu nyní odpovídá záznamu v databázi.

Pod kód, který byl přidán v předchozí části, přidejte následující kód:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet3":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet3":::

## <a name="test-the-form-behavior"></a>Testování chování formuláře

Nyní můžete testovat formulář, abyste se ujistili, že se chová podle očekávání. Chcete-li simulovat porušení souběžnosti, změňte data v databázi po vyplnění NorthwindDataSet.

1. Pro spuštění aplikace vyberte **F5** .

2. Po zobrazení formuláře ponechte spuštěný a přepněte se do integrovaného vývojového prostředí (IDE) sady Visual Studio.

3. V nabídce **zobrazení** vyberte možnost **Průzkumník serveru**.

4. V **Průzkumník serveru** rozbalte připojení, které aplikace používá, a potom rozbalte uzel **tabulky** .

5. Klikněte pravým tlačítkem myši na tabulku **Customers** a potom vyberte možnost **Zobrazit data tabulky**.

6. V prvním záznamu (**ALFKI**) změňte **kontakt** na **Marie Anders2**.

    > [!NOTE]
    > Změnu potvrďte tak, že přejdete na jiný řádek.

7. Přepněte do běžícího formuláře ConcurrencyWalkthrough.

8. V prvním záznamu ve formuláři (**ALFKI**) změňte **kontakt** na **Marie Anders1**.

9. Vyberte tlačítko **Uložit**.

     Je vyvolána chyba souběžnosti a zobrazí se okno se zprávou.

   Když vyberete možnost **ne** , aktualizace se aktualizuje a aktualizuje datovou sadu hodnotami, které jsou aktuálně v databázi. Výběrem možnosti **Ano** zapíšete navrhovanou hodnotu do databáze.

## <a name="see-also"></a>Viz také

- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)
