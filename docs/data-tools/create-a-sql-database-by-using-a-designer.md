---
title: Vytvoření souboru databáze a Návrhář tabulky
description: Kurz, který popisuje, jak přidat tabulky a cizí klíče k databázi pomocí Návrháře tabulky v sadě Visual Studio. Také ukazuje, jak přidat data prostřednictvím grafického rozhraní.
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- database tables, creating
- database files, creating
- table designer
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c071daeaa1ffe10aa9de995b375e33b76b358da7
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159864"
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>Vytvoření databáze a přidání tabulek v sadě Visual Studio

Visual Studio můžete použít k vytvoření a aktualizaci souboru místní databáze v serveru SQL Server Express LocalDB. Můžete také vytvořit databázi spuštěním příkazů jazyka Transact-SQL v **Průzkumník objektů systému SQL Server** panelu nástrojů v sadě Visual Studio. V tomto tématu vytvoříme *.mdf* a přidejte tabulkami a klíči pomocí Návrháře tabulky.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu, musíte mít nepovinný **ukládání a zpracování dat** úlohy nainstalovaná v sadě Visual Studio. Ho Pokud chcete nainstalovat, otevřete **instalační program sady Visual Studio** a zvolte **úlohy** kartu. V části **Web a Cloud**, zvolte **ukládání a zpracování dat**. Zvolte **změnit** tlačítko pro přidání úlohy ke službě Visual Studio.

## <a name="create-a-project-and-a-local-database-file"></a>Vytvoření projektu a lokálního databázového souboru

1. Vytvoření projektu Windows Forms s názvem **SampleDatabaseWalkthrough**.

2. Na panelu nabídek vyberte **projektu** > **přidat novou položku**.

3. V seznamu šablon položek, přejděte dolů a vyberte **databáze založené na službě**.

     ![Dialogové okno šablon položek](../data-tools/media/raddata-vsitemtemplates.png)

4. Pojmenujte databázi **SampleDatabase**a pak vyberte **přidat** tlačítko.

### <a name="add-a-data-source"></a>Přidání zdroje dat

1. Pokud **zdroje dat** okno není otevřeno, otevřete ho stisknutím kombinace kláves **Shift**+**Alt**+**D** nebo jeho výběru **Zobrazení** > **ostatní Windows** > **zdroje dat** na řádku nabídek.

1. V **zdroje dat** okna, vyberte **přidat nový zdroj dat** odkaz.

   **Průvodce konfigurací zdroje dat** otevře.

1. Na **zvolte typ zdroje dat** zvolte **databáze** a klikněte na tlačítko **Další**.

1. Na **vyberte databázový Model** zvolte **Další** přijměte výchozí nastavení (datová sada).

1. Na **vyberte datové připojení** stránky, vyberte **SampleDatabase.mdf** souboru v rozevíracím seznamu a klikněte na tlačítko **Další**.

1. Na **uložit připojovací řetězec do konfiguračního souboru aplikace** zvolte **Další**.

1. Jeden **zvolte vaše databázové objekty** stránky, zobrazí se zpráva, že databáze neobsahuje žádné objekty. Zvolte **Dokončit**.

### <a name="view-properties-of-the-data-connection"></a>Zobrazit vlastnosti datového připojení

Připojovací řetězec můžete zobrazit *SampleDatabase.mdf* souboru tak, že otevřete okno Vlastnosti datového připojení:

- V sadě Visual Studio, vyberte **zobrazení** > **Průzkumník objektů systému SQL Server** Pokud toto okno ještě není otevřený. Otevřete okno vlastností rozbalením **datová připojení** uzel, otevřete místní nabídku pro *SampleDatabase.mdf*a pak vyberete **vlastnosti**.

- Alternativně můžete vybrat **zobrazení** > **Průzkumníka serveru**, pokud toto okno ještě není otevřený. Otevřete okno vlastností rozbalením **datová připojení** uzlu. Otevřete místní nabídku pro *SampleDatabase.mdf*a pak vyberte **vlastnosti**.

## <a name="create-tables-and-keys-by-using-table-designer"></a>Vytvoření tabulky a klíče pomocí Návrháře tabulky

V této části vytvoříte dvě tabulky, primární klíč v každé tabulce a několik řádků ukázkových dat. Také vytvoříte cizí klíč k určení, jak záznamy v jedné tabulce odpovídat záznamům v druhé tabulce.

### <a name="create-the-customers-table"></a>Vytvoření tabulky Zákazníci

1. V **Průzkumníka serveru** nebo **Průzkumník objektů systému SQL Server**, rozbalte **datová připojení** uzel a potom rozbalte **SampleDatabase.mdf**uzlu.

2. Otevřete místní nabídku pro **tabulky**a pak vyberte **přidat novou tabulku**.

     **Návrháře tabulky** otevře a zobrazí mřížku s jedním výchozím řádkem, který představuje jeden sloupec v tabulce, kterou vytváříte. Přidáním řádků do mřížky přidáte další sloupce v tabulce.

