---
title: Vytváření uživatelských ovládacích prvků, které podporují jednoduchou datovou vazbu
description: Naučte se vytvořit uživatelský ovládací prvek model Windows Forms, který podporuje jednoduchou datovou vazbu, pomocí třídy DefaultBindingPropertyAttribute v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4ba2010b33b1defa6ef7dcb601fde9417fa47f70
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436742"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Vytvoření uživatelského ovládacího prvku modelu Windows Forms, který podporuje jednoduchou datovou vazbu

Při zobrazování dat ve formulářích v aplikacích systému Windows můžete zvolit existující ovládací prvky z **panelu nástrojů** , nebo můžete vytvořit vlastní ovládací prvky, pokud vaše aplikace vyžaduje funkce, které nejsou k dispozici ve standardních ovládacích prvcích. Tento návod ukazuje, jak vytvořit ovládací prvek, který implementuje rozhraní <xref:System.ComponentModel.DefaultBindingPropertyAttribute> . Ovládací prvky, které implementují, <xref:System.ComponentModel.DefaultBindingPropertyAttribute> mohou obsahovat jednu vlastnost, která může být svázána s daty. Tyto ovládací prvky jsou podobné <xref:System.Windows.Forms.TextBox> nebo <xref:System.Windows.Forms.CheckBox> .

