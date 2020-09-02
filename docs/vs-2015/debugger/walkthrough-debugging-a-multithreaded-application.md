---
title: 'Návod: Ladění vícevláknové aplikace | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- multithreaded debugging, walkthrough
- walkthroughs, multithreaded debugging
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 33ce391523a256bcb195deccf0c14868b5eae707
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683082"
---
# <a name="walkthrough-debugging-a-multithreaded-application"></a>Návod: Ladění vícevláknové aplikace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] poskytuje vylepšené okno **vlákna** a další vylepšení uživatelského rozhraní, které usnadňuje Ladění vícevláknových aplikací. Tento názorný postup trvá jenom několik minut, ale po jeho dokončení se seznámí s novými funkcemi rozhraní pro ladění aplikací s více vlákny.  
  
 Chcete-li začít tento návod, budete potřebovat aplikační projekt s více vlákny. Chcete-li vytvořit projekt, postupujte podle kroků uvedených tady.  
  
#### <a name="to-create-the-walkthrough-project"></a>Vytvoření projektového návodu  
  
1. V nabídce **soubor** klikněte na příkaz **Nový** a potom na **projekt**.  
  
     Zobrazí se dialogové okno **Nový projekt**.  
  
2. V poli **typ projektu**s klikněte na požadovaný jazyk: **Visual Basic**, **Visual C#** nebo **Visual C++**.  
  
3. V poli **šablony** vyberte **Konzolová aplikace** nebo **Konzolová aplikace CLR**.  
  
4. Do pole **název** zadejte název MyThreadWalkthroughApp.  
  
5. Klikněte na **OK**.  
  
     Zobrazí se nový projekt konzoly. Po vytvoření projektu se zobrazí zdrojový soubor. V závislosti na zvoleném jazyce se může zdrojový soubor jmenovat Module1. vb, Program.cs nebo MyThreadWalkthroughApp. cpp.  
  
