---
title: Data mezipaměti
description: Přečtěte si, jak můžete ukládat datové objekty do mezipaměti v přizpůsobení na úrovni dokumentu, aby data mohla být dostupná offline nebo bez otevírání systém Microsoft Office Wordu nebo Excelu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f31556e64ee93a73fb09c27edd095bcd2653dfdc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836160"
---
# <a name="cache-data"></a>Data mezipaměti
  Datové objekty můžete ukládat do mezipaměti v přizpůsobení na úrovni dokumentu, aby k datům bylo možné přejít offline nebo bez nutnosti otevírat systém Microsoft Office Word nebo systém Microsoft Office Excelu. Chcete-li objekt ukládat do mezipaměti, musí mít objekt datový typ, který splňuje určité požadavky. Mnoho běžných datových typů v .NET Framework splňuje tyto požadavky, včetně <xref:System.String> , <xref:System.Data.DataSet> a <xref:System.Data.DataTable> .

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Existují dva způsoby, jak přidat objekt do mezipaměti dat:

- Chcete-li přidat objekt do mezipaměti dat při sestavení řešení, použijte <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atribut na deklaraci objektu. Další informace najdete v tématu [Postupy: ukládání dat do mezipaměti pro použití v režimu offline nebo na serveru](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Chcete-li programově přidat objekt do mezipaměti dat v době běhu, použijte `StartCaching` metodu hostitelské položky, například `ThisDocument` `ThisWorkbook` třídy nebo. Další informace najdete v tématu [Postup: ukládání zdroje dat do dokumentu Office do mezipaměti prostřednictvím kódu programu](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).

  Po přidání objektu do mezipaměti dat máte přístup k datům uloženým v mezipaměti a jejich úpravu bez spuštění aplikace Word nebo Excel. Další informace najdete v tématu [přístup k datům v dokumentech na serveru](../vsto/accessing-data-in-documents-on-the-server.md).

## <a name="requirements-for-data-objects-to-be-cached"></a>Požadavky na ukládání datových objektů do mezipaměti
 Chcete-li uložit datový objekt do mezipaměti v řešení, objekt musí splňovat tyto požadavky:

- Musí se jednat o veřejné pole nebo vlastnost položky hostitele pro čtení a zápis, jako jsou `ThisDocument` `ThisWorkbook` třídy nebo.

- Nejedná se o indexer ani o jinou parametrizovanou vlastnost.

  Kromě toho musí být datový objekt serializovatelný <xref:System.Xml.Serialization.XmlSerializer> třídou, což znamená, že typ objektu musí mít tyto vlastnosti:

- Být veřejný typ.

- Mít veřejný konstruktor bez parametrů.

- Nespustí kód, který vyžaduje další oprávnění zabezpečení.

- Zveřejňujte pouze veřejné vlastnosti pro čtení a zápis (ostatní vlastnosti budou ignorovány).

- Nezveřejňujte multidimenzionální pole (jsou přijímána vnořená pole).

- Nenávratová rozhraní z vlastností a polí.

- Neimplementuje, <xref:System.Collections.IDictionary> Pokud je kolekce.

  Při ukládání datového objektu do mezipaměti je [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] objekt serializován do řetězce XML, který je uložen ve *vlastní části XML* v dokumentu. Další informace najdete v tématu [Přehled vlastních částí XML](../vsto/custom-xml-parts-overview.md).

## <a name="cached-data-size-limits"></a>Limity velikosti dat v mezipaměti
 K dispozici jsou určitá omezení celkového množství dat, která lze přidat do mezipaměti dat v dokumentu a velikosti jednotlivých objektů v mezipaměti dat. Pokud tato omezení překročíte, aplikace se může po uložení dat do mezipaměti dat neočekávaně zavřít.

 Pokud se chcete těmto omezením vyhnout, postupujte podle těchto pokynů:

- Nepřidávejte žádné objekty větší než 10 MB do mezipaměti dat.

- Do mezipaměti dat v jednom dokumentu Nepřidávejte více než 100 MB celkových dat.

  Jedná se o přibližné hodnoty. Přesná omezení závisí na několika faktorech, včetně dostupné paměti RAM a počtu spuštěných procesů.

## <a name="control-the-behavior-of-cached-objects"></a>Řízení chování objektů uložených v mezipaměti
 Chcete-li získat větší kontrolu nad chováním objektu v mezipaměti, můžete implementovat <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> rozhraní pro typ objektu v mezipaměti. Například můžete implementovat toto rozhraní, pokud chcete určit, jak se uživateli zobrazí oznámení o změně objektu. Příklady kódu, které ukazují, jak implementovat <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> , najdete v tématu `ControlCollection` Třída v ukázce dynamické ovládací prvky Excelu a ukázka dynamických ovládacích prvků Word v [ukázkách vývoje a návodů pro Office](../vsto/office-development-samples-and-walkthroughs.md).

## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>Zachovat změny dat uložených v mezipaměti v dokumentech chráněných heslem
 Pokud ukládáte datové objekty do mezipaměti v dokumentu chráněném heslem, změny dat uložených v mezipaměti nebudou uloženy. Změny dat uložených v mezipaměti můžete uložit přepsáním dvou metod. Přepište tyto metody pro dočasné odebrání ochrany při uložení dokumentu a pak ochranu znovu použijte po dokončení operace uložení.

 Další informace najdete v tématu [Postupy: ukládání dat do mezipaměti v dokumentu chráněném heslem](../vsto/how-to-cache-data-in-a-password-protected-document.md).

## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>Zabránit ztrátě dat při přidávání hodnot null do mezipaměti dat
 Při přidávání objektů do mezipaměti dat musí být všechny objekty v mezipaměti inicializovány na hodnotu, která není **null** , před uložením a zavřením dokumentu. Pokud má nějaký objekt v mezipaměti hodnotu **null** , když se dokument uloží a zavře, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] automaticky odebere všechny objekty uložené v mezipaměti z mezipaměti dat.

 Pokud přidáte objekt s hodnotou **null** do mezipaměti dat pomocí <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributu v době návrhu, můžete použít <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídu k inicializaci datových objektů uložených v mezipaměti před otevřením dokumentu. To je užitečné, pokud chcete inicializovat data uložená v mezipaměti na serveru bez nainstalovaného aplikace Word nebo Excel, než je dokument otevřen koncovým uživatelem. Další informace najdete v tématu [přístup k datům v dokumentech na serveru](../vsto/accessing-data-in-documents-on-the-server.md).

## <a name="see-also"></a>Viz také
- [Postupy: ukládání dat do mezipaměti pro použití v režimu offline nebo na serveru](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Postupy: ukládání zdroje dat v dokumentu Office do mezipaměti prostřednictvím kódu programu](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Postupy: ukládání dat do mezipaměti v dokumentu chráněném heslem](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Návod: Vytvoření vztahu hlavní podrobnosti pomocí datové sady uložené v mezipaměti](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)
