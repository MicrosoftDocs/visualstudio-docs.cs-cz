---
title: Registrace typu projektu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7267060f2207b0842885dc3001c3926874be30a9
ms.sourcegitcommit: 023f52f10fb91850824558478cbfd2ec965054f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94407728"
---
# <a name="registering-a-project-type"></a>Registrace typu projektu
Při vytváření nového typu projektu je nutné vytvořit položky registru, které umožňují [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rozpoznat a pracovat s typem projektu. Tyto položky registru obvykle vytváříte pomocí souboru skriptu registru (. rgs).

 V následujícím příkladu příkazy z registru poskytují výchozí cesty a data, za kterými následuje tabulka, která obsahuje položky ze skriptu registru pro každý příkaz. Tabulky poskytují položky skriptu a další informace o příkazech.

> [!NOTE]
> Následující informace registru mají být příkladem typu a účelu záznamů v skriptech registru, které budete zapisují k registraci typu projektu. Vaše skutečné položky a jejich použití se mohou lišit v závislosti na konkrétních požadavcích vašeho typu projektu. Měli byste si projít ukázky, které jsou k dispozici, a najít je, který se přesně podobá typu projektu, který vyvíjíte, a pak zkontrolovat skript registru pro tuto ukázku.

 Následující příklady jsou z HKEY_CLASSES_ROOT.

## <a name="example-1"></a>Příklad 1

```
\.figp
   @="FigPrjFile"
   "Content Type"="text/plain"
\.figp\ShellNew
   "NullFile"=""
\FigPrjFile
   @="Figure Project File"
\DefaultIcon
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"
\shell\open
   @="&Open in Visual Studio"
\shell\open\command
   @="devenv.exe \"%1\""
```

|Název|Typ|Data|Popis|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrjFile`|Název a popis souborů typu projektu, které mají příponu. figp.|
|`Content Type`|REG_SZ|`Text/plain`|Typ obsahu pro soubory projektu.|
|`NullFile`|REG_SZ|`Null`||
|`@`|REG_SZ|`%MODULE%,-206`|Výchozí ikona použitá pro projekt tohoto typu Příkaz% MODULE% byl dokončen v registru do výchozího umístění knihovny DLL typu projektu.|
|`@`|REG_SZ|`&Open in Visual Studio`|Výchozí aplikace, ve které bude tento typ projektu otevřen.|
|`@`|REG_SZ|`devenv.exe "%1"`|Výchozí příkaz, který se spustí, když se otevře projekt tohoto typu.|

 Následující příklady jsou z HKEY_LOCAL_MACHINE a jsou umístěny v registru pod klíčem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages].

## <a name="example-2"></a>Příklad 2

```
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)
   @="FigPrj Project Package"
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"
   "CompanyName"="Microsoft"
   "ProductName"="Figure Project Sample"
   "ProductVersion"="9.0"
   "MinEdition"="professional"
   "ID"=dword:00000001
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL
   "DllName"="FigPrjUI.dll"
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation
   "FigProjects"=""
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"
```

|Název|Typ|Data|Popis|
|----------|----------|----------|-----------------|
|`@` Výchozí|REG_SZ|`FigPrj Project VSPackage`|Lokalizovatelný název tohoto registrovaného VSPackage (typ projektu)|
|`InprocServer32`|REG_SZ|`%MODULE%`|Cesta k souboru DLL typu projektu. Rozhraní IDE načte tuto knihovnu DLL a předá identifikátor CLSID VSPackage pro `DllGetClassObject` <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> sestavení <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> objektu.|
|`CompanyName`|REG_SZ|`Microsoft`|Název společnosti, která vyvinula typ projektu.|
|`ProductName`|REG_SZ|`Figure Project Sample`|Název typu projektu|
|`ProductVersion`|REG_SZ|`9.0`|Číslo verze typu projektu.|
|`MinEdition`|REG_SZ|`professional`|Registrovaná edice sady VSPackage.|
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Načtený klíč balíčku pro projekt VSPackage projektu. Klíč se ověří při načtení projektu po spuštění prostředí.|
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Název souboru satelitní knihovny DLL, která obsahuje lokalizované prostředky pro typ projektu.|
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Cesta k satelitní knihovně DLL.|
|`FigProjectsEvents`|REG_SZ|Viz příkaz pro hodnotu.|Určuje textový řetězec vrácený pro tuto událost automatizace.|
|`FigProjectItemsEvents`|REG_SZ|Viz příkaz pro hodnotu.|Určuje textový řetězec vrácený pro tuto událost automatizace.|

 Všechny následující příklady jsou umístěné v registru pod klíčem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example-3"></a>Příklad 3

```
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)
   @="FigPrj Project"
   "DisplayName"="#2"
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"
   "DisplayProjectFileExtensions"="#3"
   "PossibleProjectExtensions"="figp"
   "DefaultProjectExtension"=".figp"
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)
   @="#4"
   "CommonOpenFilesFilter"=dword:00000000
   "CommonFindFilesFilter"=dword:00000000
   "NotAddExistingItemFilter"=dword:00000000
   "FindInFilesFilter"=dword:00000000
   "NotOpenFileFilter"=dword:00000000
   "SortPriority"=dword:000003e8
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2
      (Folder 2 contains settings for Find in Files filters.)
   @="#5"
   "CommonOpenFilesFilter"=dword:00000000
   "CommonFindFilesFilter"=dword:00000000
   "NotAddExistingItemFilter"=dword:00000001
   "FindInFilesFilter"=dword:00000001
   "NotOpenFileFilter"=dword:00000000
   "SortPriority"=dword:000003e8
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|Název|Typ|Data|Popis|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrj Project`|Výchozí název projektů tohoto typu.|
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|ID prostředku pro název, který se má načíst z satelitní knihovny DLL registrované v balíčcích|
|`Package`|REG_SZ|`%CLSID_Package%`|ID třídy VSPackage registrované v balíčcích|
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Výchozí cesta souborů šablon projektu. Jedná se o soubory zobrazené novou šablonou projektu.|
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Výchozí cesta souborů šablony položky projektu Jedná se o soubory zobrazované šablonou přidat novou položku.|
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Povolí rozhraní IDE implementovat dialogové okno **otevřít** .|
|`PossibleProjectExtensions`|REG_SZ|`figp`|Rozhraní IDE používá k určení, zda je otevřený projekt zpracováván tímto typem projektu (objekt pro vytváření projektu). Formát pro více než jednu položku je seznam oddělený středníky. Například "vdproj; VDP".|
|`DefaultProjectExtension`|REG_SZ|`.figp`|Používá se rozhraním IDE jako výchozí přípona názvu souboru pro operaci uložit jako.|
|`Filter Settings`|REG_DWORD|Různé, další informace najdete v tématu příkazy a komentáře v následující tabulce.|Tato nastavení slouží k nastavení různých filtrů pro zobrazení souborů v dialogových oknech uživatelského rozhraní.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|ID prostředku pro šablony pro přidání položek|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Cesta k položkám projektu zobrazeným v dialogovém okně pro šablonu **Přidat novou položku** .|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Určuje pořadí řazení v uzlu stromu souborů zobrazených v dialogovém okně **Přidat novou položku** .|

 V následující tabulce jsou uvedeny možnosti filtrů, které jsou k dispozici v předchozím segmentu kódu.

|Možnost filtru|Popis|
|-------------------|-----------------|
|`CommonFindFilesFilter`|Označuje, že filtr je jedním z běžných filtrů v dialogovém okně **najít v souborech** . Společné filtry jsou uvedeny v seznamu filtru předtím, než filtry nejsou označeny jako společné.|
|`CommonOpenFilesFilter`|Označuje, že filtr je jedním z běžných filtrů v dialogovém okně **otevřít soubor** . Společné filtry jsou uvedeny v seznamu filtru předtím, než filtry nejsou označeny jako společné.|
|`FindInFilesFilter`|Označuje, že filtr bude jedním z filtrů v dialogovém okně **najít v souborech** a bude uveden po běžných filtrech.|
|`NotOpenFileFilter`|Označuje, že filtr nebude použit v dialogovém okně **otevřít soubor** .|
|`NotAddExistingItemFilter`|Označuje, že filtr nebude použit v dialogovém okně Přidat **existující položku** .|

 Ve výchozím nastavení platí, že pokud filtr nemá jednu nebo více těchto příznaků nastaven, použije se filtr v dialogovém okně **Přidat existující položku** a otevře se dialogové okno **otevřít soubor** po uvedení běžných filtrů na seznam. Filtr se nepoužívá v dialogovém okně **najít v souborech** .

 Všechny následující příklady jsou umístěné v registru pod klíčem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example-4"></a>Příklad 4

```
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Název|Typ|Data|Popis|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|ID prostředku pro nové šablony projektu|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Výchozí cesta pro projekty registrovaného typu projektu.|
|`SortPriority`|REG_DWORD|`41 (x29)`|Nastaví pořadí řazení projektů zobrazených v dialogovém okně Průvodce vytvořením projektu.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 označuje, že se projekty tohoto typu zobrazují pouze v dialogovém okně Nový projekt.|

 Všechny následující příklady jsou umístěné v registru pod klíčem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example-5"></a>Příklad 5

