---
title: Popis adresáře šablony (. Vsdir) Soubory | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16ba609d5b05d565a12b38bd19e9a777851ced5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704692"
---
# <a name="template-directory-description-vsdir-files"></a>Soubory popisu adresáře šablon (.Vsdir)
Soubor s popisem adresáře šablony (.vsdir) je textový soubor, který umožňuje integrovanému vývojovému prostředí (IDE) zobrazovat složky, soubory průvodce .vsz a soubory šablon, které jsou přidruženy k projektu v dialogových oknech. Obsah obsahuje jeden záznam na soubor nebo složku. Všechny soubory VSDIR v odkazovaném umístění jsou sloučeny, i když je obvykle k dispozici pouze jeden soubor VSDIR, který popisuje více složek, průvodců nebo souborů šablon.

 Složky (podadresáře), soubory, na které se odkazuje v souboru .vsdir, a samotný soubor .vsdir jsou umístěny ve stejném adresáři. Pokud rozhraní IDE spustí průvodce nebo zobrazí složku nebo soubor v dialogových oknech **Nový projekt** nebo Přidat **novou položku,** ide zkontroluje adresář, který obsahuje spuštěné soubory, a zjistí, zda je přítomen soubor .vsdir. Pokud je nalezen soubor .vsdir, ide čte jej k určení, zda obsahuje položku pro spuštěné nebo zobrazené složky nebo souboru. Pokud je položka nalezena, rozhraní IDE použije informace při provádění průvodce nebo zobrazení obsahu.

 Následující příklad kódu je ze souboru SourceFiles.vsdir v klíči \<registru EnvSDK>\BscPrj\BscPrj\BscPrjProjectItems\Source_Files:

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 V tomto případě jsou dva záznamy v jednom souboru. Každý záznam odděluje nový řádek (znak konce řádku). Každý řádek představuje jiný typ souboru. Znak potrubí (&#124;) odděluje pole v každém záznamu. Jeden adresář může obsahovat více souborů VSDIR, které mají různé názvy souborů, nebo můžete mít jeden soubor VSDIR pro každý typ souboru.

## <a name="fields"></a>Fields (Pole)
 V následující tabulce jsou uvedena pole určená pro každý záznam.

| Pole | Popis |
| - | - |
| Relativní název cesty (RelPathName) | Název složky, šablony nebo souboru VSZ, například HeaderFile.h nebo MyWizard.vsz. Toto pole může být také název používaný k reprezentaci složky. |
| {clsidPackage} | Identifikátor GUID balíčku VSPackage, který umožňuje přístup k lokalizovaným řetězcům, jako jsou LocalizedName, Description, IconResourceId a SuggestedBaseName, v prostředcích knihovny satelitních dynamických odkazů (DLL) v balíčku VSPackage. IconResourceId platí, pokud není zadána aplikace DLLPath. **Poznámka:**  Toto pole je volitelné, pokud jedno nebo více předchozích polí není identifikátorem zdroje. Toto pole je obvykle prázdné pro soubory .vsdir, které odpovídají průvodcům jiných výrobců, kteří nelokalizují svůj text. |
| Lokalizovaný název | Lokalizovaný název souboru šablony nebo průvodce. Toto pole může být řetězec nebo identifikátor prostředku formuláře "#ResID". Tento název se zobrazí v dialogovém okně **Přidat novou položku.** **Poznámka:**  Pokud LocalizedName je identifikátor prostředku, je vyžadován {clsidPackage}. |
| Priorita řazení | Celé číslo představující relativní prioritu tohoto souboru šablony nebo průvodce. Pokud má například tato položka hodnotu 1, zobrazí se vedle jiných položek s hodnotou 1 a před všemi položkami s hodnotou řazení 2 nebo větší.<br /><br /> Priorita řazení je relativní vzhledem k položkám ve stejném adresáři. Ve stejném adresáři může být více než jeden soubor .vsdir. V takovém případě položky ze všech <em>.</em> vsdir soubory v tomto adresáři jsou sloučeny. Položky se stejnou prioritou jsou uvedeny v lexikografickém pořadí zobrazeného názvu bez rozlišování velkých a malých písmen. Funkce `_wcsicmp` se používá k objednání položek.<br /><br /> Položky, které nejsou popsány v souborech .vsdir, obsahují číslo priority větší než číslo s nejvyšší prioritou uvedené v souborech .vsdir. Výsledkem je, že tyto položky jsou na konci zobrazeného seznamu bez ohledu na jejich název. |
| Popis | Lokalizovaný popis souboru šablony nebo průvodce. Toto pole může být řetězec nebo identifikátor prostředku formuláře "#ResID". Tento řetězec se zobrazí v dialogovém **okně Nový projekt** nebo Přidat novou **položku,** když je položka vybraná. |
| DLLPath nebo {clsidPackage} | Slouží k načtení ikony pro soubor šablony nebo průvodce. Ikona je načtena jako prostředek ze souboru DLL nebo EXE pomocí iconresourceid. Tento soubor DLL nebo EXE lze identifikovat pomocí úplné cesty nebo pomocí identifikátoru GUID balíčku VSPackage. Implementační dll VSPackage se používá k načtení ikony (není satelitní DLL). |
| Id iconresourceid | Identifikátor prostředku v dll dll nebo VSPackage implementace DLL, která určuje ikonu, která se má zobrazit. |
| Příznaky<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>( ) | Slouží k zakázání nebo povolení polí **Název** a **Umístění** v dialogovém okně **Přidat novou položku.** Hodnota pole **Příznaky** je desítkový ekvivalent kombinace požadovaných bitových příznaků.<br /><br /> Když uživatel vybere položku na kartě **Nový,** projekt určí, zda se při prvním zobrazení dialogového okna **Přidat novou položku** zobrazí pole Název a umístění. Položka prostřednictvím souboru .vsdir může řídit pouze to, zda jsou pole povolena a zakázána, pokud je položka vybrána. |
| Název_navrhované_základny | Představuje výchozí název souboru, průvodce nebo šablony. Toto pole je řetězec nebo identifikátor prostředku formuláře "#ResID". IDE používá tuto hodnotu k zadání výchozího názvu pro položku. Tato základní hodnota je připojena s celou hodnotou, aby byl název jedinečný, například MyFile21.asp.<br /><br /> V předchozím seznamu popis, dllpath, IconResourceId, příznaky a SuggestedBaseNumber platí pouze pro soubory šablony a průvodce. Tato pole se nevztahují na složky. Tato skutečnost je znázorněna v kódu v souboru BscPrjProjectItems v klíči \<registru EnvSDK>\BscPrj\BscPrj\BscPrjItems. Tento soubor obsahuje tři záznamy (jeden pro každou složku) se čtyřmi poli pro každý záznam: RelPathName, {clsidPackage}, LocalizedName a SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 Při vytváření souboru průvodce byste měli zvážit také následující problémy.

- Jakékoli nepovinné pole, pro které neexistují žádná smysluplná data, by mělo obsahovat 0 (nula) jako zástupný symbol.

- Pokud není k dispozici žádný lokalizovaný název, použije se v souboru průvodce relativní název cesty.

- DLLPath přepíše clsidPackage pro umístění ikony.

- Pokud není definována žádná ikona, ide nahradí výchozí ikonu pro soubor, který má tuto příponu.

- Pokud není k dispozici žádný navrhovaný základní název, použije se projekt.

- Pokud odstraníte soubory. VSZ, složky nebo soubory šablon, musíte také odebrat jejich přidružené záznamy ze souboru .vsdir.

## <a name="see-also"></a>Viz také
- [Průvodci](../../extensibility/internals/wizards.md)
- [Soubor průvodce (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