6. Odstraňte kód, který se zobrazí ve zdrojovém souboru, a nahraďte ho ukázkovým kódem, který se zobrazí v části vytvoření vlákna, v tématu vytváření [vláken a předávání dat v počátečním čase](https://msdn.microsoft.com/library/52b32222-e185-4f42-91a7-eaca65c0ab6d).  
  
7. V nabídce **File** (Soubor) klikněte na **Save All** (Uložit vše).  
  
#### <a name="to-begin-the-walkthrough"></a>Postup zahájení postupu  
  
- V okně zdroje vyhledejte následující kód:  
  
    ```vb  
    Thread.Sleep(3000)   
    Console.WriteLine(  
    ```  
  
```csharp  
Thread.Sleep(3000);  
Console.WriteLine();  
```  
  
```cpp  
Thread::Sleep(3000);  
Console.WriteLine();  
```  
  
#### <a name="to-start-debugging"></a>Spuštění ladění  
  
1. Klikněte pravým tlačítkem myši na `Console.WriteLine` příkaz, přejděte na **zarážku** a pak klikněte na **Vložit zarážku**.  
  
     Na hřbetu na levé straně okna zdroje se zobrazí červená koule. To znamená, že na toto umístění je nyní nastavená zarážka.  
  
2. V nabídce **Ladit** klikněte na **Spustit ladění**.  
  
     Spustí se ladění, vaše Konzolová aplikace se začne spouštět a pak se zastaví na zarážce.  
  
3. Pokud má okno konzolové aplikace v tuto chvíli fokus, klikněte v okně, aby se [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vrátil fokus na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
4. V okně zdroje Najděte řádek, který obsahuje následující kód:  
  
    ```vb  
    Thread.Sleep(5000)   
    ```  
  
```csharp  
Thread.Sleep(3000);  
```  
  
```cpp  
Thread::Sleep(3000);  
```  
  
1. 
  
#### <a name="to-discover-the-thread-marker"></a>Zjištění značky vlákna  
  
1. V okně **vlákna** klikněte pravým tlačítkem myši a pak klikněte na **Zobrazit vlákna ve zdroji**.  
  
2. Podívejte se na hřbet na levé straně okna. Na tomto řádku se zobrazí ikona, která se podobá dvěma vláknům látky. Jedno vlákno je červené a druhý je modré. Značka vlákna označuje, že vlákno je v tomto umístění zastaveno. Je možné, že je vlákno v tomto umístění zastaveno.  
  
3. Najeďte ukazatelem myši na značku vlákna. DataTip, který se zobrazí. DataTip oznamuje název a ID vlákna pro každé zastavené vlákno. V tomto případě existuje pouze jedno vlákno, jehož název je pravděpodobně `<noname>` .  
  
4. Klikněte pravým tlačítkem na značku vlákna. Všimněte si možností v místní nabídce.  
  
   Tato ikona je *značka vlákna*:  
  
   ![Značka vlákna](../debugger/media/threadmarker.gif "ThreadMarker")  
  
## <a name="flagging-and-unflagging-threads"></a>Příznakování a odoznačování vláken  
 V nástroji [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] můžete označit vlákna, kterým chcete věnovat zvláštní pozornost. Označení vláken je dobrým způsobem, jak udržet přehled o důležitých vláknech a ignorovat vlákna, o kterých nezáleží.  
  
#### <a name="to-flag-threads"></a>Označení vláken  
  
1. V nabídce **zobrazení** přejděte na **panely nástrojů**.  
  
     Ujistěte se, že je vybraná možnost panel nástrojů **umístění ladění** .  
  
2. Přejděte na panel nástrojů **umístění ladění** a klikněte na seznam **vláken** .  
  
    > [!NOTE]
    > Tento panel nástrojů můžete rozpoznat třemi výraznými seznamy: **proces**, **vlákno**a **blok zásobníku**.  
  
3. Všimněte si, kolik vláken se v seznamu zobrazuje.  
  
4. Vraťte se do zdrojového okna a znovu klikněte na značku **vlákna** .  
  
5. V místní nabídce ukažte na **příznak**a pak klikněte na název vlákna a číslo ID.  
  
6. Vraťte se na panel nástrojů **umístění ladění** a znovu klikněte na seznam **vláken** .  
  
     V seznamu se teď zobrazí jenom vlákno s příznakem. Tlačítko příznaku, které je pouze napravo od seznamu **vláken** . Ikona příznaku na tlačítku byla předtím ztlumená. Teď je to plná, jasně červená.  
  
7. Najeďte ukazatelem myši na ikonu příznaku.  
  
     Zobrazí se automaticky otevírané okno. Tento automaticky otevírané okno informuje o tom, v jakém režimu je seznam **vláken** : **Zobrazit pouze vlákna označená příznakem**.  
  
8. Kliknutím na tlačítko příznak přepnete zpět, aby se **zobrazil celý režim vláken** .  
  
9. Znovu klikněte na seznam **vláken** a ověřte, že teď můžete zobrazit všechna vlákna znovu.  
  
10. Kliknutím na tlačítko příznak přepnete zpět, aby se **zobrazila pouze vlákna označená příznakem**.  
  
11. V nabídce **ladění** přejděte na **okna** a potom klikněte na **vlákna**.  
  
     Zobrazí se okno **vlákna** . K jednomu vláknu je připojená ikona příznaku.  
  
12. V okně zdroje klikněte znovu pravým tlačítkem na značku vlákna.  
  
     Všimněte si, jaké možnosti jsou nyní k dispozici v místní nabídce. Místo **příznaku**se teď zobrazuje **příznak**odznačit. Neklepejte na zrušit **označení**.  
  
13. Pokračujte dalším postupem, jak zrušit označení vláken.  
  
#### <a name="to-unflag-threads"></a>Chcete-li zrušit označení vláken  
  
1. V okně **vlákna** klikněte pravým tlačítkem myši na řádek odpovídající vláknu s příznakem.  
  
     Zobrazí se místní nabídka. Má možnost zrušit **označení** a odznačit **vše**.  
  
2. Chcete-li zrušit označení vlákna, klikněte na tlačítko zrušit **příznak**.  
  
3. Klikněte na ikonu červeného příznaku.  
  
4. Znovu se podívejte na panel nástrojů **umístění ladění** . Tlačítko příznak je znovu ztlumené. Neoznačili jste pouze označené vlákno. Vzhledem k tomu, že nejsou žádná vlákna označená příznakem, panel nástrojů se vrátí k **zobrazení všech režimů vláken** . Klikněte na seznam **vláken** a ověřte, zda vidíte všechna vlákna.  
  
5. Vraťte se do okna **vlákna** a Projděte si sloupce s informacemi.  
  
     V horní části každého sloupce má většina tlačítek názvy, které identifikují sloupec. První sloupec nalevo ale nemá žádný název. Místo toho má ikonu, což je obrys příznaku. Všimněte si, že se v každém řádku seznamu vláken objeví stejný obrys. Osnova znamená, že vlákno není označeno příznakem.  
  
6. Klikněte na osnovu příznaků pro dvě vlákna, druhý a třetí z dolní části seznamu.  
  
     Ikony příznaků se stanou plnou červenou barvou místo prázdných osnov.  
  
7. Klikněte na tlačítko v horní části sloupce příznak.  
  
     Pořadí seznamu vláken se po kliknutí na tlačítko změnilo. Seznam vláken je nyní seřazen s vlákny označenými příznakem nahoře.  
  
8. Znovu klikněte na tlačítko v horní části sloupce příznak.  
  
     Pořadí řazení se znovu změnilo.  
  
## <a name="more-about-the-threads-window"></a>Další informace o okně vláken  
  
#### <a name="to-learn-more-about-the-threads-window"></a>Další informace o okně vláken  
  
1. V okně **vlákna** prověřte třetí sloupec zleva. Tlačítko v horní části tohoto sloupce říká **ID**.  
  
2. Klikněte na tlačítko **ID**.  
  
     Seznam vláken je nyní seřazen podle čísla ID vlákna.  
  
3. V seznamu klikněte pravým tlačítkem myši na jakékoli vlákno. V místní nabídce klikněte na **hexadecimální zobrazení**.  
  
     Formát čísel ID vlákna se změnil.  
  
4. Najeďte ukazatelem myši na libovolné vlákno v seznamu.  
  
     Po chvilkovém zpoždění se zobrazí DataTip. Zobrazuje částečný zásobník volání pro vlákno.  
  
5. Podívejte se do čtvrtého sloupce zleva, který je označený jako **kategorie**. Vlákna jsou klasifikována do kategorií.  
  
     Prvním vláknem vytvořeným v procesu je označováno jako hlavní vlákno. Vyhledejte ji v seznamu vláken.  
  
6. Klikněte pravým tlačítkem myši na hlavní vlákno a potom klikněte na tlačítko **Přepnout do vlákna**.  
  
     Zobrazí se dialogové okno s upozorněním. Oznamuje vám, že [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nemůže zobrazit zdrojový kód pro hlavní vlákno.  
  
     Klikněte na **OK**.  
  
7. Podívejte se na okno **zásobník volání** a panel nástrojů **umístění ladění** .  
  
     Obsah okna **zásobník volání** se změnil.  
  
## <a name="switching-the-active-thread"></a>Přepínání aktivního vlákna  
  
#### <a name="to-switch-threads"></a>Přepnutí vláken  
  
1. V okně **vlákna** prověřte druhý sloupec zleva. Tlačítko v horní části tohoto sloupce nemá žádný text nebo ikonu. Tento sloupec je sloupcem **aktivního vlákna** .  
  
2. Podívejte se na sloupec **aktivního vlákna** a Všimněte si, že jeden podproces má žlutou šipku. Toto je *indikátor aktivního vlákna*.  
  
3. Poznamenejte si číslo ID vlákna, kde se nachází indikátor aktivního vlákna. Ukazatel aktivního vlákna přesunete do jiného vlákna, ale po dokončení ho budete muset vrátit zpátky.  
  
4. Klikněte pravým tlačítkem na jiné vlákno a pak klikněte na **Přepnout do vlákna**.  
  
5. Podívejte se na okno **zásobník volání** v okně zdroje. Změnil se obsah.  
  
6. Podívejte se na panel nástrojů **umístění ladění** . Aktivní vlákno bylo také změněno.  
  
7. Přejít na panel nástrojů **umístění ladění** . Klikněte na pole **vlákna** a v rozevíracím seznamu vyberte jiné vlákno.  
  
8. Podívejte se na okno **vlákna** . Indikátor aktivního vlákna se změnil.  
  
9. V okně zdroje klikněte pravým tlačítkem myši na značku vlákna. V místní nabídce přejděte na **přepínač** a klikněte na název nebo ID vlákna.  
  
     Nyní jste viděli tři způsoby, jak změnit aktivní vlákno: pomocí okna **vlákna** , pole **vlákno** na panelu nástrojů **umístění ladění** a indikátor vlákna v okně zdroje.  
  
     Pomocí indikátoru vlákna lze přepínat pouze na vlákna, která jsou zastavena v daném umístění. Pomocí okna **vlákna** a panelu nástrojů **umístění ladění** můžete přepnout do libovolného vlákna.  
  
## <a name="freezing-and-thawing-thread-execution"></a>Zamrznutí a rozmrazit provádění vlákna  
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Zablokování a uvolnění vláken  
  
1. V okně **vlákna** klikněte pravým tlačítkem na libovolný podproces a pak klikněte na **ukotvit**.  
  
2. Podívejte se na sloupec aktivního vlákna. Zde se zobrazí dvojice svislých pruhů. Tyto dva modré pruhy označují, že je vlákno zmrazeno.  
  
3. Podívejte se na sloupec **Suspend (pozastavit** ). Počet pozastavení pro vlákno je nyní 1.  
  
4. Klikněte pravým tlačítkem na zmrazené vlákno a pak klikněte na **uvolnit**.  
  
     Sloupec aktivního vlákna a změna sloupce **pozastavení** .  
  
## <a name="see-also"></a>Viz také  
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Postupy: přepnutí na jiné vlákno během ladění](../debugger/how-to-switch-to-another-thread-while-debugging.md)
