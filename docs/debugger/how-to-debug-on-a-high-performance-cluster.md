---
title: Jak ladit cluster s vysokým výkonem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-performance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 905a196b0872ac0d8665293200837861adf49795
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350066"
---
# <a name="how-to-debug-on-a-high-performance-cluster-c-visual-basic-c"></a>Postupy: ladění v clusteru s vysokým výkonem (C#, Visual Basic, C++)

Ladění programu pro více procesů v clusteru s vysokým výkonem je jako ladění běžného programu na vzdáleném počítači. Existují však některé další okolnosti. Obecné požadavky na vzdálenou instalaci najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).

 Když ladíte cluster s vysokým výkonem, můžete použít všechna okna [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ladění a techniky, které jsou k dispozici pro vzdálené ladění. Vzhledem k tomu, že se jedná o vzdálené ladění, není k dispozici externí okno konzoly.

 Okno **vlákna** a okno **procesy** jsou obzvláště užitečné pro ladění paralelních aplikací. Tipy k použití těchto oken naleznete v tématu [How to: use the Process Window](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100)) a [Návod: ladit pomocí okna vlákna](../debugger/how-to-use-the-threads-window.md).

 Následující postupy ukazují některé techniky, které jsou zvláště užitečné pro ladění v clusteru s vysokým výkonem.

 Při ladění paralelní aplikace můžete chtít nastavit zarážku na konkrétní vlákno, proces nebo počítač. To můžete provést tak, že vytvoříte normální zarážku a pak přidáte filtr zarážky.

### <a name="to-open-the-breakpoint-filter-dialog-box"></a>Otevření dialogového okna filtr zarážek

1. Klikněte pravým tlačítkem myši na glyf zarážky v okně zdroje, v okně **zpětný překlad** , v okně **zásobník volání** nebo na okno **zarážky** .

2. V místní nabídce klikněte na **Filtr**. Tato možnost se může zobrazit na nejvyšší úrovni nebo v podnabídce v části **zarážky**.

### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>Nastavení zarážky na určitém počítači

1. Získat název počítače z okna **procesy** .

2. Vyberte zarážku a otevřete dialogové okno **Filtr zarážek** , jak je popsáno v předchozím postupu.

3. Do dialogového okna **Filtr zarážek** zadejte:

     Nazev_pocitace =*yourmachinename*

     Chcete-li vytvořit složitější filtr, můžete kombinovat klauzule pomocí `&` , operátoru a, operátoru `||` OR, `!` , operátor NOT a závorky.

4. Klikněte na **OK**.

### <a name="to-set-a-breakpoint-on-a-specific-process"></a>Nastavení zarážky pro určitý proces

1. Získá název procesu nebo ID procesu z okna **procesy** .

2. Vyberte zarážku a otevřete dialogové okno **Filtr zarážek** jako v prvním postupu.

3. Do dialogového okna **Filtr zarážek** zadejte:

     `ProcessName =`  *yourprocessname*

     —nebo—

     `ProcessID =`*yourprocessIDnumber*

     Chcete-li vytvořit složitější filtr, můžete kombinovat klauzule pomocí `&` , operátoru a, operátoru `||` OR, `!` , operátor NOT a závorky.

4. Klikněte na **OK**.

### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>Nastavení zarážky v konkrétním vlákně

1. Získá název vlákna nebo ID vlákna z okna **vlákna** .

2. Vyberte zarážku a otevřete dialogové okno **Filtr zarážek** , jak je popsáno v prvním postupu.

3. Do dialogového okna **Filtr zarážek** zadejte:

     `ThreadName =`*yourthreadname*

     —nebo—

     `ThreadID =`*yourthreadIDnumber*

     Chcete-li vytvořit složitější filtr, můžete kombinovat klauzule pomocí `&` , operátoru a, operátoru `||` OR, `!` , operátor NOT a závorky.

4. Klikněte na **OK**.

## <a name="example"></a>Příklad
 Následující příklad ukazuje, jak vytvořit filtr pro zarážku v počítači s názvem `marvin` a vlákno s názvem `fourier1` .

`(MachineName = marvin) & (ThreadName = fourier1)`

## <a name="see-also"></a>Viz také
- [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Vzdálené ladění](../debugger/remote-debugging.md)
- [Postupy: použití okna procesy](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100))
- [Začínáme s laděním vícevláknových aplikací](../debugger/get-started-debugging-multithreaded-apps.md)
- [Vlákna a procesy](/previous-versions/visualstudio/visual-studio-2010/ms164740(v=vs.100))
- [Použití zarážek](../debugger/using-breakpoints.md)