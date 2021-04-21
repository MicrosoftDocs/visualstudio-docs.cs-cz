---
title: Pás karet – XML
description: Naučte se používat položku pásu karet (XML), chcete-li přizpůsobit pás karet způsobem, který není podporován položkou pásu karet (vizuálního návrháře).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a84a0c21bba42263e7b4dad9ad9118f462389ad6
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827497"
---
# <a name="ribbon-xml"></a>Pás karet – XML
  Položka pásu karet (XML) umožňuje přizpůsobit pás karet pomocí XML. Použijte položku pásu karet (XML), chcete-li přizpůsobit pás karet způsobem, který není podporován položkou pásu karet (vizuální Návrhář). Porovnání toho, co můžete s každou položkou dělat, najdete v tématu [Přehled pásu karet](../vsto/Ribbon-overview.md).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="add-a-ribbon-xml-item-to-a-project"></a>Přidat položku pásu karet (XML) do projektu
 Můžete přidat položku **pásu karet (XML)** do libovolného projektu sady Office v dialogovém okně **Přidat novou položku** . Visual Studio automaticky přidá do projektu následující soubory:

- Soubor XML pásu karet. Tento soubor definuje uživatelské rozhraní pásu karet (UI). Pomocí tohoto souboru můžete přidat prvky uživatelského rozhraní, jako jsou tabulátory, skupiny a ovládací prvky. Podrobnosti najdete v části [referenční informace k souboru XML pásu karet](#RibbonDescriptorFile) dále v tomto tématu.

- Soubor kódu pásu karet. Tento soubor obsahuje *třídu pásu karet*. Tato třída má název, který jste zadali pro položku **pásu karet (XML)** v dialogovém okně **Přidat novou položku** . Systém Microsoft Office aplikace pro načtení vlastního pásu karet používají instanci této třídy. Podrobnosti najdete v tématu [Přehled třídy pásu karet](#RibbonExtensionClass) dále v tomto tématu.

  Ve výchozím nastavení tyto soubory přidají vlastní skupinu na kartu **Doplňky** na pásu karet.

## <a name="display-the-custom-ribbon-in-a-microsoft-office-application"></a>Zobrazení vlastního pásu karet v aplikaci systém Microsoft Office
 Po přidání položky **pásu karet (XML)** do projektu je nutné přidat kód do třídy **ThisAddIn**, **ThisWorkbook** nebo **ThisDocument** , která přepíše `CreateRibbonExtensibilityObject` metodu a vrátí třídu XML pásu karet do aplikace sady Office.

 Následující příklad kódu přepíše `CreateRibbonExtensibilityObject` metodu a vrátí třídu XML pásu karet s názvem MyRibbon.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb" id="Snippet1":::

## <a name="define-the-behavior-of-the-custom-ribbon"></a>Definování chování vlastního pásu karet
 Můžete reagovat na akce uživatele, jako je například kliknutí na tlačítko na pásu karet, vytvořením *metod zpětného volání*. Metody zpětného volání připomínají události v ovládacích prvcích model Windows Forms, ale jsou označeny atributem v XML prvku uživatelského rozhraní. Metody zapisujete do třídy pásu karet a ovládací prvek volá metodu, která má stejný název jako hodnota atributu. Můžete například vytvořit metodu zpětného volání, která je volána, když uživatel klikne na tlačítko na pásu karet. K vytvoření metody zpětného volání se vyžadují dva kroky:

- Přiřaďte atribut ovládacímu prvku v souboru XML pásu karet, který identifikuje metodu zpětného volání ve vašem kódu.

- Definujte metodu zpětného volání ve třídě pásu karet.

> [!NOTE]
> Outlook vyžaduje další krok. Další informace najdete v tématu [přizpůsobení pásu karet pro Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

 Návod, který ukazuje, jak automatizovat aplikaci z pásu karet, naleznete v tématu [Návod: Vytvoření vlastní karty pomocí kódu XML pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md).

### <a name="assign-callback-methods-to-controls"></a>Přiřazení metod zpětného volání ovládacím prvkům
 Chcete-li přiřadit metodu zpětného volání ovládacímu prvku v souboru XML pásu karet, přidejte atribut, který určuje typ metody zpětného volání a název metody. Například následující prvek definuje přepínací tlačítko, které má metodu zpětného volání při **akci** s názvem `OnToggleButton1` .

```xml
<toggleButton id="toggleButton1" onAction="OnToggleButton1" />
```

 **Akce** je volána, když uživatel provede hlavní úlohu přidruženou ke konkrétnímu ovládacímu prvku. Například **metoda zpětného** volání "přepínacího tlačítka" je volána, když uživatel klikne na tlačítko.

 Metoda, kterou zadáte v atributu, může mít libovolný název. Musí se ale shodovat s názvem metody, kterou definujete v souboru kódu pásu karet.

 Existuje mnoho různých typů metod zpětného volání, které lze přiřadit ovládacím prvkům pásu karet. Úplný seznam metod zpětného volání dostupných pro každý ovládací prvek najdete v technickém článku [přizpůsobení uživatelského rozhraní pásu karet Office (2007) pro vývojáře (část 3 ze 3)](/previous-versions/office/developer/office-2007/aa722523(v=office.12)).

### <a name="define-callback-methods"></a><a name="CallBackMethods"></a> Definování metod zpětného volání
 Ve třídě pásu karet v souboru kódu pásu karet definujte metody zpětného volání. Metoda zpětného volání má několik požadavků:

- Musí být deklarován jako Public.

- Jeho název musí odpovídat názvu metody zpětného volání, která byla přiřazena ovládacímu prvku v souboru XML pásu karet.

- Jeho signatura se musí shodovat s podpisem typu metody zpětného volání, která je k dispozici pro přidružený ovládací prvek pásu karet.

  Úplný seznam signatur metod zpětného volání pro ovládací prvky pásu karet najdete v technickém článku [přizpůsobení uživatelského rozhraní pásu karet Office (2007) pro vývojáře (část 3 ze 3)](/previous-versions/office/developer/office-2007/aa722523(v=office.12)). Visual Studio neposkytuje podporu technologie IntelliSense pro metody zpětného volání, kterou vytvoříte v souboru kódu pásu karet. Pokud vytvoříte metodu zpětného volání, která se neshoduje s platným podpisem, kód bude zkompilován, ale pokud uživatel klikne na ovládací prvek, nebude provedena žádná akce.

  Všechny metody zpětného volání mají <xref:Microsoft.Office.Core.IRibbonControl> parametr, který představuje ovládací prvek, který volal metodu. Pomocí tohoto parametru lze znovu použít stejnou metodu zpětného volání pro více ovládacích prvků. Následující příklad kódu ukazuje metodu zpětného volání **Akce** , která provádí různé úkoly v závislosti na tom, který ovládací prvek uživatel klikne.

  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs" id="Snippet2":::
  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb" id="Snippet2":::

## <a name="ribbon-xml-file-reference"></a><a name="RibbonDescriptorFile"></a> Odkaz na soubor XML pásu karet
 Vlastní pás karet můžete definovat přidáním prvků a atributů do souboru XML pásu karet. Ve výchozím nastavení obsahuje soubor XML pásu karet následující kód XML.

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

 Následující tabulka popisuje výchozí prvky v souboru XML pásu karet.

|Element|Popis|
|-------------|-----------------|
|**customUI**|Představuje vlastní pás karet v projektu doplňku VSTO.|
|**pásem**|Představuje pás karet.|
|**listy**|Představuje sadu karet pásu karet.|
|**rážky**|Představuje jednu kartu pásu karet.|
|**skupina**|Představuje skupinu ovládacích prvků na kartě pásu karet.|

 Tyto prvky mají atributy, které určují vzhled a chování vlastního pásu karet. Následující tabulka popisuje výchozí atributy v souboru XML pásu karet.

|Atribut|Nadřazený element|Description|
|---------------|--------------------|-----------------|
|**onLoad**|**customUI**|Identifikuje metodu, která je volána, když aplikace načte pás karet.|
|**idMso**|**rážky**|Určuje vestavěnou kartu, která se zobrazí na pásu karet.|
|**id**|**skupina**|Identifikuje skupinu.|
|**popisek**|**skupina**|Určuje text, který se zobrazí ve skupině.|

 Výchozí elementy a atributy v souboru XML pásu karet jsou malou podmnožinou prvků a atributů, které jsou k dispozici. Úplný seznam dostupných prvků a atributů najdete v technickém článku [přizpůsobení uživatelského rozhraní pásu karet Office (2007) pro vývojáře (část 2 ze 3)](/previous-versions/office/developer/office-2007/aa338199(v=office.12)).

## <a name="ribbon-class-reference"></a><a name="RibbonExtensionClass"></a> Odkaz na třídu pásu karet
 Visual Studio vygeneruje třídu pásu karet v souboru kódu pásu karet. Do této třídy přidejte metody zpětného volání ovládacích prvků na pásu karet. Tato třída implementuje <xref:Microsoft.Office.Core.IRibbonExtensibility> rozhraní.

 Následující tabulka popisuje výchozí metody v této třídě.

|Metoda|Popis|
|------------|-----------------|
|`GetCustomUI`|Vrátí obsah souboru XML pásu karet. Systém Microsoft Office aplikace volají tuto metodu pro získání řetězce XML, který definuje uživatelské rozhraní vašeho vlastního pásu karet. Tato metoda implementuje <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> metodu. **Poznámka:** `GetCustomUI` by měla být implementována pouze pro vrácení obsahu souboru XML pásu karet; neměl by se používat k inicializaci doplňku VSTO.   Zejména se nepokoušíte zobrazit dialogová okna nebo jiná okna v `GetCustomUI` implementaci. V opačném případě se vlastní pás karet nemusí správně chovat. Pokud potřebujete spustit kód, který inicializuje doplněk VSTO, přidejte kód do `ThisAddIn_Startup` obslužné rutiny události.|
|`OnLoad`|Přiřadí <xref:Microsoft.Office.Core.IRibbonControl> parametr k `Ribbon` poli. Systém Microsoft Office aplikace volají tuto metodu při načítání vlastního pásu karet. Toto pole můžete použít k dynamické aktualizaci vlastního pásu karet. Další informace najdete v technickém článku [přizpůsobení uživatelského rozhraní pásu karet Office (2007) pro vývojáře (část 1 ze 3)](/previous-versions/office/developer/office-2007/aa338202(v=office.12)).|
|`GetResourceText`|Volá se `GetCustomUI` metodou pro získání obsahu souboru XML pásu karet.|

## <a name="see-also"></a>Viz také
- [Přehled pásu karet](../vsto/ribbon-overview.md)
- [Návod: Vytvoření vlastní karty pomocí kódu XML pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)
