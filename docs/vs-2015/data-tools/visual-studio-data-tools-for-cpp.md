---
title: Visual Studio data tools pro C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a3849d9-1bc7-47d1-805e-1755223ccba2
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 030e142911078aec36b01335c8fb3aaa4d82ac78
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849642"
---
# <a name="visual-studio-data-tools-for-c"></a>Visual Studio data tools pro C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Nativní kód C++ často poskytují nejrychlejší výkon při přístupu k zdroje dat. Nástroje pro aplikace C++ v sadě Visual Studio data však není bohaté, protože je pro aplikace .NET. Například okna zdroje dat nelze přetáhnout zdroje dat na návrhovou plochu C++. Pokud potřebujete objektově relační vrstvy, budete muset napište vlastní, nebo použijte produkt jiného výrobce.  Totéž platí pro datovou vazbu funkce, i když se aplikace, které používají knihovnu Microsoft Foundation Class můžete použít některé databázových tříd s dokumenty a zobrazeními, ukládat data v paměti a zobrazí uživateli. Další informace najdete v tématu [přístup k datům v jazyce Visual C++](https://msdn.microsoft.com/library/7wtdsdkh.aspx) .  
  
 Pro připojení k SQL Database, můžete použít nativní aplikace C++ ovladače rozhraní ODBC a OLE DB a ADO poskytovatele, které jsou součástí Windows.     Ty můžete připojit k libovolné databázi, která podporuje těchto rozhraní. Ovladač ODBC je standardem. OLE DB je k dispozici z důvodu zpětné kompatibility. Další informace o těchto technologií ještě používáte dat najdete v tématu [Windows Data Access Components](https://msdn.microsoft.com/library/windows/desktop/aa968814\(v=vs.85\).aspx)  
  
 Využijte vlastní funkce v systému SQL Server 2005 a novější, použijte [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733). Nativní klient také obsahuje ovladač ODBC systému SQL Server a SQL Server zprostředkovatele OLE DB v jedné nativní dynamické knihovny (DLL). Tato podpora aplikací rozhraní API nativního kódu (ODBC, Oledb a ADO) pro Microsoft SQL Server.  Nativní klient systému SQL Server nainstaluje SQL Server Data Tools. Průvodce programováním je tady: [SQL Server nativního klienta programování](https://msdn.microsoft.com/library/ms130892.aspx).  
  
## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Pro připojení na instanci localDB prostřednictvím rozhraní ODBC a jazyku SQL Native Client z aplikace v jazyce C++  
  
1. Nainstalujte SQL Server Data Tools.  
  
2. Pokud budete potřebovat pro připojení k ukázkové databáze SQL, stáhněte si databázi Northwind a rozbalte ho do nového umístění.  
  
3. Slouží k připojení souboru rozzipovaný Northwind.mdf na instanci localDB systému SQL Server Management Studio. Při spuštění systému SQL Server Management Studio, připojte se k (localdb) \MSSQLLocalDB.  
  
    ![Dialogové okno připojení přes SSMS](../data-tools/media/raddata-ssms-connect-dialog.png "raddata SSMS připojit dialogového okna")  
  
    Klikněte pravým tlačítkem na uzel localdb v levém podokně a zvolte **připojit**.  
  
    ![SSMS připojit databáze](../data-tools/media/raddata-ssms-attach-database.png "raddata SSMS připojit databáze")  
  
4. Stáhněte si ukázku Windows SDK rozhraní ODBC a rozbalte ho do nového umístění. Tento příklad ukazuje základní příkazy rozhraní ODBC, které se používají pro připojení k databázi a problém dotazy a příkazy. Další informace o těchto funkcích v [Microsoft připojení ODBC (Open Database)](https://msdn.microsoft.com/library/windows/desktop/ms710252\(v=vs.85\).aspx). Při prvním načtení řešení (je ve složce C++), Visual Studio nabídne upgrade řešení na aktuální verzi sady Visual Studio. Klikněte na tlačítko **Ano**.  
  
5. Použití nativního klienta, budete potřebovat jeho hlavičkový soubor a soubor lib. Tyto soubory obsahují funkce a definice specifické pro SQL Server, nad rámec funkcí ODBC definované v sql.h. V **projektu** > **vlastnosti** > **adresáře VC ++**, přidejte adresář include následující:  
  
   **\<systémová jednotka >: \Program Files\Microsoft SQL Server\110\SDK\Include** a tento adresář knihovny:  
  
   **c:\Program Files\Microsoft SQL Server\110\SDK\Lib**  
  
6. Přidejte tyto řádky odbcsql.cpp. #Define brání relevantní technologie OLE DB definice z kompilován.  
  
   ```  
   #define _SQLNCLI_ODBC_  
   #include <sqlncli.h>  
   ```  
  
    Všimněte si, že ukázky nepoužívá ve skutečnosti některé funkce nativního klienta, takže předchozí kroky nejsou nutné, aby se zkompilovat a spustit. Ale projekt je nyní nakonfigurován pro použití této funkce. Další informace najdete v tématu [SQL Server nativního klienta programování](https://msdn.microsoft.com/library/ms130892\(v=sql.130\).aspx).  
  
7. Určete, který ovladač pro použití v subsystém rozhraní ODBC. Ukázka předá atribut ovladač připojovacího řetězce v jako argument příkazového řádku. V **projektu** > **vlastnosti** > **ladění**, přidejte tento argument příkazu:  
  
   ```  
   DRIVER="SQL Server Native Client 11.0"  
   ```  
  
8. Stisknutím klávesy F5 sestavte a spusťte aplikaci. Zobrazí se dialogové okno z ovladače, který vás vyzve k zadání databáze. Zadejte `(localdb)\MSSQLLocalDB`a zkontrolujte **použít důvěryhodné připojení**. Stisknutím klávesy **OK**. Měli byste vidět konzoly s zprávy, které označují úspěšné připojení. Měli byste vidět také příkazového řádku můžete zadat v příkazu SQL. Následující obrazovka ukazuje příklad dotazu a výsledky:  
  
    ![ODBC ukázkový výstup dotazu](../data-tools/media/raddata-odbc-sample-query-output.png "raddata ODBC ukázkový dotaz výstup")  
  
## <a name="see-also"></a>Viz také  
 [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)


