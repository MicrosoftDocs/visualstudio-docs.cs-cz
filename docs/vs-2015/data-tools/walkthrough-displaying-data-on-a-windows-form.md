---
title: 'Návod: Zobrazování dat ve formuláři Windows | Dokumentace Microsoftu'
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
- Windows applications, displaying data
- data binding, Windows Forms
- data [Visual Studio], displaying on Windows Forms
- forms, displaying data
ms.assetid: f6e08c2c-c792-43de-adf3-3e52c0100225
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: f623f639458a9f5c9c055b5d6de384f6fd39cad1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201198"
---
# <a name="walkthrough-displaying-data-on-a-windows-form"></a>Návod: Zobrazování dat ve formuláři Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jedním z nejběžnějších scénářů při vývoji aplikace se zobrazí data na formulář v nástrojích pro aplikace založené na Windows. Data můžete zobrazit ve formuláři přetažením položek z [okna zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) do formuláře. Tento návod vytvoří jednoduchý formulář, který se zobrazí data z jedné tabulky v několika jednotlivých ovládacích prvků. V tomto příkladu `Customers` tabulky z ukázkové databáze Northwind.  
  
 Úlohy v tomto návodu zahrnují:  
  
-   Vytvoření nového **aplikace Windows** projektu.  
  
-   Vytvoření a konfigurace datové sady [Průvodce konfigurací zdroje dat](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Výběr ovládacího prvku, aby se ve formuláři vytvořen při přetažení položky z **zdroje dat** okna. Další informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Vytvoření ovládacího prvku vázané na data přetažením položek z **zdroje dat** okna do formuláře.  
  
## <a name="prerequisites"></a>Požadavky  
 Pokud chcete dokončit tento návod, potřebujete:  
  
-   Přístup k ukázkové databázi Northwind. Další informace najdete v tématu [postupy: Instalace ukázkových databází](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-the-windows-application"></a>Vytvoření aplikace pro Windows  
 Prvním krokem je vytvoření **aplikace Windows** projektu.  
  
#### <a name="to-create-the-new-windows-application-project"></a>Vytvoření nového projektu aplikace pro systém Windows  
  
1.  Z **souboru** nabídky, vytvořte nový projekt.  
  
2.  Pojmenujte projekt `DisplayingDataonaWindowsForm`.  
  
3.  Vyberte **aplikace Windows** a klikněte na tlačítko **OK**. Další informace najdete v tématu [klientské aplikace](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **DisplayingDataonaWindowsForm** projekt je vytvořen a přidán do **Průzkumníka řešení**.  
  
## <a name="creating-the-data-source"></a>Vytvoření zdroje dat  
 Tento krok vytváří zdroj dat pomocí **Průvodce konfigurací zdroje dat** na základě `Customers` tabulky v ukázkové databázi Northwind. Musíte mít přístup k ukázkové databázi Northwind k vytvoření připojení. Informace o instalaci ukázkové databáze Northwind naleznete v tématu [postupy: Instalace ukázkových databází](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat  
  
1.  Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.  
  
2.  V **zdroje dat** okně **přidat nový zdroj dat** spustit **Průvodce konfigurací zdroje dat**.  
  
3.  Vyberte **databáze** na **zvolte typ zdroje dat** stránce a potom klikněte na tlačítko **Další**.  
  
4.  Na **vyberte datové připojení** stránka provádění, jednu z následujících akcí:  
  
    -   Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.  
  
         -nebo-  
  
    -   Vyberte **nové připojení** ke spuštění **přidat/změnit připojení** dialogové okno...  
  
5.  Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí důvěrných osobních údajů a pak klikněte na tlačítko **Další**.  
  
6.  Klikněte na tlačítko **Další** na **uložit připojovací řetězec do konfiguračního souboru aplikace** stránky.  
  
7.  Rozbalte **tabulky** uzlu **zvolte vaše databázové objekty** stránky.  
  
8.  Vyberte **zákazníkům** tabulku a pak klikněte na tlačítko **Dokončit**.  
  
     **NorthwindDataSet** se přidá do vašeho projektu a **zákazníkům** tabulky se zobrazí v **zdroje dat** okna.  
  
## <a name="setting-the-controls-to-be-created"></a>Nastavení ovládacích prvků, který se má vytvořit  
 V tomto návodu budou data v **podrobnosti** rozložení, ve kterém se zobrazí data v jednotlivých ovládacích prvků. (Alternativním přístupem je výchozí **mřížky** rozložení, ve kterém se zobrazí data v <xref:System.Windows.Forms.DataGridView> ovládacího prvku.)  
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Chcete-li nastavit typ přetažení pro položky v okně zdrojů dat.  
  
1.  Rozbalte **zákazníkům** uzlu **zdroje dat** okno.  
  
2.  Změňte typ přetažení **zákazníkům** tabulky **podrobnosti** tak, že vyberete **podrobnosti** z rozevíracího seznamu na **zákazníkům** uzlu. Další informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
3.  Změnit **CustomerID** ve sloupci typ přetažení na popisek tak, že vyberete **popisek** ze seznamu ovládacího prvku na **CustomerID** uzlu.  
  
## <a name="creating-the-form"></a>Vytvoření formuláře  
 Vytvoření ovládacích prvků vázaných na data přetažením položek z **zdroje dat** okna do formuláře.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Vytvoření ovládacích prvků vázaných na data ve formuláři  
  
-   Přetáhněte hlavní **zákazníkům** uzlu z **zdroje dat** okna do formuláře.  
  
     Ovládací prvky vázaných dat pomocí popisků se zobrazí ve formuláři, spolu s pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, a <xref:System.Windows.Forms.BindingNavigator> zobrazují v panelu komponent.  
  
## <a name="testing-the-application"></a>Testování aplikace  
  
#### <a name="to-run-the-application"></a>Ke spuštění aplikace  
  
-   Stiskněte klávesu F5.  
  
-   Procházení záznamů pomocí <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku.  
  
## <a name="next-steps"></a>Další kroky  
 V závislosti na požadavcích aplikace existuje několik kroků, které můžete provést po vytvoření formuláře Windows vázané na data. Mezi vylepšení, která je možné pro tento návod provést, patří:  
  
-   Přidání vyhledávací funkce do formuláře. Další informace najdete v tématu [postupy: Přidání aplikace modelu Windows Forms s parametry dotazu](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
-   Přidání funkce k odeslání aktualizací zpět do databáze. Další informace najdete v tématu [návod: ukládání dat do databáze (jediná tabulka)](http://msdn.microsoft.com/library/68befa96-7463-43e8-abcf-dc2f42ccd53d).  
  
-   Přidávání `Orders` tabulky do datové sady výběrem **konfigurace datové sady pomocí průvodce** v rámci **zdroje dat** okna. Potom můžete přidat ovládací prvky zobrazující související data přetažením **objednávky** uzlu (níže jednu **Fax** sloupce v rámci **zákazníkům** tabulky) do formuláře. Další informace najdete v tématu [postupy: zobrazení souvisejících dat ve formulářové aplikaci Windows](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Viz také  
 [Návody k datům](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Vytvoření vazby ovládacích prvků Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Přidat nové zdroje dat](../data-tools/add-new-data-sources.md)   
 [TableAdapter – přehled](../data-tools/tableadapter-overview.md)