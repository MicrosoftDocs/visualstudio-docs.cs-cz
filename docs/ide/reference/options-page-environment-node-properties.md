---
title: Stránka Možnosti, vlastnosti uzlu prostředí
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio], controlling Tools Options
- Tools Options settings, Environment node properties
ms.assetid: 26dca41f-91fc-4ca7-9103-3da402baa1d5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e22b24889a14d49afddd3c30858814ddec663e6a
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672727"
---
# <a name="options-page-environment-node-properties"></a>Stránka Možnosti, vlastnosti uzlu prostředí
Tento dokument popisuje stránky (nebo kolekce vlastností), které jsou přidruženy **prostředí** kategorie, `DTE.Properties("Environment", <Property Page>)`, nástroje **možnosti** dialogové okno. Název každého pododdílu je volání, které slouží k přístupu k vlastnosti kolekce a v tabulce v každém pododdílu jsou uvedeny vlastnosti v kolekci.

## <a name="general"></a>Obecné
 `DTE.Properties("Environment", "General")`

|Název položky vlastnosti|Hodnota|Popis|
| - |-----------|-----------------|
|ShowStatusBar|Get/Set (Boolean)|Určuje, zda je viditelný stavový řádek.|
|WindowMenuContainsNItems|Získá nebo nastaví (krátký)|Určuje, jak okna dokumentu jsou obsaženy v dolní části nabídky Windows.|
|MRUListContainsNItems|Získá nebo nastaví (krátký)|Určuje, kolik souborů se zobrazí v podnabídce "Naposledy použitých".|
|Animace|Get/Set (Boolean)|Určuje, zda integrovaného vývojového prostředí (IDE) používá animace ve stavovém řádku.|
|AnimationSpeed|Získá nebo nastaví (krátký)||
|AutoAdjustExperience|Get/Set (Boolean)|Automaticky přizpůsobí vzhled v závislosti na výkonu klienta.|
|RichClientExperienceOptions|Get/Set (Enum)|Umožňuje vzhled plně funkčního klienta s hodnotami v <xref:EnvDTE100.vsRichClientExperienceOptions>.|
|CloseButtonActiveTabOnly|Get/Set (Boolean)|Určuje, zda **Zavřít** tlačítko se zobrazí pouze na aktivní kartě.|
|AutohidePinActiveTabOnly|Get/Set (Boolean)|Určuje, zda **automaticky skrýt** ovlivní pouze aktivní kartě.|

## <a name="add-inmacros-security"></a>Přidat doplňků/maker zabezpečení
 `DTE.Properties("Environment", "AddinMacrosSecurity")`

|Název položky vlastnosti|Hodnota|Popis|
| - |-----------|-----------------|
|MacrosEnabled|Get/Set (Boolean)|Umožňuje spuštění maker.|
|AddinsEnabled|Get/Set (Boolean)|Umožňuje doplňků pro načtení.|
|LoadAddinsFromTheWeb|Get/Set (Boolean)|Umožňuje doplňků pro načtení z adresy URL na webu.|

## <a name="documents"></a>Dokumenty
 `DTE.Properties("Environment", "Documents")`

|Název položky vlastnosti|Hodnota|Popis|
| - |-----------|-----------------|
|ReuseSavedActiveDocWindow|Get/Set (Boolean)|Určuje, zda otevření nového souboru opětovně používá aktuální okno dokumentu Pokud je aktuální dokument uložen. `false` znamená, že vždy otevřít nové okno dokumentu pro každý dokument otevřít.|
|DetectFileChangesOutsideIDE|Get/Set (Boolean)|Určuje, zda prostředí automaticky načte soubory otevřené v integrovaném vývojovém prostředí, když se operační systém upozornění rozhraní IDE, že soubory byly změněny na disku.|
|AutoloadExternalChanges|Get/Set (Boolean)|Určuje, zda zjistil, že externí změny otevírat dokumenty automaticky znovu načtěte upravený soubor, pokud není upraven v otevřeném dokumentu. Pokud se upraví otevřít dokument a tato vlastnost je `true`, pak IDE zobrazí výzvu, jako kdyby byla tato vlastnost `false`.|
|InitializeOpenFileFromCurrentDocument|Get/Set (Boolean)|Určuje, zda <xref:EnvDTE.DTEClass.OpenFile%2A> příkaz nasazení nasazuje adresář a název souboru z poslední aktivní dokument nebo na posledním místě otevřít soubor.|
|MiscFilesProjectSavesLastNItems|Získá nebo nastaví (krátký)|Určuje, kolik souborů záznamů různé soubory projektu. V důsledku toho se zobrazí, co naposledy otevřeném jako vedlejší soubor na disku při dalším použití integrovaného vývojového prostředí.|
|ShowMiscFilesProject|Get/Set (Boolean)|Určuje, zda je zobrazen ostatních souborech projektu.|
|CheckForConsisentLineEndings|Get/Set (Boolean)|Kontroly konce řádků při načtení souboru.|
|SaveDocsAsUnicodeWhenDataLoss|Get/Set (Boolean)|Ukládá dokumenty znakové sady Unicode, pokud data nelze uložit v znakové stránce.|
|DontShowGlobalUndoChangeLossDialog|Get/Set (Boolean)|Zobrazí upozornění, když bude globální akce zpět upravovat ostatní upravené soubory.|
|AllowEditingReadOnlyFiles|Get/Set (Boolean)|Povolí úpravy souborů pouze pro čtení, ale dáme upozornění při snaze k jejich uložení.|
|DocumentDockPreference|Get/Set (Enum)|<xref:EnvDTE100.vsDocumentDockPreferenceOptions>. Pozice v kartě a ve kterých se mají vložit otevřený dokument.|

