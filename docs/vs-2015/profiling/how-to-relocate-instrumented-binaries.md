---
title: 'Postupy: přemístění instrumentovaných binárních souborů | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 012236c9d3d02f498843f7a185efdd07c6e96a4d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770863"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Postupy: Přemístění instrumentovaných binárních souborů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Během instrumentace testy jsou vloženy do binárního souboru k měření výkonu aplikace. Výběrem přemístit instrumentované binární kopii původní binární soubor je instrumentovány a umístit do zadaného umístění. Tato možnost je užitečná, pokud nechcete, aby se profiler k přejmenování původní binární soubor. Pokud není přemístit binární soubor, přepíše původní verze binárního souboru.  
  
 **Požadavky**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-relocate-instrumented-binary"></a>K přesunutí instrumentovaný binární soubor  
  
1.  V **prohlížeč výkonu**, klikněte pravým tlačítkem na relaci výkonu a pak klikněte na tlačítko **vlastnosti**.  
  
2.  V **stránky vlastností**, klikněte na tlačítko **binární** vlastnosti.  
  
3.  Vyberte **přemístění instrumentovaných binárních souborů** zaškrtávací políčko.  
  
4.  Zadejte umístění pro instrumentované binární soubor.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)



