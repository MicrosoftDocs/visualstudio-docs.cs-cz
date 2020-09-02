---
title: 'Postupy: návrat do funkce, která se nazývá MFC, pokud je zastavená | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.mfc
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c19cbf6e892ba8b35f2b92ad9b86aa0b74a64810
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685887"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Postupy: Přechod zpět na funkci, která volala MFC při zastavení.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ZNAČTE
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce Nástroje klikněte na položku Nastavení importu a exportu. Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Pokud jste v nabídce **ladit** použili příkaz **Break** k zastavení programu a skončí v knihovně MFC a opravdu jste si jisti, že se jedná o váš kód, můžete použít okno zásobník volání a přejít zpět na svou funkci. Další informace naleznete v tématu [Postupy: použití okna zásobník volání](../debugger/how-to-use-the-call-stack-window.md).  
  
 Někdy může být váš kód v pumpě zpráv přerušen. V takovém případě není v zásobníku volání žádný uživatelský kód. Chcete-li se tomuto problému vyhnout, můžete místo příkazu **Break** použít zarážky (případně podmínky a počty přístupů). Další informace naleznete v tématu [zarážky a trasováním](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)).  
  
### <a name="to-navigate-to-the-function-from-which-mfc-was-called"></a>Pro přechod na funkci, ze které byla volána knihovna MFC  
  
- Použijte okno **zásobník volání** .  
  
## <a name="see-also"></a>Viz také  
 [Nejčastější dotazy k ladění nativního kódu](../debugger/debugging-native-code-faqs.md)   
 [Ladění nativního kódu](../debugger/debugging-native-code.md)
