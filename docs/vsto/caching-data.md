---
title: Data v mezipaměti
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: b46fa8b0138eff03757a7bd7828053cee039090f
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248115"
---
# <a name="cache-data"></a>Data v mezipaměti
  Datové objekty v přizpůsobení na úrovni dokumentu můžete mezipaměti tak, aby data přístupná v režimu offline, nebo bez otevření aplikace Microsoft Office Word nebo Microsoft Office Excel. Pro ukládání do mezipaměti objekt objekt musí mít datový typ, který splňuje určité požadavky. Mnoho běžných typů dat v rozhraní .NET Framework splňovat tyto požadavky, včetně <xref:System.String>, <xref:System.Data.DataSet>, a <xref:System.Data.DataTable>.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Existují dva způsoby přidání objektu do datové mezipaměti:  
  
- Přidání objektu do datové mezipaměti po sestavení řešení, použije <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atribut deklarace objektu. Další informace najdete v tématu [jak: Mezipaměť dat pro použití v režimu offline nebo na serveru](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
- Chcete-li programově přidat objektu do datové mezipaměti v době běhu, použijte `StartCaching` metoda hostitele položky, například `ThisDocument` nebo `ThisWorkbook` třídy. Další informace najdete v tématu [jak: Zdroj dat v dokumentu systému Office do mezipaměti prostřednictvím kódu programu](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
  Po přidání objektu do datové mezipaměti můžete používat a upravovat data uložená v mezipaměti bez spuštění aplikace Word nebo Excel. Další informace najdete v tématu [přístup k datům v dokumentech na serveru](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="requirements-for-data-objects-to-be-cached"></a>Požadavky pro datové objekty do mezipaměti  
 Pro ukládání do mezipaměti objekt dat ve vašem řešení, objekt, musí splňovat tyto požadavky:  
  
- Být r/w veřejné pole nebo vlastnosti hostitele položky, jako `ThisDocument` nebo `ThisWorkbook` třídy.  
  
- Nesmí být jiné parametry vlastnost nebo indexer.  
  
  Kromě toho musí být serializovatelný podle datový objekt <xref:System.Xml.Serialization.XmlSerializer> třídy, což znamená, že typ objektu, musíte mít tyto charakteristiky:  
  
- Být veřejným typem.  
  
- Máte veřejný konstruktor bez parametrů.  
  
- Nelze spustit kód, který vyžaduje další bezpečnostní oprávnění.  
  
- Vystavit pouze pro čtení a zápis veřejné vlastnosti (jiné vlastnosti budou ignorovány).  
  
- Bez odkrytí vícerozměrná pole (vnořená pole jsou přijímány).  
  
- Nevrací rozhraní z vlastnosti a pole.  
  
- Neimplementuje <xref:System.Collections.IDictionary> Pokud kolekce.  
  
  Když mezipaměti datový objekt [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serializuje objekt do řetězce XML, který je uložený v *vlastní část XML* v dokumentu. Další informace najdete v tématu [přehled částí XML vlastní](../vsto/custom-xml-parts-overview.md).  
  
## <a name="cached-data-size-limits"></a>Omezení velikosti dat uložených v mezipaměti  
 Existují určitá omezení celkové množství dat, které můžete přidat do datové mezipaměti v dokumentu a velikost všech jednotlivých objektů v datové mezipaměti. Pokud tato omezení překročí, může aplikace nečekaně zavře při uložení dat do datové mezipaměti.  
  
 Abyste se vyhnuli těmto omezením, postupujte podle následujících pokynů:  
  
- Nepřidávejte do datové mezipaměti libovolného objektu, který je větší než 10 MB.  
  
- Nepřidávejte více než 100 MB z celkové množství dat do datové mezipaměti v jednom dokumentu.  
  
  Toto jsou přibližné hodnoty. Přesné omezení závisí na několika různými faktory, včetně dostupné paměti RAM a počet spuštěných procesů.  
  
## <a name="control-the-behavior-of-cached-objects"></a>Řízení chování objektů uložených v mezipaměti  
 Pokud chcete získat větší kontrolu nad chováním objekt uložený v mezipaměti, můžete implementovat <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> rozhraní pro typ objektu v mezipaměti. Pokud chcete řídit, jak se uživatel dozví objektu má při změně, můžete například implementovat toto rozhraní. Příklady kódu, které ukazují, jak implementovat <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>, najdete v článku `ControlCollection` třídy v ukázka dynamické ovládací prvky aplikace Excel a Word dynamické ovládací prvky ukázku v [Office Ukázky a návody vývoje](../vsto/office-development-samples-and-walkthroughs.md).  
  
## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>Zachovat změny uložené v mezipaměti dat v chráněném heslem dokumenty  
 Pokud jste do mezipaměti datových objektů v dokumentu, který je chráněný heslem, změny dat v mezipaměti nejsou uloženy. Změny můžete uložit do data uložená v mezipaměti tak, že přepíšete dvěma způsoby. Přepsat tyto metody dočasně odebrat ochranu, když je dokument uložen a pak znovu použít ochranu po uložení operace se dokončila.  
  
 Další informace najdete v tématu [jak: Mezipaměti dat v dokumentu chráněném heslem](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>Zamezeno ztrátě dat při přidání hodnoty null do datové mezipaměti  
 Při přidání objektů do mezipaměti dat všech objektů uložených v mezipaměti, musí se inicializovat non-**null** hodnota předtím, než je dokument uložit a zavřít. Pokud libovolný objekt v mezipaměti má **null** hodnotu, pokud se dokument uloží a zavřeli, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] se automaticky odeberou všechny uložené v mezipaměti objektů z mezipaměti dat.  
  
 Pokud chcete přidat objekt se **null** hodnotu do datové mezipaměti s použitím <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atribut v době návrhu, můžete použít <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídě pro inicializaci dat uložených v mezipaměti objektů před otevřením dokumentu. To je užitečné, pokud chcete inicializovat data uložená v mezipaměti na serveru aplikace Word nebo Excel nainstalována, než dokument je otevřen v koncový uživatel. Další informace najdete v tématu [přístup k datům v dokumentech na serveru](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: Mezipaměť dat pro použití v režimu offline nebo na serveru](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Postupy: Zdroj dat v dokumentu systému Office do mezipaměti prostřednictvím kódu programu](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Postupy: Data v mezipaměti v dokumentu chráněném heslem](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Návod: Vytvořte relaci hlavní podrobností pomocí datové sady v mezipaměti](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
  
  