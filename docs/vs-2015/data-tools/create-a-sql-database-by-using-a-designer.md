---
title: Vytvoření databáze SQL pomocí návrháře | Dokumentace Microsoftu
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
- SQL Server Express
- local data
- LocalDB
- SQLEXPRESS
- data [Visual Studio], Local data
- SQL Express
- data [Visual Studio], walkthroughs
- databases, creating
- database files, creating
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
caps.latest.revision: 54
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 0ef261ec4ea803dcfc42b6151a5c828d5b03811a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49860325"
---
# <a name="create-a-sql-database-by-using-a-designer"></a>Vytvoření databáze SQL pomocí návrháře
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Můžete zkoumat základní úkoly, jako je například přidávání tabulek a definování sloupců, pomocí sady Visual Studio k vytvoření a aktualizaci souboru místní databáze v serveru SQL Server Express LocalDB. Po dokončení tohoto návodu můžete najít pokročilejší možnosti použitím místní databáze jako výchozího bodu pro další návody, které je vyžadují.  
  
 Můžete také vytvořit databázi pomocí SQL Server Management Studio (samostatný soubor ke stažení) nebo pomocí příkazů jazyka Transact-SQL v **Průzkumník objektů systému SQL Server** panelu nástrojů v sadě Visual Studio.  
  
 V tomto návodu budete prozkoumávat následující úlohy:  
  
-   [Vytvoření projektu a lokálního databázového souboru](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewSQLDB)  
  
-   [Vytvoření tabulek, sloupců, primárních klíčů a cizích klíčů](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewTbls)  
  
-   [Naplnění tabulek daty](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_Populating)  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu, ujistěte se, že máte nainstalovaný SQL Server Data Tools. Na **zobrazení** nabídky, měli byste vidět **Průzkumník objektů systému SQL Server**. Pokud tam není, přejděte na **přidat nebo odebrat programy**, klikněte na tlačítko **Visual Studio 2015**vyberte **změnu**a zaškrtněte políčko vedle položky **SQL Server Data Tools**.  
  
##  <a name="BKMK_CreateNewSQLDB"></a> Vytvoření projektu a lokálního databázového souboru  
  
#### <a name="to-create-a-project-and-a-database-file"></a>Vytvoření projektu a databázového souboru  
  
1. Vytvoření projektu Windows Forms s názvem `SampleDatabaseWalkthrough`.  
  
2. Na panelu nabídek vyberte **projektu** > **přidat novou položku**.  
  
3. V seznamu šablon položek, přejděte dolů a vyberte **databáze založené na službě**.  
  
    ![Dialogové okno šablony položky](../data-tools/media/raddata-vsitemtemplates.png "raddata VSItemTemplates")  
  
4. Pojmenujte databázi **SampleDatabase**a pak vyberte **přidat** tlačítko.  
  
5. Pokud **zdroje dat** okno není otevřeno, otevřete ho tak, že vyberete klávesy Shift + Alt + D nebo na panelu nabídek, výběrem **zobrazení** > **ostatní Windows**  >  **Zdroje dat**.  
  
6. V **zdroje dat** okna, vyberte **přidat nový zdroj dat** odkaz.  
  
7. V **Průvodce konfigurací zdroje dat**, vyberte **Další** čtyřikrát přijměte výchozí nastavení a potom vyberte **Dokončit** tlačítko.  
  
   Otevřením okna vlastností pro databázi lze zobrazit její připojovací řetězec a umístění primárního souboru .mdf databáze. Uvidíte, že databázový soubor je ve složce projektu.  
  
-   V sadě Visual Studio, vyberte **zobrazení** > **Průzkumník objektů systému SQL Server** Pokud toto okno ještě není otevřený. Otevřete okno vlastností rozbalením **datová připojení** uzel, otevřete místní nabídku pro soubor SampleDatabase.mdf a pak vyberete **vlastnosti**.  
  
-   Alternativně můžete vybrat **zobrazení** > **Průzkumníka serveru**, pokud toto okno ještě není otevřený. Otevřete okno vlastností rozbalením **datová připojení** uzlu. Otevřete místní nabídku pro soubor SampleDatabase.mdf a pak vyberte **vlastnosti**.  
  
##  <a name="BKMK_CreateNewTbls"></a> Vytvoření tabulek, sloupců, primárních klíčů a cizích klíčů  
 V této části vytvoříte několik tabulek, primární klíč v každé tabulce a několik řádků ukázkových dat. Z dalšího návodu získáte představu o tom, jak se tyto informace mohou zobrazovat v aplikaci. Také vytvoříte cizí klíč k určení toho, jak by mohly záznamy v jedné tabulce odpovídat záznamům v tabulce druhé.  
  
#### <a name="to-create-the-customers-table"></a>Vytvoření tabulky Zákazníci  
  
1.  V **Průzkumníka serveru** nebo **Průzkumník objektů systému SQL Server**, rozbalte **datová připojení** uzel a potom rozbalte **SampleDatabase.mdf**uzlu.  
  
2.  Otevřete místní nabídku pro **tabulky**a pak vyberte **přidat novou tabulku**.  
  
     **Návrháře tabulky** otevře a zobrazí mřížku s jedním výchozím řádkem, který představuje jeden sloupec v tabulce, kterou vytváříte. Přidáním řádků do mřížky přidáte další sloupce v tabulce.  
  
