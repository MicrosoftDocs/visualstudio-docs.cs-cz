---
title: Stránka možnosti, vlastnosti uzlu prostředí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio], controlling Tools Options
- Tools Options settings, Environment node properties
ms.assetid: 26dca41f-91fc-4ca7-9103-3da402baa1d5
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b45716db44dcc316ec60604aa0411e6498797ae0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595017"
---
# <a name="options-page-environment-node-properties"></a>Stránka Možnosti, vlastnosti uzlu prostředí
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tento dokument popisuje stránky (nebo kolekce vlastností), které jsou spojeny s kategorií **prostředí** , `DTE.Properties("Environment", <Property Page>)`dialogového okna **Možnosti** . Název každého dílčího oddílu je volání, které se používá pro přístup k kolekci vlastností a tabulka v každém pododdílu obsahuje seznam vlastností v kolekci.

## <a name="general"></a>Obecné
 `DTE.Properties("Environment", "General")`

|Název položky vlastnosti|Hodnota|Popis|
|------------------------|-----------|-----------------|
|ShowStatusBar|Get/Set (Boolean)|Určuje, zda je stavový řádek viditelný.|
|WindowMenuContainsNItems|Získat nebo nastavit (krátký)|Určuje způsob, jakým jsou okna dokumentu obsažena v dolní části nabídky systému Windows.|
|MRUListContainsNItems|Získat nebo nastavit (krátký)|Určuje, kolik souborů se zobrazí v podnabídce Naposledy použité.|
|Animace|Get/Set (Boolean)|Určuje, zda integrované vývojové prostředí (IDE) používá animaci ve stavovém řádku.|
|AnimationSpeed|Získat nebo nastavit (krátký)||
|AutoAdjustExperience|Get/Set (Boolean)|Automaticky upraví vizuální prostředí v závislosti na výkonu klienta.|
|RichClientExperienceOptions|Get/Set (Enum)|Umožňuje bohatě vizuální prostředí klienta s hodnotami v <xref:EnvDTE100.vsRichClientExperienceOptions>.|
|CloseButtonActiveTabOnly|Get/Set (Boolean)|Určuje, zda je tlačítko **Zavřít** zobrazeno pouze na aktivní kartě.|
|AutohidePinActiveTabOnly|Get/Set (Boolean)|Určuje, zda má tlačítko pro **automatické skrývání** vliv pouze na aktivní kartu.|

## <a name="add-inmacros-security"></a>Zabezpečení doplňků/maker
 `DTE.Properties("Environment", "AddinMacrosSecurity")`

|Název položky vlastnosti|Hodnota|Popis|
|------------------------|-----------|-----------------|
|MacrosEnabled|Get/Set (Boolean)|Umožňuje spuštění maker.|
|AddinsEnabled|Get/Set (Boolean)|Umožňuje načíst doplňky.|
|LoadAddinsFromTheWeb|Get/Set (Boolean)|Umožňuje načíst doplňky z adresy URL na webu.|

## <a name="documents"></a>Dokumenty
 `DTE.Properties("Environment", "Documents")`

|Název položky vlastnosti|Hodnota|Popis|
|------------------------|-----------|-----------------|
|ReuseSavedActiveDocWindow|Get/Set (Boolean)|Určuje, zda otevírání nového souboru znovu použije aktuální okno dokumentu, pokud je aktuální dokument uložen. `false` znamená vždy otevřít nové okno dokumentu pro každý otevřený dokument.|
|DetectFileChangesOutsideIDE|Get/Set (Boolean)|Určuje, zda prostředí automaticky znovu načte soubory otevřené v integrovaném vývojovém prostředí (IDE), když operační systém upozorní rozhraní IDE na to, že soubory byly na disku změněny.|
|AutoloadExternalChanges|Get/Set (Boolean)|Určuje, zda se při změně otevřeného dokumentu automaticky znovu načte upravený soubor a otevře se soubor s otevřenými externími úpravami. Pokud je otevřený dokument upraven a tato vlastnost je `true`, pak rozhraní IDE vyzve, jako by byla tato vlastnost `false`.|
|InitializeOpenFileFromCurrentDocument|Get/Set (Boolean)|Určuje, zda <xref:EnvDTE.DTEClass.OpenFile%2A> příkaz vyhodnotí název adresáře a souboru z posledního aktivního dokumentu nebo z posledního místa, v němž jste otevřeli soubor.|
|MiscFilesProjectSavesLastNItems|Získat nebo nastavit (krátký)|Určuje, kolik souborů soubory aplikace různé soubory zaznamená. V důsledku toho vidíte, co jste nedávno otevřeli jako různé soubory na disku při dalším použití rozhraní IDE.|
|ShowMiscFilesProject|Get/Set (Boolean)|Určuje, zda je zobrazen projekt různé soubory.|
|CheckForConsisentLineEndings|Get/Set (Boolean)|Kontroluje konzistenci konců řádků při zatížení souboru.|
|SaveDocsAsUnicodeWhenDataLoss|Get/Set (Boolean)|Ukládá dokumenty jako znakovou sadu Unicode, pokud data nelze uložit ve znakové stránce.|
|DontShowGlobalUndoChangeLossDialog|Get/Set (Boolean)|Zobrazí upozornění, pokud bude globální akce zpět upravovat ostatní upravené soubory.|
|AllowEditingReadOnlyFiles|Get/Set (Boolean)|Umožňuje upravovat soubory jen pro čtení, ale při pokusu o jejich uložení dejte pozor na upozornění.|
|DocumentDockPreference|Get/Set (Enum)|<xref:EnvDTE100.vsDocumentDockPreferenceOptions>. Pozice na kartách, do kterých se má vložit otevřený dokument|

