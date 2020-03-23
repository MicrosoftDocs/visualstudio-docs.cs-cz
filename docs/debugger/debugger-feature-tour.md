---
title: První seznámení s ladicím programem
description: Začínáme s laděním aplikací pomocí ladicího programu Sady Visual Studio
ms.custom: ''
ms.date: 04/08/2019
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 93973322c40ca62396414317c2ad8875e9b94854
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77578955"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>První pohled na ladicí program visual studia

Toto téma představuje nástroje ladicího programu poskytované visual studio. V kontextu Visual Studio při *ladění aplikace*, obvykle znamená, že spouštějíte aplikaci s připojeným ladicím programem (to znamená v režimu ladicího programu). Když toto uděláte, ladicí program poskytuje mnoho způsobů, jak zjistit, co váš kód dělá při jeho spuštění. Můžete krokovat kód a podívat se na hodnoty uložené v proměnných, můžete nastavit hodinky na proměnné, abyste viděli, kdy se hodnoty mění, můžete prozkoumat cestu spuštění kódu et al. Pokud je to poprvé, co jste se pokusili ladit kód, můžete si přečíst [ladění pro absolutní začátečníky](../debugger/debugging-absolute-beginners.md) před procházením tohoto tématu.

Zde popsané funkce se vztahují na jazyky C#, C++, Visual Basic, JavaScript a další jazyky podporované visual studio (s výjimkou případů, kdy je uvedeno jinak).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Nastavení zarážky a spuštění ladicího programu

Chcete-li ladit, musíte spustit aplikaci s ladicím programem připojeným k procesu aplikace. **F5** (**Ladění > Start Ladění**) je nejběžnější způsob, jak to udělat. V současné době však nemusí mít nastaveny žádné zarážky pro zkoumání kódu aplikace, takže to nejprve provedeme a pak začneme ladění. Zarážky jsou základní a nejjednodušší funkcí spolehlivého ladění. Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští.

Pokud máte soubor otevřený v editoru kódu, můžete nastavit zarážku kliknutím na okraj vlevo od řádku kódu.

![Nastavení zarážky](../debugger/media/dbg-tour-set-a-breakpoint.gif "Nastavení zarážky")

Stiskněte **klávesu F5** (**Ladění > spuštění ladění)** nebo tlačítko Spustit **ladění** ![Spustit ladění](../debugger/media/dbg-tour-start-debugging.png "Spustit ladění") na panelu nástrojů Ladění a ladicí program se spustí na první zarážku, se kterou narazí. Pokud aplikace ještě není spuštěna, F5 spustí ladicí program a zastaví se na první zarážky.

Zarážky jsou užitečnou funkcí, pokud znáte řádek kódu nebo část kódu, kterou chcete podrobně prozkoumat.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a><a name="navigate"></a>Navigace v kódu v ladicím programu pomocí příkazů kroku

Pro většinu příkazů poskytujeme klávesové zkratky, protože navigace kódu aplikace upřesní. (Ekvivalentní příkazy, například příkazy nabídky, jsou zobrazeny v závorce.)

Chcete-li aplikaci spustit s připojeným ladicím programem, stiskněte **klávesu F11** **(Ladění > krok do).** F11 je **krok do** příkazu a zálohy spuštění aplikace jeden příkaz najednou. Při spuštění aplikace s F11 ladicí program se rozdělí na první příkaz, který se spustí.

![F11 krok do](../debugger/media/dbg-tour-f11.png "F11 krok do")

Žlutá šipka představuje příkaz, na kterém ladicí program pozastaven, který také pozastaví spuštění aplikace ve stejném bodě (tento příkaz ještě nebyl proveden).

F11 je dobrý způsob, jak prozkoumat tok provádění v nejpodrobněji. (Chcete-li se pohybovat rychleji prostřednictvím kódu, ukážeme vám také některé další možnosti.) Ve výchozím nastavení ladicí program přeskočí kód uživatele (pokud chcete další podrobnosti, přečtěte [si část Pouze můj kód).](../debugger/just-my-code.md)

