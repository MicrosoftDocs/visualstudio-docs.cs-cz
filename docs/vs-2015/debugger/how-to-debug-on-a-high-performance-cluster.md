---
title: 'Postupy: ladění v clusteru s vysokým výkonem | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-performance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f4487b168c3d405b2449bcfb9515e60f0ea67ed1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702694"
---
# <a name="how-to-debug-on-a-high-performance-cluster"></a>Postupy: Ladění na klastru s vysokým výkonem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ladění programu pro více procesů v clusteru s vysokým výkonem je jako ladění běžného programu na vzdáleném počítači. Existují však některé další okolnosti. Obecné požadavky na vzdálenou instalaci najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).  
  
 Když ladíte cluster s vysokým výkonem, můžete použít všechna okna [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ladění a techniky, které jsou k dispozici pro vzdálené ladění. Vzhledem k tomu, že se jedná o vzdálené ladění, není k dispozici externí okno konzoly.  
  
 Okno **vlákna** a okno **procesy** jsou obzvláště užitečné pro ladění paralelních aplikací. Tipy pro použití těchto oken naleznete v tématu [How to: use](https://msdn.microsoft.com/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7) a Process Window a [How to: use the Threads Window](../debugger/how-to-use-the-threads-window.md).  
  
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
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## <a name="see-also"></a>Viz také  
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Vzdálené ladění](../debugger/remote-debugging.md)   
 [Postupy: použití okna procesy](https://msdn.microsoft.com/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [Postupy: použití okna vláken](../debugger/how-to-use-the-threads-window.md)   
 [Vlákna a procesy](https://msdn.microsoft.com/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [Použití zarážek](../debugger/using-breakpoints.md)
