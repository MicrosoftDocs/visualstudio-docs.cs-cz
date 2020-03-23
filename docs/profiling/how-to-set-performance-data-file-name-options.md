---
title: 'Postup: Nastavení možností názvu souboru dat o výkonu | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cc42b63524a867c0893aa255180c740d03d4b5fe
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778762"
---
# <a name="how-to-set-performance-data-file-name-options"></a>Postupy: Nastavení možností názvu datového souboru výkonu

Ve výchozím nastavení uložíte data profilování (.* vsp*) pomocí následující syntaxe:

*Cesta\VSP-File\YYMMDD(N)* **.vsp**

Libovolný parametr pojmenování můžete změnit na stránce **Obecné** dialogového okna vlastností relace výkonu.

|||
|-|-|
|*Cesta*|Adresář, který obsahuje sestavu. Výchozí umístění je složka řešení nebo výchozí umístění pro projekty a řešení uživatele.|
|*Soubor VSP*|Název datového souboru profilování. Výchozí název je název řešení nebo spustitelného souboru, který je profilován.|
|*YymmdD*|Razítko data, které zobrazuje rok, měsíc a den, kdy byla shromážděna data profilování.|
|*(N)*|Pokud existuje více než jeden soubor dat profilování, je k názvu souboru mezi závorky přidáno zpříbyné číslo.|

## <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Změna syntaxe syntaxe datových souborů profilování relace výkonu

1. V **Průzkumníku výkonu**klikněte pravým tlačítkem myši na název relace výkonu a potom klikněte na **příkaz Vlastnosti**.

2. Klepněte na tlačítko **Obecné**.

3. V části **Sestava**změňte libovolné z následujících nastavení:

    |||
    |-|-|
    |**Umístění sestavy**|Zadejte adresář pro uložení datových souborů profilování.|
    |**Název sestavy**|Zadejte základní název souborů.|
    |**Automatické přidávání nových sestav do relace**|Zaškrtnutím políčka automaticky přidáte datový soubor do relace výkonu.|
    |**Připojení přírůstkové číslo k vygenerovaným sestavám**|Zaškrtnutím tohoto políčka přidáte k názvu souboru číslo zvýšení, pokud existuje více než jeden soubor se stejným názvem. Chcete-li přepsat existující soubor, zrušte zaškrtnutí políčka.|
    |**Použití časového razítka pro číslo**|Zaškrtnutím políčka přidáte datumrazítko do názvu souboru.|
