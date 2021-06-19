---
title: Zobrazení závislostí mezi zdrojovými a hlavičkami souborů jazyka C++
description: Poskytuje informace o mapách kódu pro projekty C++.
ms.date: 05/16/2018
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
ms.custom: SEO-VS-2020
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 93ac1f7364e23ef9ed2b44ecd1c536a7ab2b3d40
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389667"
---
# <a name="code-maps-for-c-projects"></a>Mapy kódu pro projekty C++

Pokud chcete vytvořit úplnější mapy pro projekty C++, nastavte u těchto projektů možnost kompilátoru informací o procházení (**/FR).** Jinak se objeví zpráva s dotazem, zda chcete tuto možnost nastavit. Pokud vyberete **OK**, nastaví se možnost jenom pro aktuální mapu. U všech pozdějších map se můžete rozhodnout zprávu skrýt.

Když otevřete řešení, které obsahuje projekty Visual C++, může trvat nějakou dobu, než se aktualizuje databáze technologie IntelliSense. Během této doby možná nebudete moct vytvářet mapy kódu pro soubory hlaviček (*.h* nebo ), dokud se nedokončí `#include` aktualizace databáze IntelliSense. Na stavovém řádku v dolní části sady Visual Studio můžete sledovat průběh aktualizace.

- Pokud chcete zobrazit závislosti mezi všemi zdrojovými soubory a hlavičkami ve vašem řešení, vyberte **Architektura** Generovat  >  **graf souborů zahrnutí.**

   ![Graf závislostí pro nativní kód](../modeling/media/dependencygraphgeneral_nativecode.png)

- Pokud chcete zobrazit závislosti mezi aktuálně otevřeným souborem a souvisejícími zdrojovými soubory a soubory hlaviček, otevřete zdrojový soubor nebo soubor hlaviček. Otevřete místní nabídku souboru kdekoli v souboru. Zvolte **Generate Graph of Include Files (Vygenerovat graf souborů zahrnutí).**

   ![Graf závislostí první úrovně pro soubor .h](../modeling/media/dependencygraph_native_firstlevel.png)

## <a name="troubleshoot-code-maps-for-c-and-c-code"></a>Řešení potíží s mapami kódu pro kód C a C++

Tyto položky nejsou podporovány pro kód jazyka C a C++:

- Základní typy se nezobrazují na mapách, které obsahují nadřazenou hierarchii.

- Většina **položek** nabídky Zobrazit není k dispozici pro kód C a C++.

K těmto problémům může dojít při vytváření map kódu pro kód C a C++:

|**Problém**|**Možná příčina**|**Řešení**|
|-|-|-|
|Mapu kódu se nepodařilo vygenerovat.|V řešení nebyly úspěšně sestaveny žádné projekty.|Opravte chyby sestavení, ke kterým došlo, a pak znovu vygenerujte mapu.|
|Visual Studio při pokusu o vygenerování mapy kódu z nabídky **Architektura** přestane reagovat.|Soubor databáze programů (.pdb) může být poškozen.<br /><br /> Soubor .pdb ukládá informace o ladění, jako je typ, metoda a informace zdrojového souboru.|Znovu sestavte řešení a potom akci opakujte.|
|Určitá nastavení pro databázi procházení IntelliSense jsou zakázána.|Určitá nastavení technologie IntelliSense mohou být v dialogovém Visual Studio **Možnosti** zakázána.|Chcete-li tato nastavení povolit, zapněte je.<br /><br /> Viz [Možnosti, Textový editor, C/C++, Upřesnit](../ide/reference/options-text-editor-c-cpp-advanced.md).|
|Na **uzlu metody se** zobrazí zpráva Neznámé metody.<br /><br /> K tomuto problému dochází, protože nelze vyřešit název metody.|Binární soubor nemusí mít základní tabulku přemístění.|V linkeru zapněte možnost **/FIXED:NO.**|
||Soubor databáze programů (.pdb) nemusí být vytvořen.<br /><br /> Soubor .pdb ukládá informace o ladění, jako je typ, metoda a informace zdrojového souboru.|V linkeru zapněte možnost **/DEBUG.**|
||V očekávaných umístěních nelze otevřít nebo najít soubor .pdb.|Ujistěte se, že v předpokládaném umístění existuje soubor .pdb.|
||Informace o ladění byly ze souboru .pdb odstraněny.|Pokud jste v linkeru použili možnost **/PDBSTRIPPED,** zahrřte místo toho úplný soubor .pdb.|
||Volající není funkcí a je převodní rutinou v binárním souboru nebo ukazatelem v datové sekci.|Pokud je volajícím blok, zkuste použít , `_declspec(dllimport)` abyste se vyhnuli volání této funkce.|

## <a name="see-also"></a>Viz také

- [Mapování závislostí s mapami kódu](../modeling/map-dependencies-across-your-solutions.md)
