---
title: Ladění pomocí Visual Studio pro Mac
description: Ladění je běžné a nezbytné, což je součást programování. V rámci vyspělého integrovaného vývojového prostředí Visual Studio pro Mac obsahuje celou sadu funkcí, aby bylo ladění snadné. Z bezpečného ladění na vizualizaci dat v tomto článku se dozvíte, jak používat plný potenciál ladění v Visual Studio pro Mac.
author: therealjohn
ms.author: johmil
ms.date: 5/13/2020
ms.technology: vs-ide-debug
ms.assetid: BB7A084D-9AC2-48B5-8076-6C8518796BBA
ms.topic: overview
ms.openlocfilehash: 04fae5874a4fefcb51bdef8b00c8cb3b7171057e
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493254"
---
# <a name="debugging-with-visual-studio-for-mac"></a>Ladění pomocí Visual Studio pro Mac

Visual Studio pro Mac obsahuje ladicí programy s podporou pro aplikace .NET Core, .NET Framework, Unity a Xamarin.

Visual Studio pro Mac používá [*měkký ladicí program mono*](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger/), který je implementován do mono runtime a umožňuje Visual Studio pro Mac ladit spravovaný kód napříč všemi platformami.

## <a name="the-debugger"></a>Ladicí program

Pro ladění spravovaného kódu (C# nebo F #) ve všech aplikacích Xamarin používá Visual Studio pro Mac použití měkkého ladicího programu mono. Měkké ladění mono se liší od běžných ladicích programů v tom, že se jedná o ladicí program pro spolupráci, který je integrován do Mono runtime; generovaný kód a Mono runtime spolupracovat s IDE pro poskytování prostředí ladění. Mono runtime zpřístupňuje funkce ladění prostřednictvím přenosového protokolu, který si můžete přečíst [v dokumentaci k mono](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger-wire-format/).

Pevné ladicí programy, jako je například [LLDB]( http://lldb.llvm.org/index.html) nebo [GDB]( https://www.gnu.org/software/gdb/), řídí program bez znalosti nebo spolupráce z laděného programu, ale mohou být užitečné při ladění aplikací Xamarin v případě, že potřebujete ladit nativní kód pro iOS nebo Android.

Pro aplikace .NET Core a ASP.NET Core Visual Studio pro Mac používá ladicí program .NET Core. Tento ladicí program je také ladicí program pro spolupráci a spolupracuje s modulem runtime .NET.

## <a name="using-the-debugger"></a>Použití ladicího programu

Chcete-li spustit ladění jakékoli aplikace, vždy zajistěte, aby byla konfigurace nastavena na  **ladění**. Konfigurace ladění poskytuje užitečnou sadu nástrojů pro podporu ladění, jako je například zarážky, použití vizualizací dat a zobrazení zásobníku volání:

![Konfigurace ladění](media/debugging-image_0.png)

## <a name="setting-a-breakpoint"></a>Nastavení zarážky

Chcete-li nastavit zarážku v integrovaném vývojovém prostředí (IDE), klikněte vedle čísla řádku kódu, který chcete přerušit, na oblast okraje editoru.

![Nastavení zarážky v okraji](media/debugging-image0.png)

Kliknutím na  **okno zarážky** můžete zobrazit všechny zarážky, které byly nastaveny v kódu.

![Seznam zarážek](media/debugging-image0a.png)

## <a name="start-debugging"></a>Spustit ladění

Chcete-li spustit ladění, vyberte cílový prohlížeč, zařízení nebo simulátor/emulátor:

![Konfigurace ladění – ](media/debugging-image_0.png)
 ![ Výběr cílového zařízení](media/debugging-image1.png)

Pak aplikaci nasaďte stisknutím tlačítka  **Přehrát** nebo  **příkazu cmd + Return**. Když narazíte na zarážku, kód se zvýrazní žlutě:

![Zvýraznění ukazující, že bylo dosaženo zarážky](media/debugging-image2.png)

Nástroje pro ladění, jako je například ta, která se používá ke kontrole hodnot objektů, lze v tomto okamžiku použít k získání dalších informací o tom, co se děje v kódu:

![Ladění vizualizací](media/debugging-image3.png)

## <a name="conditional-breakpoints"></a>Podmíněné zarážky

Můžete také nastavit pravidla, která určují okolnosti, za kterých by měla být zarážka, což se říká přidání *podmíněné zarážky*. Chcete-li nastavit podmíněnou zarážku, přejděte k  **okno vlastnosti zarážky** , kterou lze provést dvěma způsoby:

* Chcete-li přidat novou podmíněnou zarážku, klikněte pravým tlačítkem myši na okraj editoru, nalevo od čísla řádku pro kód, na kterém chcete nastavit zarážku, a vyberte Nová zarážka:

 ![Místní nabídka zarážky](media/debugging-image4.png)

* Chcete-li přidat podmínku do existující zarážky, klikněte pravým tlačítkem myši na zarážku a vyberte možnost  **vlastnosti zarážky** , nebo v  **okně zarážky** vyberte tlačítko Upravit zarážku, které je zobrazeno níže:

 ![Upravit existující zarážku v okně zarážek](media/debugging-image5.png)

Pak můžete zadat podmínku, pod kterou chcete, aby se zarážka nastala:

 ![Upravit podmínky zarážky](media/debugging-image6.png)

## <a name="stepping-through-code"></a>Krokování prostřednictvím kódu

Při dosažení zarážky vám ladicí nástroje umožní získat kontrolu nad prováděním programu. Visual Studio pro Mac zobrazí čtyři tlačítka, která vám umožní spustit a krokovat kód. V Visual Studio pro Mac budou vypadat takto:

 ![Tlačítka pro krokování kódu](media/debugging-image7.png)

Tady jsou čtyři tlačítka:

* **Přehrát** – spustí se kód až do další zarážky.
* **Krok za krokem** – provede další řádek kódu. Pokud je další řádek volání funkce, krok za krokem spustí funkci a zastaví se na dalším řádku kódu *za* funkcí.
* **Krokovat** s vnořením se také spustí další řádek kódu. Pokud je další řádek volání funkce, krok dovnitř se zastaví na prvním řádku funkce, což vám umožní pokračovat v řádkovém ladění funkce. Pokud další řádek není funkce, bude se chovat stejně jako krok za krokem.
* **Krok ven** – vrátí se na řádek, kde byla zavolána aktuální funkce.

## <a name="change-which-statement-is-executed-next"></a>Změna příkazu, který je proveden jako další

Když ladicí program pozastavíte, šipka na okraji ukazuje, který řádek kódu se spustí jako další. Pokud chcete spouštěný příkaz změnit, přetáhněte šipku na jiný řádek. Stejnou věc můžete dosáhnout také tak, že kliknete pravým tlačítkem na řádek kódu a vyberete **nastavit další příkaz** z kontextové nabídky.

![Šipkou a přetažením nastavíte další příkaz.](media/debugger-drag-setnextstatement.gif)

> [!CAUTION]
> Změna aktuálního řádku provádění může způsobit neočekávané chování v aplikaci. Existují také některé podmínky, kdy změna dalšího příkazu ke spuštění není možná. Například přetažení šipky z jedné metody na jinou metodu nebude fungovat. V těchto nepodporovaných případech Visual Studio pro Mac zobrazí dialogové okno, ve kterém zjistíte, že není možné změnit aktuální řádek provádění. 

## <a name="debugging-monos-class-libraries"></a>Ladění knihoven tříd mono

Produkty Xamarin dodávané se zdrojovým kódem pro knihovny tříd mono a můžete je použít pro jeden krok ladicího programu ke kontrole, jak fungují v digestoři.

Vzhledem k tomu, že tato funkce spotřebovává větší množství paměti během ladění, je ve výchozím nastavení vypnutá.

Pokud chcete tuto funkci povolit, přejděte na **Visual Studio pro Mac > předvolby > ladicí program** a ujistěte se, že je **Vybraná** možnost " **Krok do externího kódu** ", jak je znázorněno níže:

![Krokovat s vnořením do externího kódu – možnost](media/debugging-image8.png)

## <a name="see-also"></a>Viz také

- [Ladění v aplikaci Visual Studio (ve Windows)](/visualstudio/debugger/)
