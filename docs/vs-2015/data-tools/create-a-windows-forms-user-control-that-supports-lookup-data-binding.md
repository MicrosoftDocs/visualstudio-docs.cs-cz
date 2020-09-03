---
title: Vytvoření uživatelského ovládacího prvku model Windows Forms, který podporuje datovou vazbu vyhledávacích dat | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 48891f82667270f04af49c60122c63f8d3a943f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668777"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Vytvoření uživatelského ovládacího prvku modelu Windows Forms, který podporuje vazbu vyhledávacích dat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při zobrazování dat v model Windows Forms můžete zvolit existující ovládací prvky z **panelu nástrojů**, nebo můžete vytvořit vlastní ovládací prvky, pokud vaše aplikace vyžaduje funkce, které nejsou dostupné ve standardních ovládacích prvcích. Tento návod ukazuje, jak vytvořit ovládací prvek, který implementuje rozhraní <xref:System.ComponentModel.LookupBindingPropertiesAttribute> . Ovládací prvky, které implementují, <xref:System.ComponentModel.LookupBindingPropertiesAttribute> mohou obsahovat tři vlastnosti, které mohou být vázány na data. Tyto ovládací prvky jsou podobné <xref:System.Windows.Forms.ComboBox> .

 Další informace o vytváření ovládacích prvků naleznete v tématu [vývoj model Windows Formsch ovládacích prvků v době návrhu](https://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).

 Při vytváření ovládacích prvků pro použití ve scénářích vázání dat je nutné implementovat jeden z následujících atributů datové vazby:

|Použití atributu datové vazby|
|-----------------------------------|
|Implementujte <xref:System.ComponentModel.DefaultBindingPropertyAttribute> na jednoduchých ovládacích prvcích, jako je <xref:System.Windows.Forms.TextBox> ,, které zobrazují jeden sloupec (nebo vlastnost) dat. Další informace najdete v tématu [vytvoření model Windows Forms uživatelského ovládacího prvku, který podporuje jednoduchou datovou vazbu](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implementujte <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> ovládací prvky, jako <xref:System.Windows.Forms.DataGridView> jsou, které zobrazují seznamy (nebo tabulky) dat. Další informace najdete v tématu [vytvoření model Windows Forms uživatelského ovládacího prvku, který podporuje složitou datovou vazbu](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implementujte <xref:System.ComponentModel.LookupBindingPropertiesAttribute> ovládací prvky, jako <xref:System.Windows.Forms.ComboBox> jsou, které zobrazují seznamy (nebo tabulky) dat, ale také musí obsahovat jeden sloupec nebo vlastnost. (Tento postup je popsaný v této stránce s návodem.)|

 Tento návod vytvoří ovládací prvek vyhledávání, který se váže k datům ze dvou tabulek. Tento příklad používá `Customers` tabulky a `Orders` z ukázkové databáze Northwind. Ovládací prvek vyhledávání bude svázán s `CustomerID` polem z `Orders` tabulky. Tato hodnota se použije k vyhledání `CompanyName` `Customers` tabulky v tabulce.

 V tomto návodu se naučíte:

- Vytvořte novou **aplikaci pro Windows**.

- Přidejte do projektu nový **uživatelský ovládací prvek** .

- Vizuálně Navrhněte uživatelský ovládací prvek.

- Implementujte `LookupBindingProperty` atribut.

- Vytvořte datovou sadu pomocí průvodce **konfigurací zdroje dat** .

- Nastavte sloupec **KódZákazníka** v tabulce **Orders** v okně **zdroje dat** na použití nového ovládacího prvku.

- Vytvořte formulář pro zobrazení dat v novém ovládacím prvku.

## <a name="prerequisites"></a>Požadavky
 Aby bylo možné dokončit tento návod, budete potřebovat:

- Přístup k ukázkové databázi Northwind.

## <a name="create-a-windows-application"></a>Vytvoření aplikace pro Windows
 Prvním krokem je vytvoření **aplikace pro Windows**.

#### <a name="to-create-the-new-windows-project"></a>Vytvoření nového projektu Windows

1. V aplikaci Visual Studio v nabídce **soubor** vytvořte nový **projekt**.

2. Pojmenujte projekt **LookupControlWalkthrough**.

3. Vyberte **model Windows Forms aplikace**a klikněte na **OK**.

     Vytvoří se projekt **LookupControlWalkthrough** a přidá se do **Průzkumník řešení**.

## <a name="add-a-user-control-to-the-project"></a>Přidat uživatelský ovládací prvek do projektu
 Tento návod vytvoří ovládací prvek vyhledávání z **uživatelského ovládacího prvku**, takže přidejte položku **uživatelského ovládacího prvku** do projektu **LookupControlWalkthrough** .

#### <a name="to-add-a-user-control-to-the-project"></a>Přidání uživatelského ovládacího prvku do projektu

1. V nabídce **projekt** vyberte možnost **Přidat uživatelský ovládací prvek**.

2. `LookupBox`Do oblasti **název** zadejte a pak klikněte na **Přidat**.

     Ovládací prvek **LookupBox** je přidán do **Průzkumník řešení**a otevře se v návrháři.

## <a name="design-the-lookupbox-control"></a>Návrh ovládacího prvku LookupBox

#### <a name="to-design-the-lookupbox-control"></a>Návrh ovládacího prvku LookupBox

- Přetáhněte <xref:System.Windows.Forms.ComboBox> z **panelu nástrojů** na návrhovou plochu uživatelského ovládacího prvku.

## <a name="add-the-required-data-binding-attribute"></a>Přidání požadovaného atributu datové vazby
 Pro vyhledávací ovládací prvky, které podporují datovou vazbu, můžete implementovat <xref:System.ComponentModel.LookupBindingPropertiesAttribute> .

#### <a name="to-implement-the-lookupbindingproperties-attribute"></a>Implementace atributu LookupBindingProperties

1. Přepněte ovládací prvek **LookupBox** do zobrazení kódu. (V nabídce **zobrazení** vyberte položku **kód**.)

2. Kód nahraďte následujícím kódem `LookupBox` :

     [!code-csharp[VbRaddataDisplaying#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/LookupBox.cs#5)]
     [!code-vb[VbRaddataDisplaying#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/LookupBox.vb#5)]

3. V nabídce **sestavení** klikněte na příkaz **Sestavit řešení**.

## <a name="create-a-data-source-from-your-database"></a>Vytvoření zdroje dat z databáze
 Tento krok vytvoří zdroj dat pomocí průvodce **konfigurací zdroje dat** , který je založený na `Customers` tabulkách a `Orders` v ukázkové databázi Northwind. Abyste mohli vytvořit připojení, musíte mít přístup k ukázkové databázi Northwind. Informace o nastavení ukázkové databáze Northwind najdete v tématu [Instalace ukázkových databází SQL Server](../data-tools/install-sql-server-sample-databases.md).

#### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat

1. V nabídce **data** klikněte na možnost **Zobrazit zdroje dat**.

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

#### <a name="to-set-the-customerid-column-to-bind-to-the-lookupbox-control"></a>Nastavení sloupce KódZákazníka pro svázání s ovládacím prvkem LookupBox

1. Otevřete **Form1** v návrháři.

2. Rozbalte uzel **zákazníci** v okně **zdroje dat** .

3. Rozbalte uzel **objednávky** (ten v uzlu **zákazníci** pod sloupcem **Fax** ).

4. V uzlu **objednávky** klikněte na šipku rozevíracího seznamu a v seznamu ovládacích prvků vyberte možnost **Podrobnosti** .

5. Klikněte na šipku rozevíracího seznamu ve sloupci **KódZákazníka** (v uzlu **objednávky** ) a vyberte možnost **přizpůsobit**.

6. Vyberte **LookupBox** ze seznamu **přidružených ovládacích prvků** v dialogovém okně **Možnosti přizpůsobení uživatelského rozhraní dat** .

7. Klikněte na **OK**.

8. Klikněte na šipku rozevíracího seznamu ve sloupci **KódZákazníka** a vyberte možnost **LookupBox**.

## <a name="addcontrols-to-the-form"></a>Addcontrols do formuláře
 Můžete vytvořit ovládací prvky vázané na data přetažením položek z okna **zdroje dat** do formuláře **Form1**.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Vytvoření ovládacích prvků vázaných na data ve formuláři Windows

- Přetáhněte uzel **Orders** z okna **zdroje dat** do formuláře Windows a ověřte, že se ovládací prvek **LookupBox** používá k zobrazení dat ve `CustomerID` sloupci.

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Navázání ovládacího prvku na hledání CompanyName z tabulky Customers

#### <a name="to-setup-the-lookup-bindings"></a>Nastavení vyhledávacích vazeb

- V okně **zdroje dat** vyberte uzel hlavní **zákazníci** a přetáhněte ho na pole se seznamem v **CustomerIDLookupBox** na **Form1**.

     Tím se nastaví datová vazba, aby se zobrazila `CompanyName` z `Customers` tabulky a zároveň se zachovala `CustomerID` hodnota z `Orders` tabulky.

## <a name="running-the-application"></a>Spouštění aplikace.

#### <a name="to-run-the-application"></a>Spuštění aplikace

- Stisknutím klávesy F5 spusťte aplikaci.

- Procházejte některými záznamy a ověřte, že `CompanyName` se zobrazí v `LookupBox` ovládacím prvku.

## <a name="see-also"></a>Viz také
 [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
