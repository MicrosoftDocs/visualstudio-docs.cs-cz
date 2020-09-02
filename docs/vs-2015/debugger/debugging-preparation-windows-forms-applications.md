---
title: 'Příprava ladění: model Windows Forms aplikace | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 5b11855fbd19dc464f92b4339684ef8346556c21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691153"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Příprava na ladění: Formulářová aplikace Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Šablona projektu model Windows Forms vytvoří aplikaci model Windows Forms. Ladění tohoto typu aplikace v nástroji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] je jednoduché. Další informace naleznete v tématu [Vytvoření projektu aplikace pro systém Windows](https://msdn.microsoft.com/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Při vytváření projektu model Windows Forms se šablonou projektu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automaticky vytvoří požadované nastavení pro ladění a vydání. V případě potřeby můžete tato nastavení změnit. Tato nastavení lze změnit v dialogovém okně ** \<project name> stránky vlastností** (**můj projekt** v Visual Basic).  
  
 Další informace najdete v tématu [Nastavení Doporučené vlastnosti](../debugger/managed-debugging-recommended-property-settings.md).  
  
 V následující tabulce je uvedeno jedno další nastavení Doporučené vlastnosti.  
  
### <a name="configuration-properties-in-debug-tab"></a>Vlastnosti konfigurace na kartě ladění  
  
|**Název vlastnosti**|**Nastavení**|  
|-----------------------|-----------------|  
|**Spustit akci**|-Nastavte na hodnotu **spustit projekt, a** to ve většinu času. Nastavte na **spustit externí program** , pokud chcete spustit další spustitelný soubor při spuštění ladění (obvykle pro ladění knihoven DLL).|  
  
 Můžete ladit model Windows Forms aplikace zevnitř [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nebo připojením k již spuštěné aplikaci. Další informace o připojení najdete v tématu [připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Ladění aplikace jazyka C#, F # nebo Visual Basic model Windows Forms  
  
1. Otevřete projekt v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
2. V případě potřeby vytvořte zarážky.  
  
    Vzhledem k tomu, že aplikace model Windows Forms jsou založené na událostech, vaše zarážky budou přecházet do kódu obslužné rutiny události nebo do metod volaných kódem obslužné rutiny události. Mezi obvyklé události, do kterých se mají umístit zarážky, patří:  
  
   1. Události přidružené k ovládacímu prvku, jako je například Click, ENTER atd.  
  
   2. Události spojené s spuštěním a vypnutím aplikace, jako je například Load, aktivované atd.  
  
   3. Události fokusu a ověření.  
  
      Další informace naleznete v tématu [vytváření obslužných rutin událostí v model Windows Forms](https://msdn.microsoft.com/library/6514e530-c6b8-489c-a8d2-eda7b7072701).  
  
3. V nabídce **ladit** klikněte na tlačítko **Start**.  
  
4. Ladění pomocí techniků popsaných v tématu [základní informace o ladicím programu](../debugger/debugger-basics.md).  
  
## <a name="see-also"></a>Viz také  
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)   
 [Typy projektů jazyka C#, F # a Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Postupy: nastavení konfigurace ladění a vydání](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Nastavení projektu pro konfiguraci ladění v jazyce C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Nastavení projektu pro konfiguraci Visual Basicho ladění](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Připojit ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Forms](https://msdn.microsoft.com/library/627df1e9-b254-41af-bbac-9a4f02810c54)
