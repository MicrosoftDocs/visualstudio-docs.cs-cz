---
title: Použití starších Návrhář postupu provádění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c09c4588bb1fcd0aa7487a6896d2fc286253e198
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606774"
---
# <a name="using-the-legacy-workflow-designer"></a>Používání starší verze návrháře postupu provádění
Starší verze [!INCLUDE[wfd2](../includes/wfd2-md.md)] poskytované pomocí [!INCLUDE[vs2010](../includes/vs2010-md.md)] lze použít k cílení na [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 K němu se dostanete tak, že v rozevíracím seznamu v horní části okna **Nový projekt** vyberete buď možnost **.NET Framework 3,0** , nebo možnost **.NET Framework 3,5** . Výchozí možnost v [!INCLUDE[vs2010](../includes/vs2010-md.md)] je **.NET Framework 4** , která se používá k vytváření [!INCLUDE[wf](../includes/wf-md.md)] aplikací, které cílí na [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)].

 @No__t_0 poskytuje způsob, jak vytvořit [!INCLUDE[wf](../includes/wf-md.md)] aplikace pomocí známých [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uživatelského rozhraní. [!INCLUDE[wf](../includes/wf-md.md)] aplikace se skládají z kroků procesu pracovního postupu nazývaných aktivity. Chcete-li vytvořit pracovní postup, sestavte aktivity na návrhové ploše přetažením jejich příslušných návrhářů aktivit ze **sady nástrojů** na návrhovou plochu.

 V následující tabulce jsou uvedeny klíčové funkce [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pro programovací model Windows Workflow Foundation.

|Funkce|Popis|
|-------------|-----------------|
|Přetažení aktivity|Chcete-li vytvořit pracovní postup, přetáhněte aktivity z **panelu nástrojů** na návrhovou plochu.|
|prohlížeč vlastností|Pro konfiguraci vlastností aktivity se používá okno standard **Properties** v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|Lupa|Ikona na **úrovni přiblížení** binokulárnís se nachází pod svislým posuvníkem na pravé straně návrhové plochy. Klikněte na binokulární a vyberte procento zvětšení, které způsobí zvětšení nebo zmenšení obrázku pracovního postupu. Pro přiblížení a oddálení můžete použít také ikonu **posunu** , která zvětší ukazatel myši.|
|Posouvání|Ikona **posouvání** , kruh, který obsahuje čtyři obrácené šipky ukazující na čtyři směry, je umístěný pod svislým posuvníkem na pravé straně návrhové plochy, která se nachází pod ikonou přiblížení binokulárního zobrazení. Pokud kliknete na ikonu posouvání, místní nabídka nabízí následující možnosti kurzoru:<br /><br /> – **Přiblížení** lupy vám umožní přiblížit kliknutím na návrhovou plochu.<br />– Lupa **lupy** umožňuje oddálení kliknutím na návrhovou plochu.<br />– Kurzor pro **navigační nástroj** umožňuje "přicházet" a posunout zobrazení pracovního postupu na návrhové ploše.<br />– **Výchozí** kurzor šipky umožňuje přepnout z ostatních kurzorů zpátky na výchozí kurzor šipky.|
|Automatické posouvání|Pokud máte rozsáhlý pracovní postup, můžete chtít umístit aktivitu nad viditelné zobrazení oblasti pro návrhovou plochu. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] umožňuje přetáhnout aktivitu směrem k okraji návrhové plochy, která je nejblíže místu, kam chcete aktivitu vložit. Zobrazení návrhová plocha se v tomto směru automaticky posouvá.|
|Inteligentní značky|Aktivity, které nejsou zcela nakonfigurovány nebo nejsou správně nakonfigurovány, jsou označeny ikonou s vykřičníkem. Můžete kliknout na ikonu a zobrazit rozevírací seznam požadavků na konfiguraci, které existují u aktivity. Pak můžete pomocí okna **vlastnosti** nakonfigurovat aktivitu odpovídajícím způsobem. Pokud jsou všechny vlastnosti pro aktivitu platné, ikona vykřičníku zmizí.|

## <a name="in-this-section"></a>V tomto oddílu
 [Okna pracovních postupů v sadě Visual Studio (starší verze)](../workflow-designer/visual-studio-workflow-windows-legacy.md)

 [Vytváření projektů pracovních postupů starších verzí](../workflow-designer/creating-legacy-workflow-projects.md)

 [Zobrazení sekvenčního pracovního postupu (starší verze)](../workflow-designer/sequential-workflow-views-legacy.md)

 [Aktivity starších verzí pracovních postupů](../workflow-designer/legacy-workflow-activities.md)

 [Používání motivů v pracovních postupech (starší verze)](../workflow-designer/using-themes-in-workflows-legacy.md)

 [Používání starší verze návrháře pracovních postupů stavového stroje](../workflow-designer/using-the-legacy-state-machine-workflow-designer.md)

 [Používání starší verze návrháře aktivit](../workflow-designer/using-the-legacy-activity-designer.md)

 [Nápověda k uživatelskému rozhraní návrháře pro programovací model Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)

## <a name="see-also"></a>Viz také
 [Vývoj pracovních postupů](http://go.microsoft.com/fwlink?LinkID=65010)