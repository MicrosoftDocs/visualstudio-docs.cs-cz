---
title: Vytvoření formuláře Windows pro vyhledávání dat | Microsoft Docs
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
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 81980f38cbd8fb595530cc52b2cf32056feb43a7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670064"
---
# <a name="create-a-windows-form-to-search-data"></a>Vytvoření formuláře Windows k vyhledávání dat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Běžným scénářem použití je zobrazení vybraných dat na formuláři. Například můžete chtít zobrazit objednávky konkrétního zákazníka nebo podrobnosti konkrétního objednávky. V tomto scénáři uživatel zadá informace do formuláře a následně se spustí dotaz se vstupem uživatele jako s parametrem. To znamená, že data jsou vybrána na základě parametrizovaného dotazu. Dotaz vrátí pouze data, která splňují kritéria zadaná uživatelem. Tento návod ukazuje, jak vytvořit dotaz, který vrací zákazníky v určitém městě, a upravit uživatelské rozhraní tak, aby uživatelé mohli zadat jméno města a stisknout tlačítko pro spuštění dotazu.

 Použití parametrizovaných dotazů vám pomůže zajistit efektivitu vaší aplikace tím, že umožňuje databázi provádět práci, která je nejlepší, a rychle filtrovat záznamy. Na rozdíl od toho, pokud požadujete celou databázovou tabulku, přenesete ji přes síť a pak pomocí aplikační logiky vyhledejte požadované záznamy, aplikace může být pomalá a neefektivní.

 Můžete přidat parametrizované dotazy do libovolného TableAdapter (a ovládací prvky pro přijímání hodnot parametrů a spuštění dotazu) pomocí dialogového okna **Tvůrce kritérií hledání** . Otevřete dialogové okno tak, že v nabídce **data** vyberete příkaz **Přidat dotaz** (nebo na libovolnou inteligentní značku TableAdapter).

 Úlohy, které jsou znázorněné v tomto návodu, zahrnují:

- Vytváří se nový projekt aplikace model Windows Forms.

- Vytvoření a konfigurace zdroje dat v aplikaci pomocí průvodce **konfigurací zdroje dat** .

- Nastavení typu přetažení položek v okně **zdroje dat** .

- Vytváření ovládacích prvků, které zobrazují data přetažením položek z okna **zdroje dat** do formuláře.

- Přidání ovládacích prvků pro zobrazení dat ve formuláři.

- Dokončuje se dialogové okno **Tvůrce kritérií hledání** .

- Zadáním parametrů do formuláře a spuštěním parametrizovaného dotazu.

## <a name="prerequisites"></a>Požadavky
 Aby bylo možné dokončit tento návod, potřebujete:

- Přístup k ukázkové databázi Northwind.

## <a name="create-the-windows-application"></a>Vytvoření aplikace pro Windows
 Prvním krokem je vytvoření **aplikace pro Windows**. Přiřazení názvu k projektu je v tomto kroku volitelné, ale tady se mu přiřadí název, protože ho uložíte později.

#### <a name="to-create-the-new-windows-application-project"></a>Vytvoření nového projektu aplikace pro systém Windows

1. V nabídce **soubor** vytvořte nový projekt.

2. Pojmenujte projekt `WindowsSearchForm`.

3. Vyberte **aplikace systému Windows** a klikněte na tlačítko **OK**.

     Projekt **WindowsSearchForm** je vytvořen a přidán do **Průzkumník řešení**.

## <a name="create-the-data-source"></a>Vytvoření zdroje dat
 Tento krok vytvoří zdroj dat z databáze pomocí průvodce **konfigurací zdroje dat** . Abyste mohli vytvořit připojení, musíte mít přístup k ukázkové databázi Northwind. Informace o nastavení ukázkové databáze Northwind najdete v tématu [Instalace ukázkových databází SQL Server](../data-tools/install-sql-server-sample-databases.md).

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

8. Vyberte tabulku **Customers (zákazníci** ) a pak klikněte na **Dokončit**.

     **NorthwindDataSet** je přidán do projektu a tabulka **Customers (zákazníci** ) se zobrazí v okně **zdroje dat** .

## <a name="create-the-form"></a>Vytvořit formulář
 Můžete vytvořit ovládací prvky vázané na data přetažením položek z okna **zdroje dat** do formuláře.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Vytvoření ovládacích prvků vázaných na data ve formuláři

1. Rozbalte uzel **zákazníci** v okně **zdroje dat** .

2. Přetáhněte uzel **zákazníci** z okna **zdroje dat** do formuláře.

     Na formuláři se zobrazí <xref:System.Windows.Forms.DataGridView> a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů. V zásobníku komponent se zobrazí [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> a <xref:System.Windows.Forms.BindingNavigator>.

## <a name="addparameterization-search-functionality-to-the-query"></a>Addparameterization (funkce hledání) na dotaz
 Klauzuli WHERE můžete přidat k původnímu dotazu pomocí dialogového okna **Tvůrce kritérií hledání** .

#### <a name="to-create-a-parameterized-query-and-controls-to-enter-the-parameters"></a>Vytvoření parametrizovaného dotazu a ovládacích prvků pro zadání parametrů

1. Vyberte ovládací prvek <xref:System.Windows.Forms.DataGridView> a v nabídce **data** zvolte **Přidat dotaz** .

2. Do pole **nový název dotazu** v dialogovém okně **Tvůrce kritérií hledání** zadejte `FillByCity`.

3. Přidejte `WHERE City = @City` do dotazu v oblasti **textu dotazu** .

     Dotaz by měl vypadat přibližně takto:

     `SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax`

     `FROM Customers`

     `WHERE City = @City`

    > [!NOTE]
    > Přístup ke zdrojům dat a jejich OLE DB používají otazník ('? ') k označení parametrů, takže klauzule WHERE by vypadala takto: `WHERE City = ?`.

4. Kliknutím na tlačítko **OK** zavřete dialogové okno **Tvůrce kritérií hledání** .

     Do formuláře se přidá **FillByCityToolStrip** .

## <a name="testing-the-application"></a>Testování aplikace
 Po spuštění aplikace se otevře formulář, který je připravený k převzetí parametru jako vstupu.

#### <a name="to-test-the-application"></a>Testování aplikace

1. Stisknutím klávesy F5 spusťte aplikaci.

2. Do textového pole **City** zadejte **Londýn** a pak klikněte na **FillByCity**.

     Datová mřížka je naplněna zákazníky, kteří splňují kritéria. V tomto příkladu datová mřížka zobrazuje pouze zákazníky, kteří mají ve sloupci **City** hodnotu **Londýn** .

## <a name="next-steps"></a>Další kroky
 V závislosti na požadavcích vaší aplikace existuje několik kroků, které můžete chtít provést po vytvoření parametrizovaného formuláře. Mezi vylepšení, která je možné pro tento návod provést, patří:

- Přidávání ovládacích prvků, které zobrazují související data.

- Úprava datové sady pro přidání nebo odebrání databázových objektů. Další informace najdete v tématu [Vytvoření a konfigurace datových sad](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Viz také
 [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
