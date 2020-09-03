---
title: Vytvoření databáze SQL pomocí návrháře | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 33b97050f04fd23a9fa3b6c3c641faa5dfe4802f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651061"
---
# <a name="create-a-sql-database-by-using-a-designer"></a>Vytvoření databáze SQL pomocí návrháře
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí sady Visual Studio můžete prozkoumat základní úkoly, jako například přidávání tabulek a definování sloupců, k vytvoření a aktualizaci místního databázového souboru v SQL Server Express LocalDB. Po dokončení tohoto návodu můžete najít pokročilejší možnosti použitím místní databáze jako výchozího bodu pro další návody, které je vyžadují.

 Můžete také vytvořit databázi pomocí SQL Server Management Studio (samostatné stažení) nebo příkazy jazyka Transact-SQL v okně nástroje **Průzkumník objektů systému SQL Server** v aplikaci Visual Studio.

 V tomto návodu budete prozkoumávat následující úlohy:

- [Vytvoření projektu a lokálního databázového souboru](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewSQLDB)

- [Vytváření tabulek, sloupců, primárních klíčů a cizích klíčů](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewTbls)

- [Naplnění tabulek daty](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_Populating)

## <a name="prerequisites"></a>Předpoklady
 Chcete-li dokončit tento návod, ujistěte se, že máte nainstalované nástroje SQL Server Data Tools. V nabídce **zobrazení** by se měla zobrazit **Průzkumník objektů systému SQL Server**. Pokud tam není, přejděte na **Přidat nebo odebrat programy**, klikněte na **Visual Studio 2015**, vyberte **změnit**a zaškrtněte políčko vedle **SQL Server Data Tools**.

## <a name="create-a-project-and-a-local-database-file"></a><a name="BKMK_CreateNewSQLDB"></a> Vytvoření projektu a lokálního databázového souboru

#### <a name="to-create-a-project-and-a-database-file"></a>Vytvoření projektu a databázového souboru

1. Vytvořte model Windows Forms projekt s názvem `SampleDatabaseWalkthrough` .

2. Na panelu nabídek vyberte **projekt**  >  **Přidat novou položku**.

3. V seznamu šablon položek přejděte dolů a vyberte možnost **databáze na základě služby**.

    ![Šablony položek – dialogové okno](../data-tools/media/raddata-vsitemtemplates.png "raddata VSItemTemplates")

4. Pojmenujte databázi **SampleDatabase**a pak vyberte tlačítko **Přidat** .

5. Pokud není okno **zdroje dat** otevřené, otevřete ho tak, že vyberete klávesy SHIFT + ALT + D nebo na panelu nabídek vyberete **Zobrazit**  >  **Další**  >  **zdroje dat**Windows.

6. V okně **zdroje dat** vyberte odkaz **Přidat nový zdroj dat** .

7. V **Průvodci konfigurací zdroje dat**vyberte tlačítko **Další** , čímž přijmete výchozí nastavení, a pak vyberte tlačítko **Dokončit** .

   Otevřením okna vlastností pro databázi lze zobrazit její připojovací řetězec a umístění primárního souboru .mdf databáze. Uvidíte, že soubor databáze je ve složce projektu.

- V aplikaci Visual Studio vyberte možnost **Zobrazit**  >  **Průzkumník objektů systému SQL Server** , pokud toto okno již není otevřeno. Otevřete okno Vlastnosti rozbalením uzlu **datová připojení** , otevřete místní nabídku pro SampleDatabase. mdf a potom vyberte **vlastnosti**.

- Případně můžete vybrat možnost **Zobrazit**  >  **Průzkumník serveru**, pokud už toto okno není otevřené. Otevřete okno Vlastnosti rozbalením uzlu **datová připojení** . Otevřete místní nabídku pro SampleDatabase. mdf a pak vyberte **vlastnosti**.

## <a name="create-tables-columns-primary-keys-and-foreign-keys"></a><a name="BKMK_CreateNewTbls"></a> Vytváření tabulek, sloupců, primárních klíčů a cizích klíčů
 V této části vytvoříte několik tabulek, primární klíč v každé tabulce a několik řádků ukázkových dat. Z dalšího návodu získáte představu o tom, jak se tyto informace mohou zobrazovat v aplikaci. Také vytvoříte cizí klíč k určení toho, jak by mohly záznamy v jedné tabulce odpovídat záznamům v tabulce druhé.

#### <a name="to-create-the-customers-table"></a>Vytvoření tabulky Zákazníci

1. V **Průzkumník serveru** nebo **Průzkumník objektů systému SQL Server**rozbalte uzel **datová připojení** a poté rozbalte uzel **SampleDatabase. mdf** .

2. Otevřete místní nabídku pro **tabulky**a poté vyberte možnost **Přidat novou tabulku**.

     **Návrhář tabulky** otevře a zobrazí mřížku s jedním výchozím řádkem, který představuje jeden sloupec v tabulce, kterou vytváříte. Přidáním řádků do mřížky přidáte další sloupce v tabulce.

