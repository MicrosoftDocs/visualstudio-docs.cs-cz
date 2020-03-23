---
title: Porovnání datových souborů o výkonu | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777852"
---
# <a name="compare-performance-data-files"></a>Porovnání datových souborů výkonu

Funkce porovnání datových souborů nástroje profilování umožňuje vybrat dva soubory sestavy (.* vsp* /nebo . *vsps*) soubory a generovat sestavu, která zobrazuje rozdíly, regrese výkonu a vylepšení, ke kterým došlo z jedné relace profilování do druhé.

Srovnávací sestava datových [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] souborů z nástrojů profilování porovnává výsledky analýzy v jednom souboru dat profilování s výsledky základní analýzy v jiném datovém souboru. Oba datové soubory musí být generovány pomocí stejné metody profilování. Sestava analyzovaných porovnání je uložena jako . *vsps.*

Zobrazení sestavy porovnání představuje zobrazení tabulky změněných dat. Tabulka představuje rozdíl nebo změnu od směrného plánu. Delta se vypočítá určením rozdílu mezi starou hodnotou, hodnotou směrného plánu a výslednou hodnotou z nové analýzy.

Porovnání dat profileru může být založeno na funkcích v kódu, modulech v aplikaci, řádcích, instrukčních ukazatelích (IP) a typech.

Profilování dat, která je k dispozici pro porovnání zahrnuje informace, které jsou zobrazeny ve sloupcích. Definice těchto názvů sloupců naleznete v tématu [Zobrazení sestavy výkonu](../profiling/performance-report-views.md).

Prahovou hodnotu lze nastavit tak, aby se snížil šum a odfiltrována všechna data v zobrazení srovnávací tabulky řádků, které se nezměnily o zadané množství.

## <a name="in-this-section"></a>V tomto oddílu

[Postupy: Porovnání datových souborů výkonu](../profiling/how-to-compare-performance-data-files.md)
