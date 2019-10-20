---
title: Vytvoření uživatelského ovládacího prvku model Windows Forms, který podporuje složitou datovou vazbu | Microsoft Docs
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
- data binding, complex
- user controls [Visual Studio], complex data binding
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99c4a20939ed2e3a036831930749bb59b5a42315
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670042"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Vytvoření uživatelského ovládacího prvku modelu Windows Forms, který podporuje složitou datovou vazbu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při zobrazování dat ve formulářích v aplikacích systému Windows můžete zvolit existující ovládací prvky z **panelu nástrojů**, nebo můžete vytvořit vlastní ovládací prvky, pokud vaše aplikace vyžaduje funkce, které nejsou k dispozici ve standardních ovládacích prvcích. Tento návod ukazuje, jak vytvořit ovládací prvek, který implementuje <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Ovládací prvky, které implementují <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, obsahují vlastnost `DataSource` a `DataMember`, která může být vázána na data. Tyto ovládací prvky jsou podobné <xref:System.Windows.Forms.DataGridView> nebo <xref:System.Windows.Forms.ListBox>.

 Další informace o vytváření ovládacích prvků naleznete v tématu [vývoj model Windows Formsch ovládacích prvků v době návrhu](https://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).

 Při vytváření ovládacích prvků pro použití ve scénářích vázání dat je nutné implementovat jeden z následujících atributů datové vazby:

|Použití atributu datové vazby|
|-----------------------------------|
|Implementujte <xref:System.ComponentModel.DefaultBindingPropertyAttribute> pro jednoduché ovládací prvky, jako je <xref:System.Windows.Forms.TextBox>, které zobrazují jeden sloupec (nebo vlastnost) dat. Další informace najdete v tématu [vytvoření model Windows Forms uživatelského ovládacího prvku, který podporuje jednoduchou datovou vazbu](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implementujte <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> na ovládací prvky, jako je <xref:System.Windows.Forms.DataGridView>, které zobrazují seznamy (nebo tabulky) dat. (Tento postup je popsaný v této stránce s návodem.)|
|Implementujte <xref:System.ComponentModel.LookupBindingPropertiesAttribute> na ovládací prvky, jako je <xref:System.Windows.Forms.ComboBox>, které zobrazují seznamy (nebo tabulky) dat, ale také musí obsahovat jeden sloupec nebo vlastnost. Další informace najdete v tématu [vytvoření model Windows Forms uživatelského ovládacího prvku, který podporuje vazbu vyhledávacích dat](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

 Tento návod vytvoří komplexní ovládací prvek, který zobrazí řádky dat z tabulky. V tomto příkladu se používá tabulka `Customers` z ukázkové databáze Northwind. Komplexní uživatelský ovládací prvek zobrazí tabulku Customers v <xref:System.Windows.Forms.DataGridView> vlastního ovládacího prvku.

 V tomto návodu se naučíte:

- Vytvořte novou **aplikaci pro Windows**.

- Přidejte do projektu nový **uživatelský ovládací prvek** .

- Vizuálně Navrhněte uživatelský ovládací prvek.

- Implementujte atribut `ComplexBindingProperty`.

- Vytvořte datovou sadu pomocí [Průvodce konfigurací zdroje dat](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).

- Nastavte tabulku **Customers** v [okně zdroje dat](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) na použití nového složitého ovládacího prvku.

- Přidejte nový ovládací prvek přetažením z **okna zdroje dat** do formuláře **Form1**.

## <a name="prerequisites"></a>Požadavky
 Aby bylo možné dokončit tento návod, budete potřebovat:

- Přístup k ukázkové databázi Northwind.

## <a name="create-a-windows-application"></a>Vytvoření aplikace pro Windows
 Prvním krokem je vytvoření **aplikace pro Windows**.

#### <a name="to-create-the-new-windows-project"></a>Vytvoření nového projektu Windows

1. V aplikaci Visual Studio v nabídce **soubor** vytvořte nový **projekt**.

2. Pojmenujte projekt **ComplexControlWalkthrough**.

3. Vyberte možnost **aplikace systému Windows**a klikněte na tlačítko **OK**. Další informace najdete v tématu [klientské aplikace](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Vytvoří se projekt **ComplexControlWalkthrough** a přidá se do **Průzkumník řešení**.

## <a name="add-a-user-control-to-the-project"></a>Přidat uživatelský ovládací prvek do projektu
 Vzhledem k tomu, že tento návod vytvoří komplexní ovládací prvek s datovou vazbou z **uživatelského ovládacího prvku**, je nutné do projektu přidat položku **uživatelského ovládacího prvku** .

#### <a name="to-add-a-user-control-to-the-project"></a>Přidání uživatelského ovládacího prvku do projektu

1. V nabídce **projekt** vyberte možnost **Přidat uživatelský ovládací prvek**.

2. Do oblasti **název** zadejte **ComplexDataGridView** a pak klikněte na **Přidat**.

     Ovládací prvek **ComplexDataGridView** je přidán do **Průzkumník řešení**a otevře se v návrháři.

## <a name="design-the-complexdatagridview-control"></a>Návrh ovládacího prvku ComplexDataGridView
 Tento krok přidá <xref:System.Windows.Forms.DataGridView> k uživatelskému ovládacímu prvku.

#### <a name="to-design-the-complexdatagridview-control"></a>Návrh ovládacího prvku ComplexDataGridView

- Přetáhněte <xref:System.Windows.Forms.DataGridView> ze **sady nástrojů** na návrhovou plochu uživatelského ovládacího prvku.

## <a name="add-the-required-data-binding-attribute"></a>Přidání požadovaného atributu datové vazby
 Pro komplexní ovládací prvky, které podporují datovou vazbu, můžete implementovat <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>.

#### <a name="to-implement-the-complexbindingproperties-attribute"></a>Implementace atributu ComplexBindingProperties

1. Přepněte ovládací prvek **ComplexDataGridView** do zobrazení kódu. (V nabídce **zobrazení** vyberte položku **kód**.)

2. Kód v `ComplexDataGridView` nahraďte následujícím kódem:

     [!code-csharp[VbRaddataDisplaying#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs#4)]
     [!code-vb[VbRaddataDisplaying#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb#4)]

3. V nabídce **sestavení** klikněte na příkaz **Sestavit řešení**.

## <a name="creating-a-data-source-from-your-database"></a>Vytvoření zdroje dat z databáze
 Tento krok používá Průvodce **konfigurací zdroje dat** k vytvoření zdroje dat založeného na `Customers` tabulce v ukázkové databázi Northwind. Abyste mohli vytvořit připojení, musíte mít přístup k ukázkové databázi Northwind. Informace o nastavení ukázkové databáze Northwind najdete v tématu [Instalace ukázkových databází SQL Server](../data-tools/install-sql-server-sample-databases.md).

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

8. Vyberte tabulku `Customers` a pak klikněte na **Dokončit**.

     **NorthwindDataSet** je přidán do projektu a tabulka `Customers` se zobrazí v okně **zdroje dat** .

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Nastavení tabulky Customers pro použití ovládacího prvku ComplexDataGridView
 V okně **zdroje dat** můžete nastavit, aby byl ovládací prvek vytvořen před přetažením položek do formuláře.

#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Nastavení tabulky Customers pro vytvoření vazby k ovládacímu prvku ComplexDataGridView

1. Otevřete **Form1** v návrháři.

2. Rozbalte uzel **zákazníci** v okně **zdroje dat** .

3. Klikněte na šipku rozevíracího seznamu v uzlu **Customers (zákazníci** ) a vyberte **přizpůsobit**.

4. Vyberte **ComplexDataGridView** ze seznamu **přidružených ovládacích prvků** v dialogovém okně **Možnosti přizpůsobení uživatelského rozhraní dat** .

5. Klikněte na šipku rozevíracího seznamu v `Customers` tabulce a v seznamu ovládacích prvků vyberte možnost **ComplexDataGridView** .

## <a name="addcontrols-to-the-form"></a>Addcontrols do formuláře
 Můžete vytvořit ovládací prvky vázané na data přetažením položek z okna **zdroje dat** do formuláře.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Vytvoření ovládacích prvků vázaných na data ve formuláři

- Přetáhněte hlavní uzel **Customers** z okna **zdroje dat** do formuláře. Ověřte, zda se k zobrazení dat tabulky používá ovládací prvek **ComplexDataGridView** .

## <a name="running-the-application"></a>Spuštění aplikace

#### <a name="to-run-the-application"></a>Spuštění aplikace

- Stisknutím klávesy F5 spusťte aplikaci.

## <a name="next-steps"></a>Další kroky
 V závislosti na požadavcích vaší aplikace existuje několik kroků, které můžete chtít provést po vytvoření ovládacího prvku, který podporuje datovou vazbu. Mezi typické další kroky patří:

- Vlastní ovládací prvky můžete umístit do knihovny ovládacích prvků, abyste je mohli znovu použít v jiných aplikacích.

- Vytváření ovládacích prvků, které podporují scénáře vyhledávání. Další informace najdete v tématu [vytvoření model Windows Forms uživatelského ovládacího prvku, který podporuje vazbu vyhledávacích dat](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Viz také
 [Vázání ovládacích prvků model Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md) [model Windows Forms ovládacích prvků](https://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a)
