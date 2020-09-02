---
title: 'Postupy: použití okna Registry | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.registers
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 233092af638824c462a6d9a47865a1c6f5fd9397
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697470"
---
# <a name="how-to-use-the-registers-window"></a>Postupy: Použití okna Registry
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno Registry je dostupné pouze v případě, že je povoleno ladění na úrovni adres v dialogovém okně **Možnosti** , uzel **ladění** , **Obecné** kategorie.  
  
 V okně **Registry** se zobrazí obsah registru. Pokud ponecháte okno **Registry** otevřené v průběhu provádění programu, můžete zobrazit změny hodnot registru při spuštění kódu. Hodnoty, které se nedávno změnily, se zobrazí červeně. Hodnoty registru můžete upravovat. Další informace najdete v tématu [Postupy: Úprava hodnoty registru](../debugger/how-to-edit-a-register-value.md).  
  
 Chcete-li snížit přehlednost, okno **Registry** uspořádá Registry do skupin, které se liší podle typu platformy a procesoru. Můžete zobrazit nebo skrýt skupiny podle svých potřeby. Další informace najdete v tématu [Postup: zobrazení a skrytí skupin registrů](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Úvod do konceptů za registry a v okně Registry najdete v části [základy ladění: Registry Window](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-registers-window"></a>Zobrazení okna Registry  
  
- V nabídce **ladit** zvolte **okna**a pak zvolte **Registry**.  
  
     Ladicí program musí být spuštěný nebo v režimu přerušení.  
  
    > [!NOTE]
    > Informace o registraci nejsou k dispozici pro skripty nebo aplikace SQL.  
  
## <a name="see-also"></a>Viz také  
 [Základy ladění: okno Registry](../debugger/debugging-basics-registers-window.md)   
 [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)   
 [Základní informace k ladění: okno registrů](../debugger/debugging-basics-registers-window.md)
