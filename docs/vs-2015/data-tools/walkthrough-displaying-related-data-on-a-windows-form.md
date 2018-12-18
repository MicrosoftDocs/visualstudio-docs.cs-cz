---
title: 'Návod: Zobrazování souvisejících dat ve formuláři Windows Forms | Dokumentace Microsoftu'
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
- displaying data on forms, walkthroughs
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- master-details lists, displaying on Windows Forms
- data [Visual Studio], master-details
- displaying tables, related data
- displaying table data
- displaying table information
ms.assetid: fc4b9055-2bf3-4028-8aad-9489820d69f6
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 882c8229c105920efe247a54e9525a262e6a3246
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282669"
---
# <a name="walkthrough-displaying-related-data-on-a-windows-form"></a>Návod: Zobrazování souvisejících dat ve formuláři Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V mnoha případech budete chtít, aby aplikace pracovaly s daty z více než jedné tabulky a často také s daty ze souvisejících tabulek. To znamená, že chcete pracovat se vztahem mezi nadřazenými a podřízenými objekty. Budete například chtít vytvořit formulář, ve kterém výběr záznamu zákazníka zobrazí příslušné objednávky. Zobrazení souvisejících záznamů ve formuláři je dosaženo pomocí nastavení vlastnosti <xref:System.Windows.Forms.BindingSource.DataSource%2A> podřízeného objektu <xref:System.Windows.Forms.BindingSource> na nadřazený objekt <xref:System.Windows.Forms.BindingSource> (ne na podřízenou tabulku) a nastavením vlastnosti <xref:System.Windows.Forms.BindingSource.DataMember%2A> podřízeného objektu <xref:System.Windows.Forms.BindingSource> na vztah dat, která spojují dohromady nadřazené a podřízené tabulky.  
  
 Úlohy v tomto návodu zahrnují:  
  
-   Vytváření **aplikace Windows** projektu.  
  
