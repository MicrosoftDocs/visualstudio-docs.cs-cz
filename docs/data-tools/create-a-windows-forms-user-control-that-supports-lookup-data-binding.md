---
title: Použití vyhledávacích tabulek v datové vazbě – model Windows Forms
description: Naučte se vytvořit uživatelský ovládací prvek model Windows Forms, který podporuje vazbu vyhledávacích dat, pomocí třídy LookupBindingPropertiesAttribute v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 796fc389a7cd7d0c587f955792a96d0f2f07a20c
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215965"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Vytvoření uživatelského ovládacího prvku modelu Windows Forms, který podporuje vazbu vyhledávacích dat

Při zobrazování dat v model Windows Forms můžete zvolit existující ovládací prvky z **panelu nástrojů**, nebo můžete vytvořit vlastní ovládací prvky, pokud vaše aplikace vyžaduje funkce, které nejsou dostupné ve standardních ovládacích prvcích. Tento návod ukazuje, jak vytvořit ovládací prvek, který implementuje rozhraní <xref:System.ComponentModel.LookupBindingPropertiesAttribute> . Ovládací prvky, které implementují, <xref:System.ComponentModel.LookupBindingPropertiesAttribute> mohou obsahovat tři vlastnosti, které mohou být vázány na data. Tyto ovládací prvky jsou podobné <xref:System.Windows.Forms.ComboBox> .

