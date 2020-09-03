---
title: Upgradovat soubory. mdf | Microsoft Docs
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
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
ms.assetid: 14ca6f76-f80e-4926-8020-3fee2d802b75
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 5b26b8cd9d955309e3be0e17e975bfdeb242e475
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72621408"
---
# <a name="upgrade-mdf-files"></a>Upgrade souborů .mdf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje možnosti pro upgrade souboru databáze (MDF) po instalaci novější verze sady Visual Studio. Obsahuje pokyny pro následující úlohy:

- Upgrade databázového souboru pro použití novější verze SQL Server Express LocalDB

- Upgrade databázového souboru pro použití novější verze SQL Server Express

- Práce s databázovým souborem v aplikaci Visual Studio, ale zachování kompatibility se staršími verzemi SQL Server Express nebo LocalDB

- Nastavit SQL Server Express výchozím databázovým strojem

  Pomocí sady Visual Studio můžete otevřít projekt, který obsahuje soubor databáze (. mdf), který byl vytvořen pomocí starší verze SQL Server Express nebo LocalDB. Chcete-li však pokračovat v vývoji projektu v aplikaci Visual Studio, musíte mít nainstalovanou verzi SQL Server Express nebo LocalDB nainstalované na stejném počítači jako Visual Studio nebo musíte upgradovat databázový soubor. Pokud provedete upgrade databázového souboru, nebudete k němu mít přístup pomocí starší verze SQL Server Express nebo LocalDB.

  Může se také zobrazit výzva k upgradu databázového souboru, který byl vytvořen v dřívější verzi SQL Server Express nebo LocalDB, pokud verze souboru není kompatibilní s instancí SQL Server Express nebo, která je aktuálně nainstalovaná. K vyřešení tohoto problému Visual Studio vás vyzve k upgradu souboru.

> [!IMPORTANT]
> Doporučujeme, abyste před upgradem souboru databáze zálohovali.

> [!WARNING]
> Pokud provedete upgrade souboru. mdf, který byl vytvořen v LocalDB 2014 (V12) 32 na LocalDB 2016 (v13), nebudete moci znovu otevřít soubor 32 v 16bitové verzi LocalDB.  V případě aktualizace 2 má LocalDB v13 jenom 64 bitů.

 Před upgradem databáze Vezměte v úvahu následující kritéria:

- NEUPGRADUJTE, pokud chcete pracovat na projektu jak ve starší verzi, tak v novější verzi sady Visual Studio.

- NEUPGRADUJTE, pokud se vaše aplikace bude používat v prostředích, která používají SQL Server Express spíše než LocalDB.

- NEUPGRADUJTE, pokud vaše aplikace používá vzdálená připojení, protože LocalDB je nepřijímá.

- NEUPGRADUJTE, pokud vaše aplikace spoléhá na Internetová informační služba (IIS).

- Zvažte upgrade, pokud chcete testovat databázové aplikace v prostředí izolovaného prostoru (sandbox), ale nechcete spravovat databázi.

### <a name="to-upgrade-a-database-file"></a>Postup upgradu databázového souboru

1. V **Průzkumník serveru**klikněte na tlačítko **připojit k databázi** .

2. V dialogovém okně **Přidat připojení** zadejte následující informace:

   - **Zdroj dat**: `Microsoft SQL Server (SqlClient)`

   - **Název serveru**:

       - Použití výchozí verze: `(localdb)\MSSQLLocalDB` .  Tím se zadáte buď ProjectV12 nebo ProjectV13, v závislosti na tom, která verze sady Visual Studio je nainstalovaná a kdy se vytvořila první instance LocalDB. Uzel **MSSQLLocalDB** v **Průzkumník objektů systému SQL Server** ukazuje, na kterou verzi odkazuje.

       - Použití konkrétní verze: `(localdb)\ProjectsV12` nebo `(localdb)\ProjectsV13` , kde V12 je LocalDB 2014 a v13 je LocalDB 2016.

   - **Připojit soubor databáze**: fyzická cesta primárního souboru. mdf.

   - **Logický název**: název, který chcete použít se souborem.

3. Vyberte tlačítko **OK**.

4. Až budete vyzváni, vyberte tlačítko **Ano** pro upgrade souboru.

   Databáze je upgradována, je připojena k databázovému stroji LocalDB a již není kompatibilní se starší verzí nástroje LocalDB.

   SQL Server Express připojení můžete také upravit tak, aby používalo LocalDB, a to tak, že otevřete místní nabídku pro připojení a pak vyberete **změnit připojení**. V dialogovém okně **Upravit připojení** změňte název serveru na `(LocalDB)\MSSQLLocalDB` . V dialogovém okně **Upřesnit vlastnosti** se ujistěte, že je **uživatelská instance** nastavená na **hodnotu NEPRAVDA**.

### <a name="to-upgrade-to-a-newer-version-of-sql-server-express"></a>Upgrade na novější verzi SQL Server Express

1. V místní nabídce pro připojení k databázi vyberte **Upravit připojení**.

2. V dialogovém okně **Upravit připojení** vyberte tlačítko **Upřesnit** .

3. V dialogovém okně **Upřesnit vlastnosti** vyberte tlačítko **OK** beze změny názvu serveru.

   Soubor databáze je upgradován tak, aby odpovídal aktuální verzi SQL Server Express.

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Pro práci s databází v aplikaci Visual Studio, ale zachování kompatibility s SQL Server Express

- V aplikaci Visual Studio otevřete projekt bez upgradu.

  - Chcete-li spustit projekt, vyberte klávesu F5.

  - Chcete-li upravit databázi, otevřete soubor MDF v **Průzkumník řešení**a rozbalte uzel v **Průzkumník serveru** pro práci s databází.

### <a name="to-make-sql-server-express-the-default-database-engine"></a>Zpřístupnění SQL Server Express výchozím databázovým strojem

1. Na panelu nabídek vyberte **Tools**  >  **Možnosti**nástroje.

2. V dialogovém okně **Možnosti** rozbalte položku možnosti **nástrojů pro data** a pak vyberte uzel **datová připojení** .

3. Do textového pole **název instance SQL Server** zadejte název instance SQL Server Express nebo LocalDB, které chcete použít. Pokud instance není pojmenována, zadejte `.\SQLEXPRESS or (localdb)\MSSQLLocalDB` .

4. Vyberte tlačítko **OK**.

   SQL Server Express budou výchozím databázovým strojem pro vaše aplikace.
