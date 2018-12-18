---
title: 'Příprava ladění: Formulářová aplikace Windows | Dokumentace Microsoftu'
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
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [J#], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4997aa5f184fb5d6f0e9a3ccd08a9d829c26a0cc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765632"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Příprava na ladění: Formulářová aplikace Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Šablona projektu Windows Forms vytvoří aplikace modelu Windows Forms. Ladění tohoto typu aplikace v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] je jednoduché. Další informace najdete v tématu [vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Při vytváření projektu Windows Forms pomocí šablony projektu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automaticky vytvoří požadované nastavení konfigurace Debug a Release. V případě potřeby můžete tato nastavení změnit. Tato nastavení lze změnit v  **\<název projektu > stránky vlastností** dialogové okno (**Můj projekt** v jazyce Visual Basic).  
  
 Další informace najdete v tématu [doporučené nastavení vlastností](../debugger/managed-debugging-recommended-property-settings.md).  
  
 Následující tabulka obsahuje jeden další vlastnost doporučené nastavení.  
  
### <a name="configuration-properties-in-debug-tab"></a>Vlastnosti konfigurace na kartě ladění  
  
|**Název vlastnosti**|**Nastavení**|  
|-----------------------|-----------------|  
|**Spustit akci**|– Nastavte na **spustit projekt** většinu času. Nastavte na **externí program Start** Pokud budete chtít spustit jiné spustitelný soubor při spuštění ladění (většinou pro ladění knihoven DLL).|  
  
 Můžete ladit aplikace Windows Forms z uvnitř [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], nebo připojením k již běžícímu aplikace. Další informace o připojení najdete v tématu [připojení k běžící procesy](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Chcete-li ladit C#, F#, nebo aplikaci Windows Forms jazyka Visual Basic  
  
1. Otevřete projekt v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
2. Podle potřeby vytvořte zarážky.  
  
    Protože aplikace Windows Forms jsou založené na událostech, vaše zarážky přejde do kódu obslužné rutiny události nebo do metody volané kódem obslužné rutiny události. Typické události, ve které chcete umístit zarážky zahrnují:  
  
   1. Události související s ovládacím prvkem, jako je například klikněte na Enter, atd.  
  
   2. Události související s aplikací při spuštění a vypnutí, jako je zatížení, aktivováno atd.  
  
   3. Fokus a události ověřování.  
  
      Další informace najdete v tématu [vytváření obslužných rutin událostí ve Windows Forms](http://msdn.microsoft.com/library/6514e530-c6b8-489c-a8d2-eda7b7072701).  
  
3. Na **ladění** nabídky, klikněte na tlačítko **Start**.  
  
4. Ladění pomocí technik popsaných v [základy ladicího programu](../debugger/debugger-basics.md).  
  
## <a name="see-also"></a>Viz také  
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)   
 [C#, F#a typy projektů jazyka Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Postupy: Konfigurace nastavení ladění a verzí](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Nastavení projektu pro jazyk C# konfiguraci ladění](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Konfigurace ladění projektu v jazyce Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Forms](http://msdn.microsoft.com/library/627df1e9-b254-41af-bbac-9a4f02810c54)



