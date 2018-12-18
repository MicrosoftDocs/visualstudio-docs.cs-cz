---
title: Vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje jednoduchou datovou vazbu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 607c324e11591211593522957dcd08747d230279
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219820"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje jednoduchou datovou vazbu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Při zobrazení dat ve formulářích v aplikacích Windows, můžete vybrat z existujících ovládacích prvků **nástrojů**, nebo můžete vytvořit vlastní ovládací prvky, pokud vaše aplikace vyžaduje funkce, které nejsou k dispozici ve standardní ovládací prvky. Tento návod ukazuje, jak vytvořit ovládací prvek, který implementuje <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. Ovládací prvky, které implementují <xref:System.ComponentModel.DefaultBindingPropertyAttribute> může obsahovat jednu vlastnost, která může být vázaný na data. Tyto ovládací prvky jsou podobné <xref:System.Windows.Forms.TextBox> nebo <xref:System.Windows.Forms.CheckBox>.  
  
 Další informace o vytváření ovládacího prvku, naleznete v tématu [vývoj prvky Windows Forms v době návrhu](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Při vytváření ovládacích prvků pro použití ve scénářích datové vazby, měli byste implementovat jednu z následujících atributů datové vazby:  
  
|Použití atributu vázání dat|  
|-----------------------------------|  
|Implementace <xref:System.ComponentModel.DefaultBindingPropertyAttribute> na jednoduché ovládací prvky, jako je <xref:System.Windows.Forms.TextBox>, který zobrazí jeden sloupec (nebo vlastnost) dat. (Tento proces je popsán v této stránce průvodce.)|  
|Implementace <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> na ovládací prvky, jako je <xref:System.Windows.Forms.DataGridView>, který zobrazí seznamy (nebo tabulky) data. Další informace najdete v tématu [vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje rozšířené datové vazby](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implementace <xref:System.ComponentModel.LookupBindingPropertiesAttribute> na ovládací prvky, jako je <xref:System.Windows.Forms.ComboBox>, který zobrazí seznamy (nebo tabulky) data, ale také budete muset k dispozici do jednoho sloupce nebo vlastnosti. Další informace najdete v tématu [vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje vazbu vyhledávacích dat](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 Tento návod vytvoří jednoduchý ovládací prvek zobrazující data z jednoho sloupce v tabulce. V tomto příkladu `Phone` sloupec `Customers` tabulky z ukázkové databáze Northwind. Pomocí jednoduchého uživatelského ovládacího prvku zobrazí zákazníků telefonní čísla ve standardním formátu telefonní číslo, <xref:System.Windows.Forms.MaskedTextBox> a nastavení masky na telefonní číslo.  
  
 V tomto návodu se dozvíte, jak:  
  
-   Vytvořte nový **aplikace Windows**.  
  
-   Přidat nový **uživatelský ovládací prvek** do projektu.  
  
-   Vizuální návrh uživatelského ovládacího prvku.  
  
-   Implementace `DefaultBindingProperty` atribut.  
  
-   Vytvoření datové sady **konfigurace zdroje dat** průvodce.  
  
-   Nastavit **Phone** sloupec **zdroje dat** okna nový ovládací prvek.  
  
-   Vytvořte formulář pro zobrazení dat v ovládacím prvku nové.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat:  
  
-   Přístup k ukázkové databázi Northwind. Další informace najdete v tématu [postupy: Instalace ukázkových databází](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-a-windows-application"></a>Vytvoření aplikace Windows  
 Prvním krokem je vytvoření **aplikace Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Vytvoření nového projektu Windows  
  
1.  V sadě Visual Studio z **souboru** nabídky, vytvořte nový **projektu**.  
  
2.  Pojmenujte projekt **SimpleControlWalkthrough**.  
  
3.  Vyberte **aplikace Windows** a klikněte na tlačítko **OK**. Další informace najdete v tématu [klientské aplikace](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **SimpleControlWalkthrough** projekt je vytvořen a přidán do **Průzkumníka řešení**.  
  
## <a name="add-a-user-control-to-the-project"></a>Přidat uživatelský ovládací prvek do projektu  
 Tento návod vytvoří jednoduchý data neumožňující vazbu ovládacího prvku z **uživatelský ovládací prvek**, proto přidat **uživatelský ovládací prvek** položkou **SimpleControlWalkthrough** projektu.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Chcete-li přidat uživatelský ovládací prvek do projektu  
  
1.  Z **projektu** nabídce zvolte **přidat uživatelský ovládací prvek**.  
  
2.  Typ `PhoneNumberBox` název oblasti, a klikněte na **přidat**.  
  
     **PhoneNumberBox** ovládací prvek je přidán do **Průzkumníka řešení**a otevře v návrháři.  
  
## <a name="design-the-phonenumberbox-control"></a>Návrh PhoneNumberBox ovládacího prvku  
 Tento názorný postup rozšiřují existující <xref:System.Windows.Forms.MaskedTextBox> vytvořit `PhoneNumberBox` ovládacího prvku.  
  
#### <a name="to-design-the-phonenumberbox-control"></a>Chcete-li navrhnout PhoneNumberBox ovládacího prvku  
  
1.  Přetáhněte <xref:System.Windows.Forms.MaskedTextBox> z **nástrojů** na návrhové ploše uživatelský ovládací prvek.  
  
2.  Vyberte na inteligentní značku <xref:System.Windows.Forms.MaskedTextBox> jste právě přetáhli a zvolte **nastavena maska**.  
  
3.  Vyberte **telefonní číslo** v **vstupní maska** dialogové okno a klikněte na tlačítko **OK** k nastavení masky.  
  
## <a name="add-the-required-data-binding-attribute"></a>Přidat požadovaný atribut vázání dat  
 Pro jednoduché ovládací prvky tuto podporu vázání dat, implementujte <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.  
  
#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>K implementaci atribut DefaultBindingProperty  
  
1.  Přepnout `PhoneNumberBox` ovládacího prvku na zobrazení kódu. (Na **zobrazení** nabídce zvolte **kód**.)  
  
2.  Nahraďte kód v `PhoneNumberBox` následujícím kódem:  
  
     [!code-csharp[VbRaddataDisplaying#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/PhoneNumberBox.cs#3)]
     [!code-vb[VbRaddataDisplaying#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/PhoneNumberBox.vb#3)]  
  
3.  Z **sestavení** nabídce zvolte **sestavit řešení**.  
  
## <a name="create-a-data-source-from-your-database"></a>Vytvoření zdroje dat z databáze  
 Tento krok používá **konfigurace zdroje dat** průvodce k vytvoření zdroje dat na základě `Customers` tabulky v ukázkové databázi Northwind. Musíte mít přístup k ukázkové databázi Northwind k vytvoření připojení. Informace o instalaci ukázkové databáze Northwind naleznete v tématu [postupy: Instalace ukázkových databází](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat  
  
1.  Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.  
  
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
 V rámci **zdroje dat** okně můžete nastavit ovládacího prvku má být vytvořen před přetažení položek do formuláře.  
  
#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>Chcete-li nastavit sloupec Telefon pro vytvoření vazby na ovládací prvek PhoneNumberBox  
  
1.  Otevřít **Form1** v návrháři.  
  
2.  Rozbalte **zákazníkům** uzlu **zdroje dat** okno.  
  
3.  Klikněte na šipku rozevíracího seznamu **zákazníkům** uzel a zvolte **podrobnosti** ze seznamu ovládacích prvků.  
  
4.  Klikněte na šipku rozevíracího seznamu **Phone** sloupce a zvolte **vlastní**.  
  
5.  Vyberte **PhoneNumberBox** ze seznamu **přidružené ovládací prvky** v **možnosti přizpůsobení uživatelského rozhraní dat** dialogové okno.  
  
6.  Klikněte na šipku rozevíracího seznamu **Phone** sloupce a zvolte **PhoneNumberBox**.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols do formuláře  
 Můžete vytvořit ovládací prvky vázané na data přetažením položek z **zdroje dat** okna do formuláře.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Vytvoření ovládacích prvků vázaných na data ve formuláři  
  
-   Přetáhněte hlavní **zákazníkům** uzlu z **zdroje dat** okna do formuláře a ověřte, zda `PhoneNumberBox` ovládacího prvku se používá k zobrazení dat v `Phone` sloupce.  
  
     Ovládací prvky vázaných dat pomocí popisků se zobrazí ve formuláři, spolu s pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, a <xref:System.Windows.Forms.BindingNavigator> zobrazují v panelu komponent.  
  
## <a name="run-the-application"></a>Spuštění aplikace  
  
#### <a name="to-run-the-application"></a>Ke spuštění aplikace  
  
-   Stisknutím klávesy F5 spusťte aplikaci.  
  
## <a name="next-steps"></a>Další kroky  
 V závislosti na požadavcích aplikace existuje několik kroků, které můžete provést po vytvoření ovládacího prvku, který podporuje datovou vazbu. Některé typické další postup je následující:  
  
-   Umístění vlastních ovládacích prvků do knihovny ovládacích prvků, lze je použít v jiných aplikacích.  
  
-   Vytváření ovládacích prvků, které podporují složitější scénáře datových vazeb. Další informace najdete v tématu [vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje rozšířené datové vazby](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) a [vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje vazbu vyhledávacích dat](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření vazby ovládacích prvků Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdrojů dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)

