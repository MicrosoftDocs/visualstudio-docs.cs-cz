---
title: Přehled pásu karet
description: Naučte se, jak pás karet představuje způsob, jak uspořádat související příkazy, aby bylo snazší najít a jak se příkazy zobrazí na pásu karet jako ovládací prvky.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8920c8a402b4566cf95bb74626171cca833d32de
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825547"
---
# <a name="ribbon-overview"></a>Přehled pásu karet
  Pás karet je způsob, jak uspořádat související příkazy, aby bylo snazší je najít. Příkazy se zobrazí jako ovládací prvky na pásu karet. Ovládací prvky jsou uspořádány do *skupin* podél vodorovného pruhu v horním rohu okna aplikace. Související skupiny jsou uspořádány na kartách.

 Většina funkcí, k nimž došlo pomocí nabídek a panelů nástrojů v předchozích verzích systém Microsoft Office systému, teď může být dostupná pomocí pásu karet. Další informace najdete v technickém článku [Přehled pro vývojáře uživatelského rozhraní pro systém 2007 systém Microsoft Office](/previous-versions/office/developer/office-2007/aa338198(v=office.12)).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="customize-the-microsoft-office-ribbon"></a>Přizpůsobení systém Microsoft Officeového pásu karet
 Pokud chcete pás karet přizpůsobit, přidejte do projektu Office jednu z následujících položek pásu karet:

- **Pás karet (vizuální Návrhář)**

- **Pás karet (XML)**

  Například pro přizpůsobení pásu karet aplikace Excel přidejte položku pásu karet do projektu doplňku aplikace Excel VSTO.

### <a name="ribbon-visual-designer-item"></a>Položka pásu karet (vizuální Návrhář)
 Položka **pás karet (vizuální Návrhář)** poskytuje pokročilé nástroje, které usnadňují návrh a vývoj vlastního pásu karet. Použijte položku **pás karet (vizuální Návrhář)** k přizpůsobení pásu karet následujícími způsoby:

- Přidejte vlastní nebo vestavěné karty na pás karet.

- Přidejte vlastní skupiny na vlastní nebo integrovanou kartu.

  > [!NOTE]
  > Integrovaná karta nebo skupina je taková, která již existuje na pásu karet aplikace systém Microsoft Office. Karta **data** je například Integrovaná karta v aplikaci Excel. Skupina **připojení** je vestavěnou skupinou na kartě **data** .

- Přidejte vlastní ovládací prvky do vlastní skupiny.

- Přidejte vlastní ovládací prvky do zobrazení Backstage.

  Další informace o tom, jak přizpůsobit pás karet pomocí položky **pás karet (vizuální Návrhář)** , najdete v tématu [Návrhář pásu karet](../vsto/ribbon-designer.md).

### <a name="ribbon-xml-item"></a>Položka pásu karet (XML)
 Použijte položku **pásu karet (XML)** , chcete-li přizpůsobit pás karet způsobem, který není podporován položkou **pásu karet (vizuální Návrhář)** . Použijte položku **pásu karet (XML)** k přizpůsobení pásu karet následujícími způsoby:

- Přidejte *předdefinované* skupiny na vlastní kartu nebo na integrovanou kartu.

- Přidejte předdefinované ovládací prvky do vlastní skupiny.

- Přidejte vlastní kód pro přepsání obslužných rutin událostí integrovaných ovládacích prvků.

- Přizpůsobení panelu nástrojů Rychlý přístup.

- Sdílejte přizpůsobení pásu karet mezi doplňkem VSTO pomocí kvalifikovaného ID.

  Další informace o tom, jak přizpůsobit pás karet pomocí položky **pásu karet (XML)** , naleznete v tématu [XML pásu karet](../vsto/ribbon-xml.md).

## <a name="export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Export pásu karet z Návrháře pásu karet do XML pásu karet
 Pokud vytvoříte pás karet pomocí Návrháře pásu karet a následně se rozhodnete, že chcete pás karet přizpůsobit způsobem, který položku **pásu karet (vizuální Návrhář)** nepodporuje, můžete vyexportovat pás karet do formátu XML.

 Visual Studio automaticky vytvoří položku **pásu karet (XML)** a naplní soubor XML pásu karet elementy a atributy pro každý ovládací prvek na pásu karet.

 Ne všechny vlastnosti, které jsou v okně **vlastnosti** Návrháře pásu karet, jsou přeneseny do souboru XML pásu karet.  Například Visual Studio neexportuje hodnotu vlastnosti **Obrázek** nebo **text** . Důvodem je, že je nutné vytvořit metodu zpětného volání v souboru kódu pásu karet exportovaného projektu pro přiřazení obrázku nebo nastavení textu ovládacího prvku. Visual Studio negeneruje metody zpětného volání automaticky jako součást procesu exportu.

 Kromě toho se ve výsledném souboru XML pásu karet nezobrazí všechny nezměněné výchozí hodnoty vlastností.

 Další informace o exportu pásu karet do XML najdete v tématu [How to: Export pásu karet z Návrháře pásu karet do XML pásu karet](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).