>[!NOTE]
> Ve spravovaném kódu se zobrazí dialogové okno s dotazem, zda chcete být upozorněni, když automaticky krokujete vlastnosti a operátory (výchozí chování). Chcete-li nastavení později změnit, zakažte nastavení **vlastností a operátorů v** nabídce **Možnosti nástroje >** v části **Ladění**.

## <a name="step-over-code-to-skip-functions"></a>Krok přes kód přeskočit funkce

Pokud jste na řádku kódu, který je volání funkce nebo metody, můžete stisknout **Klávesu F10** **(Ladění > krok přes)** namísto F11.

F10 posune ladicí program bez krokování do funkcí nebo metod v kódu aplikace (kód se stále spustí). Stisknutím klávesy F10 můžete přeskočit kód, který vás nezajímá. Tímto způsobem se můžete rychle dostat ke kódu, který vás více zajímá.

## <a name="step-into-a-property"></a>Krok do nemovitosti

Jak již bylo zmíněno dříve, ladicí program ve výchozím nastavení přeskočí spravované vlastnosti a pole, ale příkaz **Krok do určitého** umožňuje přepsat toto chování.

Klikněte pravým tlačítkem myši na vlastnost nebo pole a zvolte **Krok do konkrétního**, pak zvolte jednu z dostupných možností.

![Krok do konkrétní](../debugger/media/dbg-tour-step-into-specific.png "Krok do konkrétní")

V tomto příkladu **krok do konkrétní** `Path.set`nás dostane do kódu pro .

![Krok do konkrétní](../debugger/media/dbg-tour-step-into-specific-2.png "Krok do konkrétní")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Rychlé spuštění kódu do bodu, kdy můžete začít používat

Zatímco v ladicím programu, najeďte přes řádek kódu, dokud **spustit kliknutím** (Spustit spuštění sem) tlačítko ![Spustit kliknutím](../debugger/media/dbg-tour-run-to-click.png "RunToClick") se zobrazí na levé straně.

![Běžet do kliknutí](../debugger/media/dbg-tour-run-to-click-2.png "Běžet do kliknutí")

> [!NOTE]
> Spustit **kliknutím** (Spustit spuštění sem) tlačítko [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]je k dispozici od .

Klikněte na tlačítko **Spustit kliknutím** (Spustit spuštění sem). Ladicí program přejdete na řádek kódu, na který jste klikli.

Použití tohoto tlačítka je podobné nastavení dočasné zarážky. Tento příkaz je také užitečné pro rychlé obcíní v rámci viditelné oblasti kódu aplikace. Můžete použít **Spustit kliknutím** v libovolném otevřeném souboru.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Posun ladicího programu mimo aktuální funkci

Někdy můžete chtít pokračovat v relaci ladění, ale předem ladicí program celou cestu přes aktuální funkce.

Stiskněte **Shift + F11** (nebo **Ladění > krok ven).**

Tento příkaz obnoví spuštění aplikace (a posune ladicí program), dokud se nevrátí aktuální funkce.

## <a name="run-to-cursor"></a>Spustit na kurzor

Zastavte ladicí program stisknutím červeného ![tlačítka](../debugger/media/dbg-tour-stop-debugging.png "Zastavit ladění") **Zastavit** ladění nebo **Shift** + **F5**.

Klikněte pravým tlačítkem myši na řádek kódu v aplikaci a zvolte **Spustit kurzor**. Tento příkaz spustí ladění a nastaví dočasnou zarážku na aktuálním řádku kódu.

![Spustit na kurzor](../debugger/media/dbg-tour-run-to-cursor.png "Spustit na kurzor")

Pokud jste nastavili zarážky, ladicí program se pozastaví na první zarážku, která přístupů.

Stiskněte **klávesu F5,** dokud nedosáhnete řádku kódu, ve kterém jste vybrali **možnost Spustit kurzor**.

Tento příkaz je užitečný při úpravách kódu a chcete rychle nastavit dočasnou zarážku a současně spustit ladicí program.

