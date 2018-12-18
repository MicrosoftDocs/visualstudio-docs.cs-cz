---
title: 'Postupy: připojení k databázi Northwind | Dokumentace Microsoftu'
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
- connections [Visual Studio], Northwind database
- Northwind sample database
ms.assetid: cc6cb79f-d035-41f8-b398-8d4a45922bfb
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 3f64fa378029546f7a3126b324c282f6a91d7231
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897627"
---
# <a name="how-to-connect-to-the-northwind-database"></a>Postupy: Připojení k databázi Northwind
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jak se dozvíte, jak k vytvoření databázové aplikace pomocí sady Visual Studio, budete potřebovat pro připojení k databázi Northwind dodržovat mnoho příkladů v dokumentaci k produktu. V závislosti na tom, které sledujete příkladu budete připojení k databázi systému SQL Server nebo databázový soubor, třeba jednoho pro aplikace Microsoft Access nebo SQL Server.  
  
## <a name="creating-data-connections-to-the-northwind-database"></a>Vytváření datových připojení k databázi Northwind  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-data-connection-to-the-northwind-database-sql-server"></a>Vytvoření datového připojení k databázi Northwind (SQL Server)  
  
1. Na **zobrazení** nabídce zvolte **Průzkumníka serveru**/**Průzkumník databáze**.  
  
2. V **Průzkumníka serveru**/**Průzkumník databáze**, otevřete místní nabídku pro **datová připojení** a zvolte **přidat připojení**.  
  
    Po zvolení **přidat připojení**– buď **zvolit zdroj dat** dialogové okno nebo **přidat připojení** se zobrazí dialogové okno.  
  
3. Pokud **zvolit zdroj dat** dialogové okno se zobrazí, vyberte **Microsoft SQL Server**a klikněte na tlačítko **OK**.  
  
    Pokud **přidat připojení** zobrazí se dialogové okno a **zdroj dat** není **Microsoft SQL Server (SqlClient)**, zvolte **změnu** tlačítko Otevřít **změnit zdroj dat** dialogu **Microsoft SQL Server**a klikněte na tlačítko **OK** tlačítko.  
  
4. V **název serveru** seznamu, zadejte název serveru, na kterém je umístěna databáze Northwind.  
  
5. V závislosti na požadavcích vaší verzi SQL serveru a databáze Northwind, zvolte **použít ověřování Windows** nebo zvolte **použít ověřování SQL serveru** a zadejte uživatelské jméno a heslo pro přihlášení k počítači se systémem SQL Server.  
  
6. Zvolte databázi Northwind v **vyberte nebo zadejte název databáze** seznamu.  
  
7. Zvolte **Test připojení** k ověření připojení k databázi Northwind.  
  
8. Zvolte **OK**.  
  
    Přidání datového připojení k databázi Northwind k **Průzkumníka serveru**/**Průzkumník databáze**.  
  
   Kromě připojení k vzdálené instanci databáze systému SQL Server, můžete také připojit přímo k skutečné soubory, které obsahují databáze. To umožňuje přidat databázové soubory přímo do projektu, kde můžete nasadit jako součást aplikace. Aktuálně jsou podporovány následujícím lokálním databázovým souborům: databázové soubory SQL Server Compact (SDF) [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a databázové soubory SQL Server Express (.mdf) a soubory databáze Microsoft Access (MDB nebo ACCDB).  
  
#### <a name="to-create-a-data-connection-to-the-northwind-databasesql-server-database-file-mdf"></a>Vytvoření datového připojení k databázi Northwind – soubor databáze systému SQL Server (MDF)  
  
1.  Na **zobrazení** nabídce zvolte **Průzkumníka serveru**/**Průzkumník databáze**.  
  
2.  V **Průzkumníka serveru**/**Průzkumník databáze**, otevřete místní nabídku pro **datová připojení** a zvolte **přidat připojení**.  
  
     Po zvolení **přidat připojení**– buď **přidat připojení** dialogové okno nebo **zvolit zdroj dat** se zobrazí dialogové okno.  
  
3.  Pokud **zvolit zdroj dat** dialogové okno se zobrazí, vyberte **soubor databáze Microsoft SQL Server**a klikněte na tlačítko **OK**.  
  
4.  Pokud **přidat připojení** se zobrazí dialogové okno, ověřte, že **zdroj dat** je nastavena na **soubor databáze Microsoft SQL Server (SqlClient)**. Pokud není nastavená na **soubor databáze Microsoft SQL Server (SqlClient)**, zvolte **změnu** otevřít **změnit zdroj dat** dialogového okna zvolte **Microsoft SQL Soubor databáze serveru**a klikněte na tlačítko **OK** tlačítko.  
  
5.  Zvolte **Procházet** vyhledejte soubor MDF, který obsahuje databázi Northwind.  
  
6.  V závislosti na požadavcích vaší verzi databáze Northwind, zvolte **použít ověřování Windows** nebo zvolte **ověřování systému SQL Server** a zadejte uživatelské jméno a heslo pro přihlášení k počítač se systémem SQL Server.  
  
7.  Zvolte **OK** tlačítko.  
  
     Přidání datového připojení k databázi Northwind k **Průzkumníka serveru**/**Průzkumník databáze**.  
  
> [!NOTE]
>  [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] obsahuje změny, které se vztahují k souboru databáze Northwind (.mdf). Informace najdete v tématu [postupy: Instalace ukázkových databází](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-a-data-connection-to-the-northwind-databaseaccess-database-file-mdb-or-accdb"></a>Vytvoření datového připojení k databázi Northwind – soubor databáze aplikace Access (MDB nebo ACCDB)  
  
1.  Na **zobrazení** nabídce zvolte **Průzkumníka serveru**/**Průzkumník databáze**.  
  
2.  V **Průzkumníka serveru**/**Průzkumník databáze**, otevřete místní nabídku pro **datová připojení** a zvolte **přidat připojení**.  
  
     Po zvolení **přidat připojení**– buď **přidat připojení** dialogové okno nebo **zvolit zdroj dat** se zobrazí dialogové okno.  
  
3.  Pokud **zvolit zdroj dat** dialogové okno se zobrazí, vyberte **soubor databáze Microsoft Access**a klikněte na tlačítko **OK**.  
  
4.  Pokud **přidat připojení** se zobrazí dialogové okno, ověřte, že **zdroj dat** je nastavena na **soubor databáze Microsoft Access**. Pokud není nastavená na **soubor databáze Microsoft Access**, zvolte **změnu** otevřít **změnit zdroj dat** dialogového okna zvolte **databáze aplikace Microsoft Access Soubor**a klikněte na tlačítko **OK** tlačítko.  
  
5.  Zvolte **Procházet** vyhledejte soubor MDB nebo ACCDB, který obsahuje databázi Northwind.  
  
6.  Zadejte uživatelské jméno a heslo, pokud je vyžadováno vaší verzi databáze Northwind.  
  
7.  Zvolte **OK**.  
  
     Přidání datového připojení k databázi Northwind k **Průzkumníka serveru**/**Průzkumník databáze**.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Instalace ukázkových databází](../data-tools/how-to-install-sample-databases.md)   
 [Programování dat pomocí aplikace Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx)   
 [Návody k datům](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)