---
title: Vytvoření uživatelského ovládacího prvku model Windows Forms s datovou vazbou
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 97d9e64a0fcabb207d4606d4819f6afcb61b1043
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75586845"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Vytvoření uživatelského ovládacího prvku modelu Windows Forms, který podporuje složitou datovou vazbu

Při zobrazování dat ve formulářích v aplikacích systému Windows můžete zvolit existující ovládací prvky ze sady **nástrojů**. Nebo můžete vytvořit vlastní ovládací prvky, pokud vaše aplikace vyžaduje funkce, které nejsou dostupné ve standardních ovládacích prvcích. Tento návod ukazuje, jak vytvořit ovládací prvek, který implementuje rozhraní <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> . Ovládací prvky, které implementují <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> `DataSource` `DataMember` vlastnost a, které mohou být vázány na data. Tyto ovládací prvky jsou podobné <xref:System.Windows.Forms.DataGridView> nebo <xref:System.Windows.Forms.ListBox> .

Další informace o vytváření ovládacích prvků naleznete v tématu [vývoj model Windows Formsch ovládacích prvků v době návrhu](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Při vytváření ovládacích prvků pro použití ve scénářích vázání dat je nutné implementovat jeden z následujících atributů datové vazby:

|Použití atributu datové vazby|
| - |
|Implementujte <xref:System.ComponentModel.DefaultBindingPropertyAttribute> na jednoduchých ovládacích prvcích, jako je <xref:System.Windows.Forms.TextBox> ,, které zobrazují jeden sloupec (nebo vlastnost) dat. Další informace najdete v tématu [vytvoření model Windows Forms uživatelského ovládacího prvku, který podporuje jednoduchou datovou vazbu](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implementujte <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> ovládací prvky, jako <xref:System.Windows.Forms.DataGridView> jsou, které zobrazují seznamy (nebo tabulky) dat. (Tento postup je popsaný v této stránce s návodem.)|
|Implementujte <xref:System.ComponentModel.LookupBindingPropertiesAttribute> ovládací prvky, jako <xref:System.Windows.Forms.ComboBox> jsou, které zobrazují seznamy (nebo tabulky) dat, ale také musí obsahovat jeden sloupec nebo vlastnost. Další informace najdete v tématu [vytvoření model Windows Forms uživatelského ovládacího prvku, který podporuje vazbu vyhledávacích dat](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

Tento návod vytvoří komplexní ovládací prvek, který zobrazí řádky dat z tabulky. V tomto příkladu se používá `Customers` Tabulka z ukázkové databáze Northwind. Komplexní uživatelský ovládací prvek zobrazí tabulku Customers (zákazníci) ve <xref:System.Windows.Forms.DataGridView> vlastním ovládacím prvku.

V tomto návodu se dozvíte, jak:

- Přidejte do projektu nový **uživatelský ovládací prvek** .

- Vizuálně Navrhněte uživatelský ovládací prvek.

- Implementujte `ComplexBindingProperty` atribut.

- Vytvořte datovou sadu pomocí [Průvodce konfigurací zdroje dat](../data-tools/media/data-source-configuration-wizard.png).

- Nastavte tabulku **Customers** v [okně zdroje dat](add-new-data-sources.md#data-sources-window) na použití nového složitého ovládacího prvku.

- Přidejte nový ovládací prvek přetažením z okna **zdroje dat** do formuláře **Form1**.

## <a name="prerequisites"></a>Požadavky

Tento návod používá SQL Server Express LocalDB a ukázkovou databázi Northwind.

1. Pokud nemáte SQL Server Express LocalDB, nainstalujte ji buď ze [stránky pro stažení SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program pro Visual Studio**. V **instalační program pro Visual Studio**můžete nainstalovat SQL Server Express LocalDB jako součást úlohy **ukládání a zpracování dat** nebo jako jednotlivé komponenty.

1. Nainstalujte ukázkovou databázi Northwind pomocí následujících kroků:

    1. V aplikaci Visual Studio otevřete okno **Průzkumník objektů systému SQL Server** . (Průzkumník objektů systému SQL Server je nainstalován v rámci úlohy **úložiště dat a zpracování** v instalační program pro Visual Studio.) Rozbalte uzel **SQL Server** . Klikněte pravým tlačítkem na instanci LocalDB a vyberte **Nový dotaz**.

       Otevře se okno editoru dotazů.

    1. Zkopírujte [skript Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind od začátku a naplní ji daty.

    1. Vložte skript T-SQL do editoru dotazů a pak klikněte na tlačítko **Spustit** .

       Po krátké době se dotaz dokončí a vytvoří se databáze Northwind.

## <a name="create-a-windows-forms-app-project"></a>Vytvoření projektu aplikace model Windows Forms

Prvním krokem je vytvoření projektu **aplikace model Windows Forms** pro C# nebo Visual Basic. Pojmenujte projekt **ComplexControlWalkthrough**.

## <a name="add-a-user-control-to-the-project"></a>Přidat uživatelský ovládací prvek do projektu

Vzhledem k tomu, že tento návod vytvoří komplexní ovládací prvek s datovou vazbou z **uživatelského ovládacího prvku**, přidejte do projektu položku **uživatelského ovládacího prvku** :

1. V nabídce **projekt** vyberte možnost **Přidat uživatelský ovládací prvek**.

1. Do oblasti **název** zadejte **ComplexDataGridView** a pak klikněte na **Přidat**.

    Ovládací prvek **ComplexDataGridView** je přidán do **Průzkumník řešení**a otevře se v návrháři.

## <a name="design-the-complexdatagridview-control"></a>Návrh ovládacího prvku ComplexDataGridView

Chcete-li přidat <xref:System.Windows.Forms.DataGridView> do uživatelského ovládacího prvku, přetáhněte <xref:System.Windows.Forms.DataGridView> z **panelu nástrojů** na návrhovou plochu uživatelského ovládacího prvku.

## <a name="add-the-required-data-binding-attribute"></a>Přidání požadovaného atributu datové vazby

Pro komplexní ovládací prvky, které podporují datovou vazbu, můžete implementovat <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> :

1. Přepněte ovládací prvek **ComplexDataGridView** do zobrazení kódu. (V nabídce **zobrazení** vyberte položku **kód**.)

1. Kód nahraďte následujícím kódem `ComplexDataGridView` :

    [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
    [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]

1. V nabídce **sestavení** klikněte na příkaz **Sestavit řešení**.

## <a name="create-a-data-source-from-your-database"></a>Vytvoření zdroje dat z databáze

Pomocí průvodce **konfigurací zdroje dat** vytvořte zdroj dat založený na `Customers` tabulce v ukázkové databázi Northwind:

1. Chcete-li otevřít okno **zdroje dat** , klikněte v nabídce **data** na možnost **Zobrazit zdroje dat**.

2. V okně **zdroje dat** vyberte možnost **Přidat nový zdroj dat** a spusťte průvodce **konfigurací zdroje dat** .

3. Vyberte možnost **databáze** na stránce **Vybrat typ zdroje dat** a poté klikněte na tlačítko **Další**.

4. Na stránce **Vyberte datové připojení** proveďte jednu z následujících akcí:

   - Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

   - Vyberte **nové připojení** , aby se spustilo dialogové okno **Přidat nebo upravit připojení** .

5. Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí citlivých dat a potom klikněte na tlačítko **Další**.

6. Na stránce **Uložit připojovací řetězec do konfiguračního souboru aplikace** klikněte na tlačítko **Další**.

7. Na stránce **zvolit databázové objekty** rozbalte uzel **tabulky** .

8. Vyberte `Customers` tabulku a pak klikněte na **Dokončit**.

   **NorthwindDataSet** je přidán do projektu a `Customers` tabulka se zobrazí v okně **zdroje dat** .

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Nastavení tabulky Customers pro použití ovládacího prvku ComplexDataGridView

V okně **zdroje dat** můžete nastavit, aby byl ovládací prvek vytvořen před přetažením položek do formuláře:

1. Otevřete **Form1** v návrháři.

1. Rozbalte uzel **zákazníci** v okně **zdroje dat** .

1. Klikněte na šipku rozevíracího seznamu v uzlu **Customers (zákazníci** ) a vyberte **přizpůsobit**.

1. Vyberte **ComplexDataGridView** ze seznamu **přidružených ovládacích prvků** v dialogovém okně **Možnosti přizpůsobení uživatelského rozhraní dat** .

1. Klikněte na šipku rozevíracího `Customers` seznamu v tabulce a v seznamu ovládacích prvků vyberte možnost **ComplexDataGridView** .

## <a name="add-controls-to-the-form"></a>Přidat ovládací prvky do formuláře

Můžete vytvořit ovládací prvky vázané na data přetažením položek z okna **zdroje dat** do formuláře. Přetáhněte hlavní uzel **Customers** z okna **zdroje dat** do formuláře. Ověřte, zda se k zobrazení dat tabulky používá ovládací prvek **ComplexDataGridView** .

## <a name="run-the-application"></a>Spuštění aplikace

Stisknutím klávesy **F5** spusťte aplikaci.

## <a name="next-steps"></a>Další kroky

V závislosti na požadavcích vaší aplikace existuje několik kroků, které můžete chtít provést po vytvoření ovládacího prvku, který podporuje datovou vazbu. Mezi typické další kroky patří:

- Vlastní ovládací prvky můžete umístit do knihovny ovládacích prvků, abyste je mohli znovu použít v jiných aplikacích.

- Vytváření ovládacích prvků, které podporují scénáře vyhledávání. Další informace najdete v tématu [vytvoření model Windows Forms uživatelského ovládacího prvku, který podporuje vazbu vyhledávacích dat](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Viz také

- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdrojů dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
- [Ovládací prvky model Windows Forms](/dotnet/framework/winforms/controls/index)
