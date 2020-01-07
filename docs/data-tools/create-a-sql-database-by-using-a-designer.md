---
title: Vytvoření databázového souboru a použití Návrháře tabulky
description: Kurz popisující, jak přidat tabulky a cizí klíče do databáze pomocí Návrháře tabulky v aplikaci Visual Studio. Také ukazuje, jak přidat data prostřednictvím grafického rozhraní.
ms.date: 09/19/2019
ms.topic: conceptual
helpviewer_keywords:
- database tables, creating
- database files, creating
- table designer
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c8fa89b2cf6eb5afdf1d09a9b4de60cdc9ca11f2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586884"
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>Vytvoření databáze a přidání tabulek v aplikaci Visual Studio

Můžete použít Visual Studio k vytvoření a aktualizaci místního databázového souboru v SQL Server Express LocalDB. Databázi můžete vytvořit také spuštěním příkazů jazyka Transact-SQL v okně nástroje **Průzkumník objektů systému SQL Server** v aplikaci Visual Studio. V tomto tématu vytvoříme soubor *. mdf* a přidáte tabulky a klíče pomocí Návrháře tabulky.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto Názorného postupu budete potřebovat úlohy pro **vývoj desktopových** aplikací pro .NET a **ukládání a zpracování dat,** které jsou nainstalované v aplikaci Visual Studio. Pokud je chcete nainstalovat, otevřete **instalační program pro Visual Studio** a klikněte na tlačítko **Upravit** (nebo **Další** > **Upravit**) vedle verze sady Visual Studio, kterou chcete upravit.

## <a name="create-a-project-and-a-local-database-file"></a>Vytvoření projektu a lokálního databázového souboru

1. Vytvořte nový projekt **aplikace model Windows Forms** a pojmenujte ho **SampleDatabaseWalkthrough**.

2. Na panelu nabídek vyberte **projekt** > **Přidat novou položku**.

3. V seznamu šablon položek přejděte dolů a vyberte možnost **databáze na základě služby**.

   ![Šablony položek – dialogové okno](../data-tools/media/raddata-vsitemtemplates.png)

4. Pojmenujte databázi **SampleDatabase**a pak klikněte na **Přidat**.

### <a name="add-a-data-source"></a>Přidání zdroje dat

1. Pokud není okno **zdroje dat** otevřené, otevřete ho stisknutím klávesy **Shift**+**ALT**+**D** nebo výběrem možnosti **Zobrazit** > **jiné** **zdroje dat** > Windows na řádku nabídek.

1. V okně **zdroje dat** vyberte **Přidat nový zdroj dat**.

   ![Přidat nový zdroj dat v aplikaci Visual Studio](media/add-new-data-source.png)

   Otevře se **Průvodce konfigurací zdroje dat** .

1. Na stránce **Zvolte typ zdroje dat** zvolte možnost **databáze** a pak klikněte na tlačítko **Další**.

1. Na stránce **výběr databázového modelu** přijměte výchozí nastavení (datová sada) kliknutím na tlačítko **Další** .

1. Na stránce **Vyberte datové připojení** vyberte v rozevíracím seznamu soubor **SampleDatabase. mdf** a klikněte na tlačítko **Další**.

1. Na stránce **Uložit připojovací řetězec do konfiguračního souboru aplikace** klikněte na tlačítko **Další**.

1. Na stránce **Výběr databázových objektů** se zobrazí zpráva oznamující, že databáze neobsahuje žádné objekty. Zvolte **Dokončit**.

### <a name="view-properties-of-the-data-connection"></a>Zobrazit vlastnosti datového připojení

Připojovací řetězec pro soubor *SampleDatabase. mdf* můžete zobrazit otevřením okno Vlastnosti datového připojení:

- Výběrem **zobrazit** > **Průzkumník objektů systému SQL Server** otevřete okno **Průzkumník objektů systému SQL Server** . Rozbalte **(LocalDB) \MSSQLLocalDB** > **databáze**a potom klikněte pravým tlačítkem na *SampleDatabase. mdf* a vyberte **vlastnosti**.

- Případně můžete vybrat možnost **zobrazit** > **Průzkumník serveru**, pokud toto okno ještě není otevřené. Otevřete okno Vlastnosti rozbalením uzlu **datová připojení** , kliknutím pravým tlačítkem myši na *SampleDatabase. mdf*a následným výběrem **vlastností**.

  > [!TIP]
  > Pokud nemůžete rozšířit uzel datová připojení, nebo není uvedené připojení SampleDatabase. mdf, vyberte na panelu nástrojů Průzkumník serveru tlačítko **připojit k databázi** . V dialogovém okně **Přidat připojení** se ujistěte, že je v části **zdroj dat**vybraná možnost **Microsoft SQL Server databázový soubor** , a pak vyhledejte a vyberte soubor SampleDatabase. mdf. Kliknutím na **tlačítko OK**dokončete přidání připojení.

## <a name="create-tables-and-keys-by-using-table-designer"></a>Vytváření tabulek a klíčů pomocí Návrháře tabulky

V této části vytvoříte dvě tabulky, primární klíč v každé tabulce a několik řádků ukázkových dat. Také vytvoříte cizí klíč k určení způsobu, jakým budou záznamy v jedné tabulce odpovídat záznamům v druhé tabulce.

### <a name="create-the-customers-table"></a>Vytvoření tabulky Customers

1. V **Průzkumník serveru**rozbalte uzel **datová připojení** a poté rozbalte uzel **SampleDatabase. mdf** .

   Pokud nemůžete rozšířit uzel datová připojení, nebo není uvedené připojení SampleDatabase. mdf, vyberte na panelu nástrojů Průzkumník serveru tlačítko **připojit k databázi** . V dialogovém okně **Přidat připojení** se ujistěte, že je v části **zdroj dat**vybraná možnost **Microsoft SQL Server databázový soubor** , a pak vyhledejte a vyberte soubor SampleDatabase. mdf. Kliknutím na **tlačítko OK**dokončete přidání připojení.

