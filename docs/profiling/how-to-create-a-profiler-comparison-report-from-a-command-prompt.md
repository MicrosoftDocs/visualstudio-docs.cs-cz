---
title: 'Postup: Vytvoření sestavy porovnání profileru z příkazového řádku | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d0328e04067770f8837d10d532abb67d16c65e50
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776424"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Postup: Vytvoření sestavy porovnání profileru z příkazového řádku
Můžete vygenerovat [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sestavu Nástroje profilování, která porovnává data výkonu dvou dat profilování (.* vsp* /nebo . *vsps*) Soubory. Sestava zobrazuje rozdíly, regrese výkonu a vylepšení, ke kterým došlo z jedné relace profilování do druhé. Hodnoty v sestavě představují rozdíl nebo změnu od účaří prvního zadaného souboru. Tato delta se vypočítá určením rozdílu mezi starou hodnotou, což je hodnota směrného plánu, a výslednou hodnotou z nové analýzy. Porovnání dat profileru může být založeno na funkcích v kódu, modulech v aplikaci, řádcích, instrukčních ukazatelích (IP) a typech.

 Chcete-li uvést identifikátory porovnávacích kategorií a polí, zadejte následující příkazový řádek:

 **VSPerfReport /querydifftables**  *VspFileName1* *VspFileName2*

 K vytvoření sestavy porovnání použijte následující syntaxi:

 **VSPerfReport /diff** `VspFileName1` *VspFileName2* [**/**`Options`]  

 Možnosti z následující tabulky můžete přidat do příkazového řádku **VSPerfReport /diff.**

|Možnost|Popis|
|------------|-----------------|
|**DiffThreshold:**[*Hodnota*]|Nepřihlížet rozdíl, pokud je pod touto hodnotou procentní prahové hodnoty. Nová data s hodnotami, které jsou pod touto prahovou hodnotou, se také nezobrazí.|
|**DiffTable:** *Název_tabulky*|Tato tabulka slouží k porovnání souborů. Ve výchozím nastavení se používá tabulka funkcí. Zadejte identifikátor, který je uveden v **vsperfreport /querydifftables**.|
|**DiffColumn:** *ColumnName*|Tento sloupec slouží k porovnání hodnot. Ve výchozím nastavení se používá sloupec procentuální počet výhradních vzorků. Zadejte identifikátor, který je uveden v **vsperfreport /querydifftables**.|
