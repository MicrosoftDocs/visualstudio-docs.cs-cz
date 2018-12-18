---
title: Zobrazení závislostí mezi zdrojovými soubory jazyka C++ a soubory hlaviček
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 6e2925eb3bfaf64a48b36c3c7205dce36538123c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823577"
---
# <a name="code-maps-for-c-projects"></a>Mapy kódu pro projekty v jazyce C++

Pokud chcete vytvořit podrobnější mapy pro projekty C++, nastavte možnost Procházet informace kompilátoru (**/FR**) na těchto projektech. Jinak se objeví zpráva s dotazem, zda chcete tuto možnost nastavit. Pokud vyberete **OK**, tím se nastaví možnost pouze aktuální mapování. Můžete skrýt zprávu pro všechny pozdější mapy.

Když otevřete řešení, které obsahuje projekty Visual C++, může trvat nějakou dobu, než se aktualizuje databáze technologie IntelliSense. Během této doby nebudete moct vytváření map kódu pro záhlaví (*.h* nebo `#include`) soubory, dokud se nedokončí aktualizace databáze IntelliSense. Na stavovém řádku v dolní části sady Visual Studio můžete sledovat průběh aktualizace.

- Pokud chcete zobrazit závislosti mezi všechny zdrojové soubory a soubory hlaviček ve vašem řešení, vyberte **architektura** > **Generovat graf vložených souborů**.

   ![Graf závislosti pro nativní kód](../modeling/media/dependencygraphgeneral_nativecode.png)

- Pokud chcete zobrazit závislosti mezi aktuálně otevřený soubor a související zdrojové soubory a soubory hlaviček, otevřete zdrojový soubor nebo soubor hlaviček. Otevřete místní nabídku souboru kdekoli v souboru. Zvolte **Generovat graf souborů zahrnutí**.

   ![Graf závislosti na první úrovni souboru .h](../modeling/media/dependencygraph_native_firstlevel.png)

## <a name="troubleshoot-code-maps-for-c-and-c-code"></a>Řešení potíží s map kódu pro kód jazyka C a C++

Tyto položky nejsou podporovány pro kód jazyka C a C++:

- Základní typy se nezobrazují na mapách, které obsahují nadřazené hierarchie.

- Většina **zobrazit** položky nabídky není k dispozici pro kód jazyka C a C++.

Při vytváření map kódu pro kód jazyka C a C++, může dojít k těmto problémům:

|**Problém**|**Možná příčina**|**Řešení**|
|-|-|-|
|Generovat mapu kódu se nezdařilo.|V řešení nebyly úspěšně sestaveny žádné projekty.|Opravte chyby sestavení, ke kterým došlo a potom znovu vytvořte mapu.|
|Visual Studio přestane reagovat při pokusu o generování mapy kódu z **architektura** nabídky.|Soubor databáze programů (.pdb) může být poškozen.<br /><br /> Soubor .pdb ukládá informace o ladění, jako je typ, metoda a informace zdrojového souboru.|Znovu sestavte řešení a potom akci opakujte.|
|Určitá nastavení pro databázi procházení IntelliSense jsou zakázána.|Určitá nastavení IntelliSense můžou být zakázané v sadě Visual Studio **možnosti** dialogové okno.|Chcete-li tato nastavení povolit, zapněte je.<br /><br /> Zobrazit [možnosti, textový Editor, C/C++, Upřesnit](../ide/reference/options-text-editor-c-cpp-advanced.md).|
|Zpráva **neznámé metody** se zobrazí v uzlu metody.<br /><br /> K tomuto problému dochází, protože nelze vyřešit název metody.|Binární soubor nemusí mít základní tabulku přemístění.|Zapnout **/fixed: No** v linkeru možnost.|
||Soubor databáze programů (.pdb) nemusí být vytvořen.<br /><br /> Soubor .pdb ukládá informace o ladění, jako je typ, metoda a informace zdrojového souboru.|Zapnout **/DEBUG** v linkeru možnost.|
||V očekávaných umístěních nelze otevřít nebo najít soubor .pdb.|Ujistěte se, že v předpokládaném umístění existuje soubor .pdb.|
||Informace o ladění byly ze souboru .pdb odstraněny.|Pokud **/PDBSTRIPPED** byla v nástroji linker použita možnost, místo toho zahrňte kompletní soubor .pdb.|
||Volající není funkcí a je převodní rutinou v binárním souboru nebo ukazatelem v datové sekci.|Pokud je volající převodní rutinou, zkuste použít `_declspec(dllimport)` aby se zabránilo jiné bitové šířce.|

## <a name="see-also"></a>Viz také:

- [Mapování závislostí pomocí map kódu](../modeling/map-dependencies-across-your-solutions.md)