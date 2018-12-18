---
title: Pás karet – XML
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.Ribbon.RibbonXMLItem
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- callback methods
- custom Ribbon, displaying
- custom Ribbon, defining behavior
- XML [Office development in Visual Studio], Ribbon
- customizing the Ribbon, defining behavior
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, displaying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e5502ed118bf5b8bf622f18fd777889127e12aab
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672444"
---
# <a name="ribbon-xml"></a>Pás karet – XML
  Položky pásu karet (XML) umožňuje přizpůsobit pás karet pomocí XML. Pomocí položky pásu karet (XML), pokud chcete přizpůsobit pás karet tak, aby položky pásu karet (vizuální návrhář) nepodporuje. Porovnání můžete dělat s každou položku najdete v tématu [přehled pásu karet](../vsto/Ribbon-overview.md).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="add-a-ribbon-xml-item-to-a-project"></a>Přidání položky pásu karet (XML) do projektu  
 Můžete přidat **pásu karet (XML)** položky do jakéhokoli projektu Office z **přidat novou položku** dialogové okno. Následující soubory sady Visual Studio automaticky přidá do vašeho projektu:  
  
- Souboru XML pásu karet. Tento soubor definuje uživatelské rozhraní (UI) pásu karet. Tento soubor slouží k přidání prvků uživatelského rozhraní, jako jsou karty, skupiny a ovládací prvky. Podrobnosti najdete v tématu [odkaz na soubor kódu XML pásu karet](#RibbonDescriptorFile) dále v tomto tématu.  
  
- Soubor kódu pásu karet. Tento soubor obsahuje *pásu karet třídy*. Tato třída má název, který jste zadali pro **pásu karet (XML)** položky v **přidat novou položku** dialogové okno. Aplikace Microsoft Office pomocí instance této třídy můžete načíst vlastní pás karet. Podrobnosti najdete v tématu [pásu karet – přehled tříd](#RibbonExtensionClass) dále v tomto tématu.  
  
  Ve výchozím nastavení, přidejte tyto soubory vlastní skupinu k **Add-Ins** kartu na pásu karet.  
  
## <a name="display-the-custom-ribbon-in-a-microsoft-office-application"></a>Zobrazit vlastní pás karet v aplikaci Microsoft Office  
 Po přidání **pásu karet (XML)** položky do projektu, je nutné přidat kód pro **ThisAddin**, **ThisWorkbook**, nebo **ThisDocument** třídy který přepíše `CreateRibbonExtensibilityObject` třídu metodu a vrátí kódu XML pásu karet aplikace sady Office.  
  
 Následující kód například přepsání `CreateRibbonExtensibilityObject` metodu a vrátí kódu XML pásu karet pojmenované MyRibbon třídy.  
  
 [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
 [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
## <a name="define-the-behavior-of-the-custom-ribbon"></a>Definuje chování vlastní pás karet  
 Může reagovat na akce uživatele, jako je kliknutí na tlačítko na pásu karet, tak, že vytvoříte *metody zpětného volání*. Metody zpětného volání vypadat podobně jako události v ovládacích prvcích Windows Forms, ale jsou označeny atribut v jazyce XML prvku uživatelského rozhraní. Zápis metod ve třídě pásu karet a ovládacího prvku volá metody, která má stejný název jako hodnota atributu. Můžete například vytvořit metodu zpětného volání, která je volána, když uživatel klikne na tlačítko na pásu karet. Vytvořte metody zpětného volání je potřeba provést dva kroky:  
  
-   Přiřaďte atribut ovládacího prvku v souboru XML pásu karet, který identifikuje metodu zpětného volání ve vašem kódu.  
  
-   Definujte metodu zpětného volání ve třídě pásu karet.  
  
> [!NOTE]  
>  Outlook vyžaduje další krok. Další informace najdete v tématu [přizpůsobte pás karet pro aplikaci Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
 Názorný postup ukazuje, jak automatizovat aplikace pásu karet, najdete v části [návod: vytvoření vlastní karty pomocí kódu XML pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md).  
  
### <a name="assign-callback-methods-to-controls"></a>Přiřadit metody zpětného volání k ovládacím prvkům  
 Přiřadit metody zpětného volání ovládacího prvku v souboru XML pásu karet, přidejte atribut, který určuje typ metody zpětného volání a název metody. Například následující element definuje přepínací tlačítko, který má **onAction** metoda zpětného volání s názvem `OnToggleButton1`.  
  
```xml  
<toggleButton id="toggleButton1" onAction="OnToggleButton1" />  
```  
  
 **onAction** se volá, když uživatel provede hlavního úkolu spojené s konkrétní ovládací prvek. Například **onAction** metoda zpětného volání přepínací tlačítko je volána, když uživatel klikne na tlačítko.  
  
 Metoda, která zadáte v atributu může mít libovolný název. To však musí odpovídat názvu metody, které definujete v souboru s kódem pásu karet.  
  
 Existuje mnoho různých typů metod zpětného volání, které můžete přiřadit ovládacích prvků pásu karet. Úplný seznam metod zpětného volání k dispozici pro každý ovládací prvek, naleznete v tématu technického článku [přizpůsobení uživatelského rozhraní pásu karet Office (2007) pro vývojáře (část 3 ze 3)](/previous-versions/office/developer/office-2007/aa722523(v=office.12)).  
  
###  <a name="CallBackMethods"></a> Definování metod zpětného volání  
 Definujte svoje metody zpětného volání ve třídě pásu karet v soubor kódu pásu karet. Metoda zpětného volání má několik požadavků:  
  
- Musí být deklarován jako veřejná.  
  
- Název musí odpovídat názvu metody zpětného volání, který jste přiřadili do ovládacího prvku v souboru XML pásu karet.  
  
- Podpis typu metody zpětného volání, která je k dispozici pro přidružený ovládací prvek pásu karet se musí shodovat jeho podpis.  
  
  Úplný seznam podpisy metod zpětného volání pro ovládací prvky pásu karet, najdete v článku technické [přizpůsobení uživatelského rozhraní pásu karet Office (2007) pro vývojáře (část 3 ze 3)](/previous-versions/office/developer/office-2007/aa722523(v=office.12)). Visual Studio neposkytuje podporu technologie IntelliSense pro metody zpětného volání, které vytvoříte v soubor kódu pásu karet. Pokud vytvoříte metody zpětného volání, která neodpovídá platný podpis, kompilací kódu, ale nic dojde, když uživatel klikne ovládací prvek.  
  
  Mají všechny metody zpětného volání <xref:Microsoft.Office.Core.IRibbonControl> parametr, který představuje ovládací prvek, který volá metodu. Tento parametr můžete znovu použít stejnou metodu zpětného volání pro více ovládacích prvků. Následující příklad kódu ukazuje **onAction** metody zpětného volání, která provádí různé úlohy v závislosti na tom, které ovládacího prvku uživatel klikne na tlačítko.  
  
  [!code-csharp[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#2)]
  [!code-vb[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#2)]  
  
##  <a name="RibbonDescriptorFile"></a> Odkaz na soubor XML pásu karet  
 Můžete definovat vaše vlastní pás karet tak, že přidání prvků a atributů do souboru XML pásu karet. Ve výchozím souboru XML pásu karet obsahuje následující kód XML.  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<customUI xmlns="http://schemas.microsoft.com/office/2006/01/customui" onLoad="OnLoad">  
  <ribbon>  
    <tabs>  
      <tab idMso="TabAddIns">  
        <group id="MyGroup"  
               label="My Group">  
        </group>  
      </tab>  
    </tabs>  
  </ribbon>  
</customUI>  
```  
  
 Následující tabulka popisuje prvky výchozí v souboru XML pásu karet.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|**customUI**|Představuje vlastní pás karet v projektu doplňku VSTO.|  
|**Pás karet**|Představuje na pásu karet.|  
|**Karty**|Představuje sadu pás karet.|  
|**Karta**|Představuje do jedné karty na pásu karet.|  
|**Skupiny**|Představuje skupinu ovládacích prvků na kartu pásu karet.|  
  
 Tyto prvky mají atributy, které určují vzhled a chování vlastní pás karet. Následující tabulka popisuje atributy výchozí v souboru XML pásu karet.  
  
|Atribut|Nadřazený element|Popis|  
|---------------|--------------------|-----------------|  
|**Při načtení**|**customUI**|Určuje metodu, která je volána při načtení aplikace pásu karet.|  
|**idMso**|**Karta**|Identifikuje předdefinované karty zobrazit na pásu karet.|  
|**id**|**Skupiny**|Tento parametr identifikuje skupinu.|  
|**Popisek**|**Skupiny**|Určuje text, který se zobrazí ve skupině.|  
  
 Výchozí prvky a atributy v souboru XML pásu karet jsou malou podmnožinu prvky a atributy, které jsou k dispozici. Úplný seznam dostupných prvky a atributy, naleznete v tématu technického článku [přizpůsobení uživatelského rozhraní pásu karet Office (2007) pro vývojáře (část 2 ze 3)](/previous-versions/office/developer/office-2007/aa338199(v=office.12)).  
  
##  <a name="RibbonExtensionClass"></a> Referenční třídy pásu karet  
 Visual Studio vygeneruje třídy pásu karet v soubor kódu pásu karet. Přidáte do této třídy, metody zpětného volání pro ovládací prvky na pásu karet. Tato třída implementuje <xref:Microsoft.Office.Core.IRibbonExtensibility> rozhraní.  
  
 Následující tabulka popisuje výchozí metody této třídy.  
  
|Metoda|Popis|  
|------------|-----------------|  
|`GetCustomUI`|Vrátí obsah souboru XML pásu karet. Aplikace Microsoft Office volat tuto metodu za účelem získání řetězec XML, který definuje uživatelské rozhraní vlastní pás karet. Tato metoda implementuje <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> metody. **Poznámka:** `GetCustomUI` by měla být implementována pouze pro vrácení obsahu souboru XML pásu karet; nesmí sloužit k inicializaci doplňku VSTO. Konkrétně se by se neměl pokoušet zobrazit dialogová okna nebo v jiných oknech vaše `GetCustomUI` implementace. Vlastní pás karet v opačném případě nemusí chovat správně. Pokud je třeba spustit kód, který inicializuje doplňku VSTO, přidejte kód, který `ThisAddIn_Startup` obslužné rutiny události.|  
|`OnLoad`|Přiřazuje <xref:Microsoft.Office.Core.IRibbonControl> parametr `Ribbon` pole. Aplikace Microsoft Office tuto metodu volat, když se načítají vlastní pás karet. Toto pole můžete použít a dynamicky aktualizovat vlastní pás karet. Další informace najdete v tématu technického článku [přizpůsobení uživatelského rozhraní pásu karet Office (2007) pro vývojáře (část 1 ze 3)](/previous-versions/office/developer/office-2007/aa338202(v=office.12)).|  
|`GetResourceText`|Volá `GetCustomUI` metoda získat obsah souboru XML pásu karet.|  
  
## <a name="see-also"></a>Viz také:  
 [Přehled pásu karet](../vsto/ribbon-overview.md)   
 [Návod: Vytvoření vlastní karty pomocí kódu XML pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)  
  
  