---
title: Datová vazba WPF s LINQ to XML přehled | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bf80845-891b-41de-a71b-4080b5bd3ea6
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 457a097d46f9af409580d3784bb577090db0c535
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49852411"
---
# <a name="wpf-data-binding-with-linq-to-xml-overview"></a>Datová vazba WPF s LINQ to XML přehled
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje funkce vazby dynamických dat v <xref:System.Xml.Linq> oboru názvů. Tyto funkce lze použít jako zdroj dat pro prvky uživatelského rozhraní (UI) ve Windows Presentation Foundation (WPF).  
  
## <a name="xaml-and-linq-to-xml"></a>XAML a LINQ to XML  
 Rozšiřitelné aplikace Markup Language (XAML) je XML dialekt vytvořeného microsoftem pro podporu technologií rozhraní .NET Framework 3.0. Používá se v subsystému WPF představující prvky uživatelského rozhraní a související funkce, jako jsou události a datové vazby. V modelu Windows Workflow Foundation XAML se používá k reprezentování struktura programu, jako je například ovládací prvek programu (*pracovních postupů*). XAML umožňuje deklarativní aspekty technologie být odděleno od související procedurální kódu, který definuje více individualizovaná chování programu.  
  
 Existují dva široké způsobů, kterými můžete pracovat XAML a LINQ to XML:  
  
- Protože soubory XAML ve správném formátu XML, je možné dotazovat a manipulovat prostřednictvím technologiím, jako je například technologie LINQ to XML.  
  
- Protože LINQ to XML dotazy představují zdroj dat, tyto dotazy můžete použít jako zdroj dat pro datovou vazbu pro prvky uživatelského rozhraní WPF.  
  
  Tato dokumentace popisuje druhý scénář.  
  
## <a name="data-binding-in-the-windows-presentation-foundation"></a>Datové vazby ve Windows Presentation Foundation  
 Datové vazby WPF umožňuje prvku uživatelského rozhraní pro přidružení jedné z vlastností se zdrojem dat. Je to jednoduchý příklad <xref:System.Windows.Controls.Label> jejichž text představuje hodnotu veřejnou vlastnost do uživatelsky definovaného objektu. Datové vazby WPF spoléhá na následující komponenty:  
  
