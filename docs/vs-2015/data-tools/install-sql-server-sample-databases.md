---
title: Instalace ukázkových databází systému SQL Server | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38840167-c3f8-4cb3-8d15-8af04a0a20a1
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f6cd9260f29d8e46f66e54fec8cb24ae6857eb05
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50217860"
---
# <a name="install-sql-server-sample-databases"></a>Instalace ukázkových databází systému SQL Server
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Ukázkové databáze jsou užitečné pro experimentování s dotazy SQL a LINQ, vázání dat, modelování Entity Framework a tak dále.  Každý databázový produkt má svůj vlastní ukázkových databází. Northwind a AdventureWorks jsou dvě oblíbené ukázkové databáze systému SQL Server.  
  
 **AdventureWorks** je aktuální ukázkovou databázi k dispozici pro produkty SQL Server. Můžete ho stáhnout jako soubor MDF z [AdventureWorks stránky na webu Codeplex](http://msftdbprodsamples.codeplex.com/). Existují pravidelné a zjednodušené (SV) verze databáze k dispozici tady. Pro většinu scénářů je verze LT upřednostňované, protože je méně složitý.  
  
 **Northwind** je poměrně jednoduchá databáze systému SQL Server, který se použil po mnoho let. Můžete ho stáhnout jako soubor .bak z [stránka databáze Northwind na webu CodePlex](https://northwinddatabase.codeplex.com/). Abyste předešli problémům s oprávněními, rozbalte ho do nové složky, která není v rámci vaší složky uživatele.  
  
#### <a name="to-restore-a-database-from-a-bak-file-in-visual-studio"></a>Obnovení databáze ze souboru .bak v sadě Visual Studio  
  
1.  Při zálohování databáze Microsoft SQL Server, výsledek je soubor .bak. Chcete-li .bak souboru použitelné znovu jako soubor databáze, musí být *obnovit*. V hlavní nabídce vyberte **zobrazení** > **Průzkumník objektů systému SQL Server**. Pokud ho nevidíte, může být potřeba ji nainstalovat. Přejděte na **ovládací panely** > **programy a funkce**vyhledejte Microsoft Visual Studio 2015 a klikněte na tlačítko **změnu** tlačítko. Když v okně instalačního programu se zobrazí seznam nainstalovaných komponent, vyberte **Průzkumník objektů systému SQL Server** zaškrtněte políčko a potom pokračovat v instalaci.  
  
2.  V Průzkumníku objektů SQL serveru, klikněte pravým tlačítkem na libovolný databázovém stroji SQL serveru (například localdb) a vyberte**nový dotaz**.  
  
     ![SQL Server Object Explorer nový dotaz](../data-tools/media/raddata-sql-server-object-explorer-new-query.png "raddata SQL Server Object Explorer nový dotaz")  
  
3.  Nejprve je třeba logické názvy databáze a protokolu souborů v souboru .bak. Se dá stáhnout, zadejte tento dotaz do editoru dotazů SQL a pak vyberte zelené **spustit** tlačítko v horní části okna. V případě potřeby pro odkazování na soubor .bak změňte cestu k souboru.  
  
    ```  
    RESTORE FILELISTONLY  
    FROM DISK = 'C:\nw\northwind.bak'  
    GO  
    ```  
  
     Zapište si logické názvy, které se zobrazí v okně výsledky.  Pro databázi Northwind jsou dvě logické názvy Northwind a Northwind_log.  
  
4.  Nyní spusťte tento dotaz k vytvoření databáze. Nahraďte vlastní zdrojové a cílové cesty, názvy databází logický a fyzický soubor názvů pro databáze Northwind podle potřeby. Zachovejte přípony souborů .mdf a .ldf.  
  
    ```  
    RESTORE DATABASE Northwind  
    FROM DISK = 'c:\nw\northwind.bak'  
    WITH MOVE 'Northwind' TO 'c:\nw\northwind.mdf',  
    MOVE 'Northwind_log' TO 'c:\nw\northwind.ldf'  
    ```  
  
5.  V Průzkumníku objektů SQL serveru, klikněte pravým tlačítkem na **databází** uzlu, by se měla zobrazit uzel databáze Northwind. Pokud ne, pak klikněte pravým tlačítkem na databáze a vyberte **přidat novou databázi**. Zadejte název a umístění souboru .mdf, který jste právě vytvořili.  
  
6.  Databáze je nyní připravený k použití jako zdroj dat v sadě Visual Studio.  
  
#### <a name="to-restore-a-database-from-a-bak-file-in-sql-server-management-studio"></a>Obnovení databáze ze souboru .bak v SQL Server Management Studio  
  
1.  Stáhněte si SQL Server Management Studio ze serveru pro stahování.  
  
2.  V SSMS **Průzkumník objektů** okna, klikněte pravým tlačítkem na **databází** uzlu, vyberte**obnovit databázi**a poskytnout umístění souboru .bak.  
  
     ![Obnovit databázi aplikace SSMS](../data-tools/media/raddata-ssms-restore-database.png "raddata obnovit databázi aplikace SSMS")

