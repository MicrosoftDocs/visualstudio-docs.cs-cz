---
title: Popis adresáře šablon (. Soubory VSDIR) | Microsoft Docs
description: Přečtěte si, jak soubor popisu adresáře šablon umožňuje prostředí Visual Studio IDE zobrazovat složky, soubory. vsz a šablony, které jsou přidružené k vašemu projektu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: edc4b4bcfe1ac1a85524517ba467e207a792e3cd
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877725"
---
# <a name="template-directory-description-vsdir-files"></a>Soubory popisu adresáře šablon (.Vsdir)
Soubor popisu adresáře šablon (. vsdir) je textový soubor, který umožňuje integrované vývojové prostředí (IDE) zobrazovat složky, soubory s příponou. vsz a soubory šablon přidružené k vašemu projektu v dialogových oknech. Obsah zahrnuje jeden záznam na soubor nebo složku. Všechny soubory. vsdir v odkazovaném umístění jsou sloučeny, i když je obecně k dispozici pouze jeden soubor. vsdir, který popisuje více složek, průvodců nebo souborů šablon.

 Složky (podadresáře), soubory, na které se odkazuje v souboru. vsdir a samotný soubor. vsdir, se nachází ve stejném adresáři. Když IDE spustí Průvodce nebo zobrazí složku nebo soubor v dialogových oknech **Nový projekt** nebo **Přidat novou položku** , rozhraní IDE ověří adresář, který obsahuje spuštěné soubory k určení, zda je soubor. vsdir přítomen. Pokud je nalezen soubor. vsdir, rozhraní IDE ho přečte a určí, zda obsahuje položku pro spuštěnou nebo zobrazenou složku nebo soubor. Pokud je položka nalezena, rozhraní IDE použije informace při spuštění průvodce nebo zobrazení obsahu.

 Následující příklad kódu je ze souboru SourceFiles. vsdir v \<EnvSDK> klíči registru \bscprj\bscprj\bscprjprojectitems\ Source_Files:

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 V tomto případě jsou dva záznamy v jednom souboru. Nový řádek (znak návratu na začátek řádku) odděluje každý záznam. Každý řádek představuje jiný typ souboru. Znak kanálu (&#124;) odděluje pole v každém záznamu. Jeden adresář může obsahovat více souborů. vsdir, které mají různé názvy souborů, nebo můžete mít jeden soubor. vsdir pro každý typ souboru.

## <a name="fields"></a>Pole
 V následující tabulce jsou uvedena pole určená pro každý záznam.

| Pole | Popis |
| - | - |
| Název relativní cesty (RelPathName) | Název složky, šablony nebo souboru. vsz, například HeaderFile. h nebo MyWizard. vsz. V tomto poli můžete také použít název, který představuje složku. |
| {clsidPackage} | Identifikátor GUID sady VSPackage, který umožňuje přístup k lokalizovaným řetězcům, jako jsou například lokalizované, popis, IconResourceId a SuggestedBaseName, v satelitních dynamických odkazech knihovny (DLL) sady VSPackage. IconResourceId platí, pokud není zadán DLLPath. **Poznámka:**  Toto pole je volitelné, pokud jedno nebo více předchozích polí není identifikátorem prostředku. Toto pole je obvykle prázdné pro soubory. vsdir, které odpovídají průvodcům třetích stran, které Nelokalizovat jejich text. |
| Lokalizovaný | Lokalizovaný název souboru šablony nebo průvodce. Toto pole může být řetězec nebo identifikátor prostředku ve formátu "#ResID". Tento název se zobrazí v dialogovém okně **Přidat novou položku** . **Poznámka:**  Pokud je lokalizovaný identifikátor prostředku, je nutné {clsidPackage}. |
| SortPriority | Celé číslo představující relativní prioritu tohoto souboru šablony nebo průvodce. Například pokud má tato položka hodnotu 1, pak se tato položka zobrazí vedle jiných položek s hodnotou 1 a před všemi položkami s hodnotou řazení 2 nebo větší.<br /><br /> Priorita řazení je relativní vzhledem k položkám ve stejném adresáři. Ve stejném adresáři může být víc než jeden soubor. vsdir. V takovém případě položky ze všech <em>.</em> soubory VSDIR v tomto adresáři se sloučí. Položky se stejnou prioritou jsou uvedeny v lexikografickým pořadím pořadí zobrazeného názvu v nerozlišování velkých a malých písmen. `_wcsicmp`Funkce slouží k seřazení položek.<br /><br /> Položky, které nejsou popsány v souborech. vsdir, obsahují prioritní číslo větší, než je nejvyšší číslo priority uvedené v souborech. vsdir. Výsledkem je, že tyto položky jsou na konci zobrazeného seznamu bez ohledu na jejich název. |
| Popis | Lokalizovaný Popis souboru šablony nebo průvodce. Toto pole může být řetězec nebo identifikátor prostředku ve formátu "#ResID". Tento řetězec se zobrazí v dialogovém okně **Nový projekt** nebo **Přidat novou položku** , pokud je položka vybrána. |
| DLLPath nebo {clsidPackage} | Slouží k načtení ikony pro soubor šablony nebo průvodce. Ikona je načtena jako prostředek ze souboru. dll nebo. exe pomocí IconResourceId. Tento soubor. dll nebo. exe lze identifikovat buď pomocí úplné cesty, nebo pomocí identifikátoru GUID sady VSPackage. Implementační knihovna VSPackage se používá k načtení ikony (ne satelitní knihovny DLL). |
| IconResourceId | Identifikátor prostředku v knihovně DLL implementace VSPackage, který určuje ikonu, která má být zobrazena. |
| Flags ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS> ) | Slouží k zakázání nebo povolení polí **název** a **umístění** v dialogovém okně **Přidat novou položku** . Hodnota pole **Flags** je desítková ekvivalent kombinace požadovaných bitových příznaků.<br /><br /> Když uživatel vybere položku na **nové** kartě, projekt určí, zda je pole název a umístění zobrazeno, když se nejprve zobrazí dialogové okno **Přidat novou položku** . Položka, prostřednictvím souboru. vsdir, může řídit pouze to, zda jsou pole povolena a zakázána, když je položka vybrána. |
| SuggestedBaseName | Představuje výchozí název souboru, průvodce nebo šablony. Toto pole je buď řetězec, nebo identifikátor prostředku ve formátu "#ResID". Rozhraní IDE používá tuto hodnotu k poskytnutí výchozího názvu pro položku. Tato základní hodnota se připojí s celočíselnou hodnotou, aby byl název jedinečný, například MyFile21. ASP.<br /><br /> V předchozím seznamu jsou popisy, DLLPath, IconResourceId, flags a SuggestedBaseNumber platné pouze pro soubory šablon a průvodce. Tato pole se nevztahují na složky. Tento fakt je znázorněn v kódu v souboru BscPrjProjectItems v \<EnvSDK> klíči registru \BscPrj\BscPrj\BscPrjProjectItems. Tento soubor obsahuje tři záznamy (jeden pro každou složku) se čtyřmi poli pro každý záznam: RelPathName, {clsidPackage}, lokalizovaných a SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 Při vytváření souboru Průvodce byste měli také vzít v úvahu následující problémy.

- Jakékoli nepovinné pole, pro které neexistují žádná smysluplná data, by měla obsahovat 0 (nula) jako zástupný symbol.

- Pokud není zadaný žádný lokalizovaný název, použije se v souboru průvodce název relativní cesty.

- DLLPath Přepisuje clsidPackage pro umístění ikony.

- Pokud není definována žádná ikona, IDE nahradí výchozí ikonu pro soubor, který má příponu.

- Pokud není zadán žádný navrhovaný základní název, použije se ' Project '.

- Pokud odstraníte soubory. vsz, složky nebo soubory šablon, je nutné odebrat také přidružené záznamy ze souboru. vsdir.

## <a name="see-also"></a>Viz také
- [Průvodci](../../extensibility/internals/wizards.md)
- [Soubor průvodce (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
