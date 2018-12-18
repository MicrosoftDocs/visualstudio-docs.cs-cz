---
title: Připojování k datům ve Windows Forms aplikací | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- System.Data.SqlClient.SqlConnection
- System.Data.Odbc.OdbcConnection
- System.Data.OleDb.OleDbConnection
- System.Data.OracleClient.OracleConnection
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- connection objects, tools for working with
- OleDbConnection class, ADO.NET connection objects
- databases [Visual Studio], connecting to
- data adapters, connections
- connection pooling, ADO.NET connections
- connection strings [Visual Studio], ADO.NET
- connection objects, types of
- dynamic properties, ADO.NET connections
- connections, about connections
- data [Visual Studio], connecting
- design-time connections
- connections, design-time
- TableAdapters, connections
- connection objects
- SqlConnection class, ADO.NET connection objects
- connecting to databases, ADO.NET connections
- transactions, ADO.NET
- database connections [Visual Studio], ADO.NET
ms.assetid: 184cbd0d-3b26-418d-a11c-f9f8f004fbff
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: d8da35b32f3dd25bd7ed47b25f722c6b0aa21ac7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49208946"
---
# <a name="connecting-to-data-in-windows-forms-applications"></a>Připojení k datům ve formulářových aplikacích Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] poskytuje nástroje pro připojení aplikace k datům z mnoha různých zdrojů, jako je například databází, webových služeb a objektů. Pokud používáte nástroje pro návrh dat v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], často není potřeba explicitně vytvořit objekt připojení pro vaše formuláře nebo komponenta. Objekt připojení je většinou vytvořené v důsledku dokončení jednoho z průvodců dat nebo přetažení datové objekty do formuláře. Připojení aplikace k datům v databázi, webové služby nebo objekt, spusťte [Průvodce konfigurací zdroje dat](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) tak, že vyberete **přidat nový zdroj dat** z [okna zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
 Následující diagram znázorňuje standardní tok operací při připojování k datům pomocí provádí dotaz TableAdapter načítají data a zobrazit je na formulář v nástrojích pro aplikace Windows.  
  
 ![Tok dat v klientských aplikacích](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 V některých případech je vhodné vytvořit objekt připojení bez pomoci všechny datové nástroje návrhu. Informace o vytvoření připojení prostřednictvím kódu programu najdete v tématu [připojení ke zdroji dat](http://msdn.microsoft.com/library/9abc3f92-1be3-4e1a-b360-762dc689650e).  
  
> [!NOTE]
>  Informace o připojení webové aplikace k datům najdete v tématu [mapa obsahu přístupu k Data technologie ASP.NET](http://msdn.microsoft.com/en-us/f9219396-a0fa-481f-894d-e3d9c67d64f2).  
  
## <a name="walkthroughs-for-connecting-windows-forms-applications-to-data"></a>Návody pro připojení Windows Forms aplikace k datům  
 Následující návody obsahují postupy související s připojením k datům v aplikacích Windows Forms:  
  
-   [Návod: Připojování k datům v databázi (Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)  
  
-   [Návod: Připojování k datům v lokálního databázového souboru (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)  
  
-   [Návod: Připojování k datům ve webové službě (Windows Forms)](http://msdn.microsoft.com/library/079fb9b0-c733-40c1-acd1-d0d68834354d)  
  
-   [Návod: Připojování k datům v objektech (Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)  
  
-   [Připojení k datům v databázi Accessu (model Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)  
  
## <a name="creating-connections"></a>Vytvoření připojení  
 V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], připojení se konfiguruje pomocí **přidat/změnit připojení** dialogové okno. **Přidat připojení** dialogové okno se zobrazí, když jste úpravy nebo vytvoření připojení v rámci některého z průvodců dat nebo [Průzkumník serveru/Průzkumník databáze](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) nebo když upravujete vlastnosti připojení v **vlastnosti** okna.  
  
 Datová připojení se automaticky konfigurují při provádění jednoho z následujících akcí.  
  
|Akce|Popis|  
|------------|-----------------|  
|Spustit [Průvodce konfigurací zdroje dat](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).|Při výběru použijte cestu k databázi v nakonfigurovaná připojení **Průvodce konfigurací zdroje dat**. Další informace najdete v tématu [postupy: připojení k datům v databázi](../data-tools/how-to-connect-to-data-in-a-database.md).|  
|Spustit [Průvodce nastavením TableAdapter](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8).|Připojení se vytváří v rámci **Průvodce nastavením TableAdapter**. Další informace najdete v tématu [vytvoření a konfigurace objektů TableAdapter](../data-tools/create-and-configure-tableadapters.md).|  
|Spustit [TableAdapters – úpravy](../data-tools/editing-tableadapters.md).|Připojení se vytváří v rámci **Průvodce nastavením dotazu TableAdapter**. Další informace najdete v tématu [postupy: vytváření dotazů TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).|  
|Přetáhněte položky z [okna zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) do formuláře nebo [návrháře komponent](http://msdn.microsoft.com/library/61a3a450-5b15-465e-bd9a-72a6c8c2b282).|Objekty připojení se vytvoří při přetažení položky z **zdroje dat** okna do **Návrháře formulářů Windows** nebo **návrháře komponent**. Další informace najdete v tématu [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).|  
|Přidat nové připojení dat k [Průzkumník serveru/Průzkumník databáze](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d).|Datové připojení v **Průzkumník serveru/Průzkumník databáze** se zobrazí v seznamu dostupných připojení v Průvodci dat|  
  
## <a name="connection-strings"></a>Připojovací řetězce  
 Připojovací řetězce mohou být uloženy v rámci kompilované aplikace nebo v konfiguračním souboru aplikace. Další informace najdete v tématu [postupy: uložení a úpravy připojovacích řetězců](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
## <a name="connection-information-and-security"></a>Informace o připojení a zabezpečení  
 Protože otevírání připojení zahrnuje přístup k prostředku služby důležité – databáze, jsou tady často problémy se zabezpečením účastnící se konfigurace a práce s připojením.  
  
 Jak zabezpečit aplikace a jeho přístup ke zdroji dat závisí na architektuře systému. Ve webové aplikaci například uživatelé informace obvykle získáte anonymní přístup k Internetové informační služby (IIS) a proto se neposkytuje zabezpečovacích přihlašovacích údajů. V takovém případě vaše aplikace udržuje svůj vlastní přihlašovací informace a použije ji, nikoli žádné informace o konkrétního uživatele, otevřete připojení a přístup k databázi.  
  
> [!IMPORTANT]
>  Uložení podrobností připojovacího řetězce, jako je heslo může ovlivnit zabezpečení aplikace. Použití integrované zabezpečení Windows je bezpečnější způsob řízení přístupu k databázi. Další informace najdete v tématu [chrání informace o připojení](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
 V intranetu nebo vícevrstvé aplikace můžete využít možnosti integrované zabezpečení poskytované Windows, služby IIS a SQL Server. V takovém modelu ověřování přihlašovacích údajů uživatele pro místní síť se taky používají k přístupu k prostředkům databáze a žádné explicitní uživatelské jméno nebo heslo se používá v připojovacím řetězci. Obvykle oprávnění jsou vytvořeny na počítači serveru databáze pomocí skupin, takže není potřeba navázat jednotlivá oprávnění pro každého uživatele, kteří mohou přistupovat k databázi. V tomto modelu není potřeba vůbec ukládání přihlašovacích údajů k připojení a neexistují žádné další kroky potřebné k ochraně informací o připojovacím řetězci.  
  
 Další informace o zabezpečení naleznete v následujících tématech:  
  
-   [Zabezpečení aplikací ADO.NET](http://msdn.microsoft.com/library/005a1d43-6ee5-471e-ad98-1d30a44d49d5)  
  
-   [Zabezpečenější přístup k souborům a datům ve Windows Forms](http://msdn.microsoft.com/library/3cd3e55b-2f5e-40dd-835d-f50f7ce08967)  
  
## <a name="design-time-connections-in-server-explorerdatabase-explorer"></a>Připojení v době návrhu v Průzkumník serveru/Průzkumník databáze  
 **Průzkumník serveru/Průzkumník databáze** poskytuje způsob, jak vytvořit připojení ke zdrojům dat v době návrhu. To vám umožňuje procházet dostupné zdroje dat; zobrazení informací o tabulky, sloupce a další prvky, které obsahují; Upravit a vytvořit prvky databáze.  
  
 Vaše aplikace nepoužívá přímo připojení k dispozici v **Průzkumník serveru/Průzkumník databáze**. Tato připojení používají [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pro práci s databází v době návrhu. Další informace najdete v tématu [nástroje Visual Database Tools](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 Například v době návrhu může použít **Průzkumník serveru/Průzkumník databáze** vytvořit připojení k databázi. Později, při návrhu formuláře, můžete procházet databázi, vyberte sloupce z tabulky a přetáhněte je do [Návrhář Dataset](../data-tools/creating-and-editing-typed-datasets.md). Tím se vytvoří [TableAdapter](../data-tools/tableadapter-overview.md) ve vaší datové sadě. Také vytvoří nový objekt připojení, která je součástí nově vytvořené třídy TableAdapter.  
  
 Informace o připojení v době návrhu jsou uloženy v místním počítači nezávisle na určitém projektu nebo řešení. Proto, když jste vytvořili připojení k návrhu při práci v aplikaci, zobrazí se v **Průzkumník serveru/Průzkumník databáze** vždy, když pracujete v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], tak dlouho, dokud serveru, ke kterému připojení body je k dispozici. Další informace najdete v tématu [postupy: připojení k databázi z Průzkumníka serveru](http://msdn.microsoft.com/en-us/7c1c3067-0d77-471b-872b-639f9f50db74).  
  
 [!INCLUDE[SQLObjectExplorer](../includes/sqlobjectexplorer-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Připojování k datům v sadě Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Postupy: připojení k datům v databázi](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Návod: Připojování k datům v databázi (Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)   
 [Mapa obsahu přístupu k datům v technologii ASP.NET](http://msdn.microsoft.com/en-us/f9219396-a0fa-481f-894d-e3d9c67d64f2)   
 [Příprava aplikace pro příjem dat](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Načítají se Data do vaší aplikace](../data-tools/fetching-data-into-your-application.md)   
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Úpravy dat v aplikaci](../data-tools/editing-data-in-your-application.md)   
 [Ověřování dat](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Ukládání dat](../data-tools/saving-data.md)