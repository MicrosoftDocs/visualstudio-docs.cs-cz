---
title: Běžné úlohy při programování pro systém Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, getting started
- FAQs (frequently asked questions) [Office development in Visual Studio]
- Office development in Visual Studio, frequently asked questions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 085ed1a4f430be957d96991798458e411bc22992
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672805"
---
# <a name="common-tasks-in-office-programming"></a>Běžné úlohy při programování pro systém Office
  V tomto tématu slouží k vám pomůžou najít odpovědi v následujících kategoriích běžné otázky o programování řešení pro systém Office s použitím sady Visual Studio.  
  
-   [Instalační program a obecné úkoly](#projects).  
  
-   [Uživatelské úkoly vlastního nastavení rozhraní](#ui).  
  
-   [Automatizace úloh aplikace Excel](#excel).  
  
-   [Úlohy automatizace aplikace Word](#word).  
  
-   [Data úlohy](#data).  
  
-   [Úlohy správy dokumentů na straně serveru](#server).  
  
-   [Zabezpečení úloh](#security).  
  
-   [Úlohy nasazení](#deployment).  
  
##  <a name="projects"></a> Instalační program a obecné úkoly  
  
-   [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
-   [Postupy: řešení pro systém Office upgradu](https://msdn.microsoft.com/a269e539-b717-4680-a568-2152b070347e).  
  
-   [Postupy: sestavení primární spolupráce Office instalace](../vsto/how-to-install-office-primary-interop-assemblies.md).  
  
-   [Postupy: aplikace Office cílové primárních sestaveních vzájemné spolupráce](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
-   [Postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
-   [Postupy: řešení Open Office bez spuštění kódu](../vsto/how-to-open-office-solutions-without-running-code.md).  
  
-   [Postupy: nastavení informací o konfiguraci pro řešení Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md).  
  
-   [Postupy: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
-   [Postupy: Add-in zobrazení chyb uživatelského rozhraní](../vsto/how-to-show-add-in-user-interface-errors.md).  
  
##  <a name="ui"></a> Úkoly vlastního nastavení uživatelského rozhraní  
  
### <a name="controls-on-documents-and-worksheets"></a>Ovládacích prvků na dokumenty a sešity  
  
-   [Postupy: Přidání ovládacích prvků Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).  
  
-   [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
-   [Postupy: Přidání ovládacích prvků ListObject do listů](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
-   [Postupy: Přidání ovládacích prvků Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).  
  
-   [Postupy: Přidání obsahu ovládacích prvků do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
-   [Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
### <a name="task-panes-in-document-level-customizations"></a>Podokna úloh v přizpůsobeních na úrovni dokumentu  
  
-   [Postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
### <a name="task-panes-in-vsto-add-ins"></a>Podokna úloh v doplňcích VSTO  
  
-   [Postupy: Přidání vlastního podokna úloh do aplikace](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
### <a name="ribbon-customizations"></a>Přizpůsobení pásu karet  
  
-   [Postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
-   [Postupy: Změna pozice karty na pásu karet](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).  
  
-   [Postupy: Přizpůsobení předdefinované karty](../vsto/how-to-customize-a-built-in-tab.md).  
  
-   [Postupy: Přidání ovládacích prvků do zobrazení Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).  
  
-   [Postupy: Export pásu karet z Návrháře pásu karet do kódu XML pásu karet](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).  
  
### <a name="outlook-form-regions"></a>Oblastí formulářů aplikace Outlook  
  
-   [Postupy: přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
-   [Postupy: zabránění zobrazení oblasti formuláře Outlooku](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).  
  
### <a name="custom-menus"></a>Vlastní nabídky  
  
-   [Postupy: přidávání příkazů do místních nabídek](../vsto/how-to-add-commands-to-shortcut-menus.md).  
  
##  <a name="excel"></a> Úlohy automatizace aplikace Excel  
  
-   [Postupy: zobrazování v buňkách listů prostřednictvím kódu programu řetězec](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md).  
  
-   [Postupy: vytváření nových sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-create-new-workbooks.md).  
  
-   [Postupy: otevírání sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-open-workbooks.md).  
  
-   [Postupy: ukládání sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-save-workbooks.md).  
  
-   [Postupy: zavírání sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-close-workbooks.md).  
  
-   [Postupy: přidávání nových listů do sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).  
  
-   [Postupy: skrývání listů prostřednictvím kódu programu](../vsto/how-to-programmatically-hide-worksheets.md).  
  
-   [Postupy: přesouvání listů v sešitech prostřednictvím kódu programu](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md).  
  
-   [Postupy: zamykání sešitů](../vsto/how-to-programmatically-protect-workbooks.md).  
  
-   [Postupy: odkazování na oblasti listů v kódu programu](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md).  
  
-   [Postupy: používání stylů pro oblasti sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md).  
  
-   [Postupy: Změna formátování řádků listů obsahujících zvolené buňky prostřednictvím kódu programu](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md).  
  
-   [Postupy: hledání textu v oblastech listů prostřednictvím kódu programu](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md).  
  
-   [Postupy: tisk listů prostřednictvím kódu programu](../vsto/how-to-programmatically-print-worksheets.md).  
  
-   [Postupy: spouštění výpočtů v aplikaci Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md).  
  
-   [Postupy: řazení dat na listech prostřednictvím kódu programu](../vsto/how-to-programmatically-sort-data-in-worksheets.md).  
  
##  <a name="word"></a> Úlohy automatizace aplikace Word  
  
-   [Postupy: vytváření nových dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-create-new-documents.md).  
  
-   [Postupy: otevírání stávajících dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-open-existing-documents.md).  
  
-   [Postupy: ukládání dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-save-documents.md).  
  
-   [Postupy: zavírání dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-close-documents.md).  
  
-   [Postupy: vkládání textu do dokumentů aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-insert-text-into-word-documents.md).  
  
-   [Postupy: Programová definování a výběr oblastí v dokumentech](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).  
  
-   [Postupy: Programová resetování oblastí v dokumentech aplikace Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md).  
  
-   [Postupy: formátování textu v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-format-text-in-documents.md).  
  
-   [Postupy: Přidání ovládacích prvků XMLNode do dokumentů aplikace Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).  
  
-   [Postupy: programově aktualizovat textu záložky](../vsto/how-to-programmatically-update-bookmark-text.md).  
  
-   [Postupy: Programová hledání a nahrazování textu v dokumentech](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md).  
  
-   [Postupy: tisk dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-print-documents.md).  
  
-   [Postupy: vytváření tabulek aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-create-word-tables.md).  
  
-   [Postupy: Programové přidávání řádků a sloupců do tabulek aplikace Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md).  
  
-   [Postupy: Programová počet znaků v dokumentech](../vsto/how-to-programmatically-count-characters-in-documents.md).  
  
##  <a name="data"></a> Data úlohy  
  
### <a name="data-bound-controls"></a>Ovládací prvky vázané daty  
  
-   [Postupy: naplnění listů daty z databáze](../vsto/how-to-populate-worksheets-with-data-from-a-database.md).  
  
-   [Postupy: naplnění dokumentů daty z databáze](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
-   [Postupy: naplnění dokumentů daty ze služeb](../vsto/how-to-populate-documents-with-data-from-services.md).  
  
-   [Postupy: naplnění dokumentů daty z objektů](../vsto/how-to-populate-documents-with-data-from-objects.md).  
  
-   [Postupy: naplnění dokumentů daty z databáze](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
-   [Postupy: naplnění dokumentů daty ze služeb](../vsto/how-to-populate-documents-with-data-from-services.md).  
  
-   [Postupy: aktualizace zdroje dat s použitím dat z hostitelského ovládacího prvku](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
### <a name="cached-data-in-document-level-solutions"></a>Data uložená v mezipaměti v řešeních na úrovni dokumentu  
  
-   [Postupy: mezipaměti dat pro použití v režimu offline nebo na serveru](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   [Postupy: zdroj dat v dokumentu systému Office do mezipaměti prostřednictvím kódu programu](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
-   [Postupy: do mezipaměti ukládat data v dokumentu chráněném heslem](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
### <a name="custom-xml-data"></a>Vlastní data XML  
  
-   [Postupy: Přidání vlastních částí XML do přizpůsobení na úrovni dokumentu](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md).  
  
-   [Postupy: Přidání vlastních částí XML do dokumentů s použitím doplňků VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).  
  
##  <a name="server"></a> Úlohy správy dokumentů na straně serveru  
  
-   [Postupy: odebrání rozšíření se spravovaným kódem z dokumentů](../vsto/how-to-remove-managed-code-extensions-from-documents.md).  
  
-   [Postupy: připojení rozšíření se spravovaným kódem do dokumentů](../vsto/how-to-attach-managed-code-extensions-to-documents.md).  
  
##  <a name="security"></a> Zabezpečení úloh  
  
-   [Postupy: podepisování řešení pro Office](../vsto/how-to-sign-office-solutions.md).  
  
##  <a name="deployment"></a> Úlohy nasazení  
  
-   [Postupy: publikování řešení Office s použitím technologie ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).  
  
-   [Postupy: publikování řešení Office úrovni dokumentu na SharePoint serveru s použitím technologie ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58).  
  
-   [Postupy: Instalace řešení ClickOnce Office](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065).  
  
-   [Postupy: instalace požadovaných součástí na počítačích koncových uživatelů, které spouštějí řešení Office](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
-   [Postupy: Příprava služby IIS k nasazení řešení pro systém Office](https://msdn.microsoft.com/f62bce70-81d4-4f8b-86e6-2f2afec5d9b4).  
  
-   [Postupy: aktualizace nasazené řešení pro systém Office](https://msdn.microsoft.com/be96db53-b6ea-46ab-b8d9-b76b098b3b13).  
  
-   [Postupy: změnit cestu instalace řešení pro Office](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).  
  
## <a name="see-also"></a>Viz také:  
 [Začínáme &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Zadejte dostupné funkce podle aplikace systému Office a projektu](../vsto/features-available-by-office-application-and-project-type.md)   
 [Ukázky vývoje pro Office a názorné postupy](../vsto/office-development-samples-and-walkthroughs.md)  
  
  