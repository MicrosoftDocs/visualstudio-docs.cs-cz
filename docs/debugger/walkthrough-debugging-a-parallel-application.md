---
title: Ladění paralelní aplikace | Microsoft Docs
description: Ladění pomocí oken Paralelní úlohy a paralelní zásobníky v sadě Visual Studio
ms.date: 02/14/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks walkthrough
- parallel stacks toolwindow
- parallel tasks toolwindow
- parallel applications, debugging [C++]
- debugging, parallel applications
- parallel applications, debugging [Visual Basic]
- parallel applications, debugging [C#]
ms.assetid: 2820ac4c-c893-4d87-8c62-83981d561493
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84d43ede5fcca1ae76d155cb8799a61900926d7b
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183844"
---
# <a name="walkthrough-debugging-a-parallel-application-in-visual-studio-c-visual-basic-c"></a>Návod: ladění paralelní aplikace v aplikaci Visual Studio (C#, Visual Basic, C++)

Tento návod ukazuje, jak použít **Paralelní úlohy** a okna **paralelních zásobníků** k ladění paralelní aplikace. Tato okna vám pomůžou pochopit a ověřit chování kódu, který používá [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) nebo [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime). Tento návod obsahuje vzorový kód, který obsahuje předdefinované zarážky. Po zalomení kódu návod ukazuje, jak použít **Paralelní úlohy** a okna **paralelní zásobníky** k její kontrole.

 Tento návod učí tyto úlohy:

- Jak zobrazit zásobníky volání všech vláken v jednom zobrazení.

- Jak zobrazit seznam `System.Threading.Tasks.Task` instancí, které jsou vytvořeny ve vaší aplikaci.

- Jak zobrazit skutečné zásobníky volání úkolů místo vláken.

- Jak přejít na kód z okna **Paralelní úlohy** a **paralelní zásobníky**

- Způsob, jakým se Windows vypořádat se škálováním prostřednictvím seskupení, lupy a dalších souvisejících funkcí.

## <a name="prerequisites"></a>Požadavky
 Tento návod předpokládá, že je povolený **pouze můj kód** (ve výchozím nastavení je povolený v novějších verzích sady Visual Studio). V nabídce **nástroje** klikněte na položku **Možnosti**, rozbalte uzel **ladění** , vyberte možnost **Obecné**a poté vyberte možnost **Povolit pouze můj kód (pouze spravované)**. Pokud tuto funkci nenastavíte, můžete i nadále používat tento návod, ale výsledky se mohou lišit od ilustrací.

## <a name="c-sample"></a>Ukázka jazyka C#
 Použijete-li ukázku jazyka C#, tento návod také předpokládá, že je externí kód skrytý. Chcete-li přepnout, zda je zobrazen externí kód, klikněte pravým tlačítkem **myši na záhlaví tabulky v** okně **zásobník volání** a potom vyberte nebo zrušte zaškrtnutí **Zobrazit externí kód**. Pokud tuto funkci nenastavíte, můžete i nadále používat tento návod, ale výsledky se mohou lišit od ilustrací.

## <a name="c-sample"></a>Ukázka C++
 Použijete-li ukázku jazyka C++, můžete ignorovat odkazy na externí kód v tomto tématu. Externí kód se vztahuje pouze na ukázku C#.

## <a name="illustrations"></a>Ilustrace
 Ilustrace v tomto tématu zaznamenané na čtyřjádrovém počítači, na kterém je spuštěná ukázka jazyka C# I když můžete použít jiné konfigurace k dokončení tohoto Názorného postupu, ilustrace se mohou lišit od toho, co se zobrazuje v počítači.

## <a name="creating-the-sample-project"></a>Vytvoření ukázkového projektu
 Vzorový kód v tomto návodu je určen pro aplikaci, která nic nedělá. Cílem je pouze pochopit, jak používat okna nástrojů k ladění paralelní aplikace.

#### <a name="to-create-the-sample-project"></a>Vytvoření ukázkového projektu

1. Otevřete Visual Studio a vytvořte nový projekt.

   ::: moniker range=">=vs-2019"

   Pokud okno Start není otevřeno, klikněte **na tlačítko** > **Start okna**.

   V okně Start vyberte možnost **vytvořit nový projekt**.

   V okně **vytvořit nový projekt** zadejte do vyhledávacího pole nebo zadejte *Console* . Dále v seznamu jazyk vyberte **C#**, **C++** nebo **Visual Basic** a v seznamu platforma zvolte **Windows** . 

   Po použití filtrů jazyků a platforem zvolte **Konzolová aplikace (.NET Core)** nebo, pro C++, šablonu **Konzolová aplikace** a klikněte na tlačítko **Další**.

   > [!NOTE]
   > Pokud nevidíte správnou šablonu, přejděte do části **nástroje**  >  **získat nástroje a funkce...**, které otevře instalační program pro Visual Studio. Zvolte možnost vývoj **desktopových** aplikací pro .NET nebo **desktopové vývojové prostředí pomocí C++** a pak zvolte **Upravit**.

   V okně **Konfigurovat nový projekt** zadejte název nebo použijte výchozí název v poli **název projektu** . Pak zvolte **vytvořit**.

   ::: moniker-end
   ::: moniker range="vs-2017"
   V horním řádku nabídek vyberte **soubor**  >  **Nový**  >  **projekt**. V levém podokně dialogového okna **Nový projekt** vyberte následující:

   - V případě aplikace v jazyce C# v části **Visual C#** zvolte možnost **plocha systému Windows**a potom v prostředním podokně zvolte možnost **aplikace konzoly (.NET Framework)**.
   - V případě aplikace Visual Basic vyberte v části **Visual Basic**možnost **plocha Windows**a potom v prostředním podokně zvolte **Konzolová aplikace (.NET Framework)**.
   - V aplikaci C++ klikněte v části **Visual C++** na **plocha Windows**, a pak zvolte **Konzolová aplikace Windows**.

   Pokud se nezobrazuje **Konzolová aplikace (.NET Core)** nebo, pro C++, šablona projektu **Konzolová aplikace** , přejděte do části **nástroje**  >  **získat nástroje a funkce...**, které otevře instalační program pro Visual Studio. Zvolte možnost vývoj **desktopových** aplikací pro .NET nebo **desktopové vývojové prostředí pomocí C++** a pak zvolte **Upravit**.

   Pak zadejte název nebo použijte výchozí název a klikněte na **OK**.

   Vyberte **OK**.
   ::: moniker-end

   Zobrazí se nový projekt konzoly. Po vytvoření projektu se zobrazí zdrojový soubor.

1. Otevřete v projektu soubor kódu. cpp,. cs nebo. vb. Odstraňte jeho obsah a vytvořte prázdný soubor kódu.

1. Vložte následující kód pro zvolený jazyk do prázdného souboru kódu.

   [!code-csharp[Debugger#1](../debugger/codesnippet/CSharp/walkthrough-debugging-a-parallel-application_1.cs)]
   [!code-cpp[Debugger#1](../debugger/codesnippet/CPP/walkthrough-debugging-a-parallel-application_1.cpp)]
   [!code-vb[Debugger#1](../debugger/codesnippet/VisualBasic/walkthrough-debugging-a-parallel-application_1.vb)]

1. V nabídce **soubor** klikněte na **Uložit vše**.

1. V nabídce **sestavení** klikněte na příkaz **znovu sestavit řešení**.

    Všimněte si, že jsou k dispozici čtyři volání `Debugger.Break` ( `DebugBreak` v ukázce jazyka C++), proto není nutné vkládat zarážky; pouhá spuštění aplikace způsobí přerušení v ladicím programu až čtyřikrát.

## <a name="using-the-parallel-stacks-window-threads-view"></a>Použití okna Paralelní zásobníky: zobrazení vláken
 V nabídce **Ladit** klikněte na **Spustit ladění**. Počkejte, než se dorazí na první zarážku.

#### <a name="to-view-the-call-stack-of-a-single-thread"></a>Zobrazení zásobníku volání jednoho vlákna

1. V nabídce **ladění** přejděte na **okna** a potom klikněte na **vlákna**. Ukotvěte okno **vlákna** v dolní části sady Visual Studio.

2. V nabídce **ladění** přejděte na **okna** a potom klikněte na **zásobník volání**. Ukotvěte okno **zásobník volání** v dolní části sady Visual Studio.

3. Dvakrát klikněte na vlákno v okně **vlákna** , čímž se nastaví jako aktuální. Aktuální vlákna mají žlutou šipku. Když změníte aktuální vlákno, jeho zásobník volání se zobrazí v okně **zásobník volání** .

#### <a name="to-examine-the-parallel-stacks-window"></a>Kontrola okna Paralelní zásobníky

1. V nabídce **ladění** přejděte na **okna** a potom klikněte na **paralelní zásobníky**. Ujistěte se, že je v poli v levém horním rohu vybraná možnost **vlákna** .

     Pomocí okna **paralelní zásobníky** můžete zobrazit více zásobníků volání současně v jednom zobrazení. Následující ilustrace znázorňuje okno **paralelní zásobníky** nad oknem **zásobník volání** .

     ![Zobrazení vláken v okně paralelní zásobníky](../debugger/media/pdb_walkthrough_1.png "PDB_Walkthrough_1")

     Zásobník volání hlavního vlákna se zobrazí v jednom poli a zásobníky volání pro ostatní čtyři vlákna jsou seskupeny v jiném poli. Čtyři vlákna jsou seskupena dohromady, protože jejich rámce zásobníku sdílí stejné kontexty metod; To znamená, že jsou stejné metody: `A` , `B` a `C` . Chcete-li zobrazit ID a názvy vláken, která sdílejí stejné pole, umístěte ukazatel myši na pole s hlavičkou (**4 vlákna**). Aktuální vlákno je zobrazeno tučně.

     ![Popis, který zobrazuje ID a názvy vláken](../debugger/media/pdb_walkthrough_1a.png "PDB_Walkthrough_1A")

     Žlutá šipka označuje aktivní rámec zásobníku aktuálního vlákna.

     Kliknutím pravým tlačítkem myši v okně **zásobník volání** můžete nastavit, kolik podrobností se má zobrazit pro rámce zásobníku (**názvy modulů**, **typy parametrů**, **názvy parametrů**, **hodnoty parametrů**, **čísla řádků** a **posun bajtů**).

     Modrý zvýraznění kolem pole indikuje, že aktuální vlákno je součástí tohoto pole. Aktuální vlákno je také vyznačeno tučným rámcem zásobníku v popisku. Pokud dvakrát kliknete na hlavní vlákno v okně vlákna, můžete si všimnout, že modrý zvýraznění v okně **paralelní zásobníky** se odpovídajícím způsobem přesune.

     ![Zvýrazněné hlavní vlákno v okně paralelní zásobníky](../debugger/media/pdb_walkthrough_1c.png "PDB_Walkthrough_1C")

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Pokračování v provádění až do druhé zarážky

1. Chcete-li pokračovat v provádění, dokud nebude dosaženo druhé zarážce, v nabídce **ladění** klikněte na tlačítko **pokračovat**. Následující ilustrace znázorňuje strom vláken ve druhé zarážce.

     ![Okno paralelní zásobníky zobrazující mnoho větví](../debugger/media/pdb_walkthrough_2.png "PDB_Walkthrough_2")

     Na první zarážce byly čtyři vlákna z S. A až S. B až S. C. Tyto informace jsou stále viditelné v okně **paralelní zásobníky** , ale v těchto čtyřech vláknech probíhalo další postup. Jedna z nich pokračovala S. D a pak S.E. Asia Další pokračování na S. F, S. G a S.H. Dva ostatní pokračuje na S. I a S. J a z jednoho z nich se dostali na S. K a druhý neuživatelský externí kód.

     Můžete umístit ukazatel myši na záhlaví pole, například **1 vlákno** nebo **2 vlákna**, a zobrazit tak ID vláken vláken. Můžete umístit ukazatel myši na snímky zásobníku a zobrazit ID vláken a další podrobnosti o snímku. Modrý zvýraznění indikuje aktuální vlákno a žlutá šipka označuje aktivní rámec zásobníku aktuálního vlákna.

     Ikona tkanin – vlákna (proložené čáry) označují aktivní rámce zásobníku neaktuálních vláken. V okně **zásobník volání** poklikejte na y. B pro přepínání snímků. Okno **paralelní zásobníky** indikuje aktuální rámec zásobníku aktuálního vlákna pomocí ikony šipky zeleného zahnutého okna.

     V okně **vlákna** přepínejte mezi vlákny a sledujte, že zobrazení v okně **paralelní zásobníky** je aktualizováno.

     Pomocí místní nabídky v okně **paralelní zásobníky** můžete přepnout do jiného vlákna nebo do jiného rámce jiného vlákna. Například klikněte pravým tlačítkem S. J, přejděte na **Přepnout na rámec**a potom klikněte na příkaz.

     ![Cesta k paralelním zásobníkům pro spuštění](../debugger/media/pdb_walkthrough_2b.png "PDB_Walkthrough_2B")

     Klikněte pravým tlačítkem myši na možnost S. C a přejděte na možnost **Přepnout na rámec**. Jeden z příkazů má značku zaškrtnutí, která označuje rámec zásobníku aktuálního vlákna. Můžete přepnout na tento snímek stejného vlákna (pouze zelená šipka se přesune) nebo můžete přepnout do jiného vlákna (modré zvýraznění se také přesune). Následující ilustrace znázorňuje podnabídku.

     ![Nabídka zásobníků se dvěma možnostmi v C, zatímco J je aktuální.](../debugger/media/pdb_walkthrough_3.png "PDB_Walkthrough_3")

     Když je kontext metody spojen s pouze jedním snímkem zásobníku, zobrazí záhlaví pole **1 vlákno** a můžete na něj přejít dvojitým kliknutím. Pokud dvakrát kliknete na kontext metody, ke kterému je přidruženo více než 1 rámec, nabídka se automaticky otevře. Při najetí myší na kontexty metod si všimněte černého trojúhelníku vpravo. Kliknutím na tento trojúhelník se zobrazí také místní nabídka.

     U rozsáhlých aplikací, které mají mnoho vláken, můžete chtít soustředit se jenom na podmnožinu vláken. Okno **paralelní zásobníky** může zobrazit zásobníky volání pouze pro vlákna označená příznakem. Chcete-li označit vlákna, použijte místní nabídku nebo první buňku vlákna.

     Na panelu nástrojů klikněte na tlačítko **Zobrazit pouze označené příznakem** vedle rozevíracího seznamu.

     ![Okno paralelní zásobníky a popis tlačítka](../debugger/media/pdb_walkthrough_3a.png "PDB_Walkthrough_3A")

     Nyní se v okně **paralelní zásobníky** zobrazí pouze vlákno s příznakem.

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Chcete-li pokračovat v provádění až po třetí zarážku

1. Chcete-li pokračovat v provádění, dokud nebude dosaženo třetí zarážce, v nabídce **ladění** klikněte na tlačítko **pokračovat**.

     Pokud je více vláken ve stejné metodě, ale metoda nebyla na začátku zásobníku volání, metoda se zobrazí v různých polích. Příklad v aktuální zarážce je S. L, který má tři vlákna v něm a je zobrazen ve třech polích. Dvakrát klikněte na S.L.

     ![Cesta spuštění v okně paralelní zásobníky](../debugger/media/pdb_walkthrough_3b.png "PDB_Walkthrough_3B")

     Všimněte si, že S. L je tučné v dalších dvou polích tučné, abyste viděli, kde se nachází jinde. Pokud chcete zjistit, které snímky volají do S. L a které rámce volá, klikněte na tlačítko **zobrazení přepínací metody** na panelu nástrojů. Následující ilustrace znázorňuje zobrazení metody okna **paralelní zásobníky** .

     ![Zobrazení metody v okně paralelních zásobníků](../debugger/media/pdb_walkthrough_4.png "PDW_Walkthrough_4")

     Všimněte si, jak se diagram na vybrané metodě pivotoval a umístí ho do vlastního pole uprostřed zobrazení. Volané a volající se zobrazí v horní a dolní části. Pokud chcete tento režim opustit, klikněte znovu na tlačítko **zobrazení metody přepínání** .

     Místní nabídka okna **paralelní zásobníky** má také následující další položky.

    - **Hexadecimální zobrazení** přepíná čísla v popisech mezi desítkovými a šestnáctkovými hodnotami.

    - **Nastavení symbolů** otevře příslušná dialogová okna.

    - **Zobrazit vlákna ve zdroji** Přepíná zobrazení značek vláken ve zdrojovém kódu, který ukazuje umístění vláken ve zdrojovém kódu.

    - **Zobrazit externí kód** zobrazí všechny snímky i v případě, že nejsou v uživatelském kódu. Zkuste zobrazit, aby se diagram rozšířil na další snímky (což může být nedostupné, protože pro ně nemáte symboly).

2. V okně **paralelní zásobníky** se ujistěte, že je na panelu nástrojů zapnuto tlačítko **automaticky přejít na aktuální rámec zásobníku** .

     Pokud máte velké diagramy a máte krok na další zarážku, můžete chtít zobrazení automaticky přejít na aktivní rámec zásobníku aktuálního vlákna; To znamená, že vlákno, které dosáhlo zarážky jako první.

3. Než budete pokračovat, v okně **paralelní zásobníky** se posuňte všem směrem doleva a dolů.

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Pokračování v provádění až do čtvrté zarážky

1. Chcete-li pokračovat v provádění, dokud není dosaženo čtvrté zarážky, v nabídce **ladění** klikněte na tlačítko **pokračovat**.

     Všimněte si, jak se zobrazení automaticky posouvá na místo. Přepněte vlákna v okně **vlákna** nebo přepněte rámce zásobníku v okně **zásobník volání** a Všimněte si, jak se zobrazení vždy automaticky posouvá na správný rámeček. Vypne **automatické posouvání na aktuální možnost snímku nástroje** a zobrazí rozdíl.

     **Pohled na pohled z ptačí perspektivy** také pomáhá s velkými diagramy v okně **paralelní zásobníky** . Ve výchozím nastavení se **zobrazuje pohled na oči** . Můžete ho ale přepínat kliknutím na tlačítko mezi posuvníky v pravém dolním rohu okna, jak je znázorněno na následujícím obrázku.

     ![Zobrazení perspektivy&#45;v okně paralelní zásobníky](../debugger/media/pdb_walkthrough_5.png "PDB_Walkthrough_5")

     V zobrazení Perspektiva pro ptáky můžete obdélník přesunout, abyste ho mohli rychle posunout okolo diagramu.

     Dalším způsobem, jak diagram přesunout v libovolném směru, je kliknout na prázdnou oblast diagramu a přetáhnout ho tam, kde chcete.

     Chcete-li přiblížit nebo oddálit diagram, stiskněte a podržte klávesu CTRL při přesunu kolečka myši. Případně klikněte na tlačítko přiblížení na panelu nástrojů a pak použijte nástroj Lupa.

     Můžete také zobrazit zásobníky v horním směrem dolů, a to tak, že kliknete na nabídku **nástroje** , kliknete na možnost **Možnosti**a pak vyberete nebo zrušíte zaškrtnutí políčka v uzlu **ladění** .

2. Než budete pokračovat, v nabídce **ladění** klikněte na **Zastavit ladění** a ukončete provádění.

## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>Použití okna Paralelní úlohy a zobrazení úlohy okna Paralelní zásobníky
 Doporučujeme, abyste před pokračováním dokončili předchozí postupy.

#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>Restartování aplikace, dokud nebude dosaženo první zarážce

1. V nabídce **ladění** klikněte na **Spustit ladění** a počkejte, než se dorazí na první zarážku.

2. V nabídce **ladění** přejděte na **okna** a potom klikněte na **vlákna**. Ukotvěte okno **vlákna** v dolní části sady Visual Studio.

3. V nabídce **ladění** přejděte na **Windows** a klikněte na **zásobník volání**. Ukotvěte okno **zásobník volání** v dolní části sady Visual Studio.

4. Dvakrát klikněte na vlákno v okně **vlákna** , čímž se nastaví jako aktuální. Aktuální vlákna mají žlutou šipku. Když změníte aktuální vlákno, ostatní okna budou aktualizována. V dalším kroku prověříme úlohy.

5. V nabídce **ladění** vyberte možnost **Windows**a potom klikněte na položku **úlohy**. Následující obrázek znázorňuje okno **úlohy** .

     ![Čtyři spuštěné úlohy v okně úlohy](../debugger/media/pdb_walkthrough_6.png "PDW_Walkthrough_6")

     Pro každou spuštěnou úlohu si můžete přečíst jeho ID, které je vráceno se stejnou pojmenovanou vlastností, ID a název vlákna, ve kterém je spuštěno, jeho umístění (když je ukazatel myši nad, zobrazí se popis, který obsahuje celý zásobník volání). V rámci sloupce **úlohy** také můžete zobrazit metodu, která byla předána do úlohy. Jinými slovy, počátečním bodem.

     Můžete řadit libovolný sloupec. Všimněte si glyfu řazení, který označuje sloupec a směr řazení. Sloupce můžete také změnit jejich přetažením doleva nebo doprava.

     Žlutá šipka indikuje aktuální úlohu. Úkoly můžete přepínat dvojitým kliknutím na úlohu nebo pomocí místní nabídky. Když přepnete úkoly, podkladové vlákno bude aktuální a ostatní okna budou aktualizována.

     Při ručním přepnutí z jednoho úkolu na druhý se žlutá šipka přesune, ale bílá šipka stále zobrazuje úlohu, která způsobila přerušení ladicího programu.

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Pokračování v provádění až do druhé zarážky

1. Chcete-li pokračovat v provádění, dokud nebude dosaženo druhé zarážce, v nabídce **ladění** klikněte na tlačítko **pokračovat**.

     Dříve se ve sloupci **stav** zobrazily všechny úkoly jako aktivní, ale teď se zablokují dva z těchto úloh. Úlohy je možné zablokovat z mnoha různých důvodů. Ve sloupci **stav** najeďte myší na čekající úlohu a zjistěte, proč je zablokovaná. Například na následujícím obrázku úloha 3 čeká na úlohu 4.

     ![Dvě čekající úlohy v okně úlohy](../debugger/media/pdb_walkthrough_7.png "PDB_Walkthrough_7")

     Úloha 4 pak čeká na monitorování, které vlastní vlákno přiřazené k úloze 2. (Klikněte pravým tlačítkem na řádek záhlaví a vyberte **sloupce**  >  . **Přiřazení vlákna** pro zobrazení hodnoty přiřazení vlákna pro úlohu 2).

     ![Úloha a popisek čekání v okně úlohy](../debugger/media/pdb_walkthrough_7a.png "PDB_Walkthrough_7A")

     Úkol můžete označit kliknutím na příznak v prvním sloupci okna **úlohy** .

     Pomocí příznaku můžete sledovat úlohy mezi různými zarážkami ve stejné relaci ladění nebo filtrovat úkoly, jejichž zásobníky volání se zobrazují v okně **paralelní zásobníky** .

     Při předchozím použití okna **paralelní zásobníky** jste zobrazili vlákna aplikace. Zobrazte okno **paralelní zásobníky** znovu, ale tentokrát se zobrazí úlohy aplikace. Provedete to tak, že vyberete **úkoly** v poli vlevo nahoře. Na následujícím obrázku je znázorněno zobrazení úkolů.

     ![Zobrazení úlohy v okně paralelní zásobníky](../debugger/media/pdb_walkthrough_8.png "PDB_Walkthrough_8")

     Vlákna, která aktuálně nespouštějí úlohy, se nezobrazí v zobrazení úlohy okna **paralelní zásobníky** . V případě vláken, která spouštějí úkoly, jsou také z horního a dolního zásobníku filtrovány některé rámce zásobníku, které nejsou relevantní pro úlohy.

     Znovu zobrazte okno **úlohy** . Kliknutím pravým tlačítkem myši na záhlaví kteréhokoli sloupce zobrazíte místní nabídku pro daný sloupec.

     Pomocí místní nabídky můžete přidat nebo odebrat sloupce. Například není vybrán sloupec AppDomain. Proto se v seznamu nezobrazí. Klikněte na **Nadřazená položka**. **Nadřazený** sloupec se zobrazí bez hodnot pro žádnou ze čtyř úkolů.

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Chcete-li pokračovat v provádění až po třetí zarážku

1. Chcete-li pokračovat v provádění, dokud nebude dosaženo třetí zarážce, v nabídce **ladění** klikněte na tlačítko **pokračovat**.

     Nová úloha, úloha 5, je teď spuštěná a úloha 4 teď čeká. Můžete se podívat, proč na čekající úkol ve **stavovém** okně najede myší. V **nadřazeném** sloupci si všimněte, že úloha 4 představuje nadřazený úkol 5.

     Chcete-li lépe vizualizovat vztah nadřazený-podřízený, klikněte pravým tlačítkem myši na řádek záhlaví sloupce a poté klikněte na položku **nadřazené podřízené zobrazení**. Měl by se zobrazit následující obrázek.

     ![Nadřazené zobrazení podřízené&#45;v okně úlohy](../debugger/media/pdb_walkthrough_9.png "PDB_Walkthrough_9")

     Všimněte si, že úloha 4 a úloha 5 jsou spuštěny ve stejném vlákně (zobrazení sloupce **přiřazení vlákna** , je-li skrytý). Tyto informace nejsou zobrazeny v okně **vlákna** . Podívejte se, že se jedná o další výhody okna **úlohy** . Potvrďte to tak, že zobrazíte okno **paralelní zásobníky** . Ujistěte se, že prohlížíte **úkoly**. Vyhledejte úkoly 4 a 5 dvojitým kliknutím na ně v okně **úlohy** . V takovém případě se modrý zvýraznění v okně **paralelní zásobníky** aktualizuje. Můžete také vyhledat úlohy 4 a 5 kontrolou tlačítek v okně **paralelní zásobníky** .

     ![Zobrazení úloh v paralelních zásobnících okna](../debugger/media/pdb_walkthrough_9a.png "PDB_Walkthrough_9A")

     V okně **paralelní zásobníky** klikněte pravým tlačítkem na S. P a pak klikněte na **Přejít ke vláknu**. Okno se přepne do zobrazení vlákna a odpovídající rámec je v zobrazení. Ve stejném vlákně vidíte obě úlohy.

     ![Zvýrazněné vlákno v zobrazení vláken](../debugger/media/pdb_walkthrough_9b.png "PDB_Walkthrough_9B")

     Toto je další výhodou zobrazení úlohy v okně **paralelní zásobníky** ve srovnání s oknem **vláken** .

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Pokračování v provádění až do čtvrté zarážky

1. Chcete-li pokračovat v provádění, dokud nebude dosaženo třetí zarážce, v nabídce **ladění** klikněte na tlačítko **pokračovat**. Kliknutím na záhlaví sloupce **ID** seřadíte podle ID. Měl by se zobrazit následující obrázek.

     ![Čtyři stavy úloh v paralelních zásobnících okna](../debugger/media/pdb_walkthrough_10.png "PDB_Walkthrough_10")

     Protože byl úkol 5 dokončen, již není zobrazen. Pokud se nejedná o případ na vašem počítači a zablokování se nezobrazuje, proveďte krok jednou stisknutím klávesy **F11**.

     Úloha 3 a úloha 4 nyní čekají na sebe a jsou blokovány. K dispozici jsou také 5 nových úloh, které jsou podřízenými položkami úlohy 2 a jsou nyní naplánovány. Naplánované úlohy jsou úlohy, které byly spuštěny v kódu, ale ještě nebyly spuštěny. Proto jsou sloupce přiřazení **umístění** a **vlákna** prázdné.

     Znovu zobrazte okno **paralelní zásobníky** . Záhlaví každého pole má popisek, který zobrazuje ID a názvy vláken. Přepněte do zobrazení úlohy v okně **paralelní zásobníky** . Když najedete myší na záhlaví, zobrazí se ID a název úlohy a stav úlohy, jak je znázorněno na následujícím obrázku.

     ![Popisek záhlaví v okně paralelní zásobníky](../debugger/media/pdb_walkthrough_11.png "PDB_Walkthrough_11")

     Úkoly můžete seskupit podle sloupce. V okně **úlohy** klikněte pravým tlačítkem myši na záhlaví sloupce **stav** a pak klikněte na možnost **Seskupit podle stav**. Následující ilustrace znázorňuje okno **úlohy** seskupené podle stavu.

     ![Seskupené úkoly v okně úlohy](../debugger/media/pdb_walkthrough_12.png "PDB_Walkthrough_12")

     Můžete také seskupit podle libovolného jiného sloupce. Seskupením úloh se můžete soustředit na podmnožinu úkolů. Každá sbalitelná skupina má počet položek, které jsou seskupeny dohromady.

     Poslední funkcí okna **úlohy** k prohlédnutí je místní nabídka, která se zobrazí po kliknutí pravým tlačítkem myši na úlohu.

     Místní nabídka zobrazuje různé příkazy v závislosti na stavu úlohy. Příkazy mohou zahrnovat **kopírování**, **Výběr všech**, **hexadecimálního zobrazení**, **Přepnutí na úlohu**, **zablokování přiřazeného vlákna**, **zablokování všech vláken, ale toto**a **příznak**. **Thaw Assigned Thread**

     Můžete zablokovat základní vlákno úlohy nebo úlohy nebo můžete zablokovat všechna vlákna s výjimkou přiřazeného. Zmrazené vlákno je v okně **úlohy** reprezentováno, protože je v okně **vlákna** pomocí modré ikony *pauzy* .

## <a name="summary"></a>Souhrn
 Tento názorný postup ukázal okna **paralelních úkolů** a **paralelních zásobníků** pro ladicí program. Používejte tato okna na skutečných projektech, které používají vícevláknový kód. Můžete kontrolovat paralelní kód napsaný v jazyce C++, C# nebo Visual Basic.

## <a name="see-also"></a>Viz také
- [Ladění vícevláknových aplikací](../debugger/walkthrough-debugging-a-parallel-application.md)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
- [Paralelní programování](/dotnet/standard/parallel-programming/index)
- [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime)
- [Použití okna Paralelní zásobníky](../debugger/using-the-parallel-stacks-window.md)
- [Používání okna úloh](../debugger/using-the-tasks-window.md)
