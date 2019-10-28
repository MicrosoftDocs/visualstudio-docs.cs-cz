---
title: Přizpůsobení uživatelského rozhraní systému Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- menus [Office development in Visual Studio], customizing
- actions panes [Office development in Visual Studio], creating
- WPF [Office development in Visual Studio]
- toolbars [Office development in Visual Studio], customizing
- Office applications [Office development in Visual Studio], UI customization
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 15c7061030bec6aebca9cdc63d0cd0e0c79cc9aa
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985702"
---
# <a name="office-ui-customization"></a>Přizpůsobení uživatelského rozhraní systému Office
  Můžete přizpůsobit uživatelské rozhraní (UI) systém Microsoft Office aplikací pomocí nástrojů Office Developer Tools v sadě Visual Studio. Toto téma popisuje funkce uživatelského rozhraní, které můžete přizpůsobit v následujících částech:

- [Porovnání funkcí uživatelského rozhraní](#Comparison)

- [Podokna akcí a vlastní podokna úloh](#Actions)

- [Uživatelské rozhraní vlastního pásu karet](#Ribbon)

- [Zobrazení Backstage](#Backstage)

- [Oblasti formulářů aplikace Outlook](#FormRegion)

- [Ovládací prvky v dokumentech](#Controls)

- [Místní nabídky](#Shortcut)

## <a name="Comparison"></a>Porovnání funkcí uživatelského rozhraní
 Následující tabulka porovnává hlavní funkce uživatelského rozhraní, které můžete přizpůsobit v systém Microsoft Office projekty.

|Funkce|Podporované typy projektů|Podporované aplikace systém Microsoft Office|
|-------------|-----------------------------|---------------------------------------------|
|Podokno akcí|Přizpůsobení na úrovni dokumentu|Excel<br /><br /> Word|
|Vlastní podokna úloh|Doplňky VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word<br /><br /> Excel|
|Uživatelské rozhraní vlastního pásu karet|Přizpůsobení na úrovni dokumentu<br /><br /> Doplňky VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio|
|Zobrazení Backstage|Přizpůsobení na úrovni dokumentu<br /><br /> Doplňky VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)].<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio|
|Oblasti formulářů aplikace Outlook|Doplňky VSTO|Outlook|
|Ovládací prvky v dokumentech|Přizpůsobení na úrovni dokumentu<br /><br /> Doplňky VSTO|Excel<br /><br /> Word|
|Místní nabídky|Přizpůsobení na úrovni dokumentu<br /><br /> Doplňky VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio<br /><br /> Excel|

## <a name="Actions"></a>Podokna akcí a vlastní podokna úloh
 Podokna úloh jsou panely uživatelského rozhraní, které jsou obvykle ukotveny na jednu stranu okna aplikace systém Microsoft Office. Skoro všechny systém Microsoft Office aplikace obsahují integrovaná podokna úloh. Příkladem podokna úloh je podokno úloh Help (aplikace Word).

 Vývojové nástroje pro Office v sadě Visual Studio poskytují dva různé způsoby přizpůsobení podoken úloh:

- Do přizpůsobení na úrovni dokumentu můžete přidat podokno akcí. Ve výchozím nastavení se podokno akce zobrazuje na pravé straně aplikace, napravo od dokumentu. Nicméně podokno akce lze také zobrazit vlevo, nahoře nebo dole v dokumentu.

- Do doplňku VSTO můžete přidat vlastní podokno úloh. Uživatelé mohou ukotvit vlastní podokna úloh do různých stran okna aplikace nebo mohou přetahovat vlastní podokna úloh na libovolné místo v okně.

  Podokna akcí a vlastní podokna úloh poskytují funkce hostováním nejrůznějších ovládacích prvků, které uživatelům pomůžou s úkoly, jako je zadávání dat. V porovnání se skupinou pásu karet představují podokna akcí a vlastní podokna úloh mnohem větší oblast pro zahrnutí textu a ovládacích prvků.

  Další informace o podoknech akcí najdete v tématu [Přehled podokna akcí](../vsto/actions-pane-overview.md). Další informace o vlastních podoknech úloh najdete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md).

## <a name="Ribbon"></a>Uživatelské rozhraní vlastního pásu karet
 Můžete přizpůsobit uživatelské rozhraní pásu karet a vystavit funkce, které přidáte do aplikací v systému Office. Pás karet je způsob, jak uspořádat související příkazy (ve formě ovládacích prvků) tak, aby byly snáze najít. Můžete vytvořit vlastní karty a skupiny pásu karet, které uživatelům umožní přístup k funkcím, které zadáte ve vašem řešení. Většina funkcí, k nimž došlo pomocí nabídek a panelů nástrojů v předchozích verzích systém Microsoft Office systému, je teď dostupná pomocí pásu karet.

 Další informace najdete v tématu [Přehled pásu karet](../vsto/ribbon-overview.md).

## <a name="Backstage"></a>Zobrazení Backstage
 V aplikacích Office kliknutím na kartu **soubor** otevřete zobrazení Backstage. Zobrazení Backstage poskytuje uživatelské rozhraní, které kombinuje úlohy a akce na úrovni souborů, a nahrazuje podobné funkce, které jsou k dispozici na tlačítku systém Microsoft Office v systému 2007 systém Microsoft Office. Zobrazení Backstage je plně rozšiřitelné pomocí XML.

 Visual Studio neposkytuje návrháře ani rozhraní API pro přizpůsobení zobrazení Backstage. Pokud však přidáte položku **pásu karet (XML)** do projektu sady Office, můžete přidat XML do souboru XML pásu karet pro přizpůsobení zobrazení Backstage. Další informace o položkách **pásu karet (XML)** najdete v tématu [XML pásu karet](../vsto/ribbon-xml.md).

 Další informace o přizpůsobení zobrazení Backstage najdete v tématu [Úvod do zobrazení Backstage office 2010 pro vývojáře](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) a [přizpůsobení zobrazení Backstage Office 2010 pro vývojáře](/previous-versions/office/developer/office-2010/ee815851(v=office.14)).

## <a name="FormRegion"></a>Oblasti formulářů aplikace Outlook
 Pomocí oblastí formuláře můžete přidat vlastní funkce do formulářů Standard systém Microsoft Office Outlook. Můžete vytvořit oblasti formulářů, které rozšíří libovolný existující formulář s dalšími poli nebo ovládacími prvky. Pokud vytvoříte novou oblast formuláře pomocí nástrojů pro vývoj pro Office v sadě Visual Studio, můžete použít pouze ovládací prvky model Windows Forms v oblasti formuláře. Pokud importujete oblast formuláře, která byla navržena v aplikaci Outlook, můžete použít pouze nativní ovládací prvky aplikace Outlook.

 Můžete vytvořit oblasti formulářů, které zabírají různé oblasti uživatelského rozhraní aplikace Outlook. Například sousední oblasti formuláře se zobrazí v dolní části první stránky formuláře a všechny sousední oblasti formuláře jsou sbalitelné. Můžete také přidat samostatnou oblast formuláře, která se zobrazí jako plná další stránka formuláře a která se může objevit v jakékoli existující standardní formuláři nebo vlastním formuláři.

 Další informace najdete v tématu [vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md).

## <a name="Controls"></a>Ovládací prvky v dokumentech
 Do dokumentů aplikace Word a sešitů aplikace Excel lze přidat nejrůznější ovládací prvky. Například můžete chtít přidat ovládací prvek pro výběr data do dokumentu, aby uživatel mohl zadat data ve standardním formátu, nebo vložit tlačítko na list pro odeslání dat do databáze.

 Při vývoji projektů na úrovni dokumentu v aplikaci Excel nebo Word můžete pomocí návrháře aplikace Visual Studio přidat ovládací prvky do dokumentu nebo sešitu v projektu v době návrhu nebo programově přidat ovládací prvky za běhu. Když vyvíjíte projekty doplňku VSTO v Excelu nebo Wordu, můžete programově přidat ovládací prvky do libovolného otevřeného dokumentu nebo sešitu v době běhu.

 Další informace naleznete v tématu Přehled [hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md) a [ovládací prvky Windows Forms v dokumentech Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="Shortcut"></a>Místní nabídky
 Místní nabídka se zobrazí po kliknutí pravým tlačítkem myši v dokumentu nebo v okně aplikace. Můžete nastavit místní nabídku, která se zobrazí poté, co dojde k události, například když uživatel klikne pravým tlačítkem myši na dokument, sešit nebo hostitelský ovládací prvek. Do místní nabídky můžete přidat několik různých příkazů nebo ovládacích prvků nabídky. Vytvořte místní nabídky pomocí XML. Pokud přidáte položku **pásu karet (XML)** do projektu sady Office, můžete přidat XML do souboru XML pásu karet a vytvořit tak místní nabídky. Další informace o použití jazyka XML k vytvoření místních nabídek naleznete v tématu [How to: Add Commands to a Shortcut Menus](../vsto/how-to-add-commands-to-shortcut-menus.md).

## <a name="see-also"></a>Viz také:
- [Přehled pásu karet](../vsto/ribbon-overview.md)
- [Přehled ovládacích prvků Windows Forms v dokumentech Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Přehled podokna akcí](../vsto/actions-pane-overview.md)
- [Vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md)
- [Vlastní podokna úloh](../vsto/custom-task-panes.md)
- [Použití ovládacích prvků WPF v řešeních pro systém Office](../vsto/using-wpf-controls-in-office-solutions.md)
- [Postupy: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)
- [Postupy: zobrazení chyb uživatelského rozhraní doplňku](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Návod: shromáždění dat pomocí formuláře Windows](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
