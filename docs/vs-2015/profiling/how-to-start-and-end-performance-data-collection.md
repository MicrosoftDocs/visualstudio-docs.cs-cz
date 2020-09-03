---
title: 'Postupy: spuštění a ukončení shromažďování dat výkonu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.summarypage
helpviewer_keywords:
- profiling tools, launching sessions
- performance sessions, launching
- performance sessions, ending
- profiling tools, ending sessions
ms.assetid: 9f6eb0d5-d9e9-4bec-b627-445065610bce
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 15c6d6c904bbab27bac541894ed6cd4f9e1f80f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202682"
---
# <a name="how-to-start-and-end-performance-data-collection"></a>Postupy: Zahájení a ukončení shromažďování údajů o výkonu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Předtím, než spustíte profilování, je nutné do relace výkonu přidat cílový binární soubor, který chcete profilovat. Chcete-li přidat cíl, klikněte pravým tlačítkem myši na **cíle** v **prohlížeč výkonu**a pak klikněte na **Přidat cílový binární soubor**. V dialogovém okně **Přidat cílový binární** soubor vyberte název souboru a potom klikněte na tlačítko **otevřít**. Byl přidán nový binární soubor.  
  
### <a name="to-start-profiling"></a>Spuštění profilace  
  
1. V okně **prohlížeč výkonu** klikněte pravým tlačítkem na název relace výkonu a vyberte jednu z následujících možností:  
  
    - **Spustit s profilací** – spustí aplikaci a ihned zahájí profilaci.  
  
    - **Spustit s pozastaveným profilací** – spustí aplikaci, ale nespustí profilování. Profilaci můžete spustit výběrem možnosti **pokračovat v kolekci** v okně **ovládací prvek shromažďování dat** . Další informace najdete v tématu [Postup: pozastavení a obnovení shromažďování dat o výkonu](../profiling/how-to-pause-and-resume-performance-data-collection.md).  
  
### <a name="to-end-profiling"></a>Ukončení profilace  
  
- Upřednostňovanou metodou ukončení relace profilování je ukončení aplikace. Pokud chcete profilaci okamžitě zastavit, na panelu nástrojů **prohlížeč výkonu** klikněte na **zastavit**.  
  
## <a name="see-also"></a>Viz také  
 [Řízení shromažďování dat](../profiling/controlling-data-collection.md)   
 [Postupy: pozastavení a obnovení shromažďování údajů o výkonu](../profiling/how-to-pause-and-resume-performance-data-collection.md)
