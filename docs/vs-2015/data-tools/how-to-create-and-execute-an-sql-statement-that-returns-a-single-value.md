---
title: 'Postupy: vytvoření a provedení příkazu SQL, který vrací jedinou hodnotu | Dokumentace Microsoftu'
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
- data reader
- scalar values
- stored procedures, returning single value
- SQL statements, data commands
- DataReader object
- data commands, returning scalar values
ms.assetid: eb366496-69e5-4462-8683-653054165c5c
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 7d5d57637a25db62832ad535bbad60214a0aa4ad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192150"
---
# <a name="how-to-create-and-execute-an-sql-statement-that-returns-a-single-value"></a>Postupy: Vytvoření a provedení příkazu SQL, který vrací jedinou hodnotu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K provedení příkazu SQL, který vrací jedinou hodnotu, můžete spustit dotaz TableAdapter, který je nakonfigurován ke spuštění příkazu SQL (například `CustomersTableAdapter.CustomerCount()`).  
  
 Pokud vaše aplikace nepoužívá objekty TableAdapter, zavolejte `ExecuteScalar` metodu na objekt příkazu nastavení jeho `CommandType` vlastnost <xref:System.Data.CommandType>. ("Objekt příkazu" odkazuje na konkrétní příkaz pro [zprostředkovatele dat .NET Framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) vaše aplikace používá. For example, pokud vaše aplikace používá zprostředkovatele dat .NET Framework pro SQL Server, objekt příkazu by <xref:System.Data.SqlClient.SqlCommand>.)  
  
 Následující příklady ukazují, jak spouštět příkazy SQL, které vrátí jednu hodnotu v databázi pomocí buď objekty TableAdapter nebo příkaz objekty. Další informace o dotazování s příkazy a objektů TableAdapters, naleznete v tématu [vyplnění datové sady s použitím objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="executing-sql-statements-that-return-single-values-using-a-tableadapter"></a>Provádění příkazů SQL, které vrátí jednu hodnotu pomocí prvku TableAdapter  
 Tento příklad ukazuje, jak vytvořit dotaz TableAdapter pomocí [úpravy objektů TableAdapter](../data-tools/editing-tableadapters.md), a pak poskytuje informace o tom, jak deklarovat instanci typu TableAdapter a spusťte dotaz.  
  
#### <a name="to-create-an-sql-statement-returning-a-single-value-using-a-tableadapter"></a>Chcete-li vytvořit příkaz SQL, vrátí jednu hodnotu pomocí prvku TableAdapter  
  
1.  Otevřete datovou sadu v **Návrhář Dataset**. Další informace najdete v tématu [postupy: otevření datové sady v návrháři datových sad](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Pokud již nemáte, vytvořte TableAdapter. Další informace o vytváření položek TableAdapters, naleznete v tématu [vytvoření a konfigurace objektů TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Pokud již máte dotaz na vaše TableAdapter, které vrátí jednu hodnotu pomocí příkazu SQL, přejděte k dalšímu postupu "postup deklarovat instanci typu TableAdapter a spusťte dotaz." V opačném případě pokračujte krokem 4 vytvořte nový dotaz, který vrací jedinou hodnotu.  
  
4.  Klikněte pravým tlačítkem na TableAdapter, které chcete a použijte místní nabídku přidání dotazu.  
  
     **Průvodce nastavením dotazu TableAdapter** otevře.  
  
5.  Ponechte výchozí hodnotu **použít SQL příkazy**a potom klikněte na tlačítko **Další**.  
  
6.  Zvolte **vybrat, které vrátí jednu hodnotu** možnost a potom klikněte na tlačítko **Další**.  
  
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
        >  Objekty TableAdapter nejsou ve skutečnosti umístěný uvnitř své třídy přidružený objekt dataset. Každá datová sada má odpovídající kolekci objektů TableAdapter ve vlastním oboru názvů. Například, pokud máte datovou sadu s názvem `SalesDataSet`, pak by byl `SalesDataSetTableAdapters` obor názvů, který obsahuje její objekty TableAdapter.  
  
2.  Volejte dotazu, jako by volání jakékoli jiné metody v kódu. Dotaz je metodu na objektu TableAdapter. Následující kód nahraďte názvy třídy TableAdapter a dotazu. Také je nutné předat parametry požadované vaším dotazem a udělat něco s návratovou hodnotou (například přiřadit ho k proměnné). Pokud si nejste jistí, jestli váš dotaz vyžaduje parametry, nebo jaké parametry se vyžaduje, zkontrolujte technologie IntelliSense pro požadovaný podpis dotazu. V závislosti na tom, jestli váš dotaz parametry nebo ne by vypadalo podobně jako na jednu z následujících příkladů kódu:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
3.  Pravděpodobně je potřeba přiřadit hodnoty vrácené dotazem na proměnnou. Dotazy objektu TableAdapter, které vrátí jednu hodnotu vrátit datový typ na základě dotazu (nikoli `ExecuteScalar` metodu, která vrací objekt). Například pokud váš dotaz TableAdapter vybere jeden sloupec, jehož datový typ je celé číslo, návratová hodnota dotazu je celé číslo. Pokud sloupec povoluje hodnoty null, vrácená hodnota je jeden z typů s povolenou hodnotou Null (například `Nullable(Of Integer)`). Další informace o typech s povolenou hodnotou Null, naleznete v tématu <xref:System.Nullable>. Kompletní kód deklarovat instanci objektu typu TableAdapter a spuštění dotazu by měl vypadat nějak takto (Tento příklad předpokládá, vrácená hodnota je celé číslo, upravte kód tak, vzhledem k datovému typu vrácenou vaším dotazem):  
  
     [!code-csharp[VbRaddataFillingAndExecuting#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#9)]
     [!code-vb[VbRaddataFillingAndExecuting#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#9)]  
  
## <a name="executing-sql-statements-that-return-single-values-using-a-command-object"></a>Provádění příkazů SQL, které vrátí jednu hodnotu pomocí příkazu objektu  
 Následující příklad ukazuje, jak vytvořit příkaz a provedení příkazu SQL, který vrací jedinou hodnotu. Informace o nastavení a získání hodnot parametrů pro příkaz, naleznete v tématu [postupy: nastavení a získání parametrů pro objekty příkazu](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 V tomto příkladu <xref:System.Data.SqlClient.SqlCommand> objektu a vyžaduje:  
  
-   Odkazy <xref:System>, <xref:System.Data>, a <xref:System.Xml> obory názvů.  
  
-   Datové připojení s názvem `SqlConnection1`.  
  
-   Tabulku s názvem `Customers` data source `SqlConnection1` připojí k. (V opačném případě budete potřebovat platný příkaz SQL pro zdroj dat).  
  
#### <a name="to-execute-an-sql-statement-returning-a-single-value-using-a-datacommand"></a>K provedení příkazu SQL vrácení jedné hodnoty použití očekává  
  
-   Přidejte následující kód k metodě, kterou chcete spustit kód z. Vrátí jednu hodnotu voláním `ExecuteScalar` metoda příkazu (například <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>). Vrácená data do <xref:System.Object>.  
  
     [!code-csharp[VbRaddataFillingAndExecuting#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#10)]
     [!code-vb[VbRaddataFillingAndExecuting#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#10)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Aplikace vyžaduje oprávnění k přístupu k databázi a spusťte příkaz jazyka SQL.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteScalar%2A?displayProperty=fullName>   
 [Postupy: vytváření dotazů TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Postupy: upravování dotazů TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Postupy: vyplnění datové sady s daty](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Vyplnění datové sady s použitím objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Postupy: nastavování a získávání parametrů pro objekty příkazu](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)