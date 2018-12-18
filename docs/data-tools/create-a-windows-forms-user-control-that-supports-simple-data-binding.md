---
title: Vytvoření uživatelského ovládacího prvku, který podporuje jednoduchou datovou vazbu
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 673e510536ab866f3be90da630d3cfa261bb98c6
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305400"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje jednoduchou datovou vazbu

Při zobrazení dat ve formulářích v aplikacích Windows, můžete vybrat z existujících ovládacích prvků **nástrojů**, nebo můžete vytvořit vlastní ovládací prvky, pokud vaše aplikace vyžaduje funkce, které nejsou k dispozici ve standardní ovládací prvky. Tento návod ukazuje, jak vytvořit ovládací prvek, který implementuje <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. Ovládací prvky, které implementují <xref:System.ComponentModel.DefaultBindingPropertyAttribute> může obsahovat jednu vlastnost, která může být vázaný na data. Tyto ovládací prvky jsou podobné <xref:System.Windows.Forms.TextBox> nebo <xref:System.Windows.Forms.CheckBox>.

Další informace o vytváření ovládacího prvku, naleznete v tématu [vývoj prvky Windows Forms v době návrhu](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Při vytváření ovládacích prvků pro použití ve scénářích datové vazby, měli byste implementovat jednu z následujících atributů datové vazby:

|Použití atributu vázání dat|
| - |
|Implementace <xref:System.ComponentModel.DefaultBindingPropertyAttribute> na jednoduché ovládací prvky, jako je <xref:System.Windows.Forms.TextBox>, který zobrazí jeden sloupec (nebo vlastnost) dat. (Tento proces je popsán v této stránce průvodce.)|
|Implementace <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> na ovládací prvky, jako je <xref:System.Windows.Forms.DataGridView>, který zobrazí seznamy (nebo tabulky) data. Další informace najdete v tématu [vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje rozšířené datové vazby](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implementace <xref:System.ComponentModel.LookupBindingPropertiesAttribute> na ovládací prvky, jako je <xref:System.Windows.Forms.ComboBox>, který zobrazí seznamy (nebo tabulky) data, ale také budete muset k dispozici do jednoho sloupce nebo vlastnosti. Další informace najdete v tématu [vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje vazbu vyhledávacích dat](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

Tento návod vytvoří jednoduchý ovládací prvek zobrazující data z jednoho sloupce v tabulce. V tomto příkladu `Phone` sloupec `Customers` tabulky z ukázkové databáze Northwind. Jednoduché uživatelský ovládací prvek zobrazí zákazníků telefonní čísla ve standardním formátu telefonní číslo, pomocí <xref:System.Windows.Forms.MaskedTextBox> a nastavení masky na telefonní číslo.

V tomto návodu se dozvíte, jak:

-   Vytvořte nový **formulářová aplikace Windows**.

-   Přidat nový **uživatelský ovládací prvek** do projektu.

-   Vizuální návrh uživatelského ovládacího prvku.

-   Implementace `DefaultBindingProperty` atribut.

-   Vytvoření datové sady **konfigurace zdroje dat** průvodce.

-   Nastavit **Phone** sloupec **zdroje dat** okna nový ovládací prvek.

-   Vytvořte formulář pro zobrazení dat v ovládacím prvku nové.

## <a name="prerequisites"></a>Požadavky

Tento návod používá SQL Server Express LocalDB a ukázkové databáze Northwind.

1.  Pokud nemáte SQL Server Express LocalDB, nainstalujte ji z [SQL Server Express stránku pro stažení](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program sady Visual Studio**. V **instalační program sady Visual Studio**, jako součást můžete nainstalovat SQL Server Express LocalDB **ukládání a zpracování dat** úlohy, nebo jako jednotlivých komponent.

2.  Instalace ukázkové databáze Northwind pomocí následujících kroků:

    1. V sadě Visual Studio, otevřete **Průzkumník objektů systému SQL Server** okna. (Průzkumník objektů systému SQL Server je nainstalován jako součást **ukládání a zpracování dat** zatížení **instalační program sady Visual Studio**.) Rozbalte **systému SQL Server** uzlu. Klikněte pravým tlačítkem na instanci LocalDB a vyberte **nový dotaz**.

       Otevře se okno editor dotazů.

    2. Kopírovat [Northwind příkazů jazyka Transact-SQL skriptů](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind úplně od začátku a naplní daty.

    3. Vložte skript T-SQL do editoru dotazů a klikněte na tlačítko **Execute** tlačítko.

       Po chvilce dotaz doběhnutí a vytvořit databázi Northwind.

## <a name="create-a-windows-forms-application"></a>Vytvoření aplikace Windows Forms

Prvním krokem je vytvoření **formulářová aplikace Windows**:

1. V sadě Visual Studio na **souboru** nabídce vyberte možnost **nový** > **projektu**.

2. Rozbalte buď **Visual C#** nebo **jazyka Visual Basic** v levém podokně vyberte **Windows Desktop**.

3. V prostředním podokně, vyberte **aplikace Windows Forms** typ projektu.

4. Pojmenujte projekt **SimpleControlWalkthrough**a klikněte na tlačítko **OK**.

     **SimpleControlWalkthrough** projekt je vytvořen a přidán do **Průzkumníka řešení**.

## <a name="add-a-user-control-to-the-project"></a>Přidat uživatelský ovládací prvek do projektu

Tento návod vytvoří jednoduchý data neumožňující vazbu ovládacího prvku z **uživatelský ovládací prvek**. Přidat **uživatelský ovládací prvek** položkou **SimpleControlWalkthrough** projektu:

1.  Z **projektu** nabídce zvolte **přidat uživatelský ovládací prvek**.

2.  Typ **PhoneNumberBox** název oblasti, a klikněte na **přidat**.

     **PhoneNumberBox** ovládací prvek je přidán do **Průzkumníka řešení**a otevře v návrháři.

## <a name="design-the-phonenumberbox-control"></a>Návrh PhoneNumberBox ovládacího prvku

Tento názorný postup rozšiřují existující <xref:System.Windows.Forms.MaskedTextBox> vytvořit **PhoneNumberBox** ovládacího prvku:

1.  Přetáhněte <xref:System.Windows.Forms.MaskedTextBox> z **nástrojů** na návrhové ploše uživatelský ovládací prvek.

2.  Vyberte na inteligentní značku <xref:System.Windows.Forms.MaskedTextBox> jste právě přetáhli a zvolte **nastavena maska**.

3.  Vyberte **telefonní číslo** v **vstupní maska** dialogové okno a klikněte na tlačítko **OK** k nastavení masky.

## <a name="add-the-required-data-binding-attribute"></a>Přidat požadovaný atribut vázání dat

Pro jednoduché ovládací prvky tuto podporu vázání dat, implementujte <xref:System.ComponentModel.DefaultBindingPropertyAttribute>:

1.  Přepnout **PhoneNumberBox** ovládacího prvku na zobrazení kódu. (Na **zobrazení** nabídce zvolte **kód**.)

2.  Nahraďte kód v **PhoneNumberBox** následujícím kódem:

     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]

3.  Z **sestavení** nabídce zvolte **sestavit řešení**.

## <a name="create-a-data-source-from-your-database"></a>Vytvoření zdroje dat z databáze

Tento krok používá **konfigurace zdroje dat** průvodce k vytvoření zdroje dat na základě `Customers` tabulky v ukázkové databázi Northwind. Musíte mít přístup k ukázkové databázi Northwind k vytvoření připojení. Informace o instalaci ukázkové databáze Northwind naleznete v tématu [postupy: Instalace ukázkových databází](../data-tools/installing-database-systems-tools-and-samples.md).

1.  Chcete-li otevřít **zdroje dat** okno na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.

2.  V **zdroje dat** okně **přidat nový zdroj dat** spustit **konfigurace zdroje dat** průvodce.

3.  Na **zvolte typ zdroje dat** stránce **databáze**a potom klikněte na tlačítko **Další**.

4.  Na **vyberte datové připojení** stránce, proveďte jednu z následujících akcí:

    -   Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

    -   Vyberte **nové připojení** ke spuštění **přidat/změnit připojení** dialogové okno.

5.  Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí důvěrných osobních údajů a pak klikněte na tlačítko **Další**.

6.  Na **uložit připojovací řetězec do konfiguračního souboru aplikace** klikněte na **Další**.

7.  Na **zvolte vaše databázové objekty** stránce, rozbalte **tabulky** uzlu.

8.  Vyberte `Customers` tabulku a pak klikněte na tlačítko **Dokončit**.

     **NorthwindDataSet** se přidá do vašeho projektu a `Customers` se zobrazí v tabulce **zdroje dat** okna.

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Nastavte sloupec telefonu, aby pomocí ovládacího prvku PhoneNumberBox

V rámci **zdroje dat** okně můžete nastavit ovládacího prvku má být vytvořen před přetažení položek do formuláře:

1.  Otevřít **Form1** v návrháři.

2.  Rozbalte **zákazníkům** uzlu **zdroje dat** okno.

3.  Klikněte na šipku rozevíracího seznamu **zákazníkům** uzel a zvolte **podrobnosti** ze seznamu ovládacích prvků.

4.  Klikněte na šipku rozevíracího seznamu **Phone** sloupce a zvolte **vlastní**.

5.  Vyberte **PhoneNumberBox** ze seznamu **přidružené ovládací prvky** v **možnosti přizpůsobení uživatelského rozhraní dat** dialogové okno.

6.  Klikněte na šipku rozevíracího seznamu **Phone** sloupce a zvolte **PhoneNumberBox**.

## <a name="add-controls-to-the-form"></a>Přidání ovládacích prvků do formuláře

Můžete vytvořit ovládací prvky vázané na data přetažením položek z **zdroje dat** okna do formuláře.

Chcete-li vytvořit ovládací prvky vázané na data ve formuláři, přetáhněte hlavní **zákazníkům** uzlu z **zdroje dat** okna do formuláře a ověřte, že **PhoneNumberBox** je ovládací prvek slouží k zobrazení dat v **Phone** sloupce.

     Data-bound controls with descriptive labels appear on the form, along with a tool strip (<xref:System.Windows.Forms.BindingNavigator>) for navigating records. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, and <xref:System.Windows.Forms.BindingNavigator> appear in the component tray.

## <a name="run-the-application"></a>Spuštění aplikace

Stisknutím klávesy **F5** ke spuštění aplikace.

## <a name="next-steps"></a>Další kroky

V závislosti na požadavcích aplikace existuje několik kroků, které můžete provést po vytvoření ovládacího prvku, který podporuje datovou vazbu. Některé typické další postup je následující:

-   Umístění vlastních ovládacích prvků do knihovny ovládacích prvků, lze je použít v jiných aplikacích.

-   Vytváření ovládacích prvků, které podporují složitější scénáře datových vazeb. Další informace najdete v tématu [vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje rozšířené datové vazby](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) a [vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje vazbu vyhledávacích dat](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdrojů dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)