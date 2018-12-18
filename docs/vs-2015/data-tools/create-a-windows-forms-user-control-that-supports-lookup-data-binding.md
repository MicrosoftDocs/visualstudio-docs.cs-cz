---
title: Vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje vazbu vyhledávacích dat | Dokumentace Microsoftu
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
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6a1393f45c46709e4085d7e170265b92c6e00266
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219481"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje vazbu vyhledávacích dat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Při zobrazování dat ve Windows Forms, můžete vybrat z existujících ovládacích prvků **nástrojů**, nebo můžete vytvořit vlastní ovládací prvky, pokud vaše aplikace vyžaduje funkce není k dispozici ve standardní ovládací prvky. Tento návod ukazuje, jak vytvořit ovládací prvek, který implementuje <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. Ovládací prvky, které implementují <xref:System.ComponentModel.LookupBindingPropertiesAttribute> může obsahovat tři vlastnosti, které může být vázaný na data. Tyto ovládací prvky jsou podobné <xref:System.Windows.Forms.ComboBox>.  
  
 Další informace o vytváření ovládacího prvku, naleznete v tématu [vývoj prvky Windows Forms v době návrhu](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Při vytváření ovládacích prvků pro použití ve scénářích datové vazby, budete muset implementovat jedno z následujících atributů datové vazby:  
  
|Použití atributu vázání dat|  
|-----------------------------------|  
|Implementace <xref:System.ComponentModel.DefaultBindingPropertyAttribute> na jednoduché ovládací prvky, jako je <xref:System.Windows.Forms.TextBox>, který zobrazí jeden sloupec (nebo vlastnost) dat. Další informace najdete v tématu [vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje jednoduchou datovou vazbu](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implementace <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> na ovládací prvky, jako je <xref:System.Windows.Forms.DataGridView>, který zobrazí seznamy (nebo tabulky) data. Další informace najdete v tématu [vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje rozšířené datové vazby](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implementace <xref:System.ComponentModel.LookupBindingPropertiesAttribute> na ovládací prvky, jako je <xref:System.Windows.Forms.ComboBox>, který zobrazí seznamy (nebo tabulky) data, ale také budete muset k dispozici do jednoho sloupce nebo vlastnosti. (Tento proces je popsán v této stránce průvodce.)|  
  
 Tento návod vytvoří ovládací prvek vyhledávání, která vytvoří vazbu na data ze dvou tabulek. V tomto příkladu `Customers` a `Orders` tabulek z ukázkové databáze Northwind. Ovládací prvek vyhledávání bude vázán k `CustomerID` pole z `Orders` tabulky. Tato hodnota se bude používat pro vyhledávání `CompanyName` z `Customers` tabulky.  
  
 V tomto návodu se dozvíte, jak:  
  
-   Vytvořte nový **aplikace Windows**.  
  
-   Přidat nový **uživatelský ovládací prvek** do projektu.  
  
-   Vizuální návrh uživatelského ovládacího prvku.  
  
-   Implementace `LookupBindingProperty` atribut.  
  
-   Vytvoření datové sady **konfigurace zdroje dat** průvodce.  
  
-   Nastavit **CustomerID** sloupec **objednávky** tabulku **zdroje dat** okna pro použití nového ovládacího prvku.  
  
-   Vytvořte formulář pro zobrazení dat v ovládacím prvku nové.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat:  
  
-   Přístup k ukázkové databázi Northwind.  
  
## <a name="create-a-windows-application"></a>Vytvoření aplikace Windows  
 Prvním krokem je vytvoření **aplikace Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Vytvoření nového projektu Windows  
  
1.  V sadě Visual Studio z **souboru** nabídky, vytvořte nový **projektu**.  
  
2.  Pojmenujte projekt **LookupControlWalkthrough**.  
  
3.  Vyberte **formulářová aplikace Windows**a klikněte na tlačítko **OK**.  
  
     **LookupControlWalkthrough** projekt je vytvořen a přidán do **Průzkumníka řešení**.  
  
## <a name="add-a-user-control-to-the-project"></a>Přidat uživatelský ovládací prvek do projektu  
 Tento návod vytvoří ovládací prvek vyhledávání z **uživatelský ovládací prvek**, proto přidat **uživatelský ovládací prvek** položkou **LookupControlWalkthrough** projektu.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Chcete-li přidat uživatelský ovládací prvek do projektu  
  
1.  Z **projektu** nabídce vyberte možnost **přidat uživatelský ovládací prvek**.  
  
2.  Typ `LookupBox` v **název** oblasti a pak klikněte na tlačítko **přidat**.  
  
     **LookupBox** ovládací prvek je přidán do **Průzkumníka řešení**a otevře v návrháři.  
  
## <a name="design-the-lookupbox-control"></a>Návrh LookupBox ovládacího prvku  
  
#### <a name="to-design-the-lookupbox-control"></a>Chcete-li navrhnout LookupBox ovládacího prvku  
  
-   Přetáhněte <xref:System.Windows.Forms.ComboBox> z **nástrojů** na návrhové ploše uživatelský ovládací prvek.  
  
## <a name="add-the-required-data-binding-attribute"></a>Přidat požadovaný atribut vázání dat  
 Pro vyhledávání ovládacích prvků, že vazba dat podpory, můžete implementovat <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.  
  
#### <a name="to-implement-the-lookupbindingproperties-attribute"></a>K implementaci atribut LookupBindingProperties  
  
1.  Přepnout **LookupBox** ovládacího prvku na zobrazení kódu. (Na **zobrazení** nabídce zvolte **kód**.)  
  
2.  Nahraďte kód v `LookupBox` následujícím kódem:  
  
     [!code-csharp[VbRaddataDisplaying#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/LookupBox.cs#5)]
     [!code-vb[VbRaddataDisplaying#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/LookupBox.vb#5)]  
  
3.  Z **sestavení** nabídce zvolte **sestavit řešení**.  
  
## <a name="create-a-data-source-from-your-database"></a>Vytvoření zdroje dat z databáze  
 Tento krok vytváří zdroj dat pomocí **konfigurace zdroje dat** průvodce, na základě `Customers` a `Orders` tabulky v ukázkové databázi Northwind. Musíte mít přístup k ukázkové databázi Northwind k vytvoření připojení. Informace o instalaci ukázkové databáze Northwind naleznete v tématu [instalace SQL serveru, ukázkové databáze](../data-tools/install-sql-server-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat  
  
1.  Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.  
  
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
  
#### <a name="to-set-the-customerid-column-to-bind-to-the-lookupbox-control"></a>Chcete-li nastavit sloupci CustomerID k vytvoření vazby na ovládací prvek LookupBox  
  
1.  Otevřít **Form1** v návrháři.  
  
2.  Rozbalte **zákazníkům** uzlu **zdroje dat** okno.  
  
3.  Rozbalte **objednávky** uzel (v **zákazníkům** pod uzlem **Fax** sloupec).  
  
4.  Klikněte na šipku rozevíracího seznamu **objednávky** uzel a zvolte **podrobnosti** ze seznamu ovládacích prvků.  
  
5.  Klikněte na šipku rozevíracího seznamu **CustomerID** sloupce (v **objednávky** uzlu) a zvolte **vlastní**.  
  
6.  Vyberte **LookupBox** ze seznamu **přidružené ovládací prvky** v **možnosti přizpůsobení uživatelského rozhraní dat** dialogové okno.  
  
7.  Klikněte na tlačítko **OK**.  
  
8.  Klikněte na šipku rozevíracího seznamu **CustomerID** sloupce a zvolte **LookupBox**.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols do formuláře  
 Můžete vytvořit ovládací prvky vázané na data přetažením položek z **zdroje dat** okna do **Form1**.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>K vytvoření ovládacích prvků vázaných na data ve formuláři Windows  
  
-   Přetáhněte **objednávky** uzlu z **zdroje dat** okna do formuláře Windows a ověřte, zda **LookupBox** ovládacího prvku se používá k zobrazení dat v `CustomerID` sloupec.  
  
## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Vytvoření vazby ovládacího prvku k vyhledání CompanyName z tabulky Zákazníci  
  
#### <a name="to-setup-the-lookup-bindings"></a>Nastavení vazby vyhledávání  
  
-   Vyberte hlavní **zákazníkům** uzlu v **zdroje dat** okna a přetáhněte ji do pole se seznamem v poli **CustomerIDLookupBox** na **Form1** .  
  
     Tím se nastaví datové vazby k zobrazení `CompanyName` z `Customers` tabulky, a přitom `CustomerID` hodnotu `Orders` tabulky.  
  
## <a name="running-the-application"></a>Spuštění aplikace  
  
#### <a name="to-run-the-application"></a>Ke spuštění aplikace  
  
-   Stisknutím klávesy F5 spusťte aplikaci.  
  
-   Procházet některé záznamy a ověřte, že `CompanyName` se zobrazí v `LookupBox` ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

