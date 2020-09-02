---
title: Porovnávání datových souborů výkonu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, comparing profiling tools report files
- profiling tools reports, comparing
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 64842c5b4f622a1f76aa528360f79403ec92cb42
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74777852"
---
# <a name="compare-performance-data-files"></a>Porovnání datových souborů výkonu

Funkce porovnání datových souborů Nástroje pro profilaci umožňují vybrat dva soubory sestav (.* VSP* /or. *vsps*) soubory a vygenerujte sestavu, která zobrazuje rozdíly, regrese výkonu a vylepšení, k nimž došlo z jedné relace profilování na druhou.

Porovnávací sestava datových souborů z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci porovnává výsledky analýzy v jednom souboru dat profilování s výsledky analýzy standardních hodnot v jiném datovém souboru. Oba datové soubory musí být vygenerovány pomocí stejné metody profilace. Sestava analyzovaných porovnání je uložena jako. soubor *vsps*

Zobrazení sestavy porovnání prezentuje tabulková zobrazení změněných dat. V tabulce se zobrazí rozdílová hodnota nebo se změní ze směrného plánu. Rozdíl se vypočítá pomocí určení rozdílu mezi starou hodnotou, základní hodnotou a výslednou hodnotou z nové analýzy.

Porovnání dat profileru může být založeno na funkcích v kódu, modulech aplikace, řádcích, ukazateli instrukcí (IP) a typech.

Data profilace, která jsou k dispozici pro porovnání, zahrnují informace, které se zobrazí ve sloupcích. Definice těchto názvů sloupců najdete v tématu [zobrazení sestav výkonu](../profiling/performance-report-views.md).

Prahovou hodnotu lze nastavit tak, aby snižovala šum a vyfiltroval všechna data v zobrazení srovnávací tabulky řádků, které se nezměnily zadanou hodnotou.

## <a name="in-this-section"></a>V této části

[Postupy: Porovnání datových souborů výkonu](../profiling/how-to-compare-performance-data-files.md)
