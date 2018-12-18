---
title: Popis šablony adresáře (. Soubory VSDIR) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 67e2cf5dcb898614750aecd7e4fe997fbde0b5cc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938432"
---
# <a name="template-directory-description-vsdir-files"></a>Soubory popisu adresáře šablon (.Vsdir)
Soubor popisu adresáře šablon (.vsdir) je textový soubor, který umožňuje integrované vývojové prostředí (IDE) pro zobrazení složek, souborů průvodce .vsz a souborů šablon, které jsou spojené s projektem v dialogových oknech. Obsah zahrnuje jeden záznam na souboru nebo složky. Všechny soubory .vsdir v odkazované umístění jsou sloučeny, i když jediný projektový soubor je obvykle zadáváno popisující více složek, průvodců nebo soubory šablon.  

 Složky (v podadresářích), soubory, které jsou odkazovány v souboru .vsdir a samotný soubor .vsdir jsou umístěny ve stejném adresáři. Když integrovaného vývojového prostředí spustí průvodce, nebo zobrazuje složky nebo souboru v **nový projekt** nebo **přidat novou položku** dialogových oknech, rozhraní IDE prozkoumá adresáře, který obsahuje prováděnou soubory, které chcete zjistit, zda je soubor .vsdir k dispozici. Pokud je nalezen soubor .vsdir, rozhraní IDE načte ji k určení, zda obsahuje položku pro spuštěný nebo zobrazené složky nebo souboru. Pokud se položka nenajde, integrovaném vývojovém prostředí používá spuštění průvodce nebo zobrazení obsahu.  

 Následující příklad kódu je ze souboru SourceFiles.vsdir v \<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems\Source_Files klíč registru:  

```  
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127  
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124  
```  

 V tomto případě jsou dva záznamy do jednoho souboru. Nový řádek (návratový znak) odděluje každý záznam. Každý řádek představuje jiný typ souboru. Kanál (&#124;) odděluje pole v jednotlivých záznamech. Jeden adresář může obsahovat více souborů .vsdir, které mají různými názvy, nebo může mít jeden projektový soubor pro každý typ souboru.  

## <a name="fields"></a>Pole  
 V následující tabulce jsou uvedeny na pole určená pro každý záznam.  


| Pole | Popis |
| - | - |
| Relativní cesta (RelPathName) | Název souboru složky, šablonu nebo .vsz, například HeaderFile.h nebo MyWizard.vsz. Toto pole může být také název používá k reprezentování složku. |
| {clsidPackage} | Identifikátor GUID sady VSPackage, která umožňuje přístup k lokalizované řetězce, jako je například LocalizedName, popis, IconResourceId a SuggestedBaseName, sady VSPackage satelitní dynamická knihovna (DLL) prostředky. IconResourceId platí v případě, že není zadán DLLPath. **Poznámka:** toto pole je volitelné, pokud jeden nebo více polí předchozí není identifikátor prostředku. Toto pole je obvykle prázdné, pokud souborů .vsdir, které odpovídají s použitím průvodců třetích stran, které nelze lokalizovat jejich textu. |
| LocalizedName | Lokalizovaný název souboru šablony nebo průvodce. Toto pole může být řetězec nebo identifikátor prostředku ve formě "#ResID". Tento název se zobrazí v **přidat novou položku** dialogové okno. **Poznámka:** Pokud LocalizedName identifikátor prostředku, pak {clsidPackage} je povinný. |
| SortPriority | Celé číslo představující relativní priorita tohoto souboru šablony nebo průvodce. Například pokud se tato položka má hodnotu 1, pak tato položka se zobrazí vedle dalších položek s hodnotou 1 a před všechny položky s hodnotou řazení 2 nebo větší.<br /><br /> Řazení priorita je relativní vůči položky ve stejném adresáři. Může být více než jeden soubor .vsdir ve stejném adresáři. V takovém případě položky ze všech <em>.</em> soubory VSDIR v tomto adresáři jsou sloučeny. Položky se stejnou prioritou jsou uvedeny ve velkých a malých písmen slovníkovém pořadí zobrazovaný název. `_wcsicmp` Funkce slouží ke třídění položek.<br /><br /> Položky, které nejsou popsané v souborů .vsdir zahrnují priorita je větší než nejvyšší priorita v souborech .vsdir. Výsledkem je, že tyto položky jsou na konci seznamu bez ohledu na jejich název. |
| Popis | Lokalizovaný popis souboru šablony nebo průvodce. Toto pole může být řetězec nebo identifikátor prostředku ve formě "#ResID". Tento řetězec je zobrazen v **nový projekt** nebo **přidat novou položku** dialogové okno při výběru položky. |
| DLLPath nebo {clsidPackage} | Umožňuje načíst ikonu pro soubor šablony nebo průvodce. Ikona je načtena jako prostředek ze souboru .dll nebo .exe s použitím IconResourceId. Tento soubor .dll nebo .exe lze identifikovat pomocí úplnou cestu nebo identifikátor GUID sady VSPackage pomocí. Implementace DLL sady VSPackage slouží k načtení ikony (ne satelitní knihovny DLL). |
| IconResourceId | Identifikátor prostředku v implementaci VSPackage nebo knihovny DLL knihovny DLL, která určuje ikonu k zobrazení. |
| Příznaky (<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>) | Umožňuje povolit nebo zakázat **název** a **umístění** pole na **přidat novou položku** dialogové okno. Hodnota **příznaky** pole je desítkový ekvivalent kombinací vyžaduje bitové příznaky.<br /><br /> Když uživatel vybere položku na **nový** kartu, projektu určuje, zda pole název a umístění se zobrazí při **přidat novou položku** nejprve zobrazí dialogové okno. Položky, pomocí souborů .vsdir, můžete určit pouze, zda pole jsou povolené a zakázané při výběru položky. |
| SuggestedBaseName | Představuje výchozí název souboru, průvodce nebo šablony. Toto pole je řetězec nebo identifikátor prostředku ve formě "#ResID". Integrované vývojové prostředí používá tuto hodnotu jako výchozí název položky. S celočíselnou hodnotou. Chcete-li název jedinečný, jako je například MyFile21.asp se připojí tento základní hodnota.<br /><br /> V předchozím seznamu popis, DLLPath, IconResourceId, příznaky a SuggestedBaseNumber platí pouze pro soubory šablon a průvodce. Tato pole se nevztahují ke složkám. Tato skutečnost je znázorněn v kódu v souboru BscPrjProjectItems \<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems klíč registru. Tento soubor obsahuje tři záznamy (jeden pro každou složku) s čtyři pole pro každý záznam: RelPathName {clsidPackage} LocalizedName a SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 Při vytváření souboru průvodce byste také zvážit následující problémy.  

-   Libovolné nepovinné pole pro kterou neexistují žádná smysluplná data by měla obsahovat hodnotu 0 (nula) jako zástupný symbol.  

-   Pokud není lokalizovaný název zadán, použije se v souboru průvodce název relativní cestu.  

-   DLLPath přepíše clsidPackage pro umístění ikony.  

-   Pokud není definována žádná ikona, IDE nahradí výchozí ikonu pro soubor, který se má toto rozšíření.  

-   Pokud není navrhované základní název zadán, použije se 'Project'.  

-   Pokud odstraníte soubory .vsz, složky nebo soubory šablon, musíte také odebrat jejich přidružené záznamy ze souboru .vsdir.  

## <a name="see-also"></a>Viz také  
 [Průvodce](../../extensibility/internals/wizards.md)   
 [Soubor průvodce (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)