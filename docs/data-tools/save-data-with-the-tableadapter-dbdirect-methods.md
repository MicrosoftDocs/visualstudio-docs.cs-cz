---
title: Ukládání dat pomocí metod TableAdapter DBDirect
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ef1860274c9234774b8af42525a0215d9468a858
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304568"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Ukládání dat pomocí metod TableAdapter DBDirect

Tento názorný postup obsahuje podrobné pokyny ke spouštění příkazů SQL přímo proti databázi s použitím dbdirect – metody třídy TableAdapter. Dbdirect – metody třídy TableAdapter poskytovat jemné úroveň kontroly nad aktualizace databáze. Můžete je použít ke spuštění konkrétních příkazů jazyka SQL a uložených procedur voláním jednotlivých `Insert`, `Update`, a `Delete` metody podle potřeb vaší aplikace (na rozdíl od přetížené `Update` metodu, která provádí aktualizace Příkazů INSERT a DELETE vše v jednom volání).

V tomto návodu se dozvíte, jak:

-   Vytvořte nový **formulářová aplikace Windows**.

-   Vytvoření a konfigurace datové sady [Průvodce konfigurací zdroje dat](../data-tools/media/data-source-configuration-wizard.png).

-   Vyberte ovládací prvek, který má být vytvořen ve formuláři při přetažení položek z **zdroje dat** okna. Další informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Vytvoření formuláře vázané na data přetažením položek z **zdroje dat** okna do formuláře.

-   Přidejte metody k přímému přístupu k databázi a provést vložení, aktualizace a odstranění.

## <a name="prerequisites"></a>Požadavky

Tento návod používá SQL Server Express LocalDB a ukázkové databáze Northwind.

