---
title: Začínáme s laděním v sadě VS 2017
description: Začínáme s laděním aplikace pomocí ladicího programu sady Visual Studio
ms.custom: mvc
ms.date: 06/15/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d5c479251b7002e506f1dff5e64a028875aa8f80
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882663"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>První pohled na ladicí program sady Visual Studio

Toto téma představuje nástrojům pro ladicí program poskytovaný sadou Visual Studio. V rámci sady Visual Studio při vám *ladění aplikace*, obvykle to znamená, že spustíte aplikaci s připojeným ladícím nástrojem (to znamená, v režimu ladění). Když toto provedete, ladicí program poskytuje mnoho způsobů, jak zjistit, co kód dělá, při spuštění. Můžete krokovat kód a podívejte se na hodnoty uložené v proměnné, Watch můžete nastavit na proměnné, které se zobrazí při změně hodnot, můžete prozkoumat postupu provádění kódu, a další. Pokud je to poprvé, kterou jste se pokusili ladění kódu, můžete chtít číst [ladění pro naprosté začátečníky](../debugger/debugging-absolute-beginners.md) před provedením tohoto tématu.

Funkce popsané tady platí pro C#, C++, Visual Basic, JavaScript a jinými jazyky podporovanými sady Visual Studio (Pokud není uvedeno jinak).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Nastavte zarážku a spuštění ladicího programu

Chcete-li ladit, musíte aplikaci spustit v ladicím programu připojit k procesu aplikace. **F5** (**ladit > Spustit ladění**) je nejběžnější způsob, jak to udělat. Však pravé teď nemusí mít nastavte všechny zarážky prozkoumat vaše aplikace kódu, takže budeme učiňte tak nyní a spusťte ladění. Zarážky jsou základní a nejjednodušší funkcí spolehlivého ladění. Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští. 

Pokud máte soubor otevřený v editoru kódu, můžete nastavit zarážku kliknutím na okraji vlevo od řádku kódu.

![Nastavit zarážku](../debugger/media/dbg-tour-set-a-breakpoint.gif "nastavte zarážku")

Stisknutím klávesy **F5** (**ladit > Spustit ladění**) nebo **spustit ladění** tlačítko ![spustit ladění](../debugger/media/dbg-tour-start-debugging.png "spustit ladění ") v panelu nástrojů ladění a spuštění ladicího programu k první zarážce, kterou zjistí. Pokud ještě není aplikace spuštěna, F5 spustí ladicí program a k první zarážce se zastaví.

Zarážky jsou užitečná funkce, když znáte řádek kódu nebo části kódu, který chcete prozkoumat podrobněji.

## <a name="navigate"></a> Vyhledání kódu v ladicím programu pomocí příkazů kroku

Poskytujeme klávesové zkratky pro většinu příkazů, protože využívají navigace v kódu vaší aplikace rychleji. (Ekvivalentní příkazy, například příkazy nabídek, které jsou uvedeny v závorkách.)

Chcete-li aplikaci spustit s připojeným ladícím nástrojem, stiskněte **F11** (**ladit > Krokovat s vnořením**). Je F11 **Krokovat s vnořením** příkazu a posune jeden příkaz spuštění aplikace v čase. Při spuštění aplikace s F11 ladicí program přeruší na první příkaz, která se provede.

![F11 Krokovat s vnořením](../debugger/media/dbg-tour-f11.png "F11 Krokovat s vnořením")

Žlutá šipka označuje příkaz na které ladicí program pozastaví, což také pozastaví provádění aplikace na stejném místě (Tento příkaz nebyl dosud proveden).

F11 je dobrým způsobem, jak prozkoumat provádění toku v nejvíce podrobností. (Rychlejší procházení kódu, ukážeme některé další možnosti stejně.) Ve výchozím nastavení, ladicí program přeskočí neuživatelském kódu (Pokud potřebujete další podrobnosti, [pouze můj kód](../debugger/just-my-code.md)).

>[!NOTE]
> Ve spravovaném kódu zobrazí se dialogové okno s dotazem, jestli chcete být upozorněni na automaticky Krokovat přes vlastnosti a operátory (výchozí chování). Pokud chcete změnit nastavení později, zakažte **Krokovat přes vlastnosti a operátory** nastavení **nástroje > Možnosti** nabídky v části **ladění**.

## <a name="step-over-code-to-skip-functions"></a>Krokovat přes kódu přeskočit funkce

