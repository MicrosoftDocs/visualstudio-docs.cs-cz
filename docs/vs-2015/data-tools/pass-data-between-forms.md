---
title: Předávání dat mezi formuláři | Dokumentace Microsoftu
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
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a9f28902673018a4ae90fbb2ed83e741be99fbfc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204825"
---
# <a name="pass-data-between-forms"></a>Předávání dat mezi formuláři
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Tento názorný postup obsahuje podrobné pokyny pro předávání dat z jednoho formuláře. Pomocí zákazníci a objednávky tabulky z databáze Northwind, jeden formulář umožňuje uživatelům vybrat zákazníka a druhý formulář pro zobrazení objednávek pro vybraného zákazníka. Tento návod ukazuje, jak vytvořit metodu na druhý formulář, který přijímá data z první formuláře.  
  
> [!NOTE]
>  Tento návod ukazuje pouze jeden ze způsobů předání dat mezi formuláři. Existují další možnosti pro předávání dat do formuláře, včetně vytváření druhý konstruktor pro příjem dat, nebo vytvoření veřejné vlastnosti, které lze nastavit s daty z první formuláře.  
  
 Úlohy v tomto návodu zahrnují:  
  
-   Vytvoření nového **aplikace Windows** projektu.  
  
-   Vytvoření a konfigurace datové sady [Průvodce konfigurací zdroje dat](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Výběr ovládacího prvku, aby se ve formuláři vytvořen při přetažení položky z **zdroje dat** okna. Další informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Vytvoření ovládacího prvku vázané na data přetažením položek z **zdroje dat** okna do formuláře.  
  
-   Vytváří se druhý formulář s mřížce se zobrazí data.  
  
-   Vytváření dotazu TableAdapter načíst objednávek pro konkrétního zákazníka.  
  
-   Předávání dat mezi formuláři.  
  
## <a name="prerequisites"></a>Požadavky  
 Pokud chcete dokončit tento návod, potřebujete:  
  
-   Přístup k ukázkové databázi Northwind. Další informace najdete v tématu [postupy: Instalace ukázkových databází](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-the-windows-application"></a>Vytvoření aplikace Windows  
  
#### <a name="to-create-the-new-windows-project"></a>Vytvoření nového projektu Windows  
  
1.  Z **souboru** nabídky, vytvořte nový projekt.  
  
2.  Pojmenujte projekt `PassingDataBetweenForms`.  
  
3.  Vyberte **formulářová aplikace Windows**a klikněte na tlačítko **OK**. Další informace najdete v tématu [klientské aplikace](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **PassingDataBetweenForms** projekt je vytvořen a přidán do **Průzkumníka řešení**.  
  
## <a name="create-the-data-source"></a>Vytvoření zdroje dat  
  
#### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat  
  
1.  Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.  
  
2.  V **zdroje dat** okně **přidat nový zdroj dat** spustit **konfigurace zdroje dat** průvodce.  
  
3.  Vyberte **databáze** na **zvolte typ zdroje dat** stránce a potom klikněte na tlačítko **Další**.  
  
4.  Na **vyberte databázový model** stránce ověřte, jestli **datovou sadu** je zadán a potom klikněte na **Další**.  
  
5.  Na **vyberte datové připojení** stránce, proveďte jednu z následujících akcí:  
  
    -   Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.  
  
    -   Vyberte **nové připojení** ke spuštění **přidat/změnit připojení** dialogové okno.  
  
6.  Pokud vaše databáze vyžaduje heslo, a pokud je povolena možnost zahrnutí důvěrných osobních údajů, vyberte možnost a potom klikněte na tlačítko **Další**.  
  
7.  Na **uložit připojovací řetězec do konfiguračního souboru aplikace** klikněte na **Další**.  
  
8.  Na **zvolte vaše databázové objekty** stránce, rozbalte **tabulky** uzlu.  
  
9. Vyberte **zákazníkům** a **objednávky** tabulky a pak klikněte na tlačítko **Dokončit**.  
  
     **NorthwindDataSet** se přidá do vašeho projektu a **zákazníkům** a **objednávky** tabulky se zobrazí v **zdroje dat** okna.  
  
## <a name="create-the-first-form-form1"></a>Vytvoření první formulář (Form1)  
 Můžete vytvořit mřížky vázané na data ( <xref:System.Windows.Forms.DataGridView> ovládací prvek), přetažením **zákazníkům** uzlu z **zdroje dat** okna do formuláře.  
  
#### <a name="to-create-a-data-bound-grid-on-the-form"></a>K vytvoření mřížky vázané na data ve formuláři  
  
-   Přetáhněte hlavní **zákazníkům** uzlu z **zdroje dat** okna do **Form1**.  
  
     A <xref:System.Windows.Forms.DataGridView> a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů se zobrazí na **Form1**. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, a <xref:System.Windows.Forms.BindingNavigator> zobrazují v panelu komponent.  
  
## <a name="create-the-second-form-form2"></a>Vytvořte druhý formulář (Form2)  
  
#### <a name="to-create-a-second-form-to-pass-the-data-to"></a>Chcete-li vytvořit druhý formulář k předávání dat do  
  
1.  Z **projektu** nabídce zvolte **přidat formulář Windows**.  
  
2.  Ponechte výchozí název **Form2**a klikněte na tlačítko **přidat**.  
  
3.  Přetáhněte hlavní **objednávky** uzlu z **zdroje dat** okna do **Form2**.  
  
     A <xref:System.Windows.Forms.DataGridView> a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů se zobrazí na **Form2**. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, a <xref:System.Windows.Forms.BindingNavigator> zobrazují v panelu komponent.  
  
4.  Odstranit **OrdersBindingNavigator** z panelu komponent.  
  
     **OrdersBindingNavigator** dané zařízení zmizí z **Form2**.  
  
## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>Přidání dotazu TableAdapter Form2 načíst objednávek pro vybraného zákazníka na Form1  
  
#### <a name="to-create-a-tableadapter-query"></a>Chcete-li vytvořit dotaz TableAdapter  
  
1.  Dvakrát klikněte **NorthwindDataSet.xsd** ve **Průzkumníka řešení**.  
  
2.  Klikněte pravým tlačítkem myši **OrdersTableAdapter**a vyberte **přidat dotaz**.  
  
3.  Ponechte výchozí možnost **použít SQL příkazy**a potom klikněte na tlačítko **Další**.  
  
4.  Ponechte výchozí možnost **SELECT, který vrátí řádky**a potom klikněte na tlačítko **Další**.  
  
5.  Přidat klauzuli WHERE do dotazu vrátit `Orders` na základě `CustomerID`. Dotaz by měl vypadat přibližně takto:  
  
    ```  
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry  
    FROM Orders   
    WHERE CustomerID = @CustomerID  
    ```  
  
    > [!NOTE]
    >  Ověření parametru správná syntaxe pro vaši databázi. Například v aplikaci Microsoft Access, klauzuli WHERE vypadat nějak takto: `WHERE CustomerID = ?`.  
  
6.  Klikněte na tlačítko **Další**.  
  
7.  Pro **zadejte název DataTableMethod**, typ `FillByCustomerID`.  
  
8.  Zrušte **vrátit tabulku DataTable** možnost a potom klikněte na tlačítko **Další**.  
  
9. Klikněte na tlačítko **Dokončit**.  
  
## <a name="create-a-method-on-form2-to-pass-data-to"></a>Vytvořit metodu na Form2 k předávání dat do  
  
#### <a name="to-create-a-method-to-pass-data-to"></a>Chcete-li vytvořit metodu k předání dat  
  
1.  Klikněte pravým tlačítkem na **Form2**a vyberte **zobrazit kód** otevřete **Form2** v **Editor kódu**.  
  
2.  Přidejte následující kód, který **Form2** po `Form2_Load` metody:  
  
     [!code-csharp[VbRaddataDisplaying#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form2.cs#1)]
     [!code-vb[VbRaddataDisplaying#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form2.vb#1)]  
  
## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Vytvořit metodu na Form1 k předání dat a zobrazení Form2  
  
#### <a name="to-create-a-method-to-pass-data-to-form2"></a>Vytvoření metody k předávání dat Form2  
  
1.  V **Form1**, klikněte pravým tlačítkem na mřížce dat zákazníků a pak klikněte na **vlastnosti**.  
  
2.  V **vlastnosti** okna, klikněte na tlačítko **události**.  
  
3.  Dvakrát klikněte **CellDoubleClick** událostí.  
  
     Zobrazí se editor kódu.  
  
4.  Aktualizujte definici metody tak, aby odpovídala následující ukázce:  
  
     [!code-csharp[VbRaddataDisplaying#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#2)]
     [!code-vb[VbRaddataDisplaying#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#2)]  
  
## <a name="run-the-application"></a>Spuštění aplikace  
  
#### <a name="to-run-the-application"></a>Ke spuštění aplikace  
  
-   Stisknutím klávesy F5 spusťte aplikaci.  
  
-   Klikněte dvakrát na záznam zákazníka v **Form1** otevřete **Form2** s objednávek tohoto zákazníka.  
  
## <a name="next-steps"></a>Další kroky  
 V závislosti na požadavcích aplikace existuje několik kroků, které můžete provést po předávání dat mezi formuláři. Mezi vylepšení, která je možné pro tento návod provést, patří:  
  
-   Úpravy datové sady, přidání nebo odebrání databázové objekty. Další informace najdete v tématu [vytvoření a konfigurace datové sady](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
-   Přidáváme funkci pro uložení dat zpět do databáze. Další informace najdete v tématu [uložit data zpět do databáze](../data-tools/save-data-back-to-the-database.md).  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