2. Klikněte pravým tlačítkem na **tabulky** a vyberte **Přidat novou tabulku**.

   Návrhář tabulky otevře a zobrazí mřížku s jedním výchozím řádkem, který představuje jeden sloupec v tabulce, kterou vytváříte. Přidáním řádků do mřížky přidáte další sloupce v tabulce.

3. V mřížce přidejte řádek pro každou z následujících položek:

   |Název sloupce|Datový typ|Povolit hodnoty NULL|
   |-----------------|---------------|-----------------|
   |`CustomerID`|`nchar(5)`|Nepravda (nezaškrtnuto)|
   |`CompanyName`|`nvarchar(50)`|Nepravda (nezaškrtnuto)|
   |`ContactName`|`nvarchar (50)`|Pravda (zaškrtnuto)|
   |`Phone`|`nvarchar (24)`|Pravda (zaškrtnuto)|

4. Klikněte pravým tlačítkem na řádek `CustomerID` a pak vyberte **nastavit primární klíč**.

5. Klikněte pravým tlačítkem na výchozí řádek (`Id`) a pak vyberte **Odstranit**.

6. Pojmenujte tabulku Zákazníci prostřednictvím aktualizace prvního řádku v podokně se skriptem tak, aby odpovídala následující ukázce:

   ```sql
   CREATE TABLE [dbo].[Customers]
   ```

   Mělo by se zobrazit něco takového:

   ![Návrhář tabulky](../data-tools/media/table-designer.png)

7. V levém horním rohu **Návrháře tabulky**vyberte **aktualizovat**.

8. V dialogovém okně **Náhled aktualizací databáze** vyberte **aktualizovat databázi**.

   Tabulka Customers (zákazníci) se vytvoří v souboru místní databáze.

### <a name="create-the-orders-table"></a>Vytvoření tabulky Orders

1. Přidejte další tabulku a potom přidejte řádek pro každou položku v následující tabulce:

   |Název sloupce|Datový typ|Povolit hodnoty NULL|
   |-----------------|---------------|-----------------|
   |`OrderID`|`int`|Nepravda (nezaškrtnuto)|
   |`CustomerID`|`nchar(5)`|Nepravda (nezaškrtnuto)|
   |`OrderDate`|`datetime`|Pravda (zaškrtnuto)|
   |`OrderQuantity`|`int`|Pravda (zaškrtnuto)|

2. Jako primární klíč nastavte **ČísloObjednávky** a pak výchozí řádek odstraňte.

3. Pojmenujte tabulku Objednávky prostřednictvím aktualizace prvního řádku v podokně se skriptem tak, aby odpovídala následující ukázce:

   ```sql
   CREATE TABLE [dbo].[Orders]
   ```

4. V levém horním rohu **Návrháře tabulky**vyberte **aktualizovat**.

5. V dialogovém okně **Náhled aktualizací databáze** vyberte **aktualizovat databázi**.

   Tabulka Orders (objednávky) se vytvoří v souboru místní databáze. Pokud rozbalíte uzel **tabulky** v Průzkumník serveru, zobrazí se tyto dvě tabulky:

   ![Uzel Tables se rozšířil v Průzkumník serveru.](media/server-explorer-tables-node.png)

### <a name="create-a-foreign-key"></a>Vytvoření cizího klíče

1. V kontextovém podokně na pravé straně mřížky Návrháře tabulky pro tabulku objednávky klikněte pravým tlačítkem na **cizí klíče** a vyberte **Přidat nový cizí klíč**.

   ![Přidání cizího klíče v Návrháři tabulky v aplikaci Visual Studio](../data-tools/media/add-foreign-key.png)

2. Do textového pole, které se zobrazí, nahraďte text ToTable **zákazníky**.

3. V podokně T-SQL aktualizujte poslední řádek tak, aby odpovídal následující ukázce:

   ```sql
   CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
   ```

4. V levém horním rohu **Návrháře tabulky**vyberte **aktualizovat**.

5. V dialogovém okně **Náhled aktualizací databáze** vyberte **aktualizovat databázi**.

   Je vytvořen cizí klíč.

## <a name="populate-the-tables-with-data"></a>Naplnění tabulek daty

1. V **Průzkumník serveru** nebo **Průzkumník objektů systému SQL Server**rozbalte uzel pro ukázkovou databázi.

2. Otevřete místní nabídku pro uzel **tabulky** , vyberte **aktualizovat**a potom rozbalte uzel **tabulky** .

3. Otevřete místní nabídku tabulky Customers a potom vyberte možnost **Zobrazit data tabulky**.

4. Přidejte libovolná data, která chcete pro některé zákazníky.

    Jako ID zákazníka můžete zadat libovolných pět znaků, ale vyberte alespoň jedno ID takové, které si zapamatujete, abyste je mohli použít později v tomto postupu.

5. Otevřete místní nabídku tabulky Orders a pak vyberte možnost **Zobrazit data tabulky**.

6. Přidejte data pro některé objednávky.

    > [!IMPORTANT]
    > Zajistěte, aby všechny ID objednávek a množství objednávek byly celá čísla a aby každé ID zákazníka odpovídalo hodnotě, kterou jste zadali ve sloupci **KódZákazníka** tabulky Customers.

7. Na řádku nabídek vyberte **soubor** > **Uložit vše**.

## <a name="see-also"></a>Viz také:

- [Přístup k datům v sadě Visual Studio](accessing-data-in-visual-studio.md)