Pokud jste na řádek kódu, který je volání funkce nebo metoda, můžete stisknout **F10** (**ladit > Krokovat s přeskočením**) namísto F11.

F10 přejde ladicí program bez krokování do funkce nebo metody v kódu vaší aplikace (kód stále provádí). Stisknutím kombinace kláves F10, můžete přeskočit kód, který vás zajímá není. Díky tomu můžete rychle získat kód, který vás zajímá více.

## <a name="step-into-a-property"></a>Krokovat s vnořením vlastností

Jak už bylo zmíněno dříve, ve výchozím nastavení ladicího programu přeskočí spravované vlastnosti a pole, ale **Vkročit do určitého** příkaz umožňuje toto chování přepsat.

Klikněte pravým tlačítkem na vlastnost nebo pole a tlačítko **Vkročit do určitého**, pak vyberte jednu z dostupných možností.

![Krok do určeného](../debugger/media/dbg-tour-step-into-specific.png "Krok dovnitř")

V tomto příkladu **Vkročit do určitého** získá nám kód `Path.set`.

![Krok do určeného](../debugger/media/dbg-tour-step-into-specific-2.png "Krok dovnitř")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Spustit na místo v kódu rychle pomocí myši

V ladicím programu, najeďte myší na řádek kódu až **běžet do kliknutí** (běžet do tohoto místa) tlačítko ![běžet do kliknutí](../debugger/media/dbg-tour-run-to-click.png "RunToClick") se zobrazí na levé straně.

![Běžet do kliknutí](../debugger/media/dbg-tour-run-to-click-2.png "běžet do kliknutí")

