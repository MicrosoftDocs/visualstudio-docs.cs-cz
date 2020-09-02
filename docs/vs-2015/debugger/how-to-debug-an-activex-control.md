---
title: 'Postupy: ladění ovládacího prvku ActiveX | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vc.controls.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9524ab08ab955609f29f437e8a1576af02738aa1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704453"
---
# <a name="how-to-debug-an-activex-control"></a>Postupy: Ladění ovládacího prvku ActiveX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ZNAČTE
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce Nástroje klikněte na položku Nastavení importu a exportu. Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Chcete-li ladit ovládací prvek ActiveX, je nutné zadat kontejner (spustitelný soubor), v němž bude ovládací prvek spuštěn.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>Určení kontejneru pro relaci ladění  
  
1. V Průzkumník řešení vyberte projekt.  
  
2. V nabídce **zobrazení** klikněte na položku **stránky vlastností**.  
  
3. V dialogovém okně **stránky vlastností projektu** otevřete složku **Vlastnosti konfigurace** a vyberte možnost **ladění**.  
  
4. V kategorii **ladění** vyhledejte vlastnost **Command** .  
  
5. Zadejte název cesty pro kontejner. Například C:\Program Files\Internet Explorer\IEXPLORE.EXE.  
  
6. Pokud jako kontejner určíte aplikaci Internet Explorer a používáte službu Active Desktop, zadejte `/new` do pole **argumenty příkazu** .  
  
7. Klikněte na **OK**.  
  
     Pokud nezadáte kontejner do dialogového okna **stránky vlastností projektu** , můžete zadat kontejner při zahájení ladění. Když vyberete příkaz pro spuštění pro spuštění ladění, zobrazí se [dialogové okno spustitelný soubor pro relaci ladění](../debugger/executable-for-debugging-session-dialog-box.md) . Zadejte název cesty kontejneru v dialogovém okně.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky ActiveX](https://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)   
 [Testování vlastností a událostí pomocí kontejneru testů](https://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917)   
 [Ladění modelu COM a ActiveX](../debugger/com-and-activex-debugging.md)   
 [Ladění v sadě Visual Studio](../debugger/debugging-in-visual-studio.md)
