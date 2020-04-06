---
title: Registrace typu projektu | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 05ac1f393632934f193f5f4efaaf9e5459ffbb14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705873"
---
# <a name="registering-a-project-type"></a>Registrace typu projektu
Při vytváření nového typu projektu je nutné [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vytvořit položky registru, které umožní rozpoznat typ projektu a pracovat s ním. Tyto položky registru obvykle vytváříte pomocí souboru skriptu registru (.rgs).

 V níže uvedeném příkladu příkazy z registru poskytují výchozí cesty a data, kde je to možné, následované tabulkou obsahující položky ze skriptu registru pro každý příkaz. Tabulky obsahují položky skriptu a další informace o příkazech.

> [!NOTE]
> Následující informace o registru mají být příkladem typu a účelů položek ve skriptech registru, které budete zapisovat za účelem registrace typu projektu. Skutečné položky a jejich použití se mohou lišit v závislosti na konkrétních požadavcích typu projektu. Měli byste zkontrolovat vzorky k dispozici najít ten, který se velmi podobá typu projektu, který vyvíjíte a zkontrolujte skript registru pro tuto ukázku.

 Následující příklady jsou z HKEY_CLASSES_ROOT.

## <a name="example"></a>Příklad

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

|Name (Název)|Typ|Data|Popis|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrjFile`|Název a popis souborů typu projektu, které mají příponu .figp.|
|`Content Type`|REG_SZ|`Text/plain`|Typ obsahu pro soubory projektu.|
|`NullFile`|REG_SZ|`Null`||
|`@`|REG_SZ|`%MODULE%,-206`|Výchozí ikona použitá pro projekt tohoto typu. Příkaz %MODULE% je dokončen v registru do výchozího umístění typu dll projektu.|
|`@`|REG_SZ|`&Open in Visual Studio`|Výchozí aplikace, ve které bude tento typ projektu otevřen.|
|`@`|REG_SZ|`devenv.exe "%1"`|Výchozí příkaz, který bude spuštěn při otevření projektu tohoto typu.|

 Následující příklady jsou z HKEY_LOCAL_MACHINE a jsou umístěny v registru pod klíčem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages].

## <a name="example"></a>Příklad

```
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)
   @="FigPrj Project Package"
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"
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

|Name (Název)|Typ|Data|Popis|
|----------|----------|----------|-----------------|
|`@`(Výchozí)|REG_SZ|`FigPrj Project VSPackage`|Lokalizovatelný název tohoto registrovaného balíčku VSPackage (typ projektu).|
|`InprocServer32`|REG_SZ|`%MODULE%`|Cesta typu dll projektu. IDE načte tuto knihovnu DLL a předá Identifikátor CLSID v balíčku VSPackage, `DllGetClassObject` aby se objekt dostal <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> ke konstrukci. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|
|`CompanyName`|REG_SZ|`Microsoft`|Název společnosti, která vyvinula typ projektu.|
|`ProductName`|REG_SZ|`Figure Project Sample`|Název typu projektu.|
|`ProductVersion`|REG_SZ|`9.0`|Číslo verze verze verze typu projektu.|
|`MinEdition`|REG_SZ|`professional`|Vydání VSPackage je registrována.|
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Klíč načítání balíčku pro projekt VSPackage. Klíč je ověřen při načtení projektu po spuštění prostředí.|
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Název souboru satelitní dll, který obsahuje lokalizované zdroje pro typ projektu.|
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Cesta satelitní dll.|
|`FigProjectsEvents`|REG_SZ|Viz příkaz pro hodnotu.|Určuje textový řetězec vrácený pro tuto událost automatizace.|
|`FigProjectItemsEvents`|REG_SZ|Viz příkaz pro hodnotu.|Určuje textový řetězec vrácený pro tuto událost automatizace.|

 Všechny následující příklady jsou umístěny v registru pod klíčem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example"></a>Příklad

