---
title: XMLNodes – ovládací prvek
description: Přečtěte si, že ovládací prvek XMLNodes je vytvořen pouze v případě, že je opakující se element schématu mapován na dokument aplikace Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, events
- XMLNodes control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cd82b4bac36d648bee3f6735cf844691ef6d58b2
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527843"
---
# <a name="xmlnodes-control"></a>XMLNodes – ovládací prvek
  **Důležité** informace Informace uvedené v tomto tématu týkající se Microsoft Wordu se poskytují výhradně pro zvýhodnění a použití jednotlivců a organizací, kteří se nacházejí mimo USA a její oblasti nebo kteří používají nebo vyvíjí programy, na kterých běží, od společnosti Microsoft Word, které byly licencované od společnosti Microsoft před lednem 2010, když společnost Microsoft odebrala implementaci konkrétních funkcí souvisejících s vlastním kódem XML z aplikace Microsoft Word. Tyto informace týkající se Microsoft Wordu nemusí číst ani používat jednotlivci nebo organizace v USA nebo na jejích oblastech, kteří používají, nebo vyvíjet programy, na kterých běží, od společnosti Microsoft Word, které byly licencované od Microsoftu po 10. ledna 2010. Tyto produkty se nebudou chovat stejně jako produkty licencované před tímto datem nebo zakoupené a licencované pro použití mimo USA.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 <xref:Microsoft.Office.Tools.Word.XMLNodes>Ovládací prvek je kolekcí objektů mapovaných uzlů XML, které zpřístupňují události. <xref:Microsoft.Office.Tools.Word.XMLNodes>Ovládací prvek je vytvořen pouze v případě, že je opakující se element schématu mapován na systém Microsoft Office wordový dokument. Pokud opakující element obsahuje podřízené prvky, každá z podřízených elementů je také vytvořena jako <xref:Microsoft.Office.Tools.Word.XMLNodes> ovládací prvek.

 Poté, co sada Visual Studio vytvoří kolekci uzlů XML, lze programovat na ovládacím prvku přímo bez nutnosti procházení objektového modelu aplikace Word. <xref:Microsoft.Office.Tools.Word.XMLNodes>Ovládací prvek lze odstranit pouze odebráním mapování elementu z dokumentu.

> [!NOTE]
> Pokud přistupujete k podřízenému prvku <xref:Microsoft.Office.Tools.Word.XMLNodes> ovládacího prvku prostřednictvím <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> vlastnosti, vrátí <xref:Microsoft.Office.Interop.Word.XMLNode> objekt spíše než <xref:Microsoft.Office.Tools.Word.XMLNode> ovládací prvek. Další informace najdete v tématu [programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="bind-data-to-the-control"></a>Vázání dat k ovládacímu prvku
 <xref:Microsoft.Office.Tools.Word.XMLNodes>Ovládací prvek nepodporuje datovou vazbu. Důvodem je to <xref:Microsoft.Office.Tools.Word.XMLNodes> , že ovládací prvek nemá komplexní možnosti vytváření datových vazeb a jednoduchá vazba dat nemůže reprezentovat opakující se data.

## <a name="formatting"></a>Formátování
 Pro ovládací prvek lze použít jakékoli formátování, které lze použít na text v dokumentu <xref:Microsoft.Office.Tools.Word.XMLNodes> .

## <a name="events"></a>Události
 K dispozici jsou události pro <xref:Microsoft.Office.Tools.Word.XMLNodes> ovládací prvek:

- <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>

## <a name="compare-events"></a>Porovnat události
 Můžete zachytit událost, když uživatel přesune svůj kurzor do kontextu určitého <xref:Microsoft.Office.Tools.Word.XMLNodes> ovládacího prvku. Například můžete mít <xref:Microsoft.Office.Tools.Word.XMLNodes> ovládací prvek s názvem `Customer` , který má podřízený <xref:Microsoft.Office.Tools.Word.XMLNodes> ovládací prvek s názvem a `Company` `Company` má dva podřízené <xref:Microsoft.Office.Tools.Word.XMLNodes> ovládací prvky s názvem a následujícím `CompanyName` `CompanyRegion` způsobem:

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Chcete-li zobrazit ovládací prvek v podokně akce vždy, když je kurzor přesunut do `Company` uzlu, neměl by se jednat o skutečnost, zda je kurzor umístěn v `CompanyName` nebo, `CompanyRegion` protože jsou v rámci kontextu `Company` . V takovém případě můžete napsat kód v <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> případě `Company` .

 Ve většině případů, když kurzor vstoupí do <xref:Microsoft.Office.Tools.Word.XMLNodes> ovládacího prvku, <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> jsou vyvolány události a. V následující tabulce jsou uvedeny rozdíly mezi těmito událostmi.

|Vybrat událost|Událost ContextEnter|
|------------------|------------------------|
|Vyvolá se v případě, že je kurzor umístěn uvnitř jednoho z uzlů <xref:Microsoft.Office.Tools.Word.XMLNodes> kolekce.|Nastane, pokud je kurzor umístěn uvnitř jednoho z uzlů nebo podřízených uzlů <xref:Microsoft.Office.Tools.Word.XMLNodes> kolekce, z oblasti mimo kontext uzlu. Jinými slovy, je vyvolána pouze v případě změny kontextu a lze jej vyvolat pro více vnořených <xref:Microsoft.Office.Tools.Word.XMLNodes> ovládacích prvků.|

 Například když přesunete kurzor mimo aplikaci `Customer` do `CompanyName` , <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> `Customer` `Company` `CompanyName` jsou vyvolány události pro, a. Pokud pak přesunete kurzor z `CompanyName` na `CompanyRegion` , vyvolá se <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> pouze událost pro `CompanyRegion` je vyvolána, protože kontext je stejný pro i `Company` `Customer` . V dokumentu může být více `Company` uzlů. Pokud přesunete kurzor z `CompanyName` uzlu jednoho `Company` na `CompanyName` uzel jiného `Company` , kontext je stejný, takže <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> je vyvolána pouze událost.

 Mezi <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> událostí a událostí existují stejné rozdíly <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> .

## <a name="see-also"></a>Viz také
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)
- [XMLNode – ovládací prvek](../vsto/xmlnode-control.md)
- [Postupy: Přidání ovládacích prvků XMLNodes do dokumentů aplikace Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [Postupy: mapování schémat na dokumenty aplikace Word v rámci sady Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