-   Vytvoření a konfigurace datové sady v aplikaci založené na `Customers` a `Orders` tabulek v databázi Northwind pomocí průvodce [Průvodce konfigurací zdroje dat](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Přidání ovládacích prvků pro zobrazení dat z tabulky `Customers`.  
  
-   Přidávání ovládacích prvků pro zobrazení dat z tabulky `Orders` na základě vybraných dat z tabulky `Customer`.  
  
-   Testování aplikace pomocí výběru různých zákazníků a ověření zobrazení správných objednávek pro vybraného zákazníka.  
  
## <a name="prerequisites"></a>Požadavky  
 Pokud chcete dokončit tento návod, potřebujete:  
  
-   Přístup k ukázkové databázi Northwind. Nastavení vzorových databází naleznete v tématu [postupy: Instalace ukázkových databází](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření **aplikace Windows**.  
  
#### <a name="to-create-the-windows-application-project"></a>Postup vytvoření projektu aplikace pro Windows  
  
1.  Z **souboru** nabídky, vytvořte nový projekt.  
  
2.  Pojmenujte projekt `RelatedDataWalkthrough`.  
  
3.  Vyberte **aplikace Windows** a klikněte na tlačítko **OK**. Další informace najdete v tématu [klientské aplikace](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **RelatedDataWalkthrough** projekt je vytvořen a přidán do **Průzkumníka řešení**.  
  
## <a name="creating-the-data-source"></a>Vytvoření zdroje dat  
 Tento krok vytvoří datovou sadu založenou na tabulkách `Customers` a `Orders` vzorové databáze Northwind.  
  
#### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat  
  
1.  Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.  
  
2.  V **zdroje dat** okně **přidat nový zdroj dat** spustit **Průvodce konfigurací zdroje dat**.  
  
3.  Vyberte **databáze** na **zvolte typ zdroje dat** stránce a potom klikněte na tlačítko **Další**.  
  
4.  Na **vyberte datové připojení** stránka provádění, jednu z následujících akcí:  
  
    -   Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.  
  
         -nebo-  
  
    -   Vyberte **nové připojení** ke spuštění **přidat/změnit připojení** dialogové okno.  
  
5.  Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí důvěrných osobních údajů a pak klikněte na tlačítko **Další**.  
  
6.  Klikněte na tlačítko **Další** na **uložit připojovací řetězec do konfiguračního souboru aplikace** stránky.  
  
7.  Rozbalte **tabulky** uzlu **zvolte vaše databázové objekty** stránky.  
  
8.  Vyberte **zákazníkům** a **objednávky** tabulky a pak klikněte na tlačítko **Dokončit**.  
  
     **NorthwindDataSet** se přidá do vašeho projektu a **zákazníkům** tabulky se zobrazí v **zdroje dat** okna.  
  
## <a name="creating-controls-to-display-data-from-the-customers-table"></a>Vytvoření ovládacích prvků pro zobrazení dat z tabulky Zákazníci.  
  
#### <a name="to-create-controls-to-display-the-customer-data-parent-records"></a>Vytvoření ovládacích prvků pro zobrazení údajů o zákazníkovi (nadřazené záznamy)  
  
1.  V **zdroje dat** okna, vyberte **zákazníkům** tabulku a poté klikněte na šipku rozevíracího seznamu.  
  
2.  Zvolte **podrobnosti** z nabídky.  
  
3.  Přetáhněte hlavní **zákazníkům** uzlu z **zdroje dat** okna do horní části **Form1**.  
  
     Ovládací prvky vázaných dat pomocí popisků se zobrazí ve formuláři, spolu s pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, a <xref:System.Windows.Forms.BindingNavigator> zobrazují v panelu komponent.  
  
## <a name="creating-controls-to-display-data-from-the-orders-table"></a>Vytvoření ovládacích prvků pro zobrazení dat z tabulky Objednávky.  
 ![Okno zdroje dat zobrazuje vztah](../data-tools/media/datasources2.gif "DataSources2")  
  
#### <a name="to-create-controls-to-display-the-orders-for-each-customer-child-records"></a>Vytvoření ovládacích prvků zobrazujících objednávky pro každého zákazníka (podřízené záznamy)  
  
-   V **zdroje dat** okna, rozbalte **zákazníkům** uzel a vyberte poslední sloupec **zákazníkům** tabulky, což je rozbalitený **objednávky** uzel a přetáhněte ji na konci **Form1**.  
  
     Ovládací prvek <xref:System.Windows.Forms.DataGridView> je přidán do formuláře a nové komponenty <xref:System.Windows.Forms.BindingSource> (`OrdersBindingSource`) a TableAdapter (`OrdersTableAdapter`) jsou přidány do panelu komponent.  
  
    > [!NOTE]
    >  Otevřít [okno vlastností](../ide/reference/properties-window.md) a vyberte **OrdersBindingSource**. Ověřením vlastností <xref:System.Windows.Forms.BindingSource.DataSource%2A> a <xref:System.Windows.Forms.BindingSource.DataMember%2A> zjistěte, jakým způsobem jsou datové vazby nakonfigurovány pro zobrazení souvisejících záznamů. Objekt <xref:System.Windows.Forms.BindingSource.DataSource%2A> je namísto na tabulku `CustomersBindingSource` nastaven na možnost <xref:System.Windows.Forms.BindingSource> (`Orders` nadřazené tabulky). Vlastnost <xref:System.Windows.Forms.BindingSource.DataMember%2A> je nastavena na možnost `FK_Orders_Customers`, což je název objektu <xref:System.Data.DataRelation>, který vytváří spojení mezi tabulkami.  
  
## <a name="testing-the-application"></a>Testování aplikace  
  
#### <a name="to-test-the-application"></a>Testování aplikace  
  
1.  Stisknutím klávesy F5 spusťte aplikaci.  
  
2.  Označením různých zákazníků pomocí **CustomersBindingNavigator** ověření jsou zobrazeny správné objednávky v <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="next-steps"></a>Další kroky  
 V závislosti na požadavcích aplikace existuje několik kroků, které můžete provést, chcete-li vytvořit formulář s podrobnostmi. Jedním z vylepšení tohoto návodu by mohlo být:  
  
-   Filtrování záznamů tabulky `Customers` přidáním parametrizace do tabulky `Customers`. Chcete-li to provést, vyberte libovolný ovládací prvek, který zobrazuje data z `Customers` tabulku, klikněte na inteligentní značku a zvolte **přidat dotaz**. Dokončení [dialogové okno Tvůrce kritérií vyhledávání](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d). Další informace najdete v tématu [postupy: Přidání aplikace modelu Windows Forms s parametry dotazu](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
## <a name="see-also"></a>Viz také  
 [Návody k datům](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Okno zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Vytvoření vazby ovládacích prvků Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Přidat nové zdroje dat](../data-tools/add-new-data-sources.md)   
 [TableAdapter – přehled](../data-tools/tableadapter-overview.md)   
 [Postupy: zobrazení souvisejících dat v Windows Forms aplikace](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md)   
 [Přehled komponenty BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)   
 [Přehled ovládacího prvku BindingNavigator](http://msdn.microsoft.com/library/4423eede-f8d1-4d02-822f-5bf8432680d0)