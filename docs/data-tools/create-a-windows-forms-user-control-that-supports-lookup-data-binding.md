---
title: Pomocí vyhledávacích tabulek v datové vazbě – ovládací prvky Windows Forms | Dokumentace Microsoftu
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 07c9cf40952eabcafe9d1587d3e2ae4aa02de3a0
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305076"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje vazbu vyhledávacích dat

Při zobrazování dat ve Windows Forms, můžete vybrat z existujících ovládacích prvků **nástrojů**, nebo můžete vytvořit vlastní ovládací prvky, pokud vaše aplikace vyžaduje funkce není k dispozici ve standardní ovládací prvky. Tento návod ukazuje, jak vytvořit ovládací prvek, který implementuje <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. Ovládací prvky, které implementují <xref:System.ComponentModel.LookupBindingPropertiesAttribute> může obsahovat tři vlastnosti, které může být vázaný na data. Tyto ovládací prvky jsou podobné <xref:System.Windows.Forms.ComboBox>.

Další informace o vytváření ovládacího prvku, naleznete v tématu [řídí vývoj Windows Forms v době návrhu](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Při vytváření ovládacích prvků pro použití ve scénářích datové vazby, budete muset implementovat jedno z následujících atributů datové vazby:

|Použití atributu vázání dat|
| - |
|Implementace <xref:System.ComponentModel.DefaultBindingPropertyAttribute> na jednoduché ovládací prvky, jako je <xref:System.Windows.Forms.TextBox>, který zobrazí jeden sloupec (nebo vlastnost) dat. Další informace najdete v tématu [vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje jednoduchou datovou vazbu](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implementace <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> na ovládací prvky, jako je <xref:System.Windows.Forms.DataGridView>, který zobrazí seznamy (nebo tabulky) data. Další informace najdete v tématu [vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje rozšířené datové vazby](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implementace <xref:System.ComponentModel.LookupBindingPropertiesAttribute> na ovládací prvky, jako je <xref:System.Windows.Forms.ComboBox>, který zobrazí seznamy (nebo tabulky) data, ale také budete muset k dispozici do jednoho sloupce nebo vlastnosti. (Tento proces je popsán v této stránce průvodce.)|

Tento návod vytvoří ovládací prvek vyhledávání, která vytvoří vazbu na data ze dvou tabulek. V tomto příkladu `Customers` a `Orders` tabulek z ukázkové databáze Northwind. Ovládací prvek vyhledávání je vázán `CustomerID` pole z `Orders` tabulky. Používá tato hodnota k vyhledání `CompanyName` z `Customers` tabulky.

V tomto návodu se dozvíte, jak:

-   Vytvořte nový **formulářová aplikace Windows**.

-   Přidat nový **uživatelský ovládací prvek** do projektu.

-   Vizuální návrh uživatelského ovládacího prvku.

-   Implementace `LookupBindingProperty` atribut.

-   Vytvoření datové sady **konfigurace zdroje dat** průvodce.

-   Nastavit **CustomerID** sloupec **objednávky** tabulku **zdroje dat** okna pro použití nového ovládacího prvku.

-   Vytvořte formulář pro zobrazení dat v ovládacím prvku nové.

## <a name="prerequisites"></a>Požadavky

Tento návod používá SQL Server Express LocalDB a ukázkové databáze Northwind.

1.  Pokud nemáte SQL Server Express LocalDB, nainstalujte ji z [SQL Server Express stránku pro stažení](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program sady Visual Studio**. V **instalační program sady Visual Studio**, jako součást můžete nainstalovat SQL Server Express LocalDB **ukládání a zpracování dat** úlohy, nebo jako jednotlivých komponent.

2.  Instalace ukázkové databáze Northwind pomocí následujících kroků:

    1. V sadě Visual Studio, otevřete **Průzkumník objektů systému SQL Server** okna. (Průzkumník objektů systému SQL Server je nainstalován jako součást **ukládání a zpracování dat** úlohy v instalačním programu sady Visual Studio.) Rozbalte **systému SQL Server** uzlu. Klikněte pravým tlačítkem na instanci LocalDB a vyberte **nový dotaz**.

       Otevře se okno editor dotazů.

    2. Kopírovat [Northwind příkazů jazyka Transact-SQL skriptů](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind úplně od začátku a naplní daty.

    3. Vložte skript T-SQL do editoru dotazů a klikněte na tlačítko **Execute** tlačítko.

       Po chvilce dotaz doběhnutí a vytvořit databázi Northwind.

## <a name="create-a-windows-forms-app-project"></a>Vytvoření projektu aplikace Windows Forms

Prvním krokem je vytvoření **formulářová aplikace Windows** projektu.

1. V sadě Visual Studio na **souboru** nabídce vyberte možnost **nový** > **projektu**.

2. Rozbalte buď **Visual C#** nebo **jazyka Visual Basic** v levém podokně vyberte **Windows Desktop**.

3. V prostředním podokně, vyberte **aplikace Windows Forms** typ projektu.

4. Pojmenujte projekt **LookupControlWalkthrough**a klikněte na tlačítko **OK**.

     **LookupControlWalkthrough** projekt je vytvořen a přidán do **Průzkumníka řešení**.

## <a name="add-a-user-control-to-the-project"></a>Přidat uživatelský ovládací prvek do projektu

Tento návod vytvoří ovládací prvek vyhledávání z **uživatelský ovládací prvek**, proto přidat **uživatelský ovládací prvek** položkou **LookupControlWalkthrough** projektu.

1.  Z **projektu** nabídce vyberte možnost **přidat uživatelský ovládací prvek**.

2.  Typ `LookupBox` v **název** oblasti a pak klikněte na tlačítko **přidat**.

     **LookupBox** ovládací prvek je přidán do **Průzkumníka řešení**a otevře v návrháři.

## <a name="design-the-lookupbox-control"></a>Návrh LookupBox ovládacího prvku

Chcete-li navrhnout LookupBox ovládací prvek, přetáhněte <xref:System.Windows.Forms.ComboBox> z **nástrojů** na návrhové ploše uživatelský ovládací prvek.

## <a name="add-the-required-data-binding-attribute"></a>Přidat požadovaný atribut vázání dat

Pro vyhledávání ovládacích prvků, že vazba dat podpory, můžete implementovat <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.

1.  Přepnout **LookupBox** ovládacího prvku na zobrazení kódu. (Na **zobrazení** nabídce zvolte **kód**.)

2.  Nahraďte kód v `LookupBox` následujícím kódem:

     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]

3.  Z **sestavení** nabídce zvolte **sestavit řešení**.

## <a name="create-a-data-source-from-your-database"></a>Vytvoření zdroje dat z databáze

Tento krok vytváří zdroj dat pomocí **konfigurace zdroje dat** průvodce, na základě `Customers` a `Orders` tabulky v ukázkové databázi Northwind.

1.  Chcete-li otevřít **zdroje dat** okno na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.

2.  V **zdroje dat** okně **přidat nový zdroj dat** spustit **konfigurace zdroje dat** průvodce.

3.  Vyberte **databáze** na **zvolte typ zdroje dat** stránce a potom klikněte na tlačítko **Další**.

4.  Na **vyberte datové připojení** stránka provádění, jednu z následujících akcí:

    -   Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

    -   Vyberte **nové připojení** ke spuštění **přidat/změnit připojení** dialogové okno.

5.  Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí důvěrných osobních údajů a pak klikněte na tlačítko **Další**.

6.  Na **uložit připojovací řetězec do konfiguračního souboru aplikace** klikněte na **Další**.

7.  Na **zvolte vaše databázové objekty** stránce, rozbalte **tabulky** uzlu.

8.  Vyberte `Customers` a `Orders` tabulky a pak klikněte na tlačítko **Dokončit**.

     **NorthwindDataSet** se přidá do vašeho projektu a `Customers` a `Orders` tabulky se zobrazí v **zdroje dat** okna.

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Nastavte sloupci CustomerID v tabulce objednávky pomocí ovládacího prvku LookupBox

V rámci **zdroje dat** okně můžete nastavit ovládacího prvku má být vytvořen před přetažení položek do formuláře.

1.  Otevřít **Form1** v návrháři.

2.  Rozbalte **zákazníkům** uzlu **zdroje dat** okno.

3.  Rozbalte **objednávky** uzel (v **zákazníkům** pod uzlem **Fax** sloupec).

4.  Klikněte na šipku rozevíracího seznamu **objednávky** uzel a zvolte **podrobnosti** ze seznamu ovládacích prvků.

5.  Klikněte na šipku rozevíracího seznamu **CustomerID** sloupce (v **objednávky** uzlu) a zvolte **vlastní**.

6.  Vyberte **LookupBox** ze seznamu **přidružené ovládací prvky** v **možnosti přizpůsobení uživatelského rozhraní dat** dialogové okno.

7.  Klikněte na tlačítko **OK**.

8.  Klikněte na šipku rozevíracího seznamu **CustomerID** sloupce a zvolte **LookupBox**.

## <a name="add-controls-to-the-form"></a>Přidání ovládacích prvků do formuláře

Můžete vytvořit ovládací prvky vázané na data přetažením položek z **zdroje dat** okna do **Form1**.

Chcete-li vytvořit ovládací prvky vázané na data ve formuláři Windows, přetáhněte **objednávky** uzlu z **zdroje dat** okna do formuláře Windows a ověřte, zda **LookupBox** je ovládací prvek slouží k zobrazení dat v `CustomerID` sloupce.

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Vytvoření vazby ovládacího prvku k vyhledání CompanyName z tabulky Zákazníci

Nastavení vazby vyhledávání, vyberte hlavní **zákazníkům** uzlu v **zdroje dat** okna a přetáhněte ji do pole se seznamem v poli **CustomerIDLookupBox** na **Form1**.

Tím se nastaví datové vazby k zobrazení `CompanyName` z `Customers` tabulky, a přitom `CustomerID` hodnotu `Orders` tabulky.

## <a name="run-the-application"></a>Spuštění aplikace

-   Stisknutím klávesy **F5** ke spuštění aplikace.

-   Procházet některé záznamy a ověřte, že `CompanyName` se zobrazí v `LookupBox` ovládacího prvku.

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)