---
title: Datové nástroje proC++
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CPP
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: 33c91a7c21a04624d71692d12b7a7f15a16e1d67
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72639508"
---
# <a name="visual-studio-data-tools-for-c"></a>Datové nástroje sady Visual Studio pro C++

Nativní C++ může často poskytovat nejrychlejší výkon při přístupu ke zdrojům dat. Nástroje data pro C++ aplikace v aplikaci Visual Studio však nejsou tak snadné, protože jsou pro aplikace .NET. Například okno **zdroje dat** nelze použít k přetahování datových zdrojů na C++ návrhovou plochu. Pokud potřebujete objektově-relační vrstvu, budete muset napsat vlastní nebo použít produkt třetí strany. Totéž platí pro funkce vázání dat, i když aplikace, které používají knihovnu Microsoft Foundation Class Library, mohou použít některé databázové třídy spolu s dokumenty a zobrazeními k ukládání dat do paměti a jejich zobrazení uživateli. Další informace najdete v tématu [přístup k datům v C++vizuálu ](/cpp/data/data-access-in-cpp).

Aby bylo možné se připojit k databázím SQL, nativní C++ aplikace mohou používat ovladače ODBC a OLE DB a poskytovatele ADO, kteří jsou součástí systému Windows. Ty se můžou připojit k libovolné databázi, která tato rozhraní podporuje. Ovladač ODBC je standardem. OLE DB je k dispozici kvůli zpětné kompatibilitě. Další informace o těchto technologiích dat najdete v tématu [součásti Windows Data Access](/previous-versions/windows/desktop/ms692897(v=vs.85)).

Pokud chcete využít vlastní funkce v SQL Server 2005 a novějších, použijte [klienta SQL Server Native](/sql/relational-databases/native-client/sql-server-native-client). Nativní klient také obsahuje ovladač SQL Server ODBC a poskytovatele SQL Server OLE DB v jedné nativní dynamické knihovně (DLL). Tyto aplikace podpory používají rozhraní API nativního kódu (ODBC, OLE DB a ADO) k Microsoft SQL Server. SQL Server Native Client se instaluje pomocí nástrojů SQL Server Data Tools. Průvodce programováním je tady: [SQL Server Nativní programování klienta](/sql/relational-databases/native-client/sql-server-native-client-programming).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Připojení k localDB prostřednictvím rozhraní ODBC a SQL Native Client z C++ aplikace

1. Nainstalujte nástroje SQL Server Data Tools.

2. Pokud potřebujete ukázkovou databázi SQL, ke které se chcete připojit, Stáhněte databázi Northwind a rozbalte ji do nového umístění.

3. Pomocí SQL Server Management Studio připojte k localDB soubor *. mdf* pro extrahování. Když se SQL Server Management Studio spustí, připojte se (LocalDB) \MSSQLLocalDB.

   ![Dialogové okno SSMS Connect](../data-tools/media/raddata-ssms-connect-dialog.png)

   Pak v levém podokně klikněte pravým tlačítkem na uzel LocalDB a vyberte **připojit**.

   ![SSMS připojit databázi](../data-tools/media/raddata-ssms-attach-database.png)

4. Stáhněte si ukázku Windows SDK ODBC a rozbalte ji do nového umístění. Tato ukázka zobrazuje základní příkazy ODBC, které slouží k připojení k databázi a vydávání dotazů a příkazů. Další informace o těchto funkcích najdete v části [Microsoft Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc). Při prvním načtení řešení (je ve C++ složce) bude Visual Studio nabízet upgrade řešení na aktuální verzi sady Visual Studio. Klikněte na tlačítko **Ano**.

5. Chcete-li použít nativního klienta, budete potřebovat soubor *hlaviček* a soubor *lib* . Tyto soubory obsahují funkce a definice, které jsou specifické pro SQL Server, nad rámec funkcí rozhraní ODBC definovaných v SQL. h. V okně**vlastnosti** **projektu**  >   > **adresáře VC + +** přidejte následující adresář include:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

   A tento adresář knihovny:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6. Přidejte tyto řádky do *ODBCSQL. cpp*. #Define brání kompilování nepodstatných OLE DB definic.

   ```cpp
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Všimněte si, že vzorek ve skutečnosti nepoužívá žádnou z nativních funkcí klienta, takže předchozí kroky není nutné, aby je bylo možné zkompilovat a spustit. Ale projekt je teď nakonfigurovaný, abyste mohli tuto funkci používat. Další informace najdete v tématu [SQL Server Native Client programování](/sql/relational-databases/native-client/sql-server-native-client).

7. Určete, který ovladač se má použít v subsystému rozhraní ODBC. Ukázka předá atribut připojovacího řetězce ovladače v podobě argumentu příkazového řádku. V  > **vlastnosti** **projektu**  > **ladění**přidejte tento argument příkazu:

   ```cpp
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Stisknutím klávesy **F5** Sestavte a spusťte aplikaci. Mělo by se zobrazit dialogové okno z ovladače, který vás vyzve k zadání databáze. Zadejte `(localdb)\MSSQLLocalDB` a ověřte **použití důvěryhodného připojení**. Stiskněte **OK**. Měla by se zobrazit konzola se zprávami, které indikují úspěšné připojení. Měl by se zobrazit také příkazový řádek, kde můžete zadat příkaz SQL. Následující obrazovka ukazuje příklad dotazu a výsledků:

   ![Výstup ukázkového dotazu ODBC](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>Viz také:

- [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)