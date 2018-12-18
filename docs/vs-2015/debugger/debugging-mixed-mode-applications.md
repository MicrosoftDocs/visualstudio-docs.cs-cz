---
title: Ladění ve smíšeném režimu aplikací | Dokumentace Microsoftu
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
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging, property evaluation
- Call Stack window
- mixed-mode debugging
- Call Stack window, mixed-mode debugging
- debugging managed code, mixed code
- mixed-mode debugging, call stack
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b176ae4a911e6948634cda2330d0c895f8b61cfd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773338"
---
# <a name="debugging-mixed-mode-applications"></a>Ladění aplikací ve smíšeném režimu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikace pracující v kombinovaném režimu je libovolná aplikace, která kombinuje nativní kód (jazyk C++) se spravovaným kódem (například jazyk Visual Basic, Visual C# nebo C++, který běží na modulu CLR). Ladění aplikací ve smíšeném režimu je z velké části transparentní [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]; není příliš odlišné od ladění režimu jedné aplikace. Existuje však několik důležitých informací.  
  
## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>Povolení příkazů Edit a Continue jazyka C++ v kombinovaném režimu ladění  
  
-   Pokud chcete používat příkazy Edit a Continue (Upravit a pokračovat) jazyka C++ v sadě Visual Studio 2013, budete muset přejít na starší verzi modulu pro ladění. Zobrazit [přepnutí do spravovaného režimu kompatibility v sadě Visual Studio 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013.aspx) na blogu Microsoft Application Lifecycle Management.  
  
## <a name="property-evaluation-in-mixed-mode-applications"></a>Vyhodnocení vlastnosti v aplikacích pracujících v kombinovaném režimu  
 Vyhodnocení vlastností ladicím programem je v aplikaci pracující v kombinovaném režimu náročná operace. V důsledku toho se operace ladění, jako je například krokování, mohou zdát pomalé. Další informace najdete v tématu [krokování](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9). Pokud se při ladění v kombinovaném režimu setkáváte s nízkým výkonem, lze vyhodnocení vlastností vypnout v oknech ladicího programu.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
#### <a name="to-turn-off-property-evaluation"></a>Chcete-li vypnout vyhodnocení vlastností  
  
1. Na **nástroje** nabídce zvolte **možnosti**.  
  
2. V **možnosti** dialogovém okně Otevřít **ladění** a pak zvolte položku **Obecné** kategorie.  
  
3. Zrušte **povolit vyhodnocování vlastností a jiných implicitních volání funkcí** zaškrtávací políčko.  
  
   Vzhledem k tomu, že se nativní a spravované zásobníky volání liší, ladicí program nemůže vždy pro smíšený kód stanovit úplný zásobník volání. Když nativní kód volá spravovaný kód, lze zaznamenat některé nesrovnalosti. Další informace najdete v tématu [smíšený kód a chybějící informace v okně zásobník volání](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).  
  
## <a name="see-also"></a>Viz také  
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)



