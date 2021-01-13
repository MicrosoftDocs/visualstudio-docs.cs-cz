---
title: Přepnutí na jiné vlákno během ladění
description: Přečtěte si různé metody pro přepnutí na jiné vlákno při ladění vícevláknové aplikace v aplikaci Visual Studio.
ms.custom: SEO-VS-2020, seodec18
ms.date: 04/27/2017
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8df37beafe7a6c8f88631568ea9eb36394c105a5
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150714"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>Postupy: přepnutí na jiné vlákno během ladění v aplikaci Visual Studio (C#, Visual Basic, C++)
Při ladění vícevláknové aplikace můžete použít některou z několika metod k přepnutí z vlákna, se kterým jste pracovali, s jiným vláknem.

> [!NOTE]
> Chcete-li řídit pořadí, ve kterém jsou vlákna spouštěna, je nutné [zablokovat a uvolnit vlákna](../debugger/get-started-debugging-multithreaded-apps.md).

Při prozkoumávání vláken v editoru kódu a různých oknech s více vlákny pro ladění, žlutá šipka indikuje aktuální vlákno. Zelená šipka s kudrlinkou zakončením označuje, že neaktuální vlákno má aktuální kontext ladicího programu.

### <a name="to-switch-to-any-thread-that-appears"></a>Přepnutí na jakékoli vlákno, které se zobrazí

- V okně **vlákna** nebo **paralelní sledování** dvakrát klikněte na vlákno.

### <a name="to-switch-to-a-thread-in-a-source-window"></a>Přepnutí na vlákno v okně zdrojového kódu

- V levém hřbetu klikněte pravým tlačítkem myši na ![značku vlákna](../debugger/media/dbg-thread-marker.png "ThreadMarker")ikony vlákna, přejděte na možnost **Přepnout na** a potom klikněte na název vlákna, na které chcete přepnout. Místní nabídka zobrazuje pouze vlákna na daném konkrétním místě.

     Pokud se nezobrazí žádné značky vlákna, klikněte pravým tlačítkem myši v okně **vlákna** a ověřte, zda je vybrána možnost **Zobrazit vlákna ve zdroji** .

### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Přepnutí na vlákno na panelu nástrojů umístění ladění

1. Na panelu nástrojů **umístění ladění** klikněte na seznam **vláken** .

2. V seznamu klikněte na vlákno, na které chcete přepnout.

## <a name="see-also"></a>Viz také
- [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)
