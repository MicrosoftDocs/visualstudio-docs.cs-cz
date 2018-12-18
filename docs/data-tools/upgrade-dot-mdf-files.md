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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 875208d068c791c0238c110ea0e83b04e18348fc
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117937"
---
# <a name="upgrade-mdf-files"></a>Upgrade souborů .mdf

Toto téma popisuje možnosti pro upgrade souboru databáze (*.mdf*) po instalaci novější verze sady Visual Studio. Obsahuje pokyny pro následující úkoly:

- Upgrade na novější verze systému SQL Server Express LocalDB souboru databáze

- Upgrade souboru databáze pro použití novější verze systému SQL Server Express

- Práci se souborem databáze v sadě Visual Studio, ale zachováte kompatibility se starší verzí systému SQL Server Express nebo LocalDB

- Ujistěte se, SQL Server Express výchozí databázový stroj

Visual Studio můžete otevřít projekt, který obsahuje databázový soubor (*.mdf*), byl vytvořen pomocí starší verze SQL Server Express nebo LocalDB. Však k dál vyvíjet projekt v sadě Visual Studio, musíte mít tuto verzi SQL Server Express nebo LocalDB nainstalovaná na stejném počítači jako Visual Studio, nebo je nutné upgradovat databázový soubor. Pokud provádíte upgrade databázový soubor, nebudete moct přistupovat pomocí starší verze systému SQL Server Express nebo LocalDB.

Budete také vyzváni k upgradu databázový soubor, který byl vytvořen pomocí dřívější verzi SQL Server Express nebo LocalDB, pokud verzi souboru není kompatibilní s instancí systému SQL Server Express nebo LocalDB, která je aktuálně nainstalována. K vyřešení problému, Visual Studio zobrazí výzvu k upgradu soubor.

> [!IMPORTANT]
> Doporučujeme, abyste před zahájením proveďte upgrade zálohování souboru databáze.

> [!WARNING]
> Pokud upgradujete *.mdf* soubor, který byl vytvořen v LocalDB 2014 (V12) 32bitové na instanci LocalDB 2016 (V13) nebo novější, nebude možné znovu otevřete soubor v 32bitové verzi LocalDB.

Před provedením upgradu databáze, vezměte v úvahu následující kritéria:

-   Neprovádějte upgrade, pokud chcete pracovat na projekt v starší verze a novější verze sady Visual Studio.

-   Neprovádějte upgrade, pokud se vaše aplikace bude používat v prostředích, která používá SQL Server Express namísto LocalDB.

-   Pokud vaše aplikace používá vzdálená připojení, nebudete upgradovat, protože LocalDB není přijměte je.

-   Neprovádějte upgrade, pokud vaše aplikace spoléhá na Internetové informační služby (IIS).

-   Pokud chcete otestovat databázové aplikace v prostředí izolovaného prostoru, ale nechcete, aby ke správě databáze, zvažte možnost upgradu.

### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>Upgrade souboru databáze na použití LocalDB verze

1.  V **Průzkumníka serveru**, vyberte **připojit k databázi** tlačítko.

2.  V **přidat připojení** dialogové okno pole, zadejte následující informace:

    -   **Zdroj dat**: `Microsoft SQL Server (SqlClient)`

    -   **Název serveru**:

        -   Chcete-li použít výchozí verze: `(localdb)\MSSQLLocalDB`.  Tímto určí ProjectV12 nebo ProjectV13, v závislosti na nainstalované verze sady Visual Studio a vytvoření první instanci LocalDB. **MSSQLLocalDB** uzlu v **Průzkumník objektů systému SQL Server** ukazuje, která verze bude ukazovat na.

        -   Chcete-li použít konkrétní verzi: `(localdb)\ProjectsV12` nebo `(localdb)\ProjectsV13`, kde je LocalDB 2014 verze 12 a V13 je LocalDB 2016.

    -   **Připojit soubor databáze**: fyzickou cestu primární *.mdf* souboru.

    -   **Logický název**: název, který chcete použít se souborem.

3.  Vyberte **OK** tlačítko.

4.  Když se zobrazí výzva, vyberte **Ano** tlačítko Upgrade souboru.

    Databáze je upgradovat, je připojen k databázovému stroji LocalDB a již není kompatibilní s starší verzi LocalDB.

Můžete také upravit připojení SQL Server Express pro použití LocalDB otevřením místní nabídku pro připojení a pak vyberete **upravit připojení**. V **upravit připojení** dialogové okno pole, změňte název serveru a `(LocalDB)\MSSQLLocalDB`. V **Upřesnit vlastnosti** dialogové okno pole, ujistěte se, že **uživatelskou instanci** je nastaven na **False**.

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>Upgrade souboru databáze používat verzi systému SQL Server Express

1.  V místní nabídce pro připojení k databázi, vyberte **upravit připojení**.

2.  V **upravit připojení** dialogové okno, vyberte **Upřesnit** tlačítko.

3.  V **Upřesnit vlastnosti** dialogové okno, vyberte **OK** tlačítko beze změny názvu serveru.

    Soubor databáze je upgradovat tak, aby odpovídala aktuální verze systému SQL Server Express.

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Práce s databází v sadě Visual Studio, ale zachování kompatibility s SQL Server Express

-   V sadě Visual Studio otevřete projekt bez upgradování.

    -   Chcete-li spustit projekt, vyberte **F5** klíč.

    -   Chcete-li upravit databázi, otevřete *.mdf* souboru v **Průzkumníku řešení**a rozbalte uzel v **Průzkumníka serveru** pro práci s vaší databáze.

### <a name="to-make-sql-server-express-the-default-database-engine"></a>Chcete-li systém SQL Server Express výchozí databázový stroj

1.  Na panelu nabídek vyberte **nástroje** > **možnosti**.

2.  V **možnosti** dialogové okno, rozbalte seznam **databázové nástroje** možnosti a pak vyberte **datová připojení**.

3.  V **název Instance systému SQL Server** textové pole, zadejte název instance systému SQL Server Express nebo LocalDB, který chcete použít. Pokud není název instance, zadejte `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB`.

4.  Vyberte **OK** tlačítko.

    SQL Server Express, bude výchozí databázový stroj pro vaše aplikace.

## <a name="see-also"></a>Viz také:

- [Přístup k datům v sadě Visual Studio](accessing-data-in-visual-studio.md)