---
title: 'Postupy: provedení uložené procedury, které nevrací žádnou hodnotu | Dokumentace Microsoftu'
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
- ExecuteNonQuery method
- stored procedures, creating
- stored procedures, executing
ms.assetid: 8a929e96-2cf5-43a5-b5b7-c0a5a397bbc5
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 38dea599c0c3247c3dd2e3e1d1ca8bb02315cfc5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263091"
---
# <a name="how-to-execute-a-stored-procedure-that-returns-no-value"></a>Postupy: Provedení uložené procedury, jež nevrací žádnou hodnotu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K provedení uložené procedury, které nevrací žádnou hodnotu, můžete spustit dotaz TableAdapter, který je nakonfigurován ke spuštění uložené procedury (například `CustomersTableAdapter.UpdateTableData(CustomersDataTable)`).  
  
 Pokud vaše aplikace nepoužívá objekty TableAdapter, zavolejte `ExecuteNonQuery` metodu na objekt příkazu nastavení jeho `CommandType` vlastnost <xref:System.Data.CommandType>. ("Objekt příkazu" odkazuje na konkrétní příkaz pro [zprostředkovatele dat .NET Framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) vaše aplikace používá. For example, pokud vaše aplikace používá zprostředkovatele dat .NET Framework pro SQL Server, pak objekt příkazu bude <xref:System.Data.SqlClient.SqlCommand>.)  
  
 Následující příklady ukazují, jak spouštět uložené procedury, které vracejí žádná hodnota z databáze pomocí buď objekty TableAdapter nebo příkaz objekty. Další informace o dotazování s příkazy a objektů TableAdapters, naleznete v tématu [vyplnění datové sady s použitím objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="executing-stored-procedures-that-return-no-values-using-a-tableadapter"></a>Provedení uložené procedury, které nevrací žádnou hodnotu pomocí prvku TableAdapter  
 Tento příklad ukazuje, jak vytvořit dotaz TableAdapter pomocí [úpravy objektů TableAdapter](../data-tools/editing-tableadapters.md), a pak poskytuje informace o tom, jak deklarovat instanci typu TableAdapter a spusťte dotaz.  
  
#### <a name="to-create-a-stored-procedure-that-returns-no-value-using-a-tableadapter"></a>Vytvořit uloženou proceduru, která nevrací žádnou hodnotu pomocí prvku TableAdapter  
  
1.  Otevřete datovou sadu v **Návrhář Dataset**. Další informace najdete v tématu [postupy: otevření datové sady v návrháři datových sad](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Pokud již nemáte, vytvořte TableAdapter. Další informace o vytváření položek TableAdapters, naleznete v tématu [vytvoření a konfigurace objektů TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Pokud už máte dotaz na vaše TableAdapter, který používá uložené procedury, které nevrací žádnou hodnotu, přejděte k dalšímu postupu "postup deklarovat instanci typu TableAdapter a spusťte dotaz." V opačném případě pokračujte krokem 4 vytvořte nový dotaz, který nevrací žádnou hodnotu.  
  
4.  Klikněte pravým tlačítkem na TableAdapter, které chcete a použijte místní nabídku přidání dotazu.  
  
     **Průvodce nastavením dotazu TableAdapter** otevře.  
  
5.  Vyberte **použití existující uložené procedury**a potom klikněte na tlačítko **Další**.  
  
6.  Vyberte uloženou proceduru z rozevíracího seznamu a potom klikněte na tlačítko **Další**.  
  
7.  Vyberte možnost vrátit **žádná hodnota**a potom klikněte na tlačítko **Další**.  
  
8.  Zadejte název dotazu.  
  
9. Klikněte na tlačítko **Další**, nebo **Dokončit** dokončete průvodce; dotaz je přidán do objektu TableAdapter.  
  
10. Sestavte projekt.  
  
#### <a name="to-declare-an-instance-of-the-tableadapter-and-execute-the-query"></a>Deklarujte instanci typu TableAdapter a spusťte dotaz  
  
1.  Deklarujte instanci TableAdapter, který obsahuje dotaz, který chcete spustit.  
  
    -   Chcete-li vytvořit instanci pomocí návrhových nástrojů, přetáhněte TableAdapter, který chcete z **nástrojů**. (Komponent ve vašem projektu teď budou zobrazovat v **nástrojů** pod nadpisem, která odpovídá názvu vašeho projektu.) Pokud TableAdapter se nezobrazují v **nástrojů**, pak budete muset svůj projekt sestavit.  
  
         -nebo-  
  
    -   K vytvoření instance v kódu, nahraďte následujícím kódem názvy vašich <xref:System.Data.DataSet> a TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  Objekty TableAdapter nejsou ve skutečnosti umístěný uvnitř své třídy přidružený objekt dataset. Každá datová sada má odpovídající kolekci objektů TableAdapter ve vlastním oboru názvů. Například, pokud máte datovou sadu s názvem `SalesDataSet`, pak by byl `SalesDataSetTableAdapters` obor názvů, který obsahuje její objekty TableAdapter.  
  
2.  Volejte dotazu, jako by volání jakékoli jiné metody v kódu. Dotaz je metodu na objektu TableAdapter. Následující kód nahraďte názvy třídy TableAdapter a dotazu. Musíte taky předat parametry požadované vaším dotazem. Pokud si nejste jistí, jestli váš dotaz vyžaduje parametry, nebo jaké parametry se vyžaduje, zkontrolujte technologie IntelliSense pro požadovaný podpis dotazu. V závislosti na tom, jestli váš dotaz parametry nebo ne by vypadalo podobně jako na jednu z následujících příkladů kódu:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     Kompletní kód deklarovat instanci typu TableAdapter a spusťte dotaz by měl vypadat nějak takto:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#11)]
     [!code-vb[VbRaddataFillingAndExecuting#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#11)]  
  
## <a name="executing-stored-procedures-that-return-no-value-using-a-command-object"></a>Provedení uložené procedury, které vracejí žádná hodnota, pomocí příkazu objektu  
 Následující příklad ukazuje, jak vytvořit příkaz a provedení uložené procedury, které nevrací žádnou hodnotu. Informace o nastavení a získání hodnot parametrů pro příkaz, naleznete v tématu [postupy: nastavení a získání parametrů pro objekty příkazu](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 V tomto příkladu <xref:System.Data.SqlClient.SqlCommand> objektu a vyžaduje:  
  
-   Odkazy <xref:System>, <xref:System.Data>, a <xref:System.Xml> obory názvů.  
  
#### <a name="to-execute-a-stored-procedure-that-returns-no-value-using-a-datacommand"></a>K provedení uložené procedury, které nevrací žádnou hodnotu očekává pomocí  
  
-   Přidejte následující kód k metodě, kterou chcete spustit uloženou proceduru z. Volání `ExecuteNonQuery` metody příkazu vrátit žádnou hodnotu (například <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>).  
  
     [!code-csharp[VbRaddataFillingAndExecuting#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#15)]
     [!code-vb[VbRaddataFillingAndExecuting#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#15)]  
  
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