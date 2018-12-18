---
title: 'Postupy: shromažďování dat vzorkování na úrovni řádků | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0920c9a506adaf562a8acc77b2b030e461f11ed1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934886"
---
# <a name="how-to-collect-line-level-sampling-data"></a>Postupy: shromažďování dat vzorkování na úrovni řádků
Vzorkování na úrovni řádku je schopnost profiler k určení, kde v kódu funkce náročnou na procesor, jako je například funkce, která má vysokou exkluzivní vzorky procesoru trávit většinu času.  
  
## <a name="overview"></a>Přehled  
 Pro vzorkování na úrovni řádku, profiler vás program zásobník volání v nastavených intervalech a agreguje výsledky. Tyto výsledky ukazují, jaký instrukce procesoru byla spuštěna při ukázky byly provedeny. K identifikaci řádků kódu a ukazatel instrukce (IP) se pak analyzuje shromážděná data o výhradních vzorků.  
  
 Vzorkování na úrovni řádků funguje i pro spravované i nativní kód. Sestavy o výkonu, které se zobrazit tato data zahrnují zobrazení řádků a zobrazení modulů.  
  
 Informace o znacích begin/end není k dispozici pro nativní kód. Víceřádkové příkazy řádek začít informace není k dispozici pro nativní kód; je k dispozici pouze informace o ukončení řádku.  
  
### <a name="available-data"></a>K dispozici data  
 K dispozici vzorkování na úrovni řádku dat obsahuje následující informace:  
  
- Název funkce.  
  
- Adresa funkce.  
  
- Začněte řádky – číslo řádku vzorky kódu.  
  
- Konec řádku – koncové číslo řádku zdroje. Toto je obecně stejná jako "Řádku begin" data s výjimkou případů, kdy jeden příkaz program zahrnuje více řádky zdrojového kódu.  
  
- Znaky begin - začátek sloupec agregační vzorku. Obvykle se jedná 0 s výjimkou případů, kdy jeden řádek obsahuje více příkazů programu.  
  
- Koncový znak - poslední sloupec agregační vzorku.  
  
- IP adresa – adresa, kde agregované vzorku (pouze zobrazení IP).  
  
  V **moduly** zobrazit, pokud je funkce Statistika na úrovni řádku, statistiky jsou vnořené v rámci jednotlivých funkcí. Kromě toho se zobrazí statistika na úrovni IP, které jsou vnořené v každém řádku.  
  
### <a name="turn-off-line-level-sampling-for-managed-code"></a>Vypnutí vzorkování na úrovni řádku pro spravovaný kód  
 Vzorkování na úrovni řádku je ve výchozím nastavení zapnutá. Můžete vypnout shromažďování dat na úrovni řádku pro spravovaný kód pomocí jedné z následujících příkazů:  
  
-   Před profilací, zadejte **VSPerfCLREnv /samplelineoff**. Tímto je ovlivněn aplikací a služeb.  
  
     – nebo –  
  
-   Při spuštění aplikace, zadejte **VSPerfCmd/lineoff \<ostatních argumentů >**.  
  
## <a name="see-also"></a>Viz také:  
 [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)   
 [Analýza dat nástrojů pro měření výkonu](../profiling/analyzing-performance-tools-data.md)