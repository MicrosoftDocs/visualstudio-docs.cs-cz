---
title: 'Postupy: shromažďování dat vzorkování na úrovni řádků | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 65890bf31a1257c3a41bc1fd7ed3f732c50eda14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185959"
---
# <a name="how-to-collect-line-level-sampling-data"></a>Postupy: Shromažďování dat vzorkování na úrovni řádků
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vzorkování na úrovni řádků je schopnost profileru určit, kde v kódu funkce náročné na procesor, jako je například funkce, která má vysoce exkluzivní ukázky, musí procesor strávit nejvíc času.  
  
## <a name="overview"></a>Přehled  
 Pro vzorkování na úrovni řádků Profiler provede v nastavených intervalech zásobník volání programu a agreguje tyto výsledky. Tyto výsledky zobrazují informace o tom, jaké pokyny byl procesor spuštěn při pořízení vzorků. Shromážděná data o exkluzivních ukázkách se pak analyzují, aby identifikovala řádky kódu a ukazatel na instrukce (IP).  
  
 Vzorkování na úrovni řádků funguje pro spravovaný i nativní kód. Sestavy výkonu, které zobrazují tato data, zahrnují zobrazení řádků a zobrazení modulů.  
  
 Pro nativní kód nejsou k dispozici informace o počátečním/koncovém znaku. Pro víceřádkové příkazy nejsou k dispozici informace o zahájení řádku pro nativní kód; k dispozici jsou pouze informace o koncích řádků.  
  
### <a name="available-data"></a>Dostupná data  
 Dostupná data vzorkování na úrovni řádků obsahují následující informace:  
  
- Název funkce  
  
- Adresa funkce  
  
- Začátek řádku – číslo řádku s ukázkovým kódem.  
  
- Konec řádku – číslo koncového řádku zdroje To je obvykle stejné jako při "řádku begin" data kromě případů, kdy jeden program zahrnuje více řádků zdrojového kódu.  
  
- Začátek znaku – počáteční sloupec agregované ukázky. Obvykle se jedná o 0 s výjimkou případů, kdy jeden řádek obsahuje více příkazů programu.  
  
- End znak – konečný sloupec agregované ukázky.  
  
- IP – adresa, kde byla provedena agregovaná ukázka (jenom zobrazení IP).  
  
  V zobrazení **modulů** , pokud funkce obsahuje statistiku na úrovni řádků, statistika je vnořena do každé funkce. Kromě toho se zobrazí statistiky na úrovni protokolu IP, které jsou vnořené pod každým řádkem.  
  
### <a name="turn-off-line-level-sampling-for-managed-code"></a>Vypnout vzorkování na úrovni řádků pro spravovaný kód  
 Ve výchozím nastavení je vzorkování na úrovni řádků zapnuté. Shromažďování dat na úrovni řádků pro spravovaný kód můžete vypnout jedním z následujících způsobů:  
  
- Před profilací zadejte **VSPerfCLREnv/samplelineoff**. To má vliv na aplikace i služby.  
  
     ani  
  
- Při spouštění aplikace zadejte **VSPerfCmd/LineOff \<other arguments> **.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace relací výkonu](../profiling/configuring-performance-sessions.md)   
 [Analýza dat nástrojů pro měření výkonu](../profiling/analyzing-performance-tools-data.md)
