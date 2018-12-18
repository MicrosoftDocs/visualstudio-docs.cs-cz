---
title: Registrace šablon projektů a položek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fea06b4e36b35266f39dc07d58a29c1b53310b57
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934597"
---
# <a name="registering-project-and-item-templates"></a>Registrace šablon projektů a položek
Typy projektů musíte zaregistrovat adresáře, kde se nachází jejich šablony projektů a položek projektů. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] informace o registraci přidružený k vaší typy projektů používá k určení, co se má zobrazit v **přidat nový projekt** a **přidat novou položku** dialogových oknech.  

 Další informace o šablonách najdete v tématu [přidání projektů a šablon položek projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).  

## <a name="registry-entries-for-projects"></a>Položky registru pro projekty  
 Následující příklady ukazují položky registru v rámci HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*verze*>. Související tabulky popisují prvky použité v případech.  

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
|displayName|REG_SZ|ID prostředku, který se má načíst z satelitní knihovny DLL název zaregistrován balíčky.|  
|Balíček|REG_SZ|ID třídy balíčku zaregistrován balíčky.|  
|ProjectTemplatesDir|REG_SZ|Výchozí cesty k souboru šablony projektu. Soubory šablon projektu se zobrazí podle **nový projekt** šablony.|  

### <a name="registering-item-templates"></a>Registrace šablon položek  
 Je nutné zaregistrovat na adresář, kam ukládat šablony položek.  

```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  


| Název | Typ | Popis |
|--------------------------|-----------| - |
| @ | REG_SZ | ID prostředku pro přidat položku šablony. |
| TemplatesDir | REG_SZ | Cesta položky projektu zobrazí v dialogovém okně **přidat novou položku** průvodce. |
| TemplatesLocalizedSubDir | REG_SZ | ID prostředku řetězce, který podadresáři TemplatesDir názvů, který obsahuje lokalizované šablony. Protože [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zatížení prostředek řetězce ze satelitní knihovny DLL Pokud je máte, každý satelitní knihovny DLL může obsahovat název jiné lokalizované podadresáře. |
| SortPriority | REG_DWORD | Nastavte SortPriority k řízení pořadí, ve kterém šablony se zobrazují v **přidat novou položku** dialogové okno. Vyšší hodnoty SortPriority zobrazí výše v seznamu šablon. |

### <a name="registering-file-filters"></a>Registrace filtry souborů  
 Volitelně můžete zaregistrovat filtry, které [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] používá, když ho vyzve k zadání názvů souborů. Například [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] filtrovat **otevřít soubor** dialogové okno je:  

 **Soubory Visual C# (\*.cs,\*.resx,\*.settings,\*XSD,\*WSDL);\*. cs,\*.resx,\*.settings,\*XSD,\*WSDL)**  

 Pro podporu registrace více filtrů, každý filtr je zaregistrován ve vlastní podklíč pod HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*verze*> \Projects\\{ \< *ProjectGUID*>} \Filters\\<*podklíč*>. Název podklíče je libovolný. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignoruje v podklíči název a používá jenom jeho hodnoty.  

 Můžete řídit kontextech, ve kterých se používá filtr tak, že nastavíte příznaky, které jsou uvedeny v následující tabulce. Pokud filtr nemá nastaveny žádné příznaky, objeví se po běžné filtry v **přidat existující položku** dialogové okno a **otevřít soubor** dialogovému oknu, ale nesmí být použity v **najít v souborech**  dialogové okno.  

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
|CommonFindFilesFilter|REG_DWORD|Vytvoří jeden z běžných filtrů filtr na **najít v souborech** dialogové okno. Běžné filtry jsou uvedeny v seznamu filtru před filtry, které nejsou označeny jako běžné.|  
|CommonOpenFilesFilter|REG_DWORD|Vytvoří jeden z běžných filtrů filtr na **otevřít soubor** dialogové okno. Běžné filtry jsou uvedeny v seznamu filtru před filtry, které nejsou označeny jako běžné.|  
|FindInFilesFilter|REG_DWORD|Seznam filtru po běžné filtry v **najít v souborech** dialogové okno.|  
|NotOpenFileFilter|REG_DWORD|Označuje, že se nepoužívá filtr **otevřít soubor** dialogové okno.|  
|NotAddExistingItemFilter|REG_DWORD|Označuje, že se nepoužívá filtr **přidat existující položku** dialogové okno.|  
|SortPriority|REG_DWORD|Nastavit SortPriority k řízení pořadí, ve kterém jsou zobrazeny filtry. Vyšší hodnoty SortPriority zobrazí výše v seznamu filtrů.|  

## <a name="directory-structure"></a>Adresářová struktura  
 Rozšíření VSPackages můžete do šablony soubory a složky, kdekoli na místním nebo vzdáleném disk, tak dlouho, dokud umístění je zaregistrované prostřednictvím integrovaného vývojového prostředí (IDE). Ale pro usnadnění organizace, doporučujeme následující adresářovou strukturu v cestě instalace produktu.  

 \Templates  

 \Projects (obsahuje šablony projektu)  

 \Applications  

 \Components  

 \ ...  

 \ProjectItems (obsahuje položky projektu)  

 \Class  

 \Form  

 \Web stránky  

 \HelperFiles (obsahuje soubory používané v položkách projektu více soubory)  

 \WizardFiles  

## <a name="see-also"></a>Viz také  
 [Přidání projektu a šablony položek projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Průvodce](../../extensibility/internals/wizards.md)   
 [Lokalizace aplikací](../../ide/localizing-applications.md)   
 [Identifikátory CATID pro objekty používané obvykle k rozšíření projektů](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)