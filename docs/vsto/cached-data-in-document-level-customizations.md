---
title: Data uložená v mezipaměti v přizpůsobeních na úrovni dokumentu
description: Přečtěte si, jak Visual Studio odděluje data ze zobrazení v přizpůsobení na úrovni dokumentu tím, že umožňuje vložení dat jako mezipaměti dat.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: be4229c179ec6c5640ab612d28991fe476363a53
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847894"
---
# <a name="cached-data-in-document-level-customizations"></a>Data uložená v mezipaměti v přizpůsobeních na úrovni dokumentu
  Hlavním cílem přizpůsobení na úrovni dokumentu je oddělení dat od zobrazení v dokumentech Office. Data odkazují na informace, které jsou uloženy v dokumentu, včetně čísel a textu. Zobrazení odkazuje na uživatelské rozhraní a objektový model systém Microsoft Office Word a systém Microsoft Office Excel.

 Visual Studio odděluje data ze zobrazení v přizpůsobeních na úrovni dokumentu tím, že povoluje vkládání dat jako *datové ostrůvky*, označované také jako *mezipaměť dat*. Data můžete číst nebo upravovat přímo bez spuštění Wordu nebo Excelu. To je užitečné v případě, že potřebujete upravit data v dokumentech na serveru, na kterém není nainstalovaná aplikace systém Microsoft Office. Word a Excel jsou určené pro použití v klientských prostředích; nejsou určeny ke spouštění na serveru.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Další informace o přizpůsobení na úrovni dokumentu najdete v tématu [Přehled vývoje řešení pro systém Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) a [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md).

## <a name="understand-the-cached-data-programming-model"></a>Princip programovacího modelu pro data v mezipaměti
 Datový ostrůvek může ve vašem řešení obsahovat libovolný objekt, který splňuje určité požadavky. Tyto objekty zahrnují <xref:System.Data.DataSet> objekty, <xref:System.Data.DataTable> objekty a jakýkoli jiný objekt, který může být serializován <xref:System.Xml.Serialization.XmlSerializer> třídou. Další informace najdete v tématu [cache data](../vsto/caching-data.md).

 Chcete-li poskytnout zobrazení pro data uložená v mezipaměti, můžete navazovat ovládací prvky model Windows Forms a *hostitelské ovládací prvky* v dokumentu na objekty v datovém ostrovu. Datová vazba mezi datovým ostrůvkem a ovládacími prvky svázanými s daty udržuje dvě synchronizované. Můžete také přidat ověřovací kód pro data, která jsou nezávislá na ovládacích prvcích. Další informace najdete v tématu [vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md).

 Hostitelské ovládací prvky jsou rozšířené verze nativních objektů v objektových modelech aplikace Excel a Word. Na rozdíl od nativních objektů lze hostitelské ovládací prvky svázat přímo se spravovanými datovými objekty. Další informace najdete v tématu [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md) a [model Windows Forms ovládacích prvků v dokumentech Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="access-cached-data-on-the-server"></a>Přístup k datům uloženým v mezipaměti na serveru
 Chcete-li získat přístup k datům uloženým v mezipaměti v dokumentu, můžete použít <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídu. Tato třída je součástí a je [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] možné ji použít na serveru bez spuštění aplikace Excel nebo Word. Když uživatel otevře dokument po úpravě dat uložených v mezipaměti, všechny ovládací prvky, které jsou vázány na data, budou automaticky synchronizovány se změnami a uživatel se zobrazí s aktualizovanými daty. Další informace najdete v tématu [přístup k datům v dokumentech na serveru](../vsto/accessing-data-in-documents-on-the-server.md).

 Aplikace Excel a Word není nutné zapisovat na data na serveru, pouze k jejich zobrazení na klientovi. Aplikace Excel a Word není dokonce nutné instalovat na server. To poskytuje lepší škálovatelnost a možnost provádět rychlé dávkové zpracování dokumentů, které obsahují datové ostrůvky.

## <a name="data-caching-for-offline-use"></a>Ukládání dat do mezipaměti pro použití v režimu offline
 Ukládání dat v datovém ostrově umožňuje offline scénáře. Když uživatel poprvé otevře dokument nebo požádá o dokument od serveru, datový ostrůvek se vyplní nejnovějšími daty. Datový ostrůvek je uložen do mezipaměti v dokumentu a je pak k dispozici v režimu offline. Uživatel (a váš kód) může manipulovat s daty, i když není k dispozici žádné živé připojení. Když se uživatel znovu připojí, změny dat se dají rozšířit zpátky do zdroje dat na serveru.

## <a name="cached-data-and-custom-xml-parts-compared"></a>Porovnání dat uložených v mezipaměti a vlastních částí XML
 Vlastní části XML byly představeny v 2007 systém Microsoft Office systému jako způsob ukládání libovolných částí XML do dokumentu. I když jsou vlastní části XML užitečné v mnoha stejných scénářích jako mezipaměť dat, existují určité rozdíly mezi datovými ostrovy a vlastními částmi XML. Další informace o vlastních částech XML naleznete v tématu [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md).

 V následující tabulce jsou uvedeny některé rozdíly a podobnosti.

|Otázka/charakteristika|Mezipaměť dat|Vlastní části XML|
|-|----------------|----------------------|
|Které aplikace Office je můžou používat?|Přizpůsobení na úrovni dokumentu pro následující aplikace:<br /><br /> – Excel<br />– Word|Řešení na úrovni dokumentu a na úrovni aplikace pro následující aplikace:<br /><br /> – Excel<br />– PowerPoint<br />– Word|
|Jaké typy dat můžete ukládat?|Všechny veřejné objekty v sestavení vlastního nastavení, které splňují určité požadavky. Další informace najdete v tématu [cache data](../vsto/caching-data.md).|Všechna data XML.|
|Máte přístup k datům, aniž byste museli spouštět aplikace systém Microsoft Office?|Ano, pomocí <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídy poskytované [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .|Ano, pomocí tříd v <xref:System.IO.Packaging> oboru názvů nebo pomocí Open XML Format SDK.|

## <a name="see-also"></a>Viz také
- [Data v řešeních pro systém Office](../vsto/data-in-office-solutions.md)
- [Architektura řešení pro systém Office v sadě Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
