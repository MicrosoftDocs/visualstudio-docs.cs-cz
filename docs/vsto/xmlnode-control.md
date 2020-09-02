---
title: XMLNode – ovládací prvek
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a8bd5c4612b59f909ae623eb4092a209798f98c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62975724"
---
# <a name="xmlnode-control"></a>XMLNode – ovládací prvek
  **Důležité** informace Informace uvedené v tomto tématu týkající se Microsoft Wordu se poskytují výhradně pro zvýhodnění a použití jednotlivců a organizací, kteří se nacházejí mimo USA a její oblasti nebo kteří používají nebo vyvíjí programy, na kterých běží, od společnosti Microsoft Word, které byly licencované od společnosti Microsoft před lednem 2010, když společnost Microsoft odebrala implementaci konkrétních funkcí souvisejících s vlastním kódem XML z aplikace Microsoft Word. Tyto informace týkající se Microsoft Wordu nemusí číst ani používat jednotlivci nebo organizace v USA nebo na jejích oblastech, kteří používají, nebo vyvíjet programy, na kterých běží, od společnosti Microsoft Word, které byly licencované od Microsoftu po 10. ledna 2010. Tyto produkty se nebudou chovat stejně jako produkty licencované před tímto datem nebo zakoupené a licencované pro použití mimo USA.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 <xref:Microsoft.Office.Tools.Word.XMLNode>Ovládací prvek je mapovaný objekt uzlu XML, který zpřístupňuje události a může být svázán s daty. <xref:Microsoft.Office.Tools.Word.XMLNode>Ovládací prvek je vytvořen pouze v případě, že není opakující se element schématu mapován na systém Microsoft Office wordový dokument. Poté, co aplikace Visual Studio vytvoří uzel XML, můžete jej naprogramovat přímo bez nutnosti procházení objektového modelu aplikace Word.

 <xref:Microsoft.Office.Tools.Word.XMLNode>Ovládací prvek lze odstranit pouze odebráním mapování elementu ve Wordu.

## <a name="bind-data-to-the-control"></a>Vázání dat k ovládacímu prvku
 <xref:Microsoft.Office.Tools.Word.XMLNode>Ovládací prvek podporuje jednoduchou datovou vazbu. Uzel XML by měl být svázán se zdrojem dat pomocí <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> Vlastnosti. Pokud jsou data v vázané sadě dat aktualizována, <xref:Microsoft.Office.Tools.Word.XMLNode> ovládací prvek tyto změny odráží.

## <a name="formatting"></a>Formátování
 Formátování, které lze použít na <xref:Microsoft.Office.Interop.Word.XMLNode> objekt, lze použít pro <xref:Microsoft.Office.Tools.Word.XMLNode> ovládací prvek. To zahrnuje písma, styly podtržení a znakové styly.

## <a name="events"></a>Události
 Pro ovládací prvek jsou k dispozici následující události <xref:Microsoft.Office.Tools.Word.XMLNode> :

- <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>

## <a name="compare-events"></a>Porovnat události
 Můžete zachytit událost, když uživatel přesune svůj kurzor do kontextu určitého <xref:Microsoft.Office.Tools.Word.XMLNode> ovládacího prvku. Například můžete mít <xref:Microsoft.Office.Tools.Word.XMLNode> ovládací prvek s názvem `Customer` , který má podřízený <xref:Microsoft.Office.Tools.Word.XMLNode> ovládací prvek s názvem a `Company` `Company` má dva podřízené <xref:Microsoft.Office.Tools.Word.XMLNode> ovládací prvky s názvem a následujícím `CompanyName` `CompanyRegion` způsobem:

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Chcete-li zobrazit ovládací prvek v podokně akce vždy, když je kurzor přesunut do `Company` uzlu, neměl by se jednat o skutečnost, zda je kurzor umístěn v `CompanyName` nebo, `CompanyRegion` protože jsou v rámci kontextu `Company` . V takovém případě můžete napsat kód v <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> případě `Company` .

 Ve většině případů, když kurzor vstoupí do <xref:Microsoft.Office.Tools.Word.XMLNode> ovládacího prvku, <xref:Microsoft.Office.Tools.Word.XMLNode.Select> <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> jsou vyvolány události a. V následující tabulce jsou uvedeny rozdíly mezi těmito událostmi.

|Vybrat událost|Událost ContextEnter|
|------------------|------------------------|
|Vyvolá se v případě, že je kurzor umístěn uvnitř prvku <xref:Microsoft.Office.Tools.Word.XMLNode> .|Nastane, pokud je kurzor umístěn uvnitř <xref:Microsoft.Office.Tools.Word.XMLNode> nebo jednoho z jeho podřízených uzlů z oblasti mimo kontext uzlu. Jinými slovy, je vyvolána pouze v případě, že dojde ke změně kontextu.|

 Například když přesunete kurzor mimo aplikaci `Customer` do `CompanyName` , <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> `Customer` je vyvolána událost pro, `Company` a `CompanyName` . Pokud pak přesunete kurzor z `CompanyName` na `CompanyRegion` , <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> je vyvolána pouze událost pro, `CompanyRegion` protože jste stále v rámci kontextu `Company` a `Customer` .

 Mezi <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> událostí a událostí existují stejné rozdíly <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> .

## <a name="see-also"></a>Viz také
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)
- [Ovládací prvek XMLNodes](../vsto/xmlnodes-control.md)
- [Postupy: Přidání ovládacích prvků XMLNode do dokumentů aplikace Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)
- [Postupy: mapování schémat na dokumenty aplikace Word v rámci sady Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