> [!NOTE]
> Můžete použít **Spustit kurzor** v okně **zásobníku volání** při ladění.

## <a name="restart-your-app-quickly"></a>Rychlé restartování aplikace

Klepněte na tlačítko **Restartovat** ![aplikaci](../debugger/media/dbg-tour-restart.png "Restartovat aplikaci") na panelu nástrojů ladění (**Ctrl + Shift +F5**).

Po stisknutí tlačítka **Restart**ušetří tečas oproti zastavení aplikace a restartování ladicího programu. Ladicí program se pozastaví na první zarážku, která je přístupná spuštěním kódu.

Pokud chcete zastavit ladicí program a vrátit se do editoru kódu, můžete místo **restartovat**klávesu stisknout červené tlačítko ![Stop Debugging](../debugger/media/dbg-tour-stop-debugging.png "Zastavit ladění") .

## <a name="edit-your-code-and-continue-debugging-c-vb-c-xaml"></a>Upravte kód a pokračujte v ladění (C#, VB, C++, XAML)

Ve většině jazyků podporovaných visual studio, můžete upravit kód uprostřed relace ladění a pokračovat v ladění. Chcete-li tuto funkci použít, klikněte do kódu kurzorem, zatímco pozastaveno v ladicím programu, provést úpravy a stiskněte **Klávesu F5**, **F10**nebo **F11** pokračovat ladění.

![Úprava a pokračování ladění](../debugger/media/dbg-tips-edit-and-continue.gif "Editand Pokračovat")

Další informace o používání funkce a omezeních funkcí naleznete v tématu [Úpravy a pokračování](../debugger/edit-and-continue.md).

Chcete-li upravit kód XAML během relace ladění, přečtěte si informace o [zápisu a ladění se spuštěným kódem XAML s opětovným načtením xaml.](../xaml-tools/xaml-hot-reload.md)

## <a name="inspect-variables-with-data-tips"></a>Kontrola proměnných pomocí datových špiček

Teď, když se trochu znáte, máte dobrou příležitost začít kontrolovat stav aplikace (proměnné) s ladicím programem. Funkce, které umožňují kontrolovat proměnné jsou některé z nejužitečnějších funkcí ladicího programu a existují různé způsoby, jak to udělat. Často při pokusu o ladění problému se pokoušíte zjistit, zda proměnné ukládají hodnoty, které očekáváte, že budou mít v určitém stavu aplikace.

Při pozastavení v ladicím programu najeďte myší na objekt a zobrazí se jeho výchozí `market 031.jpg` hodnota vlastnosti (v tomto příkladu je název souboru výchozí hodnotou vlastnosti).

![Zobrazení tipu na data](../debugger/media/dbg-tour-data-tips.gif "Zobrazení tipu na data")

Rozbalte objekt zobrazíte všechny jeho `FullPath` vlastnosti (například vlastnost v tomto příkladu).

Často při ladění, chcete rychlý způsob, jak zkontrolovat hodnoty vlastností na objekty a tipy dat jsou dobrý způsob, jak to udělat.

