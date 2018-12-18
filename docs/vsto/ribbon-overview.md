---
title: Přehled pásu karet
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, multiple Ribbons
- Ribbon [Office development in Visual Studio], about Ribbon
- toolbars [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], multiple Ribbons
- toolbars [Office development in Visual Studio]
- custom Ribbon, multiple Ribbons
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 51de8b5fbc4e21b4dabaf34f526b85f0b98623db
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846355"
---
# <a name="ribbon-overview"></a>Přehled pásu karet
  Na pásu karet je způsob, jak uspořádat příkazy související tak, aby byly snadněji najít. Příkazy se zobrazují jako ovládací prvky na pásu karet. Ovládací prvky jsou uspořádány do *skupiny* podél horizontální pruh v horním okrajem jeho okna aplikace. Související skupiny jsou uspořádány na kartách.  
  
 Většina funkcí, které byly přístupné prostřednictvím nabídek a panelů nástrojů v dřívějších verzích systému Microsoft Office je teď přístupný pomocí pásu karet. Další informace najdete v tématu technického článku [– přehled pro vývojáře uživatelského rozhraní pro systém Microsoft Office 2007](http://go.microsoft.com/fwlink/?LinkID=70860).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="customize-the-microsoft-office-ribbon"></a>Přizpůsobení pásu karet aplikace Microsoft Office  
 Přizpůsobení pásu karet, přidejte jeden z následujících položek pásu karet do projektu Office:  
  
- **Pás karet (vizuální návrhář)**  
  
- **Pás karet (XML)**  
  
  K přizpůsobení pásu karet Excelu, například přidání položky pásu karet do projektu doplňku VSTO pro Excel.  
  
### <a name="ribbon-visual-designer-item"></a>Položky pásu karet (vizuální návrhář)  
 **Pás karet (vizuální návrhář)** položky poskytuje pokročilé nástroje, které usnadňují navrhovat a vyvíjet vlastní pás karet. Použití **pás karet (vizuální návrhář)** položky k přizpůsobení pásu karet následujícími způsoby:  
  
- Přidání vlastních nebo předdefinovaných karet na pás karet.  
  
- Přidáte vlastní skupiny na vlastní nebo integrovanou kartu.  
  
  > [!NOTE]  
  >  Předdefinované karty nebo skupina je ten, který je už na pásu karet aplikace Microsoft Office. Například **Data** karta je integrovanou kartou v aplikaci Excel. **Připojení** skupina je předdefinovaná skupina na **Data** kartu.  
  
- Přidání vlastních ovládacích prvků do vlastní skupiny.  
  
- Přidání vlastních ovládacích prvků do zobrazení Backstage.  
  
  Další informace o tom, jak přizpůsobit pás karet pomocí **pás karet (vizuální návrhář)** položky, naleznete v tématu [Návrháře pásu karet](../vsto/ribbon-designer.md).  
  
### <a name="ribbon-xml-item"></a>Položky pásu karet (XML)  
 Použití **pásu karet (XML)** položku, pokud chcete přizpůsobit pás karet způsobem, který není podporován **pás karet (vizuální návrhář)** položky. Použití **pásu karet (XML)** položky k přizpůsobení pásu karet následujícími způsoby:  
  
- Přidat *integrované* skupiny na vlastní kartu nebo předdefinované karty.  
  
- Přidání integrovaných ovládacích prvků do vlastní skupiny.  
  
- Přidání vlastního kódu k přepsání obslužných rutin událostí z integrovaných ovládacích prvků.  
  
- Přizpůsobení panelu nástrojů Rychlý přístup.  
  
- Sdílení vlastního nastavení pásu karet mezi doplňku VSTO pomocí kvalifikovaného ID.  
  
  Další informace o tom, jak přizpůsobit pás karet pomocí **pásu karet (XML)** položky, naleznete v tématu [kódu XML pásu karet](../vsto/ribbon-xml.md).  
  
## <a name="export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Export pásu karet z Návrháře pásu karet do kódu XML pásu karet  
 Pokud vytvoříte pásu karet pomocí Návrháře pásu karet a následně se rozhodnete, že chcete přizpůsobit pás karet způsoby, které **pás karet (vizuální návrhář)** položka nepodporuje, můžete exportovat na pásu karet do XML.  
  
 Visual Studio automaticky vytvoří **pásu karet (XML)** položky a naplní souboru XML pásu karet s prvky a atributy pro každý ovládací prvek na pásu karet.  
  
 Ne všechny vlastnosti, které jsou v **vlastnosti** okna Návrháře pásu karet jsou přeneseny do souboru XML pásu karet.  Například Visual Studio neexportuje hodnotu **Image** nebo **Text** vlastnost. Důvodem je, je nutné vytvořit metodu zpětného volání v soubor kódu pásu karet exportovaném projektu přiřazení bitovou kopii nebo nastavte vlastnost text ovládacího prvku. Visual Studio automaticky negeneruje metody zpětného volání jako součást procesu exportu.  
  
 Kromě toho všechny nezměněné výchozí hodnoty vlastností se nezobrazují ve výsledném souboru XML pásu karet.  
  
 Další informace o tom, jak exportovat na pásu karet do XML, naleznete v tématu [postupy: Export pásu karet z Návrháře pásu karet do kódu XML pásu karet](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).  
  
### <a name="update-the-code"></a>Aktualizace kódu  
 Přidá nový soubor kódu pásu karet do **Průzkumníka řešení**. Tento soubor obsahuje třídu kódu XML pásu karet. Je nutné vytvořit metody zpětného volání ve `Ribbon Callbacks` oblasti této třídy pro zpracování uživatelské akce, jako je kliknutí na tlačítko. Přesuňte váš kód z obslužných rutin událostí těchto metod zpětného volání a upravte kód pro práci s pásu karet ribbonx (Ribbon extensibility) programovacího modelu. Další informace najdete v tématu [kódu XML pásu karet](../vsto/ribbon-xml.md).  
  
 Musíte taky přidat kód, který `ThisAddIn`, `ThisWorkbook`, nebo `ThisDocument` třídu, která přepíše `CreateRibbonExtensibilityObject` třídu metodu a vrátí kódu XML pásu karet aplikace sady Office.  
  
 Další informace najdete v tématu [kódu XML pásu karet](../vsto/ribbon-xml.md).  
  
## <a name="add-multiple-ribbon-items-to-a-project"></a>Přidání více položek pásu karet do projektu  
 Můžete přidat více než jednu položku pásu karet do jednoho projektu. To je užitečné, pokud chcete provést jednu z následujících akcí:  
  
-   Vytváření pásů karet pro aplikaci Outlook *kontroly*. Další informace najdete v tématu [přizpůsobte pás karet pro aplikaci Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
    > [!NOTE]  
    >  Je kontrola je okno, které se otevře, když uživatelé provedou určité úlohy, jako je například vytváření e-mailové zprávy.  
  
-   Vyberte, které pásu karet za běhu zobrazit.  
  
### <a name="select-which-ribbons-to-display-at-runtime"></a>Vyberte které pásů karet zobrazíte za běhu  
 Vzhledem k tomu, že projekt může obsahovat více než jeden pásu karet, můžete vybrat, které pásu karet za běhu zobrazit.  
  
 Vyberte pás karet zobrazíte za běhu přepsat `CreateRibbonExtensibilityObject` metoda ve `ThisAddin`, `ThisWorkbook`, nebo `ThisDocument` třídu vašeho projektu a vraťte se na pásu karet, který chcete zobrazit. Následující příklad zkontroluje hodnotu vlastnosti pole s názvem `myCondition` a vrátí odpovídající pásu karet.  
  
> [!NOTE]  
>  Syntaxe používané v tomto příkladu vrátí pás karet, který byl vytvořen pomocí **pás karet (vizuální návrhář)** položky. Syntaxe pro vrácení pásu karet, který je vytvořen pomocí **pásu karet (XML)** položky se mírně liší. Další informace o vrácení **pásu karet (XML)** položky, naleznete v tématu [kódu XML pásu karet](../vsto/ribbon-xml.md).  
  
 Přidejte následující kód:  
  
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.cs#1)]  
  
### <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md)|Ukazuje, jak přizpůsobit pás karet aplikace Microsoft Office, přidejte **pás karet (vizuální návrhář)** nebo **pásu karet (XML)** položky projektu sady Office.|  
|[Návrhář pásu karet](../vsto/ribbon-designer.md)|Popisuje, jak můžete pomocí Návrháře pásu karet přidat vlastní karty, skupiny a ovládací prvky na pásu karet aplikace Microsoft Office.|  
|[Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Ukazuje, jak vytvořit vlastní kartu pásu karet pomocí Návrháře pásu karet. Návrhář pásu karet můžete přidat a umístit ovládací prvky na vlastní kartě.|  
|[Přehled modelu objektů pásu karet](../vsto/ribbon-object-model-overview.md)|Poskytuje přehled o model silně typovaných objektů, které můžete použít k získání a nastavení vlastností ovládacích prvků pásu karet za běhu.|  
|[Návod: Aktualizace ovládacích prvků na pásu karet za běhu](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Ukazuje, jak použít model objektu pásu karet po načtení pásu do aplikace sady Office aktualizace ovládacích prvků na pásu karet.|  
|[Přizpůsobte pás karet pro aplikaci Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Obsahuje pokyny k přizpůsobení pásu karet v aplikaci Microsoft Office Outlook.|  
|[Přizpůsobte pás karet pro aplikaci InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|Obsahuje pokyny k přizpůsobení pásu karet v aplikaci Microsoft Office InfoPath.|  
|[Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)|Ukazuje, jak zobrazit, skrýt a změnám pásu karet a povolit uživatelům spustit kód z ovládacích prvků v vlastního podokna úloh, podokna akcí nebo oblasti formuláře aplikace Outlook.|  
|[Postupy: Změna pozice karty na pásu karet](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Ukazuje, jak chcete-li změnit pořadí karet na pásu karet.|  
|[Postupy: Přizpůsobení předdefinované karty](../vsto/how-to-customize-a-built-in-tab.md)|Ukazuje, jak přidat skupiny a ovládací prvky k předdefinované kartě.|  
|[Postupy: Přidání ovládacích prvků do zobrazení Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)|Ukazuje, jak přidat ovládací prvky do nabídky, které se otevře po kliknutí **souboru**.|  
|[Postupy: Přidání Spouštěče dialogového okna do skupiny pásu karet](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Ukazuje přidání Spouštěče dialogového okna pro libovolnou skupinu na pásu karet.|  
|[Postupy: Export pásu karet z Návrháře pásu karet do kódu XML pásu karet](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Ukazuje, jak přizpůsobit pás karet Upřesnit způsoby tak, že vyexportujete na pásu karet do kódu XML pásu karet z návrháře.|  
|[Pás karet – XML](../vsto/ribbon-xml.md)|Vysvětluje, jak můžete přizpůsobit pás karet pomocí kódu XML pásu karet.|  
|[Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Ukazuje, jak vytvořit vlastní kartu pásu karet pomocí **pásu karet (XML)** položky.|  
  
  