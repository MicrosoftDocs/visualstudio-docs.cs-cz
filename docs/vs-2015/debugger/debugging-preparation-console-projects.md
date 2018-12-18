---
title: 'Příprava ladění: Projekty konzoly | Dokumentace Microsoftu'
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
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78cdf137f4804b2cdad26a21daf2dc34592ed774
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722925"
---
# <a name="debugging-preparation-console-projects"></a>Příprava ladění: projekty konzoly
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Příprava na ladění projektu konzoly je podobný připravuje se ladit projekt Windows, se několik dalších důležitých informací. Další informace najdete v tématu [formulářových aplikací Windows](../debugger/debugging-preparation-windows-forms-applications.md), a [Příprava ladění: Windows Forms aplikace (.NET)](http://msdn.microsoft.com/en-us/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5). Z důvodu podobnosti všechny konzolové aplikace Toto téma popisuje následující typy projektů:  
  
- Konzolovou aplikaci C#  
  
- Konzolová aplikace jazyka Visual Basic  
  
- C++ Konzolová aplikace (.NET)  
  
- Aplikace konzoly C++ (Win32)  
  
  Budete muset zadat argumenty příkazového řádku pro konzolové aplikace. Další informace najdete v tématu [nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [nastavení projektu pro konfiguraci ladění jazyka Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), nebo [nastavení projektu pro ladění konfigurace jazyka C# ](../debugger/project-settings-for-csharp-debug-configurations.md).  
  
  Stejně jako všechny vlastnosti projektu, tyto argumenty zachovat mezi relacemi ladění a mezi relacemi aplikace Visual Studio. Proto pokud konzolové aplikace je ten, který jste dříve ladit, mějte na paměti, že může být argumenty ze zadaného v předchozích relacích  **\<Projekt > stránky vlastností** dialogové okno.  
  
  Využívá konzolovou aplikaci **konzoly** okna tak, aby přijímal vstupní a výstupní zprávy zobrazíte. Zapsat do **konzoly** okno, musí vaše aplikace používat **konzoly** objektu namísto objektu Debug. Zapsat do **výstup Visual Studia** okně pomocí objektu Debug jako obvykle. Ujistěte se, že víte, kde vaše aplikace zapisuje nebo jste možná hledáte zprávy ve špatné místo. Další informace najdete v tématu [konzoly třídy](https://msdn.microsoft.com/library/system.console.aspx), [ladit třídy](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx), a [okno výstup](../ide/reference/output-window.md).  
  
## <a name="starting-the-application"></a>Spuštění aplikace  
 Když se některé aplikace konzoly, doběhla do konce a poté ukončete. Toto chování nemusí poskytnout dostatek času spuštění a ladění. Aby bylo možné ladit aplikaci, použijte jednu z následujících postupů spusťte aplikaci:  
  
- Aplikace se spustí provádění a spuštění untils dosáhne zarážky.  
  
- Vaše aplikace se spustí a okamžitě přestane fungovat na prvním řádku zdrojového kódu.  
  
- V okně zdrojového kódu, klikněte pravým tlačítkem na řádku a vyberte **spustit ke kurzoru**.  
  
   Vaše aplikace spustí a spustí vybraného řádku, nebo k zarážce, v případě, že zarážka se projeví před řádkem.  
  
  Když ladíte konzolovou aplikaci, můžete aplikaci spustit z příkazového řádku, spíše než ze sady Visual Studio. V takovém případě můžete spustit aplikaci z příkazového řádku a k němu připojit ladicí program sady Visual Studio. Další informace najdete v tématu [připojení k běžící procesy](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
  Při spuštění aplikace konzoly z aplikace Visual Studio **konzoly** někdy okno za okno sady Visual Studio. Pokud se pokusíte spustit konzolovou aplikaci v sadě Visual Studio, ale nic zdá se, že se stát, zkuste přesunout okno sady Visual Studio.  
  
## <a name="see-also"></a>Viz také  
 [Ladění nativního kódu](../debugger/debugging-native-code.md)   
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)   
 [Typy projektů Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#, F#a typy projektů jazyka Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)



