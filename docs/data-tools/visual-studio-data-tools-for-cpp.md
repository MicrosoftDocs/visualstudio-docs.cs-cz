---
title: Data tools pro C++
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CPP
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: 4c247d693da287581b8ab163880e9cecf4aeb17c
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304914"
---
# <a name="visual-studio-data-tools-for-c"></a>Visual Studio data tools pro C++

Nativní kód C++ často poskytují nejrychlejší výkon při přístupu k zdroje dat. Nástroje pro aplikace C++ v sadě Visual Studio data však není bohaté, protože je pro aplikace .NET. Například **zdroje dat** okno nejde přetáhnout zdroje dat na návrhovou plochu C++. Pokud potřebujete objektově relační vrstvy, budete muset napište vlastní, nebo použijte produkt jiného výrobce. Totéž platí pro datovou vazbu funkce, i když se aplikace, které používají knihovnu Microsoft Foundation Class můžete použít některé databázových tříd s dokumenty a zobrazeními, ukládat data v paměti a zobrazí uživateli. Další informace najdete v tématu [přístup k datům v jazyce Visual C++](/cpp/data/data-access-in-cpp).

Pro připojení k SQL Database, můžete použít nativní aplikace C++ ovladače rozhraní ODBC a OLE DB a ADO poskytovatele, které jsou součástí Windows. Ty můžete připojit k libovolné databázi, která podporuje těchto rozhraní. Ovladač ODBC je standardem. OLE DB je k dispozici z důvodu zpětné kompatibility. Další informace o těchto technologií ještě používáte dat najdete v tématu [Windows Data Access Components](/previous-versions/windows/desktop/ms692897(v=vs.85)).

Využijte vlastní funkce v systému SQL Server 2005 a novější, použijte [Nativní klient systému SQL Server](/sql/relational-databases/native-client/sql-server-native-client). Nativní klient také obsahuje ovladač ODBC systému SQL Server a SQL Server zprostředkovatele OLE DB v jedné nativní dynamické knihovny (DLL). Tato podpora aplikací rozhraní API nativního kódu (ODBC, Oledb a ADO) pro Microsoft SQL Server. Nativní klient systému SQL Server nainstaluje SQL Server Data Tools. Průvodce programováním je tady: [Nativní klient systému SQL Server programování](/sql/relational-databases/native-client/sql-server-native-client-programming).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Pro připojení na instanci localDB prostřednictvím rozhraní ODBC a jazyku SQL Native Client z aplikace v jazyce C++

1. Nainstalujte SQL Server Data Tools.

2. Pokud budete potřebovat pro připojení k ukázkové databáze SQL, stáhněte si databázi Northwind a rozbalte ho do nového umístění.

3. Pomocí SQL Server Management Studio k připojení rozzipovaný *Northwind.mdf* souboru na instanci localDB. Při spuštění systému SQL Server Management Studio, připojte se k (localdb) \MSSQLLocalDB.

   ![Dialogové okno připojení přes SSMS](../data-tools/media/raddata-ssms-connect-dialog.png)

   Klikněte pravým tlačítkem na uzel localdb v levém podokně a zvolte **připojit**.

   ![SSMS připojit databázi](../data-tools/media/raddata-ssms-attach-database.png)

4. Stáhněte si ukázku Windows SDK rozhraní ODBC a rozbalte ho do nového umístění. Tento příklad ukazuje základní příkazy rozhraní ODBC, které se používají pro připojení k databázi a problém dotazy a příkazy. Další informace o těchto funkcích v [Microsoft připojení ODBC (Open Database)](/sql/odbc/microsoft-open-database-connectivity-odbc). Při prvním načtení řešení (je ve složce C++), Visual Studio nabídne upgrade řešení na aktuální verzi sady Visual Studio. Klikněte na tlačítko **Ano**.

5. Použití nativního klienta, budete potřebovat jeho *záhlaví* souboru a *lib* souboru. Tyto soubory obsahují funkce a definice specifické pro SQL Server, nad rámec funkcí ODBC definované v sql.h. V **projektu** > **vlastnosti** > **adresáře VC ++**, přidejte adresář include následující:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

   A tento adresář knihovny:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6. Přidejte tyto řádky v *odbcsql.cpp*. #Define brání relevantní technologie OLE DB definice z kompilován.

   ```cpp
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Všimněte si, že ukázky nepoužívá ve skutečnosti některé funkce nativního klienta, takže předchozí kroky nejsou nutné, aby se zkompilovat a spustit. Ale projekt je nyní nakonfigurován pro použití této funkce. Další informace najdete v tématu [SQL Server Native Client programování](/sql/relational-databases/native-client/sql-server-native-client).

7. Určete, který ovladač pro použití v subsystém rozhraní ODBC. Ukázka předá atribut ovladač připojovacího řetězce v jako argument příkazového řádku. V **projektu** > **vlastnosti** > **ladění**, přidejte tento argument příkazu:

   ```cpp
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Stisknutím klávesy **F5** sestavíte a spustíte aplikaci. Zobrazí se dialogové okno z ovladače, který vás vyzve k zadání databáze. Zadejte `(localdb)\MSSQLLocalDB`a zkontrolujte **použít důvěryhodné připojení**. Stisknutím klávesy **OK**. Měli byste vidět konzoly s zprávy, které označují úspěšné připojení. Měli byste vidět také příkazového řádku můžete zadat v příkazu SQL. Následující obrazovka ukazuje příklad dotazu a výsledky:

   ![Výstup dotazu ukázkové rozhraní ODBC](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>Viz také:

- [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)