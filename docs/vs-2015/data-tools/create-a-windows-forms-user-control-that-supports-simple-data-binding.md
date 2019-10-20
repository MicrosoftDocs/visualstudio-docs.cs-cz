---
title: Vytvoření uživatelského ovládacího prvku model Windows Forms, který podporuje jednoduchou datovou vazbu | Microsoft Docs
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
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bf30a38384863c9ba5a8af35af3326a51058d831
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668761"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Vytvoření uživatelského ovládacího prvku modelu Windows Forms, který podporuje jednoduchou datovou vazbu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při zobrazování dat ve formulářích v aplikacích systému Windows můžete zvolit existující ovládací prvky z **panelu nástrojů**, nebo můžete vytvořit vlastní ovládací prvky, pokud vaše aplikace vyžaduje funkce, které nejsou k dispozici ve standardních ovládacích prvcích. Tento návod ukazuje, jak vytvořit ovládací prvek, který implementuje <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. Ovládací prvky, které implementují <xref:System.ComponentModel.DefaultBindingPropertyAttribute> mohou obsahovat jednu vlastnost, která může být svázána s daty. Tyto ovládací prvky jsou podobné <xref:System.Windows.Forms.TextBox> nebo <xref:System.Windows.Forms.CheckBox>.

 Další informace o vytváření ovládacích prvků naleznete v tématu [vývoj model Windows Formsch ovládacích prvků v době návrhu](https://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).

 Při vytváření ovládacích prvků pro použití ve scénářích vázání dat byste měli implementovat jeden z následujících atributů datové vazby:

|Použití atributu datové vazby|
|-----------------------------------|
|Implementujte <xref:System.ComponentModel.DefaultBindingPropertyAttribute> pro jednoduché ovládací prvky, jako je <xref:System.Windows.Forms.TextBox>, které zobrazují jeden sloupec (nebo vlastnost) dat. (Tento postup je popsaný v této stránce s návodem.)|
|Implementujte <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> na ovládací prvky, jako je <xref:System.Windows.Forms.DataGridView>, které zobrazují seznamy (nebo tabulky) dat. Další informace najdete v tématu [vytvoření model Windows Forms uživatelského ovládacího prvku, který podporuje složitou datovou vazbu](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implementujte <xref:System.ComponentModel.LookupBindingPropertiesAttribute> na ovládací prvky, jako je <xref:System.Windows.Forms.ComboBox>, které zobrazují seznamy (nebo tabulky) dat, ale také musí obsahovat jeden sloupec nebo vlastnost. Další informace najdete v tématu [vytvoření model Windows Forms uživatelského ovládacího prvku, který podporuje vazbu vyhledávacích dat](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

 Tento návod vytvoří jednoduchý ovládací prvek, který zobrazí data z jednoho sloupce v tabulce. V tomto příkladu se používá sloupec `Phone` tabulky `Customers` z ukázkové databáze Northwind. Jednoduchý uživatelský ovládací prvek zobrazí telefonní čísla zákazníků ve standardním formátu pro telefonní číslo, a to pomocí <xref:System.Windows.Forms.MaskedTextBox> a nastavení masky na telefonní číslo.

 V tomto návodu se naučíte:

- Vytvořte novou **aplikaci pro Windows**.

- Přidejte do projektu nový **uživatelský ovládací prvek** .

- Vizuálně Navrhněte uživatelský ovládací prvek.

- Implementujte atribut `DefaultBindingProperty`.

- Vytvořte datovou sadu pomocí průvodce **konfigurací zdroje dat** .

- Nastavte sloupec **telefon** v okně **zdroje dat** na použití nového ovládacího prvku.

- Vytvořte formulář pro zobrazení dat v novém ovládacím prvku.

## <a name="prerequisites"></a>Požadavky
 Aby bylo možné dokončit tento návod, budete potřebovat:

- Přístup k ukázkové databázi Northwind.

## <a name="create-a-windows-application"></a>Vytvoření aplikace pro Windows
 Prvním krokem je vytvoření **aplikace pro Windows**.

#### <a name="to-create-the-new-windows-project"></a>Vytvoření nového projektu Windows

1. V aplikaci Visual Studio v nabídce **soubor** vytvořte nový **projekt**.

2. Pojmenujte projekt **SimpleControlWalkthrough**.

3. Vyberte **aplikace systému Windows** a klikněte na tlačítko **OK**. Další informace najdete v tématu [klientské aplikace](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Vytvoří se projekt **SimpleControlWalkthrough** a přidá se do **Průzkumník řešení**.

## <a name="add-a-user-control-to-the-project"></a>Přidat uživatelský ovládací prvek do projektu
 Tento návod vytvoří jednoduchý ovládací prvek s datovou vazbou z **uživatelského ovládacího prvku**, takže přidejte položku **uživatelského ovládacího prvku** do projektu **SimpleControlWalkthrough** .

#### <a name="to-add-a-user-control-to-the-project"></a>Přidání uživatelského ovládacího prvku do projektu

1. V nabídce **projekt** vyberte možnost **Přidat uživatelský ovládací prvek**.

2. Do oblasti název zadejte `PhoneNumberBox` a klikněte na **Přidat**.

     Ovládací prvek **PhoneNumberBox** je přidán do **Průzkumník řešení**a otevře se v návrháři.

## <a name="design-the-phonenumberbox-control"></a>Návrh ovládacího prvku PhoneNumberBox
 Tento návod rozbalí existující <xref:System.Windows.Forms.MaskedTextBox> a vytvoří ovládací prvek `PhoneNumberBox`.

#### <a name="to-design-the-phonenumberbox-control"></a>Návrh ovládacího prvku PhoneNumberBox

1. Přetáhněte <xref:System.Windows.Forms.MaskedTextBox> ze **sady nástrojů** na návrhovou plochu uživatelského ovládacího prvku.

2. Vyberte inteligentní značku na <xref:System.Windows.Forms.MaskedTextBox>, kterou jste právě přetáhli, a zvolte **nastavit masku**.

3. V dialogovém okně **vstupní maska** vyberte **telefonní číslo** a kliknutím na tlačítko **OK** nastavte masku.

## <a name="add-the-required-data-binding-attribute"></a>Přidání požadovaného atributu datové vazby
 Pro jednoduché ovládací prvky, které podporují datovou vazbu, implementujte <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.

#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>Implementace atributu DefaultBindingProperty

1. Přepněte ovládací prvek `PhoneNumberBox` do zobrazení kódu. (V nabídce **zobrazení** vyberte položku **kód**.)

2. Kód v `PhoneNumberBox` nahraďte následujícím kódem:

     [!code-csharp[VbRaddataDisplaying#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/PhoneNumberBox.cs#3)]
     [!code-vb[VbRaddataDisplaying#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/PhoneNumberBox.vb#3)]

3. V nabídce **sestavení** klikněte na příkaz **Sestavit řešení**.

## <a name="create-a-data-source-from-your-database"></a>Vytvoření zdroje dat z databáze
 Tento krok používá Průvodce **konfigurací zdroje dat** k vytvoření zdroje dat založeného na `Customers` tabulce v ukázkové databázi Northwind. Abyste mohli vytvořit připojení, musíte mít přístup k ukázkové databázi Northwind.

#### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat

1. V nabídce **data** klikněte na možnost **Zobrazit zdroje dat**.

2. V okně **zdroje dat** vyberte možnost **Přidat nový zdroj dat** a spusťte průvodce **konfigurací zdroje dat** .

3. Na stránce **Zvolte typ zdroje dat** vyberte možnost **databáze**a poté klikněte na tlačítko **Další**.

4. Na stránce **Vyberte datové připojení** proveďte jednu z následujících akcí:

    - Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

    - Vyberte **nové připojení** , aby se spustilo dialogové okno **Přidat nebo upravit připojení** .

5. Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí citlivých dat a potom klikněte na tlačítko **Další**.

6. Na stránce **Uložit připojovací řetězec do konfiguračního souboru aplikace** klikněte na tlačítko **Další**.

7. Na stránce **zvolit databázové objekty** rozbalte uzel **tabulky** .

8. Vyberte tabulku `Customers` a pak klikněte na **Dokončit**.

     **NorthwindDataSet** je přidán do projektu a tabulka `Customers` se zobrazí v okně **zdroje dat** .

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Nastavit sloupec pro telefon na použití ovládacího prvku PhoneNumberBox
 V okně **zdroje dat** můžete nastavit, aby byl ovládací prvek vytvořen před přetažením položek do formuláře.

#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>Nastavení sloupce pro telefon na svázání s ovládacím prvkem PhoneNumberBox

1. Otevřete **Form1** v návrháři.

2. Rozbalte uzel **zákazníci** v okně **zdroje dat** .

3. V uzlu **Customers** klikněte na šipku rozevíracího seznamu a v seznamu ovládacích prvků vyberte možnost **Podrobnosti** .

4. Klikněte na šipku rozevíracího seznamu ve sloupci **telefon** a vyberte možnost **přizpůsobit**.

5. Vyberte **PhoneNumberBox** ze seznamu **přidružených ovládacích prvků** v dialogovém okně **Možnosti přizpůsobení uživatelského rozhraní dat** .

6. Klikněte na šipku rozevíracího seznamu ve sloupci **telefon** a vyberte možnost **PhoneNumberBox**.

## <a name="addcontrols-to-the-form"></a>Addcontrols do formuláře
 Můžete vytvořit ovládací prvky vázané na data přetažením položek z okna **zdroje dat** do formuláře.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Vytvoření ovládacích prvků vázaných na data ve formuláři

- Přetáhněte hlavní uzel **Customers** z okna **zdroje dat** do formuláře a ověřte, zda se k zobrazení dat ve sloupci `Phone` používá ovládací prvek `PhoneNumberBox`.

     Ovládací prvky vázané na data s popisnými popisky se zobrazí ve formuláři spolu s pruhem nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů. V zásobníku komponent se zobrazí [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> a <xref:System.Windows.Forms.BindingNavigator>.

## <a name="run-the-application"></a>Spuštění aplikace

#### <a name="to-run-the-application"></a>Spuštění aplikace

- Stisknutím klávesy F5 spusťte aplikaci.

## <a name="next-steps"></a>Další kroky
 V závislosti na požadavcích vaší aplikace existuje několik kroků, které můžete chtít provést po vytvoření ovládacího prvku, který podporuje datovou vazbu. Mezi typické další kroky patří:

- Vlastní ovládací prvky můžete umístit do knihovny ovládacích prvků, abyste je mohli znovu použít v jiných aplikacích.

- Vytváření ovládacích prvků, které podporují složitější scénáře vázání dat. Další informace najdete v tématu [vytvoření model Windows Forms uživatelského ovládacího prvku, který podporuje složitou datovou vazbu](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) a [Vytvoření model Windows Forms uživatelského ovládacího prvku, který podporuje vazbu vyhledávacích dat](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Viz také
 [Vázání ovládacích prvků model Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) [nastavení ovládacího prvku, který má být vytvořen při přetahování z okna zdrojů dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
