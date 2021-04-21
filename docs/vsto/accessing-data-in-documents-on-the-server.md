---
title: Přístup k datům v dokumentech na serveru
description: Přečtěte si, jak můžete programovat s daty v přizpůsobení na úrovni dokumentu bez nutnosti použití objektového modelu systém Microsoft Office Wordu nebo systém Microsoft Office Excelu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], accessing on server
- data access [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0df6aef3c83d66b84f569e85e953fde8a3f0e16c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826769"
---
# <a name="access-data-in-documents-on-the-server"></a>Přístup k datům v dokumentech na serveru
  Můžete programovat s daty v přizpůsobení na úrovni dokumentu bez nutnosti používat objektový model systém Microsoft Office Word nebo systém Microsoft Office Excel. To znamená, že budete mít přístup k datům, která jsou obsažena v dokumentu na serveru, na kterém není nainstalován Word nebo Excel. Například kód na serveru (například na [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] stránce) může přizpůsobit data v dokumentu a odeslat přizpůsobený dokument koncovému uživateli. Když koncový uživatel otevře dokument, kód vazby dat v sestavení řešení váže přizpůsobená data do dokumentu. To je možné, protože data v dokumentu jsou oddělená od uživatelského rozhraní. Další informace najdete v tématu [data uložená v mezipaměti v přizpůsobeních na úrovni dokumentu](../vsto/cached-data-in-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="cache-data-for-use-on-a-server"></a>Data mezipaměti pro použití na serveru
 Chcete-li uložit datový objekt do mezipaměti v dokumentu, označte jej <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributem v době návrhu nebo použijte `StartCaching` metodu položky hostitele v době běhu. Když ukládáte do mezipaměti datový objekt v dokumentu, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] objekt se zaserializace do řetězce XML, který je uložen v dokumentu. Objekty musí splňovat určité požadavky, aby měly nárok na ukládání do mezipaměti. Další informace najdete v tématu [cache data](../vsto/caching-data.md).

 Kód na straně serveru může manipulovat s datovými objekty v mezipaměti dat. Ovládací prvky, které jsou vázány na instance dat v mezipaměti, jsou synchronizovány s uživatelským rozhraním, aby všechny změny na straně serveru, které jsou provedeny v datech, byly automaticky zobrazeny, když je dokument otevřen v klientovi.

## <a name="access-data-in-the-cache"></a>Přístup k datům v mezipaměti
 K datům v mezipaměti můžete přistupovat z aplikací mimo kancelář, například z konzolové aplikace, model Windows Forms aplikace nebo webové stránky. Aplikace, která přistupuje k datům uloženým v mezipaměti, musí mít úplný vztah důvěryhodnosti; Webová aplikace, která má částečnou důvěryhodnost, nemůže vkládat, načítat ani měnit data uložená v dokumentu Office.

 Mezipaměť dat je přístupná prostřednictvím hierarchie kolekcí, které jsou zpřístupněny <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> vlastností <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídy:

- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>Vlastnost vrátí <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> , která obsahuje všechna data uložená v mezipaměti v přizpůsobení na úrovni dokumentu.

- Každý <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> obsahuje jeden nebo více <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> objektů. <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>Obsahuje všechny datové objekty uložené v mezipaměti, které jsou definovány v rámci jedné třídy.

- Každý <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> obsahuje jeden nebo více <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> objektů. <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>Představuje jeden datový objekt uložený v mezipaměti.

  Následující příklad kódu ukazuje, jak přistupovat k řetězci v mezipaměti ve `Sheet1` třídě projektu excelového sešitu. Tento příklad je součástí většího příkladu, který je k dispozici pro <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> metodu.

  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs" id="Snippet12":::
  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb" id="Snippet12":::

## <a name="modify-data-in-the-cache"></a>Úprava dat v mezipaměti
 Chcete-li upravit datový objekt uložený v mezipaměti, obvykle proveďte následující kroky:

1. Deserializace reprezentace XML objektu v mezipaměti do nové instance objektu. K XML můžete přistupovat pomocí <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> vlastnosti <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> , která představuje datový objekt uložený v mezipaměti.

2. Proveďte změny této kopie.

3. Pomocí jedné z následujících možností serializace změněného objektu zpět do mezipaměti dat:

    - Pokud chcete automaticky serializovat změny, použijte <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> metodu. Tato metoda používá formát formátu **DiffGram** k serializaci <xref:System.Data.DataSet> , <xref:System.Data.DataTable> a typových objektů DataSet v mezipaměti dat. Formát formátu **DiffGram** zajišťuje, aby se změny v mezipaměti dat v offline dokumentu odesílaly na server správně.

    - Chcete-li provést vlastní serializaci pro změny dat uložených v mezipaměti, můžete zapisovat přímo do <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> Vlastnosti. Určete formát formátu **DiffGram** , pokud použijete <xref:System.Data.Common.DataAdapter> k aktualizaci databáze se změnami provedenými v datech v datové <xref:System.Data.DataSet> <xref:System.Data.DataTable> sadě, nebo typu. V opačném případě <xref:System.Data.Common.DataAdapter> bude aktualizace databáze aktualizována přidáním nových řádků místo úprav stávajících řádků.

### <a name="modify-data-without-deserializing-the-current-value"></a>Úprava dat bez deserializace aktuální hodnoty
 V některých případech můžete chtít změnit hodnotu objektu uloženého v mezipaměti bez prvotního deserializace aktuální hodnoty. To lze provést například v případě, že měníte hodnotu objektu, který má jednoduchý typ, například řetězec nebo celé číslo, nebo Pokud inicializujete ukládání do mezipaměti <xref:System.Data.DataSet> v dokumentu na serveru. V těchto případech můžete použít <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> metodu bez prvotního deserializace aktuální hodnoty objektu uloženého v mezipaměti.

 Následující příklad kódu ukazuje, jak změnit hodnotu řetězce v mezipaměti ve `Sheet1` třídě projektu excelového sešitu. Tento příklad je součástí většího příkladu, který je k dispozici pro <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> metodu.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs" id="Snippet11":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb" id="Snippet11":::

### <a name="modify-null-values-in-the-data-cache"></a>Úprava hodnot null v mezipaměti dat
 Mezipaměť dat neukládá objekty, které mají hodnotu **null** při uložení a zavření dokumentu. Toto omezení má při úpravě dat uložených v mezipaměti několik důsledků:

- Pokud nastavíte libovolný objekt v mezipaměti dat na hodnotu **null**, všechny objekty v mezipaměti dat budou při otevření dokumentu automaticky nastaveny na **hodnotu null** a celá mezipaměť dat bude vymazána při uložení a zavření dokumentu. To znamená, že všechny objekty uložené v mezipaměti budou odebrány z mezipaměti dat a <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> kolekce bude prázdná.

- Pokud sestavíte řešení s objekty **null** v mezipaměti dat a chcete tyto objekty inicializovat pomocí <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídy před prvním otevřením dokumentu, je nutné zajistit, aby všechny objekty v mezipaměti dat byly inicializovány. Pokud inicializujete pouze některé objekty, všechny objekty budou při otevření dokumentu nastaveny na **hodnotu null** a celá mezipaměť dat bude vymazána při uložení a zavření dokumentu.

## <a name="access-typed-datasets-in-the-cache"></a>Přístup k typovým datovým sadám v mezipaměti
 Chcete-li získat přístup k datům ve typové datové sadě jak z řešení Office, tak z aplikace mimo kancelář, například model Windows Forms aplikace nebo [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] projektu, je nutné definovat typovou datovou sadu v samostatném sestavení, které je odkazováno v obou projektech. Pokud přidáte typovou datovou sadu do každého projektu pomocí průvodce **konfigurací zdroje dat** nebo **Návrhář datových sad**, bude .NET Framework zacházet s typovými datovými sadami v těchto dvou projektech jako různé typy. Další informace o vytváření typových datových sad naleznete v tématu [Create and Configure datasetss in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Viz také

- [Přístup k datům v dokumentech na serveru](../vsto/accessing-data-in-documents-on-the-server.md)
- [Data uložená v mezipaměti v přizpůsobeních na úrovni dokumentu](../vsto/cached-data-in-document-level-customizations.md)