---
title: XMLNodes – ovládací prvek
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, events
- XMLNodes control
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 18b1a9cf6028b02d16b15b17950b9918b7b79d89
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258535"
---
# <a name="xmlnodes-control"></a>XMLNodes – ovládací prvek
  **Důležité** informace uvedené v tomto tématu týkající se aplikace Microsoft Word je vidění výhradně pro benefit a použití jednotlivce a organizace, kteří se nacházejí mimo Spojené státy a jeho území nebo který používáte, nebo vývoj programy, které běží na, produkty Microsoft Word, které byly před leden 2010, když Microsoft odebrat implementace konkrétní funkce licencí společnosti Microsoft týkající se vlastní kód XML z aplikace Microsoft Word. Tyto informace týkající se aplikace Microsoft Word nemusí přečteny nebo používány jednotlivce nebo organizace v USA nebo v jeho území, které používáte, nebo vývoj programy, které běží na produkty Microsoft Word, které byly licencí společnosti Microsoft po 10 leden 2010 ; tyto produkty nebudou chovají stejně jako produkty licencované před tímto datem nebo zakoupených a licenci na použití mimo Spojené státy.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNodes> Řízení je kolekce objektů namapované uzel XML, který zpřístupní události. <xref:Microsoft.Office.Tools.Word.XMLNodes> Ovládací prvek je vytvořen pouze v případě, že opakující se prvek schématu je namapovaný na dokument aplikace Microsoft Office Word. Pokud opakující se prvek obsahuje podřízené elementy, jednotlivých podřízených prvků se také vytvoří jako <xref:Microsoft.Office.Tools.Word.XMLNodes> ovládacího prvku.  
  
 Jakmile sady Visual Studio vytvoří kolekci z uzlů XML, můžete ovládat ovládacího prvku přímo bez nutnosti procházení model objektů aplikace Word. <xref:Microsoft.Office.Tools.Word.XMLNodes> Řízení lze odstranit pouze odebráním mapování elementu z dokumentu.  
  
> [!NOTE]  
>  Pokud máte přístup k podřízeného prvku <xref:Microsoft.Office.Tools.Word.XMLNodes> ovládat prostřednictvím <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> vlastnost, vrátí <xref:Microsoft.Office.Interop.Word.XMLNode> objekt ne <xref:Microsoft.Office.Tools.Word.XMLNode> ovládacího prvku. Další informace najdete v tématu [programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="bind-data-to-the-control"></a>Vázání dat k ovládacímu prvku  
 <xref:Microsoft.Office.Tools.Word.XMLNodes> Ovládací prvek nepodporuje datová vazba. Důvodem je, že <xref:Microsoft.Office.Tools.Word.XMLNodes> ovládací prvek nemá rozšířené datové vazby funkcí a jednoduché datové vazby nelze představují opakující se data.  
  
## <a name="formatting"></a>Formátování  
 Veškeré formátování, které lze použít na text v tomto dokumentu lze použít <xref:Microsoft.Office.Tools.Word.XMLNodes> ovládacího prvku.  
  
## <a name="events"></a>Události  
 K dispozici pro události <xref:Microsoft.Office.Tools.Word.XMLNodes> řízení, představují:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>  
  
## <a name="compare-events"></a>Porovnání události  
 Můžete zaznamenat událost v případě, že uživatel přesune své kurzor v rámci konkrétní <xref:Microsoft.Office.Tools.Word.XMLNodes> ovládacího prvku. Například můžete mít <xref:Microsoft.Office.Tools.Word.XMLNodes> ovládací prvek s názvem `Customer` má podřízenou <xref:Microsoft.Office.Tools.Word.XMLNodes> ovládací prvek s názvem `Company`, a `Company` má dva podřízené <xref:Microsoft.Office.Tools.Word.XMLNodes> ovládací prvky s názvem `CompanyName` a `CompanyRegion` následujícím způsobem:  
  
```xml  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Pokud chcete zobrazit ovládací prvek v podokně akce vždy, když ukazatel je přesunut do `Company` uzlu je nesmí důležité, zda je umístěn kurzor v `CompanyName` nebo `CompanyRegion` vzhledem k tomu, že jsou oba v kontextu `Company`. V takovém případě můžete napsat kód <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> události `Company`.  
  
 Ve většině případů, kdy ukazatel vstoupí <xref:Microsoft.Office.Tools.Word.XMLNodes> řídit, jak <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> a <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> události jsou vyvolány. V následující tabulce jsou uvedeny rozdíly mezi tyto události.  
  
|Vyberte události|ContextEnter událostí|  
|------------------|------------------------|  
|Nastane, když ukazatel je umístěn uvnitř jednoho z uzlů <xref:Microsoft.Office.Tools.Word.XMLNodes> kolekce.|Nastane, když ukazatel je umístěn uvnitř jeden z uzlů nebo následné uzlů <xref:Microsoft.Office.Tools.Word.XMLNodes> kolekci z oblasti mimo kontext uzlu. Jinými slovy, je vyvolána, pouze v případě změny kontextu a mohou být vyvolány pro více vnořených <xref:Microsoft.Office.Tools.Word.XMLNodes> ovládací prvky.|  
  
 Například když přesunete kurzor z mimo `Customer` do `CompanyName`, <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> události pro `Customer`, `Company`, a `CompanyName` jsou vyvolány. Pokud pak přesuňte se ukazatelem z `CompanyName` k `CompanyRegion`, <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> událost pouze pro `CompanyRegion` se vyvolá, protože kontext je stejné pro `Company` a `Customer`. Můžete mít více `Company` uzly v dokumentu. Pokud přesunutí kurzoru z `CompanyName` uzlu jednoho `Company` k `CompanyName` uzlu jiného `Company`, kontext je stejné, takže jenom <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> událost se vyvolá.  
  
 Existují stejné rozdíly mezi <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> událostí a <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> událostí.  
  
## <a name="see-also"></a>Viz také:  
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)   
 [XmlNode – ovládací prvek](../vsto/xmlnode-control.md)   
 [Postupy: Přidání ovládacích prvků XMLNodes do dokumentů aplikace Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Postupy: mapování schémat na dokumenty aplikace Word v sadě Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  