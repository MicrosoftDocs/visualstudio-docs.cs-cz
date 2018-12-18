---
title: Data uložená v mezipaměti v přizpůsobeních na úrovni dokumentu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data islands [Office development in Visual Studio]
- view [Office development in Visual Studio]
- caching data [Office development in Visual Studio], about caching data
- data caching [Office development in Visual Studio], about data caching
- data [Office development in Visual Studio], cache
- data [Office development in Visual Studio], document-level solutions
- document-level customizations [Office development in Visual Studio], data model
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: c17c24dda11ea210c190a31197b783036357f2de
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248293"
---
# <a name="cached-data-in-document-level-customizations"></a>Data uložená v mezipaměti v přizpůsobeních na úrovni dokumentu
  Primární cílem přizpůsobení na úrovni dokumentu je oddělení dat ze zobrazení v dokumentech systému Office. Data představují informace, které jsou uloženy v dokumentu, včetně čísel a text. Zobrazení odkazuje na uživatelské rozhraní a objektový model Microsoft Office Word a Microsoft Office Excel.  
  
 Visual Studio tím, že data mají být vloženy jako data odděluje ze zobrazení v přizpůsobeních na úrovni dokumentu *datový ostrůvek*, označované také jako *přístupů do datové mezipaměti*. Může číst nebo upravovat data přímo, bez spuštění aplikace Word nebo Excel. To je užitečné, když budete chtít upravovat data v dokumentech na serveru, který nemá nainstalovanou sadu Microsoft Office. Aplikace Word a Excel jsou určeny k použití v prostředí klienta; nejsou určeny k použití na serveru.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Další informace o přizpůsobení na úrovni dokumentu naleznete v tématu [přehled vývoje řešení pro Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) a [architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="understand-the-cached-data-programming-model"></a>Vysvětlení programovací model dat uložených v mezipaměti  
 Data ostrov může obsahovat libovolný objekt v rámci vašeho řešení, která splňuje určité požadavky. Mezi tyto objekty patří <xref:System.Data.DataSet> objekty, <xref:System.Data.DataTable> objekty a jakýkoli jiný objekt, který lze serializovat pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy. Další informace najdete v tématu [ukládat data do mezipaměti](../vsto/caching-data.md).  
  
 Zajištění zobrazení pro data uložená v mezipaměti, můžete svázat ovládací prvky Windows Forms a *hostování ovládacích prvků* pro dokument k objektům v ostrov data. Vytváření datových vazeb mezi ovládacími prvky vázané na data a datový ostrůvek zajišťuje dvě synchronizované. Můžete také přidat kód pro ověření dat, která je nezávislá ovládací prvky. Další informace najdete v tématu [vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Hostitelské ovládací prvky jsou rozšířeny verze nativních objektů v objektové modely Excelu a Wordu. Na rozdíl od nativních objektů hostitelské ovládací prvky lze vázat přímo spravovaných datových objektů. Další informace najdete v tématu [hostovat položky a hostujte Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md) a [ovládací prvky Windows Forms v přehledu dokumenty Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## <a name="access-cached-data-on-the-server"></a>Přístup do mezipaměti dat na serveru  
 Chcete-li získat přístup k data uložená v mezipaměti v dokumentu, můžete použít <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídy. Tato třída je součástí [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], a je možné na server bez spuštěné aplikace Excel nebo Word. Když uživatel otevře dokument po upravovat data uložená v mezipaměti, všechny ovládací prvky, které jsou vázány na data se automaticky synchronizují na změny a uživateli se zobrazí aktualizovaná data. Další informace najdete v tématu [přístup k datům v dokumentech na serveru](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Excelu a Wordu nejsou potřeba k zápisu dat na serveru pouze k zobrazení na straně klienta. Excelu a Wordu ještě nemusí být nainstalován na serveru. To poskytuje lepší škálovatelnost a schopnost provádět rychlé dávkové zpracování dokumentů, které obsahují datové ostrůvky.  
  
## <a name="data-caching-for-offline-use"></a>Ukládání dat do mezipaměti pro použití v offline režimu  
 Ukládání dat v data ostrov umožňuje scénáře v režimu offline. Když uživatel poprvé otevře dokument nebo vyžádá dokument ze serveru, je datový ostrůvek vyplněna nejnovější data. Ostrov data se uloží do mezipaměti v dokumentu a je pak k dispozici v režimu offline. Uživatel (a váš kód) můžete pracuje s daty, i když není k dispozici žádné živé připojení. Když se uživatel znovu připojí, můžete změny v datech šířeny zpět do zdroje dat serveru.  
  
## <a name="cached-data-and-custom-xml-parts-compared"></a>Data uložená v mezipaměti a vlastní části XML, porovnání  
 Vlastní části XML byly zavedeny v systému Microsoft Office 2007 jako způsob, jak ukládat libovolné části XML v dokumentu. I když jsou užitečné v mnoha stejné scénáře jako mezipaměť dat vlastní části XML, existují určité rozdíly mezi datový ostrůvek a vlastní části XML. Další informace o vlastních částí XML, naleznete v tématu [Přehled vlastních částí XML](../vsto/custom-xml-parts-overview.md).  
  
 V následující tabulce jsou uvedeny některé rozdíly a podobnosti.  
  
||Mezipaměť dat|Vlastní části XML|  
|-|----------------|----------------------|  
|Aplikace Office, které mohou využívat?|Přizpůsobení na úrovni dokumentu v následujících aplikacích:<br /><br /> – Excel<br />-Aplikace Word|Řešení na úrovni dokumentu a úrovni aplikace v následujících aplikacích:<br /><br /> – Excel<br />-PowerPoint<br />-Aplikace Word|  
|Jaké typy dat můžete ukládat?|Všechny veřejné objektu vlastního nastavení sestavení, který splňuje určité požadavky. Další informace najdete v tématu [ukládat data do mezipaměti](../vsto/caching-data.md).|Žádná data XML.|  
|Může přistupovat k datům bez spuštění aplikace Microsoft Office?|Ano, s použitím <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídy poskytované [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|Ano, s využitím tříd v <xref:System.IO.Packaging> obor názvů, nebo pomocí sady SDK formát Open XML.|  
  
## <a name="see-also"></a>Viz také:  
 [Data v řešeních pro systém Office](../vsto/data-in-office-solutions.md)   
 [Architektura řešení pro Office v sadě Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  