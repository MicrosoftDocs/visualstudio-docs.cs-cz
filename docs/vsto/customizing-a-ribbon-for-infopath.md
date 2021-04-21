---
title: Přizpůsobení pásu karet pro aplikaci InfoPath
description: Dozvíte se, že při přizpůsobení pásu karet v aplikaci systém Microsoft Office InfoPath je nutné vzít v úvahu, kde se vlastní pás karet zobrazí v aplikaci.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- InfoPath [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], InfoPath
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5af7c4ed2f396c5a806cc42c49c8f4209b6b5c2c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828134"
---
# <a name="customize-a-ribbon-for-infopath"></a>Přizpůsobení pásu karet pro aplikaci InfoPath
  Při přizpůsobení pásu karet v aplikaci systém Microsoft Office InfoPath je nutné vzít v úvahu, kde se vlastní pás karet zobrazí v aplikaci. [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] může zobrazit pás karet v následujících třech typech oken aplikace InfoPath:

- Systém Windows, který zobrazuje šablonu formuláře, která je otevřena v režimu návrhu.

- Systém Windows, který zobrazuje formulář založený na šabloně formuláře.

- Okno náhledu tisku.

  **Platí pro:** Informace v tomto tématu se vztahují na projekty doplňku VSTO v InfoPathu 2010. Další informace najdete v tématu [dostupné funkce podle aplikace systému Office a typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

  Uživatelé a návrháři otevřou šablonu formuláře v návrhovém režimu pro úpravu vzhledu a rozložení šablony. Uživatelé otevřou formuláře, které jsou založeny na šabloně formuláře pro přidání obsahu.

  Okno Náhled tisku umožňuje návrhářům a uživatelům zobrazit náhled stránek formuláře nebo šablony formuláře před jejich tiskem.

> [!NOTE]
> Karta **Doplňky** se nezobrazí v okně náhledu tisku. Pokud chcete, aby se v okně náhledu tisku zobrazovala vlastní karta, ujistěte se, že vlastnost **OfficeId** karty není nastavená na **TabAddIns**.

 Je nutné zadat typ pásu karet pro každé okno, ve kterém se má pás karet zobrazit.

## <a name="specify-the-ribbon-type-in-the-ribbon-designer"></a>Určení typu pásu karet v Návrháři pásu karet
 Pokud používáte položku **pás karet (vizuální Návrhář)** , klikněte na vlastnost **RibbonType** pásu karet v okně **vlastnosti** a pak vyberte libovolné ID pásu karet popsané v následující tabulce.

|ID pásu karet|Okno, ve kterém se zobrazí pás karet při spuštění projektu|
|---------------|---------------------------------------------------------------------|
|**Microsoft. InfoPath. Designer**|Systém Windows, který zobrazuje šablonu formuláře, která je otevřena v režimu návrhu.|
|**Microsoft. InfoPath. Editor**|Systém Windows, který zobrazuje formulář založený na šabloně formuláře.|
|**Microsoft. InfoPath. PrintPreview**|Okno náhledu tisku.|

 Do projektu můžete přidat více než jeden pás karet. Pokud má více než jeden pás sdílení ID pásu karet, přepište `CreateRibbonExtensibilityObject` metodu ve `ThisAddin` třídě projektu, abyste určili, který pás karet se má zobrazit v době běhu. Další informace najdete v tématu [Přehled pásu karet](../vsto/ribbon-overview.md).

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Určení typu pásu karet pomocí kódu XML pásu karet
 Pokud používáte položku **pásu karet (XML)** , ověřte hodnotu parametru *RibbonId* v <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> metodě a vraťte příslušný pás karet.

 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A>Metoda je automaticky vygenerována v aplikaci Visual Studio v souboru kódu pásu karet. Parametr *RibbonId* je řetězec, který určuje typ okna aplikace InfoPath, které se otevírá.

 Následující příklad kódu ukazuje, jak zobrazit vlastní pás karet pouze v okně, které v návrhovém režimu zobrazuje šablonu formuláře. Pás karet, který se má zobrazit, je určen v `GetResourceText()` metodě, která je vygenerována ve třídě pásu karet. Další informace o třídě pásu karet naleznete v tématu [XML pásu karet](../vsto/ribbon-xml.md).

 :::code language="csharp" source="../vsto/codesnippet/CSharp/myinfopathproject/ribbon.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/myinfopathproject/ribbon.vb" id="Snippet1":::

## <a name="see-also"></a>Viz také
- [Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)
- [Přehled pásu karet](../vsto/ribbon-overview.md)
- [Návrhář pásu karet](../vsto/ribbon-designer.md)
- [Pás karet – XML](../vsto/ribbon-xml.md)
