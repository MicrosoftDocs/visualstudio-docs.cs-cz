---
title: Ladění v době návrhu | Dokumentace Microsoftu
ms.custom: ''
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
ms.openlocfilehash: beb16ae52f880e31bd19a185d47b13c02026752f
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916147"
---
# <a name="debug-at-design-time-in-visual-studio-c-ccli-visual-basic-f"></a>Ladění v době návrhu v aplikaci Visual StudioC#( C++,/CLI, Visual Basic F#)

Postup ladění kódu v době návrhu namísto při aplikace běží, můžete použít **okamžité** okna.

Chcete-li ladit kód XAML za aplikací z návrháře XAML, například pomocí deklarativních scénářů vázání dat, můžete použít **ladění** > **připojit k procesu**.

## <a name="use-the-immediate-window"></a>Použijte příkazové podokno

Můžete použít Visual Studio **okamžité** okna spuštění funkce nebo podprogram bez spuštění vaší aplikace. Pokud funkce nebo podprogram obsahuje zarážku, sada Visual Studio přeruší na zarážce. Potom můžete ladicí program windows prozkoumat stav vaší aplikace. Tato funkce se nazývá *ladění v době návrhu*.

V následujícím příkladu je v jazyce Visual Basic. Můžete také použít **okamžité** okno v době návrhu v C#aplikacích, F#a C++/CLI.

1. Následující kód vložte do prázdné konzolové aplikace jazyka Visual Basic:

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

1. Nastavit zarážku na řádku **End Function**.

1. Otevřít **okamžité** okna tak, že vyberete **ladění** > **Windows** > **okamžité**. Typ `?MyFunction` , a poté stiskněte klávesu **Enter**.

   Zarážka je dosaženo a hodnota **MáFunkce** v **lokální** je okno **1**. Když je aplikace v režimu pozastavení můžete prozkoumat zásobník volání a dalších oknech ladění.

1. Vyberte **pokračovat** na panelu nástrojů sady Visual Studio. Ukončení aplikace a **1** se vrátí v **okamžité** okna. Ujistěte se, že jste stále v režimu návrhu.

1. Typ `?MyFunction` v **okamžité** znovu okno a stiskněte klávesu **Enter**. Zarážka je dosaženo a hodnota **MáFunkce** v **lokální** je okno **2**.

1. Nevybírejte **pokračovat**, typ `?MySub()` v **okamžité** okno a poté stiskněte klávesu **Enter**. Zarážka je dosaženo a hodnota **MáFunkce** v **lokální** je okno **3**. Když je aplikace v režimu pozastavení můžete zkoumat stav aplikace.

1. Vyberte **pokračovat**. Zarážka je dosaženo znovu a hodnota **MáFunkce** v **lokální** je okno **2**. **Okamžité** vrátí okno **výraz byl vyhodnocen a nemá žádnou hodnotu**.

1. Vyberte **pokračovat** znovu. Ukončení aplikace a **2** se vrátí v **okamžité** okna. Ujistěte se, že jste stále v režimu návrhu.

1. Vymazat obsah **okamžité** okna, klikněte pravým tlačítkem a vyberte **Vymazat vše**.

## <a name="debug-a-custom-xaml-control-at-design-time-by-attaching-to-xaml-designer"></a>Ladění vlastního ovládacího prvku XAML v době návrhu připojením k Návrháři XAML

1. Otevřete své řešení nebo projekt v aplikaci Visual Studio.

1. Sestavte řešení/projekt.

1. Otevřete stránku XAML obsahující vlastní ovládací prvek, který chcete ladit.

   V případě projektů UWP cílících na Windows Build 16299 nebo vyšší se v tomto kroku spustí proces *UwpSurface. exe* . U verzí WPF a UWP starších než Windows Build 16299 se v tomto kroku spustí proces *XDesProc. exe* .

1. Otevřete druhou instanci aplikace Visual Studio. Neotevírejte řešení nebo projekt ve druhé instanci.

1. Ve druhé instanci aplikace Visual Studio otevřete nabídku **ladění** a vyberte možnost **připojit k procesu...** .

1. V závislosti na typu projektu (viz předchozí kroky) vyberte v seznamu dostupných procesů buď proces *UwpSurface. exe* , nebo *XDesProc. exe* .

1. V dialogovém okně **připojit k** **procesu** vyberte pro vlastní ovládací prvek, který chcete ladit, správný typ kódu.

   Pokud vlastní ovládací prvek byl napsán v jazyce .NET, vyberte odpovídající typ kódu .NET, například **Managed (CoreCLR)** . Pokud vlastní ovládací prvek byl napsán v C++, vyberte možnost **nativní**.

1. Připojte druhou instanci aplikace Visual Studio kliknutím na tlačítko **připojit** .

1. Ve druhé instanci aplikace Visual Studio otevřete soubory kódu přidružené k vlastnímu ovládacímu prvku, který chcete ladit. Nezapomeňte pouze otevřít soubory, ne celé řešení nebo projekt.

1. Požadované zarážky umístěte do dříve otevřených souborů.

1. V první instanci aplikace Visual Studio zavřete stránku XAML obsahující vlastní ovládací prvek, který chcete ladit (stejnou stránku jste otevřeli v předchozích krocích).

1. V první instanci sady Visual Studio otevřete stránku XAML, kterou jste uzavřeli v předchozím kroku. To způsobí, že se ladicí program zastaví na první zarážce, kterou jste nastavili ve druhé instanci aplikace Visual Studio.

1. Ladit kód ve druhé instanci aplikace Visual Studio.

## <a name="see-also"></a>Viz také:
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)