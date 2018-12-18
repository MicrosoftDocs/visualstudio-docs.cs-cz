---
title: 'Postupy: ladění nativních knihoven DLL | Dokumentace Microsoftu'
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
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- DLLs, debugging
- executable files, specifying for debug sessions
ms.assetid: 76b34d15-a66d-4963-842e-c8b955c81696
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6577395d33d9004d8f17d91f273e3a53e7a3897d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757480"
---
# <a name="how-to-debug-native-dlls"></a>Postupy: Ladění nativních knihoven DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte nastavení importu a exportu v nabídce Nástroje. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Při ladění knihovny DLL ladění lze spustit z:  
  
- Projekt pro vytvoření spustitelného souboru, který volá knihovnu DLL.  
  
  \- nebo –  
  
- Projekt použitý k vytvoření samotná knihovna DLL.  
  
  Pokud máte projekt použitý k vytvoření spustitelného souboru, spusťte ladění z tohoto projektu. Můžete otevřít zdrojový soubor pro knihovnu DLL a nastavit zarážky v souboru, i když není součástí projektu použít k vytvoření spustitelného souboru. Další informace najdete v tématu [zarážky](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
  Pokud spustíte ladění z projektu, který vytvoří knihovnu DLL, je nutné zadat spustitelný soubor, který chcete použít v ladění knihovny DLL.  
  
### <a name="to-specify-an-executable-for-the-debug-session"></a>Můžete zadat spustitelný soubor pro relaci ladění  
  
1. V **Průzkumníka řešení**, vyberte projekt, který vytvoří knihovnu DLL.  
  
2. Z **zobrazení** nabídce zvolte**stránky vlastností**.  
  
3. V **stránky vlastností** dialogovém okně Otevřít **vlastnosti konfigurace** a pak zvolte položku **ladění** kategorie.  
  
4. V **příkaz** , zadejte název cesty pro kontejner. Například C:\Program Files\MyApplication\MYAPP. SOUBOR EXE.  
  
5. V **argumenty příkazu** zadejte všechny potřebné argumenty pro spustitelný soubor.  
  
   Pokud není zadán spustitelný soubor _projektu_**stránky vlastností** dialogovém okně [spustitelný soubor pro dialogové okno ladění relace](../debugger/executable-for-debugging-session-dialog-box.md) se zobrazí při spuštění ladění.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Ladění v sadě Visual Studio](../debugger/debugging-in-visual-studio.md)



