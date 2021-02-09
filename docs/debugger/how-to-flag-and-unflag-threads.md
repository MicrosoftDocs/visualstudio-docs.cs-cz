---
title: Označit a zrušit označení vláken | Microsoft Docs
description: Naučte se označit nebo zrušit označení vláken v aplikaci Visual Studio. Označit nebo zrušit označení vlákna, několik vláken nebo všech vláken. Označení pouze kódu nebo těch, které jsou přidruženy k modulu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5f31bb73b4a22a11235e471dfa1fa99545e422e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877600"
---
# <a name="how-to-flag-and-unflag-threads-c-visual-basic-c"></a>Postupy: označení a odoznačení vláken vlákna (C#, Visual Basic, C++)

Můžete označit vlákno, které chcete poskytnout zvláštní pozornost, a to tak, že ho označíte ikonou v podoknech **vlákna**, **paralelní zásobníky** (zobrazení vlákna), **paralelní kukátko** a **vlákna GPU** . Tato ikona vám může pomáhat a jiným odlišit vlákna označená příznakem z jiných vláken.

Vlákna označená příznakem také dostanou zvláštní zpracování v seznamu **vláken** na panelu nástrojů **umístění ladění** a v ostatních oknech s více vlákny pro ladění. Můžete zobrazit všechna vlákna nebo pouze vlákna označená příznakem v seznamu **vláken** nebo v jiných oknech.

### <a name="to-flag-or-unflag-a-thread"></a>Označení nebo odoznačení vlákna vláknem

- V okně **vlákna** nebo **paralelní sledování** Najděte vlákno, které vás zajímá, a kliknutím na ikonu příznak vyberte nebo zrušte zaškrtnutí tohoto příznaku.
- V okně **paralelní zásobníky** klikněte pravým tlačítkem na vlákno nebo skupinu vláken a vyberte **příznak \<thread> /** nebo zrušit **příznak/ \<thread>**.

### <a name="to-unflag-all-threads"></a>Chcete-li zrušit označení všech vláken

- V okně **vlákna** klikněte pravým tlačítkem na libovolné vlákno a pak klikněte na zrušit **označení všech vláken**.
- V okně **paralelní sledování** vyberte všechna vlákna označená příznakem, potom klikněte pravým tlačítkem a vyberte zrušit **označení**.

### <a name="to-display-only-flagged-threads"></a>Chcete-li zobrazit pouze vlákna označená příznakem

- Vyberte tlačítko **Zobrazit pouze vlákna označená příznakem** v jednom z oken ladění s více vlákny.

### <a name="to-flag-just-my-code"></a>Označení Pouze můj kód

1. Na panelu nástrojů v horní části okna **vlákna** klikněte na ikonu příznak.

2. V rozevíracím seznamu klikněte na **příznak pouze můj kód**.

### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Označení vláken, která jsou přidružena k vybraným modulům

1. Na panelu nástrojů okna **vlákna** klikněte na ikonu příznak.

2. V rozevíracím seznamu klikněte na možnost **Označit vlastní výběr modulu**.

3. V dialogovém okně **Vybrat moduly** vyberte moduly, které chcete.

4. Volitelné Do **vyhledávacího** pole zadejte řetězec, který bude hledat konkrétní moduly.

5. Klikněte na **OK**.

## <a name="see-also"></a>Viz také
- [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Začínáme s laděním vícevláknových aplikací](../debugger/get-started-debugging-multithreaded-apps.md)
- [Návod: Ladění vícevláknových aplikací pomocí okna vlákna](../debugger/how-to-use-the-threads-window.md)