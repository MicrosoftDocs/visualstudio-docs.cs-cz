---
title: Projekty a řešení – dialogové okno Možnosti
ms.date: 07/14/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
- VS.ToolsOptionsPages.Projects.Locations
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09881462b0723dc1e601c908efeabc317ed70b69
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388946"
---
# <a name="projects-and-solutions-page-options-dialog-box"></a>Stránku projekty a řešení, dialogové okno Možnosti

Nastaví chování sady Visual Studio související s projekty a řešení. Zpřístupníte tyto možnosti, vyberte **nástroje** > **možnosti**, rozbalte **projekty a řešení**a pak vyberte **Obecné** .

Výchozí cesty pro složky projektu a šablony, které se konfigurují pomocí **umístění** kartu v dialogovém okně stejné.

## <a name="general-page"></a>Obecná stránka

Tyto možnosti jsou k dispozici na **Obecné** stránky.

### <a name="always-show-error-list-if-build-finishes-with-errors"></a>Vždy zobrazit seznam chyb-li sestavení dokončí s chybami

Otevře **seznam chyb** okně při dokončení sestavení, pouze v případě, že projekt se nepovedlo sestavit. Se zobrazí chyby, ke kterým dochází během procesu sestavení. Když toto políčko zaškrtnuto, stále dochází k chybám, ale okno se neotevře, po dokončení sestavení. Tato možnost je povolená ve výchozím nastavení.

### <a name="track-active-item-in-solution-explorer"></a>Sledovat aktivní položku v Průzkumníku řešení

Pokud je vybráno, **Průzkumníka řešení** automaticky otevře a aktivní položky je vybrána. Vybraná položka změny při práci s různé soubory v projektu nebo řešení nebo různé součásti v návrháři. Pokud tato možnost vybrána, výběr v **Průzkumníka řešení** nezmění automaticky. Tato možnost je povolená ve výchozím nastavení.

### <a name="show-advanced-build-configurations"></a>Zobrazit pokročilou konfiguraci sestavení

Při výběru možnosti konfigurace sestavení se zobrazí na **stránky vlastností projektu** dialogové okno a **stránek vlastností řešení** dialogové okno. Není-li zaškrtnuto, možnosti konfigurace sestavení nejsou zobrazeny na **stránky vlastností projektu** dialogové okno a **stránek vlastností řešení** dialogové okno pro jazyk Visual Basic a C# projekty, které obsahují jeden konfigurace nebo dvě konfigurace pro ladění a vydání. Pokud projekt obsahuje konfigurace definovaná uživatelem, jsou uvedeny možnosti konfigurace sestavení.

Při zrušení výběru, příkazy na **sestavení** nabídky, jako například **sestavit řešení**, **znovu sestavit řešení**, a **Vyčistit řešení**, jsou proveden na konfiguraci vydané verze a příkazy na **ladění** nabídky, například **spustit ladění** a **spustit bez ladění**, jsou prováděny na konfiguraci ladění.

### <a name="always-show-solution"></a>Vždy zobrazit řešení

Při výběru řešení a všechny příkazy, které fungují v řešení jsou vždy zobrazen v integrovaném vývojovém prostředí. Není-li zaškrtnuto, všechny projekty byly vytvořeny jako samostatné projekty a nevidíte řešení v Průzkumníku řešení nebo příkazy, které fungují v řešení v integrovaném vývojovém prostředí Pokud řešení obsahuje pouze jeden projekt.

### <a name="save-new-projects-when-created"></a>Uložit nové projekty při vytvoření

Pokud je vybráno, můžete zadat umístění pro váš projekt v **nový projekt** dialogové okno. Není-li zaškrtnuto, všechny nové projekty jsou vytvořeny jako dočasné projekty. Při práci s dočasné projekty, můžete vytvořit a experimentovat s projektem, aniž byste museli zadat umístění na disku.

### <a name="warn-user-when-the-project-location-is-not-trusted"></a>Upozornit uživatele, pokud umístění projektu není důvěryhodné

Při pokusu o vytvoření nového projektu nebo otevřete existující projekt do umístění, které není plně důvěryhodné (třeba na cestu UNC nebo cesta k protokolu HTTP), zobrazí se zpráva. Tuto možnost použijte k určení, zda zpráva se zobrazí pokaždé, když se při pokusu o vytvoření nebo otevření projektu do umístění, které není plně důvěryhodné.

### <a name="show-output-window-when-build-starts"></a>Zobrazit okno výstup při spuštění sestavení

Automaticky zobrazí [okno výstup](../../ide/reference/output-window.md) v integrovaném vývojovém prostředí od počátku řešení sestavení.

### <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>Vyzvat k symbolickému přejmenování při přejmenování souborů

Pokud je vybráno, Visual Studio zobrazí okno se zprávou s dotazem, jestli ji by měl také přejmenování všech referencí v projektu na prvek kódu.

### <a name="prompt-before-moving-files-to-a-new-location"></a>Zobrazit výzvu před přesunutím souborů do nového umístění

Pokud je vybráno, Visual Studio zobrazí okno se zprávou potvrzení před akcemi v se změnilo umístění souborů **Průzkumníka řešení**.

### <a name="reopen-documents-on-solution-load"></a>Znovu otevřít dokumenty u načtení řešení

**Nové ve verzi Visual Studio 2017 verze 15.8 preview 2 a novější**

Pokud je vybráno, dokumenty, které byly zanechány otevřít předchozí doba řešení bylo ukončeno. jsou automaticky otevře při otevření řešení.

Znovu otevřít určité typy souborů nebo návrháři zpozdit načtení řešení. Zrušte zaškrtnutí této možnosti [vylepšil výkon při zatížení řešení](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore) Pokud už nechcete obnovit předchozí místní řešení.

## <a name="locations-page"></a>Stránka umístění

Tyto možnosti jsou k dispozici na **umístění** stránky.

### <a name="projects-location"></a>Umístění projektů

Určuje výchozí umístění, kde sada Visual Studio vytvoří nové projekty a řešení. Dialogová okna několika také použít tak umístění, nastavte tuto možnost pro složku počáteční body. Například **otevřít projekt** dialogové okno používá toto umístění pro **projekty** zástupce.

### <a name="user-project-templates-location"></a>Umístění šablon projektů uživatele

Určuje výchozí umístění, která **nový projekt** dialogové okno používá k vytvoření seznamu **šablony**. Další informace najdete v tématu [postupy: vyhledání a uspořádat šablony](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

### <a name="user-item-templates-location"></a>Umístění šablon položek uživatele

Určuje výchozí umístění, která **přidat novou položku** dialogové okno používá k vytvoření seznamu **šablony**. Další informace najdete v tématu [postupy: vyhledání a uspořádat šablony](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Viz také:

- [Dialogové okno Možnosti, projekty a řešení, sestavit a spustit](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Dialogové okno Možnosti, Projekty a řešení, Webové projekty](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
