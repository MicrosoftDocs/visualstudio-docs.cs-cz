---
title: První seznámení s ladicím programem
description: Začínáme s laděním aplikací pomocí ladicího programu sady Visual Studio
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
ms.openlocfilehash: c6d451735042374f0e3c6fb2154cd54520a069fc
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761430"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>První pohled na ladicí program sady Visual Studio

Toto téma představuje nástroje ladicího programu, které poskytuje Visual Studio. V kontextu sady Visual Studio se při *ladění aplikace* obvykle to znamená, že spouštíte aplikaci s připojeným ladicím programem (tj. v režimu ladění). Když to uděláte, ladicí program poskytuje mnoho způsobů, jak zjistit, co váš kód při spuštění dělá. Můžete si projít kód a prohlédnout si hodnoty uložené v proměnných, můžete nastavit hodinky pro proměnné, abyste viděli, kdy se hodnoty mění, můžete zkontrolovat cestu provádění vašeho kódu, a to et al. Pokud se jedná o první pokus o ladění kódu, můžete si před tím, než projdete toto téma, přečíst [ladění pro absolutní začátečníky](../debugger/debugging-absolute-beginners.md) .

Zde popsané funkce platí pro C#, C++, Visual Basic, JavaScript a další jazyky, které podporuje Visual Studio (s výjimkou popsaných případů).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Nastavit zarážku a spustit ladicí program

Pro ladění musíte aplikaci spustit pomocí ladicího programu připojeného k procesu aplikace. **F5** (**ladění > spustit ladění**) je nejběžnější způsob, jak to provést. V současné době ale nemůžete mít nastavené žádné zarážky pro kontrolu kódu vaší aplikace, proto to provedeme a pak spustíte ladění. Zarážky jsou základní a nejjednodušší funkcí spolehlivého ladění. Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští.

Pokud máte otevřený soubor v editoru kódu, můžete nastavit zarážku kliknutím na okraj nalevo od řádku kódu.

![Nastavit zarážku](../debugger/media/dbg-tour-set-a-breakpoint.gif "Nastavení zarážky")

Stiskněte **F5** (**ladění > spustit ladění**) nebo tlačítko **Spustit ladění** ![Spustit ladění](../debugger/media/dbg-tour-start-debugging.png "Spustit ladění") na panelu nástrojů ladění a ladicí program se spustí na první zarážku, ke které dojde. Pokud aplikace ještě není spuštěná, spustí F5 ladicí program a zastaví se na první zarážce.

Zarážky jsou užitečnou funkcí, když znáte řádek kódu nebo oddíl kódu, který chcete podrobně prošetřit.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a><a name="navigate"></a> Procházení kódu v ladicím programu pomocí příkazů Step

Klávesové zkratky pro většinu příkazů poskytujeme, protože usnadňují navigaci v kódu vaší aplikace. (Ekvivalentní příkazy, jako jsou například příkazy nabídky, jsou uvedeny v závorkách.)

Pokud chcete aplikaci spustit pomocí připojeného ladicího programu, stiskněte klávesu **F11** (**ladění > krokovat do**). Klávesa F11 je **Krok do** příkazu a aplikace pokračuje v jednom příkazu v jednom okamžiku. Při spuštění aplikace pomocí klávesy F11 se ladicí program ukončí na prvním příkazu, který se spustí.

![F11 Krokovat s vnořením](../debugger/media/dbg-tour-f11.png "F11 Krokovat s vnořením")

Žlutá šipka představuje příkaz, na kterém je ladicí program pozastaven, což také pozastavuje spuštění aplikace ve stejném bodě (Tento příkaz ještě nebyl proveden).

Klávesa F11 je dobrým způsobem, jak prostudovat tok spouštění v nejpodrobnějším podrobnostech. (K rychlejšímu přesunu kódu vám ukážeme i některé další možnosti.) Ve výchozím nastavení přeskočí ladicí program neuživatelský kód (Pokud chcete více podrobností, přečtěte si téma [pouze můj kód](../debugger/just-my-code.md)).

