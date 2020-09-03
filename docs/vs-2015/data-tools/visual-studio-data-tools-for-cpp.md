---
title: Visual Studio Data Tools for C++ | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 3a3849d9-1bc7-47d1-805e-1755223ccba2
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: ec68d54ced85737d66c64ca2dbf7942ca81e5314
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72621213"
---
# <a name="visual-studio-data-tools-for-c"></a>Datové nástroje sady Visual Studio pro C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nativní jazyk C++ může často poskytovat nejrychlejší výkon při přístupu ke zdrojům dat. Nástroje pro data v aplikacích C++ v aplikaci Visual Studio však nejsou tak snadné, protože jsou pro aplikace .NET. Například okna zdrojů dat nelze použít k přetahování zdrojů dat na návrhovou plochu jazyka C++. Pokud potřebujete objektově-relační vrstvu, budete muset napsat vlastní nebo použít produkt třetí strany.  Totéž platí pro funkce vázání dat, i když aplikace, které používají knihovnu Microsoft Foundation Class Library, mohou použít některé databázové třídy spolu s dokumenty a zobrazeními k ukládání dat do paměti a jejich zobrazení uživateli. Další informace najdete v tématu [přístup k datům v Visual C++](https://msdn.microsoft.com/library/7wtdsdkh.aspx) .

 Pro připojení k databázím SQL mohou nativní aplikace C++ používat ovladače ODBC a OLE DB a poskytovatele ADO, který je součástí systému Windows.     Ty se můžou připojit k libovolné databázi, která tato rozhraní podporuje. Ovladač ODBC je standardem. OLE DB je k dispozici kvůli zpětné kompatibilitě. Další informace o těchto technologiích dat najdete v tématu [součásti Windows Data Access](https://msdn.microsoft.com/library/windows/desktop/aa968814\(v=vs.85\).aspx) .

 Pokud chcete využít výhod vlastních funkcí v SQL Server 2005 a novějších, použijte [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733). Nativní klient také obsahuje ovladač SQL Server ODBC a poskytovatele SQL Server OLE DB v jedné nativní dynamické knihovně (DLL). Tyto aplikace podpory používají rozhraní API nativního kódu (ODBC, OLE DB a ADO) k Microsoft SQL Server.  SQL Server Native Client se instaluje pomocí nástrojů SQL Server Data Tools. Průvodce programováním je tady: [SQL Server Native Client programování](https://msdn.microsoft.com/library/ms130892.aspx).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Připojení k localDB prostřednictvím rozhraní ODBC a SQL Native Client z aplikace C++

1. Nainstalujte nástroje SQL Server Data Tools.

2. Pokud potřebujete ukázkovou databázi SQL, ke které se chcete připojit, Stáhněte databázi Northwind a rozbalte ji do nového umístění.

3. Pomocí SQL Server Management Studio připojte k localDB soubor. mdf pro extrahování. Když se SQL Server Management Studio spustí, připojte se (LocalDB) \MSSQLLocalDB.

    ![Dialogové okno SSMS Connect](../data-tools/media/raddata-ssms-connect-dialog.png "Dialogové okno raddata SSMS Connect")

    Pak v levém podokně klikněte pravým tlačítkem na uzel LocalDB a vyberte **připojit**.

    ![SSMS připojit databázi](../data-tools/media/raddata-ssms-attach-database.png "raddata SSMS připojit databázi")

4. Stáhněte si ukázku Windows SDK ODBC a rozbalte ji do nového umístění. Tato ukázka zobrazuje základní příkazy ODBC, které slouží k připojení k databázi a vydávání dotazů a příkazů. Další informace o těchto funkcích najdete v části [Microsoft Open Database Connectivity (ODBC)](https://msdn.microsoft.com/library/windows/desktop/ms710252\(v=vs.85\).aspx). Při prvním načtení řešení (je ve složce C++) bude Visual Studio nabízet upgrade řešení na aktuální verzi sady Visual Studio. Klikněte na **Ano**.

5. Chcete-li použít nativního klienta, budete potřebovat soubor hlaviček a soubor LIB. Tyto soubory obsahují funkce a definice, které jsou specifické pro SQL Server, nad rámec funkcí rozhraní ODBC definovaných v SQL. h. V **Project**  >  okně**vlastnosti**projektu  >  **VC + +** přidejte následující adresář include:

   ** \<system drive> : \Program Files\Microsoft SQL Server\110\SDK\Include** a tento adresář knihovny:

   **c:\Program Files\Microsoft SQL Server\110\SDK\Lib**

6. Přidejte tyto řádky do ODBCSQL. cpp. #Define brání kompilování nepodstatných OLE DB definic.

   ```
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Všimněte si, že vzorek ve skutečnosti nepoužívá žádnou z nativních funkcí klienta, takže předchozí kroky není nutné, aby je bylo možné zkompilovat a spustit. Ale projekt je teď nakonfigurovaný, abyste mohli tuto funkci používat. Další informace najdete v tématu [SQL Server Native Client programování](https://msdn.microsoft.com/library/ms130892\(v=sql.130\).aspx).

7. Určete, který ovladač se má použít v subsystému rozhraní ODBC. Ukázka předá atribut připojovacího řetězce ovladače v podobě argumentu příkazového řádku. V **Project**  >  **Možnosti**  >  **ladění**vlastností projektu přidejte tento argument příkazu:

   ```
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Stisknutím klávesy F5 aplikaci sestavíte a spustíte. Mělo by se zobrazit dialogové okno z ovladače, který vás vyzve k zadání databáze. Zadejte `(localdb)\MSSQLLocalDB` a ověřte **použití důvěryhodného připojení**. Stiskněte **OK**. Měla by se zobrazit konzola se zprávami, které indikují úspěšné připojení. Měl by se zobrazit také příkazový řádek, kde můžete zadat příkaz SQL. Následující obrazovka ukazuje příklad dotazu a výsledků:

    ![Výstup ukázkového dotazu ODBC](../data-tools/media/raddata-odbc-sample-query-output.png "výstup ukázkového dotazu raddata ODBC")

## <a name="see-also"></a>Viz také
 [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