|Součást|Popis|  
|---------------|-----------------|  
|Cíl vazby|Prvek uživatelského rozhraní, které chcete přidružit ke zdroji dat. Vizuální prvky v objektu WPF jsou odvozeny z <xref:System.Windows.UIElement> třídy.|  
|Vlastnost target|*Vlastnost závislosti* cíle vazby, který odpovídá hodnotě zdrojové datové vazby. Vlastnosti závislosti jsou podporovány přímo <xref:System.Windows.DependencyObject> třídy, které <xref:System.Windows.UIElement> je odvozena z.|  
|Zdroje připojení|Zdrojový objekt pro jednu nebo více hodnot, které jsou dodávány pro prvek uživatelského rozhraní pro prezentaci. WPF automaticky podporuje následující typy jako vytvoření vazby zdroje: CLR objekty, objekty dat ADO.NET, data XML (z nebo technologie LINQ to XML dotazy XPath) nebo jiné <xref:System.Windows.DependencyObject>.|  
|Zdrojová cesta|Vlastnosti zdroje vazby, který se přeloží na hodnotu nebo množinu hodnot, který má být vázána.|  
  
 Vlastnost závislosti je koncept specifické pro WPF, které představují dynamicky vypočítané vlastnosti prvku uživatelského rozhraní. Vlastnosti závislostí například často mají výchozí hodnoty nebo hodnoty, které jsou k dispozici v nadřazeném elementu. Tyto speciální vlastnosti využívají instance <xref:System.Windows.DependencyProperty> třídu (a ne pole jako pomocí standardní vlastnosti). Další informace najdete v tématu [přehled vlastností závislosti](http://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5).  
  
### <a name="dynamic-data-binding-in-wpf"></a>Dynamické datové vazby ve WPF  
 Ve výchozím nastavení datová vazba dochází pouze v případě, že je inicializován cílového prvku uživatelského rozhraní. Tento postup se nazývá *jednorázové* vazby. Pro většinu účelů to nestačí; datové vazby řešení obvykle vyžaduje, že změny rozšířit dynamicky za běhu pomocí jedné z následujících akcí:  
  
- *Jednosměrná* vazby způsobí, že se změní na jedné straně mohly rozšířit automaticky. Nejčastěji se projeví změny do zdroje do cíle, ale naopak někdy může být užitečné.  
  
- V *obousměrný* vazby, změny ve zdroji se automaticky rozšíří do cíle a změny cíle se automaticky rozšíří na zdroji.  
  
  Jednosměrné nebo obousměrné vazby na výskyt, zdroj musí implementovat mechanismus oznámení změn, například implementací <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní nebo pomocí *PropertyNameChanged* vzor pro každou vlastnost podporována.  
  
  Další informace o datové vazbě v subsystému WPF naleznete v tématu [datové vazby (WPF)](http://msdn.microsoft.com/library/90f79b97-17e7-40d1-abf0-3ba600ad1d7e).  
  
## <a name="dynamic-properties-in-linq-to-xml-classes"></a>Dynamické vlastnosti v technologii LINQ to XML tříd  
 Většina tříd LINQ to XML jako zdroj dynamických dat správné WPF nekvalifikujte: některé z velmi užitečné informace je k dispozici pouze prostřednictvím metody (a nikoli vlastnosti) a vlastností v těchto tříd neimplementují oznámení o změnách. Pro podporu datové vazby WPF, technologii LINQ to XML zveřejňuje sadu *dynamické vlastnosti*.  
  
 Tyto dynamické vlastnosti jsou speciální vlastnosti za běhu, které duplikují funkce stávajících metod a vlastností v <xref:System.Xml.Linq.XAttribute> a <xref:System.Xml.Linq.XElement> třídy. Byly přidány do těchto tříd výhradně, aby se mohly tak, aby fungoval jako zdroj dynamických dat pro WPF. Chcete-li splňuje tyto potřeby implementovat tyto dynamické vlastnosti oznámení o změnách. V další části, se poskytuje podrobné referenční pro tyto dynamické vlastnosti [XML dynamické vlastnosti LINQ to](../designers/linq-to-xml-dynamic-properties.md).  
  
> [!NOTE]
>  Mnohé standardní veřejné vlastnosti v různých tříd v nalezen <xref:System.Xml.Linq> obor názvů, je možné pro jednorázové datovou vazbu. Nezapomeňte však, že zdrojový ani cílový dynamicky aktualizují v rámci tohoto režimu.  
  
### <a name="accessing-dynamic-properties"></a>Přístup k dynamické vlastnosti  
 Dynamické vlastnosti v <xref:System.Xml.Linq.XAttribute> a <xref:System.Xml.Linq.XElement> třídy nelze získat přístup, jako je standardní vlastnosti. Například CLS CLR jazyků C#, nemohou být:  
  
- Přistupovat přímo v době kompilace. Dynamické vlastnosti nejsou viditelná v kompilátoru a IntelliSense ve Visual Studio.  
  
- Zjištěná nebo používaná v době běhu pomocí reflexe .NET. Dokonce i v době běhu nejsou vlastnosti v základní smysl CLR.  
  
  V jazyce C#, dynamické vlastnosti je přístupný pouze v době běhu prostřednictvím zařízení poskytovaných <xref:System.ComponentModel> oboru názvů.  
  
  Naproti tomu však ve formátu XML dynamické vlastnosti zdroje budou přístupné prostřednictvím jednoduché zápis v následujícím tvaru:  
  
```  
<object>.<dynamic-property>  
```  
  
 Dynamické vlastnosti pro tyto dvě třídy, vyřeší hodnotu, která je možné přímo, nebo indexer, který musí být zadán s indexem získat výsledné hodnoty nebo shromažďování hodnot. Druhá syntaxe má podobu:  
  
```  
<object>.<dynamic-property>[<index-value>]  
```  
  
 Další informace najdete v tématu [XML dynamické vlastnosti LINQ to](../designers/linq-to-xml-dynamic-properties.md).  
  
 K implementaci WPF dynamické vazby, se použije dynamické vlastnosti zařízení poskytovaných <xref:System.Windows.Data> obor názvů, zejména <xref:System.Windows.Data.Binding> třídy.  
  
## <a name="see-also"></a>Viz také  
 [Datová vazba WPF s LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [Technologie LINQ to XML dynamické vlastnosti](../designers/linq-to-xml-dynamic-properties.md)   
 [XAML ve WPF](http://msdn.microsoft.com/library/5d858575-a83b-42df-ad3f-047ed2d6e3c8)   
 [Datová vazba (WPF)](http://msdn.microsoft.com/library/90f79b97-17e7-40d1-abf0-3ba600ad1d7e)   
 [Pomocí značek pracovního postupu](http://go.microsoft.com/fwlink/?LinkId=98685)



