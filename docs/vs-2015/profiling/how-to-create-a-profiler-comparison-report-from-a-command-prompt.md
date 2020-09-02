---
title: 'Postupy: Vytvoření sestavy porovnání profileru z příkazového řádku | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8c6dabbae5f2d3758aebe0562f99767ee6993d80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179567"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Postupy: Vytvoření sestavy porovnání profileru z příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete vygenerovat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sestavu nástroje pro profilaci, která porovná údaje o výkonu dvou profilových dat (. VSP/or. VSPS) soubory. Tato sestava obsahuje rozdíly, regrese výkonu a vylepšení, k nimž došlo z jedné relace profilování na druhou. Hodnoty v sestavě prezentují rozdíl nebo změnu od základů prvního souboru, který zadáte. Tato rozdílová hodnota je počítána určením rozdílu mezi starou hodnotou, která je základní hodnotou, a výslednou hodnotou z nové analýzy. Porovnání dat profileru může být založeno na funkcích v kódu, modulech aplikace, řádcích, ukazateli instrukcí (IP) a typech.  
  
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