## <a name="extension-manager"></a>správce rozšíření
 `DTE.Properties("Environment", "ExtensionManager")`

|Název položky vlastnosti|Hodnota|Popis|
| - |-----------|-----------------|
|EnableAdminExtensions|Get/Set (Boolean)|Načte rozšíření vázaná na uživatele při spuštění sady Visual Studio v části přihlašovací údaje správce. Po změně této hodnoty je třeba restartovat Visual Studio.|
|EnableOnline|Get/Set (Boolean)|Umožňuje přístup k rozšíření na Visual Studio Marketplace.|
|AutomaticallyCheckForUpdates|Get/Set (Boolean)|Automaticky vyhledá aktualizace nainstalované rozšíření.|

## <a name="find-and-replace"></a>hledání a nahrazování
 `DTE.Properties("Environment", "FindAndReplace")`

|Název položky vlastnosti|Hodnota|Popis|
| - |-----------|-----------------|
|ShowWarningMessages|Get/Set (Boolean)|Zobrazí upozornění.|
|InitializeFromEditor|Get/Set (Boolean)|Automaticky naplní **najít** pole s textem z editoru.|
|ShowMessageBoxes|Get/Set (Boolean)|Zobrazí informační zprávy.|
|HideWindowsAfterMatchFromQuickFindReplace|Get/Set (Boolean)|Skryje **najít a nahradit** okno po shoda je vyhledán pomocí **rychlé hledání** nebo **rychlého nahrazení**.|

## <a name="import-and-export-settings"></a>Nastavení importu a exportu
 `DTE.Properties("Environment", "Import and Export Settings")`

|Název položky vlastnosti|Hodnota|Popis|
| - |-----------|-----------------|
|TrackTeamSettings|Get/Set (Boolean)|Použije nastavení v souboru určeném TeamSettingsFile.|
|TeamSettingsFile|Získá nebo nastaví (String)|Název souboru, který má nastavení týmu.|
|AutoSaveFile|Získá nebo nastaví (String)|Název souboru, kde se automaticky uloží uživatelská nastavení.|

## <a name="international-settings"></a>Mezinárodní nastavení
 `DTE.Properties("Environment", "International")`

|Název položky vlastnosti|Hodnota|Popis|
| - |-----------|-----------------|
|Jazyk|Získá nebo nastaví (String)|Hodnota LCID pro aktuální jazyk pro Visual Studio.|

## <a name="keyboard"></a>Klávesnice
 `DTE.Properties("Environment", "Keyboard")`

|Název položky vlastnosti|Hodnota|Popis|
| - |-----------|-----------------|
|Schéma|Získá nebo nastaví (String)|Vrátí řetězec, který obsahuje vestavěné schéma, řetězec obsahující úplnou cestu souboru .vsk, který je načten nebo "(výchozí)" Pokud se žádný soubor .vsk, který je načten.|

## <a name="projects-and-solution"></a>Projekty a řešení
 `DTE.Properties("Environment", "ProjectsAndSolution")`