Další informace o vytváření ovládacích prvků naleznete v tématu [vývoj model Windows Formsch ovládacích prvků v době návrhu](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Při vytváření ovládacích prvků pro použití ve scénářích vázání dat je nutné implementovat jeden z následujících atributů datové vazby:

|Použití atributu datové vazby|
| - |
|Implementujte <xref:System.ComponentModel.DefaultBindingPropertyAttribute> na jednoduchých ovládacích prvcích, jako je <xref:System.Windows.Forms.TextBox> ,, které zobrazují jeden sloupec (nebo vlastnost) dat. Další informace najdete v tématu [vytvoření model Windows Forms uživatelského ovládacího prvku, který podporuje jednoduchou datovou vazbu](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implementujte <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> ovládací prvky, jako <xref:System.Windows.Forms.DataGridView> jsou, které zobrazují seznamy (nebo tabulky) dat. Další informace najdete v tématu [vytvoření model Windows Forms uživatelského ovládacího prvku, který podporuje složitou datovou vazbu](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implementujte <xref:System.ComponentModel.LookupBindingPropertiesAttribute> ovládací prvky, jako <xref:System.Windows.Forms.ComboBox> jsou, které zobrazují seznamy (nebo tabulky) dat, ale také musí obsahovat jeden sloupec nebo vlastnost. (Tento postup je popsaný v této stránce s návodem.)|

Tento návod vytvoří ovládací prvek vyhledávání, který se váže k datům ze dvou tabulek. Tento příklad používá `Customers` tabulky a `Orders` z ukázkové databáze Northwind. Ovládací prvek vyhledávání je svázán s `CustomerID` polem z `Orders` tabulky. Tato hodnota se používá k vyhledání tabulky v `CompanyName` `Customers` tabulce.

V tomto návodu se dozvíte, jak:

- Vytvořte novou **model Windows Forms aplikaci**.

- Přidejte do projektu nový **uživatelský ovládací prvek** .

- Vizuálně Navrhněte uživatelský ovládací prvek.

- Implementujte `LookupBindingProperty` atribut.

- Vytvořte datovou sadu pomocí průvodce **konfigurací zdroje dat** .

- Nastavte sloupec **KódZákazníka** v tabulce **Orders** v okně **zdroje dat** na použití nového ovládacího prvku.

- Vytvořte formulář pro zobrazení dat v novém ovládacím prvku.

## <a name="prerequisites"></a>Požadavky

Tento návod používá SQL Server Express LocalDB a ukázkovou databázi Northwind.

1. Pokud nemáte SQL Server Express LocalDB, nainstalujte ji buď ze [stránky pro stažení SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program pro Visual Studio**. V **instalační program pro Visual Studio** můžete nainstalovat SQL Server Express LocalDB jako součást úlohy **ukládání a zpracování dat** nebo jako jednotlivé komponenty.

2. Nainstalujte ukázkovou databázi Northwind pomocí následujících kroků:

    1. V aplikaci Visual Studio otevřete okno **Průzkumník objektů systému SQL Server** . (Průzkumník objektů systému SQL Server je nainstalován v rámci úlohy **úložiště dat a zpracování** v instalační program pro Visual Studio.) Rozbalte uzel **SQL Server** . Klikněte pravým tlačítkem na instanci LocalDB a vyberte **Nový dotaz**.

       Otevře se okno editoru dotazů.

    2. Zkopírujte [skript Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind od začátku a naplní ji daty.

    3. Vložte skript T-SQL do editoru dotazů a pak klikněte na tlačítko **Spustit** .

       Po krátké době se dotaz dokončí a vytvoří se databáze Northwind.

## <a name="create-a-windows-forms-app-project"></a>Vytvoření projektu aplikace model Windows Forms

Prvním krokem je vytvoření projektu **aplikace model Windows Forms** .

1. V aplikaci Visual Studio v nabídce **soubor** vyberte **Nový**  >  **projekt**.

2. V levém podokně rozbalte možnost **Visual C#** nebo **Visual Basic** a pak vyberte možnost **desktopová plocha systému Windows**.

3. V prostředním podokně vyberte typ projektu **aplikace model Windows Forms** .

4. Pojmenujte projekt **LookupControlWalkthrough** a klikněte na **tlačítko OK**.

     Vytvoří se projekt **LookupControlWalkthrough** a přidá se do **Průzkumník řešení**.

## <a name="add-a-user-control-to-the-project"></a>Přidat uživatelský ovládací prvek do projektu

Tento návod vytvoří ovládací prvek vyhledávání z **uživatelského ovládacího prvku**, takže přidejte položku **uživatelského ovládacího prvku** do projektu **LookupControlWalkthrough** .

1. V nabídce **projekt** vyberte možnost **Přidat uživatelský ovládací prvek**.

2. `LookupBox`Do oblasti **název** zadejte a pak klikněte na **Přidat**.

     Ovládací prvek **LookupBox** je přidán do **Průzkumník řešení** a otevře se v návrháři.

## <a name="design-the-lookupbox-control"></a>Návrh ovládacího prvku LookupBox

Chcete-li navrhnout ovládací prvek LookupBox, přetáhněte <xref:System.Windows.Forms.ComboBox> z **panelu nástrojů** na návrhovou plochu uživatelského ovládacího prvku.

## <a name="add-the-required-data-binding-attribute"></a>Přidání požadovaného atributu datové vazby

Pro vyhledávací ovládací prvky, které podporují datovou vazbu, můžete implementovat <xref:System.ComponentModel.LookupBindingPropertiesAttribute> .

1. Přepněte ovládací prvek **LookupBox** do zobrazení kódu. (V nabídce **zobrazení** vyberte položku **kód**.)

2. Kód nahraďte následujícím kódem `LookupBox` :

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/LookupBox.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/LookupBox.cs" id="Snippet5":::

3. V nabídce **sestavení** klikněte na příkaz **Sestavit řešení**.

## <a name="create-a-data-source-from-your-database"></a>Vytvoření zdroje dat z databáze

Tento krok vytvoří zdroj dat pomocí průvodce **konfigurací zdroje dat** , který je založený na `Customers` tabulkách a `Orders` v ukázkové databázi Northwind.

1. Chcete-li otevřít okno **zdroje dat** , klikněte v nabídce **data** na možnost **Zobrazit zdroje dat**.

2. V okně **zdroje dat** vyberte možnost **Přidat nový zdroj dat** a spusťte průvodce **konfigurací zdroje dat** .

3. Vyberte možnost **databáze** na stránce **Vybrat typ zdroje dat** a poté klikněte na tlačítko **Další**.

4. Na stránce **Vyberte datové připojení** proveďte jednu z následujících akcí:

    - Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

    - Vyberte **nové připojení** , aby se spustilo dialogové okno **Přidat nebo upravit připojení** .

5. Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí citlivých dat a potom klikněte na tlačítko **Další**.

6. Na stránce **Uložit připojovací řetězec do konfiguračního souboru aplikace** klikněte na tlačítko **Další**.

7. Na stránce **zvolit databázové objekty** rozbalte uzel **tabulky** .

8. Vyberte `Customers` tabulky a a `Orders` pak klikněte na **Dokončit**.

     **NorthwindDataSet** je přidán do projektu a `Customers` `Orders` tabulky a se zobrazí v okně **zdroje dat** .

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Nastavení sloupce KódZákazníka tabulky Orders na použití ovládacího prvku LookupBox

V okně **zdroje dat** můžete nastavit, aby byl ovládací prvek vytvořen před přetažením položek do formuláře.

1. Otevřete **Form1** v návrháři.

2. Rozbalte uzel **zákazníci** v okně **zdroje dat** .

3. Rozbalte uzel **objednávky** (ten v uzlu **zákazníci** pod sloupcem **Fax** ).

4. V uzlu **objednávky** klikněte na šipku rozevíracího seznamu a v seznamu ovládacích prvků vyberte možnost **Podrobnosti** .

5. Klikněte na šipku rozevíracího seznamu ve sloupci **KódZákazníka** (v uzlu **objednávky** ) a vyberte možnost **přizpůsobit**.

6. Vyberte **LookupBox** ze seznamu **přidružených ovládacích prvků** v dialogovém okně **Možnosti přizpůsobení uživatelského rozhraní dat** .

7. Klikněte na **OK**.

8. Klikněte na šipku rozevíracího seznamu ve sloupci **KódZákazníka** a vyberte možnost **LookupBox**.

## <a name="add-controls-to-the-form"></a>Přidat ovládací prvky do formuláře

Můžete vytvořit ovládací prvky vázané na data přetažením položek z okna **zdroje dat** do formuláře **Form1**.

Chcete-li vytvořit ovládací prvky vázané na data ve formuláři Windows, přetáhněte uzel **objednávky** z okna **zdroje dat** do formuláře Windows a ověřte, zda se ovládací prvek **LookupBox** používá k zobrazení dat ve `CustomerID` sloupci.

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Navázání ovládacího prvku na hledání CompanyName z tabulky Customers

Chcete-li nastavit vyhledávací vazby, vyberte uzel hlavní **zákazníci** v okně **zdroje dat** a přetáhněte jej na pole se seznamem v **CustomerIDLookupBox** na **Form1**.

Tím se nastaví datová vazba, aby se zobrazila `CompanyName` z `Customers` tabulky a zároveň se zachovala `CustomerID` hodnota z `Orders` tabulky.

## <a name="run-the-application"></a>Spuštění aplikace

- Stisknutím klávesy **F5** spusťte aplikaci.

- Procházejte některými záznamy a ověřte, že `CompanyName` se zobrazí v `LookupBox` ovládacím prvku.

## <a name="see-also"></a>Viz také

- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
