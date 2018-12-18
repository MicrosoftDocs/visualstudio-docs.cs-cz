---
title: Zpracování výjimky souběžnosti
ms.date: 09/11/2017
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fef30f836ab27cd7a67d85a04254be0018d5b33e
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388735"
---
# <a name="handle-a-concurrency-exception"></a>Zpracování výjimky souběžnosti

Výjimky souběžnosti (<xref:System.Data.DBConcurrencyException?displayProperty=fullName>) jsou vyvolány, když dva uživatelé pokoušejí změnit na stejná data v databázi ve stejnou dobu. V tomto návodu vytvoříte aplikaci Windows, která ukazuje, jak zachytit <xref:System.Data.DBConcurrencyException>, vyhledejte řádek, který způsobil chybu a další strategie, jak ji zpracovat.

Tento názorný postup vás provede následující postup:

1. Vytvořte nový **formulářová aplikace Windows** projektu.

2. Vytvořte novou datovou sadu založenou na tabulku zákazníků Northwind.

3. Vytvořit formulář s <xref:System.Windows.Forms.DataGridView> zobrazit data.

4. Zadejte datovou sadu s daty z tabulky Customers v databázi Northwind.

5. Použití **zobrazit Data tabulky** funkci **Průzkumníka serveru** přístup k datům zákazníků – tabulky a změňte záznam.

6. Změnit stejného záznamu na jinou hodnotu, aktualizovat datovou sadu a pokusí se zapsat změny do databáze, což vede k chybě souběžnosti vyvolaných.

7. Zachytit chybu, zobrazit různé verze záznamu, které uživateli umožňují určit, zda chcete pokračovat a aktualizaci databáze nebo také aktualizaci zrušit.

## <a name="prerequisites"></a>Požadavky

Tento návod používá SQL Server Express LocalDB a ukázkové databáze Northwind.

