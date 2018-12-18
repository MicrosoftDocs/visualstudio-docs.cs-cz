---
title: 'Postupy: ladění na vysoký výkon clusteru | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-perfomance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75f2a96df18137f04b8b7637940c70378842e23d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747724"
---
# <a name="how-to-debug-on-a-high-performance-cluster"></a>Postupy: Ladění na klastru s vysokým výkonem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ladění programu multiprocesingem na vysoký výkon clusteru je jako ladění program ve vzdáleném počítači. Existuje ale několik dalších důležitých informací. Obecné nastavení vzdálené požadavky najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).  
  
 Při ladění na vysoký výkon clusteru můžete použít všechny [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ladění systému windows a techniky, které jsou k dispozici pro vzdálené ladění. Vzhledem k tomu, že ladíte vzdáleně, ale okno externí konzoly není k dispozici.  
  
 **Vlákna** okno a **procesy** jsou obzvláště užitečné pro ladění paralelních aplikací. Tipy k používání těchto oken naleznete v tématu [postupy: použití okna procesy](http://msdn.microsoft.com/en-us/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7) a [postupy: použití okna vláken](../debugger/how-to-use-the-threads-window.md).  
  
 Následující postupy ukazují některé techniky, které jsou obzvláště užitečné pro ladění na vysoký výkon clusteru.  
  
 Při ladění paralelní aplikace můžete nastavit zarážku na konkrétní vlákno, proces nebo počítače. Můžete to provést vytvořením normální zarážky a následným přidáním filtru zarážky.  
  
### <a name="to-open-the-breakpoint-filter-dialog-box"></a>Chcete-li otevřít dialogové okno Filtr zarážek  
  
1.  Klikněte pravým tlačítkem na piktogram zarážky v okně zdroje **zpětný překlad** okně **zásobník volání** okna, nebo **zarážky** okno.  
  
2.  V místní nabídce klikněte na tlačítko **filtr**. Tato možnost může zobrazit v nejvyšší úrovni nebo v podnabídce v části **zarážky**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>Chcete-li nastavit zarážku v určitém počítači  
  
1.  Získejte název počítače z **procesy** okna.  
  
2.  Vyberte zarážku a otevřete **filtr zarážek** dialogovému oknu, jak je popsáno v předchozím postupu.  
  
3.  V **filtr zarážek** dialogové okno, zadejte:  
  
     MachineName =*yourmachinename*  
  
     Chcete-li vytvořit složitější filtr, můžete kombinovat klauzule pomocí `&`, operátoru AND `||`, operátoru OR `!`, operátoru NOT a závorek.  
  
4.  Klikněte na tlačítko **OK**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-process"></a>Nastavení zarážky v konkrétním procesu  
  
1.  Získejte název procesu nebo ID procesu z **procesy** okna.  
  
2.  Vyberte zarážku a otevřete **filtr zarážek** dialogové okno stejně jako v prvním postupu.  
  
3.  V **filtr zarážek** dialogové okno, zadejte:  
  
     `ProcessName =`  *yourprocessname*  
  
     —nebo—  
  
     `ProcessID =` *yourprocessIDnumber*  
  
     Chcete-li vytvořit složitější filtr, můžete kombinovat klauzule pomocí `&`, operátoru AND `||`, operátoru OR `!`, operátoru NOT a závorek.  
  
4.  Klikněte na tlačítko **OK**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>Nastavení zarážky v konkrétním vlákně  
  
1.  Získejte název vlákna nebo ID vlákna z **vlákna** okna.  
  
2.  Vyberte zarážku a otevřete **filtr zarážek** dialogovému oknu, jak je popsáno v prvním postupu.  
  
3.  V **filtr zarážek** dialogové okno, zadejte:  
  
     `ThreadName =` *yourthreadname*  
  
     —nebo—  
  
     `ThreadID =` *yourthreadIDnumber*  
  
     Chcete-li vytvořit složitější filtr, můžete kombinovat klauzule pomocí `&`, operátoru AND `||`, operátoru OR `!`, operátoru NOT a závorek.  
  
4.  Klikněte na tlačítko **OK**.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit filtr pro zarážku v počítači s názvem `marvin` a vlákno s názvem `fourier1`.  
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## <a name="see-also"></a>Viz také  
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Vzdálené ladění](../debugger/remote-debugging.md)   
 [Postupy: použití okna procesy](http://msdn.microsoft.com/en-us/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [Postupy: použití okna vláken](../debugger/how-to-use-the-threads-window.md)   
 [Vláken a procesů](http://msdn.microsoft.com/en-us/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [Použití zarážek](../debugger/using-breakpoints.md)



