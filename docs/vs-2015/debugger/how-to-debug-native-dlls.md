---
title: 'Postupy: ladění nativních knihoven DLL | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 16a533b27e619526edab71374d922e68baf0a4b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702681"
---
# <a name="how-to-debug-native-dlls"></a>Postupy: Ladění nativních knihoven DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce Nástroje klikněte na položku Nastavení importu a exportu. Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Při ladění knihovny DLL můžete spustit ladění z:  
  
- Projekt použitý k vytvoření spustitelného souboru, který volá knihovnu DLL.  
  
  \- ani  
  
- Projekt použitý k vytvoření samotné knihovny DLL.  
  
  Pokud máte projekt, který jste použili k vytvoření spustitelného souboru, spusťte ladění z tohoto projektu. Pak můžete otevřít zdrojový soubor pro knihovnu DLL a nastavit zarážky v tomto souboru, i když není součástí projektu, který jste použili k vytvoření spustitelného souboru. Další informace naleznete v tématu [zarážky](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
  Pokud spustíte ladění z projektu, který vytváří knihovnu DLL, je nutné zadat spustitelný soubor, který chcete použít při ladění knihovny DLL.  
  
### <a name="to-specify-an-executable-for-the-debug-session"></a>Určení spustitelného souboru pro relaci ladění  
  
1. V **Průzkumník řešení**vyberte projekt, který vytváří knihovnu DLL.  
  
2. V nabídce **zobrazení** klikněte na položku**stránky vlastností**.  
  
3. V dialogovém okně **stránky vlastností** otevřete složku **Vlastnosti konfigurace** a vyberte kategorii **ladění** .  
  
4. Do **příkazového řádku** zadejte název cesty pro kontejner. Například C:\Program Files\MyApplication\MYAPP.EXE.  
  
5. V poli **argumenty příkazu** zadejte všechny potřebné argumenty pro spustitelný soubor.  
  
   Pokud nezadáte spustitelný soubor do dialogového okna**stránky vlastností** _projektu_, při spuštění ladění se zobrazí [dialogové okno spustitelný soubor pro relaci ladění](../debugger/executable-for-debugging-session-dialog-box.md) .  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Ladění v sadě Visual Studio](../debugger/debugging-in-visual-studio.md)