```
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)
   @="Miscellaneous Files Project"
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1
                                 (CLSID for Figures Project projects)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|Název|Typ|Data|Popis|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|Žádné|Výchozí hodnota, která označuje, že následující položky jsou pro položky projektů různých souborů.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Hodnota ID prostředku pro soubory šablon přidání nových položek.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Výchozí cesta k položkám, které se zobrazí v dialogovém okně **Přidat novou položku** .|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Vytvoří pořadí řazení pro zobrazení v uzlu strom dialogového okna **Přidat novou položku** .|

 Následující příklad je umístěný v registru pod klíčem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus].

## <a name="example-6"></a>Příklad 6

```
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"
```

 Položka nabídky odkazuje rozhraní IDE na prostředek použitý k načtení informací o nabídce. Pokud byla tato data sloučena do databáze nabídky, bude do oddílu MenusMerged v registru přidán stejný klíč. VSPackage by neměl upravovat cokoli v části MenusMerged přímo. V datovém poli v následující tabulce jsou tři pole oddělená čárkami. První pole určuje úplnou cestu k souboru prostředků nabídky:

- Pokud je první pole vynecháno, je prostředek nabídky načten z satelitní knihovny DLL identifikované identifikátorem GUID VSPackage.

  Druhé pole identifikuje ID prostředku nabídky pro typ CTMENU:

- Pokud je zadáno ID prostředku a cesta k souboru je poskytnuta prvním parametrem, je prostředek nabídky načten z úplné cesty k souboru.

- Pokud je zadáno ID prostředku, ale cesta k souboru není, je prostředek nabídky načten z satelitní knihovny DLL.

- Pokud je k dispozici úplná cesta k souboru a bylo vynecháno ID prostředku, je soubor, který má být načten, považován za soubor technický ředitel.

  Poslední pole určuje číslo verze pro prostředek CTMENU. Nabídku můžete znovu sloučit změnou čísla verze.

|Název|Typ|Data|Popis|
|----------|----------|----------|-----------------|
|% CLSID_Package%|REG_SZ|`,1000,1`|Prostředek, ze kterého mají být načteny informace nabídky.|

 Všechny následující příklady jsou umístěné v registru pod klíčem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates].

```
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Název|Typ|Data|Popis|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Hodnota ID prostředku pro prvky projekt pro nové šablony projektů|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Výchozí cesta k novému adresáři projektů Položky v tomto adresáři se zobrazí v dialogovém okně **Průvodce vytvořením projektu** .|
|`SortPriority`|REG_DWORD|`41 (x29)`|Určuje pořadí, ve kterém se budou projekty zobrazovat v uzlu strom v dialogovém okně **Nový projekt** .|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 označuje, že se projekty tohoto typu zobrazují pouze v dialogovém okně **Nový projekt** .|

 Následující příklad je umístěný v registru pod klíčem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts].

```
\FiguresProductSample
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "UseInterface"=dword:00000001
```

|Název|Typ|Data|Popis|
|----------|----------|----------|-----------------|
|`Package`|REG_SZ|`%CLSID_Package%`|ID třídy registrované sady VSPackage|
|`UseInterface`|REG_DWORD|`1`|1 označuje, že uživatelské rozhraní bude sloužit k interakci s tímto projektem. 0 znamená, že neexistuje žádné rozhraní uživatelského rozhraní.|

 Soubory. vsz, které řídí nové typy projektů, často obsahují položku RELATIVE_PATH. Tato cesta je relativní ke cestě zadané v položce \ProductDir typu projektu v následujícím instalačním klíči:

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup

 Například šablony projektů podnikových architektur přidávají následující položky registru:

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\

 To znamená, že pokud zahrnete do souboru. vsz položku PROJECT_TYPE = EF, prostředí nalezne vaše soubory. vsz v adresáři ProductDir, který jste zadali dříve.

## <a name="see-also"></a>Viz také
- [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Prvky modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)
- [Vytváření instancí projektu pomocí objektů pro vytváření projektů](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