1. Pokud nemáte SQL Server Express LocalDB, nainstalujte ji z [SQL Server Express stránku pro stažení](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program sady Visual Studio**. V **instalační program sady Visual Studio**, jako součást můžete nainstalovat SQL Server Express LocalDB **ukládání a zpracování dat** úlohy, nebo jako jednotlivých komponent.

2. Instalace ukázkové databáze Northwind pomocí následujících kroků:

    1. V sadě Visual Studio, otevřete **Průzkumník objektů systému SQL Server** okna. (Průzkumník objektů systému SQL Server je nainstalován jako součást **ukládání a zpracování dat** úlohy v instalačním programu sady Visual Studio.) Rozbalte **systému SQL Server** uzlu. Klikněte pravým tlačítkem na instanci LocalDB a vyberte **nový dotaz**.

       Otevře se okno editor dotazů.

    2. Kopírovat [Northwind příkazů jazyka Transact-SQL skriptů](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind úplně od začátku a naplní daty.

    3. Vložte skript T-SQL do editoru dotazů a klikněte na tlačítko **Execute** tlačítko.

       Po chvilce dotaz doběhnutí a vytvořit databázi Northwind.

## <a name="create-a-windows-forms-application"></a>Vytvoření aplikace Windows Forms

Prvním krokem je vytvoření **formulářová aplikace Windows**.

1. V sadě Visual Studio na **souboru** nabídce vyberte možnost **nový** > **projektu**.

2. Rozbalte buď **Visual C#** nebo **jazyka Visual Basic** v levém podokně vyberte **Windows Desktop**.

3. V prostředním podokně, vyberte **aplikace Windows Forms** typ projektu.

4. Pojmenujte projekt **TableAdapterDbDirectMethodsWalkthrough**a klikněte na tlačítko **OK**.

     **TableAdapterDbDirectMethodsWalkthrough** projekt je vytvořen a přidán do **Průzkumníka řešení**.

## <a name="create-a-data-source-from-your-database"></a>Vytvoření zdroje dat z databáze

Tento krok používá **Průvodce konfigurací zdroje dat** vytvořit zdroj dat na základě `Region` tabulky v ukázkové databázi Northwind. Musíte mít přístup k ukázkové databázi Northwind k vytvoření připojení. Informace o nastavení ukázkové databáze Northwind naleznete v tématu [postupy: Instalace ukázkových databází](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat

1. Na **Data** nabídce vyberte možnost **zobrazit zdroje dat**.

   **Zdroje dat** otevře se okno.

2. V **zdroje dat** okně **přidat nový zdroj dat** spustit **Průvodce konfigurací zdroje dat**.

3. Na **zvolte typ zdroje dat** obrazovky, vyberte **databáze**a pak vyberte **Další**.

4. Na **vyberte datové připojení** obrazovky, proveďte jednu z následujících akcí:

    -   Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

         -nebo-

    -   Vyberte **nové připojení** ke spuštění **přidat/změnit připojení** dialogové okno.

5. Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí důvěrných osobních údajů a pak vyberte **Další**.

6. Na **uložit připojovací řetězec do konfiguračního souboru aplikace** obrazovky, vyberte **Další**.

7. Na **zvolte vaše databázové objekty** obrazovky, rozbalte **tabulky** uzlu.

8. Vyberte `Region` tabulku a pak vyberte **Dokončit**.

     **NorthwindDataSet** se přidá do vašeho projektu a `Region` se zobrazí v tabulce **zdroje dat** okna.

## <a name="add-controls-to-the-form-to-display-the-data"></a>Přidání ovládacích prvků do formuláře a zobrazení dat

Vytvoření ovládacích prvků vázaných na data přetažením položek z **zdroje dat** okna do formuláře.

Chcete-li vytvořit ovládací prvky data vázaná na formuláři Windows, přetáhněte hlavní **oblasti** uzlu z **zdroje dat** okna do formuláře.

A <xref:System.Windows.Forms.DataGridView> ovládacího prvku a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů se zobrazí ve formuláři. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `RegionTableAdapter`, <xref:System.Windows.Forms.BindingSource>, a <xref:System.Windows.Forms.BindingNavigator> zobrazují v panelu komponent.

### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Přidat tlačítka, který bude volat jednotlivé třídy TableAdapter dbdirect – metody

1. Přetáhněte tři <xref:System.Windows.Forms.Button> ovládacích prvků z **nástrojů** do **Form1** (dole **RegionDataGridView**).

2. Nastavte následující **název** a **Text** vlastnosti na každé tlačítko.

    |Název|Text|
    |----------|----------|
    |`InsertButton`|**Vložit**|
    |`UpdateButton`|**Aktualizace**|
    |`DeleteButton`|**Delete**|

### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Přidat kód pro vkládání nových záznamů do databáze

1. Vyberte **InsertButton** vytvořit obslužnou rutinu události pro událost click a otevřete formulář v editoru kódu.

2. Nahradit `InsertButton_Click` obslužné rutiny události s následujícím kódem:

     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]

### <a name="to-add-code-to-update-records-in-the-database"></a>Chcete-li přidat kód k aktualizaci záznamů v databázi

1. Dvakrát klikněte **UpdateButton** vytvořit obslužnou rutinu události pro událost click a otevřete formulář v editoru kódu.

2. Nahradit `UpdateButton_Click` obslužné rutiny události s následujícím kódem:

     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]

### <a name="to-add-code-to-delete-records-from-the-database"></a>Chcete-li přidat kód k odstranění záznamů z databáze

1. Vyberte **DeleteButton** vytvořit obslužnou rutinu události pro událost click a otevřete formulář v editoru kódu.

2. Nahradit `DeleteButton_Click` obslužné rutiny události s následujícím kódem:

     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]

## <a name="run-the-application"></a>Spuštění aplikace

-   Vyberte **F5** ke spuštění aplikace.

-   Vyberte **vložit** tlačítko a ověřte, že nový záznam se zobrazí v mřížce.

-   Vyberte **aktualizace** tlačítko a ověřte, že záznam se aktualizuje v mřížce.

-   Vyberte **odstranit** tlačítko a ověřte, že záznam se odebere z mřížky.

## <a name="next-steps"></a>Další kroky

V závislosti na požadavcích aplikace existuje několik kroků, které můžete chtít provést po vytvoření formuláře vázané na data. Mezi vylepšení, která je možné pro tento návod provést, patří:

-   Přidání vyhledávací funkce do formuláře.

-   Přidání další tabulky do datové sady výběrem **konfigurace datové sady pomocí průvodce** v rámci **zdroje dat** okna. Můžete přidat ovládací prvky zobrazující související data přetažením související uzly na formuláři. Další informace najdete v tématu [vztahy v datových sadách](relationships-in-datasets.md).

## <a name="see-also"></a>Viz také:

- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)