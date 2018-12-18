---
title: Příprava na ladění projektů konzoly | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 55c588bfffbf11d4abd26fbae1490cf0039373c3
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057073"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>Příprava ladění: Projekty konzoly (C#, C++, Visual Basic, F#)

Příprava na ladění projektu konzoly je podobný připravuje se ladit projekt Windows, se několik dalších důležitých informací. Další informace najdete v tématu [formulářových aplikací Windows](../debugger/debugging-preparation-windows-forms-applications.md), a [Příprava ladění: Windows Forms aplikace (.NET)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/sez9z95a(v=vs.100)). Z důvodu podobnosti všechny konzolové aplikace Toto téma popisuje následující typy projektů:  
  
- C#, Visual Basic a F# konzolové aplikace  
  
- C++ Konzolová aplikace (.NET)  
  
- Aplikace konzoly C++ (Win32)  
  
  Budete muset zadat argumenty příkazového řádku pro konzolové aplikace. Další informace najdete v tématu [nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [nastavení projektu pro konfiguraci ladění jazyka Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), nebo [nastavení projektu pro ladění konfigurace jazyka C# ](../debugger/project-settings-for-csharp-debug-configurations.md).  
  
  Stejně jako všechny vlastnosti projektu, tyto argumenty zachovat mezi relacemi ladění a mezi relacemi aplikace Visual Studio. Proto pokud konzolové aplikace je ten, který jste dříve ladit, mějte na paměti, že může být argumenty ze zadaného v předchozích relacích  **\<Projekt > stránky vlastností** dialogové okno.  
  
  Využívá konzolovou aplikaci **konzoly** okna tak, aby přijímal vstupní a výstupní zprávy zobrazíte. Zapsat do **konzoly** okno, musí vaše aplikace používat **konzoly** objektu namísto objektu Debug. Zapsat do **výstup Visual Studia** okně pomocí objektu Debug jako obvykle. Ujistěte se, že víte, kde vaše aplikace zapisuje nebo jste možná hledáte zprávy ve špatné místo. Další informace najdete v tématu [konzoly třídy](/dotnet/api/system.console), [ladit třídy](/dotnet/api/system.diagnostics.debug), a [okno výstup](../ide/reference/output-window.md).  
  
## <a name="starting-the-application"></a>Spuštění aplikace  
 Když se některé aplikace konzoly, doběhla do konce a poté ukončete. Toto chování nemusí poskytnout dostatek času spuštění a ladění. Aby bylo možné ladit aplikaci, použijte jednu z následujících postupů spusťte aplikaci:  
  
- Nastavte zarážku v kódu a spusťte aplikaci.
  
- Spusťte aplikaci pomocí **F10** (**ladění** > **Krokovat s přeskočením**) nebo **F11** (**ladění**  >  **Krokovat s vnořením**) a potom navigace v kódu pomocí dalších možností, jako **běžet do kliknutí**.
  
- V editoru kódu, klikněte pravým tlačítkem na řádku a vyberte **spustit ke kurzoru**.  
  
  Když ladíte konzolovou aplikaci, můžete aplikaci spustit z příkazového řádku, spíše než ze sady Visual Studio. V takovém případě můžete spustit aplikaci z příkazového řádku a k němu připojit ladicí program sady Visual Studio. Další informace najdete v tématu [připojení k běžící procesy](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
  Při spuštění aplikace konzoly z aplikace Visual Studio **konzoly** někdy okno za okno sady Visual Studio. Pokud se pokusíte spustit konzolovou aplikaci v sadě Visual Studio, ale nic zdá se, že se stát, zkuste přesunout okno sady Visual Studio.  
  
## <a name="see-also"></a>Viz také  
 [Ladění nativního kódu](../debugger/debugging-native-code.md)   
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)   
 [Typy projektů Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#, F#a typy projektů jazyka Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)