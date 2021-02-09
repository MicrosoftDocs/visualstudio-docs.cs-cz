---
title: Zobrazit závislosti mezi zdrojovými a hlavičkými soubory C++
description: Poskytuje informace o mapách kódu pro projekty jazyka C++.
ms.date: 05/16/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
ms.custom: SEO-VS-2020
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9c2aa1e49c0465fcf75917f0d9bd134962794c74
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861748"
---
# <a name="code-maps-for-c-projects"></a>Mapy kódu pro projekty v jazyce C++

Pokud chcete vytvořit úplnější mapování pro projekty v jazyce C++, nastavte u těchto projektů možnost Procházet informace kompilátoru (**/fr**). Jinak se objeví zpráva s dotazem, zda chcete tuto možnost nastavit. Pokud vyberete **OK**, tato možnost nastaví možnost pouze pro aktuální mapu. Můžete zvolit, že se má skrýt zpráva u všech pozdějších map.

Když otevřete řešení, které obsahuje projekty Visual C++, může trvat nějakou dobu, než se aktualizuje databáze technologie IntelliSense. Během této doby možná nebudete moci vytvořit mapy kódu pro soubory hlaviček (*. h* nebo `#include` ), dokud se nedokončí aktualizace databáze IntelliSense. Na stavovém řádku v dolní části sady Visual Studio můžete sledovat průběh aktualizace.

- Chcete-li zobrazit závislosti mezi všemi zdrojovými soubory a hlavičkovým soubory ve vašem řešení, vyberte možnost **Architektura**  >  **Generovat graf souborů zahrnutí**.

   ![Graf závislosti pro nativní kód](../modeling/media/dependencygraphgeneral_nativecode.png)

- Chcete-li zobrazit závislosti mezi aktuálně otevřeným souborem a souvisejícími zdrojovými soubory a hlavičkou souborů, otevřete zdrojový soubor nebo soubor hlaviček. Otevřete místní nabídku souboru kdekoli v souboru. Vyberte možnost **Generovat graf souborů zahrnutí**.

   ![Graf závislosti první úrovně pro soubor. h](../modeling/media/dependencygraph_native_firstlevel.png)

## <a name="troubleshoot-code-maps-for-c-and-c-code"></a>Řešení potíží s mapami kódu pro kód C a C++

Tyto položky nejsou podporovány pro kód jazyka C a C++:

- Základní typy se nezobrazují na mapách, které zahrnují nadřazenou hierarchii.

- Většina položek nabídky **Zobrazit** není k dispozici pro kód C a C++.

Tyto problémy mohou nastat při vytváření map kódu pro kód jazyka C a C++:

|**Chybu**|**Možná příčina**|**Řešení**|
|-|-|-|
|Nepovedlo se vygenerovat mapu kódu.|V řešení nebyly úspěšně sestaveny žádné projekty.|Opravte chyby sestavení, k nimž došlo, a potom znovu vygenerujte mapu.|
|Pokud se pokusíte vygenerovat mapu kódu z nabídky **Architektura** , Visual Studio přestane reagovat.|Soubor databáze programů (.pdb) může být poškozen.<br /><br /> Soubor .pdb ukládá informace o ladění, jako je typ, metoda a informace zdrojového souboru.|Znovu sestavte řešení a potom akci opakujte.|
|Určitá nastavení pro databázi procházení IntelliSense jsou zakázána.|Některá nastavení IntelliSense mohou být zakázána v dialogovém okně **Možnosti** aplikace Visual Studio.|Chcete-li tato nastavení povolit, zapněte je.<br /><br /> Viz [Možnosti, textový editor, C/C++, Upřesnit](../ide/reference/options-text-editor-c-cpp-advanced.md).|
|Zpráva **neznámé metody** se zobrazí v uzlu metody.<br /><br /> K tomuto problému dochází, protože nelze vyřešit název metody.|Binární soubor nemusí mít základní tabulku přemístění.|V linkeru zapněte možnost **/fixed: No** .|
||Soubor databáze programů (.pdb) nemusí být vytvořen.<br /><br /> Soubor .pdb ukládá informace o ladění, jako je typ, metoda a informace zdrojového souboru.|V linkeru zapněte možnost **/Debug** .|
||V očekávaných umístěních nelze otevřít nebo najít soubor .pdb.|Ujistěte se, že v předpokládaném umístění existuje soubor .pdb.|
||Informace o ladění byly ze souboru .pdb odstraněny.|Pokud se v linkeru použila možnost **/PDBSTRIPPED** , zahrňte místo toho úplný soubor. pdb.|
||Volající není funkcí a je převodní rutinou v binárním souboru nebo ukazatelem v datové sekci.|Je-li volajícím převodem, zkuste použít příkaz, `_declspec(dllimport)` aby nedošlo k převodu.|

## <a name="see-also"></a>Viz také

- [Mapování závislostí pomocí map kódu](../modeling/map-dependencies-across-your-solutions.md)