3. V mřížce přidejte řádek pro každou z následujících položek:

    |Název sloupce|Datový typ|Povolit hodnoty NULL|
    |-----------------|---------------|-----------------|
    |`CustomerID`|`nchar(5)`|Nepravda (nezaškrtnuto)|
    |`CompanyName`|`nvarchar(50)`|Nepravda (nezaškrtnuto)|
    |`ContactName`|`nvarchar (50)`|Pravda (zaškrtnuto)|
    |`Phone`|`nvarchar (24)`|Pravda (zaškrtnuto)|

4. Otevřete místní nabídku `CustomerID` řádku a pak vyberte **nastavit primární klíč**.

5. Otevřete místní nabídku pro výchozí řádek a pak vyberte **Odstranit**.

6. Pojmenujte tabulku Zákazníci prostřednictvím aktualizace prvního řádku v podokně se skriptem tak, aby odpovídala následující ukázce:

    ```
    CREATE TABLE [dbo].[Customers]
    ```

     Měli byste vidět přibližně toto:

     ![Návrhář tabulky](../data-tools/media/raddata-table-designer.png "Návrhář tabulky raddata")

7. V levém horním rohu **Návrháře tabulky**klikněte na tlačítko **aktualizovat** .

8. V dialogovém okně **Náhled aktualizací databáze** vyberte tlačítko **aktualizace databáze** .

     Vaše změny jsou uloženy do lokálního databázového souboru.

#### <a name="to-create-the-orders-table"></a>Vytvoření tabulky objednávek

1. Přidejte další tabulku a potom přidejte řádek pro každou položku v následující tabulce:

    |Název sloupce|Datový typ|Povolit hodnoty NULL|
    |-----------------|---------------|-----------------|
    |`OrderID`|`int`|Nepravda (nezaškrtnuto)|
    |`CustomerID`|`nchar(5)`|Nepravda (nezaškrtnuto)|
    |`OrderDate`|`datetime`|Pravda (zaškrtnuto)|
    |`OrderQuantity`|`int`|Pravda (zaškrtnuto)|

2. Jako primární klíč nastavte **ČísloObjednávky** a pak výchozí řádek odstraňte.

3. Pojmenujte tabulku Objednávky prostřednictvím aktualizace prvního řádku v podokně se skriptem tak, aby odpovídala následující ukázce:

    ```
    CREATE TABLE [dbo].[Orders]
    ```

4. V levém horním rohu **Návrháře tabulky**klikněte na tlačítko **aktualizovat** .

5. V dialogovém okně **Náhled aktualizací databáze** vyberte tlačítko **aktualizace databáze** .

     Vaše změny jsou uloženy do lokálního databázového souboru.

#### <a name="to-create-a-foreign-key"></a>Vytvoření cizího klíče

1. V kontextovém podokně na pravé straně mřížky otevřete místní nabídku pro **cizí klíče**a pak vyberte **Přidat nový cizí klíč**, jak ukazuje následující obrázek.

     ![Přidání cizího klíče v Návrháři tabulky](../data-tools/media/foreignkey.png "Klíč ForeignKey")

2. Do textového pole, které se zobrazí, nahraďte **ToTable** parametrem `Customers` .

3. V podokně T-SQL aktualizujte poslední řádek tak, aby odpovídal následující ukázce:

    ```
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
    ```

4. V levém horním rohu **Návrháře tabulky**klikněte na tlačítko **aktualizovat** .

5. V dialogovém okně **Náhled aktualizací databáze** vyberte tlačítko **aktualizace databáze** .

     Vaše změny jsou uloženy do lokálního databázového souboru.

## <a name="populate-the-tables-with-data"></a><a name="BKMK_Populating"></a> Naplnění tabulek daty

#### <a name="to-populate-the-tables-with-data"></a>Naplnění tabulek daty

1. V **Průzkumník serveru** nebo **Průzkumník objektů systému SQL Server**rozbalte uzel pro ukázkovou databázi.

2. Otevřete místní nabídku pro uzel **tabulky** , vyberte **aktualizovat**a potom rozbalte uzel **tabulky** .

3. Otevřete místní nabídku tabulky Customers a potom vyberte možnost **Zobrazit data tabulky**.

4. Přidejte jakákoli data pro alespoň tři zákazníky.

     Jako ID zákazníka můžete zadat libovolných pět znaků, ale vyberte alespoň jedno ID takové, které si zapamatujete, abyste je mohli použít později v tomto postupu.

5. Otevřete místní nabídku tabulky Orders a pak vyberte možnost **Zobrazit data tabulky**.

6. Přidejte data pro nejméně tři objednávky.

    > [!IMPORTANT]
    > Přesvědčte se, zda jsou všechna ID objednávek a množství objednávek celými čísly a že každé ID zákazníka odpovídá hodnotě uvedené ve sloupci ID zákazníka v tabulce Zákazníci.

7. Na řádku nabídek vyberte **soubor**  >  **Uložit vše**.

8. Na panelu nabídek vyberte **soubor**  >  **Zavřít řešení**.

    > [!NOTE]
    > Jako nejvhodnější postup můžete zálohovat soubor databáze, který jste právě vytvořili, zkopírováním a vložením kopie do jiného umístění nebo pojmenováním kopie jiným názvem.

## <a name="next-steps"></a>Další kroky
 Teď, když máte místní databázový soubor s ukázkovými daty, můžete dokončit kterýkoli z návodů, které ukazují úlohy databáze.
