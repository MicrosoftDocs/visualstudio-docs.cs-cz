---
title: Ladění v době návrhu | Microsoft Docs
description: Používejte okamžité okno k ladění kódu v době návrhu bez spuštění aplikace. Můžete spustit funkci a prozkoumávat stav, když je dosaženo zarážky.
ms.custom: SEO-VS-2020
ms.date: 01/10/2019
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f127c630cec0e0b64ab5602e81f2b314a3896b16
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148844"
---
# <a name="debug-at-design-time-in-visual-studio-c-ccli-visual-basic-f"></a>Ladění v době návrhu v aplikaci Visual Studio (C#, C++/CLI, Visual Basic, F #)

Chcete-li ladit kód v době návrhu namísto spuštění aplikace, můžete použít okno **Immediate** .

Chcete-li ladit kód XAML za aplikací z návrháře XAML, například pomocí deklarativních scénářů vázání dat, můžete použít **ladění**  >  **připojit k procesu**.

## <a name="use-the-immediate-window"></a>Použít příkazové okno

K provedení funkce nebo podprogramu bez spuštění aplikace můžete použít okno Visual Studio **Immediate** . Pokud funkce nebo podprogram obsahuje zarážku, bude Visual Studio na zarážce přerušeno. Pak můžete použít okna ladicího programu k prohlédnutí stavu programu. Tato funkce se nazývá *ladění v době návrhu*.

Následující příklad je Visual Basic. Můžete také použít **okamžité** okno v době návrhu v aplikacích C#, F # a C++/CLI.

1. Vložte následující kód do prázdné Visual Basic konzolové aplikace:

   ```vb
   Module Module1

       Sub Main()
           MySub()
       End Sub

       Function MyFunction() As Decimal
           Static i As Integer
           i = i + 1
           Return i
       End Function

       Sub MySub()
           MyFunction()

       End Sub
   End Module
   ```

1. Nastavte zarážku na **funkci end** řádku.

1. Otevřete okno **okamžité** , a to tak, že vyberete možnost **ladit**  >  **Windows** hned  >  . `?MyFunction`Do okna zadejte a stiskněte klávesu **ENTER**.

   Zarážka je dosaženo a hodnota **MyFunction** v okně **místních** hodnot je **1**. Můžete kontrolovat zásobník volání a další ladicí okna, zatímco je aplikace v režimu přerušení.

1. Na panelu nástrojů sady Visual Studio vyberte **pokračovat** . Aplikace skončí a v **příkazovém** okně se vrátí **1** . Ujistěte se, že jste stále v režimu návrhu.

1. Zadejte `?MyFunction` znovu **příkazové** okno a stiskněte klávesu **ENTER**. Zarážka je dosaženo a hodnota **MyFunction** v okně **místních** hodnot je **2**.

1. Bez výběru možnosti **pokračovat** zadejte `?MySub()` do příkazového **podokna** a potom stiskněte klávesu **ENTER**. Zarážka je dosaženo a hodnota **MyFunction** v okně **místní** hodnoty je **3**. Stav aplikace můžete prošetřit, zatímco je aplikace v režimu přerušení.

1. Vyberte **Pokračovat**. Zarážka se znovu opakuje a hodnota **MyFunction** v okně **místní** hodnoty je teď **2**. **Okamžité** okno vrací **výraz byl vyhodnocen a nemá žádnou hodnotu**.

1. Vyberte **pokračovat** znovu. Aplikace skončí a v **příkazovém** okně se vrátí **2** . Ujistěte se, že jste stále v režimu návrhu.

1. Pokud chcete vymazat obsah příkazového **podokna,** klikněte na něj pravým tlačítkem a vyberte **Vymazat vše**.

## <a name="debug-a-custom-xaml-control-at-design-time-by-attaching-to-xaml-designer"></a>Ladění vlastního ovládacího prvku XAML v době návrhu připojením k Návrháři XAML

1. Otevřete své řešení nebo projekt v aplikaci Visual Studio.

1. Sestavte řešení/projekt.

1. Otevřete stránku XAML obsahující vlastní ovládací prvek, který chcete ladit.

   V případě projektů UWP cílících na Windows Build 16299 nebo vyšší bude tento krok zahájit proces *UwpSurface.exe* . V případě projektů WPF cílících na Windows Build 16299 nebo vyšší bude tento krok zahájit proces *WpfSurface.exe* . U verzí WPF a UWP starších než Windows Build 16299 se v tomto kroku spustí proces *XDesProc.exe* . 

1. Otevřete druhou instanci aplikace Visual Studio. Neotevírejte řešení nebo projekt ve druhé instanci.

1. Ve druhé instanci aplikace Visual Studio otevřete nabídku **ladění** a vyberte možnost **připojit k procesu...**.

1. V závislosti na typu projektu (viz předchozí kroky) vyberte *UwpSurface.exe*, *WpfSurface.exe* nebo *XDesProc.exeho* procesu ze seznamu dostupných procesů.

1. V dialogovém okně **připojit k** **procesu** vyberte pro vlastní ovládací prvek, který chcete ladit, správný typ kódu.

   Pokud vlastní ovládací prvek byl napsán v jazyce .NET, vyberte odpovídající typ kódu .NET, například **Managed (CoreCLR)**. Pokud vlastní ovládací prvek byl napsaný v jazyce C++, vyberte možnost **nativní**.

1. Připojte druhou instanci aplikace Visual Studio kliknutím na tlačítko **připojit** .

1. Ve druhé instanci aplikace Visual Studio otevřete soubory kódu přidružené k vlastnímu ovládacímu prvku, který chcete ladit. Nezapomeňte pouze otevřít soubory, ne celé řešení nebo projekt.

1. Požadované zarážky umístěte do dříve otevřených souborů.

1. V první instanci aplikace Visual Studio zavřete stránku XAML obsahující vlastní ovládací prvek, který chcete ladit (stejnou stránku jste otevřeli v předchozích krocích).

1. V první instanci sady Visual Studio otevřete stránku XAML, kterou jste uzavřeli v předchozím kroku. To způsobí, že se ladicí program zastaví na první zarážce, kterou jste nastavili ve druhé instanci aplikace Visual Studio.

1. Ladit kód ve druhé instanci aplikace Visual Studio.

## <a name="see-also"></a>Viz také
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)