3. V mřížce přidejte řádek pro každou z následujících položek:

    |Název sloupce|Datový typ|Povolit hodnoty NULL|
    |-----------------|---------------|-----------------|
    |`CustomerID`|`nchar(5)`|Nepravda (nezaškrtnuto)|
    |`CompanyName`|`nvarchar(50)`|Nepravda (nezaškrtnuto)|
    |`ContactName`|`nvarchar (50)`|Pravda (zaškrtnuto)|
    |`Phone`|`nvarchar (24)`|Pravda (zaškrtnuto)|

4. Otevřete místní nabídku `CustomerID` řádku a potom vyberte **nastavit primární klíč**.

5. Otevřete místní nabídku pro výchozí řádek a pak vyberte **odstranit**.

6. Pojmenujte tabulku Zákazníci prostřednictvím aktualizace prvního řádku v podokně se skriptem tak, aby odpovídala následující ukázce:

    ```sql
    CREATE TABLE [dbo].[Customers]
    ```

    By měl vypadat přibližně takto:

    ![Návrhář tabulky](../data-tools/media/raddata-table-designer.png)

7. V levém horním rohu **návrháře tabulky**, vyberte **aktualizace** tlačítko.

8. V **náhled aktualizací databáze** dialogové okno, vyberte **aktualizace databáze** tlačítko.

    Vaše změny jsou uloženy do lokálního databázového souboru.

### <a name="create-the-orders-table"></a>Vytvoření tabulky objednávek

1. Přidejte další tabulku a potom přidejte řádek pro každou položku v následující tabulce:

    |Název sloupce|Datový typ|Povolit hodnoty NULL|
    |-----------------|---------------|-----------------|
    |`OrderID`|`int`|Nepravda (nezaškrtnuto)|
    |`CustomerID`|`nchar(5)`|Nepravda (nezaškrtnuto)|
    |`OrderDate`|`datetime`|Pravda (zaškrtnuto)|
    |`OrderQuantity`|`int`|Pravda (zaškrtnuto)|

2. Nastavte **OrderID** jako primární klíč a potom odstraňte výchozí řádek.

3. Pojmenujte tabulku Objednávky prostřednictvím aktualizace prvního řádku v podokně se skriptem tak, aby odpovídala následující ukázce:

    ```sql
    CREATE TABLE [dbo].[Orders]
    ```

4. V levém horním rohu **návrháře tabulky**, vyberte **aktualizace** tlačítko.

5. V **náhled aktualizací databáze** dialogové okno, vyberte **aktualizace databáze** tlačítko.

    Vaše změny jsou uloženy do lokálního databázového souboru.

### <a name="create-a-foreign-key"></a>Vytvoření cizího klíče

1. V kontextovém podokně na pravé straně tabulky, otevřete místní nabídku pro **cizí klíče**a pak vyberte **přidat nový cizí klíč**, jak je vidět na následujícím obrázku.

     ![Přidání cizí klíče v Návrháři tabulek](../data-tools/media/foreignkey.png)

2. V textovém poli nahraďte **ToTable** s **zákazníkům**.

3. V podokně T-SQL aktualizujte poslední řádek tak, aby odpovídala následující ukázce:

    ```sql
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
    ```

4. V levém horním rohu **návrháře tabulky**, vyberte **aktualizace** tlačítko.

5. V **náhled aktualizací databáze** dialogové okno, vyberte **aktualizace databáze** tlačítko.

    Vaše změny jsou uloženy do lokálního databázového souboru.

## <a name="populate-the-tables-with-data"></a>Naplnění tabulek daty

1. V **Průzkumníka serveru** nebo **Průzkumník objektů systému SQL Server**, rozbalte uzel pro vzorovou databázi.

2. Otevřete místní nabídku **tabulky** uzlu, vyberte **aktualizovat**a potom rozbalte **tabulky** uzlu.

3. Otevřete místní nabídku tabulky Zákazníci a zvolte **zobrazit Data tabulky**.

4. Přidejte jakákoli data pro některé zákazníky.

    Jako ID zákazníka můžete zadat libovolných pět znaků, ale vyberte alespoň jedno ID takové, které si zapamatujete, abyste je mohli použít později v tomto postupu.

5. Otevřete místní nabídku tabulky objednávky a pak vyberte **zobrazit Data tabulky**.

6. Přidání dat pro některé objednávky.

    > [!IMPORTANT]
    > Ujistěte se, že všechna ID objednávek a množství objednávek celými čísly a že každé ID zákazníka odpovídá hodnotě uvedené v **CustomerID** sloupec v tabulce Zákazníci.

7. Na panelu nabídek vyberte **souboru** > **Uložit vše**.

## <a name="see-also"></a>Viz také:

- [Přístup k datům v sadě Visual Studio](accessing-data-in-visual-studio.md)