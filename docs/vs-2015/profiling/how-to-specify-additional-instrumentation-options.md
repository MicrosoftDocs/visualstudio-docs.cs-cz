---
title: 'Postupy: určení dalších možností instrumentace | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
ms.assetid: 639afe26-8335-4bd4-8aa5-f2c607b81f07
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d4bc6eeb208ab6d80168431f110f0f6169abbc82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64794727"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Postupy: Určení dalších možností instrumentace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete instrumentovat binární soubory z [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] integrovaného vývojového prostředí (IDE) nebo pomocí nástrojů příkazového řádku. Pokud instrumentovat binární data z integrovaného vývojového prostředí (IDE), můžete řídit objem dat shromažďovaných během instrumentace tím, že zadáte další možnosti instrumentace pro nástroj [VSInstr](../profiling/vsinstr.md) . Tyto možnosti jsou k dispozici v relaci nebo na cílové úrovni. Pokud například chcete zahrnout nebo vyloučit konkrétní funkce během procesu instrumentace, použijte možnost Další instrumentace na cílové úrovni.  
  
 **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!IMPORTANT]
> Každý vložený test upraví chování původního programu mírně. Tato změna způsobí režii v době analýzy. I když je aproximace této režie odečtena, má stále jemný efekt časování u vícevláknových aplikací. Možnosti nástroje [VSInstr](../profiling/vsinstr.md) slouží k řízení shromažďování dat během profilace.  
  
### <a name="to-specify-additional-instrumentation-option"></a>Určení dalších možností instrumentace  
  
1. V **prohlížeč výkonu**vyberte **relaci výkonu** , klikněte na ni pravým tlačítkem a vyberte **vlastnosti**.  
  
2. Na **stránkách vlastnosti**klikněte na **Upřesnit** vlastnosti.  
  
3. Možnosti typu v poli **Další možnosti instrumentace** .  
  
     Například použijte/CONTROL: THREAD k určení úrovně profilace. Úplný seznam možností najdete v tématu [VSInstr](../profiling/vsinstr.md).  
  
4. Klikněte na **OK**.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace relací výkonu](../profiling/configuring-performance-sessions.md)   
 [Profilace prostřednictvím příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)