Další informace o vytváření ovládacích prvků naleznete v tématu [vývoj model Windows Formsch ovládacích prvků v době návrhu](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Při vytváření ovládacích prvků pro použití ve scénářích vázání dat byste měli implementovat jeden z následujících atributů datové vazby:

|Použití atributu datové vazby|
| - |
|Implementujte <xref:System.ComponentModel.DefaultBindingPropertyAttribute> na jednoduchých ovládacích prvcích, jako je <xref:System.Windows.Forms.TextBox> ,, které zobrazují jeden sloupec (nebo vlastnost) dat. (Tento postup je popsaný v této stránce s návodem.)|
|Implementujte <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> ovládací prvky, jako <xref:System.Windows.Forms.DataGridView> jsou, které zobrazují seznamy (nebo tabulky) dat. Další informace najdete v tématu [vytvoření model Windows Forms uživatelského ovládacího prvku, který podporuje složitou datovou vazbu](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implementujte <xref:System.ComponentModel.LookupBindingPropertiesAttribute> ovládací prvky, jako <xref:System.Windows.Forms.ComboBox> jsou, které zobrazují seznamy (nebo tabulky) dat, ale také musí obsahovat jeden sloupec nebo vlastnost. Další informace najdete v tématu [vytvoření model Windows Forms uživatelského ovládacího prvku, který podporuje vazbu vyhledávacích dat](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

Tento návod vytvoří jednoduchý ovládací prvek, který zobrazí data z jednoho sloupce v tabulce. V tomto příkladu se používá `Phone` sloupec `Customers` tabulky z ukázkové databáze Northwind. Jednoduchý uživatelský ovládací prvek zobrazuje telefonní čísla zákazníků ve standardním formátu telefonního čísla pomocí <xref:System.Windows.Forms.MaskedTextBox> a nastavuje masku na telefonní číslo.

V tomto návodu se naučíte:

- Vytvořte novou **model Windows Forms aplikaci**.

- Přidejte do projektu nový **uživatelský ovládací prvek** .

- Vizuálně Navrhněte uživatelský ovládací prvek.

- Implementujte `DefaultBindingProperty` atribut.

- Vytvořte datovou sadu pomocí průvodce **konfigurací zdroje dat** .

- Nastavte sloupec **telefon** v okně **zdroje dat** na použití nového ovládacího prvku.

- Vytvořte formulář pro zobrazení dat v novém ovládacím prvku.

## <a name="prerequisites"></a>Předpoklady

Tento návod používá SQL Server Express LocalDB a ukázkovou databázi Northwind.

1. Pokud nemáte SQL Server Express LocalDB, nainstalujte ji buď ze [stránky pro stažení SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program pro Visual Studio**. V **instalační program pro Visual Studio** můžete nainstalovat SQL Server Express LocalDB jako součást úlohy **ukládání a zpracování dat** nebo jako jednotlivé komponenty.

2. Nainstalujte ukázkovou databázi Northwind pomocí následujících kroků:

    1. V aplikaci Visual Studio otevřete okno **Průzkumník objektů systému SQL Server** . (Průzkumník objektů systému SQL Server je nainstalován v rámci úlohy **úložiště dat a zpracování** v **instalační program pro Visual Studio**.) Rozbalte uzel **SQL Server** . Klikněte pravým tlačítkem na instanci LocalDB a vyberte **Nový dotaz**.

       Otevře se okno editoru dotazů.

    2. Zkopírujte [skript Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind od začátku a naplní ji daty.

    3. Vložte skript T-SQL do editoru dotazů a pak klikněte na tlačítko **Spustit** .

       Po krátké době se dotaz dokončí a vytvoří se databáze Northwind.

## <a name="create-a-windows-forms-application"></a>Vytvoření aplikace model Windows Forms

Prvním krokem je vytvoření **model Windows Forms aplikace** :

1. V aplikaci Visual Studio v nabídce **soubor** vyberte **Nový**  >  **projekt**.

2. V levém podokně rozbalte možnost **Visual C#** nebo **Visual Basic** a pak vyberte možnost **desktopová plocha systému Windows**.

3. V prostředním podokně vyberte typ projektu **aplikace model Windows Forms** .

4. Pojmenujte projekt **SimpleControlWalkthrough** a klikněte na **tlačítko OK**.

     Vytvoří se projekt **SimpleControlWalkthrough** a přidá se do **Průzkumník řešení**.

## <a name="add-a-user-control-to-the-project"></a>Přidat uživatelský ovládací prvek do projektu

Tento návod vytvoří jednoduchý ovládací prvek s datovou vazbou z **uživatelského ovládacího prvku**. Přidejte položku **uživatelského ovládacího prvku** do projektu **SimpleControlWalkthrough** :

1. V nabídce **projekt** vyberte možnost **Přidat uživatelský ovládací prvek**.

2. Do oblasti název zadejte **PhoneNumberBox** a klikněte na **Přidat**.

     Ovládací prvek **PhoneNumberBox** je přidán do **Průzkumník řešení** a otevře se v návrháři.

## <a name="design-the-phonenumberbox-control"></a>Návrh ovládacího prvku PhoneNumberBox

Tento návod se rozšíří na stávající <xref:System.Windows.Forms.MaskedTextBox> a vytvoří ovládací prvek **PhoneNumberBox** :

1. Přetáhněte <xref:System.Windows.Forms.MaskedTextBox> z **panelu nástrojů** na návrhovou plochu uživatelského ovládacího prvku.

2. Vyberte inteligentní značku na <xref:System.Windows.Forms.MaskedTextBox> právě přetaženou a zvolte **nastavit masku**.

3. V dialogovém okně **vstupní maska** vyberte **telefonní číslo** a kliknutím na tlačítko **OK** nastavte masku.

## <a name="add-the-required-data-binding-attribute"></a>Přidání požadovaného atributu datové vazby

Pro jednoduché ovládací prvky, které podporují datovou vazbu, implementujte <xref:System.ComponentModel.DefaultBindingPropertyAttribute> :

1. Přepněte ovládací prvek **PhoneNumberBox** do zobrazení kódu. (V nabídce **zobrazení** vyberte položku **kód**.)

2. Nahraďte kód v **PhoneNumberBox** následujícím způsobem:

     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]

3. V nabídce **sestavení** klikněte na příkaz **Sestavit řešení**.

## <a name="create-a-data-source-from-your-database"></a>Vytvoření zdroje dat z databáze

Tento krok používá Průvodce **konfigurací zdroje dat** k vytvoření zdroje dat založeného na `Customers` tabulce v ukázkové databázi Northwind. Abyste mohli vytvořit připojení, musíte mít přístup k ukázkové databázi Northwind. Informace o nastavení ukázkové databáze Northwind najdete v tématu [Postup: Instalace ukázkových databází](../data-tools/installing-database-systems-tools-and-samples.md).

1. Chcete-li otevřít okno **zdroje dat** , klikněte v nabídce **data** na možnost **Zobrazit zdroje dat**.

2. V okně **zdroje dat** vyberte možnost **Přidat nový zdroj dat** a spusťte průvodce **konfigurací zdroje dat** .

3. Na stránce **Zvolte typ zdroje dat** vyberte možnost **databáze** a poté klikněte na tlačítko **Další**.

4. Na stránce **Vyberte datové připojení** proveďte jednu z následujících akcí:

    - Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

    - Vyberte **nové připojení** , aby se spustilo dialogové okno **Přidat nebo upravit připojení** .

5. Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí citlivých dat a potom klikněte na tlačítko **Další**.

6. Na stránce **Uložit připojovací řetězec do konfiguračního souboru aplikace** klikněte na tlačítko **Další**.

7. Na stránce **zvolit databázové objekty** rozbalte uzel **tabulky** .

8. Vyberte `Customers` tabulku a pak klikněte na **Dokončit**.

     **NorthwindDataSet** je přidán do projektu a `Customers` tabulka se zobrazí v okně **zdroje dat** .

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Nastavit sloupec pro telefon na použití ovládacího prvku PhoneNumberBox

V okně **zdroje dat** můžete nastavit, aby byl ovládací prvek vytvořen před přetažením položek do formuláře:

1. Otevřete **Form1** v návrháři.

2. Rozbalte uzel **zákazníci** v okně **zdroje dat** .

3. V uzlu **Customers** klikněte na šipku rozevíracího seznamu a v seznamu ovládacích prvků vyberte možnost **Podrobnosti** .

4. Klikněte na šipku rozevíracího seznamu ve sloupci **telefon** a vyberte možnost **přizpůsobit**.

5. Vyberte **PhoneNumberBox** ze seznamu **přidružených ovládacích prvků** v dialogovém okně **Možnosti přizpůsobení uživatelského rozhraní dat** .

6. Klikněte na šipku rozevíracího seznamu ve sloupci **telefon** a vyberte možnost **PhoneNumberBox**.

## <a name="add-controls-to-the-form"></a>Přidat ovládací prvky do formuláře

Můžete vytvořit ovládací prvky vázané na data přetažením položek z okna **zdroje dat** do formuláře.

Chcete-li vytvořit ovládací prvky vázané na data na formuláři, přetáhněte hlavní uzel **Customers** z okna **zdroje dat** do formuláře a ověřte, zda se ovládací prvek **PhoneNumberBox** používá k zobrazení dat ve sloupci **telefon** .

Ovládací prvky vázané na data s popisnými popisky se zobrazí ve formuláři spolu s pruhem nástrojů ( <xref:System.Windows.Forms.BindingNavigator> ) pro procházení záznamů. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> a <xref:System.Windows.Forms.BindingNavigator> se zobrazí v zásobníku komponent.

## <a name="run-the-application"></a>Spuštění aplikace

Stisknutím klávesy **F5** spusťte aplikaci.

## <a name="next-steps"></a>Další kroky

V závislosti na požadavcích vaší aplikace existuje několik kroků, které můžete chtít provést po vytvoření ovládacího prvku, který podporuje datovou vazbu. Mezi typické další kroky patří:

- Vlastní ovládací prvky můžete umístit do knihovny ovládacích prvků, abyste je mohli znovu použít v jiných aplikacích.

- Vytváření ovládacích prvků, které podporují složitější scénáře vázání dat. Další informace najdete v tématu [vytvoření model Windows Forms uživatelského ovládacího prvku, který podporuje složitou datovou vazbu](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) a [Vytvoření model Windows Forms uživatelského ovládacího prvku, který podporuje vazbu vyhledávacích dat](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Viz také

- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdrojů dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