```
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)
   @="FigPrj Project"
   "DisplayName"="#2"
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"
   "DisplayProjectFileExtensions"="#3"
   "PossibleProjectExtensions"="figp"
   "DefaultProjectExtension"=".figp"
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)
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
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|Name (Název)|Typ|Data|Popis|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrj Project`|Výchozí název projektů tohoto typu.|
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|ID prostředku názvu, který má být načten ze satelitní dll registrované v části Balíčky.|
|`Package`|REG_SZ|`%CLSID_Package%`|ID třídy VSPackage registrované v rámci packages.|
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Výchozí cesta k souborům šablony projektu Jedná se o soubory zobrazené šablonou Nový projekt.|
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Výchozí cesta k souborům šablony položky projektu. Jedná se o soubory zobrazené šablonou Přidat novou položku.|
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Umožňuje ide implementovat dialogové okno **Otevřít.**|
|`PossibleProjectExtensions`|REG_SZ|`figp`|Používá ide k určení, zda je otevřený projekt zpracován tento typ projektu (factory projektu). Formát pro více než jednu položku je seznam oddělený středníkem. Například "vdproj;vdp".|
|`DefaultProjectExtension`|REG_SZ|`.figp`|Používá ide jako výchozí příponu názvu souboru pro operaci Uložit jako.|
|`Filter Settings`|REG_DWORD|Různé, viz příkazy a komentáře následující tabulka.|Tato nastavení slouží k nastavení různých filtrů pro zobrazení souborů v dialogových oknech ui.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|ID prostředku pro přidání šablon položek.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Cesta k položkám projektu zobrazeným v dialogovém okně pro šablonu **Přidat novou položku**|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Určuje pořadí řazení souborů zobrazených v dialogovém okně **Přidat novou položku** v uzlu stromu.|

 V následující tabulce jsou uvedeny možnosti filtrů dostupné v předchozím segmentu kódu.

|Možnost filtru|Popis|
|-------------------|-----------------|
|`CommonFindFilesFilter`|Označuje, že filtr je jedním z běžných filtrů v dialogovém okně **Najít v souborech.** Běžné filtry jsou uvedeny v seznamu filtrů před filtry, které nejsou označeny jako běžné.|
|`CommonOpenFilesFilter`|Označuje, že filtr je jedním z běžných filtrů v dialogovém okně **Otevřít soubor.** Běžné filtry jsou uvedeny v seznamu filtrů před filtry, které nejsou označeny jako běžné.|
|`FindInFilesFilter`|Označuje, že filtr bude jedním z filtrů v dialogovém okně **Najít v souborech** a bude uveden za běžnými filtry.|
|`NotOpenFileFilter`|Označuje, že filtr nebude použit v dialogovém okně **Otevřít soubor.**|
|`NotAddExistingItemFilter`|Označuje, že filtr nebude použit v dialogovém okně Přidat **existující položku.**|

 Ve výchozím nastavení, pokud filtr nemá nastaven jeden nebo více těchto příznaků, použije se filtr v dialogovém okně **Přidat existující položku** a v dialogovém okně **Otevřít soubor** po uvedení běžných filtrů. Filtr se nepoužívá v dialogovém okně **Najít v souborech.**

 Všechny následující příklady jsou umístěny v registru pod klíčem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example"></a>Příklad

```
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Name (Název)|Typ|Data|Popis|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|ID zdroje pro šablony nového projektu|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Výchozí cesta pro projekty registrovaného typu projektu.|
|`SortPriority`|REG_DWORD|`41 (x29)`|Nastaví pořadí řazení projektů zobrazených v dialogovém okně Průvodce novými projekty.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 označuje, že projekty tohoto typu jsou zobrazeny pouze v dialogovém okně Nový projekt.|

 Všechny následující příklady jsou umístěny v registru pod klíčem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example"></a>Příklad

```
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)
   @="Miscellaneous Files Project"
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1
                                 (CLSID for Figures Project projects)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|Name (Název)|Typ|Data|Popis|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|Žádný|Výchozí hodnota, která označuje, že následující položky jsou pro položky projektů různé soubory.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Hodnota ID prostředku pro soubory předlohy Přidat nové položky|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Výchozí cesta k položkám, které se zobrazí v dialogovém okně **Přidat novou položku.**|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Vytvoří pořadí řazení pro zobrazení v uzlu stromu dialogového okna **Přidat novou položku.**|

 Následující příklad je umístěn v registru pod klíčem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menu].

