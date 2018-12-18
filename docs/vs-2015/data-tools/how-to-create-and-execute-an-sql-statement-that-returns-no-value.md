---
title: 'Postupy: vytvoření a provedení příkazu SQL, které nevrací žádnou hodnotu | Dokumentace Microsoftu'
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
- method calls, examples
- calling methods, examples
- SQL statements, executing
- SQL statements, creating
ms.assetid: 612d3046-0cfa-4d90-be6e-c4d6bcbd5aee
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 1768db097d2555726b17862c9c4a4b82a3e2a6a8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188601"
---
# <a name="how-to-create-and-execute-an-sql-statement-that-returns-no-value"></a>Postupy: Vytvoření a provedení příkazu SQL, který nevrací žádnou hodnotu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K provedení příkazu SQL, které nevrací žádnou hodnotu, můžete spustit dotaz TableAdapter, který je nakonfigurován ke spuštění příkazu SQL (například `CustomersTableAdapter.UpdateTableData(CustomersDataTable)`).  
  
 Pokud vaše aplikace nepoužívá objekty TableAdapter, zavolejte `ExecuteNonQuery` metodu na objekt příkazu nastavení jeho `CommandType` vlastnost <xref:System.Data.CommandType>. ("Objekt příkazu" odkazuje na konkrétní příkaz pro [zprostředkovatele dat .NET Framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) vaše aplikace používá. For example, pokud vaše aplikace používá zprostředkovatele dat .NET Framework pro SQL Server, objekt příkazu by <xref:System.Data.SqlClient.SqlCommand>.)  
  
 Následující příklady znázorňují způsob spouštění příkazů jazyka SQL, které vracejí žádná hodnota z databáze pomocí buď objekty TableAdapter nebo příkaz objekty. Další informace o dotazování s příkazy a objektů TableAdapters, naleznete v tématu [vyplnění datové sady s použitím objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
## <a name="executing-sql-statements-that-return-no-values-using-a-tableadapter"></a>Provádění příkazů SQL, které nevrací žádnou hodnotu pomocí prvku TableAdapter  
 Tento příklad ukazuje, jak vytvořit dotaz TableAdapter pomocí [úpravy objektů TableAdapter](../data-tools/editing-tableadapters.md), a pak poskytuje informace o tom, jak deklarovat instanci typu TableAdapter a spusťte dotaz.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-an-sql-statement-that-returns-no-value-using-a-tableadapter"></a>Chcete-li vytvořit příkaz SQL, které nevrací žádnou hodnotu pomocí prvku TableAdapter  
  
1.  Otevřete datovou sadu v **Návrhář Dataset**. Další informace najdete v tématu [postupy: otevření datové sady v návrháři datových sad](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Pokud již nemáte, vytvořte TableAdapter. Další informace o vytváření položek TableAdapters, naleznete v tématu [vytvoření a konfigurace objektů TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Pokud již máte dotaz na vaše TableAdapter, který používá příkazu SQL, které nevrací žádnou hodnotu, potom přejděte k dalšímu postupu "postup deklarovat instanci typu TableAdapter a spusťte dotaz." V opačném případě pokračujte krokem 4 vytvořte nový dotaz, který nevrací žádnou hodnotu.  
  
4.  Klikněte pravým tlačítkem na TableAdapter, které chcete a použijte místní nabídku přidání dotazu.  
  
     **Průvodce nastavením dotazu TableAdapter** otevře.  
  
5.  Ponechte výchozí hodnotu **použít SQL příkazy**a potom klikněte na tlačítko **Další**.  
  
6.  Zvolte **aktualizace**, **vložit** nebo **odstranit** možnost a potom klikněte na tlačítko **Další**.  
  
7.  Zadejte svůj příkaz SQL, nebo použít **Tvůrce dotazů** vám pomůže s vytvářením a potom klikněte na **Další**.  
  
8.  Zadejte název dotazu.  
  
9. Dokončete průvodce. dotaz je přidána do objektu TableAdapter.  
  
10. Sestavte projekt.  
  
#### <a name="to-declare-an-instance-of-the-tableadapter-and-execute-the-query"></a>Deklarujte instanci typu TableAdapter a spusťte dotaz  
  
1.  Deklarujte instanci TableAdapter, který obsahuje dotaz, který chcete spustit.  
  
    -   Chcete-li vytvořit instanci pomocí návrhových nástrojů, přetáhněte TableAdapter, který chcete z **nástrojů**. (Komponent ve vašem projektu teď budou zobrazovat v **nástrojů** pod nadpisem, která odpovídá názvu vašeho projektu.) Pokud TableAdapter se nezobrazují v **nástrojů**, pak budete muset svůj projekt sestavit.  
  
         -nebo-  
  
    -   K vytvoření instance v kódu, nahraďte následujícím kódem názvy vašich <xref:System.Data.DataSet> a TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  Objekty TableAdapter nejsou ve skutečnosti umístěný uvnitř své třídy přidružený objekt dataset. Každá datová sada má odpovídající kolekci objektů TableAdapter ve vlastním oboru názvů. Například, pokud máte datovou sadu s názvem `SalesDataSet`, bude `SalesDataSetTableAdapters` obor názvů, který obsahuje její objekty TableAdapter.  
  
2.  Volejte dotazu, jako by volání jakékoli jiné metody v kódu. Dotaz je metodu na objektu TableAdapter. Následující kód nahraďte názvy třídy TableAdapter a dotazu. Musíte taky předat parametry požadované vaším dotazem. Pokud si nejste jistí, jestli váš dotaz vyžaduje parametry, nebo jaké parametry se vyžaduje, zkontrolujte technologie IntelliSense pro požadovaný podpis dotazu. V závislosti na tom, jestli váš dotaz parametry nebo ne by vypadalo podobně jako na jednu z následujících příkladů kódu:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     Dotazy, které můžeme představit jako nevracející žádnou hodnotu vracet hodnotu – celé číslo obsahující počet řádků, které jsou ovlivněny dotazu. Kompletní kód deklarovat instanci objektu typu TableAdapter a spuštění dotazu by měl vypadat nějak takto:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#11)]
     [!code-vb[VbRaddataFillingAndExecuting#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#11)]  
  
## <a name="executing-sql-statements-that-return-no-value-using-a-command-object"></a>Provádění příkazů SQL, které vracejí žádná hodnota, pomocí příkazového objektu  
 Následující příklad ukazuje, jak vytvořit příkaz a provedení příkazu SQL, které nevrací žádnou hodnotu. Informace o nastavení a získání hodnot parametrů pro příkaz, naleznete v tématu [postupy: nastavení a získání parametrů pro objekty příkazu](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 V tomto příkladu <xref:System.Data.SqlClient.SqlCommand> objektu a vyžaduje:  
  
-   Odkazy <xref:System>, <xref:System.Data>, a <xref:System.Xml> obory názvů.  
  
-   Datové připojení s názvem `SqlConnection1`.  
  
-   Tabulku s názvem `Customers` data source `SqlConnection1` připojí k. (V opačném případě budete potřebovat platný příkaz SQL pro zdroj dat).  
  
#### <a name="to-execute-an-sql-statement-that-returns-no-value-using-a-datacommand"></a>K provedení příkazu SQL, které nevrací žádnou hodnotu očekává pomocí  
  
-   Přidejte následující kód k metodě, kterou chcete spustit příkaz jazyka SQL ze. Volání `ExecuteNonQuery` metody příkazu vrátit žádnou hodnotu (například <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>).  
  
     [!code-csharp[VbRaddataFillingAndExecuting#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#12)]
     [!code-vb[VbRaddataFillingAndExecuting#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#12)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Aplikace vyžaduje oprávnění k přístupu k databázi a spusťte příkaz jazyka SQL.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 [Postupy: vytváření dotazů TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Postupy: upravování dotazů TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Postupy: vyplnění datové sady s daty](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Vyplnění datové sady s použitím objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Postupy: nastavování a získávání parametrů pro objekty příkazu](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)