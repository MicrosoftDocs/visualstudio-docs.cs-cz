---
title: TableAdapter – přehled | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DataAccessor
- vbdata.Microsoft.VSDesigner.DataSource.DataAccessor
- TableAdapter
- vs.data.TableAdapter
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], table adapters
- TableAdapters, queries
- data [Visual Studio], TableAdapters
- query data in Visual Studio
- TableAdapter.GetData
- TableAdapter.Fill
- data [Visual Studio], datasets
- TableAdapters
- table adapters
ms.assetid: a87c46a0-52ab-432a-a864-9ba55069f9eb
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: fb5ebcdaa1bebe67c2fb8e378c7345467dd10b78
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269045"
---
# <a name="tableadapter-overview"></a>TableAdapter – přehled
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Objekty TableAdapter jsou návrhářem vygenerované komponenty, které připojení k databázi, spustit dotazy nebo uložené procedury a zadat jejich objekt DataTable s vrácenými daty. Objekty TableAdapter se také používají k odesílání dat z aplikace zpět do databáze. Můžete mít tolik dotazů, kolik chcete na objektu typu TableAdapter tak dlouho, dokud vrátí data, která odpovídají schématu tabulky, se kterým je spojen TableAdapter. Následující diagram znázorňuje, jak objekty TableAdapter komunikovat s databází a jiných objektů v paměti:  
  
 ![Tok dat v klientských aplikacích](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 Zatímco objekty TableAdapter jsou navrženy s **Návrhář Dataset**, generované třídy TableAdapter nejsou generovány jako vnořené třídy typu <xref:System.Data.DataSet>. Jsou umístěny v samostatných oborech názvů specifických pro jednotlivé datové sady. Pokud máte například datovou sadu s názvem `NorthwindDataSet`, typy TableAdapter přidružené typům <xref:System.Data.DataTable> v datové sadě `NorthwindDataSet` by měly být v oboru názvů `NorthwindDataSetTableAdapters`. Pro programový přístup k určitému typu TableAdapter musíte deklarovat novou instanci typu TableAdapter. Příklad:  
  
 [!code-csharp[VbRaddataTableAdapters#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs#7)]
 [!code-vb[VbRaddataTableAdapters#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb#7)]  
  
## <a name="associated-datatable-schema"></a>Přidružené schéma objektu DataTable  
 Při vytváření objektu TableAdapter se počáteční dotaz nebo uložená procedura použije pro definování schématu objektu <xref:System.Data.DataTable> přidruženého k tomuto objektu TableAdapter. Tento počáteční dotaz nebo uloženou proceduru provedete voláním objektu TableAdapter `Fill` – metoda (která naplní TableAdapter přidružené k <xref:System.Data.DataTable>). Jakékoli změny provedené v hlavním dotazu objektu TableAdapter se projeví ve schématu přidružené tabulky dat. Například odebráním sloupce z hlavního dotazu odeberete sloupec z přidružené tabulky dat. Pokud jakékoliv další dotazy provedené na objektu TableAdapter používají příkazy jazyka SQL vracející sloupce, které nejsou v hlavním dotazu, pokusí se návrhář synchronizovat změny ve sloupcích mezi hlavním dotazem a jakýmikoliv dalšími dotazy. Další informace najdete v tématu [jak: Edit TableAdapters](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).  
  
## <a name="tableadapter-update-commands"></a>Příkazy aktualizace objektu TableAdapter  
 Funkce aktualizace objektu TableAdapter je závislá na množství informací, které jsou k dispozici na základě hlavního dotazu zadaného v průvodci vytvořením objektu TableAdapter. Například objekty TableAdapter, které jsou nakonfigurovány k načtení hodnot z více tabulek (spojení JOIN), skalárních hodnot, zobrazení nebo výsledků agregačních funkcí, nejsou původně vytvořeny s možností odesílat aktualizace zpět do databáze. Ale můžete nakonfigurovat ručně v příkazy INSERT, UPDATE a DELETE **vlastnosti** okna.  
  
## <a name="tableadapter-queries"></a>Dotazy objektu TableAdapter  
 ![TableAdapter s více dotazy](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 Objekty TableAdapter mohou obsahovat několik dotazů k vyplnění přidružených datových tabulek. Objektu TableAdapter lze definovat tolik dotazů, kolik vyžaduje vaše aplikace, pokud každý dotaz vrací data, která odpovídají stejnému schématu jako jeho přidružená tabulka dat. To umožňuje načítání dat, která splňují odlišná kritéria. Pokud vaše aplikace například obsahuje tabulku zákazníků, lze vytvořit dotaz, který tuto tabulku vyplní všemi zákazníky, jejichž jména začínají určitým písmenem, a další dotaz, který tuto tabulku vyplní všemi zákazníky, kteří se nacházejí ve stejném státě. Chcete-li tabulku `Customers` vyplnit zákazníky v daném státě, můžete vytvořit dotaz `FillByState`, který přijímá parametr pro hodnotu státu: `SELECT * FROM Customers WHERE State = @State`. Dotaz spustíte voláním metody `FillByState` a předáním hodnoty parametru, například `CustomerTableAdapter.FillByState("WA")`. Další informace najdete v tématu [postupy: vytváření dotazů TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
 Kromě dotazů, které vracejí data stejného schématu jako tabulka dat objektu TableAdapter, lze přidat dotazy, které vracejí skalární hodnoty. Například vytvoření dotazu, který vrací počet zákazníků (`SELECT Count(*) From Customers`) je pro objekt `CustomersTableAdapter` platný, ačkoliv vrácená data neodpovídají schématu příslušné tabulky.  
  
## <a name="clearbeforefill-property"></a>Vlastnost ClearBeforeFill  
 Ve výchozím nastavení jsou při každém spuštění dotazu k vyplnění tabulky dat objektu TableAdapter příslušná data odstraněna a jsou načteny pouze výsledky dotazu. Pokud budete chtít přidat nebo sloučit data vrácená dotazem se stávajícími daty v tabulce dat, nastavte vlastnost `ClearBeforeFill` objektu TableAdapter na hodnotu `false`. Bez ohledu na to, zda tato data odstraníte, je v případě potřeby nutné explicitní odeslání aktualizací zpět do databáze. Proto nezapomeňte před provedením dalšího dotazu, který tuto tabulku vyplní, uložit všechny změny provedené v datech tabulky. Další informace najdete v tématu [aktualizace dat pomocí TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).  
  
## <a name="tableadapter-inheritance"></a>Dědičnost třídy TableAdapter  
 Objekty TableAdapter rozšiřují funkce standardních datových adaptérů zapouzdřením nakonfigurovaného objektu <xref:System.Data.Common.DataAdapter>. Třída TableAdapter standardně dědí z třídy <xref:System.ComponentModel.Component> a nelze ji převést na třídu <xref:System.Data.Common.DataAdapter>. Převedení objektu typu TableAdapter na typ <xref:System.Data.Common.DataAdapter> má za následek výjimku <xref:System.InvalidCastException>. Chcete-li změnit základní třídu třídy TableAdapter, lze zadat třídu, která je odvozena z <xref:System.ComponentModel.Component> v **základní třídy** vlastnost objektu TableAdapter v **Návrhář Dataset**.  
  
## <a name="tableadapter-methods-and-properties"></a>Vlastnosti a metody třídy TableAdapter  
 Třída TableAdapter není součástí [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], a proto je nelze vyhledat v dokumentaci nebo **prohlížeče objektů**. Je vytvořena v době návrhu, pokud použijete jeden z výše uvedených průvodců. Název přiřazený objektu typu TableAdapter při jeho vytvoření vychází z názvu tabulky, se kterou právě pracujete. Například při vytvoření objektu typu TableAdapter založeném na tabulce v databázi s názvem `Orders` bude tento objekt typu TableAdapter pojmenován jako `OrdersTableAdapter`. Název třídy TableAdapter lze změnit pomocí **název** vlastnost **Návrhář Dataset**.  
  
 Zde jsou uvedeny běžně používané metody a vlastnosti třídy TableAdapter:  
  
|Člen|Popis|  
|------------|-----------------|  
|`TableAdapter.Fill`|Vyplní datovou tabulku přidruženou objektu TableAdapter výsledky příkazu SELECT objektu TableAdapter. Další informace najdete v tématu [postupy: vyplnění datové sady s daty](../data-tools/how-to-fill-a-dataset-with-data.md).|  
|`TableAdapter.Update`|Odešle změny zpět do databáze a vrátí celé číslo představující počet řádků, které byly touto aktualizací ovlivněny. Další informace najdete v tématu [aktualizace dat pomocí TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|  
|`TableAdapter.GetData`|Vrátí nový objekt <xref:System.Data.DataTable> naplněný daty.|  
|`TableAdapter.Insert`|Vytvoří v tabulce dat nový řádek. Další informace najdete v tématu [postupy: Přidání řádků do DataTable určitého](http://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).|  
|`TableAdapter.ClearBeforeFill`|Určuje, zda bude tabulka dat před voláním metody `Fill` vyprázdněna.|  
  
## <a name="tableadapter-update-method"></a>Metoda aktualizace třídy TableAdapter  
 Objekty TableAdapter používají příkazy pro čtení a zápis dat z databáze. Počáteční (hlavní) dotaz metody `Fill` objektu TableAdapter slouží jako základ pro vytvoření schématu přidružené tabulky dat, stejně jako příkazy `InsertCommand`, `UpdateCommand` a `DeleteCommand` přidružené metodě `TableAdapter.Update`. To znamená, že volání objektu TableAdapter `Update` metoda provede příkazy vytvořené při byl TableAdapter původně nakonfigurován a některý další dotazy přidané pomocí **Průvodce nastavením dotazu TableAdapter**.  
  
 Objekt TableAdapter efektivně provede stejné operace s příkazy, které byste obvykle provedli. Například při volání metody `Fill` adaptér spustí datový příkaz v rámci své vlastnosti `SelectCommand` a k načtení sady výsledků do tabulky dat použije čtečku dat (například typ <xref:System.Data.SqlClient.SqlDataReader>). Obdobně platí, že pokud voláte metodu `Update` adaptéru, je spuštěn příslušný příkaz (ve vlastnosti `UpdateCommand`, `InsertCommand` nebo `DeleteCommand`) pro jednotlivé změněné záznamy v tabulce dat.  
  
> [!NOTE]
>  Pokud v hlavním dotazu není k dispozici dostatek informací, příkazy `InsertCommand`, `UpdateCommand` a `DeleteCommand` jsou vytvořeny jako výchozí při generování objektu TableAdapter. Pokud hlavním dotazem objektu TableAdapter je více než jen příkaz SELECT z jedné tabulky, je možné, že návrhář nebude schopen příkazy `InsertCommand`, `UpdateCommand` a `DeleteCommand` vygenerovat. Pokud tyto příkazy nejsou vygenerovány, může se při provádění metody `TableAdapter.Update` zobrazit chyba.  
  
## <a name="tableadapter-generatedbdirectmethods"></a>Vlastnost GenerateDBDirectMethods třídy TableAdapter  
 Kromě příkazů `InsertCommand`, `UpdateCommand` a `DeleteCommand` jsou objekty TableAdapter vytvořeny metodami, které mohou být provedeny přímo v databázi. Tyto metody (`TableAdapter.Insert`, `TableAdapter.Update` a `TableAdapter.Delete`) lze volat přímo pro manipulaci s daty v databázi. To znamená, že za účelem provedení operací vložení, aktualizace a odstranění, které čekají na přidruženou tabulku dat, lze tyto metody volat z vašeho kódu namísto volání metody Update objektu TableAdapter.  
  
 Pokud chcete tyto přímé metody vytvořit nechcete, nastavte TableAdapter **GenerateDbDirectMethods** vlastnost `false` (v **vlastnosti** okno). Další dotazy přidané do objektu TableAdapter jsou samostatné dotazy a tyto metody nejsou generovány.  
  
## <a name="tableadapter-support-for-nullable-types"></a>Třída TableAdapter podporuje typy s povolenou hodnotou null  
 Třída TableAdapter podporuje typy s povolenou hodnotou null `Nullable(Of T)` a `T?`. Další informace o typech s povolenou hodnotou Null v jazyce Visual Basic, naleznete v tématu [hodnotové typy s možnou hodnotou Null](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6). Další informace o typech s povolenou hodnotou Null v jazyce C# najdete v tématu [typy připouštějící hodnotu Null pomocí](http://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28).  
  
## <a name="see-also"></a>Viz také  
 [Návody k datům](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Postupy: připojení k datům v databázi](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Návod: Připojování k datům v databázi (Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)   
 [Příprava aplikace pro příjem dat](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Načítají se Data do vaší aplikace](../data-tools/fetching-data-into-your-application.md)   
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Úpravy dat v aplikaci](../data-tools/editing-data-in-your-application.md)   
 [Ověřování dat](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Ukládání dat](../data-tools/saving-data.md)