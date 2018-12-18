---
title: Vytvoření formuláře Windows k vyhledávání dat | Dokumentace Microsoftu
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
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e42c86cf94115d317eb20df66f4cef005e05eba9
ms.sourcegitcommit: c9a01c599ce19a5845605b3b28c0229fd0abb93f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281794"
---
# <a name="create-a-windows-form-to-search-data"></a>Vytvoření formuláře Windows k vyhledávání dat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Běžný scénář, kdy aplikace se má zobrazit vybraná data ve formuláři. Můžete například chtít zobrazujících objednávky pro konkrétního zákazníka nebo podrobnosti o určitém pořadí. V tomto scénáři uživatel zadá informace do formátu, a pak je dotaz proveden se vstupem uživatele jako parametr; To znamená data se určí parametrický dotaz. Dotaz vrátí pouze data, která splňuje kritéria zadaná uživatelem. Tento návod ukazuje, jak vytvořit dotaz, který vrátí zákazníky v konkrétním městě a upravte uživatelské rozhraní, aby uživatelé můžete zadat název města a kliknutím na tlačítko Spustit dotaz.  
  
 Použití parametrizovaných dotazů pomáhá zajištění efektivního aplikace tím, že databáze je nejvhodnější při práci – rychle filtrování záznamů. Naopak pokud vyžádáte tabulku celé databáze, přenos přes síť a pak použít k vyhledání záznamy, které chcete aplikaci logiky, aplikace může být pomalé a neefektivní.  
  
 Parametrizované dotazy můžete přidat všechny třídy TableAdapter (a ovládací prvky přijmout hodnoty parametrů a spusťte dotaz), pomocí **Tvůrce kritérií vyhledávání** dialogové okno. Otevřete dialogové okno tak, že vyberete **přidat dotaz** příkaz **Data** nabídce (nebo na libovolné klíčové slovo inteligentní TableAdapter).  
  
 Úlohy v tomto návodu zahrnují:  
  
-   Vytvoření nového projektu aplikace Windows Forms.  
  
-   Vytvoření a konfigurace zdroje dat ve vaší aplikaci se **konfigurace zdroje dat** průvodce.  
  
-   Typ rozevírací položky v nastavení **zdroje dat** okna.  
  
-   Vytváření ovládacích prvků, které data zobrazit přetažením položek z **zdroje dat** okna do formuláře.  
  
-   Přidání ovládacích prvků pro zobrazení dat ve formuláři.  
  
-   Dokončuje **Tvůrce kritérií vyhledávání** dialogové okno.  
  
-   Zadat parametry do formuláře a provádění parametrický dotaz.  
  
## <a name="prerequisites"></a>Požadavky  
 Pokud chcete dokončit tento návod, potřebujete:  
  
-   Přístup k ukázkové databázi Northwind.  
  
## <a name="create-the-windows-application"></a>Vytvoření aplikace Windows  
 Prvním krokem je vytvoření **aplikace Windows**. Přiřazení názvu projektu je volitelné v tomto kroku, ale budete jí přiřadit názvu na toto vzhledem k tomu, že ho budete později uložit.  
  
#### <a name="to-create-the-new-windows-application-project"></a>Vytvoření nového projektu aplikace pro systém Windows  
  
1.  Z **souboru** nabídky, vytvořte nový projekt.  
  
2.  Pojmenujte projekt `WindowsSearchForm`.  
  
3.  Vyberte **aplikace Windows** a klikněte na tlačítko **OK**.  
  
     **WindowsSearchForm** projekt je vytvořen a přidán do **Průzkumníka řešení**.  
  
## <a name="create-the-data-source"></a>Vytvoření zdroje dat  
 Tento krok vytváří zdroj dat z databáze pomocí **konfigurace zdroje dat** průvodce. Musíte mít přístup k ukázkové databázi Northwind k vytvoření připojení. Informace o instalaci ukázkové databáze Northwind naleznete v tématu [instalace SQL serveru, ukázkové databáze](../data-tools/install-sql-server-sample-databases.md).  
  
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
  
8.  Vyberte **zákazníkům** tabulku a pak klikněte na tlačítko **Dokončit**.  
  
     **NorthwindDataSet** se přidá do vašeho projektu a **zákazníkům** tabulky se zobrazí v **zdroje dat** okna.  
  
## <a name="create-the-form"></a>Vytvoření formuláře  
 Můžete vytvořit ovládací prvky vázané na data přetažením položek z **zdroje dat** okna do formuláře.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Vytvoření ovládacích prvků vázaných na data ve formuláři  
  
1.  Rozbalte **zákazníkům** uzlu **zdroje dat** okno.  
  
2.  Přetáhněte **zákazníkům** uzlu z **zdroje dat** okna do formuláře.  
  
     A <xref:System.Windows.Forms.DataGridView> a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů se zobrazí ve formuláři. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, a <xref:System.Windows.Forms.BindingNavigator> zobrazují v panelu komponent.  
  
## <a name="addparameterization-search-functionality-to-the-query"></a>Addparameterization (funkce hledání) do dotazu  
 Můžete přidat klauzuli WHERE dotazu na původní pomocí **Tvůrce kritérií vyhledávání** dialogové okno.  
  
#### <a name="to-create-a-parameterized-query-and-controls-to-enter-the-parameters"></a>Chcete-li vytvořit parametrický dotaz a ovládací prvky k zadání parametrů  
  
1.  Vyberte <xref:System.Windows.Forms.DataGridView> ovládací prvek a klikněte na tlačítko **přidat dotaz** na **Data** nabídky.  
  
2.  Typ `FillByCity` v **nový název dotazu** oblast na **Tvůrce kritérií vyhledávání** dialogové okno.  
  
3.  Přidat `WHERE City = @City` do dotazu v **Text dotazu** oblasti.  
  
     Dotaz by měl vypadat přibližně takto:  
  
     `SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax`  
  
     `FROM Customers`  
  
     `WHERE City = @City`  
  
    > [!NOTE]
    >  Přístup a technologie OLE DB zdroje dat používat otazník ("?") k označení parametrů, takže v klauzuli WHERE bude vypadat takto: `WHERE City = ?`.  
  
4.  Klikněte na tlačítko **OK** zavřete **Tvůrce kritérií vyhledávání** dialogové okno.  
  
     A **FillByCityToolStrip** je přidán do formuláře.  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Spuštění aplikace se otevře chtějí posunout parametr jako vstup formuláře.  
  
#### <a name="to-test-the-application"></a>Testování aplikace  
  
1.  Stisknutím klávesy F5 spusťte aplikaci.  
  
2.  Typ **Londýn** do **Město** textové pole a pak klikněte na tlačítko **FillByCity**.  
  
     Datové mřížce se vyplní zákazníky, kteří splňují kritéria. V tomto příkladu datové mřížky se zobrazí pouze zákazníci, kteří mají hodnotu **Londýn** v jejich **Město** sloupce.  
  
## <a name="next-steps"></a>Další kroky  
 V závislosti na požadavcích aplikace existuje několik kroků, které můžete provést po vytvoření parametrizovaného formuláře. Mezi vylepšení, která je možné pro tento návod provést, patří:  
  
-   Přidání ovládacích prvků, které zobrazují související data. Další informace najdete v tématu [postupy: zobrazení souvisejících dat ve formulářové aplikaci Windows](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
-   Úpravy datové sady pro přidání nebo odebrání databázové objekty. Další informace najdete v tématu [vytvoření a konfigurace datové sady](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