> [!NOTE]
> **Běžet do kliknutí** tlačítko (běžet do tohoto místa) je novinkou [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Klikněte na tlačítko **běžet do kliknutí** tlačítko (běžet do tohoto místa). Ladicí program přejde na řádek kódu, které jste klepnuli na.

Pomocí tohoto tlačítka je podobné nastavení dočasné zarážky. Tento příkaz je také užitečné pro rychlé navigace v rámci viditelné oblasti kódu aplikace. Můžete použít **běžet do kliknutí** v všechny otevřené soubory.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Přejděte ladicí program aktuální funkci

V některých případech můžete chtít pokračovat v relaci ladění, ale předem ladicí program rozúčtují aktuální funkce.

Stisknutím klávesy **Shift + F11** (nebo **ladit > Krokovat s Vystoupením**).

Tento příkaz pokračuje v provádění aplikace (a přejde ladicí program) až do aktuálního funkce vrátí.

## <a name="run-to-cursor"></a>Spustit ke kurzoru

Ladicí program ukončit stisknutím kombinace kláves **Zastavit ladění** červené tlačítko ![Zastavit ladění](../debugger/media/dbg-tour-stop-debugging.png "Zastavit ladění") nebo **Shift**  +  **F5**.

Klikněte pravým tlačítkem na řádek kódu ve vaší aplikaci a zvolte **spustit ke kurzoru**. Tento příkaz spustí ladění a nastaví dočasné zarážky na aktuálním řádku kódu.

![Spustit ke kurzoru](../debugger/media/dbg-tour-run-to-cursor.png "spustit ke kurzoru")

Pokud jste nastavili zarážky, ladicí program pozastaví na první zarážce, kterou volání.

Stisknutím klávesy **F5** dokud se nedostanete na řádek kódu, pokud jste vybrali **spustit ke kurzoru**.

Tento příkaz je užitečné, když upravujete kód a chcete rychle nastavení dočasné zarážky a spuštění ladicího programu ve stejnou dobu.

> [!NOTE]
> Můžete použít **spustit ke kurzoru** v **zásobník volání** okno během ladění.

## <a name="restart-your-app-quickly"></a>Rychlé restartování aplikace

Klikněte na tlačítko **restartovat** ![restartovat aplikaci](../debugger/media/dbg-tour-restart.png "restartovat aplikaci") tlačítko na panelu nástrojů ladění (**Ctrl + Shift + F5**).

Když stisknete klávesu **restartovat**, šetří čas a zastavuje se aplikace a restartování ladicího programu. Ladicí program pozastaví na první zarážce, kterou dosáhnete spuštěním kódu.

Pokud chcete zastavit ladicí program a dostat se zpátky do editoru kódu, můžete stisknutím red stop ![Zastavit ladění](../debugger/media/dbg-tour-stop-debugging.png "Zastavit ladění") tlačítko místo **restartovat**.

## <a name="inspect-variables-with-data-tips"></a>Kontrolovat proměnné s datových tipech

Teď, když ovládat trochu znáte, jste o vhodnou příležitost k spuštění kontroly stavu aplikace (proměnné) s ladicím programem. Funkce, které umožňují kontrolovat proměnné jsou některé nejužitečnější funkce ladicího programu, a to různými způsoby. Při pokusu o ladění chyby se často, pokoušíte zjistit, zda jsou proměnné ukládání hodnoty, které očekáváte, že ho, aby ve stavu dané aplikace.

Během pozastavení v ladicím programu, najeďte myší objekt pomocí myši a zobrazit jeho výchozí hodnota vlastnosti (v tomto příkladu, název souboru `market 031.jpg` je výchozí hodnota vlastnosti).

![Zobrazení datového tipu](../debugger/media/dbg-tour-data-tips.gif "zobrazení popisu dat.")

Rozbalte objekt, který chcete zobrazit všechny vlastnosti (například `FullPath` vlastnosti v tomto příkladu).

Často při ladění, chcete rychle zkontrolovat hodnoty vlastností pro objekty a datové tipy jsou dobrým způsobem, jak to udělat.

> [!TIP]
> V nejvíce podporovaných jazyků můžete upravit kód během relace ladění. Další informace najdete v tématu [upravit a pokračovat](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Kontrolovat proměnné s okna Automatické hodnoty a místní hodnoty

Při ladění, podívejte se na **automatické hodnoty** okno v dolní části editoru kódu.

![Okno Automatické hodnoty](../debugger/media/dbg-tour-autos-window.png "okno Automatické hodnoty")

V **automatické hodnoty** okně se zobrazí proměnné spolu s jejich aktuální hodnotu a jejich typu. **Automatické hodnoty** okně se zobrazí všechny proměnné používané v aktuálním řádkem nebo předchozí řádku (v jazyce C++, v okně se zobrazí proměnné v předchozí tři řádky kódu. V dokumentaci pro konkrétní jazyk chování).

> [!NOTE]
> V jazyce JavaScript **lokální** okna je ale není podporován **automatické hodnoty** okna.

Dále, podívejte se na **lokální** okna. **Lokální** v okně se zobrazí proměnné, které se aktuálně nacházejí v oboru.

![Okno místních hodnot](../debugger/media/dbg-tour-locals-window.png "okně místních hodnot")

V tomto příkladu `this` objektem a objektem `f` nacházejí v oboru. Další informace najdete v tématu [kontrolovat proměnné v oknech pro automatické hodnoty a místní hodnoty Windows](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Nastavení sledování

Můžete použít **Watch** okno zadat proměnné (nebo výraz), který chcete sledovat.

Při ladění, klikněte pravým tlačítkem na objekt a zvolte **Přidat kukátko**.

![Okno kukátka](../debugger/media/dbg-tour-watch-window.png "okna kukátka")

V tomto příkladu máte nastavit na sledování `f` objekt kde můžete zobrazit její hodnotu změnit při procházení ladicí program. Na rozdíl od jiných proměnných oknech **Watch** windows vždy zobrazit proměnné, že se díváte (jsou sice zobrazené šedě, když mimo rozsah).

Další informace najdete v tématu [nastavení sledování pomocí kukátko a Rychlé kukátko Windows](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>Prozkoumat zásobník volání

Klikněte na tlačítko **zásobník volání** okno při ladění, což je ve výchozím nastavení, otevřete v pravém dolním podokně.

![Prozkoumat zásobník volání](../debugger/media/dbg-tour-call-stack.png "prozkoumat zásobník volání")

**Zásobník volání** okno zobrazuje pořadí, ve kterém jsou získávání volány metody a funkce. Na horní zobrazený řádek zobrazuje aktuální funkci ( `Update` metoda v tomto příkladu). Druhý řádek ukazuje, že `Update` byla volána `Path.set` vlastnosti a tak dále. Zásobník volání je dobrým způsobem, jak zkoumat a pochopit provádění toku aplikace.

> [!NOTE]
> **Zásobník volání** okno je podobné ladění perspektivy v některých prostředí IDE, jako je Eclipse.

Dvojitým kliknutím na řádek kódu go, podívejte se na tento zdrojový kód a také změny v aktuálním oboru kontrolován ladicím programem. To nepřesouvejte vpřed ladicí program.

Můžete také použít nabídek klikněte pravým tlačítkem **zásobník volání** okno a dělat jiné věci. Například můžete vložit do konkrétní funkce zarážky, restartujte vaši aplikaci s použitím **spustit ke kurzoru**a k přechodu Zkontrolujte zdrojový kód. Zobrazit [jak: prozkoumat zásobník volání](../debugger/how-to-use-the-call-stack-window.md).

## <a name="exception"></a> Prozkoumat výjimky

Pokud vaše aplikace vyvolá výjimku, ladicí program přejde na řádek kódu, který vyvolal výjimku.

![Pomocníka výjimky](../debugger/media/dbg-tour-exception-helper.png "pomocníka výjimky")

V tomto příkladu **pomocníka výjimky** se dozvíte `System.Argument` výjimky a chybová zpráva s upozorněním, že cesta není platný tvar. Proto nám jasné, že došlo k chybě na argumentu metody nebo funkce.

V tomto příkladu `DirectoryInfo` volání přiřadil chyby na prázdný řetězec uložený v `value` proměnné.

Pomocníka výjimky je skvělé funkce, která vám může pomoci ladit chyby. Můžete také provádět akce podobně jako zobrazení Podrobnosti o chybě a přidat kukátko z pomocníka výjimky. Nebo v případě potřeby můžete změnit podmínky pro vyvolání konkrétní výjimky.

> [!NOTE]
> Nahrazuje Pomocníka pro výjimky v Pomocníkovi výjimky [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Rozbalte **nastavení výjimek** uzel pro další možnosti, jak zpracovat výjimky tohoto typu, ale není potřeba nic u této ukázky změnit!

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Ladění živé aplikace ASP.NET ve službě Azure App Service

**Snapshot Debugger** pořídí snímek vaší aplikace do produkčního prostředí, když spustí kód, který vás zajímá. Dáte pokyn, aby ladicí program k vytvoření snímku, můžete nastavit snímkovací a protokolovací body ve vašem kódu. Ladicí program umožňuje zobrazit přesně toho, co nefunguje, aniž by to ovlivnilo provozu aplikace v produkčním prostředí. Snapshot Debugger můžete výrazně zkrátit čas potřebný k vyřešení problémů, ke kterým dochází v produkčním prostředí.

![Spuštění ladicího programu snímků](../debugger/media/snapshot-launch.png "spuštění ladicího programu snímků")

Snímek kolekce je k dispozici pro aplikace ASP.NET běžící ve službě Azure App Service. Aplikace ASP.NET musí běžet na rozhraní .NET Framework 4.6.1 nebo novější, a musí být spuštěná aplikace ASP.NET Core na .NET Core 2.0 nebo novější na Windows.

Další informace najdete v tématu [ladit živé aplikace ASP.NET pomocí ladicího programu snímků](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Zobrazení snímků pomocí zpětného kroku IntelliTrace (Visual Studio Enterprise)

**Zpětného kroku IntelliTrace** automaticky vytvoří snímek vaší aplikace v každé zarážce a ladicí program krok události. Zaznamenané snímky umožňují snadno vrátit k předchozím zarážkám nebo krokům a zobrazit stav aplikace jako v minulosti. IntelliTrace zpětným krokem vám může ušetřit čas při chcete zobrazit předchozí stav aplikace, ale nebudete chtít znovu spusťte ladění nebo znovu vytvořit stav požadované aplikace.

Můžete procházet a zobrazit snímky pomocí **krok zpět** a **krok vpřed** tlačítka na panelu nástrojů ladění. Tato tlačítka Procházet události, které se zobrazují v **události** kartu **diagnostické nástroje** okna.

![Krokovat zpět a vpřed tlačítka](../debugger/media/intellitrace-step-back-icons-description.png  "krok zpět a vpřed tlačítka")

Další informace najdete v tématu [kontrolovat předchozí nové aplikace pomocí nástroje IntelliTrace](../debugger/view-historical-application-state.md) stránky.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste měli rychlý přehled mnoha funkcí ladicího programu. Může být vhodné podrobnější pohled na tyto funkce pomocí ukázkové aplikace

> [!div class="nextstepaction"]
> [Další informace k ladění pomocí sady Visual Studio](../debugger/getting-started-with-the-debugger.md)
