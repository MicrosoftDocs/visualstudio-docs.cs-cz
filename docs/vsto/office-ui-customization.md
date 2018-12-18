---
title: Přizpůsobení uživatelského rozhraní systému Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 48c7fe1948231f88aba8309d6d06186848d32455
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836760"
---
# <a name="office-ui-customization"></a>Přizpůsobení uživatelského rozhraní systému Office
  Můžete přizpůsobit uživatelské rozhraní (UI) aplikace Microsoft Office s použitím nástroje Office developer tools v sadě Visual Studio. Toto téma popisuje funkce uživatelského rozhraní, které můžete přizpůsobit v následujících částech:  
  
-   [Porovnání funkcí uživatelského rozhraní](#Comparison)  
  
-   [Podokna akcí a vlastních podoken úloh](#Actions)  
  
-   [Vlastní uživatelské rozhraní pásu karet](#Ribbon)  
  
-   [Zobrazení Backstage](#Backstage)  
  
-   [Oblastí formulářů aplikace Outlook](#FormRegion)  
  
-   [Ovládací prvky v dokumentech](#Controls)  
  
-   [Používání místních nabídek](#Shortcut)  
  
##  <a name="Comparison"></a> Porovnání funkcí uživatelského rozhraní  
 Následující tabulka porovnává hlavní funkce uživatelského rozhraní, které můžete přizpůsobit v projektech pro aplikaci Microsoft Office.  
  
|Funkce|Podporované typy projektů|Podporované aplikace Microsoft Office|  
|-------------|-----------------------------|---------------------------------------------|  
|Podokna akcí|Přizpůsobení na úrovni dokumentu|Excel<br /><br /> Word|  
|Vlastní podokna úloh|Doplňky VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word<br /><br /> Excel|  
|Vlastní uživatelské rozhraní pásu karet|Přizpůsobení na úrovni dokumentu<br /><br /> Doplňky VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Word<br /><br /> Visio|  
|Zobrazení Backstage|Přizpůsobení na úrovni dokumentu<br /><br /> Doplňky VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)].<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Word<br /><br /> Visio|  
|Oblastí formulářů aplikace Outlook|Doplňky VSTO|Outlook|  
|Ovládací prvky v dokumentech|Přizpůsobení na úrovni dokumentu<br /><br /> Doplňky VSTO|Excel<br /><br /> Word|  
|Používání místních nabídek|Přizpůsobení na úrovni dokumentu<br /><br /> Doplňky VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Word<br /><br /> Visio<br /><br /> Excel|  
  
##  <a name="Actions"></a> Podokna akcí a vlastních podoken úloh  
 Panely uživatelského rozhraní, které jsou obvykle ukotven k okraji okna v aplikaci Microsoft Office jsou podokna úloh. Téměř všechny aplikace sady Office zahrnují integrované podoken. Příkladem podokna úloh je v podokně úloh nápovědy v aplikaci Word.  
  
 Vývojářské nástroje balíku Office v sadě Visual Studio poskytuje dva různé způsoby přizpůsobení podokna úloh:  
  
- Přidání podokna akcí do přizpůsobení na úrovni dokumentu. Ve výchozím nastavení zobrazí se na pravé straně aplikace napravo od dokumentu podokno akcí. Na levé straně, horní nebo dolní části dokumentu však lze rovněž zobrazit podokno akcí.  
  
- Můžete přidat vlastního podokna úloh do doplňku VSTO. Uživatelům můžete ukotvit vlastní podokna úloh do jiné straně okna aplikace nebo vlastní podokna úloh, můžete přetáhnout do libovolného umístění v okně.  
  
  Podokna akcí a vlastních podoken úloh nakonfigurovánu hostováním širokou škálu ovládacích prvků pro pomoc s úkoly, jako je například zadávání dat uživatelům. Ve srovnání s skupiny pásu karet, podokna akcí a vlastních podoken úloh poskytují mnohem větší oblasti obsahovat text a ovládací prvky.  
  
  Další informace o podoknech akcí najdete v tématu [přehled podokna akcí](../vsto/actions-pane-overview.md). Další informace o vlastních podoknech úloh najdete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md).  
  
##  <a name="Ribbon"></a> Vlastní uživatelské rozhraní pásu karet  
 Můžete přizpůsobit uživatelské rozhraní pásu karet na funkci, která přidáte do aplikace sady Office. Na pásu karet je způsob, jak uspořádat související příkazy (ve formuláři ovládací prvky), aby byly snadněji najít. Můžete vytvořit vlastní karty pásu karet a skupiny můžete uživatelům udělit přístup k funkcím, které poskytujete ve vašem řešení. Většina funkcí, které byly přístupné prostřednictvím nabídek a panelů nástrojů v dřívějších verzích systému Microsoft Office je teď přístupný pomocí pásu karet.  
  
 Další informace najdete v tématu [přehled pásu karet](../vsto/ribbon-overview.md).  
  
##  <a name="Backstage"></a> Zobrazení Backstage  
 V aplikacích Office, kliknutím **souboru** kartě se otevře zobrazení Backstage. Zobrazení Backstage poskytuje uživatelské rozhraní, který kombinuje úrovni souboru úloh a akcí a nahrazuje podobné funkce, které jsou k dispozici tlačítko Microsoft Office v systému Microsoft Office 2007. Zobrazení Backstage je plná rozšiřitelnost pomocí XML.  
  
 Visual Studio neposkytuje Návrhář nebo rozhraní API pro přizpůsobení zobrazení Backstage. Ale pokud přidáte **pásu karet (XML)** položky do projektu sady Office můžete přidat XML do souboru XML pásu karet k přizpůsobení zobrazení Backstage. Další informace o **pásu karet (XML)** položky, naleznete v tématu [kódu XML pásu karet](../vsto/ribbon-xml.md).  
  
 Další informace o úpravách zobrazení Backstage naleznete v tématu [Úvod do zobrazení Office 2010 Backstage pro vývojáře](http://go.microsoft.com/fwlink/?LinkId=182189) a [přizpůsobení zobrazení Office 2010 Backstage pro vývojáře](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
##  <a name="FormRegion"></a> Oblastí formulářů aplikace Outlook  
 Použijte oblasti formuláře pro přidání vlastních funkcí do standardní formulářů aplikace Microsoft Office Outlook. Můžete vytvořit oblasti formulářů, které rozšiřují jakékoli existujícího formuláře s další pole nebo ovládací prvky. Pokud vytvoříte novou oblast formuláře pomocí nástroje pro vývoj sady Office v sadě Visual Studio, můžete použít pouze Windows Forms ovládací prvky na oblast formuláře. Pokud importujete oblasti formuláře, která je navržená v Outlooku, můžete použít pouze nativní ovládací prvky aplikace Outlook.  
  
 Můžete vytvořit oblasti formulářů, které zabírají různé oblasti uživatelského rozhraní aplikace Outlook. Například sousední oblasti formuláře se zobrazí v dolní části na první stránku formuláři a každý sousední oblasti formuláře je možné sbalit. Můžete také přidat oblasti formuláře samostatné, která se zobrazí jako stránky s úplné další formuláře a, který se může objevit v žádné stávající standardní formuláře nebo vlastního formuláře.  
  
 Další informace najdete v tématu [oblastí formulářů aplikace Outlook vytvořit](../vsto/creating-outlook-form-regions.md).  
  
##  <a name="Controls"></a> Ovládací prvky v dokumentech  
 Můžete přidat širokou škálu ovládacích prvků na dokumenty aplikace Word a sešitů aplikace Excel. Můžete například chtít přidejte ovládací prvek Výběr data do dokumentu, aby uživatel mohl zadat data ve standardním formátu, nebo umístit tlačítko na list pro odesílání dat do databáze.  
  
 Při vývoji projekty na úrovni dokumentu pro aplikaci Excel nebo Word návrháře aplikace Visual Studio můžete použít k přidání ovládacích prvků do dokumentu nebo sešitu v projektu v době návrhu nebo prostřednictvím kódu programu můžete přidat ovládací prvky za běhu. Při vývoji projekty doplňku VSTO pro Excel nebo Word prostřednictvím kódu programu můžete přidat ovládací prvky otevřeného dokumentu nebo sešitu v době běhu.  
  
 Další informace najdete v tématu [hostovat položky a hostujte Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md) a [ovládacích prvků na dokumenty Office – přehled Windows forms](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
##  <a name="Shortcut"></a> Používání místních nabídek  
 Místní nabídce se zobrazí, když kliknete pravým tlačítkem v okně aplikace nebo dokumentu. Můžete nastavit místní nabídce se zobrazí po provedení událost, například když uživatel klepne pravým tlačítkem myši dokumentu, sešitu nebo hostitelského ovládacího prvku. Počet různých příkazů nebo ovládacích prvků můžete přidat do místní nabídky. Vytvořte místní nabídky pomocí XML. Pokud chcete přidat **pásu karet (XML)** položky do projektu sady Office můžete přidat XML do souboru XML pásu karet, chcete-li vytvořit místní nabídky. Další informace o vytváření místních nabídek pomocí XML, naleznete v tématu [postupy: přidávání příkazů do místních nabídek](../vsto/how-to-add-commands-to-shortcut-menus.md).  
  
## <a name="see-also"></a>Viz také:  
 [Přehled pásu karet](../vsto/ribbon-overview.md)   
 [Windows forms ovládacích prvků na dokumenty Office – přehled](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Přehled podokna akcí](../vsto/actions-pane-overview.md)   
 [Vytváření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md)   
 [Vlastní podokna úloh](../vsto/custom-task-panes.md)   
 [Použití ovládacích prvků WPF v řešeních pro systém Office](../vsto/using-wpf-controls-in-office-solutions.md)   
 [Postupy: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)   
 [Postupy: Add-in zobrazení chyb uživatelského rozhraní](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Návod: Shromažďování dat pomocí formuláře Windows](../vsto/walkthrough-collecting-data-using-a-windows-form.md)  
  
  