>[!NOTE]
> Ve spravovaném kódu se zobrazí dialogové okno s dotazem, zda chcete být upozorněni, když automaticky provedete krok nad vlastnostmi a operátory (výchozí chování). Chcete-li změnit nastavení později, v nabídce **nástroje > možnosti** v části **ladění** zakažte možnost **Krokovat přes vlastnosti a operátory** .

## <a name="step-over-code-to-skip-functions"></a>Krokovat s kódem pro přeskočení funkcí

Pokud jste na řádku kódu, který je funkcí nebo voláním metody, můžete stisknout **F10** (**ladění > krokování**) místo klávesy F11.

F10 posune ladicí program bez krokování do funkcí nebo metod v kódu aplikace (kód se pořád spustí). Stisknutím klávesy F10 můžete přeskočit kód, na který nejste zajímat. Tímto způsobem můžete rychle získat kód, který vás zajímá.

## <a name="step-into-a-property"></a>Krokovat s vlastností

Jak bylo zmíněno dříve, ladicí program ve výchozím nastavení přeskočí spravované vlastnosti a pole, ale **Krok do konkrétního** příkazu umožňuje toto chování přepsat.

Klikněte pravým tlačítkem na vlastnost nebo pole a zvolte **Krok do konkrétní** a pak zvolte jednu z dostupných možností.

![Snímek obrazovky ladicího programu sady Visual Studio se zvýrazněným řádkem kódu Krok do konkrétní je vybrán v místní nabídce a je vybrána metoda Path. set.](../debugger/media/dbg-tour-step-into-specific.png)

V tomto příkladu se **Krok do konkrétní** dostane do kódu pro `Path.set` .

![Snímek obrazovky ladicího programu sady Visual Studio zobrazující kód pro cestu. set. Složené závorky obklopující funkci set jsou zvýrazněné žlutě.](../debugger/media/dbg-tour-step-into-specific-2.png)

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Rychlé spuštění s bodem v kódu pomocí myši

Když jste v ladicím programu, najeďte myší na řádek kódu, dokud nekliknete na tlačítko **Spustit** pro kliknutí (spustit do tohoto pole) na tlačítku ![ Spustit pro klikněte v ladicím programu sady Visual Studio. Tlačítko označuje, že spuštění by mělo běžet na řádek, kde je tlačítko umístěno.](../debugger/media/dbg-tour-run-to-click.png) zobrazí se vlevo.

![Snímek obrazovky ladicího programu sady Visual Studio zobrazující tlačítko spustit pro kliknutí, které se zobrazuje hned vlevo od volání funkce Update](../debugger/media/dbg-tour-run-to-click-2.png)

> [!NOTE]
> Tlačítko **spustit do kliknutím** (spustit do tohoto umístění) je dostupné od začátku v [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] .

Klikněte na tlačítko **Spustit pro kliknutím** (spustit do tohoto umístění). Ladicí program přejde na řádek kódu, na který jste klikli.

Použití tohoto tlačítka je podobné nastavení dočasné zarážky. Tento příkaz je také užitečný pro rychlé seznámení v rámci viditelné oblasti kódu aplikace. Pomocí rutiny **Run můžete kliknout** na libovolný otevřený soubor.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Posunutí ladicího programu z aktuální funkce

V některých případech možná budete chtít pokračovat v relaci ladění, ale ladicí program můžete procházet všemi způsoby prostřednictvím aktuální funkce.

Stiskněte **SHIFT + F11** (nebo **ladění > krokovat**).

Tento příkaz obnoví spuštění aplikace (a ladicí program posune), dokud aktuální funkce nevrátí.

## <a name="run-to-cursor"></a>Spustit ke kurzoru

Pokud upravujete kód (místo pozastavení v ladicím programu), klikněte pravým tlačítkem myši na řádek kódu v aplikaci a vyberte možnost **Spustit ke kurzoru**. Tento příkaz spustí ladění a nastaví dočasnou zarážku na aktuálním řádku kódu.

![Spustit ke kurzoru](../debugger/media/dbg-tour-run-to-cursor.png "Spustit ke kurzoru")

Pokud jste nastavili zarážky, ladicí program se pozastaví na první zarážce, ke které má narazí.

Stiskněte klávesu **F5** , dokud se nedostanete na řádek kódu, kde jste vybrali **možnost Spustit ke kurzoru**.