3.  V mřížce přidejte řádek pro každou z následujících položek:  
  
    |Název sloupce|Datový typ|Povolit hodnoty NULL|  
    |-----------------|---------------|-----------------|  
    |`CustomerID`|`nchar(5)`|Nepravda (nezaškrtnuto)|  
    |`CompanyName`|`nvarchar(50)`|Nepravda (nezaškrtnuto)|  
    |`ContactName`|`nvarchar (50)`|Pravda (zaškrtnuto)|  
    |`Phone`|`nvarchar (24)`|Pravda (zaškrtnuto)|  
  
4.  Otevřete místní nabídku `CustomerID` řádku a potom vyberte **nastavit primární klíč**.  
  
5.  Otevřete místní nabídku pro výchozí řádek a pak vyberte **odstranit**.  
  
6.  Pojmenujte tabulku Zákazníci prostřednictvím aktualizace prvního řádku v podokně se skriptem tak, aby odpovídala následující ukázce:  
  
    ```  
    CREATE TABLE [dbo].[Customers]  
    ```  
  
     By měl vypadat přibližně takto:  
  
     ![Tabulka návrháře](../data-tools/media/raddata-table-designer.png "raddata Návrhář tabulky")  
  
7.  V levém horním rohu **návrháře tabulky**, vyberte **aktualizace** tlačítko.  
  
8.  V **náhled aktualizací databáze** dialogové okno, vyberte **aktualizace databáze** tlačítko.  
  
     Vaše změny jsou uloženy do lokálního databázového souboru.  
  
#### <a name="to-create-the-orders-table"></a>Vytvoření tabulky objednávek  
  
1.  Přidejte další tabulku a potom přidejte řádek pro každou položku v následující tabulce:  
  
    |Název sloupce|Datový typ|Povolit hodnoty NULL|  
    |-----------------|---------------|-----------------|  
    |`OrderID`|`int`|Nepravda (nezaškrtnuto)|  
    |`CustomerID`|`nchar(5)`|Nepravda (nezaškrtnuto)|  
    |`OrderDate`|`datetime`|Pravda (zaškrtnuto)|  
    |`OrderQuantity`|`int`|Pravda (zaškrtnuto)|  
  
2.  Nastavte **OrderID** jako primární klíč a potom odstraňte výchozí řádek.  
  
3.  Pojmenujte tabulku Objednávky prostřednictvím aktualizace prvního řádku v podokně se skriptem tak, aby odpovídala následující ukázce:  
  
    ```  
    CREATE TABLE [dbo].[Orders]  
    ```  
  
4.  V levém horním rohu **návrháře tabulky**, vyberte **aktualizace** tlačítko.  
  
5.  V **náhled aktualizací databáze** dialogové okno, vyberte **aktualizace databáze** tlačítko.  
  
     Vaše změny jsou uloženy do lokálního databázového souboru.  
  
#### <a name="to-create-a-foreign-key"></a>Vytvoření cizího klíče  
  
1.  V kontextovém podokně na pravé straně tabulky, otevřete místní nabídku pro **cizí klíče**a pak vyberte **přidat nový cizí klíč**, jak je vidět na následujícím obrázku.  
  
     ![Přidání cizí klíče v Návrháři tabulek](../data-tools/media/foreignkey.png "cizí klíč")  
  
2.  V textovém poli nahraďte **ToTable** s `Customers`.  
  
3.  V podokně T-SQL aktualizujte poslední řádek tak, aby odpovídala následující ukázce:  
  
    ```  
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])  
    ```  
  
4.  V levém horním rohu **návrháře tabulky**, vyberte **aktualizace** tlačítko.  
  
5.  V **náhled aktualizací databáze** dialogové okno, vyberte **aktualizace databáze** tlačítko.  
  
     Vaše změny jsou uloženy do lokálního databázového souboru.  
  
##  <a name="BKMK_Populating"></a> Naplnění tabulek daty  
  
#### <a name="to-populate-the-tables-with-data"></a>Naplnění tabulek daty  
  
1.  V **Průzkumníka serveru** nebo **Průzkumník objektů systému SQL Server**, rozbalte uzel pro vzorovou databázi.  
  
2.  Otevřete místní nabídku **tabulky** uzlu, vyberte **aktualizovat**a potom rozbalte **tabulky** uzlu.  
  
3.  Otevřete místní nabídku tabulky Zákazníci a zvolte **zobrazit Data tabulky**.  
  
4.  Přidejte jakákoli data pro alespoň tři zákazníky.  
  
     Jako ID zákazníka můžete zadat libovolných pět znaků, ale vyberte alespoň jedno ID takové, které si zapamatujete, abyste je mohli použít později v tomto postupu.  
  
5.  Otevřete místní nabídku tabulky objednávky a pak vyberte **zobrazit Data tabulky**.  
  
6.  Přidejte data pro nejméně tři objednávky.  
  
    > [!IMPORTANT]
    >  Přesvědčte se, zda jsou všechna ID objednávek a množství objednávek celými čísly a že každé ID zákazníka odpovídá hodnotě uvedené ve sloupci ID zákazníka v tabulce Zákazníci.  
  
7.  Na panelu nabídek vyberte **souboru** > **Uložit vše**.  
  
8.  Na panelu nabídek vyberte **souboru** > **zavřít řešení**.  
  
    > [!NOTE]
    >  Jako nejvhodnější postup můžete zálohovat soubor databáze, který jste právě vytvořili, zkopírováním a vložením kopie do jiného umístění nebo pojmenováním kopie jiným názvem.  
  
## <a name="next-steps"></a>Další kroky  
 Teď, když máte místní databázový soubor s ukázkovými daty, můžete dokončit některé názorné postupy, které popisují databázové úlohy.

