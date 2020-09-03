---
title: Registrace šablon projektů a položek | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a06e7a292d960e675ad4b0de97499557542fef1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185840"
---
# <a name="registering-project-and-item-templates"></a>Registrace šablon projektů a položek
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Typy projektů musí registrovat adresáře, ve kterých se nacházejí šablony projektů a položek projektů. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pomocí registračních informací přidružených k vašim typům projektů určuje, co se má zobrazit v dialogových oknech **Přidat nový projekt** a **Přidat novou položku** .  
  
 Další informace o šablonách naleznete v tématu [Přidání projektů a šablon položek projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="registry-entries-for-projects"></a>Položky registru pro projekty  
 Následující příklady ukazují položky registru v části HKEY_LOCAL_MACHINE \software\microsoft\visualstudio \\ < *verze*>. Doprovodné tabulky vysvětlují prvky používané v příkladech.  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|Název|Typ|Popis|  
|----------|----------|-----------------|  
|@|REG_SZ|Výchozí název projektů tohoto druhu.|  
|DisplayName|REG_SZ|ID prostředku pro název, který se má načíst z satelitní knihovny DLL registrované v balíčcích|  
|Balíček|REG_SZ|ID třídy balíčku registrovaného v balíčcích|  
|ProjectTemplatesDir|REG_SZ|Výchozí cesta souborů šablony projektu Soubory šablon projektu se zobrazí v šabloně **nového projektu** .|  
  
### <a name="registering-item-templates"></a>Registrace šablon položek  
 Je nutné zaregistrovat adresář, do kterého ukládáte šablony položek.  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|Název|Typ|Popis|  
|----------|----------|-----------------|  
|@|REG_SZ|ID prostředku pro šablony pro přidání položek|  
|TemplatesDir|REG_SZ|Cesta k položkám projektu zobrazeným v dialogovém okně průvodce **přidáním nové položky**|  
|TemplatesLocalizedSubDir|REG_SZ|ID prostředku řetězce, který pojmenovává podadresář TemplatesDir, který obsahuje lokalizované šablony. Protože [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] načte prostředek řetězce z satelitních knihoven DLL, pokud je máte, každá satelitní knihovna DLL může obsahovat jiný lokalizovaný název podadresáře.|  
|SortPriority|REG_DWORD|Nastavte SortPriority tak, aby se řídilo pořadí, ve kterém se šablony zobrazují v dialogovém okně **Přidat novou položku** . Větší hodnoty SortPriority se zobrazí v seznamu šablon dříve.|  
  
### <a name="registering-file-filters"></a>Probíhá registrace filtrů souborů.  
 Volitelně můžete zaregistrovat filtry, které nástroj [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] používá při výzvě k zadání názvů souborů. Například [!INCLUDE[csprcs](../../includes/csprcs-md.md)] Filtr pro dialogové okno **otevřít soubor** je:  
  
 **Soubory Visual C# ( \* . cs, \* . resx, \* . Settings, \* . xsd, \* . WSDL); \* . cs, \* . resx, \* . Settings, \* . xsd, \* . WSDL)**  
  
 Aby bylo možné podporovat registraci více filtrů, je každý filtr zaregistrován ve svém vlastním podklíči v části HKEY_LOCAL_MACHINE \software\microsoft\visualstudio \\ < *verze*> \Projects \\ { \<*ProjectGUID*> } \Filters \\ < *podklíč*>. Název podklíče je libovolný; [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ignoruje název podklíče a použije pouze jeho hodnoty.  
  
 Můžete ovládat kontexty, ve kterých se filtr používá, nastavením příznaků, které jsou uvedeny v následující tabulce. Pokud filtr nemá nastaveny žádné příznaky, bude uveden po běžných filtrech v dialogovém okně **Přidat existující položku** a v dialogovém okně **otevřít soubor** , ale nebude použito v dialogovém okně **najít v souborech** .  
  
```  
[Projects\{ProjectGUID}\Filters\MyLanguageFilter]  
@="#3"  
"CommonOpenFilesFilter"=dword:00000000  
"CommonFindFilesFilter"=dword:00000000  
"FindInFilesFilter"=dword:00000000  
"NotOpenFileFilter"=dword:00000000  
"NotAddExistingItemFilter"=dword:00000000  
"SortPriority"=dword:00000064  
```  
  
|Název|Typ|Popis|  
|----------|----------|-----------------|  
|CommonFindFilesFilter|REG_DWORD|Vytvoří filtr jeden z běžných filtrů v dialogovém okně **najít v souborech** . Běžné filtry jsou uvedeny v seznamu filtru před filtry, které nejsou označeny jako společné.|  
|CommonOpenFilesFilter|REG_DWORD|Vytvoří filtr jeden z běžných filtrů v dialogovém okně **otevřít soubor** . Běžné filtry jsou uvedeny v seznamu filtru před filtry, které nejsou označeny jako společné.|  
|FindInFilesFilter|REG_DWORD|Vypíše filtr po běžných filtrech v dialogovém okně **najít v souborech** .|  
|NotOpenFileFilter|REG_DWORD|Označuje, že se filtr nepoužívá v dialogovém okně **otevřít soubor** .|  
|NotAddExistingItemFilter|REG_DWORD|Označuje, že se filtr nepoužívá v dialogovém okně **Přidat existující položku** .|  
|SortPriority|REG_DWORD|Nastavte SortPriority na pořadí, ve kterém se zobrazují filtry. V seznamu filtru se objeví větší SortPriority hodnoty.|  
  
## <a name="directory-structure"></a>Adresářová struktura  
 Sady VSPackage můžou umístit soubory šablon a složky kdekoli na místní nebo vzdálený disk, pokud je umístění zaregistrované prostřednictvím integrovaného vývojového prostředí (IDE). Pro snazší organizaci ale doporučujeme následující adresářovou strukturu v cestě k instalaci vašeho produktu.  
  
 \Templates  
  
 \Projects (obsahuje šablony projektu)  
  
 \Applications  
  
 \Components  
  
 \ ...  
  
 \ProjectItems (obsahuje položky projektu)  
  
 \Class  
  
 \Form  
  
 Stránka \Web  
  
 \HelperFiles (obsahuje soubory používané v položkách projektu s více soubory)  
  
 \WizardFiles  
  
## <a name="see-also"></a>Viz také  
 [Přidávání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Průvodc](../../extensibility/internals/wizards.md)   
 [Lokalizace aplikací](../../ide/localizing-applications.md)   
 [Identifikátory CATID pro objekty používané obvykle k rozšíření projektů](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
