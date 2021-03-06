---
title: Vytvoření sestavy porovnání profileru (příkazový řádek)
description: Pomocí VSPerfReport.exe z příkazového řádku můžete porovnat výsledky dvou datových souborů profileru. Porovnání ukazuje rozdíly mezi relacemi profilace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 38303a091838fae6fdc86ab91eb1ee95dfb429ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911703"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Postupy: Vytvoření sestavy porovnání profileru z příkazového řádku
Můžete vygenerovat [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sestavu nástroje pro profilaci, která porovná údaje o výkonu dvou profilových dat (.*VSP* /or. *vsps*) spis. Tato sestava obsahuje rozdíly, regrese výkonu a vylepšení, k nimž došlo z jedné relace profilování na druhou. Hodnoty v sestavě prezentují rozdíl nebo změnu od základů prvního souboru, který zadáte. Tato rozdílová hodnota je počítána určením rozdílu mezi starou hodnotou, která je základní hodnotou, a výslednou hodnotou z nové analýzy. Porovnání dat profileru může být založeno na funkcích v kódu, modulech aplikace, řádcích, ukazateli instrukcí (IP) a typech.

 K vypsání identifikátorů kategorií porovnání a polí zadejte následující příkazový řádek:

 **VSPerfReport/querydifftables**  *VspFileName1* *VspFileName2*

 K vytvoření sestavy porovnání použijte následující syntax:

 **VSPerfReport diff** `VspFileName1` *VspFileName2* [ **/** `Options` ]  

 Do příkazového řádku **VSPerfReport diff** můžete přidat možnosti z následující tabulky.

|Možnost|Popis|
|------------|-----------------|
|**DiffThreshold:**[*hodnota*]|Ignoruje rozdíl, pokud je pod touto procentuální prahovou hodnotou. Navíc se nezobrazí nová data s hodnotami, které jsou pod touto prahovou hodnotou.|
|**Diff:** *TableName*|Pomocí této tabulky můžete porovnat soubory. Ve výchozím nastavení se používá tabulka Functions. Zadejte identifikátor, který je uveden v **VSPerfReport/querydifftables**.|
|**DiffColumn:** *ColumnName*|Pomocí tohoto sloupce můžete porovnat hodnoty. Ve výchozím nastavení se používá sloupec s hodnotou výhradní vzorky. Zadejte identifikátor, který je uveden v **VSPerfReport/querydifftables**.|
