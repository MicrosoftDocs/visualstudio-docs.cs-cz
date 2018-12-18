---
title: Clang vlastnosti Linkeru (Android C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 66e88848-116c-4eb0-bc57-183394d35b57
author: corob
ms.author: mblome
manager: douge
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
ms.openlocfilehash: 1b491257c561af337afdfd0d066c9ed8cd550c15
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2018
ms.locfileid: "39230945"
---
# <a name="clang-linker-properties-android-c"></a>Clang vlastnosti Linkeru (Android C++)

Vlastnost | Popis | Možnosti
--- | ---| ---
Výstupní soubor | Tato možnost přepíše výchozí název a umístění programu, který vytvoří linker. (-o).
Zobrazit průběh | Vytiskne zprávy o průběhu Linkeru.
Version | -Version přikáže linkeru, aby vložil číslo verze v záhlaví spustitelného souboru.
Povolit podrobný výstup | -Verbose – možnost dá linkeru pokyn, do výstupu vypisoval podrobné zprávy pro ladění.
Povolit přírůstkové propojení | Přikazuje linkeru, aby umožnil přírůstkové propojování.
Sdílené cesty pro hledání knihovny | Umožňuje uživateli naplnit cestu hledání sdílené knihovny.
Další adresáře knihoven | Umožňuje uživateli přepsat cestu ke knihovně prostředí. (-L složka).
Hlásit nevyřešené odkazy na symboly | Povolení této možnosti budou hlásit nevyřešené odkazy na symboly.
Optimalizovat využití paměti | Optimalizujte využití paměti opětovným čtením tabulek symbolů podle potřeby.
Ignorovat konkrétní výchozí knihovny | Určuje jeden nebo více názvů výchozích knihoven k ignorování.
Vynutit odkazy na symboly | Vynutit zapsání symbolu do výstupního souboru jako nedefinovaného symbolu.
Informace o symbolech ladicího programu | Ladicí program informace o symbolech z výstupního souboru. | **Zahrnout všechny**<br>**Vynechat nepotřebné symboly pro zpracování přemístění**<br>**Vynechat informace o symbolech ladicího programu pouze**<br>**Vynechat všechny informace o symbolech**<br>
Informace o symbolech ladicího programu balíčku | Odstranit informace o symbolech ladicího programu před balení.  Kopii původní binární soubor se použije pro ladění.
Název souboru mapy | Možnost Map přikazuje linkeru, aby vytvořil soubor mapy s uživatelsky definovaným názvem.
Označit jen pro čtení proměnné po přemístění | Tato možnost označí proměnné jen pro čtení po přemístění.
Povolit okamžité vázání funkcí | Tato možnost označí objekt pro okamžité vázání funkcí.
Vyžadovat spustitelný zásobník | Tato možnost určí, že výstup nevyžaduje spustitelný zásobník.
Celý archiv | Celý archiv používá veškerý kód ze zdrojů a dalších závislostí.
Další možnosti | Další možnosti.
Další závislosti | Určuje další položky pro přidání do příkazového řádku propojení.
Závislé položky knihoven | Tato možnost umožňuje zadat další knihovny, které mají být přidány do příkazového řádku linkeru. Další knihovny se přidá na konec spuštění příkazového řádku linkeru s *lib* a na konci *.a* nebo *.so* rozšíření.  (-lFILE)