## <a name="example"></a>Příklad

```
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"
```

 Položka nabídky odkazuje ide na prostředek použitý k načtení informací o nabídce. Po sloučení těchto dat do databáze nabídky bude stejný klíč přidán do části MenusMerged v registru. VSPackage by neměl upravovat nic v části MenusMerged přímo. V poli Data v následující tabulce jsou tři pole oddělená čárkou. První pole identifikuje úplnou cestu k souboru prostředků nabídky:

- Pokud je první pole vynecháno, zdroj nabídky je načten ze satelitní dll označené identifikátorem GUID balíčku VSPackage.

  Druhé pole identifikuje ID zdroje nabídky typu CTMENU:

- Pokud je zadáno ID prostředku a cesta k souboru je dodávána prvním parametrem, je prostředek nabídky načten z úplné cesty k souboru.

- Pokud je k dispozici ID prostředku, ale cesta k souboru není, je prostředek nabídky načten ze satelitní dll.

- Pokud je k dispozici úplná cesta k souboru a ID prostředku vynecháno, očekává se, že načtení souboru bude soubor CTO.

  Poslední pole identifikuje číslo verze zdroje CTMENU. Nabídku můžete znovu sloučit změnou čísla verze.

|Name (Název)|Typ|Data|Popis|
|----------|----------|----------|-----------------|
|%CLSID_Package %|REG_SZ|`,1000,1`|Prostředek k načtení informací o nabídce.|

 Všechny následující příklady jsou umístěny v registru pod klíčem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates].

```
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Name (Název)|Typ|Data|Popis|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Hodnota ID zdroje pro šablony projektu Nový projekt|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Výchozí cesta adresáře Nové projekty. Položky v tomto adresáři se zobrazí v dialogovém okně **Průvodce novým projektem.**|
|`SortPriority`|REG_DWORD|`41 (x29)`|Stanoví pořadí, ve kterém budou projekty zobrazeny v uzlu stromu dialogového okna **Nový projekt.**|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 označuje, že projekty tohoto typu jsou zobrazeny pouze v dialogovém okně **Nový projekt.**|

 Následující příklad je umístěn v registru pod klíčem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts].

```
\FiguresProductSample
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "UseInterface"=dword:00000001
```

|Name (Název)|Typ|Data|Popis|
|----------|----------|----------|-----------------|
|`Package`|REG_SZ|`%CLSID_Package%`|ID třídy registrovaného balíčku VSPackage.|
|`UseInterface`|REG_DWORD|`1`|1 označuje, že ui bude použit k interakci s tímto projektem. 0 označuje, že neexistuje žádné rozhraní uživatelského rozhraní.|

 Soubory.vsz, které řídí nové typy projektů často obsahují RELATIVE_PATH položku. Tato cesta je relativní vzhledem k cestě zadané v položce \ProductDir typu projektu v následujícím klíči instalace:

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup

 Například šablony projektů Enterprise Frameworks přidávají následující položky registru:

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\

 To znamená, že pokud do souboru .vsz zahrnete položku PROJECT_TYPE=EF, prostředí najde vaše soubory .vsz v dříve zadaném adresáři ProductDir.

## <a name="see-also"></a>Viz také
- [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Prvky modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)
- [Vytváření instancí projektu pomocí objektů pro vytváření projektů](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