Tento příkaz je užitečný při úpravách kódu a chcete rychle nastavit dočasnou zarážku a spustit ladicí program současně.

> [!NOTE]
> Při ladění můžete použít **příkaz Spustit ke kurzoru** v okně **zásobník volání** .

## <a name="restart-your-app-quickly"></a>Rychlé restartování aplikace

Klikněte na tlačítko **restartovat** ![aplikaci](../debugger/media/dbg-tour-restart.png "Restartovat aplikaci") na panelu nástrojů ladění (**CTRL + SHIFT + F5**).

Po stisknutí tlačítka **restartovat** ušetří čas oproti zastavování aplikace a restartování ladicího programu. Ladicí program se pozastaví na první zarážce, která je dosaženo spuštěním kódu.

Pokud chcete zastavit ladicí program a vrátit se zpět do editoru kódu, můžete stisknout červené tlačítko Zastavit ![ladění](../debugger/media/dbg-tour-stop-debugging.png "Zastavit ladění") namísto **restartu**.

## <a name="edit-your-code-and-continue-debugging-c-vb-c-xaml"></a>Úprava kódu a pokračování v ladění (C#, VB, C++, XAML)

Ve většině jazyků podporovaných v rámci sady Visual Studio můžete upravit kód uprostřed relace ladění a pokračovat v ladění. Chcete-li použít tuto funkci, klikněte na svůj kód v průběhu pozastaveného ladicího programu, proveďte úpravy a stisknutím klávesy **F5**, **F10** nebo **F11** pokračujte v ladění.

