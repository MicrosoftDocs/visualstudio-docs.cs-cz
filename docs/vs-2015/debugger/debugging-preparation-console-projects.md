---
title: 'Příprava ladění: projekty konzoly | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ac87f6c5ef5fcf9fc7ca5532fe7436dedb8ba97
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691217"
---
# <a name="debugging-preparation-console-projects"></a>Příprava ladění: projekty konzoly
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Příprava na ladění projektu konzoly je podobná přípravě ladění projektu Windows, s některými dalšími důležitými informacemi. Další informace najdete v tématech [model Windows Forms aplikace](../debugger/debugging-preparation-windows-forms-applications.md)a [příprava ladění: model Windows Forms aplikace (.NET)](https://msdn.microsoft.com/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5). Z důvodu podobnosti všech konzolových aplikací toto téma popisuje následující typy projektů:  
  
- Konzolová aplikace jazyka C#  
  
- Visual Basic Konzolová aplikace  
  
- Konzolová aplikace C++ (.NET)  
  
- Konzolová aplikace C++ (Win32)  
  
  Možná budete muset zadat argumenty příkazového řádku pro konzolovou aplikaci. Další informace naleznete v tématu [nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [nastavení projektu pro Visual Basic konfigurace ladění](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)nebo [nastavení projektu pro konfiguraci ladění jazyka C#](../debugger/project-settings-for-csharp-debug-configurations.md).  
  
  Stejně jako všechny vlastnosti projektu jsou tyto argumenty trvalé mezi relacemi ladění a mezi relacemi sady Visual Studio. Proto pokud je Konzolová aplikace ta, kterou jste dříve laděni, pamatujte, že v dialogovém okně ** \<Project> stránky vlastností** mohou být zadány argumenty z předchozích relací.  
  
  Konzolová aplikace používá okno **konzoly** k přijetí vstupu a zobrazení výstupních zpráv. Chcete-li zapisovat do okna **konzoly** , aplikace musí místo objektu Debug použít objekt **konzoly** . Chcete-li zapisovat do okna **výstup aplikace Visual Studio** , použijte objekt ladění, jako obvykle. Ujistěte se, že víte, kam vaše aplikace píšete, nebo že chcete zprávy vyhledat na nesprávném místě. Další informace naleznete v tématu [Třída konzoly](https://msdn.microsoft.com/library/system.console.aspx), [třída ladění](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx)a [okno výstup](../ide/reference/output-window.md).  
  
## <a name="starting-the-application"></a>Spuštění aplikace  
 Po spuštění některých konzolových aplikací se jejich spuštění dokončí a pak se ukončí. K tomuto chování nemusí dodávat dostatek času k přerušení provádění a ladění. Aby bylo možné ladit aplikaci, použijte jeden z následujících postupů pro spuštění aplikace:  
  
- Vaše aplikace se spustí a spustí, dokud nebude dosaženo zarážky.  
  
- Vaše aplikace se spustí a okamžitě se přeruší na první řádek zdrojového kódu.  
  
- V okně zdrojového kódu klikněte pravým tlačítkem myši na řádek a vyberte možnost **Spustit ke kurzoru**.  
  
   Vaše aplikace se spustí a spustí na vybraný řádek nebo na zarážku, pokud se zarážka narazí před řádek.  
  
  Při ladění konzolové aplikace je vhodné spustit aplikaci z příkazového řádku, nikoli ze sady Visual Studio. V takovém případě můžete aplikaci spustit z příkazového řádku a připojit k ní ladicí program sady Visual Studio. Další informace najdete v tématu [připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
  Při spuštění konzolové aplikace ze sady Visual Studio se okno **konzoly** někdy zobrazuje v okně sady Visual Studio. Pokud se pokusíte spustit konzolovou aplikaci ze sady Visual Studio a nic se nestane, zkuste přesunout okno aplikace Visual Studio.  
  
## <a name="see-also"></a>Viz také  
 [Ladění nativního kódu](../debugger/debugging-native-code.md)   
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)   
 [Visual C++ typy projektů](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Typy projektů jazyka C#, F # a Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)
