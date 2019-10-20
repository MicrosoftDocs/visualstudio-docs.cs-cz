---
title: Upgrade souborů .mdf
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e0196c582fbe673d73c7aeb89280d05e11a071a5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72639572"
---
# <a name="upgrade-mdf-files"></a>Upgrade souborů .mdf

Toto téma popisuje možnosti upgradu databázového souboru ( *. mdf*) po instalaci novější verze sady Visual Studio. Obsahuje pokyny pro následující úlohy:

- Upgrade databázového souboru pro použití novější verze SQL Server Express LocalDB

- Upgrade databázového souboru pro použití novější verze SQL Server Express

- Práce s databázovým souborem v aplikaci Visual Studio, ale zachování kompatibility se staršími verzemi SQL Server Express nebo LocalDB

- Nastavit SQL Server Express výchozím databázovým strojem

Pomocí sady Visual Studio můžete otevřít projekt, který obsahuje soubor databáze ( *. mdf*), který byl vytvořen pomocí starší verze SQL Server Express nebo LocalDB. Chcete-li však pokračovat v vývoji projektu v aplikaci Visual Studio, musíte mít nainstalovanou verzi SQL Server Express nebo LocalDB nainstalované na stejném počítači jako Visual Studio nebo musíte upgradovat databázový soubor. Pokud provedete upgrade databázového souboru, nebudete k němu mít přístup pomocí starší verze SQL Server Express nebo LocalDB.

Může se také zobrazit výzva k upgradu databázového souboru, který byl vytvořen v dřívější verzi SQL Server Express nebo LocalDB, pokud verze souboru není kompatibilní s instancí SQL Server Express nebo, která je aktuálně nainstalovaná. K vyřešení tohoto problému Visual Studio vás vyzve k upgradu souboru.

> [!IMPORTANT]
> Doporučujeme, abyste před upgradem souboru databáze zálohovali.

> [!WARNING]
> Pokud upgradujete soubor *. mdf* , který byl vytvořen v LocalDB 2014 (V12) 32 na LocalDB 2016 (v13) nebo novější, nebudete moci znovu otevřít soubor 32 v 16bitové verzi LocalDB.

Před upgradem databáze Vezměte v úvahu následující kritéria:

- NEUPGRADUJTE, pokud chcete pracovat na projektu jak ve starší verzi, tak v novější verzi sady Visual Studio.

- NEUPGRADUJTE, pokud se vaše aplikace bude používat v prostředích, která používají SQL Server Express spíše než LocalDB.

- NEUPGRADUJTE, pokud vaše aplikace používá vzdálená připojení, protože LocalDB je nepřijímá.

- NEUPGRADUJTE, pokud vaše aplikace spoléhá na Internetová informační služba (IIS).

- Zvažte upgrade, pokud chcete testovat databázové aplikace v prostředí izolovaného prostoru (sandbox), ale nechcete spravovat databázi.

### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>Postup upgradu databázového souboru tak, aby používal verzi LocalDB

1. V **Průzkumník serveru**klikněte na tlačítko **připojit k databázi** .

2. V dialogovém okně **Přidat připojení** zadejte následující informace:

    - **Zdroj dat**: `Microsoft SQL Server (SqlClient)`

    - **Název serveru**:

        - Chcete-li použít výchozí verzi: `(localdb)\MSSQLLocalDB`.  Tím se zadáte buď ProjectV12 nebo ProjectV13, v závislosti na tom, která verze sady Visual Studio je nainstalovaná a kdy se vytvořila první instance LocalDB. Uzel **MSSQLLocalDB** v **Průzkumník objektů systému SQL Server** ukazuje, na kterou verzi odkazuje.

        - Použití konkrétní verze: `(localdb)\ProjectsV12` nebo `(localdb)\ProjectsV13`, kde V12 je LocalDB 2014 a v13 je LocalDB 2016.

    - **Připojit soubor databáze**: fyzická cesta primárního souboru *. mdf* .

    - **Logický název**: název, který chcete použít se souborem.

3. Klikněte na tlačítko **OK** .

4. Až budete vyzváni, vyberte tlačítko **Ano** pro upgrade souboru.

    Databáze je upgradována, je připojena k databázovému stroji LocalDB a již není kompatibilní se starší verzí nástroje LocalDB.

SQL Server Express připojení můžete také upravit tak, aby používalo LocalDB, a to tak, že otevřete místní nabídku pro připojení a pak vyberete **změnit připojení**. V dialogovém okně **Upravit připojení** změňte název serveru na `(LocalDB)\MSSQLLocalDB`. V dialogovém okně **Upřesnit vlastnosti** se ujistěte, že je **uživatelská instance** nastavená na **hodnotu NEPRAVDA**.

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>Postup upgradu databázového souboru tak, aby používal verzi SQL Server Express

1. V místní nabídce pro připojení k databázi vyberte **Upravit připojení**.

2. V dialogovém okně **Upravit připojení** vyberte tlačítko **Upřesnit** .

3. V dialogovém okně **Upřesnit vlastnosti** vyberte tlačítko **OK** beze změny názvu serveru.

    Soubor databáze je upgradován tak, aby odpovídal aktuální verzi SQL Server Express.

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Pro práci s databází v aplikaci Visual Studio, ale zachování kompatibility s SQL Server Express

- V aplikaci Visual Studio otevřete projekt bez upgradu.

  - Chcete-li spustit projekt, vyberte klávesu **F5** .

  - Chcete-li upravit databázi, otevřete soubor *MDF* v **Průzkumník řešení**a rozbalte uzel v **Průzkumník serveru** pro práci s databází.

### <a name="to-make-sql-server-express-the-default-database-engine"></a>Zpřístupnění SQL Server Express výchozím databázovým strojem

1. Na panelu nabídek vyberte možnost **nástroje**  > **Možnosti**.

2. V dialogovém okně **Možnosti** rozbalte možnosti **nástroje databáze** a pak vyberte **datová připojení**.

3. Do textového pole **název instance SQL Server** zadejte název instance SQL Server Express nebo LocalDB, které chcete použít. Pokud instance není pojmenována, zadejte `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB`.

4. Klikněte na tlačítko **OK** .

    SQL Server Express budou výchozím databázovým strojem pro vaše aplikace.

## <a name="see-also"></a>Viz také:

- [Přístup k datům v sadě Visual Studio](accessing-data-in-visual-studio.md)
