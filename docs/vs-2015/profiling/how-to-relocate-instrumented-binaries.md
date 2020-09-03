---
title: 'Postupy: přemístění Instrumentních souborů | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 00b39b91b0a776438199d1df3c212cb9fe40f338
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155520"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Postupy: Přemístění instrumentovaných binárních souborů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Během instrumentace jsou testy vloženy do binárního souboru pro měření výkonu aplikace. Zvolením možnosti přemístit instrumentované binární soubory se zainstrumentuje a umístí se do zadaného umístění kopie původního binárního souboru. Tato možnost je užitečná v případě, že nechcete, aby Profiler přejmenoval původní binární soubor. Pokud binární soubor není přemístěný, původní verze binárního souboru bude přepsána.  
  
 **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-relocate-instrumented-binary"></a>Přemístění instrumentované binární  
  
1. V **prohlížeč výkonu**klikněte pravým tlačítkem na relaci výkonu a pak klikněte na **vlastnosti**.  
  
2. Na **stránkách vlastností**klikněte na **binární** vlastnosti.  
  
3. Zaškrtněte políčko **přemístit instrumentované binární soubory** .  
  
4. Zadejte umístění pro instrumentované binární soubory.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace relací výkonu](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)
