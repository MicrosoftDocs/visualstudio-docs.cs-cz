---
title: Příprava na ladění projektů konzoly | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e92e27b123102cb45069c47ebf9de3971039801d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738137"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>Příprava ladění: projekty konzoly (C#, C++, Visual Basic, F#)

Příprava na ladění projektu konzoly je podobná přípravě ladění projektu Windows, s některými dalšími hledisky, jako je například nastavení argumentů příkazového řádku a Postup pozastavení aplikace pro ladění. Další informace najdete v tématech [model Windows Forms aplikace](../debugger/debugging-preparation-windows-forms-applications.md)a [příprava ladění: model Windows Forms aplikace (.NET)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/sez9z95a(v=vs.100)). Z důvodu podobnosti všech konzolových aplikací toto téma popisuje následující typy projektů:

- C#, Visual Basic a F# konzolové aplikace

- C++Konzolová aplikace (.NET)

- C++Konzolová aplikace (Win32)

  Konzolová aplikace používá okno **konzoly** k přijetí vstupu a zobrazení výstupních zpráv. Chcete-li zapisovat do okna **konzoly** , aplikace musí místo objektu Debug použít objekt **konzoly** . Chcete-li zapisovat do okna **výstup aplikace Visual Studio** , použijte objekt ladění, jako obvykle. Ujistěte se, že víte, kam vaše aplikace píšete, nebo že chcete zprávy vyhledat na nesprávném místě. Další informace naleznete v tématu [Třída konzoly](/dotnet/api/system.console), [třída ladění](/dotnet/api/system.diagnostics.debug)a [okno výstup](../ide/reference/output-window.md).

## <a name="set-command-line-arguments"></a>Nastavit argumenty příkazového řádku

Možná budete muset zadat argumenty příkazového řádku pro konzolovou aplikaci. Další informace naleznete v tématu [nastavení projektu pro konfiguraci C++ ladění](../debugger/project-settings-for-a-cpp-debug-configuration.md), [nastavení projektu pro Visual Basic konfiguraci ladění](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)nebo [nastavení projektu pro C# konfiguraci ladění](../debugger/project-settings-for-csharp-debug-configurations.md).

Stejně jako všechny vlastnosti projektu jsou tyto argumenty trvalé mezi relacemi ladění a mezi relacemi sady Visual Studio. Proto pokud je Konzolová aplikace ta, kterou jste dříve laděni, pamatujte na to, že v dialogovém okně **\<Project > stránky vlastností** se můžou zadat argumenty z předchozích relací.

## <a name="start-the-application"></a>Spuštění aplikace

 Po spuštění některých konzolových aplikací se jejich spuštění dokončí a pak se ukončí. K tomuto chování nemusí dodávat dostatek času k přerušení provádění a ladění. Aby bylo možné ladit aplikaci, použijte jeden z následujících postupů pro spuštění aplikace:

- Nastavte zarážku v kódu a spusťte aplikaci.

- Spusťte aplikaci pomocí nástroje **F10** (**ladění** > **Krok přes**) nebo **F11** (**ladění** > **kroku do**) a pak procházením kódu pomocí dalších možností, jako je například **Run, klikněte na tlačítko spustit**.

- V editoru kódu klikněte pravým tlačítkem myši na řádek a vyberte možnost **Spustit ke kurzoru**.

  Při ladění konzolové aplikace je vhodné spustit aplikaci z příkazového řádku, nikoli ze sady Visual Studio. V takovém případě můžete aplikaci spustit z příkazového řádku a připojit k ní ladicí program sady Visual Studio. Další informace najdete v tématu [připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

  Při spuštění konzolové aplikace ze sady Visual Studio se okno **konzoly** někdy zobrazuje v okně sady Visual Studio. Pokud se pokusíte spustit konzolovou aplikaci ze sady Visual Studio a nic se nestane, zkuste přesunout okno aplikace Visual Studio.

## <a name="see-also"></a>Viz také:
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
- [Příprava na ladění C++ projektů](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Typy projektů jazyka C#, F# a Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)