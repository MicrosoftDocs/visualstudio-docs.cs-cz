---
title: Registrace šablon projektů a položek | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e35a476ab8fe8d8de3ce11dd117de4c84a3befa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724631"
---
# <a name="registering-project-and-item-templates"></a>Registrace šablon projektů a položek
Typy projektů musí registrovat adresáře, ve kterých se nacházejí šablony projektů a položek projektů. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] používá registrační informace přidružené k vašim typům projektů k určení toho, co se má zobrazit v dialogových oknech **Přidat nový projekt** a **Přidat novou položku** .

 Další informace o šablonách naleznete v tématu [Přidání projektů a šablon položek projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="registry-entries-for-projects"></a>Položky registru pro projekty
 Následující příklady ukazují položky registru v části HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio \\ <*verze*>. Doprovodné tabulky vysvětlují prvky používané v příkladech.

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|Name|Typ|Popis|
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

| Name | Typ | Popis |
|--------------------------|-----------| - |
| @ | REG_SZ | ID prostředku pro šablony pro přidání položek |
| TemplatesDir | REG_SZ | Cesta k položkám projektu zobrazeným v dialogovém okně průvodce **přidáním nové položky** |
| TemplatesLocalizedSubDir | REG_SZ | ID prostředku řetězce, který pojmenovává podadresář TemplatesDir, který obsahuje lokalizované šablony. Vzhledem k tomu, že [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] načte prostředek řetězce z satelitních knihoven DLL, pokud je máte, každá satelitní knihovna DLL může obsahovat jiný lokalizovaný název podadresáře. |
| SortPriority | REG_DWORD | Nastavte SortPriority tak, aby se řídilo pořadí, ve kterém se šablony zobrazují v dialogovém okně **Přidat novou položku** . Větší hodnoty SortPriority se zobrazí v seznamu šablon dříve. |

### <a name="registering-file-filters"></a>Probíhá registrace filtrů souborů.
 Volitelně můžete zaregistrovat filtry, které [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] používá, když se zobrazí výzva k zadání názvů souborů. Například [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] filtr pro dialogové okno **otevřít soubor** je:

 **Soubory C# vizuálů (\*. cs, \*. resx, \*. settings, \*. xsd, \*. WSDL); \*. cs, \*. resx, \*. Settings, 0. xsd, 1. WSDL)**

 Aby bylo možné podporovat registraci více filtrů, je každý filtr zaregistrován ve vlastním podklíči v části HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio \\ <*verze*> \Projects \\ {\<*ProjectGUID*>} \Filters >*podklíč*\\ <. Název podklíče je libovolný;  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignoruje název podklíče a použije pouze jeho hodnoty.

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

|Name|Typ|Popis|
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

## <a name="see-also"></a>Viz také:

- [Přidávání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Průvodci](../../extensibility/internals/wizards.md)
- [Lokalizace aplikací](../../ide/globalizing-and-localizing-applications.md)
- [Identifikátory CATID pro objekty používané obvykle k rozšíření projektů](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)