---
title: Vlastnosti linkeru Clang ( C++Android) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 66e88848-116c-4eb0-bc57-183394d35b57
author: corob-msft
ms.author: corob
manager: jillfra
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- VC.Project.VCLinkerTool.ShowProgress
- VC.Project.VCLinkerTool.Version
- VC.Project.VCLinkerTool.VerboseOutput
- VC.Project.VCLinkerTool.IncrementalLink
- VC.Project.VCLinkerTool.SharedLibrarySearchPath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
- VC.Project.VCLinkerTool.UnresolvedReferences
- VC.Project.VCLinkerTool.OptimizeForMemory
- VC.Project.VCLinkerTool.IgnoreDefaultLibraryNames
- VC.Project.VCLinkerTool.ForceSymbolReferences
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.OmitDebuggerSymbolInformation
- VC.Project.VCLinkerTool.GenerateMapFile
- VC.Project.VCLinkerTool.Relocation
- VC.Project.VCLinkerTool.FunctionBinding
- VC.Project.VCLinkerTool.NoExecStackRequired
- VC.Project.WholeArchive
- VC.Project.AdditionalOptionsPage
- VC.Project.VCLinkerTool.AdditionalDependencies
- VC.Project.VCLinkerTool.LibraryDependencies
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: e8f138b6c496f9dec32ad44dbdfa2064dd639990
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950683"
---
# <a name="clang-linker-properties-android-c"></a>Vlastnosti linkeru Clang ( C++Android)

Vlastnost | Popis | Vlastnit
--- | ---| ---
Výstupní soubor | Možnost přepíše výchozí název a umístění programu, který vytvoří linker. (-o)
Zobrazit průběh | Zobrazí zprávy o průběhu linkeru.
Version | Možnost-Version dá linkeru pokyn, aby vložil číslo verze do hlavičky spustitelného souboru.
Povolit podrobný výstup | Možnost-verbose dá linkeru pokyn, aby výstupem podrobných zpráv pro ladění.
Povolit přírůstkové propojování | Možnost dá linkeru pokyn, aby umožnil přírůstkové propojování.
Cesta pro hledání sdílené knihovny | Umožňuje uživateli naplnit cestu pro hledání ve sdílené knihovně.
Další adresáře knihoven | Umožňuje uživateli přepsat cestu ke knihovně prostředí. (-L složka).
Oznamovat nevyřešené odkazy na symboly | Tato možnost, pokud je povolená, bude hlásit nevyřešené odkazy na symboly.
Optimalizovat využití paměti | Optimalizuje využití paměti přečtením tabulek symbolů podle potřeby.
Ignorovat specifické výchozí knihovny | Určuje jeden nebo více názvů výchozích knihoven, které se mají ignorovat.
Vynutit odkazy na symboly | Vynutí zadání symbolu do výstupního souboru jako nedefinovaného symbolu.
Informace o symbolech ladicího programu | Informace o symbolech ladicího programu z výstupního souboru. | **Zahrnout vše**<br>**Vynechat nepotřebné symboly pro zpracování přemístění**<br>**Vynechat jenom informace o symbolech ladicího programu**<br>**Vynechat všechny informace o symbolech**<br>
Informace o symbolu ladicího programu balíčku | Před zabalením přepruhujte informace o symbolech ladicího programu.  Pro ladění se použije kopie původního binárního souboru.
Název souboru mapy | Možnost map dá linkeru pokyn, aby vytvořil soubor mapy se zadaným uživatelským jménem.
Označit proměnné jen pro čtení po přemístění | Tato možnost označí proměnné po přemístění jen pro čtení.
Povolit okamžitou vazbu funkcí | Tato možnost označí objekt pro okamžité vázání funkcí.
Vyžadovat spustitelný zásobník | Tato možnost označuje výstup, který nevyžaduje spustitelný zásobník.
Celý archiv | Celý archiv používá veškerý kód ze zdrojů a dalších závislostí.
Další možnosti | Další možnosti
Další závislosti | Určuje další položky, které se mají přidat do příkazového řádku propojení.
Závislosti knihoven | Tato možnost umožňuje zadat další knihovny, které mají být přidány do příkazového řádku linkeru. Další knihovny budou přidány na konec příkazového řádku linkeru, který začíná pomocí *knihovny LIB* a končí příponou *. a* nebo *. so* .  (-lFILE)
