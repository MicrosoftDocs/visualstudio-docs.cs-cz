---
title: Hledání procesu v zobrazení procesů | Microsoft Docs
description: Vyhledejte konkrétní proces v zobrazení procesů nástroje Spy + + pomocí jeho ID procesu nebo řetězce modulu jako kritéria vyhledávání při ladění v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85b2c2bab29316846620c7dbec935b41eec1d9df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99845071"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Postupy: Hledání procesu v zobrazení procesů
Konkrétní proces můžete vyhledat v zobrazení procesů pomocí jeho ID procesu nebo řetězce modulu jako kritéria vyhledávání. Můžete také zadat počáteční směr hledání. Pole v dialogovém okně zobrazí atributy vybraného procesu ve stromu procesu.

### <a name="to-search-for-a-process-in-processes-view"></a>Hledání procesu v zobrazení procesů

1. Uspořádejte okna tak, aby se zobrazila okna nástroje Spy + + a aktivní [procesy](../debugger/processes-view.md) .

2. V nabídce **Hledat** vyberte možnost **Najít proces** .

    Otevře se [dialogové okno hledání procesu](../debugger/process-search-dialog-box.md) .

3. Jako kritéria hledání zadejte ID procesu nebo řetězec modulu.

4. Vymažte všechna pole, pro která nechcete zadávat hodnoty.

   > [!TIP]
   > Chcete-li najít všechny procesy, které vlastní modul, zrušte zaškrtnutí políčka **proces** a do pole **modul** zadejte název modulu. Pak pokračujte v hledání procesů pomocí **Najít další** .

5. Pro počáteční směr hledání vyberte **nahoru** nebo **dolů** .

6. Klikněte na **OK**.

   Pokud se najde stejný proces, zvýrazní se v okně **zobrazení procesu** .