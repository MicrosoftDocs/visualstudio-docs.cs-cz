---
title: Ukládání dat v rámci transakce | Dokumentace Microsoftu
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
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b0912ffbe2a9a82ac5efbd3b2ca6ba3566ce5b02
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219299"
---
# <a name="save-data-in-a-transaction"></a>Ukládání dat do transakce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Tento návod ukazuje, jak uložit data v transakci pomocí <xref:System.Transactions> oboru názvů. V tomto příkladu `Customers` a `Orders` tabulek z ukázkové databáze Northwind.  
  
## <a name="prerequisites"></a>Požadavky  
 Tento návod vyžaduje přístup k ukázkové databázi Northwind. Informace o nastavení ukázkové databáze Northwind naleznete v tématu [postupy: Instalace ukázkových databází](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-a-windows-application"></a>Vytvoření aplikace Windows  
 Prvním krokem je vytvoření **aplikace Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Vytvoření nového projektu Windows  
  
1.  V sadě Visual Studio na **souboru** nabídky, vytvořte nový **projektu**.  
  
2.  Pojmenujte projekt **SavingDataInATransactionWalkthrough**.  
  
3.  Vyberte **aplikace Windows**a pak vyberte **OK**. Další informace najdete v tématu [klientské aplikace](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **SavingDataInATransactionWalkthrough** projekt je vytvořen a přidán do **Průzkumníka řešení**.  
  
## <a name="create-a-database-data-source"></a>Vytvoření databázového zdroje dat  
 Tento krok používá [Průvodce konfigurací zdroje dat](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) vytvořit zdroj dat na základě `Customers` a `Orders` tabulky v ukázkové databázi Northwind.  
  
#### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat  
  
1.  Na **Data** nabídce vyberte možnost**zobrazit zdroje dat**.  
  
2.  V **zdroje dat** okně **přidat nový zdroj dat** spustit **Průvodce konfigurací zdroje dat**.  
  
3.  Na **zvolte typ zdroje dat**obrazovky, vyberte **databáze**a pak vyberte **Další**.  
  
4.  Na **vyberte datové připojení**obrazovky proveďte následující:  
  
    -   Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.  
  
         -nebo-  
  
    -   Vyberte **nové připojení** ke spuštění **přidat/změnit připojení** dialogové okno a vytvořte připojení k databázi Northwind.  
  
5.  Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí důvěrných osobních údajů a pak vyberte **Další**.  
  
6.  Na **uložit připojovací řetězec do konfiguračního souboru aplikace** obrazovky, vyberte **Další**.  
  
7.  Na **zvolte vaše databázové objekty** obrazovky, rozbalte **tabulky** uzlu.  
  
8.  Vyberte `Customers` a `Orders` tabulky a pak vyberte **Dokončit**.  
  
     **NorthwindDataSet** se přidá do vašeho projektu a `Customers` a `Orders` tabulky se zobrazí v **zdroje dat** okna.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols do formuláře  
 Můžete vytvořit ovládací prvky vázané na data přetažením položek z **zdroje dat** okna do formuláře.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Vytvoření dat vázané ovládací prvky na formuláři Windows  
  
-   V **zdroje dat** okna, rozbalte **zákazníkům** uzlu.  
  
-   Přetáhněte hlavní **zákazníkům** uzlu z **zdroje dat** okna do **Form1**.  
  
     A <xref:System.Windows.Forms.DataGridView> ovládacího prvku a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů se zobrazí ve formuláři. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md),<xref:System.Windows.Forms.BindingSource>, a <xref:System.Windows.Forms.BindingNavigator> zobrazují v panelu komponent.  
  
-   Přetáhněte související **objednávky** uzlu (není hlavním **objednávky** uzlu, ale následující související podřízené tabulky uzlu **Fax** sloupce) do níže uvedeného formuláře  **CustomersDataGridView**.  
  
     A <xref:System.Windows.Forms.DataGridView> se zobrazí ve formuláři. [OrdersTableAdapter](../data-tools/tableadapter-overview.md) a <xref:System.Windows.Forms.BindingSource> zobrazují v panelu komponent.  
  
## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Přidat odkaz na sestavení System.Transactions  
 Použití transakce <xref:System.Transactions> oboru názvů. Odkaz na sestavení system.transactions není přidán ve výchozím nastavení, takže je třeba ručně přidat.  
  
#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Chcete-li přidat odkaz na soubor System.Transactions DLL  
  
1.  Na **projektu** nabídce vyberte možnost**přidat odkaz**.  
  
2.  Vyberte **System.Transactions**(na **.NET** kartu) a pak vyberte **OK**.  
  
     Odkaz na **System.Transactions** se přidá do projektu.  
  
## <a name="modifythe-code-in-the-bindingnavigators-saveitem-button"></a>Kód Modifythe tlačítku SaveItem prvku BindingNavigator  
 Kód je jako první tabulku přetaženy do formuláře přidán ve výchozím nastavení `click` události uložení tlačítko <xref:System.Windows.Forms.BindingNavigator>. Budete muset ručně přidat kód pro aktualizaci žádné další tabulky. V tomto návodu budeme Refaktorovat stávající uložit kód mimo uložení tlačítko obslužné rutiny události. Můžeme také vytvořit několik další metody, které poskytují funkce konkrétní aktualizace na základě na, jestli řádku musí být přidány nebo odstraněny.  
  
#### <a name="to-modify-the-auto-generated-save-code"></a>Chcete-li změnit automaticky generovanou uložit kódu  
  
1. Vyberte **Uložit** tlačítko **CustomersBindingNavigator** (tlačítko s ikonou diskety).  
  
2. Nahradit `CustomersBindingNavigatorSaveItem_Click` metodu s následujícím kódem:  
  
    [!code-csharp[VbRaddataSaving#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#4)]
    [!code-vb[VbRaddataSaving#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#4)]  
  
   Sjednocování změn na související data pořadí vypadá takto:  
  
-   Odstraňte podřízené záznamy. (V tomto případě odstranit záznamy `Orders` tabulky.)  
  
-   Odstraňte nadřazené záznamy. (V tomto případě odstranit záznamy `Customers` tabulky.)  
  
-   Vložte nadřazené záznamy. (V tomto případě vkládání záznamů v `Customers` tabulky.)  
  
-   Vložte podřízené záznamy. (V tomto případě vkládání záznamů v `Orders` tabulky.)  
  
#### <a name="to-delete-existing-orders"></a>Chcete-li odstranit existující objednávky  
  
-   Přidejte následující `DeleteOrders` metodu **Form1**:  
  
     [!code-csharp[VbRaddataSaving#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#5)]
     [!code-vb[VbRaddataSaving#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#5)]  
  
#### <a name="to-delete-existing-customers"></a>Chcete-li odstranit stávající zákazníci  
  
-   Přidejte následující `DeleteCustomers` metodu **Form1**:  
  
     [!code-csharp[VbRaddataSaving#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#6)]
     [!code-vb[VbRaddataSaving#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#6)]  
  
#### <a name="to-add-new-customers"></a>Chcete-li přidat nové zákazníky  
  
-   Přidejte následující `AddNewCustomers` metodu **Form1**:  
  
     [!code-csharp[VbRaddataSaving#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#7)]
     [!code-vb[VbRaddataSaving#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#7)]  
  
#### <a name="to-add-new-orders"></a>Chcete-li přidat nové objednávky  
  
-   Přidejte následující `AddNewOrders` metodu **Form1**:  
  
     [!code-csharp[VbRaddataSaving#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#8)]
     [!code-vb[VbRaddataSaving#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#8)]  
  
## <a name="run-the-application"></a>Spuštění aplikace  
  
#### <a name="to-run-the-application"></a>Ke spuštění aplikace  
  
-   Vyberte **F5** ke spuštění aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)

