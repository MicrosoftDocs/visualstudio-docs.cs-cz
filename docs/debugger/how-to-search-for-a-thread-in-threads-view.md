---
title: Hledání vlákna v zobrazení vláken | Microsoft Docs
description: Vyhledejte konkrétní vlákno v zobrazení vláken nástroje Spy + + pomocí jeho ID vlákna nebo řetězce modulu jako kritéria vyhledávání při ladění v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85d82897144a0ed366d95dfa590a09224a875f55
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99845058"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Postupy: Hledání vlákna v zobrazení vláken
Konkrétní vlákno můžete vyhledat v zobrazení vlákna pomocí jeho ID vlákna nebo řetězce modulu jako kritéria vyhledávání. Můžete také zadat počáteční směr hledání. Pole v dialogovém okně zobrazí atributy vybraného vlákna ve stromu vláken.

### <a name="to-search-for-a-thread-in-threads-view"></a>Hledání vlákna v zobrazení vláken

1. Uspořádejte okna tak, aby se zobrazilo okno pro zobrazení Spy + + a aktivní [vlákna](../debugger/threads-view.md) .

2. V nabídce **Hledat** vyberte možnost **Najít vlákno**.

    Otevře se [dialogové okno hledání vláken](../debugger/thread-search-dialog-box.md) .

3. Jako kritéria hledání zadejte ID vlákna nebo řetězec modulu.

4. Vymažte všechna pole, pro která nechcete zadávat hodnoty.

   > [!TIP]
   > Chcete-li najít všechna vlákna vlastněná modulem, zrušte zaškrtnutí políčka **vlákno** a zadejte název modulu do pole **modul** . Pak pokračujte v hledání vláken pomocí **find Next** .

5. Pro počáteční směr hledání vyberte **nahoru** nebo **dolů** .

6. Klikněte na **OK**.

   Pokud je nalezeno vyhovující vlákno, je zvýrazněno v okně zobrazení vláken.