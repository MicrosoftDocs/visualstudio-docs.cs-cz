---
title: 'Postupy: vytvoření sestavy porovnání profileru z příkazového řádku | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 88fac8339491acbe73a4a446cde8afb54fa63143
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814648"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Postupy: vytvoření sestavy porovnání profileru z příkazového řádku
Můžete vygenerovat [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástrojích pro profilaci sestavy, který porovnává výkonnostní data součásti dvě data profilování (. *Vsp* /nebo. *vsps*) soubory. Sestava zobrazí rozdíly, výkon regresí a vylepšení, které došlo k jedné relace profilování na druhý. Hodnoty v sestavě prezentují rozdílů nebo změna ze směrného plánu první soubor, který určíte. Touto položkou delta je vypočtena určením rozdíl mezi původní hodnoty, což je hodnota směrného plánu, a hodnota výsledek z nové analýzy. Porovnání profileru dat může být založen na funkce v kódu, modulů v aplikaci, řádky, ukazatele na instrukce (IP) a typy.  
  
 Pro zobrazení seznamu identifikátory porovnání kategorií a pole, zadejte následující příkaz:  
  
 **Vsperfreport – /querydifftables***VspFileName1* *VspFileName2*  
  
 Vytvoření sestavy porovnání použijte následující syntaxi:  
  
 **Vsperfreport – / diff** `VspFileName1` *VspFileName2* [**/**`Options`]  
  
 Můžete přidat možnosti z následující tabulce **/vsperfreport – diff** příkazového řádku.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**DiffThreshold:**[*hodnotu*]|Rozdíl ignorujte, pokud je pod tuto procentuální prahová hodnota. Navíc se nezobrazí nová data s hodnotami, které jsou pod touto prahovou hodnotou.|  
|**DiffTable:** *TableName*|Pomocí této tabulky k porovnání souborů. Ve výchozím nastavení se používá tabulce funkce. Zadejte identifikátor, který je uvedený v **vsperfreport – /querydifftables**.|  
|**DiffColumn:** *ColumnName*|Tento sloupec slouží k porovnání hodnot. Ve výchozím nastavení se používá sloupec procent výhradní ukázky. Zadejte identifikátor, který je uvedený v **vsperfreport – /querydifftables**.|