---
title: Vytvoření uživatelského ovládacího prvku Windows Forms pomocí vytváření datových vazeb
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7de5cbfe7de8919143cd30517c18f9e5ad6ba598
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305244"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje komplexní datovou vazbu

Při zobrazení dat ve formulářích v aplikacích Windows, můžete vybrat z existujících ovládacích prvků **nástrojů**, nebo můžete vytvořit vlastní ovládací prvky, pokud vaše aplikace vyžaduje funkce, které nejsou k dispozici ve standardní ovládací prvky. Tento návod ukazuje, jak vytvořit ovládací prvek, který implementuje <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Ovládací prvky, které implementují <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> obsahovat `DataSource` a `DataMember` vlastnost, která může být vázaný na data. Tyto ovládací prvky jsou podobné <xref:System.Windows.Forms.DataGridView> nebo <xref:System.Windows.Forms.ListBox>.

Další informace o vytváření ovládacího prvku, naleznete v tématu [řídí vývoj Windows Forms v době návrhu](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Při vytváření ovládacích prvků pro použití ve scénářích datové vazby, budete muset implementovat jedno z následujících atributů datové vazby:

|Použití atributu vázání dat|
| - |
|Implementace <xref:System.ComponentModel.DefaultBindingPropertyAttribute> na jednoduché ovládací prvky, jako je <xref:System.Windows.Forms.TextBox>, který zobrazí jeden sloupec (nebo vlastnost) dat. Další informace najdete v tématu [vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje jednoduchou datovou vazbu](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implementace <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> na ovládací prvky, jako je <xref:System.Windows.Forms.DataGridView>, který zobrazí seznamy (nebo tabulky) data. (Tento proces je popsán v této stránce průvodce.)|
|Implementace <xref:System.ComponentModel.LookupBindingPropertiesAttribute> na ovládací prvky, jako je <xref:System.Windows.Forms.ComboBox>, který zobrazí seznamy (nebo tabulky) data, ale také budete muset k dispozici do jednoho sloupce nebo vlastnosti. Další informace najdete v tématu [vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje vazbu vyhledávacích dat](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

Tento návod vytvoří komplexní ovládací prvek, který zobrazuje řádky dat z tabulky. V tomto příkladu `Customers` tabulky z ukázkové databáze Northwind. Komplexní uživatelský ovládací prvek zobrazí tabulku customers v <xref:System.Windows.Forms.DataGridView> v vlastního ovládacího prvku.

V tomto návodu se dozvíte, jak:

- Vytvořte nový **formulářová aplikace Windows**.

- Přidat nový **uživatelský ovládací prvek** do projektu.

- Vizuální návrh uživatelského ovládacího prvku.

- Implementace `ComplexBindingProperty` atribut.

- Vytvoření datové sady [Průvodce konfigurací zdroje dat](../data-tools/media/data-source-configuration-wizard.png).

- Nastavte **zákazníkům** tabulku v [okna zdroje dat](add-new-data-sources.md#data-sources-window) používat nový komplexní ovládací prvek.

- Přidat nový ovládací prvek z jeho přetažením **zdroje dat** okna do **Form1**.

## <a name="prerequisites"></a>Požadavky

Tento návod používá SQL Server Express LocalDB a ukázkové databáze Northwind.

1. Pokud nemáte SQL Server Express LocalDB, nainstalujte ji z [SQL Server Express stránku pro stažení](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program sady Visual Studio**. V **instalační program sady Visual Studio**, jako součást můžete nainstalovat SQL Server Express LocalDB **ukládání a zpracování dat** úlohy, nebo jako jednotlivých komponent.

1. Instalace ukázkové databáze Northwind pomocí následujících kroků:

    1. V sadě Visual Studio, otevřete **Průzkumník objektů systému SQL Server** okna. (Průzkumník objektů systému SQL Server je nainstalován jako součást **ukládání a zpracování dat** úlohy v instalačním programu sady Visual Studio.) Rozbalte **systému SQL Server** uzlu. Klikněte pravým tlačítkem na instanci LocalDB a vyberte **nový dotaz**.

       Otevře se okno editor dotazů.

    1. Kopírovat [Northwind příkazů jazyka Transact-SQL skriptů](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind úplně od začátku a naplní daty.

    1. Vložte skript T-SQL do editoru dotazů a klikněte na tlačítko **Execute** tlačítko.

       Po chvilce dotaz doběhnutí a vytvořit databázi Northwind.

## <a name="create-a-windows-forms-application"></a>Vytvoření aplikace Windows Forms

Prvním krokem je vytvoření **formulářová aplikace Windows**:

1. V sadě Visual Studio na **souboru** nabídce vyberte možnost **nový** > **projektu**.

1. Rozbalte buď **Visual C#** nebo **jazyka Visual Basic** v levém podokně vyberte **Windows Desktop**.

1. V prostředním podokně, vyberte **aplikace Windows Forms** typ projektu.

1. Pojmenujte projekt **ComplexControlWalkthrough**a klikněte na tlačítko **OK**.

    **ComplexControlWalkthrough** projekt je vytvořen a přidán do **Průzkumníka řešení**.

## <a name="add-a-user-control-to-the-project"></a>Přidat uživatelský ovládací prvek do projektu

Protože tento návod vytvoří komplexní data neumožňující vazbu ovládacího prvku z **uživatelský ovládací prvek**, přidejte **uživatelský ovládací prvek** položky do projektu:

1. Z **projektu** nabídce zvolte **přidat uživatelský ovládací prvek**.

1. Typ **ComplexDataGridView** v **název** oblasti a pak klikněte na tlačítko **přidat**.

    **ComplexDataGridView** ovládací prvek je přidán do **Průzkumníka řešení**a otevře v návrháři.

## <a name="design-the-complexdatagridview-control"></a>Návrh ComplexDataGridView ovládacího prvku

Chcete-li přidat <xref:System.Windows.Forms.DataGridView> uživatelského ovládacího prvku, přetáhněte <xref:System.Windows.Forms.DataGridView> z **nástrojů** na návrhové ploše uživatelský ovládací prvek.

## <a name="add-the-required-data-binding-attribute"></a>Přidat požadovaný atribut vázání dat

Pro komplexní ovládací prvky, že vazba dat podpory, můžete implementovat <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>:

1. Přepnout **ComplexDataGridView** ovládacího prvku na zobrazení kódu. (Na **zobrazení** nabídce vyberte možnost **kód**.)

1. Nahraďte kód v `ComplexDataGridView` následujícím kódem:

    [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
    [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]

1. Z **sestavení** nabídce zvolte **sestavit řešení**.

## <a name="create-a-data-source-from-your-database"></a>Vytvoření zdroje dat z databáze

Použití **konfigurace zdroje dat** průvodce k vytvoření zdroje dat na základě `Customers` tabulky v ukázkové databázi Northwind:

1.  Chcete-li otevřít **zdroje dat** okno na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.

2.  V **zdroje dat** okně **přidat nový zdroj dat** spustit **konfigurace zdroje dat** průvodce.

3.  Vyberte **databáze** na **zvolte typ zdroje dat** stránce a potom klikněte na tlačítko **Další**.

4.  Na **vyberte datové připojení** stránka provádění, jednu z následujících akcí:

    - Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

    - Vyberte **nové připojení** ke spuštění **přidat/změnit připojení** dialogové okno.

5.  Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí důvěrných osobních údajů a pak klikněte na tlačítko **Další**.

6.  Na **uložit připojovací řetězec do konfiguračního souboru aplikace** klikněte na **Další**.

7.  Na **zvolte vaše databázové objekty** stránce, rozbalte **tabulky** uzlu.

8.  Vyberte `Customers` tabulku a pak klikněte na tlačítko **Dokončit**.

    **NorthwindDataSet** se přidá do vašeho projektu a `Customers` se zobrazí v tabulce **zdroje dat** okna.

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Nastavit pomocí ovládacího prvku ComplexDataGridView tabulky Zákazníci

V rámci **zdroje dat** okně můžete nastavit ovládacího prvku má být vytvořen před přetažení položek do formuláře:

1. Otevřít **Form1** v návrháři.

1. Rozbalte **zákazníkům** uzlu **zdroje dat** okno.

1. Klikněte na šipku rozevíracího seznamu **zákazníkům** uzel a zvolte **vlastní**.

1. Vyberte **ComplexDataGridView** ze seznamu **přidružené ovládací prvky** v **možnosti přizpůsobení uživatelského rozhraní dat** dialogové okno.

1. Klikněte na šipku rozevíracího seznamu `Customers` tabulce a zvolte **ComplexDataGridView** ze seznamu ovládacích prvků.

## <a name="add-controls-to-the-form"></a>Přidání ovládacích prvků do formuláře

Můžete vytvořit ovládací prvky vázané na data přetažením položek z **zdroje dat** okna do formuláře. Přetáhněte hlavní **zákazníkům** uzlu z **zdroje dat** okna do formuláře. Ověřte, že **ComplexDataGridView** ovládacího prvku se používá k zobrazení dat v tabulce.

## <a name="run-the-application"></a>Spuštění aplikace

Stisknutím klávesy **F5** ke spuštění aplikace.

## <a name="next-steps"></a>Další kroky

V závislosti na požadavcích aplikace existuje několik kroků, které můžete provést po vytvoření ovládacího prvku, který podporuje datové vazby. Některé typické další postup je následující:

- Umístění vlastních ovládacích prvků do knihovny ovládacích prvků, lze je použít v jiných aplikacích.

- Vytváření ovládacích prvků, které podporují scénáře vyhledávání. Další informace najdete v tématu [vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje vazbu vyhledávacích dat](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdrojů dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
- [Windows Forms – ovládací prvky](/dotnet/framework/winforms/controls/index)