![Upravit a pokračovat v ladění](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Další informace o používání funkce a omezení funkcí najdete v tématu [Upravit a pokračovat](../debugger/edit-and-continue.md).

Chcete-li upravit kód XAML během relace ladění, [Přečtěte si téma zápis a ladění spouštění kódu XAML pomocí programu XAML Hot reloading](../xaml-tools/xaml-hot-reload.md).

## <a name="inspect-variables-with-data-tips"></a>Kontrola proměnných pomocí tipů k datům

Když teď víte, že jste trochu, měli byste mít dobrou možnost začít kontrolovat stav vaší aplikace (proměnné) pomocí ladicího programu. Funkce, které umožňují kontrolu proměnných, jsou některé z nejužitečnějších funkcí ladicího programu a existují různé způsoby, jak to provést. Při pokusu o ladění problému se často snažíte zjistit, jestli proměnné ukládají hodnoty, které očekáváte v určitém stavu aplikace.

Při pozastavení v ladicím programu, najeďte myší na objekt pomocí myši a zobrazí se jeho výchozí hodnota vlastnosti (v tomto příkladu je název souboru `market 031.jpg` Výchozí hodnota vlastnosti).

![Zobrazit Tip pro data](../debugger/media/dbg-tour-data-tips.gif "Zobrazit Tip pro data")

Rozbalením objektu zobrazíte všechny jeho vlastnosti (například `FullPath` vlastnost v tomto příkladu).

Často se při ladění požaduje rychlý způsob kontroly hodnot vlastností u objektů a tipy k datům představují dobrý způsob, jak to provést.

> [!TIP]
> V nejvíce podporovaných jazycích můžete kód upravit uprostřed relace ladění. Další informace najdete v tématu [Upravit a pokračovat](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Kontrola proměnných pomocí oken automatické hodnoty a místní hodnoty

Během ladění se v dolní části editoru kódu podívejte na okno **Automatické** hodnoty.

![Okno Automatické hodnoty](../debugger/media/dbg-tour-autos-window.png "Automatické hodnoty – okno")

V okně **Automatické** hodnoty vidíte proměnné spolu s jejich aktuální hodnotou a jejich typem. Okno **Automatické** hodnoty zobrazuje všechny proměnné, které jsou použity na aktuálním řádku nebo v předchozím řádku (v jazyce C++, okno zobrazuje proměnné v předchozích třech řádcích kódu. Podívejte se na dokumentaci pro specifické chování jazyka).

> [!NOTE]
> V jazyce JavaScript je okno **místní** hodnoty podporováno, ale ne okno **Automatické** hodnoty.

Potom se podívejte do okna **místní** hodnoty. V okně **místní** hodnoty se zobrazí proměnné, které jsou aktuálně v oboru.

![Okno místních hodnot](../debugger/media/dbg-tour-locals-window.png "Místní hodnoty – okno")

V tomto příkladu je `this` objekt a objekt `f` v rozsahu. Další informace najdete v tématu [Kontrola proměnných v oknech automatické hodnoty a místní](../debugger/autos-and-locals-windows.md)hodnoty.

## <a name="set-a-watch"></a>Nastavení kukátka

Okno **kukátka** můžete použít k určení proměnné (nebo výrazu), pro kterou chcete zachovat oči.

Při ladění klikněte pravým tlačítkem myši na objekt a vyberte možnost **Přidat kukátko**.

![Okno kukátka](../debugger/media/dbg-tour-watch-window.png "Kukátko – okno")

V tomto příkladu máte na objektu nastavenou kukátko `f` a při přesunu prostřednictvím ladicího programu můžete zobrazit jeho změnu hodnoty. Na rozdíl od ostatních oken proměnných se v oknech **kukátka** vždy zobrazují proměnné, které sledujete (v případě nedostatku rozsahu jsou šedé).

Další informace najdete v tématu [Nastavení kukátka pomocí oken kukátka a QuickWatch](../debugger/watch-and-quickwatch-windows.md) .

## <a name="examine-the-call-stack"></a>Kontrola zásobníku volání

Při ladění klikněte na okno **zásobník volání** , což je ve výchozím nastavení otevřené v pravém dolním podokně.

![Kontrola zásobníku volání](../debugger/media/dbg-tour-call-stack.png "Kontrola zásobníku volání")

Okno **zásobník volání** zobrazuje pořadí, ve kterém jsou metody a funkce volány. V horním řádku se zobrazuje aktuální funkce ( `Update` metoda v tomto příkladu). Druhý řádek ukazuje, který `Update` byl volán z `Path.set` vlastnosti a tak dále. Zásobník volání je dobrým způsobem, jak prostudovat a pochopit tok spuštění aplikace.

> [!NOTE]
> Okno **zásobník volání** je podobné perspektivě ladění v některých prostředích, jako je například zatmění.

Dvakrát klikněte na řádek kódu, abyste se mohli podívat na zdrojový kód a zároveň změnit aktuální rozsah, který je kontrolován ladicím programem. Toto nepokročilý ladicí program.

Můžete také použít nabídky kliknutím pravým tlačítkem z okna **zásobník volání** k provedení dalších akcí. Například můžete vložit zarážky do konkrétních funkcí, restartovat aplikaci pomocí funkce **Spustit na kurzor** a přejít na zdrojový kód. Viz [Postupy: prohlédnutí zásobníku volání](../debugger/how-to-use-the-call-stack-window.md).

## <a name="examine-an-exception"></a><a name="exception"></a> Kontrola výjimky

Když vaše aplikace vyvolá výjimku, ladicí program přejde na řádek kódu, který vyvolal výjimku.

![Pomocník pro výjimky](../debugger/media/dbg-tour-exception-helper.png "Pomocník pro výjimky")

V tomto příkladu Pomocník pro **výjimky** ukazuje `System.Argument` výjimku a chybovou zprávu, která říká, že cesta není právním formulářem. Proto víme, že k chybě došlo v argumentu metody nebo funkce.

V tomto příkladu `DirectoryInfo` volání vrátilo chybu v prázdném řetězci uloženém v `value` proměnné.

Pomocný Pomocník pro výjimky je skvělou funkcí, která vám může pomoci při ladění chyb. Můžete také provádět věci, jako jsou podrobnosti o chybě zobrazení a Přidat kukátko z pomocníka výjimky. Nebo v případě potřeby můžete změnit podmínky pro vyvolání konkrétní výjimky. Další informace o tom, jak zpracovávat výjimky v kódu, naleznete v tématu [techniky a nástroje ladění](../debugger/write-better-code-with-visual-studio.md).

> [!NOTE]
> Pomocník výjimek nahradil pomocníka výjimky od začátku [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] .

Rozbalením uzlu **Nastavení výjimek** zobrazíte další možnosti, jak tento typ výjimky zpracovat, ale nemusíte u této prohlídky nic měnit.

## <a name="configure-debugging"></a>Konfigurace ladění

Můžete nakonfigurovat projekt tak, aby se vytvořil jako [Konfigurace ladění nebo vydání](../debugger/how-to-set-debug-and-release-configurations.md), konfigurovat vlastnosti projektu pro ladění nebo konfigurovat [Obecné nastavení](../debugger/how-to-specify-debugger-settings.md) pro ladění. Kromě toho můžete nakonfigurovat ladicí program tak, aby zobrazoval vlastní informace pomocí funkcí, jako je například atribut [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) nebo, pro C/C++, [rozhraní NatVis](create-custom-views-of-native-objects.md).

Vlastnosti ladění jsou specifické pro každý typ projektu. Můžete například zadat argument, který má být aplikaci předána při jejím spuštění. K vlastnostem specifickým pro projekt máte přístup kliknutím pravým tlačítkem myši na projekt v Průzkumník řešení a výběrem **vlastností**. Vlastnosti ladění obvykle se zobrazí na kartě **sestavení** nebo **ladění** v závislosti na konkrétním typu projektu.

![Vlastnosti projektu](../debugger/media/dbg-tour-project-properties.png "Vlastnosti projektu")

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Ladění živých aplikací ASP.NET v Azure App Service

**Snapshot Debugger** pořizování snímku vašich aplikací v produkčním prostředí, když máte spuštěný kód. Chcete-li ladicímu programu dát pokyn k pořízení snímku, nastavte snímkovací body a protokolovacích bodů ve svém kódu. Ladicí program vám umožní zobrazit přesně to, co se nepovedlo, aniž by to ovlivnilo provoz vaší produkční aplikace. Snapshot Debugger vám může výrazně zkrátit dobu potřebnou k vyřešení problémů, ke kterým dochází v produkčních prostředích.

![Spustit ladicí program snímků](../debugger/media/snapshot-launch.png "Spustit ladicí program snímků")

Kolekce snímků je k dispozici pro aplikace ASP.NET běžící v Azure App Service. ASP.NET aplikace musí běžet na .NET Framework 4.6.1 nebo novějším. ASP.NET Core aplikace musí běžet na .NET Core 2,0 nebo novějším ve Windows.

Další informace najdete v tématu [ladění živých aplikací ASP.NET pomocí Snapshot Debugger](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Zobrazení snímků pomocí IntelliTrace kroků zpět (Visual Studio Enterprise)

**IntelliTraceý krok zpět** automaticky provede snímek vaší aplikace při každé události krok zarážky a ladicího programu. Zaznamenané snímky vám umožní přejít zpět na předchozí zarážky nebo kroky a zobrazit stav aplikace, stejně jako v minulosti. IntelliTraceý krok zpátky vám ušetří čas, když chcete zobrazit předchozí stav aplikace, ale nechcete znovu spustit ladění nebo znovu vytvořit požadovaný stav aplikace.

Snímky můžete procházet a zobrazovat pomocí tlačítek **krok zpět** a **krok vpřed** na panelu nástrojů ladění. Tato tlačítka přecházejí na události, které se zobrazí na kartě **události** v okně **diagnostické nástroje** .

![Krokovat tlačítka zpět a dopředu](../debugger/media/intellitrace-step-back-icons-description.png  "Krokovat tlačítka zpět a dopředu")

Další informace najdete v tématu [Kontrola stavů předchozích aplikací pomocí stránky IntelliTrace](../debugger/view-historical-application-state.md) .

## <a name="debug-performance-issues"></a>Ladění problémů s výkonem

Pokud vaše aplikace běží příliš pomalu nebo používá příliš mnoho paměti, možná budete muset otestovat aplikaci pomocí nástrojů pro profilaci v počátečním prostředí. Další informace o nástrojích pro profilaci, jako je nástroj využití CPU a analyzátor paměti, najdete v tématu [první pohled na nástroje pro profilaci](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Další kroky

V tomto kurzu se vám podíváme na mnoho funkcí ladicího programu. Můžete chtít podrobnější pohled na jednu z těchto funkcí, jako je například zarážky.

> [!div class="nextstepaction"]
> [Naučte se používat zarážky.](../debugger/using-breakpoints.md)