### <a name="update-the-code"></a>Aktualizace kódu
 Do **Průzkumník řešení** se přidá nový soubor kódu pásu karet. Tento soubor obsahuje třídu XML pásu karet. `Ribbon Callbacks`Pro zpracování akcí uživatele, jako je například kliknutí na tlačítko, je nutné v oblasti této třídy vytvořit metody zpětného volání. Přesuňte kód z obslužných rutin událostí do těchto metod zpětného volání a upravte kód tak, aby fungoval s programovacím modelem rozšíření pásu karet (Ribbon Extensibility). Další informace najdete v tématu [XML pásu karet](../vsto/ribbon-xml.md).

 Musíte také přidat kód do `ThisAddIn` `ThisWorkbook` třídy, nebo, `ThisDocument` která přepisuje `CreateRibbonExtensibilityObject` metodu a vrátí třídu XML pásu karet do aplikace sady Office.

 Další informace najdete v tématu [XML pásu karet](../vsto/ribbon-xml.md).

## <a name="add-multiple-ribbon-items-to-a-project"></a>Přidání více položek pásu karet do projektu
 Do jednoho projektu můžete přidat více než jednu položku pásu karet. To je užitečné v případě, že chcete provést jednu z následujících dvou úloh:

- Vytvořte pás karet pro *kontroly* aplikace Outlook. Další informace najdete v tématu [přizpůsobení pásu karet pro Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

    > [!NOTE]
    > Inspektor je okno, které se otevře, když uživatelé provedou určité úlohy, například vytvoření e-mailové zprávy.

- Vyberte, který pás karet se má zobrazit v době běhu.

### <a name="select-which-ribbons-to-display-at-run-time"></a>Vybrat, které pásy se mají zobrazit v době běhu
 Vzhledem k tomu, že projekt může obsahovat více než jeden pás karet, můžete vybrat, který pás karet se má zobrazit v době běhu.

 Chcete-li vybrat pás karet, který má být zobrazen v době běhu, přepište `CreateRibbonExtensibilityObject` metodu ve `ThisAddin` `ThisWorkbook` třídě, nebo v `ThisDocument` projektu a vraťte pás karet, který chcete zobrazit. Následující příklad zkontroluje hodnotu pole s názvem `myCondition` a vrátí příslušný pás karet.

> [!NOTE]
> Syntaxe použitá v tomto příkladu vrací pás karet, který byl vytvořen pomocí položky **pásu karet (vizuální Návrhář)** . Syntaxe pro vrácení pásu karet, která je vytvořena pomocí položky **pásu karet (XML)** , je mírně odlišná. Další informace o vracení položky **pásu karet (XML)** najdete v tématu [XML pásu karet](../vsto/ribbon-xml.md).

 Přidejte následující kód:

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.cs" id="Snippet1":::

### <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md)|Ukazuje, jak přizpůsobit pás karet aplikace systém Microsoft Office, přidat **pás karet (vizuální Návrhář)** nebo položku **pásu karet (XML)** do projektu sady Office.|
|[Návrhář pásu karet](../vsto/ribbon-designer.md)|Popisuje, jak můžete pomocí Návrháře pásu karet přidat vlastní karty, skupiny a ovládací prvky na pás karet aplikace systém Microsoft Office.|
|[Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Ukazuje, jak vytvořit vlastní kartu pásu karet pomocí Návrháře pásu karet. Pomocí Návrháře pásu karet můžete přidat a umístit ovládací prvky na vlastní kartě.|
|[Přehled modelu objektů pásu karet](../vsto/ribbon-object-model-overview.md)|Poskytuje přehled modelu objektu silného typu, který můžete použít k získání a nastavení vlastností ovládacích prvků pásu karet v době běhu.|
|[Návod: aktualizace ovládacích prvků na pásu karet v době běhu](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Ukazuje, jak použít objektový model pásu karet k aktualizaci ovládacích prvků na pásu karet po načtení pásu karet do aplikace sady Office.|
|[Přizpůsobení pásu karet pro Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Poskytuje pokyny pro přizpůsobení pásu karet v aplikaci systém Microsoft Office Outlook.|
|[Přizpůsobení pásu karet pro aplikaci InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|Poskytuje pokyny pro přizpůsobení pásu karet v aplikaci systém Microsoft Office InfoPath.|
|[Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)|Ukazuje, jak zobrazit, skrýt a upravit pás karet a povolit uživatelům spouštění kódu z ovládacích prvků ve vlastním podokně úloh, podokně akce nebo oblasti formuláře aplikace Outlook.|
|[Postupy: Změna pozice karty na pásu karet](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Ukazuje, jak změnit pořadí karet na pásu karet.|
|[Postupy: Přizpůsobení předdefinované karty](../vsto/how-to-customize-a-built-in-tab.md)|Ukazuje, jak přidat skupiny a ovládací prvky na vestavěnou kartu.|
|[Postupy: Přidání ovládacích prvků do zobrazení Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)|Ukazuje, jak přidat ovládací prvky do nabídky, která se otevře po kliknutí na **soubor**.|
|[Postupy: Přidání spouštěče dialogového okna do skupiny pásu karet](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Ukazuje, jak přidat spouštěč dialogového okna do libovolné skupiny na pásu karet.|
|[Postupy: Export pásu karet z Návrháře pásu karet do XML pásu karet](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Ukazuje, jak lze pás karet upravit pomocí možnosti Exportovat pás karet z návrháře na pás XML pásu karet.|
|[Pás karet – XML](../vsto/ribbon-xml.md)|Vysvětluje, jak lze pás karet přizpůsobit pomocí pásu karet XML.|
|[Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Ukazuje, jak vytvořit vlastní kartu pásu karet pomocí položky **pásu karet (XML)** .|
