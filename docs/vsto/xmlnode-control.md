---
title: XMLNode – ovládací prvek
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cd047814f11b5fddad868bd65b84deba369facd5
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258886"
---
# <a name="xmlnode-control"></a>XMLNode – ovládací prvek
  **Důležité** informace uvedené v tomto tématu týkající se aplikace Microsoft Word je vidění výhradně pro benefit a použití jednotlivce a organizace, kteří se nacházejí mimo Spojené státy a jeho území nebo který používáte, nebo vývoj programy, které běží na, produkty Microsoft Word, které byly před leden 2010, když Microsoft odebrat implementace konkrétní funkce licencí společnosti Microsoft týkající se vlastní kód XML z aplikace Microsoft Word. Tyto informace týkající se aplikace Microsoft Word nemusí přečteny nebo používány jednotlivce nebo organizace v USA nebo v jeho území, které používáte, nebo vývoj programy, které běží na produkty Microsoft Word, které byly licencí společnosti Microsoft po 10 leden 2010 ; tyto produkty nebudou chovají stejně jako produkty licencované před tímto datem nebo zakoupených a licenci na použití mimo Spojené státy.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode> Řízení je namapované objekt uzlu XML, který zpřístupní události a mohou být vázány na data. <xref:Microsoft.Office.Tools.Word.XMLNode> Ovládací prvek je vytvořen pouze v případě, že element bez opakování schématu je namapovaný na dokument aplikace Microsoft Office Word. Po Visual Studio vytvoří uzel XML, můžete je ovládat přímo bez nutnosti procházení model objektů aplikace Word.  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode> Řízení lze odstranit pouze odebráním element mapování v aplikaci Word.  
  
## <a name="bind-data-to-the-control"></a>Vázání dat k ovládacímu prvku  
 <xref:Microsoft.Office.Tools.Word.XMLNode> Řízení podporuje jednoduché datové vazby. Uzel XML by měl být vázán ke zdroji dat pomocí <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> vlastnost. Při aktualizaci dat v datové sadě vázané <xref:Microsoft.Office.Tools.Word.XMLNode> ovládací prvek odráží změny.  
  
## <a name="formatting"></a>Formátování  
 Formátování, které lze použít pro <xref:Microsoft.Office.Interop.Word.XMLNode> objekt lze použít pro <xref:Microsoft.Office.Tools.Word.XMLNode> ovládacího prvku. To zahrnuje písma, podtržení styly a styly znaků.  
  
## <a name="events"></a>Události  
 Tyto události jsou k dispozici pro <xref:Microsoft.Office.Tools.Word.XMLNode> ovládacího prvku:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>  
  
## <a name="compare-events"></a>Porovnání události  
 Můžete zaznamenat událost v případě, že uživatel přesune své kurzor v rámci konkrétní <xref:Microsoft.Office.Tools.Word.XMLNode> ovládacího prvku. Například můžete mít <xref:Microsoft.Office.Tools.Word.XMLNode> ovládací prvek s názvem `Customer` má podřízenou <xref:Microsoft.Office.Tools.Word.XMLNode> ovládací prvek s názvem `Company`, a `Company` má dva podřízené <xref:Microsoft.Office.Tools.Word.XMLNode> ovládací prvky s názvem `CompanyName` a `CompanyRegion` následujícím způsobem:  
  
```xml  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Pokud chcete zobrazit ovládací prvek v podokně akce vždy, když ukazatel je přesunut do `Company` uzlu je nesmí důležité, zda je umístěn kurzor v `CompanyName` nebo `CompanyRegion` vzhledem k tomu, že jsou oba v kontextu `Company`. V takovém případě můžete napsat kód <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> události `Company`.  
  
 Ve většině případů, kdy ukazatel vstoupí <xref:Microsoft.Office.Tools.Word.XMLNode> řídit, jak <xref:Microsoft.Office.Tools.Word.XMLNode.Select> a <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> události jsou vyvolány. V následující tabulce jsou uvedeny rozdíly mezi tyto události.  
  
|Vyberte události|ContextEnter událostí|  
|------------------|------------------------|  
|Nastane, když ukazatel je umístěn uvnitř <xref:Microsoft.Office.Tools.Word.XMLNode>.|Nastane, když ukazatel je umístěn uvnitř <xref:Microsoft.Office.Tools.Word.XMLNode> nebo jednoho z jeho podřízené uzly z oblasti mimo kontext uzlu. Jinými slovy je vyvolána, pouze v případě změny kontextu.|  
  
 Například když přesunete kurzor z mimo `Customer` do `CompanyName`, <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> událost pro `Customer`, `Company`, a `CompanyName` je vyvolána. Pokud pak přesuňte se ukazatelem z `CompanyName` k `CompanyRegion`, jenom <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> událost pro `CompanyRegion` se vyvolá, protože je stále v kontextu obě `Company` a `Customer`.  
  
 Existují stejné rozdíly mezi <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> událostí a <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> událostí.  
  
## <a name="see-also"></a>Viz také:  
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)   
 [XmlNodes – ovládací prvek](../vsto/xmlnodes-control.md)   
 [Postupy: Přidání ovládacích prvků XMLNode do dokumentů aplikace Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Postupy: mapování schémat na dokumenty aplikace Word v sadě Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  