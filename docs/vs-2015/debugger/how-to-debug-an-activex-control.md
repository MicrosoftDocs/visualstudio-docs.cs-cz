---
title: 'Postupy: ladění ovládacího prvku ActiveX | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: f1e43d94807fa28f86193fc7818b77887d797772
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745159"
---
# <a name="how-to-debug-an-activex-control"></a>Postupy: Ladění ovládacího prvku ActiveX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

POZNÁMKA:]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte nastavení importu a exportu v nabídce Nástroje. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Chcete-li ladit ovládací prvek ActiveX, je nutné zadat (spustitelného souboru) pro ovládací prvek pro spuštění v kontejneru.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>K určení kontejneru se pro relaci ladění  
  
1.  V Průzkumníku řešení vyberte projekt.  
  
2.  Z **zobrazení** nabídce zvolte **stránky vlastností**.  
  
3.  V **stránky vlastností projektu** dialogovém okně Otevřít **vlastnosti konfigurace** a pak zvolte položku **ladění**.  
  
4.  V části **ladění** kategorie, vyhledejte **příkaz** vlastnost.  
  
5.  Zadejte název cesty pro kontejner. Například C:\Program Files\Internet Explorer\IEXPLORE. SOUBOR EXE.  
  
6.  Pokud zadáte jako kontejner aplikace Internet Explorer a používáte aktivní plochu, zadejte `/new` v **argumenty příkazu** pole.  
  
7.  Klikněte na tlačítko **OK**.  
  
     Pokud nezadáte kontejner ve službě **stránky vlastností projektu** dialogovém okně můžete zadat kontejner při zahájení ladění. Po výběru příkazu ke spuštění pro spuštění ladění, [spustitelný soubor pro dialogové okno ladění relace](../debugger/executable-for-debugging-session-dialog-box.md) se zobrazí. V dialogovém okně zadejte název cesty kontejneru.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky ActiveX](http://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)   
 [Testování vlastností a událostí pomocí testovacího kontejneru](http://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917)   
 [COM a ActiveX ladění](../debugger/com-and-activex-debugging.md)   
 [Ladění v sadě Visual Studio](../debugger/debugging-in-visual-studio.md)



