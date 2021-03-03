---
title: Ladění vícevláknové aplikace
description: Ladění pomocí okna vlákna a panelu nástrojů umístění ladění v sadě Visual Studio
ms.date: 02/14/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cbde477e076203625e35ebf0109ed344679563f8
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683316"
---
# <a name="walkthrough-debug-a-multithreaded-app-using-the-threads-window-c-visual-basic-c"></a>Návod: Ladění vícevláknové aplikace pomocí okna vlákna (C#, Visual Basic, C++)

Některé prvky uživatelského rozhraní sady Visual Studio vám pomůžou ladit aplikace s více vlákny. Tento článek představuje vícevláknové funkce ladění v okně Editor kódu, panelu nástrojů **umístění ladění** a okně **vláken** . Informace o dalších nástrojích pro ladění aplikací s více vlákny najdete v tématu Začínáme s [laděním vícevláknových aplikací](../debugger/get-started-debugging-multithreaded-apps.md).

Dokončení tohoto kurzu trvá jenom několik minut a seznámí se základy ladění aplikací s více vlákny.

## <a name="create-a-multithreaded-app-project"></a>Vytvoření vícevláknového projektu aplikace

Vytvořte následující projekt s více vlákny pro použití v tomto kurzu:

1. Otevřete Visual Studio a vytvořte nový projekt.

   ::: moniker range=">=vs-2019"

   Pokud okno Start není otevřeno, klikněte **na tlačítko** > **Start okna**.

   V okně Start vyberte možnost **vytvořit nový projekt**.

   V okně **vytvořit nový projekt** zadejte do vyhledávacího pole nebo zadejte *Console* . Dále v seznamu jazyk vyberte **C#** nebo **C++** a v seznamu platforma zvolte **Windows** . 

   Po použití filtrů jazyků a platforem zvolte **Konzolová aplikace** pro .NET Core nebo C++ a pak zvolte **Další**.

   > [!NOTE]
   > Pokud nevidíte správnou šablonu, přejděte do části **nástroje**  >  **získat nástroje a funkce...**, které otevře instalační program pro Visual Studio. Zvolte možnost vývoj pro vývoj a vývoj pro **různé platformy .NET Core s využitím** úlohy **C++** a pak zvolte **změnit**.

   V okně **Konfigurovat nový projekt** zadejte nebo zadejte *MyThreadWalkthroughApp* do pole **název projektu** . Pak klikněte na tlačítko **Další** nebo **vytvořit**, podle toho, jaká možnost je k dispozici.

   V případě .NET Core zvolte Doporučené cílové rozhraní (.NET Core 3,1) nebo .NET 5 a pak zvolte **vytvořit**.

   ::: moniker-end
   ::: moniker range="vs-2017"
   V horním řádku nabídek vyberte **soubor**  >  **Nový**  >  **projekt**. V levém podokně dialogového okna **Nový projekt** vyberte následující:

   - V případě aplikace v jazyce C# v části **Visual C#** zvolte možnost **plocha systému Windows** a potom v prostředním podokně zvolte možnost **aplikace konzoly (.NET Framework)**.
   - V aplikaci C++ klikněte v části **Visual C++** na **plocha Windows**, a pak zvolte **Konzolová aplikace Windows**.

   Pokud nevidíte **konzolovou aplikaci (.NET Framework)** nebo, pro C++, šablona projektu **Konzolová aplikace** , přejděte do části **nástroje**  >  **získat nástroje a funkce...**, který otevře instalační program pro Visual Studio. Zvolte možnost vývoj **desktopových** aplikací pro .NET nebo **desktopové vývojové prostředí pomocí C++** a pak zvolte **Upravit**.

   Pak zadejte název jako *MyThreadWalkthroughApp* a klikněte na **OK**.

   Vyberte **OK**.
   ::: moniker-end

   Zobrazí se nový projekt konzoly. Po vytvoření projektu se zobrazí zdrojový soubor. V závislosti na zvoleném jazyce se může zdrojový soubor jmenovat *program.cs*, *MyThreadWalkthroughApp. cpp* nebo *Module1. vb*.

1. Nahraďte kód ve zdrojovém souboru ukázkovým kódem C# nebo C++ z [tématu Začínáme s laděním vícevláknových aplikací](../debugger/get-started-debugging-multithreaded-apps.md).