|Název položky vlastnosti|Hodnota|Popis|
| - |-----------|-----------------|
|OnRunOrPreview|Získá nebo nastaví (String)|Určuje, zda integrovaného vývojového prostředí všechno, co ukládat před náhledem nebo spuštěním sestavením projektu.|
|ProjectsLocation|Získá nebo nastaví (String)|Určuje výchozí adresář kde **přidat projekt** dialogové okno uloží nové projekty.|
|ShowOutputWindowBeforeBuild|Get/Set (Boolean)|Určuje, zda od sestavení se zobrazí **výstup** okna.|
|ShowTaskListAfterBuild|Get/Set (Boolean)|Určuje, zda operace neúspěšné sestavení se zobrazí **seznamu úkolů** po dokončení sestavení.|
|TrackFileSelectionInExplorer|Get/Set (Boolean)|Určuje, zda je aktuální položky sledována v **Průzkumníka řešení**.|
|AlwaysShowSolutionNode|Get/Set (Boolean)|Určuje, zda se zobrazí uzel řešení.|
|OnlySaveStartupProjectsAndDependencies|Get/Set (Boolean)|Určuje, zda operace ukládání projektů po spuštění a jejich závislé soubory.|
|ShowAdvancedBuildConfigurations|Get/Set (Boolean)|Určuje, zda se zobrazí upřesněné konfigurace sestavení.|
|ConcurrentBuilds|Získá nebo nastaví (String)|Určuje maximální počet paralelně sestavovaných projektů, které mohou nastat.|
|SaveNewProjects|Get/Set (Boolean)|Určuje, jestli se po vytvoření automaticky uloží nové projekty.|
|PromptForRenameSymbol|Get/Set (Boolean)|Určuje, zda chcete vyzvat k symbolickému přejmenování, když jsou soubory přejmenovat.|
|OnRunWhenErrors|Get/Set (Enum)|Určuje chování při spuštění, když se sestavení dokončilo s chybami.|
|OnRunWhenOutOfDate|Get/Set (Enum)|Určuje chování při spuštění, když projekt není aktuální.|
|ProjectTemplatesLocation|Získá nebo nastaví (String)|Adresář, který obsahuje šablony projektů uživatele.|
|ProjectItemTemplatesLocation|Získá nebo nastaví (String)|Adresář, který obsahuje šablon položek uživatele.|
|DefaultBehaviorForStartupProjects|Získá nebo nastaví (String)||
|MSBuildOutputVerbosity|Získá nebo nastaví (String)|Určuje úroveň podrobností pro výstup sestavení.|

## <a name="startup"></a>Třída pro spuštění
 `DTE.Properties("Environment", "Startup")`

|Název položky vlastnosti|Hodnota|Popis|
| - |-----------|-----------------|
|OnStartUp|Get/Set (Enum)|Akce se má provést při spuštění z <xref:EnvDTE.vsStartUp>, s hodnotami 0 až 5:<br /><br /> -0: Otevřete domovskou stránku<br />-1: načtení posledního načtení řešení<br />-2: Zobrazit **otevřít projekt** dialogové okno<br />-3: zobrazení **nový projekt** dialogové okno<br />-4: Zobrazit prázdné prostředí<br />-5: zobrazit úvodní stránku|
|StartPageRSSUrl|Získá nebo nastaví (String)|Adresa URL pro informační kanál RSS informačního kanálu, který se používá při spuštění.|
|StartPageRefreshDownloadedContent|Get/Set (Boolean)|Úvodní stránka se aktualizuje po každé průchodu intervalu zadaném ve StartPageRefreshInterval.|
|StartPageRefreshInterval|Získá nebo nastaví (krátký)|Interval v minutách, chcete-li aktualizovat úvodní stránku.|

## <a name="tasklist"></a>Seznamu úkolů
 `DTE.Properties("Environment", "TaskList")`

|Název položky vlastnosti|Hodnota|Popis|
| - |-----------|-----------------|
|ConfirmTaskDeletion|Get/Set (Boolean)|Určuje, zda potvrzovací okno se zobrazí při odstraňování úlohy **seznamu úkolů**.|
|WarnOnAddingHiddenItem|Get/Set (Boolean)|Určuje, zda se zobrazí upozornění při přidávání uživatele úlohu, která se nezobrazí.|
|DontShowFilePaths|Get/Set (Boolean)|Určuje, jestli se má zobrazit celé cesty souborů v seznamu úkolů.|
|CommentTokens|SafeArray|Vrátí pole SafeArray komentářů k tomuto tokenu hodnoty. Každý obsahuje pole, `Name` (řetězec) a `Priority` (<xref:EnvDTE.vsTaskPriority>, vysoká, střední nebo nízká).|

## <a name="web-browser"></a>Webový prohlížeč
 `DTE.Properties("Environment", "WebBrowser")`

|Název položky vlastnosti|Hodnota|Popis|
| - |-----------|-----------------|
|Domovská stránka|Získá nebo nastaví (String)|Představuje adresu URL domovské stránky.|
|SearchPage|Získá nebo nastaví (String)|Představuje adresu URL stránky vyhledávání.|
|ViewSourceIn|Get/Set (Enum)|<xref:EnvDTE.vsBrowserViewSource> (Externí zdroj, návrh,).|
|ViewSourceExternalProgram|Získá nebo nastaví (String)|Cesta v prohlížeči externího zdroje.|

## <a name="see-also"></a>Viz také

- [Řízení nastavení možností](https://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)
- [Určování názvů položky vlastností na stránkách možností](https://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)
- [Stránka Možnosti, vlastnosti uzlu Písma a barvy](../../ide/reference/options-page-fonts-and-colors-node-properties.md)
- [Stránka Možnosti, vlastnosti uzlu Textový editor](../../ide/reference/options-page-text-editor-node-properties.md)
- [Prostředí, dialogové okno Možnosti](../../ide/reference/environment-options-dialog-box.md)