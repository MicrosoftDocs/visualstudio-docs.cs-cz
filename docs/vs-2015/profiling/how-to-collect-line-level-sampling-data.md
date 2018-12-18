---
title: 'Postupy: shromažďování dat vzorkování na úrovni řádků | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 21ef50736e00bd835b4e1bc88530d2aaef30ee82
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51767536"
---
# <a name="how-to-collect-line-level-sampling-data"></a>Postupy: Shromažďování dat vzorkování na úrovni řádků
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vzorkování na úrovni řádku je schopnost profiler k určení, kde v kódu funkce náročnou na procesor, jako je například funkce, která má vysokou exkluzivní vzorky procesoru trávit většinu času.  
  
## <a name="overview"></a>Přehled  
 Pro vzorkování na úrovni řádku, profiler vás program zásobník volání v nastavených intervalech a agreguje výsledky. Tyto výsledky ukazují, jaký instrukce procesoru byla spuštěna při ukázky byly provedeny. K identifikaci řádků kódu a ukazatel instrukce (IP) se pak analyzuje shromážděná data o výhradních vzorků.  
  
 Vzorkování na úrovni řádků funguje i pro spravované i nativní kód. Sestavy o výkonu, které se zobrazit tato data zahrnují zobrazení řádků a zobrazení modulů.  
  
 Informace o znacích begin/end není k dispozici pro nativní kód. Víceřádkové příkazy řádek začít informace není k dispozici pro nativní kód; je k dispozici pouze informace o ukončení řádku.  
  
### <a name="available-data"></a>K dispozici Data  
 K dispozici vzorkování na úrovni řádku dat obsahuje následující informace:  
  
- Název funkce.  
  
- Adresa funkce.  
  
- Řádek začíná – číslo řádku vzorky kódu.  
  
- Konec řádku – koncové číslo řádku zdroje. Toto je obecně stejná jako "Řádku begin" data s výjimkou případů, kdy jeden příkaz program zahrnuje více řádky zdrojového kódu.  
  
- Znak začít – začátek sloupec agregační vzorku. Obvykle se jedná 0 s výjimkou případů, kdy jeden řádek obsahuje více příkazů programu.  
  
- Koncový znak – poslední sloupec agregační vzorku.  
  
- IP adresa – adresa, kde agregované vzorku (pouze zobrazení IP).  
  
  V **moduly** zobrazit, pokud je funkce Statistika na úrovni řádku, statistiky jsou vnořené v rámci jednotlivých funkcí. Kromě toho se zobrazí statistika na úrovni IP, které jsou vnořené v každém řádku.  
  
### <a name="turn-off-line-level-sampling-for-managed-code"></a>Vypnutí vzorkování na úrovni řádku pro spravovaný kód  
 Vzorkování na úrovni řádku je ve výchozím nastavení zapnutá. Můžete vypnout shromažďování dat na úrovni řádku pro spravovaný kód pomocí jedné z následujících akcí:  
  
-   Před profilací, zadejte **VSPerfCLREnv /samplelineoff**. Tímto je ovlivněn aplikací a služeb.  
  
     – nebo –  
  
-   Při spuštění aplikace, zadejte **VSPerfCmd/lineoff \<ostatních argumentů >**.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)   
 [Analýza dat nástrojů pro měření výkonu](../profiling/analyzing-performance-tools-data.md)



