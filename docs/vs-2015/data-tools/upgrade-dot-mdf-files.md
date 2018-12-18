---
title: Upgrade souborů .mdf | Dokumentace Microsoftu
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
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
ms.assetid: 14ca6f76-f80e-4926-8020-3fee2d802b75
caps.latest.revision: 36
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: d71b38fe0d4aef412860a9dc65002c9b8d98c79c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812631"
---
# <a name="upgrade-mdf-files"></a>Upgrade souborů .mdf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Toto téma popisuje možnosti pro upgrade souboru databáze (MDF), po instalaci novější verze sady Visual Studio. Obsahuje pokyny pro následující úlohy:  
  
- Upgrade databázového souboru, který chcete používat novější verzi SQL Server Express LocalDB  
  
- Upgrade databázového souboru pro použití novější verze systému SQL Server Express  
  
- Práce s databázového souboru v sadě Visual Studio při zachování kompatibility se starší verzí systému SQL Server Express nebo LocalDB  
  
- Ujistěte se, SQL Server Express. databázový stroj výchozí  
  
  Visual Studio můžete použít k otevření projektu, který obsahuje soubor databáze (MDF), která byla vytvořena pomocí starší verze systému SQL Server Express nebo LocalDB. Ale dalším vývoji projektu v sadě Visual Studio, musíte mít verzi systému SQL Server Express nebo LocalDB nainstalované ve stejném počítači jako Visual Studio, nebo musíte upgradovat tento databázový soubor. Pokud provedete upgrade databázového souboru, nebude možné k němu přistupovat pomocí starší verze systému SQL Server Express nebo LocalDB.  
  
  Také můžete být vyzváni k upgradu databáze soubor, který byl vytvořen pomocí dřívější verzi serveru SQL Server Express nebo LocalDB, pokud není kompatibilní s instancí systému SQL Server Express nebo LocalDB, který je aktuálně nainstalované verzi souboru. Chcete-li vyřešit tento problém, Visual Studio vás vyzve k upgradu soubor.  
  
> [!IMPORTANT]
>  Doporučujeme, abyste před provedením upgradu zálohovat soubor databáze.  
  
> [!WARNING]
>  Pokud provádíte upgrade souboru .mdf, který byl vytvořen v LocalDB 2014 (V12) 32 bitů na LocalDB 2016 (V13), nebudete moct znovu otevřít soubor v 32bitové verzi LocalDB.  V aktualizaci Update 2 je LocalDB V13 pouze 64bitová verze.  
  
 Než spustíte upgrade databáze, zvažte následující kritéria:  
  
-   Neprovádějte upgrade, pokud budete chtít pracovat na projektu ve starší verzi a novější verze sady Visual Studio.  
  
-   Neprovádějte upgrade, pokud vaše aplikace se použije v prostředí, které používá namísto LocalDB systému SQL Server Express.  
  
-   Pokud vaše aplikace používá vzdálená připojení, nemusíte upgradovat, protože LocalDB nepřijme.  
  
-   Neprovádějte upgrade, pokud vaše aplikace využívá v Internetové informační služby (IIS).  
  
-   Pokud chcete otestovat databázových aplikací v prostředí izolovaného prostoru, ale nechcete, aby ke správě databáze, zvažte možnost upgradovat.  
  
### <a name="to-upgrade-a-database-file"></a>Upgrade databázového souboru  
  
1. V **Průzkumníka serveru**, vyberte **připojit k databázi** tlačítko.  
  
2. V **přidat připojení** dialogovém okně zadejte následující informace:  
  
   -   **Zdroj dat**: `Microsoft SQL Server (SqlClient)`  
  
   -   **Název serveru**:  
  
       -   Chcete-li použít výchozí verzi: `(localdb)\MSSQLLocalDB`.  To určí ProjectV12 nebo ProjectV13, v závislosti na tom, která verze sady Visual Studio je nainstalovaná a vytvoření první instanci LocalDB. **MSSQLLocalDB** uzel v **Průzkumník objektů systému SQL Server** ukazuje, která verze bude ukazovat.  
  
       -   Chcete-li použít konkrétní verzi: `(localdb)\ProjectsV12` nebo `(localdb)\ProjectsV13`, kde je V12 LocalDB 2014 a V13 je LocalDB 2016.  
  
   -   **Připojit soubor databáze**: fyzickou cestu primárního souboru MDF.  
  
   -   **Logický název**: název, který chcete použít se souborem.  
  
3. Vyberte **OK** tlačítko.  
  
4. Po zobrazení výzvy, vyberte **Ano** tlačítko Upgradovat soubor.  
  
   Databáze se upgraduje, je připojen k modulu databáze LocalDB a již není kompatibilní s starší verzi LocalDB.  
  
   Můžete také upravit připojení SQL Server Express LocalDB použít tak, že otevřete místní nabídku pro připojení a pak vyberete **změna připojení**. V **změna připojení** dialogové okno pole, změňte název serveru, aby `(LocalDB)\MSSQLLocalDB`. V **Upřesnit vlastnosti** dialogové okno pole, ujistěte se, že **uživatelskou instanci** je nastavena na **False**.  
  
### <a name="to-upgrade-to-a-newer-version-of-sql-server-express"></a>Upgrade na novější verzi systému SQL Server Express  
  
1. V místní nabídce pro připojení k databázi, vyberte **změna připojení**.  
  
2. V **změna připojení** dialogové okno, vyberte **Upřesnit** tlačítko.  
  
3. V **Upřesnit vlastnosti** dialogové okno, vyberte **OK** tlačítko beze změny názvu serveru.  
  
   Soubor databáze se upgraduje na shodovat s aktuální verzí systému SQL Server Express.  
  
### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>K práci s databází v sadě Visual Studio, ale zachovat kompatibilitu s SQL Server Express  
  
-   V sadě Visual Studio otevřete projekt bez upgradu ho.  
  
    -   Spusťte projekt, vyberte klávesu F5.  
  
    -   Chcete-li upravit databázi, otevřete soubor MDF v **Průzkumníku řešení**a rozbalte uzel v **Průzkumníka serveru** pro práci s databází.  
  
### <a name="to-make-sql-server-express-the-default-database-engine"></a>Chcete-li systém SQL Server Express výchozí databázový stroj  
  
1. Na panelu nabídek vyberte **nástroje** > **možnosti**.  
  
2. V **možnosti** dialogového okna rozbalte **Data Tools** možnosti a pak vyberte **datová připojení** uzlu.  
  
3. V **název Instance systému SQL Server** textové pole, zadejte název instance systému SQL Server Express nebo LocalDB, který chcete použít. Pokud není název instance, zadejte `.\SQLEXPRESS or (localdb)\MSSQLLocalDB`.  
  
4. Vyberte **OK** tlačítko.  
  
   SQL Server Express budou mít výchozí databázový stroj pro vaše aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Přehled lokálních dat](../data-tools/local-data-overview.md)   
 [Návod: Připojování k datům v lokálního databázového souboru (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)