> [!TIP]
> Ve většině podporovaných jazyků můžete upravit kód uprostřed relace ladění. Další informace najdete v [tématu Úpravy a pokračování](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Kontrola proměnných pomocí oken Autos a Locals

Při ladění se podívejte na okno **Autos** v dolní části editoru kódu.

![Okno Autos](../debugger/media/dbg-tour-autos-window.png "Automatické hodnoty – okno")

V okně **Autos** se zobrazí proměnné spolu s jejich aktuální hodnotou a jejich typem. Okno **Autos** zobrazuje všechny proměnné použité na aktuálním řádku nebo na předchozím řádku (v jazyce C++ se v okně zobrazí proměnné v předchozích třech řádcích kódu. Zkontrolujte dokumentaci pro chování specifické pro jazyk).

> [!NOTE]
> V jazyce JavaScript je podporováno okno **Locals,** ale ne okno **Autos.**

Dále se podívejte na okno **Locals.** Místní **Locals** okno zobrazí proměnné, které jsou aktuálně v oboru.

![Místní okno](../debugger/media/dbg-tour-locals-window.png "Místní hodnoty – okno")

V tomto příkladu `this` objekt `f` a objekt jsou v oboru. Další informace naleznete [v tématu Kontrola proměnných v systému Autos a Locals Windows](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Nastavení hodinek

Okno **Kukátko** můžete použít k určení proměnné (nebo výrazu), na kterou chcete dávat pozor.

Při ladění klepněte pravým tlačítkem myši na objekt a zvolte **Přidat hodinky**.

![Okno kukátka](../debugger/media/dbg-tour-watch-window.png "Kukátko – okno")

V tomto příkladu máte hodinky `f` nastavit na objekt uvidíte jeho změnu hodnoty při procházení ladicího programu. Na rozdíl od ostatních proměnných **oken, hodinky** okna vždy zobrazit proměnné, které sledujete (jsou šedě, když mimo rozsah).

Další informace najdete [v tématu Nastavení kuse pomocí watch a quickwatch windows](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>Zkontrolujte zásobník volání

Při ladění klikněte na okno **Zásobník volání,** které je ve výchozím nastavení otevřeno v pravém dolním podokně.

![Zkontrolujte zásobník volání](../debugger/media/dbg-tour-call-stack.png "Zkontrolujte zásobník volání")

Okno **Zásobník volání** zobrazuje pořadí, ve kterém jsou volány metody a funkce. Horní řádek zobrazuje aktuální funkci `Update` (metoda v tomto příkladu). Druhý řádek ukazuje, že `Update` `Path.set` byl volán z vlastnosti a tak dále. Zásobník volání je dobrý způsob, jak prozkoumat a pochopit tok spuštění aplikace.

> [!NOTE]
> Okno **Zásobník volání** je podobné perspektivě ladění v některých IDE, jako je Eclipse.

Můžete poklepat na řádek kódu jít podívat na tento zdrojový kód a že také změní aktuální obor kontrolovány ladicí program. To neposune ladicí program.

Můžete také použít nabídky po kliknutí pravým tlačítkem myši z okna **Zásobník volání** k jiným věcem. Můžete například vložit zarážky do konkrétních funkcí, restartovat aplikaci pomocí **spustit kurzor**a přejít ke kontrole zdrojového kódu. Viz [Postup: Zkontrolujte zásobník volání](../debugger/how-to-use-the-call-stack-window.md).

## <a name="examine-an-exception"></a><a name="exception"></a>Přezkoumat výjimku

Když vaše aplikace vyvolá výjimku, ladicí program vás přenese na řádek kódu, který vyvolal výjimku.

![Pomocník pro výjimky](../debugger/media/dbg-tour-exception-helper.png "Pomocník pro výjimky")

V tomto příkladu pomocník a `System.Argument` **výjimky** zobrazí výjimku a chybovou zprávu, která říká, že cesta není právní forma. Takže víme, že došlo k chybě na metodu nebo funkce argument.

V tomto příkladu `DirectoryInfo` volání dal chybu na prázdný `value` řetězec uložený v proměnné.

Pomocník výjimek je skvělá funkce, která vám může pomoci při ladění chyb. Můžete také dělat věci, jako je zobrazení podrobností o chybě a přidání hodinek z pomocníka pro výjimky. Nebo v případě potřeby můžete změnit podmínky pro vyvolání konkrétní výjimky. Další informace o tom, jak zpracovat výjimky v kódu, naleznete v [tématu](../debugger/write-better-code-with-visual-studio.md)ladění techniky a nástroje .

> [!NOTE]
> Pomocník pro výjimky nahradil Pomocníka [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]pro výjimky začínající v .

Rozbalte uzel **Nastavení výjimek,** abyste viděli další možnosti, jak zpracovat tento typ výjimky, ale nemusíte nic měnit pro tuto prohlídku!

## <a name="configure-debugging"></a>Konfigurace ladění

Projekt můžete nakonfigurovat tak, aby byl vytvářen jako [konfigurace ladění nebo vydání](../debugger/how-to-set-debug-and-release-configurations.md), nakonfiguroval vlastnosti projektu pro ladění nebo nakonfiguroval obecné [nastavení](../debugger/how-to-specify-debugger-settings.md) ladění. Kromě toho můžete nakonfigurovat ladicí program pro zobrazení vlastních informací pomocí funkcí, jako je [debuggerDisplay](using-the-debuggerdisplay-attribute.md) atribut nebo pro C/C++, [rozhraní NatVis](create-custom-views-of-native-objects.md).

Ladění vlastnosti jsou specifické pro každý typ projektu. Můžete například zadat argument, který má být předáván aplikaci při spuštění. K vlastnostem specifickým pro projekt můžete získat přístup klepnutím pravým tlačítkem myši na projekt v Průzkumníku řešení a výběrem **příkazu Vlastnosti**. Ladění vlastnosti se obvykle zobrazí na kartě **Sestavení** nebo **ladění,** v závislosti na konkrétním typu projektu.

![Vlastnosti projektu](../debugger/media/dbg-tour-project-properties.png "Vlastnosti projektu")

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Ladění aplikací živého ASP.NET ve službě Azure App Service

**Snímek debugger** pořídí snímek vašich produkčních aplikací při kódu, který vás zajímá provede. Chcete-li pokyn ladicí program pořídit snímek, nastavte snappoints a logpoints v kódu. Ladicí program umožňuje přesně zobrazit, co se pokazilo, aniž by to mělo vliv na provoz produkční aplikace. Ladicí program snímek vám může pomoci výrazně zkrátit dobu potřebný k vyřešení problémů, ke kterým dochází v produkčním prostředí.

![Spuštění ladicího programu snímků](../debugger/media/snapshot-launch.png "Spuštění ladicího programu snímků")

Kolekce snímků je k dispozici pro ASP.NET aplikace spuštěné ve službě Azure App Service. ASP.NET aplikace musí být spuštěny v rozhraní .NET Framework 4.6.1 nebo novější a ASP.NET základní aplikace musí být spuštěny v rozhraní .NET Core 2.0 nebo novější v systému Windows.

Další informace naleznete [v tématu Ladění živých ASP.NET aplikací pomocí ladicího programu snímek](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Zobrazení snímků pomocí krokového zpětného kroku IntelliTrace (Visual Studio Enterprise)

**Krok zpět intelliTrace** automaticky pořídí snímek vaší aplikace při každé události kroku zarážky a ladicího programu. Zaznamenané snímky umožňují vrátit se k předchozím zarážky nebo kroky a zobrazit stav aplikace, jak tomu bylo v minulosti. IntelliTrace krok-back můžete ušetřit čas, když chcete zobrazit předchozí stav aplikace, ale nechcete restartovat ladění nebo znovu vytvořit požadovaný stav aplikace.

Snímky můžete procházet a zobrazovat pomocí tlačítek **Krok vpřed** a **Krok vpřed** na panelu nástrojů Ladění. Tato tlačítka procházet události, které se zobrazí na kartě **Události** v okně **Diagnostické nástroje.**

![Kroková tlačítka vpřed a vpřed](../debugger/media/intellitrace-step-back-icons-description.png  "Krok vpřed a vpřed")

Další informace najdete v [tématu Kontrola předchozích stavů aplikace pomocí stránky IntelliTrace.](../debugger/view-historical-application-state.md)

## <a name="debug-performance-issues"></a>Problémy s výkonem ladění

Pokud vaše aplikace běží příliš pomalu nebo používá příliš mnoho paměti, možná budete muset aplikaci otestovat pomocí nástrojů pro profilování v rané fázi. Další informace o nástrojích profilování, jako je například nástroj využití procesoru a analyzátor paměti, naleznete [v tématu První pohled na nástroje profilování](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste měli rychlý pohled na mnoho funkcí ladicího programu. Můžete chtít podrobnější pohled na jednu z těchto funkcí, jako jsou například zarážky.

> [!div class="nextstepaction"]
> [Naučte se používat zarážky](../debugger/using-breakpoints.md)