1. Pokud nemáte SQL Server Express LocalDB, nainstalujte ji z [SQL Server Express stránku pro stažení](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program sady Visual Studio**. V **instalační program sady Visual Studio**, jako součást můžete nainstalovat SQL Server Express LocalDB **ukládání a zpracování dat** úlohy, nebo jako jednotlivých komponent.

2. Instalace ukázkové databáze Northwind pomocí následujících kroků:

    1. V sadě Visual Studio, otevřete **Průzkumník objektů systému SQL Server** okna. (Průzkumník objektů systému SQL Server je nainstalován jako součást **ukládání a zpracování dat** úlohy v instalačním programu sady Visual Studio.) Rozbalte **systému SQL Server** uzlu. Klikněte pravým tlačítkem na instanci LocalDB a vyberte **nový dotaz**.

       Otevře se okno editor dotazů.

    2. Kopírovat [Northwind příkazů jazyka Transact-SQL skriptů](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind úplně od začátku a naplní daty.

    3. Vložte skript T-SQL do editoru dotazů a klikněte na tlačítko **Execute** tlačítko.

       Po chvilce dotaz doběhnutí a vytvořit databázi Northwind.

## <a name="create-a-new-project"></a>Vytvoření nového projektu

Začněte tím, že vytvoření nové aplikace Windows Forms:

1. V sadě Visual Studio na **souboru** nabídce vyberte možnost **nový** > **projektu**.

2. Rozbalte buď **Visual C#** nebo **jazyka Visual Basic** v levém podokně vyberte **Windows Desktop**.

3. V prostředním podokně, vyberte **aplikace Windows Forms** typ projektu.

4. Pojmenujte projekt **ConcurrencyWalkthrough**a klikněte na tlačítko **OK**.

     **ConcurrencyWalkthrough** projekt je vytvořen a přidán do **Průzkumníka řešení**, a otevře se v Návrháři nový formulář.

## <a name="create-the-northwind-dataset"></a>Vytvořte datovou sadu Northwind

Dále vytvořte datovou sadu s názvem **NorthwindDataSet**:

1. Na **Data** nabídce zvolte **zdroje přidat nová Data**.

   Otevře se Průvodce konfigurací zdroje dat.

2. Na **zvolte typ zdroje dat** obrazovky, vyberte **databáze**.

   ![Průvodce konfigurací zdroje dat v sadě Visual Studio](media/data-source-configuration-wizard.png)

3. Vyberte připojení ze seznamu dostupných připojení k ukázkové databázi Northwind. Pokud připojení není k dispozici v seznamu připojení, vyberte **nové připojení**.

    > [!NOTE]
    > Pokud se připojujete k místní databázový soubor, vyberte **ne** když se zobrazí výzva, pokud byste chtěli přidat soubor do projektu.

4. Na **uložit připojovací řetězec do konfiguračního souboru aplikace** obrazovky, vyberte **Další**.

5. Rozbalte **tabulky** uzel a vyberte **zákazníkům** tabulky. Výchozí název pro tuto datovou sadu by měl být **NorthwindDataSet**.

6. Vyberte **Dokončit** na datovou sadu přidat do projektu.

## <a name="create-a-data-bound-datagridview-control"></a>Vytvoření ovládacího prvku DataGridView vázaný na data

V této části vytvoříte <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> přetažením **zákazníkům** položky **zdroje dat** okna do formuláře Windows.

1. Chcete-li otevřít **zdroje dat** okno na **Data** nabídky, zvolte **zobrazit zdroje dat**.

2. V **zdroje dat** okna, rozbalte **NorthwindDataSet** uzlu a pak vyberte **zákazníkům** tabulky.

3. Vyberte šipku dolů na uzel tabulky a pak vyberte **DataGridView** v rozevíracím seznamu.

4. Přetáhněte tabulku na prázdnou oblast formuláře.

     A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem **CustomersDataGridView**a <xref:System.Windows.Forms.BindingNavigator> s názvem **CustomersBindingNavigator**, jsou přidány do formuláře, který je vázán <xref:System.Windows.Forms.BindingSource>. To je, pak vázán na tabulku Customers v NorthwindDataSet.

## <a name="test-the-form"></a>Testovací formulář

Teď můžete otestovat formulář, abyste měli jistotu, že se chová podle očekávání do této chvíle:

1. Vyberte **F5** ke spuštění aplikace.

     Formulář se zobrazí s <xref:System.Windows.Forms.DataGridView> ovládacím prvkem, který je naplněný daty z tabulky Zákazníci.

2. Na **ladění** nabídce vyberte možnost **Zastavit ladění**.

## <a name="handle-concurrency-errors"></a>Zpracování chyb, které souběžnosti

Způsob zpracování chyb, závisí na konkrétní obchodní pravidla, kterými se řídí vaše aplikace. V tomto návodu používáme jako příklad způsob zpracování došlo k chybě souběžnosti následující strategie.

Aplikace nabídne uživateli tři verze záznamu:

- Aktuální záznam v databázi

- Původní záznam, který je načten do datové sady

- Navrhovaných změn v datové sadě

Uživatel je pak možné přepsat databázi navrhovaných verzí, nebo také aktualizaci zrušit a aktualizovat datovou sadu s novými hodnotami z databáze.

### <a name="to-enable-the-handling-of-concurrency-errors"></a>Povolit zpracování chyb souběžnosti

1. Vytvoření obslužné rutiny vlastních chyb.

2. Zobrazit možnosti pro uživatele.

3. Zpracování odpovědi uživatele.

4. Znovu odeslal aktualizaci nebo obnovit data v datové sadě.

### <a name="add-code-to-handle-the-concurrency-exception"></a>Přidejte kód pro zpracování výjimky souběžnosti

Když se pokusíte provést aktualizace a je vyvolána výjimka, obvykle chcete udělat něco s informacemi, které poskytuje vyvolanou výjimku. V této části přidáte kód, který se pokouší aktualizovat databázi. Můžete také zpracována <xref:System.Data.DBConcurrencyException> , který může být vyvolána, stejně jako všechny ostatní výjimky.

> [!NOTE]
> `CreateMessage` a `ProcessDialogResults` metody jsou přidány později v tomto návodu.

1. Přidejte následující kód níže `Form1_Load` metody:

   [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
   [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]

2. Nahradit `CustomersBindingNavigatorSaveItem_Click` metoda se má volat `UpdateDatabase` metodu tak, aby vypadala takto:

   [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
   [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]

### <a name="display-choices-to-the-user"></a>Zobrazit možnosti pro uživatele

Kód, který jste právě napsal volání `CreateMessage` postupem zobrazíte informace o chybě pro uživatele. V tomto návodu použijete okno se zprávou k zobrazit různé verze záznamu pro uživatele. To umožňuje uživateli zvolit, jestli se má přepsat záznam změny nebo zrušit úpravy. Když uživatel vybere možnost (klikne na tlačítko) v okně se zprávou, je předán odpovědi `ProcessDialogResult` metody.

Vytvoření zprávy přidáním následujícího kódu **Editor kódu**. Tento kód níže zadejte `UpdateDatabase` metody:

[!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
[!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]

### <a name="process-the-users-response"></a>Zpracovat odpověď uživatele

Musíte také kód pro zpracování odpověď uživatele do pole zpráva. Možnostmi jsou buď přepsat aktuální záznam v databázi navrhované změny, nebo zahodit prováděné změny v místní a aktualizovat datovou tabulku s záznam, který je aktuálně v databázi. Pokud uživatel zvolí **Ano**, <xref:System.Data.DataTable.Merge%2A> metoda je volána *preserveChanges* argument nastaven na **true**. To způsobí, že pokus o aktualizace bude úspěšné, protože původní verze záznamu nyní odpovídá záznam v databázi.

Přidejte následující kód za kód, který byl přidán v předchozí části:

[!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
[!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]

## <a name="test-the-form"></a>Testovací formulář

Teď můžete otestovat formulář, abyste měli jistotu, že se chová podle očekávání. Pro simulaci narušení souběžného zpracování, změna dat v databázi po vyplnění NorthwindDataSet.

1. Vyberte **F5** ke spuštění aplikace.

2. Po zobrazení formuláře necháte spuštěné a přejděte do integrovaného vývojového prostředí sady Visual Studio.

3. Na **zobrazení** nabídce zvolte **Průzkumníka serveru**.

4. V **Průzkumníka serveru**, rozbalte připojení, vaše aplikace používá a potom rozbalte **tabulky** uzlu.

5. Klikněte pravým tlačítkem myši **zákazníkům** tabulku a pak vyberte **zobrazit Data tabulky**.

6. V prvním záznamu (**ALFKI**), změňte **ContactName** k **Marie Anders2**.

    > [!NOTE]
    > Přejděte na jiný řádek pro potvrzení změn.

7. Přepnout ConcurrencyWalkthrough spuštěné formuláře.

8. V první záznam ve formuláři (**ALFKI**), změňte **ContactName** k **Marie Anders1**.

9. Vyberte **Uložit** tlačítko.

     Došlo k chybě souběžnosti se vyvolá a zobrazí se okno se zprávou.

   Výběr **ne** zruší aktualizace a aktualizace datové sady s hodnotami, které jsou aktuálně v databázi. Výběr **Ano** navrhovanou hodnotu zapisuje do databáze.

## <a name="see-also"></a>Viz také:

- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)