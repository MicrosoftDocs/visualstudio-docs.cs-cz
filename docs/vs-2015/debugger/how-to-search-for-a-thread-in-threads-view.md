---
title: 'Postupy: hledání vlákna v zobrazení vláken | Dokumentace Microsoftu'
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
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb1c3979b0505305fd4f6a600e3352c0d08955de
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766907"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Postupy: Hledání vlákna v zobrazení vláken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete vyhledat konkrétního vlákna v zobrazení vláken pomocí jeho ID nebo modul řetězec vlákna jako kritéria hledání. Můžete také zadat počáteční směr hledání. Pole v dialogovém okně zobrazí atributy zvoleném vlákně ve stromové struktuře vlákna.  
  
### <a name="to-search-for-a-thread-in-threads-view"></a>Hledání vlákna v zobrazení vláken  
  
1. Uspořádat okna tak tohoto nástroje Spy ++ a aktivní [zobrazení vláken](../debugger/threads-view.md) okna jsou viditelné.  
  
2. Z **hledání** nabídce zvolte **najít vlákno**.  
  
    [Dialogové okno vlákna hledání](../debugger/thread-search-dialog-box.md) otevře.  
  
3. Zadejte ID vlákna nebo řetězce modulu, jako kritéria hledání.  
  
4. Zrušte zaškrtnutí všech polí, u kterých nechcete k určení hodnot.  
  
   > [!TIP]
   >  Chcete-li najít všechna vlákna vlastní modul, zrušte **vlákna** textové pole a typ modulu název v **modulu** pole. Pak pomocí **najít další** pokračujte hledání vláken.  
  
5. Zvolte **nahoru** nebo **dolů** pro počáteční směr hledání.  
  
6. Klikněte na tlačítko **OK**.  
  
   Pokud se najde odpovídající vlákno je zvýrazněn v okně zobrazení vláken.



