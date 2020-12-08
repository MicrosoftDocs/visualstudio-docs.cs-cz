---
title: Přizpůsobení pásu karet pro Outlook
description: Dozvíte se, že při přizpůsobení pásu karet v aplikaci systém Microsoft Office Outlook je nutné vzít v úvahu, kde se vlastní pás karet zobrazí v aplikaci.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], Ribbon
- customizing the Ribbon, about customizing the Ribbon
- custom Ribbon, about customizing the Ribbon
- Ribbon [Office development in Visual Studio], Outlook
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 25b4faa994a99bccdc2122ad6b9d124f7391e9f8
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848102"
---
# <a name="customize-a-ribbon-for-outlook"></a>Přizpůsobení pásu karet pro Outlook
  Při přizpůsobení pásu karet v aplikaci systém Microsoft Office Outlook je nutné vzít v úvahu, kde se vlastní pás karet zobrazí v aplikaci. Outlook zobrazí pás karet v hlavním uživatelském rozhraní aplikace (UI) a ve Windows, které se otevře, když uživatelé provedou určité úlohy, například vytváření e-mailových zpráv. Tato okna aplikací jsou pojmenována jako kontroloři.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>Přidání vlastního pásu karet do hlavního uživatelského rozhraní aplikace
 Hlavní uživatelské rozhraní aplikace v Outlooku se nazývá Průzkumník. Pokud používáte položku **pás karet (vizuální Návrhář)** , můžete do Průzkumníka přidat pás karet kliknutím na vlastnost **RibbonType** na pásu karet v okně **vlastnosti** a následným výběrem **Microsoft. Outlook. Explorer**.

## <a name="assign-a-ribbon-to-an-inspector"></a>Přiřazení pásu karet k kontrolorovi
 Určíte inspektora, který chcete přizpůsobit, zadáním typu pásu karet, který odpovídá třídě zpráv pro inspektora.

 Pokud používáte položku **pás karet (vizuální Návrhář)** , klikněte na vlastnost **RibbonType** pásu karet v okně **vlastnosti** a potom v seznamu hodnot vyberte jedno nebo více ID pásu karet.

 Do projektu můžete přidat více než jeden pás karet. Pokud ID pásu karet sdílí více než jeden pás karet, přepište `CreateRibbonExtensibilityObject` metodu ve `ThisAddin` třídě projektu, abyste určili, který pás karet se má zobrazit v době běhu. Další informace najdete v tématu [Přehled pásu karet](../vsto/ribbon-overview.md). Další informace o jednotlivých typech pásu karet najdete v technickém článku [přizpůsobení pásu karet v aplikaci Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Určení typu pásu karet pomocí kódu XML pásu karet
 Pokud používáte položku **pásu karet (XML)** , ověřte hodnotu parametru *RibbonId* v <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> metodě a vraťte příslušný pás karet.

 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A>Metoda je automaticky vygenerována v aplikaci Visual Studio v souboru kódu pásu karet. Parametr *RibbonId* je řetězec, který identifikuje Průzkumníka nebo konkrétní typ kontrolora. Úplný seznam možných hodnot parametru *RibbonId* najdete v technickém článku [přizpůsobení pásu karet v aplikaci Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).

 Následující příklad kódu ukazuje, jak zobrazit vlastní pás karet pouze v `Microsoft.Outlook.Mail.Compose` inspektoru. Toto je kontroler, který se otevře, když uživatel vytvoří novou e-mailovou zprávu. Pás karet, který se má zobrazit, je určen v `GetResourceText()` metodě, která je vygenerována ve třídě **pásu karet** . Další informace o třídě **pásu karet** naleznete v tématu [XML pásu karet](../vsto/ribbon-xml.md).

 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]

## <a name="see-also"></a>Viz také
- [Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)
- [Přehled pásu karet](../vsto/ribbon-overview.md)
- [Návrhář pásu karet](../vsto/ribbon-designer.md)
- [Pás karet – XML](../vsto/ribbon-xml.md)
