---
title: Přístup k datům v dokumentech na serveru
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], accessing on server
- data access [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 70c00a9c0de4afd9f54062e1c2ffabcc2911a538
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305569"
---
# <a name="access-data-in-documents-on-the-server"></a>Přístup k datům v dokumentech na serveru
  Bez nutnosti použít objektový model Microsoft Office Word nebo Microsoft Office Excel můžete programovat proti data v přizpůsobení na úrovni dokumentu. To znamená, že přistupujete k datům, která je součástí dokumentu na serveru, který nemá Word nainstalována aplikace Excel. Například kód na serveru (například v [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] stránky) můžete přizpůsobit data v dokumentu a odeslání přizpůsobeného dokumentu pro koncového uživatele. Když koncový uživatel otevře dokument, sváže data vazební kód v sestavení řešení upravená data do dokumentu. To je možné, protože data v dokumentu je oddělená od uživatelského rozhraní. Další informace najdete v tématu [data v přizpůsobeních na úrovni dokumentu v mezipaměti](../vsto/cached-data-in-document-level-customizations.md).  

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  

## <a name="cache-data-for-use-on-a-server"></a>Data v mezipaměti pro použití na serveru  
 Pro ukládání do mezipaměti objekt dat v dokumentu, označte ji pomocí <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atribut v době návrhu, nebo použít `StartCaching` metoda hostitele položky v době běhu. Když mezipaměti objekt dat v dokumentu, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serializuje objekt do řetězce, která je uložena v dokumentu XML. Objekty, musí splňovat určité požadavky způsobilé k ukládání do mezipaměti. Další informace najdete v tématu [ukládat data do mezipaměti](../vsto/caching-data.md).  

 Kód na straně serveru s všechny objekty data v datové mezipaměti. Ovládací prvky, které jsou vázány na data uložená v mezipaměti instancí synchronizaci s uživatelským rozhraním, aby všechny změny na straně serveru, které jsou provedené v datech se nezobrazí automaticky při otevření dokumentu na straně klienta.  

## <a name="access-data-in-the-cache"></a>Přístup k datům v mezipaměti  
 Data v mezipaměti můžete přistupovat z aplikace mimo Office, třeba z konzolové aplikace, aplikace modelu Windows Forms nebo na webové stránce. Aplikace, která přistupuje data uložená v mezipaměti musí mít plnou důvěryhodnost; Webové aplikace s částečným vztahem důvěryhodnosti nelze vložit, načtení nebo změnit data, která se uloží do mezipaměti v dokumentu systému Office.  

 Mezipaměť dat je přístupný prostřednictvím hierarchie kolekcí, které jsou vystavené <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> vlastnost <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídy:  

- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> Vrátí vlastnost <xref:Microsoft.VisualStudio.Tools.Applications.CachedData>, která obsahuje všechna data uložená v mezipaměti v přizpůsobení na úrovni dokumentu.  

- Každý <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> obsahuje jeden nebo více <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> objekty. A <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> obsahuje všechna data uložená v mezipaměti objektů, které jsou definovány v rámci jedné třídy.  

- Každý <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> obsahuje jeden nebo více <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> objekty. A <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> představuje objekt jednoho data uložená v mezipaměti.  

  Následující příklad kódu ukazuje, jak získat přístup k řetězec uložený v mezipaměti v `Sheet1` třídy projektu sešitu aplikace Excel. V tomto příkladu je součástí většího příkladu, která je k dispozici pro <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> metody.  

  [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
  [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]  

## <a name="modify-data-in-the-cache"></a>Změna dat v mezipaměti  
 Pokud chcete upravit objekt data uložená v mezipaměti, obvykle provádí následující kroky:  

1.  Deserializuje reprezentaci XML pro objekt uložený v mezipaměti do nové instance objektu. Můžete přístup k souboru XML s použitím <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> vlastnost <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> , který představuje objekt data uložená v mezipaměti.  

2.  Změny této kopii.  

3.  Změněný objekt zpět do datové mezipaměti Serializujte pomocí jedné z následujících možností:  

    -   Pokud chcete automaticky serializovat změny, použijte <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> metody. Tato metoda používá **formát DiffGram** formát pro serializaci <xref:System.Data.DataSet>, <xref:System.Data.DataTable>a typované datové sady objektů v datové mezipaměti. **Formát DiffGram** formát zajišťuje, že změny v datové mezipaměti v režimu offline dokumentu jsou správně odeslány na server.  

    -   Pokud chcete provést vlastní serializace pro změny dat uložených v mezipaměti, můžete psát přímo <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> vlastnost. Zadejte **formát DiffGram** formátování, když použijete <xref:System.Data.Common.DataAdapter> aktualizace databáze se změny provedené v datech <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, nebo zadaná datová sada. V opačném případě <xref:System.Data.Common.DataAdapter> aktualizuje databázi tak, že přidáte nové řádky namísto upravit existující řádků.  

### <a name="modify-data-without-deserializing-the-current-value"></a>Úprava dat bez deserializaci aktuální hodnotu  
 V některých případech můžete chtít změnit hodnotu objektu v mezipaměti bez první deserializaci aktuální hodnotu. Například to můžete provést Pokud chcete změnit hodnotu objektu, který má jednoduchý typ, jako je například řetězec nebo celé číslo, nebo pokud se inicializace uložená v mezipaměti <xref:System.Data.DataSet> v dokumentu na serveru. V těchto případech můžete použít <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> metody bez první deserializaci aktuální hodnota objekt uložený v mezipaměti.  

 Následující příklad kódu ukazuje, jak změnit hodnotu řetězec uložený v mezipaměti v `Sheet1` třídy projektu sešitu aplikace Excel. V tomto příkladu je součástí většího příkladu, která je k dispozici pro <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> metody.  

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]  

### <a name="modify-null-values-in-the-data-cache"></a>Upravit hodnoty null v mezipaměti dat  
 Datové mezipaměti neukládá objekty, které mají hodnotu **null** když je dokument uložit a zavřít. Toto omezení má několik důsledků při změně dat uložených v mezipaměti:  

-   Pokud jste nastavili libovolný objekt v mezipaměti dat na hodnotu **null**, všechny objekty v datové mezipaměti bude automaticky nastavena na **null** při otevření dokumentu, a celé datové mezipaměti bude vymazáno při dokument je uložit a zavřít. To znamená, všech objektů uložených v mezipaměti se odeberou z mezipaměti dat a <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> kolekce bude prázdná.  

-   Při sestavování řešení s **null** objekty v mezipaměti dat a chcete inicializovat tyto objekty pomocí <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třída před dokument se otevře poprvé, ujistěte se, že všechny objekty inicializovat v datové mezipaměti. Pokud je inicializovat pouze některé objekty, všech objektů bude nastavena na **null** při otevření dokumentu, a celé datové mezipaměti bude vymazáno, když je dokument uložit a zavřít.  

## <a name="access-typed-datasets-in-the-cache"></a>Přístup k zadané datové sady v mezipaměti  
 Pokud chcete získat přístup k datům v typové datové sady z řešení pro Office a aplikace svojí kanceláři, jako jsou aplikace modelu Windows Forms nebo [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] projektu, je nutné definovat typové datové sady v samostatné sestavení, na který odkazuje v obou projekty. Pokud přidáte typové datové sady do každého projektu pomocí **konfigurace zdroje dat** průvodce nebo **Návrhář Dataset**, rozhraní .NET Framework bude zacházet s typové datové sady v dva projekty jako různé typy . Další informace o vytvoření typové datové sady, naleznete v tématu [vytvoření a konfigurace datové sady v sadě Visual Studio](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).  

## <a name="see-also"></a>Viz také:  
 [Přístup k datům v dokumentech na serveru](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Data uložená v mezipaměti v přizpůsobeních na úrovni dokumentu](../vsto/cached-data-in-document-level-customizations.md)  
