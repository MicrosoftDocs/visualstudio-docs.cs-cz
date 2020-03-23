---
title: Ladění pomocí Visual Studia pro Mac
description: Ladění je běžnou a nezbytnou součástí programování. Jako starší IDE, Visual Studio pro Mac obsahuje celou sadu funkcí, které usnadňují ladění. Od bezpečnéladění, na vizualizaci dat, tento článek vysvětluje, jak využít plný potenciál ladění v Sadě Visual Studio pro Mac.
author: therealjohn
ms.author: johmil
ms.date: 12/13/2019
ms.technology: vs-ide-debug
ms.assetid: BB7A084D-9AC2-48B5-8076-6C8518796BBA
ms.openlocfilehash: 8a12880c25e980d668351ef4c24ced1e479577d4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75397949"
---
# <a name="debugging-with-visual-studio-for-mac"></a>Ladění pomocí Visual Studia pro Mac

Visual Studio pro Mac má ladicí program s podporou aplikací .Net Core, .NET Framework, Unity a Xamarin.

Visual Studio pro Mac používá [*Mono Soft Debugger*](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger/), který je implementován do mono runtime, což umožňuje Visual Studio pro Mac ladit spravovaný kód na všech platformách.

## <a name="the-debugger"></a>Ladicí program

Visual Studio pro Mac používá Mono Soft Debugger k ladění spravovaného (C# nebo F#) kódu ve všech aplikacích Xamarin. Ladicí program Mono Soft se liší od běžných ladicích programů v tom, že se jedná o kooperativní ladicí program, který je integrován do intervalu runtime Mono; generovaný kód a mono runtime spolupracují s ide poskytnout ladění prostředí. Mono runtime zveřejňuje funkce ladění prostřednictvím drátového protokolu, který si můžete přečíst více [v dokumentaci Mono](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger-wire-format/).

Tvrdé ladicí programy, jako je [LLDB]( http://lldb.llvm.org/index.html) nebo [GDB]( https://www.gnu.org/software/gdb/), řídí program bez vědomí nebo spolupráce z laděné ho programu, ale může být stále užitečné při ladění aplikací Xamarin v případě, že potřebujete ladit nativní kód iOS nebo Android.

Pro aplikace .NET Core a ASP.NET Core visual studio pro Mac používá ladicí program .NET Core. Tento ladicí program je také družstevní ladicí program a pracuje s rozhraním .NET runtime.

## <a name="using-the-debugger"></a>Použití ladicího programu

Chcete-li spustit ladění libovolné aplikace, vždy se ujistěte, že konfigurace je nastavena na **ladění**. Konfigurace ladění poskytuje užitečnou sadu nástrojů pro podporu ladění, jako jsou zarážky, pomocí vizualizérů dat a zobrazení zásobníku volání:

![Konfigurace ladění](media/debugging-image_0.png)

## <a name="setting-a-breakpoint"></a>Nastavení zarážky

Chcete-li nastavit zarážku v rozhraní IDE, klikněte na oblast okrajů editoru vedle čísla řádku kódu, kde chcete přerušit:

![Nastavení zarážky v okraji](media/debugging-image0.png)

Všechny zarážky, které byly nastaveny v kódu, můžete zobrazit tak, že přejdete na **panel Zarážky**:

![Seznam zarážek](media/debugging-image0a.png)

## <a name="start-debugging"></a>Zahájit ladění

Chcete-li zahájit ladění, vyberte cílový prohlížeč, zařízení nebo simulátor/emulátor:

![Ladění konfigurace](media/debugging-image_0.png)
![Vybrat cílové zařízení](media/debugging-image1.png)

Pak nasadit aplikaci stisknutím tlačítka **Play,** nebo **Cmd + return**. Když narazíte na zarážku, kód se zvýrazní žlutě:

![Zvýraznění zobrazující zarážku bylo dosaženo](media/debugging-image2.png)

Ladicí nástroje, jako je například ten, který slouží ke kontrole hodnot objektů, lze v tomto okamžiku použít k získání dalších informací o tom, co se děje ve vašem kódu:

![Ladění vizualizací](media/debugging-image3.png)

## <a name="conditional-breakpoints"></a>Podmíněné zarážky

Můžete také nastavit pravidla diktovat okolnosti, za kterých by mělo dojít k zarážky, to se označuje jako přidání *podmíněné zarážky*. Chcete-li nastavit podmíněnou zarážku, přejděte do **okna Vlastnosti zarážky**, které lze provést dvěma způsoby:

* Chcete-li přidat novou podmíněnou zarážku, klikněte pravým tlačítkem myši na okraj editoru, vlevo od čísla řádku kódu, na který chcete nastavit zarážku, a vyberte Nový zarážka:

 ![Kontextová nabídka zarážky](media/debugging-image4.png)

* Chcete-li přidat podmínku k existující zarážky, klepněte pravým tlačítkem myši na zarážku a vyberte **vlastnosti zarážky**nebo v **panelu zarážek**vyberte tlačítko Upravit zarážky znázorněné níže:

 ![Úprava existující zarážky v panelu zarážek](media/debugging-image5.png)

Potom můžete zadat podmínku, pod kterou chcete, aby došlo k zarážky:

 ![Upravit podmínky zarážky](media/debugging-image6.png)

## <a name="stepping-through-code"></a>Krokování kódu

Po dosažení zarážky, ladicí nástroje umožňují získat kontrolu nad provádění programu. Visual Studio for Mac zobrazí čtyři tlačítka, což vám umožní spustit a krokovat kód. Ve Visual Studiu pro Mac budou vypadat takto:

 ![Tlačítka pro krokovací kód](media/debugging-image7.png)

Zde jsou čtyři tlačítka:

* **Přehrát** – začne se spouštět kód až do další zarážky.
* **Krok přes** - To provede další řádek kódu. Pokud další řádek je volání funkce, Krok přes spustí funkci a zastaví se na dalším řádku kódu *za* funkcí.
* **Krok do** - To také spustí další řádek kódu. Pokud je dalším řádkem volání funkce, Krok Do se zastaví na prvním řádku funkce, což vám umožní pokračovat v ladění funkce řádek po řádku. Pokud další řádek není funkce, bude se chovat stejně jako Krok přes.
* **Krok ven** - To se vrátí na řádek, kde byla volána aktuální funkce.

## <a name="debugging-monos-class-libraries"></a>Ladění knihoven tříd Mono

Produkty Xamarin jsou dodávány se zdrojovým kódem pro knihovny tříd Mono a můžete použít tento krok z ladicího programu ke kontrole, jak věci fungují pod kapotou.

Vzhledem k tomu, že tato funkce spotřebovává více paměti během ladění, je ve výchozím nastavení vypnuta.

Chcete-li tuto funkci povolit, přejděte do **předvoleb > ladicí program** sady Visual Studio for Mac > a ujistěte se, že je **vybrána**možnost **"Přejít do externího kódu**" , jak je znázorněno níže:

![Krokovat do externího kódu, možnost](media/debugging-image8.png)

## <a name="see-also"></a>Viz také

- [Ladění v sadě Visual Studio (v systému Windows)](/visualstudio/debugger/)
