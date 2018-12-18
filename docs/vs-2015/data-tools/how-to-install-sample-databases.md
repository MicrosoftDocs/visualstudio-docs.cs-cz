---
title: 'Postupy: Instalace ukázkových databází | Dokumentace Microsoftu'
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
- sample databases, Adventure Works
- data [Visual Studio], sample databases
- sample databases, Northwind
- Northwind sample database
- Adventure Works sample database
ms.assetid: ed1291f6-604c-4972-ae22-0345c6dea12e
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: d3ffe88fb54da26468ca510a2f1a7ab6170d88db
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881715"
---
# <a name="how-to-install-sample-databases"></a>Postupy: Instalace ukázkových databází
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mnoho příkladů dat vyžaduje možnost připojení k Northwind, Pubs a AdventureWorks ukázkových databází. Můžete nainstalovat a připojení k těmto databázím s použitím následujících postupů.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="installing-databases"></a>Instalace databáze  
 Mnoho příkladů dat vyžaduje dostupnost ukázkové databáze, kterou si můžete stáhnout z webových serverů. Ukázkové databáze zahrnují databáze AdventureWorks, Northwind a Pubs.  
  
#### <a name="to-install-the-northwind-and-pubs-sample-databases-for-sql-server"></a>K instalaci ukázkové databáze Pubs a Northwind pro SQL Server  
  
1.  Přejděte [ukázkové databáze Pubs a Northwind](http://go.microsoft.com/fwlink?linkid=64296) webu.  
  
2.  Stáhněte si a spusťte instalační program.  
  
     Instalační program přidá složku **SQL Server 2000 Sample Databases** ke kořenové složce v počítači. (Příklad: **C:\SQL Server 2000 Sample Databases**).  
  
3.  Vyhledejte skript SQL pro databázi, kterou chcete, Northwind nebo Pubs.  
  
    > [!WARNING]
    >  Na. Soubor databáze MDF nelze snadno převést do formátu, který vám pomůže v aktuálních verzích SQL serveru, takže je vhodné použít skript k vytvoření databáze.  
  
4.  V **Průzkumníka serveru**, vytvořit připojení k instanci systému SQL Server, ve které chcete nainstalovat databázi. Pokud nemáte konkrétní SQL Server, který chcete použít, můžete použít databázi, která je automaticky nainstalován se sadou Visual Studio. Chcete-li to mohli udělat, zadejte `(localdb)\v11.0` jako název serveru.  
  
     K vytvoření připojení, postupujte podle těchto kroků.  
  
    ###### <a name="to-create-a-connection-to-an-instance-of-sql-server"></a>Chcete-li vytvořit připojení k instanci systému SQL Server  
  
    1.  V **Průzkumníka serveru**, otevřete místní nabídku **datová připojení** uzel a zvolte **přidat připojení**.  
  
         **Přidat připojení** zobrazí se dialogové okno.  
  
    2.  Zadejte název SQL serveru, kde chcete vytvořit databázi Northwind nebo Pubs nebo zadejte (localdb) \v11.0.  
  
    3.  V části **vyberte nebo zadejte název databáze**, zvolte libovolnou databázi ze seznamu, například databázi tempdb.  
  
    4.  Zvolte **Test připojení** tlačítko ověřit, že všechno funguje a klikněte na tlačítko **OK** tlačítko.  
  
         Nový uzel připojení se zobrazí v **Průzkumníka serveru**.  
  
5.  Na místní nabídku pro uzel připojení serveru a klikněte na tlačítko **nový dotaz** tlačítko.  
  
     Okno editoru se otevře a zobrazí prázdný soubor skriptu .sql.  
  
6.  Vložte obsah souboru instnwnd.sql nebo instpubs.sql do okna editoru.  
  
7.  Klikněte na tlačítko Spustit dotaz (otevřít zeleným trojúhelníkem ikonu v horní části napravo od okna dotazu).  
  
     Pokud je dotaz úspěšný, zprávy **příkazy byly úspěšně dokončeny** se zobrazí. To znamená, že byla vytvořena databáze Northwind nebo pubs.  
  
     Stále musíte přidat připojení k ukázkové databázi. V **Průzkumníka serveru**, otevřete místní nabídku **datová připojení** uzlu a zvolte **přidat připojení**.  
  
8.  Zvolte stejný databázový server, který jste zvolili dříve, ale tentokrát, v části vyberte nebo zadejte název databáze, zvolte databázi Northwind nebo pubs a zvolte **OK** tlačítko.  
  
     Nový uzel se zobrazí v části připojení dat pro vzorovou databázi.  
  
9. Zavře okno editoru a potvrďte, že nechcete uložit soubor dotazu. Není nutné uložit skript vytvoření databáze po vytvoření databáze.  
  
#### <a name="to-install-the-adventureworks-sample-databases"></a>Instalace ukázkových databází AdventureWorks  
  
-   Stažení ukázkových databází AdventureWorks z [webových stránkách CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
#### <a name="to-install-the-northwind-sample-database-for-microsoft-access"></a>K instalaci ukázkové databáze Northwind pro aplikaci Microsoft Access  
  
1. V aplikaci Microsoft Access 2010 nebo novější, vyhledání online šablon Northwind a zvolte **ukázkovou databázi Desktop Northwind 2007**.  
  
2. V aplikaci Microsoft Access uložte soubor databáze jako Northwind.accdb.  
  
   Nové rozšíření pro databáze aplikace Access je .accdb. Zobrazit [programování dat pomocí aplikace Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx). Připojení k databázi Northwind pomocí přístupu najdete v tématu [postupy: připojení k databázi Northwind](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Ukázkové databáze slouží pouze pro ilustraci a nemusí nutně používat osvědčené postupy zabezpečení.  
  
## <a name="see-also"></a>Viz také  
 [Jak určit verzi a edici systému SQL Server a jeho součásti](http://support.microsoft.com/kb/321185)   
 [Vytvoření databáze SQL pomocí návrháře](../data-tools/create-a-sql-database-by-using-a-designer.md)   
 [Postupy: připojení k databázi Northwind](../data-tools/how-to-connect-to-the-northwind-database.md)