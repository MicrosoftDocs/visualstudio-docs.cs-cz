---
title: Registrace typu projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1839ed51b3bd8b26bd67583054fa142f5853a2de
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939680"
---
# <a name="registering-a-project-type"></a>Registrace typu projektu
Když vytvoříte nový typ projektu, je nutné vytvořit položky registru, které umožňují [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nerozpozná a nenahraje a pracovat s vašeho typu projektu. Tyto položky registru obvykle vytvoříte pomocí souboru registru skript (.rgs).  
  
 V následujícím příkladu příkazy z registru poskytují výchozí cesty a data kde je to možné, za nímž následuje tabulku, která obsahuje položky z registru skriptu příkazu for each. Tabulky poskytují položkami skriptu a další informace o dotazech.  
  
> [!NOTE]
>  Do registru následující informace slouží jako příklad typu a účely položky v registru skripty, které vás bude psaní registrace typu projektu. Skutečné položky a jejich použití se může lišit v závislosti na konkrétní požadavky na typu projektu. Zkontrolujte dostupných najít takový, který připomíná typ projektu, kterou vyvíjíte a pak zkontrolujte skript registru pro tuto ukázku.  
  
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
  
|Název|Typ|Data|Popis|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrjFile`|Název a popis projektu zadejte soubory, které mají .figp rozšíření.|  
|`Content Type`|REG_SZ|`Text/plain`|Typ obsahu pro soubory projektu.|  
|`NullFile`|REG_SZ|`Null`||  
|`@`|REG_SZ|`%MODULE%,-206`|Výchozí ikona použitá pro projekt tohoto typu. Příkaz % modulu % byla dokončena v registru do umístění výchozího typu projektu DLL.|  
|`@`|REG_SZ|`&Open in Visual Studio`|Výchozí aplikace, ve které se otevřou tento typ projektu.|  
|`@`|REG_SZ|`devenv.exe "%1"`|Výchozí příkaz, který se spustí při otevření projektu tohoto typu.|  
  
 Následující příklady jsou z HKEY_LOCAL_MACHINE a jsou umístěny v registru pod klíčem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages].  
  
## <a name="example"></a>Příklad  
  
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
|`@` (Výchozí)|REG_SZ|`FigPrj Project VSPackage`|Lokalizovatelný název registrované balíčku VSPackage (typ projektu).|  
|`InprocServer32`|REG_SZ|`%MODULE%`|Cesta k typu projektu DLL. Rozhraní IDE načte tuto knihovnu DLL a předává identifikátor CLSID VSPackage `DllGetClassObject` zobrazíte <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> k sestavení kompletních <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> objektu.|  
|`CompanyName`|REG_SZ|`Microsoft`|Název společnosti, který vyvinul typ projektu.|  
|`ProductName`|REG_SZ|`Figure Project Sample`|Název typu projektu.|  
|`ProductVersion`|REG_SZ|`9.0`|Číslo verze typu projektu release.|  
|`MinEdition`|REG_SZ|`professional`|Edice sady VSPackage registrována.|  
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Balíček načíst klíč projektu VSPackage. Klíč je ověřeno při načtení projektu po spuštění prostředí.|  
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Název souboru satelitní knihovny DLL obsahující lokalizované prostředky pro typ projektu.|  
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Cestu k satelitní knihovně DLL.|  
|`FigProjectsEvents`|REG_SZ|Naleznete v části prohlášení pro hodnotu.|Určuje textový řetězec pro tuto událost služby automation.|  
|`FigProjectItemsEvents`|REG_SZ|Naleznete v části prohlášení pro hodnotu.|Určuje textový řetězec pro tuto událost služby automation.|  
  
 Následující příklady jsou umístěny v registru pod klíčem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Příklad  
  
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
|`@`|REG_SZ|`FigPrj Project`|Výchozí název projektech tohoto typu.|  
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|ID prostředku, který se má načíst z satelitní knihovny DLL název zaregistrován balíčky.|  
|`Package`|REG_SZ|`%CLSID_Package%`|ID třídy sady VSPackage zaregistrován balíčky.|  
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Výchozí cesta souborů šablon projektu. Jsou to soubory nový projekt šablonou zobrazena.|  
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Výchozí cesta souboru šablony položky projektu. Jsou to soubory, přidat novou položku šablonou zobrazena.|  
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Umožňuje rozhraní IDE k implementaci **otevřít** dialogové okno.|  
|`PossibleProjectExtensions`|REG_SZ|`figp`|Integrované vývojové prostředí používané k určení, zda se otevření projektu se zpracovává souborem tento typ projektu (objekt pro vytváření projektu). Více než jedna položka formát je středníkem oddělený seznam. Například "vdproj; vdp".|  
|`DefaultProjectExtension`|REG_SZ|`.figp`|Integrovaným vývojovým prostředím používá jako výchozí přípona názvu souboru pro operace Uložit jako.|  
|`Filter Settings`|REG_DWORD|Různé, naleznete v tématu Příkazy a komentáře, následující tabulka.|Tato nastavení umožňují nastavit různé filtry pro zobrazení souborů v dialogových oknech uživatelského rozhraní.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|ID prostředku pro přidat položku šablony.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Cesta položky projektu zobrazí v dialogovém okně **přidat novou položku** šablony.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Určuje pořadí řazení v uzlu stromu soubory zobrazené v **přidat novou položku** dialogové okno.|  
  
 V následující tabulce jsou uvedeny filtry možnosti dostupné v předchozího segmentu kódu.  
  
|Možnost Filter|Popis|  
|-------------------|-----------------|  
|`CommonFindFilesFilter`|Označuje, že filtr je jedním z běžných filtry v **najít v souborech** dialogové okno. Běžné filtry jsou uvedeny v seznamu filtru před filtry nejsou označeny jako běžné.|  
|`CommonOpenFilesFilter`|Označuje, že filtr je jedním z běžných filtry v **otevřít soubor** dialogové okno. Běžné filtry jsou uvedeny v seznamu filtru před filtry nejsou označeny jako běžné.|  
|`FindInFilesFilter`|Označuje, že filtr bude jeden z filtrů v **najít v souborech** dialogové okno pole a zobrazí se po běžné filtry.|  
|`NotOpenFileFilter`|Označuje, že tento filtr se nepoužije v **otevřít soubor** dialogové okno.|  
|`NotAddExistingItemFilter`|Označuje, že tento filtr se nepoužije v přidáním **existující položku** dialogové okno.|  
  
 Ve výchozím nastavení, pokud filtr nemá jeden nebo více z těchto příznaků set, filtr je používán **přidat existující položku** dialogové okno a **otevřít soubor** dialogové okno po běžné filtry jsou k dispozici. Filtr se nepoužívá **najít v souborech** dialogové okno.  
  
 Následující příklady jsou umístěny v registru pod klíčem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Příklad  
  
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
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|ID prostředku pro nový projekt šablony.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Výchozí cesta pro projekty typu registrované projektu.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Nastaví řazení projektů se zobrazí v dialogovém okně Průvodce nové projekty.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|Hodnota 0 znamená, že tento typ projektů se zobrazí jenom v dialogovém okně Nový projekt.|  
  
 Následující příklady jsou umístěny v registru pod klíčem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Příklad  
  
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
|`@`|REG_SZ|Žádné|Výchozí hodnota, která označuje, že následující položky jsou pro různé soubory projektů položky.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Hodnota ID prostředku pro soubory šablon přidat nové položky.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Výchozí cesta položky, které se zobrazí v **přidat novou položku** dialogové okno.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Stanovuje pořadí řazení pro zobrazení v uzlu stromu **přidat novou položku** dialogové okno.|  
  
 V následujícím příkladu se nachází v registru pod klíčem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus].  
  
## <a name="example"></a>Příklad  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 Položka nabídky odkazuje na prostředek, který používá k načtení informací o nabídce integrovaného vývojového prostředí. Když tato data byly sloučeny do nabídky databáze, stejný klíč se přidají v části MenusMerged registru. Sady VSPackage neměli měnit nic části MenusMerged přímo. V poli Data v následující tabulce jsou tři čárkami oddělených pole. První pole určuje úplnou cestu souboru prostředků nabídky:  
  
- Pokud první pole je vynechán, prostředku nabídky je načten z satelitní knihovny DLL, které jsou označeny identifikátorem GUID balíčku VSPackage.  
  
  Druhé pole určuje Identifikátor prostředku nabídky typu CTMENU:  
  
- Pokud je zadané ID prostředku, a cesta k souboru poskytl první parametr, prostředku nabídky je načten z úplnou cestu k souboru.  
  
- Pokud je zadané ID prostředku, ale je cesta k souboru, prostředku nabídky je načten z satelitní knihovny DLL.  
  
- Pokud je k dispozici úplnou cestu k souboru a vynechá ID prostředku, soubor, který se má načíst má být soubor technický ředitel.  
  
  Poslední pole určuje číslo verze CTMENU prostředku. V nabídce můžete sloučit znovu tak, že změníte číslo verze.  
  
|Název|Typ|Data|Popis|  
|----------|----------|----------|-----------------|  
|CLSID_Package %|REG_SZ|`,1000,1`|Prostředek, který chcete načíst informace o nabídce.|  
  
 Následující příklady jsou umístěny v registru pod klíčem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates].  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Název|Typ|Data|Popis|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Hodnota ID prostředku pro šablony obrázky projekt nový projekt.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Výchozí cestu k adresáři nové projekty. Zobrazí se položky v tomto adresáři v **Průvodce novým projektem** dialogové okno.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Stanovuje pořadí, ve kterém projektů se zobrazí v uzlu stromu **nový projekt** dialogové okno.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 znamená, že projekty tohoto typu se zobrazují jenom v **nový projekt** dialogové okno.|  
  
 V následujícím příkladu se nachází v registru pod klíčem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts].  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|Název|Typ|Data|Popis|  
|----------|----------|----------|-----------------|  
|`Package`|REG_SZ|`%CLSID_Package%`|ID třídy registrované VSPackage.|  
|`UseInterface`|REG_DWORD|`1`|1 znamená, že uživatelské rozhraní se použije k interakci s tímto projektem. 0 znamená, že neexistuje žádná uživatelského rozhraní.|  
  
 The.vsz souborů, které řídí nových typů projektů často obsahovat RELATIVE_PATH položku. Tato cesta je relativní vzhledem k cesta zadaná v \ProductDir položky typu projektu v následujícím klíči instalační program:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup  
  
 Šablony projektů Enterprise Frameworks přidat například následující položky registru:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\  
  
 To znamená, že pokud zahrnete PROJECT_TYPE = EF záznam v souboru .vsz, najde prostředí vaší .vsz soubory v adresáři ProductDir zadali dřív.  
  
## <a name="see-also"></a>Viz také  
 [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Prvky modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)   
 [Vytváření instancí projektu pomocí objektů pro vytváření projektů](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)