## <a name="extension-manager"></a>správce rozšíření
 `DTE.Properties("Environment", "ExtensionManager")`

|Název položky vlastnosti|Hodnota|Popis|
|------------------------|-----------|-----------------|
|EnableAdminExtensions|Get/Set (Boolean)|Načte rozšíření pro jednotlivé uživatele, když je aplikace Visual Studio spuštěna v rámci pověření správce. Po změně této hodnoty je nutné restartovat aplikaci Visual Studio.|
|EnableOnline|Get/Set (Boolean)|Umožňuje přístup k rozšířením v galerii sady Visual Studio.|
|AutomaticallyCheckForUpdates|Get/Set (Boolean)|Automaticky zjišťuje aktualizace nainstalovaných rozšíření.|

## <a name="find-and-replace"></a>hledání a nahrazování
 `DTE.Properties("Environment", "FindAndReplace")`

|Název položky vlastnosti|Hodnota|Popis|
|------------------------|-----------|-----------------|
|ShowWarningMessages|Get/Set (Boolean)|Zobrazí varovné zprávy.|
|InitializeFromEditor|Get/Set (Boolean)|Automaticky vyplní pole **Najít** s textem z editoru.|
|ShowMessageBoxes|Get/Set (Boolean)|Zobrazí informační zprávy.|
|HideWindowsAfterMatchFromQuickFindReplace|Get/Set (Boolean)|Skryje okno **Najít a nahradit** po nalezení shody pomocí **rychlého hledání** nebo **rychlého nahrazení**.|

## <a name="import-and-export-settings"></a>Nastavení importu a exportu
 `DTE.Properties("Environment", "Import and Export Settings")`

|Název položky vlastnosti|Hodnota|Popis|
|------------------------|-----------|-----------------|
|TrackTeamSettings|Get/Set (Boolean)|Používá nastavení v souboru určeném parametrem TeamSettingsFile.|
|TeamSettingsFile|Get/Set (String)|Název souboru, který obsahuje nastavení týmu.|
|AutoSaveFile|Get/Set (String)|Název souboru, do kterého se budou automaticky ukládat uživatelská nastavení|

## <a name="international-settings"></a>Mezinárodní nastavení
 `DTE.Properties("Environment", "International")`

|Název položky vlastnosti|Hodnota|Popis|
|------------------------|-----------|-----------------|
|Jazyk|Get/Set (String)|Hodnota LCID pro aktuální jazyk sady Visual Studio.|

## <a name="keyboard"></a>Klávesnice
 `DTE.Properties("Environment", "Keyboard")`

|Název položky vlastnosti|Hodnota|Popis|
|------------------------|-----------|-----------------|
|Schéma|Get/Set (String)|Vrátí řetězec, který obsahuje předdefinované schéma, řetězec obsahující úplnou cestu souboru. VSK, který je načten, nebo "(výchozí)", pokud není načten soubor. VSK.|

## <a name="projects-and-solution"></a>Projekty a řešení
 `DTE.Properties("Environment", "ProjectsAndSolution")`

