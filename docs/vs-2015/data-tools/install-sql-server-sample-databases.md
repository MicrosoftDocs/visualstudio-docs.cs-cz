---
title: Instalace ukázkových databází SQL Server | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 38840167-c3f8-4cb3-8d15-8af04a0a20a1
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3991d3b741162b4b1993e5359ad427c17f00321a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651531"
---
# <a name="install-sql-server-sample-databases"></a>Instalace ukázkové databáze SQL Serveru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ukázkové databáze jsou užitečné pro experimentování s dotazy SQL a LINQ, DataBinding, modelování Entity Framework a tak dále.  Každý databázový produkt má své vlastní ukázkové databáze. Northwind a AdventureWorks jsou dvě oblíbené SQL Server ukázkové databáze.

 **AdventureWorks** je aktuální ukázková databáze poskytovaná pro SQL Server Products. Můžete si ho stáhnout jako soubor. mdf ze [stránky AdventureWorks na webu CodePlex](http://msftdbprodsamples.codeplex.com/). Zde jsou k dispozici běžné a zjednodušené verze (LT) databáze. Ve většině scénářů je preferovaná verze LT, protože je méně složitá.

 **Northwind** je poměrně jednoduchá databáze SQL Server, která se používá po řadu let. Můžete si ho stáhnout jako soubor. bak [na stránce databáze Northwind na webu CodePlex](https://northwinddatabase.codeplex.com/). Aby se zabránilo problémům s oprávněními, rozbalte soubor do nové složky, která není ve složce uživatele.

#### <a name="to-restore-a-database-from-a-bak-file-in-visual-studio"></a>Obnovení databáze ze souboru. bak v aplikaci Visual Studio

1. Při zálohování databáze Microsoft SQL Server je výsledkem soubor. bak. Aby se soubor. bak mohl znovu použít jako databázový soubor, musí být *obnoven*. V hlavní nabídce vyberte **zobrazit**  > **Průzkumník objektů systému SQL Server**. Pokud ho nevidíte, možná ho budete muset nainstalovat. Přejděte na **Ovládací panely**  > **programy a funkce**, vyhledejte Microsoft Visual Studio 2015 a klikněte na tlačítko **změnit** . Když se v okně instalačního programu zobrazí seznam nainstalovaných součástí, zaškrtněte políčko **Průzkumník objektů systému SQL Server** a potom pokračujte v instalaci.

2. V Průzkumník objektů systému SQL Server klikněte pravým tlačítkem na jakýkoli SQL Server databázový stroj (například LocalDB) a vyberte**Nový dotaz**.

     ![Průzkumník objektů systému SQL Server nový dotaz](../data-tools/media/raddata-sql-server-object-explorer-new-query.png "raddata Průzkumník objektů systému SQL Server nový dotaz")

3. Nejdřív budete potřebovat logické názvy databází a souborů protokolu v souboru. bak. Pokud ho chcete získat, zadejte tento dotaz do editoru dotazů SQL a potom v horní části okna vyberte zelené tlačítko **Spustit** . V případě potřeby upravte cestu k souboru tak, aby odkazovala na soubor. bak.

    ```
    RESTORE FILELISTONLY
    FROM DISK = 'C:\nw\northwind.bak'
    GO
    ```

     Vypište logické názvy, které se zobrazí v okně výsledků.  Pro databázi Northwind jsou tyto dva logické názvy Northwind a Northwind_log.

4. Nyní spusťte tento dotaz k vytvoření databáze. Podle potřeby nahraďte vlastní zdrojové a cílové cesty, názvy logických databází a fyzické názvy souborů pro Northwind. Ponechejte přípony souborů. mdf a. ldf.

    ```
    RESTORE DATABASE Northwind
    FROM DISK = 'c:\nw\northwind.bak'
    WITH MOVE 'Northwind' TO 'c:\nw\northwind.mdf',
    MOVE 'Northwind_log' TO 'c:\nw\northwind.ldf'
    ```

5. V Průzkumník objektů systému SQL Server klikněte pravým tlačítkem myši na uzel **databáze** a měli byste vidět uzel databáze Northwind. Pokud ne, klikněte pravým tlačítkem na databáze a vyberte **Přidat novou databázi**. Zadejte název a umístění souboru. mdf, který jste právě vytvořili.

6. Databáze je nyní připravena k použití jako zdroj dat v aplikaci Visual Studio.

#### <a name="to-restore-a-database-from-a-bak-file-in-sql-server-management-studio"></a>Obnovení databáze ze souboru. bak v SQL Server Management Studio

1. Stáhněte SQL Server Management Studio z webu pro stažení.

2. V okně SSMS **Průzkumník objektů** klikněte pravým tlačítkem myši na uzel **databáze** , vyberte možnost**obnovit databázi**a zadejte umístění souboru. bak.

     ![Databáze obnovení SSMS](../data-tools/media/raddata-ssms-restore-database.png "Databáze obnovení raddata SSMS")
