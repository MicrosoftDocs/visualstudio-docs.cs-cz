---
title: Nastavení možností názvu datového souboru výkonu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bba5677c491e77e6f1c2758e64cec1b598c9b627
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851564"
---
# <a name="how-to-set-performance-data-file-name-options"></a>Postupy: Nastavení možností názvu datového souboru výkonu

Ve výchozím nastavení uložíte data profilování (.* VSP*) soubor pomocí následující syntaxe:

*Path\VSP-File\YYMMDD (N)* **. vsp**

Libovolný parametr pojmenování můžete změnit na stránce **Obecné** dialogového okna vlastnosti pro relaci výkonu.

|Parametr|Popis|
|-|-|
|*Cesta*|Adresář, který obsahuje sestavu. Výchozím umístěním je složka řešení nebo výchozí umístění pro projekty a řešení uživatele.|
|*Soubor VSP*|Název souboru dat profilování. Výchozí název je název řešení nebo spustitelného souboru.|
|*RRMMDD*|Časové razítko, které zobrazuje rok, měsíc a den, kdy se data profilace shromáždila.|
|*N*|Pokud existuje více než jeden datový soubor profilování, přidá se k názvu souboru mezi závorky navýšené číslo.|

## <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Změna syntaxe názvů datových souborů profilování relace výkonu

1. V **prohlížeč výkonu**klikněte pravým tlačítkem na název relace výkonu a pak klikněte na **vlastnosti**.

2. Klikněte na **Obecné**.

3. V části **Sestava**změňte kterékoli z následujících nastavení:

    |Název|Popis|
    |-|-|
    |**Umístění sestavy**|Zadejte adresář, do kterého se mají ukládat soubory dat profilování.|
    |**Název sestavy**|Zadejte základní název souborů.|
    |**Automaticky přidávat nové sestavy do relace**|Zaškrtněte políčko, chcete-li automaticky přidat datový soubor do výkonnostní relace.|
    |**Připojit přírůstkové číslo k vygenerovaným sestavám**|Zaškrtněte políčko, pokud chcete přidat přírůstkové číslo k názvu souboru, pokud existuje více než jeden soubor se stejným názvem. Zrušením zaškrtnutí políčka přepíšete existující soubor.|
    |**Použít časové razítko pro číslo**|Zaškrtnutím políčka přidejte k názvu souboru dateStamp.|
