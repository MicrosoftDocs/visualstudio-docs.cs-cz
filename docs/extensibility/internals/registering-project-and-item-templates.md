---
title: Registrace šablon projektů a položek | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b64504c39b1fc3c4a82530b265cfd0e96832b4f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705825"
---
# <a name="registering-project-and-item-templates"></a>Registrace šablon projektů a položek
Typy projektů musí registrovat adresáře, kde jsou umístěny jejich šablony projektu a položky projektu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Pomocí registračních informací přidružených k typům projektu určíte, co se má zobrazit v dialogových oknech **Přidat nový projekt** a Přidat novou **položku.**

 Další informace o šablonách naleznete [v tématu Přidání šablon položek projektu a projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="registry-entries-for-projects"></a>Položky registru pro projekty
 Následující příklady zobrazují položky registru v části\\<HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio*Version*>. V doprovodných tabulkách jsou vysvětleny prvky použité v příkladech.

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|Name (Název)|Typ|Popis|
|----------|----------|-----------------|
|@|REG_SZ|Výchozí název projektů tohoto druhu.|
|DisplayName|REG_SZ|ID prostředku názvu, který má být načten ze satelitní dll registrované v části Balíčky.|
|Balíček|REG_SZ|ID třídy balíčku registrovaného v části Balíčky.|
|ProjektŠablonyDir|REG_SZ|Výchozí cesta k souborům šablony projektu Soubory šablony projektu jsou zobrazeny šablonou **Nový projekt.**|

### <a name="registering-item-templates"></a>Registrace šablon položek
 Je nutné zaregistrovat adresář, do kterého ukládáte šablony položek.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| Name (Název) | Typ | Popis |
|--------------------------|-----------| - |
| @ | REG_SZ | ID prostředku pro přidání šablon položek. |
| ŠablonyDir | REG_SZ | Cesta k položkám projektu zobrazeným v dialogovém okně průvodce **Přidat novou položku** |
| ŠablonyLocalizedSubDir | REG_SZ | ID prostředku řetězce, který pojmenovává podadresář TemplatesDir, který obsahuje lokalizované šablony. Vzhledem k tomu, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] že načte řetězec prostředek ze satelitních knihoven DLL, pokud je máte, může každá satelitní knihovna DLL obsahovat jiný lokalizovaný název podadresáře. |
| Priorita řazení | REG_DWORD | Nastavte sortpriority tak, aby řídila pořadí, ve kterém jsou šablony zobrazeny v dialogovém okně **Přidat novou položku.** Větší hodnoty SortPriority se zobrazí dříve v seznamu šablon. |

### <a name="registering-file-filters"></a>Registrace filtrů souborů
 Volitelně můžete zaregistrovat [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] filtry, které se používají při zobrazení výzvy k zadání názvů souborů. Například filtr pro dialogové okno Otevřít soubor je: **Open File** [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]

 **Visual C#\*Files (\*.cs,\*.resx, .settings,\*.xsd,\*.wsdl); \*.cs,\*.resx,\*.settings,\*.xsd,\*.wsdl)**

 Pro podporu registrace více filtrů je každý filtr registrován ve vlastním podklíči pod HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*Version*>\Projects\\\<{*ProjectGUID*>}\Filters\\<*Subkey*>. Název podklíče je libovolný; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignoruje název podklíče a používá pouze jeho hodnoty.

 Kontexty, ve kterých je filtr používán, můžete řídit nastavením příznaků zobrazených v následující tabulce. Pokud filtr nemá nastaveny žádné příznaky, bude uveden za běžnými filtry v dialogovém okně **Přidat existující položku** a v dialogovém okně **Otevřít soubor,** ale nebude použit v dialogovém okně **Najít v souborech.**

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

|Name (Název)|Typ|Popis|
|----------|----------|-----------------|
|CommonFindFilesFilter|REG_DWORD|Načiní filtr jedním z běžných filtrů v dialogovém okně **Najít v souborech.** Běžné filtry jsou uvedeny v seznamu filtrů před filtry, které nejsou označeny jako běžné.|
|CommonOpenFilesFilter|REG_DWORD|Načiní filtr jedním z běžných filtrů v dialogovém okně **Otevřít soubor.** Běžné filtry jsou uvedeny v seznamu filtrů před filtry, které nejsou označeny jako běžné.|
|Filtr FindInFilesFilter|REG_DWORD|Zobrazí filtr za běžnými filtry v dialogovém okně **Najít v souborech.**|
|NotOpenFileFilter|REG_DWORD|Označuje, že filtr není použit v dialogovém okně **Otevřít soubor.**|
|NotAddExistingItemFilter|REG_DWORD|Označuje, že filtr není použit v dialogovém okně **Přidat existující položku.**|
|Priorita řazení|REG_DWORD|Nastavte SortPriority pro řízení pořadí, ve kterém jsou filtry zobrazeny. Větší hodnoty SortPriority se zobrazí dříve v seznamu filtrů.|

## <a name="directory-structure"></a>Adresářová struktura
 VSPackages můžete umístit soubory šablon a složky kdekoli na místní nebo vzdálený disk, tak dlouho, dokud umístění je registrována prostřednictvím integrovaného vývojového prostředí (IDE). Pro usnadnění organizace však doporučujeme následující strukturu adresářů pod cestou instalace produktu.

 \Šablony

 \Projekty (obsahuje šablony projektu)

 \Aplikace

 \Součásti

 \ ...

 \ProjectItems (obsahuje položky projektu)

 \Třída

 \Formulář

 \Webová stránka

 \HelperFiles (obsahuje soubory používané v položkách projektu s více soubory)

 \Průvodce soubory

## <a name="see-also"></a>Viz také

- [Přidávání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Průvodci](../../extensibility/internals/wizards.md)
- [Lokalizace aplikací](../../ide/globalizing-and-localizing-applications.md)
- [Identifikátory CATID pro objekty používané obvykle k rozšíření projektů](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