|Název položky vlastnosti|Hodnota|Popis|
|------------------------|-----------|-----------------|
|OnRunOrPreview|Get/Set (String)|Určuje, zda IDE uloží vše před zobrazením náhledu nebo spuštěním sestaveného projektu.|
|ProjectsLocation|Get/Set (String)|Určuje výchozí adresář, do kterého se v dialogovém okně **Přidat projekt** ukládají nové projekty.|
|ShowOutputWindowBeforeBuild|Get/Set (Boolean)|Určuje, zda se při spuštění sestavení zobrazí okno **výstup** .|
|ShowTaskListAfterBuild|Get/Set (Boolean)|Určuje, zda neúspěšná operace sestavení po dokončení sestavení zobrazí **seznam úkolů** .|
|TrackFileSelectionInExplorer|Get/Set (Boolean)|Určuje, zda je aktuální položka sledována v **Průzkumník řešení**.|
|AlwaysShowSolutionNode|Get/Set (Boolean)|Určuje, zda je zobrazen uzel řešení.|
|OnlySaveStartupProjectsAndDependencies|Get/Set (Boolean)|Určuje, zda jsou operace ukládání omezeny na spouštěné projekty a jejich závislé soubory.|
|ShowAdvancedBuildConfigurations|Get/Set (Boolean)|Určuje, zda jsou zobrazeny rozšířené konfigurace sestavení.|
|ConcurrentBuilds|Get/Set (String)|Určuje maximální počet paralelních sestavení projektu, které mohou nastat.|
|SaveNewProjects|Get/Set (Boolean)|Určuje, zda jsou po vytvoření automaticky uloženy nové projekty.|
|PromptForRenameSymbol|Get/Set (Boolean)|Určuje, zda se má při přejmenování souborů zobrazovat výzva k zadání symbolického názvu.|
|OnRunWhenErrors|Get/Set (Enum)|Určuje chování při spuštění, když se sestavení dokončilo s chybami.|
|OnRunWhenOutOfDate|Get/Set (Enum)|Určuje chování, které se spustí, když projekt není aktuální.|
|ProjectTemplatesLocation|Get/Set (String)|Adresář, který obsahuje šablony projektu uživatele.|
|ProjectItemTemplatesLocation|Get/Set (String)|Adresář, který obsahuje šablony uživatelských položek.|
|DefaultBehaviorForStartupProjects|Get/Set (String)||
|MSBuildOutputVerbosity|Get/Set (String)|Určuje úroveň podrobností pro výstup sestavení.|

## <a name="startup"></a>Třída pro spuštění
 `DTE.Properties("Environment", "Startup")`

|Název položky vlastnosti|Hodnota|Popis|
|------------------------|-----------|-----------------|
|OnStartUp|Get/Set (Enum)|Akce, která se má provést při spuštění, od <xref:EnvDTE.vsStartUp>s hodnotami od 0 do 5:<br /><br /> -0: otevřít domovskou stránku<br />-1: načtení posledního načteného řešení<br />-2: zobrazení dialogového okna **Otevřít projekt**<br />-3: zobrazení dialogového okna **Nový projekt**<br />-4: zobrazení prázdného prostředí<br />-5: Zobrazit úvodní stránku|
|StartPageRSSUrl|Get/Set (String)|Adresa URL informačního kanálu RSS, který se používá při spuštění.|
|StartPageRefreshDownloadedContent|Get/Set (Boolean)|Aktualizuje úvodní stránku po každém průchodu intervalu zadaného v StartPageRefreshInterval.|
|StartPageRefreshInterval|Získat nebo nastavit (krátký)|Interval obnovování úvodní stránky v minutách|

## <a name="tasklist"></a>Seznamu úkolů
 `DTE.Properties("Environment", "TaskList")`

|Název položky vlastnosti|Hodnota|Popis|
|------------------------|-----------|-----------------|
|ConfirmTaskDeletion|Get/Set (Boolean)|Určuje, zda se při odstraňování úloh z **seznam úkolů**Zobrazuje potvrzovací pole.|
|WarnOnAddingHiddenItem|Get/Set (Boolean)|Určuje, zda se zobrazí upozornění při přidávání úkolu uživatele, který nebude zobrazen.|
|DontShowFilePaths|Get/Set (Boolean)|Určuje, zda se mají v Seznam úkolů zobrazovat úplné cesty k souborům.|
|CommentTokens|SafeArray|Vrátí hodnotu SafeArray hodnot tokenu komentáře. Každé má pole, `Name` (String) a `Priority` (<xref:EnvDTE.vsTaskPriority>, vysoká, střední nebo nízká).|

## <a name="web-browser"></a>Webový prohlížeč
 `DTE.Properties("Environment", "WebBrowser")`

|Název položky vlastnosti|Hodnota|Popis|
|------------------------|-----------|-----------------|
|Domovské stránky|Get/Set (String)|Představuje adresu URL domovské stránky.|
|SearchPage|Get/Set (String)|Představuje adresu URL vyhledávací stránky.|
|ViewSourceIn|Get/Set (Enum)|<xref:EnvDTE.vsBrowserViewSource> (zdroj, návrh, externí).|
|ViewSourceExternalProgram|Get/Set (String)|Cesta k externímu prohlížeči zdrojového kódu.|

## <a name="see-also"></a>Viz také

- [Řízení nastavení možností](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d)
- [Určení názvů položek vlastností na stránkách možností](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)
- [Stránka Možnosti, vlastnosti uzlu Písma a barvy](../../ide/reference/options-page-fonts-and-colors-node-properties.md)
- [Stránka Možnosti, vlastnosti uzlu Textový editor](../../ide/reference/options-page-text-editor-node-properties.md)
- [Prostředí, dialogové okno Možnosti](../../ide/reference/environment-options-dialog-box.md)
