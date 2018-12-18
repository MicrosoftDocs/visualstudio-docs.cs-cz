---
title: Ladění s využitím kódu Xamarin
description: Ladění je běžné a potřeby součástí programování. Jako až po zralé integrovaného vývojového prostředí sady Visual Studio for Mac obsahuje celou sadu funkcí pro zajištění snadné ladění. Z bezpečné ladění k vizualizaci dat, tento článek vysvětluje, jak použít celý potenciál ladění v sadě Visual Studio pro Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.technology: vs-ide-debug
ms.assetid: BB7A084D-9AC2-48B5-8076-6C8518796BBA
ms.openlocfilehash: e17a423e9db6826c8cc693e1c75c75bb067a19e8
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295290"
---
# <a name="debugging-with-xamarin"></a>Ladění s využitím kódu Xamarin

Visual Studio for Mac obsahuje nativní ladicí program umožňuje ladění podporu pro aplikace Xamarin.Android, Xamarin.iOS a Xamarin.Mac.

Visual Studio pro Mac používá [ *Obnovitelně ladicí program Mono*](http://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger/), která je implementována do modulu Mono runtime, umožňuje sadě Visual Studio for Mac pro ladění spravovaného kódu na všech platformách.

## <a name="the-debugger"></a>Ladicí program

Visual Studio pro Mac používá ladicí program Mono Obnovitelně ladit spravované (C# nebo F#) kódu ve všech aplikacích Xamarin. Ladicí program Mono Obnovitelně se liší od standardní ladicí programy v tom, že je kooperativního ladicí program, který je součástí modulu Mono runtime; generovaný kód a modul Mono runtime spolupracovat s integrovaným vývojovým prostředím poskytnout možnosti ladění. Modul Mono runtime poskytuje funkce pro ladění přes přenosový protokol, který si můžete přečíst více o [v dokumentace Mono](http://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger-wire-format/).

Pevné ladicích programů, jako například [LLDB]( http://lldb.llvm.org/index.html) nebo [GDB]( https://www.gnu.org/software/gdb/), řízení programu bez vědomí nebo spolupráci od laděného programu, ale může být přesto užitečné při ladění aplikací v Xamarinu v události, které jste třeba ladění nativních aplikací pro iOS nebo Android kódu.

## <a name="using-the-debugger"></a>Pomocí ladicího programu

Spustit ladění všech aplikací, vždycky zkontrolujte, že konfiguraci je nastavená na **ladění**. Konfigurace ladění poskytuje sadu nástrojů pro podporu ladění, jako je například zarážek, vizualizérů dat pomocí a zobrazení zásobníku volání užitečné:

![Konfigurace ladění](media/debugging-image_0.png)

## <a name="setting-a-breakpoint"></a>Nastavením zarážky

Pokud chcete nastavit zarážku v prostředí (IDE), klikněte na oblast okraje editoru, vedle číslo řádku kódu, kde chcete zrušit:

![Nastavení zarážky v rozpětí](media/debugging-image0.png)

Můžete zobrazit všechny zarážky, které jsou nastavené v kódu tak, že přejdete **zarážky panel**:

![Seznam zarážky](media/debugging-image0a.png)

## <a name="start-debugging"></a>Spustit ladění

Spustit ladění, vyberte cílové zařízení nebo podobné/emulátor v prostředí (IDE):

![Vyberte cílové zařízení](media/debugging-image1.png)

Potom nasaďte svoji aplikaci stisknutím klávesy **Přehrát** tlačítko, nebo **Cmd + return**. Při dosažení zarážky kód bude zvýrazněné žlutou barvou:

![Zvýraznění znázorňující zarážky](media/debugging-image2.png)

Ladicí nástroje, jako je například jaký se používá ke kontrole hodnoty objekty, lze v tomto okamžiku získat další informace o tom, co se děje ve vašem kódu:

![Ladění vizualizace](media/debugging-image3.png)

## <a name="conditional-breakpoints"></a>Podmíněné zarážky

Můžete také nastavit pravidla diktování okolnosti, kdy by mělo dojít k zarážce, to se označuje jako přidávání *podmíněné zarážky*. Pokud chcete nastavit podmíněné zarážky, přístup **okna Vlastnosti zarážky**, což lze provést dvěma způsoby:

* Chcete-li přidat nový podmíněné zarážky, klikněte pravým tlačítkem myši na okraj editoru, doleva číslo řádku kódu, který chcete nastavit zarážku na a vyberte Nová zarážka:

 ![Místní nabídka zarážku](media/debugging-image4.png)

* Přidání podmínky do existující zarážce, klikněte pravým tlačítkem na zarážku a vyberte **vlastnosti zarážky**, nebo v **zarážky panel**, klikněte na tlačítko Upravit zarážku znázorněno níže:

 ![Upravit existující zarážce v oblasti zarážky](media/debugging-image5.png)

Zadejte podmínku, u které chcete zarážku na výskyt:

 ![Upravit podmínky zarážky](media/debugging-image6.png)

## <a name="stepping-through-code"></a>Krokování kódem

Když se dosáhne zarážky, nástroje pro ladění umožňují získat kontrolu nad vykonávání programu. Visual Studio pro Mac se zobrazí čtyři tlačítka, díky tomu můžete spustit a krokovat kód. V sadě Visual Studio pro Mac bude vypadat nějak takto:

 ![Tlačítka pro jednotlivé kroky v kódu](media/debugging-image7.png)

Tady jsou čtyři tlačítka:

*   **Přehrát** – zahájí se spouští kód, dokud k další zarážce.
*   **Krokovat s přeskočením** – tím se spustí další řádek kódu. Pokud se na další řádek je volání funkce, Krokovat s přeskočením se spuštění funkce a se zastaví na další řádek kódu *po* funkce.
*   **Krokovat s vnořením** – to také provede další řádek kódu. Pokud na další řádek je volání funkce, Krokovat s vnořením se zastaví na prvním řádku funkci, abyste mohli pokračovat v ladění řádek po řádku funkce. Pokud se na další řádek není funkce, budou chovat stejné jako Krokovat s přeskočením.
*   **Krokovat s Vystoupením** – to se vrátí k řádku, kde byla volána aktuální funkce.

## <a name="debugging-monos-class-libraries"></a>Ladění knihoven tříd pro Mono

Dodávat produkty Xamarin se zdrojovým kódem pro knihovny tříd pro Mono, a to do jednoho kroku z ladicího programu můžete použít ke kontrole, jak věci pracují pod pokličkou.

Protože tato funkce vyžaduje další paměť během ladění, je ve výchozím nastavení vypnuté.

Tuto funkci povolit, přejděte do **Visual Studio for Mac > Předvolby > ladicí program** a ujistěte se, že "**ladit kód projektu. Nekrokovat s vnořením do kódu architektury.** " možnost je **nevybrané**, jak je znázorněno níže:

![Nekrokovat s vnořením do rozhraní framework kód – možnost](media/debugging-image8.png)

## <a name="see-also"></a>Viz také:

- [Ladění v sadě Visual Studio (ve Windows)](/visualstudio/debugger/)