1. Vyberte **soubor**  >  **Uložit vše**.

## <a name="start-debugging"></a>Spustit ladění

1. Ve zdrojovém kódu Najděte tyto řádky:

   ```csharp
   Thread.Sleep(3000);
   Console.WriteLine();
   ```

   ```C++
   Thread::Sleep(3000);
   Console.WriteLine();
   ```

1. Nastavte zarážku na `Console.WriteLine();` řádku tak, že kliknete na levou stranu, nebo vyberete čáru a stisknete **F9**.

   Zarážka se zobrazuje jako červený kroužek v levém hřbetu vedle řádku kódu.

1. Vyberte **ladění**  >  **Spustit ladění** nebo stiskněte klávesu **F5**.

   Aplikace se spustí v režimu ladění a zastaví se na zarážce.

1. V režimu pozastavení otevřete okno **vlákna** výběrem možnosti **ladit**  >  **vlákna systému Windows**  >  . Chcete-li otevřít nebo zobrazit **vlákna** a další okna ladění, musíte být v relaci ladění.

## <a name="examine-thread-markers"></a>Kontrola značek vláken

1. Ve zdrojovém kódu vyhledejte `Console.WriteLine();` řádek.

   1. Klikněte pravým tlačítkem myši v okně **vlákna** a v nabídce vyberte možnost **Zobrazit vlákna ve zdroji** ![Zobrazit vlákna ve zdroji](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") .

   Hřbet vedle řádku zdrojového kódu nyní zobrazuje ![značku vlákna](../debugger/media/dbg-thread-marker.png "Značka vlákna") *ikony vlákna* . Značka vlákna označuje, že vlákno je v tomto umístění zastaveno. Pokud je v umístění více než jeden podproces zastavil, zobrazí se ikona ![více vláken](../debugger/media/dbg-multithreaded-show-threads.png "více vláken") .

1. Najeďte ukazatelem myši na značku vlákna. Zobrazí se DataTip se zobrazením názvu a ID vlákna pro zastavené vlákno nebo vlákna. Název vlákna může být `<No Name>` .

   >[!TIP]
   >Pro lepší identifikaci vláken Nameless je můžete přejmenovat v okně **vlákna** . Klikněte pravým tlačítkem na vlákno a vyberte **Přejmenovat**.

1. Kliknutím pravým tlačítkem na značku vlákna ve zdrojovém kódu zobrazíte dostupné možnosti v místní nabídce.

## <a name="flag-and-unflag-threads"></a>Označení a odstranění označení vlákna

Můžete označit vlákna, abyste udrželi přehled o vláknech, pro které chcete věnovat zvláštní pozornost.

Označte a odznačit vlákna z editoru zdrojového kódu nebo z okna **vlákna** . Vyberte, zda chcete zobrazit pouze vlákna označená příznakem nebo všechna vlákna, z panelu nástrojů **umístění ladění** nebo okna **vlákna** . Výběry provedené z libovolného umístění ovlivní všechna umístění.

### <a name="flag-and-unflag-threads-in-source-code"></a>Příznak a odoznačení vláken ve zdrojovém kódu

1. Otevřete panel nástrojů **umístění ladění** výběrem možnosti **Zobrazit**  >  **panely nástrojů**  >  **umístění ladění**. Můžete také kliknout pravým tlačítkem myši v oblasti panelu nástrojů a vybrat **umístění ladění**.

1. Panel nástrojů **umístění ladění** má tři pole: **proces**, **vlákno** a **blok zásobníku**. Vyřaďte seznam **vláken** a Všimněte si, kolik vláken existuje. V seznamu **vláken** je aktuálně spuštěné vlákno označeno **>** symbolem.

1. V okně zdrojový kód umístěte ukazatel myši na ikonu značky vlákna na hřbetu a vyberte ikonu příznaku (nebo jednu z ikon prázdný příznak) v DataTip. Ikona příznaku se změní na červenou.

   Můžete také kliknout pravým tlačítkem myši na ikonu značky vlákna, Ukázat na **příznak** a pak vybrat vlákno, které chcete označit z místní nabídky.

1. Na panelu nástrojů **umístění ladění** zaškrtněte ikonu **Zobrazit pouze vlákna označená příznakem** ![Zobrazit vlákna označená](../debugger/media/dbg-threads-show-flagged.png "Zobrazit vlákna označená příznakem")příznakem a napravo od pole **vlákna** . Ikona je zobrazena šedě, pokud není označeno jedno nebo více podprocesů.

   V rozevíracím seznamu **vlákna** na panelu nástrojů se nyní zobrazí pouze vlákno s příznakem. Chcete-li znovu zobrazit všechna vlákna, zaškrtněte ikonu **Zobrazit pouze vlákna označená příznakem** .

   >[!TIP]
   >Po označení některých vláken můžete umístit kurzor do editoru kódu, kliknout pravým tlačítkem myši a vybrat možnost **Spustit vlákna s příznakem na kurzoru**. Ujistěte se, že jste zvolili kód, který bude mít všechna vlákna s příznakem. **Spustit vlákna s příznakem pro kurzor** pozastaví vlákna na vybraném řádku kódu, což usnadňuje řízení pořadí spouštění pomocí [zmrazení a odmrazování vláken](#bkmk_freeze).

1. Chcete-li přepnout stav příznaku nebo bez příznaku v aktuálně zpracovávaném vlákně, vyberte možnost jediný příznak **Přepnout stav aktuálního vlákna** na panelu nástrojů, nalevo od tlačítka **Zobrazit pouze příznakovaná vlákna** . Označení aktuálního vlákna je užitečné pro vyhledání aktuálního vlákna, když jsou zobrazována pouze vlákna s příznakem.

1. Chcete-li zrušit označení vlákna, najeďte myší na značku vlákna ve zdrojovém kódu a výběrem ikony červeného příznaku ho zrušte, nebo klikněte pravým tlačítkem na značku vlákna a vyberte možnost zrušit **příznak**.

### <a name="flag-and-unflag-threads-in-the-threads-window"></a>Příznak a odoznačení vláken v okně vláken

V okně **vláken** mají vlákna s příznakem vedle sebe ikony červeného označení, zatímco vlákna bez příznaku, pokud jsou zobrazena, mají prázdné ikony.

![Okno vláken](../debugger/media/dbg-threads-window.png "Okno vláken")

Vyberte ikonu příznaku pro změnu stavu vlákna na příznak nebo bez příznaku v závislosti na jeho aktuálním stavu.

Můžete také kliknout pravým tlačítkem na řádek a vybrat **příznak**, zrušit **příznak** nebo zrušit **označení všech vláken** z místní nabídky.

Panel nástrojů okna **vlákna** má také tlačítko **Zobrazit pouze vlákna označená příznakem** , což je pravá jedna ze dvou ikon příznaků. Funguje stejně jako tlačítko na panelu nástrojů **umístění ladění** a buď tlačítko ovládá zobrazení v obou umístěních.

### <a name="other-threads-window-features"></a>Další funkce okna vlákna

V okně **vlákna** vyberte záhlaví libovolného sloupce a seřaďte vlákna podle daného sloupce. Opětovným výběrem znovu změňte pořadí řazení. Pokud se zobrazují všechna vlákna, výběr sloupce ikona příznaku seřadí vlákna podle stavu s příznakem nebo bez příznaku.

Druhý sloupec okna **vlákna** (bez záhlaví) je **aktuální sloupec vlákna** . Žlutá šipka v tomto sloupci označuje aktuální bod spuštění.

Sloupec **umístění** zobrazuje, kde se každé vlákno zobrazuje ve zdrojovém kódu. Vyberte šipku rozbalení vedle položky **umístění** nebo najeďte myší na položku a zobrazte pro toto vlákno částečný zásobník volání.

>[!TIP]
>Pro grafické zobrazení zásobníků volání pro vlákna použijte okno [paralelní zásobníky](../debugger/using-the-parallel-stacks-window.md) . Chcete-li otevřít okno, při ladění vyberte možnost **ladit** >    >  **paralelní zásobníky** systému Windows.

Kromě **příznaku**, **odznačit a** zrušit **označení všech vláken** má místní nabídka pro položky okna **vlákna** po kliknutí pravým tlačítkem myši:

- Tlačítko **Zobrazit vlákna ve zdroji**
- **Hexadecimální zobrazení**, které změní **ID vlákna** v okně **vlákna** z desítkového na šestnáctkového formátu.
- [Přepněte do vlákna](#switch-to-another-thread), které okamžitě přepne spuštění do tohoto vlákna.
- **Přejmenování**, které umožňuje změnit název vlákna.
- [Zablokování a rozmrazení](#bkmk_freeze) příkazů.

## <a name="freeze-and-thaw-thread-execution"></a><a name="bkmk_freeze"></a> Zablokovat a uvolnit provádění vlákna

Můžete blokovat a odblokovat nebo pozastavit a obnovit vlákna a řídit pořadí, ve kterém vlákna provádějí práci. Zamrznutí a rozmrazení vláken vám může pomáhat vyřešit problémy souběžnosti, jako jsou zablokování a konflikty časování.

> [!TIP]
> Chcete-li postupovat podle jednoho vlákna bez zmrazení jiných vláken, což je také běžný scénář ladění, přečtěte si téma Začínáme s [laděním vícevláknových aplikací](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).

**Chcete-li zablokovat a uvolnit vlákna:**

1. V okně **vlákna** klikněte pravým tlačítkem na libovolný podproces a pak vyberte **ukotvit**. Ikona **pozastavení** v aktuálním sloupci **vlákna** označuje, že je vlákno zmrazeno.

1. Vyberte **sloupce** na panelu nástrojů okna **vlákna** a pak vyberte **pozastavený počet** pro zobrazení sloupce **pozastavený počet** . Hodnota počet pozastavených vláken pro zmrazené vlákno je **1**.

1. Klikněte pravým tlačítkem na zmrazené vlákno a vyberte možnost **uvolnit**.

   Ikona **pozastavení** zmizí a hodnota **počet pozastavených** změn se změní na **0**.

## <a name="switch-to-another-thread"></a>Přepnout na jiné vlákno

Při pokusu o přepnutí na jiné vlákno se může zobrazit **aplikace v okně režimu přerušení** . V tomto okně se dozvíte, že vlákno neobsahuje žádný kód, který může zobrazit aktuální ladicí program. Můžete například ladit spravovaný kód, ale vlákno je nativní kód. Okno nabízí návrhy na vyřešení problému.

**Přepnutí na jiné vlákno:**

1. V okně **vlákna** si poznamenejte aktuální ID vlákna, což je vlákno se žlutou šipkou v **aktuálním sloupci vlákna** . Chcete-li pokračovat v aplikaci, přepněte zpět do tohoto vlákna.

1. Klikněte pravým tlačítkem myši na jiné vlákno a v místní nabídce vyberte možnost **Přepnout do vlákna** .

1. Všimněte si, že se v okně **vláken** změnila žlutá poloha šipky. Původní značka aktuálního vlákna také zůstává jako obrys.

   Podívejte se na popis značky vlákna v editoru zdrojového kódu a v rozevíracím seznamu **vlákna** na panelu nástrojů **umístění ladění** . Všimněte si, že se zde změnila i aktuální vlákno.

1. Na panelu nástrojů **umístění ladění** vyberte jiné vlákno ze seznamu **vláken** . Všimněte si, že aktuální vlákno se změní také v dalších dvou umístěních.

1. V editoru zdrojového kódu klikněte pravým tlačítkem myši na značku vlákna, přejděte na příkaz **Přepnout do vlákna** a v seznamu vyberte jiné vlákno. Pozor, aby se aktuální vlákno změnilo ve všech třech umístěních.

Se značkou vlákna ve zdrojovém kódu můžete přepínat pouze na vlákna, která jsou v tomto umístění zastavena. Pomocí okna **vlákna** a panelu nástrojů **umístění ladění** můžete přepnout do libovolného vlákna.

Nyní jste se naučili základy ladění aplikací s více vlákny. Můžete sledovat, označovat a odznačit a odblokovat a odblokovat vlákna pomocí okna **vlákna** , seznamu **vláken** na panelu nástrojů **umístění ladění** nebo značek vláken v editoru zdrojového kódu.

## <a name="see-also"></a>Viz také
- [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Postupy: Přepnutí na jiné vlákno během ladění](../debugger/how-to-switch-to-another-thread-while-debugging.md)
