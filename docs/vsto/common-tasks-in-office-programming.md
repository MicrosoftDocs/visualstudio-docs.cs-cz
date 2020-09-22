---
title: Běžné úlohy při programování pro systém Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, getting started
- FAQs (frequently asked questions) [Office development in Visual Studio]
- Office development in Visual Studio, frequently asked questions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c82b4dec0c92f19933b045040ed0f1fcecb5b10b
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809856"
---
# <a name="common-tasks-in-office-programming"></a>Běžné úlohy při programování pro systém Office
  Toto téma je navrženo tak, aby vám pomohlo najít odpovědi na následující kategorie běžných otázek týkajících se programování řešení Office pomocí sady Visual Studio.

- [Nastavení a obecné úlohy](#projects).

- [Úkoly přizpůsobení uživatelského rozhraní](#ui).

- [Úlohy automatizace Excelu](#excel)

- [Úkoly automatizace Wordu](#word).

- [Datové úlohy](#data).

- [Úlohy správy dokumentů na straně serveru](#server).

- [Úkoly zabezpečení](#security).

- [Úlohy nasazení](#deployment).

## <a name="setup-and-general-tasks"></a><a name="projects"></a> Nastavení a obecné úlohy

- [Postupy: vytváření projektů Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

- [Postupy: upgrade řešení pro systém Office](/previous-versions/4bez6837(v=vs.140)).

- [Postupy: instalace primárních sestavení vzájemné spolupráce pro systém Office](../vsto/how-to-install-office-primary-interop-assemblies.md)

- [Postupy: cílení aplikací Office prostřednictvím primárních sestavení spolupráce](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)

- [Postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

- [Postupy: otevření řešení pro systém Office bez spuštění kódu](../vsto/how-to-open-office-solutions-without-running-code.md).

- [Postupy: nastavení informací o konfiguraci pro řešení pro systém Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md).

- [Postupy: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

- [Postupy: zobrazení chyb uživatelského rozhraní doplňku](../vsto/how-to-show-add-in-user-interface-errors.md)

## <a name="user-interface-customization-tasks"></a><a name="ui"></a> Úkoly přizpůsobení uživatelského rozhraní

### <a name="controls-on-documents-and-worksheets"></a>Ovládací prvky dokumentů a listů

- [Postupy: Přidání ovládacích prvků model Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

- [Postupy: Přidání ovládacích prvků ListObject do listů](../vsto/how-to-add-listobject-controls-to-worksheets.md)

- [Postupy: Přidání ovládacích prvků model Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- [Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)

- [Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

### <a name="task-panes-in-document-level-customizations"></a>Podokna úloh v přizpůsobeních na úrovni dokumentu

- [Postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

### <a name="task-panes-in-vsto-add-ins"></a>Podokna úloh v doplňcích VSTO

- [Postupy: Přidání vlastního podokna úloh do aplikace](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)

### <a name="ribbon-customizations"></a>Přizpůsobení pásu karet

- [Postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md).

- [Postupy: Změna pozice karty na pásu karet](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

- [Postupy: Přizpůsobení předdefinované karty](../vsto/how-to-customize-a-built-in-tab.md).

- [Postupy: Přidání ovládacích prvků do zobrazení Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).

- [Postupy: Export pásu karet z Návrháře pásu karet do XML pásu karet](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).

### <a name="outlook-form-regions"></a>Oblasti formulářů aplikace Outlook

- [Postupy: Přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

- [Postupy: zabránění zobrazení oblasti formuláře v aplikaci Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)

### <a name="custom-menus"></a>Vlastní nabídky

- [Postupy: přidávání příkazů do místních nabídek](../vsto/how-to-add-commands-to-shortcut-menus.md).

## <a name="excel-automation-tasks"></a><a name="excel"></a> Úlohy automatizace Excelu

- [Postupy: zobrazení řetězce v buňce listu prostřednictvím kódu programu](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md)

- [Postupy: vytváření nových sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-create-new-workbooks.md)

- [Postupy: otevírání sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-open-workbooks.md)

- [Postupy: ukládání sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-save-workbooks.md)

- [Postupy: zavírání sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-close-workbooks.md)

- [Postupy: přidávání nových listů do sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)

- [Postupy: skrývání listů prostřednictvím kódu programu](../vsto/how-to-programmatically-hide-worksheets.md)

- [Postupy: přesouvání listů v sešitech prostřednictvím kódu programu](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)

- [Postupy: Ochrana sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-protect-workbooks.md)

- [Postupy: odkazování na oblasti listů v kódu prostřednictvím kódu programu](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)

- [Postupy: používání stylů pro oblasti sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)

- [Postupy: Změna formátování řádků listů obsahujících vybrané buňky prostřednictvím kódu programu](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)

- [Postupy: hledání textu v oblastech listů prostřednictvím kódu programu](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)

- [Postupy: tisk listů prostřednictvím kódu programu](../vsto/how-to-programmatically-print-worksheets.md)

- [Postupy: spouštění výpočtů v aplikaci Excel prostřednictvím kódu programu](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)

- [Postupy: řazení dat v listech prostřednictvím kódu programu](../vsto/how-to-programmatically-sort-data-in-worksheets.md)

## <a name="word-automation-tasks"></a><a name="word"></a> Úkoly automatizace Wordu

- [Postupy: vytváření nových dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-create-new-documents.md)

- [Postupy: otevírání existujících dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-open-existing-documents.md)

- [Postupy: ukládání dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-save-documents.md)

- [Postupy: zavírání dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-close-documents.md)

- [Postupy: vkládání textu do dokumentů aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-insert-text-into-word-documents.md)

- [Postupy: definování a výběr oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)

- [Postupy: resetování oblastí v dokumentech aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)

- [Postupy: formátování textu v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-format-text-in-documents.md)

- [Postupy: Přidání ovládacích prvků XMLNode do dokumentů aplikace Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)

- [Postupy: aktualizace textu záložek prostřednictvím kódu programu](../vsto/how-to-programmatically-update-bookmark-text.md)

- [Postupy: hledání a nahrazování textu v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)

- [Postupy: tisk dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-print-documents.md)

- [Postupy: vytváření tabulek aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-create-word-tables.md)

- [Postupy: přidávání řádků a sloupců do tabulek aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)

- [Postupy: počítání znaků v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-count-characters-in-documents.md)

## <a name="data-tasks"></a><a name="data"></a> Datové úlohy

### <a name="data-bound-controls"></a>Ovládací prvky vázané na data

- [Postupy: naplnění listů daty z databáze](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)

- [Postupy: Naplnění dokumentů daty z databáze](../vsto/how-to-populate-documents-with-data-from-a-database.md)

- [Postupy: Naplnění dokumentů daty ze služeb](../vsto/how-to-populate-documents-with-data-from-services.md)

- [Postupy: Naplnění dokumentů daty z objektů](../vsto/how-to-populate-documents-with-data-from-objects.md)

- [Postupy: Naplnění dokumentů daty z databáze](../vsto/how-to-populate-documents-with-data-from-a-database.md)

- [Postupy: Naplnění dokumentů daty ze služeb](../vsto/how-to-populate-documents-with-data-from-services.md)

- [Postupy: aktualizace zdroje dat s použitím dat z hostitelského ovládacího prvku](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

### <a name="cached-data-in-document-level-solutions"></a>Data uložená v mezipaměti v řešeních na úrovni dokumentu

- [Postupy: ukládání dat do mezipaměti pro použití v režimu offline nebo na serveru](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- [Postupy: ukládání zdroje dat v dokumentu Office do mezipaměti prostřednictvím kódu programu](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)

- [Postupy: ukládání dat do mezipaměti v dokumentu chráněném heslem](../vsto/how-to-cache-data-in-a-password-protected-document.md).

### <a name="custom-xml-data"></a>Vlastní data XML

- [Postupy: Přidání vlastních částí XML do přizpůsobení na úrovni dokumentu](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md).

- [Postupy: Přidání vlastních částí XML do dokumentů s použitím doplňků VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).

## <a name="server-side-document-management-tasks"></a><a name="server"></a> Úlohy správy dokumentů na straně serveru

- [Postupy: odebrání rozšíření spravovaného kódu z dokumentů](../vsto/how-to-remove-managed-code-extensions-from-documents.md).

- [Postupy: připojení rozšíření spravovaného kódu k dokumentům](../vsto/how-to-attach-managed-code-extensions-to-documents.md).

## <a name="security-tasks"></a><a name="security"></a> Úkoly zabezpečení

- [Postupy: podepisování řešení pro systém Office](../vsto/how-to-sign-office-solutions.md).

## <a name="deployment-tasks"></a><a name="deployment"></a> Úlohy nasazení

- [Postupy: publikování řešení pro systém Office pomocí technologie ClickOnce](/previous-versions/bb386095(v=vs.110)).

- [Postupy: publikování řešení Office na úrovni dokumentu na server SharePoint pomocí technologie ClickOnce](/previous-versions/bb608595(v=vs.110)).

- [Postupy: instalace řešení ClickOnce pro sadu Office](/previous-versions/bb608592(v=vs.110)).

- [Postupy: instalace požadovaných součástí na počítačích koncových uživatelů ke spouštění řešení pro systém Office](/previous-versions/bb608608(v=vs.110)).

- [Postupy: Příprava služby IIS na nasazení řešení pro systém Office](/previous-versions/bb608629(v=vs.110)).

- [Postupy: aktualizace nasazených řešení Office](/previous-versions/bb157871(v=vs.110))

- [Postupy: změna instalační cesty řešení pro systém Office](/previous-versions/bb608626(v=vs.110)).

## <a name="see-also"></a>Viz také
- [Začněte &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Dostupné funkce podle aplikace systému Office a typu projektu](../vsto/features-available-by-office-application-and-project-type.md)
- [Ukázky a návody pro vývoj pro Office](../vsto/office-development-samples-and-walkthroughs.md)