---
title: 'Postupy: vystoupení ze spravovaného kódu, pokud v okně zásobník volání chybějí nativní rámce | Dokumentace Microsoftu'
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
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f67dcff047b29d2fb51044e6c0973c5b6e6b747
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788495"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Postupy: Vystoupení ze spravovaného kódu, pokud v okně Zásobník volání chybějí nativní rámce.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud má váš kód nativní rámce, které jsou viditelné ve **zásobník volání** okno krokování mimo spravovaný kód může vést k neočekávaným výsledkům. Jako alternativní řešení můžete použít zarážku místo **Krokovat s Vystoupením**.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Chcete-li vystoupení ze spravovaného kódu, pokud zobrazení zásobníku volání chybějí nativní rámce  
  
1.  V nativním kódu nastavte zarážku umístění po volání spravovaného kódu.  
  
2.  Na **ladění** nabídce zvolte **pokračovat**.  
  
     Po dokončení spravovaných volání provádění zastaví na zarážce v nativním kódu.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Použití okna Zásobník volání](../debugger/how-to-use-the-call-stack-window.md)





