---
title: Ladění paralelní aplikace | Dokumentace Microsoftu
description: Ladění pomocí okna paralelních úloh a Paralelní zásobníky v sadě Visual Studio
ms.date: 03/22/2018
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
ms.openlocfilehash: dcc63eef048dd1e4ae205214ac62f8aa04d8a824
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252522"
---
# <a name="walkthrough-debugging-a-parallel-application-in-visual-studio-c-visual-basic-c"></a>Návod: Ladění paralelní aplikace v aplikaci Visual Studio (C#Visual Basic, C++)

Tento návod ukazuje, jak používat **paralelní úlohy** a **paralelní zásobníky** ladění paralelní aplikace systému windows. Tato okna vám pomůžou pochopit a ověřit chování kódu, který používá [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) nebo [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime). Tento názorný postup obsahuje ukázkový kód, který má integrovanou zarážky. Poté, co kód přestane fungovat, návodu ukazuje způsob použití **paralelní úlohy** a **paralelní zásobníky** windows jej prozkoumat.

 Tento návod vás naučí tyto úlohy:

- Jak zobrazit zásobníky volání všech vláken v jednom zobrazení.

- Postup zobrazení seznamu `System.Threading.Tasks.Task` instancí, které jsou vytvořeny ve vaší aplikaci.

- Jak zobrazit skutečné volání zásobníků úkolů místo vlákna.

- Jak se orientovat na kód z **paralelní úlohy** a **paralelní zásobníky** systému windows.

- Jak windows zvládnout škálování prostřednictvím seskupování, přibližování a další související funkce.

## <a name="prerequisites"></a>Požadavky
 Tento návod předpokládá, že **pouze můj kód** je povolená (je povolená ve výchozím nastavení v novějších verzích sady Visual Studio). Na **nástroje** nabídky, klikněte na tlačítko **možnosti**, rozbalte **ladění** uzlu, vyberte **Obecné**a pak vyberte **povolit Pouze můj kód (pouze spravované)** . Pokud tato funkce není nastavený, můžete nadále používat Tento názorný postup, ale vaše výsledky můžou lišit od ilustrací.

## <a name="c-sample"></a>Ukázka v jazyce C#
 Pokud použitím této ukázky jazyka C# Tento názorný Průvodce také předpokládá, že externí kód je skrytá. Určí, zda se zobrazí externí kód, klikněte pravým tlačítkem myši **název** záhlaví tabulky **zásobník volání** okna a poté zaškrtněte nebo zrušte **zobrazit externí kód**. Pokud tato funkce není nastavený, můžete nadále používat Tento názorný postup, ale vaše výsledky můžou lišit od ilustrací.

## <a name="c-sample"></a>Ukázky jazyka C++
 Pokud používáte ukázkou jazyka C++, můžete ignorovat odkazy na externí kód v tomto tématu. Externí kód vztahuje pouze na ukázky jazyka C#.

## <a name="illustrations"></a>Obrázky
 Na obrázcích v tomto tématu se zaznamenávají čtyřjádrový procesor počítače spuštěním ukázky jazyka C#. I když ostatní konfigurace můžete použít k dokončení tohoto návodu, obrázky můžou lišit od co se zobrazí ve vašem počítači.

## <a name="creating-the-sample-project"></a>Vytvoření ukázkového projektu
 Ukázkový kód v tomto názorném postupu se pro aplikaci, která nemá žádný účinek. Cílem je právě pochopit, jak pomocí nástroje systému windows pro ladění paralelní aplikace.

#### <a name="to-create-the-sample-project"></a>K vytvoření ukázkového projektu

1. Otevřete Visual Studio a vytvořte nový projekt.

    ::: moniker range=">=vs-2019"
    Stisknutím klávesy **ESC** zavřete okno Start. Zadáním **CTRL + Q** otevřete vyhledávací pole, zadejte příkaz **Console** (nebo **c++** ), zvolte **šablony**a potom:

    - Pro C# nebo Visual Basic vyberte možnost **vytvořit nový projekt konzolové aplikace (.NET Framework)** pro C# nebo Visual Basic. V dialogovém okně, které se zobrazí, vyberte **vytvořit**.
    - Pro C++vyberte možnost **vytvořit nový projekt konzolové aplikace** pro C++. V dialogovém okně, které se zobrazí, vyberte **vytvořit**.

    Pak zadejte název nebo použijte výchozí název a klikněte na **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**. V levém podokně dialogového okna **Nový projekt** vyberte následující:

    - V případě C# aplikace v části **vizuál C#** zvolte **Windows Desktop**a potom v prostředním podokně zvolte **Konzolová aplikace (.NET Framework)** .
    - V případě aplikace Visual Basic vyberte v části **Visual Basic**možnost **plocha Windows**a potom v prostředním podokně zvolte **Konzolová aplikace (.NET Framework)** .
    - V případě C++ aplikace v části **vizuál C++** zvolte **plocha Windows**, a pak zvolte **Konzolová aplikace Windows**.

    Pak zadejte název nebo použijte výchozí název a klikněte na **OK**.
    ::: moniker-end

    Pokud nevidíte šablonu projektu **konzolové aplikace** , přejděte do části **nástroje** > **získat nástroje a funkce...** , které otevře instalační program pro Visual Studio. Zvolte možnost vývoj **desktopových** aplikací pro .NET nebo **Desktop C++**  a zvolte možnost **Upravit**.

1. Otevřete soubor kódu .cpp, .cs nebo .vb v projektu. Odstraňte její obsah, chcete-li vytvořit prázdný soubor kódu.

1. Vložte následující kód pro zvolený jazyk do souboru prázdný kód.

   [!code-csharp[Debugger#1](../debugger/codesnippet/CSharp/walkthrough-debugging-a-parallel-application_1.cs)]
   [!code-cpp[Debugger#1](../debugger/codesnippet/CPP/walkthrough-debugging-a-parallel-application_1.cpp)]
   [!code-vb[Debugger#1](../debugger/codesnippet/VisualBasic/walkthrough-debugging-a-parallel-application_1.vb)]

1. Na **souboru** nabídky, klikněte na tlačítko **Uložit vše**.

1. Na **sestavení** nabídky, klikněte na tlačítko **znovu sestavit řešení**.

    Všimněte si, že existují čtyři volání `Debugger.Break` (`DebugBreak` v C++ ukázce) proto není potřeba vložit zarážky; jednoduše spuštěním aplikace způsobí jeho přerušení v ladicím programu až čtyřikrát.

## <a name="using-the-parallel-stacks-window-threads-view"></a>Použití okna Paralelní zásobníky: Zobrazení vláken
 Na **ladění** nabídky, klikněte na tlačítko **spustit ladění**. Počkejte první zarážce.

#### <a name="to-view-the-call-stack-of-a-single-thread"></a>Chcete-li zobrazit zásobník volání z jednoho vlákna

1. Na **ladění** nabídky, přejděte k **Windows** a potom klikněte na tlačítko **vlákna**. Ukotvit **vlákna** okno v dolní části sady Visual Studio.

2. Na **ladění** nabídky, přejděte k **Windows** a potom klikněte na tlačítko **zásobník volání**. Ukotvit **zásobník volání** okno v dolní části sady Visual Studio.

3. Klikněte dvakrát na vlákno v **vlákna** okna, aby byl aktuální. Aktuální vlákna mají žlutá šipka. Při změně aktuálního vlákna, zobrazí se jeho zásobník volání v **zásobník volání** okna.

#### <a name="to-examine-the-parallel-stacks-window"></a>Prozkoumat okna paralelní zásobníky

1. Na **ladění** nabídky, přejděte k **Windows** a potom klikněte na tlačítko **paralelní zásobníky**. Ujistěte se, že **vlákna** je vybraná pole v levém horním rohu.

     S použitím **paralelní zásobníky** můžete zobrazit více zásobníky volání ve stejnou dobu v jednom zobrazení. Je vidět na následujícím obrázku **paralelní zásobníky** okno výše **zásobník volání** okna.

     ![Zobrazení okna paralelní zásobníky vlákna](../debugger/media/pdb_walkthrough_1.png "PDB_Walkthrough_1")

     V jednom poli se zobrazí zásobník volání z hlavního vlákna a zásobníky volání pro čtyři vlákna jsou seskupené do jiného pole. Čtyři vlákna jsou seskupeny dohromady, protože jejich rámce zásobníku sdílet stejnou metodu kontexty; To znamená, že jsou ve stejné metody: `A`, `B`, a `C`. K zobrazení ID vlákna a názvy vláken, které sdílejí stejné pole, najeďte myší do tohoto pole hlavičky (**4 vlákna**). Aktuální vlákno je zobrazená tučným písmem.

     ![Popisek, který ukazuje názvy a ID vlákna](../debugger/media/pdb_walkthrough_1a.png "PDB_Walkthrough_1A")

     Žlutá šipka označuje aktivní blok zásobníku aktuálního vlákna.

     Můžete nastavit, kolik detailů chcete zobrazit pro rámce zásobníku (**názvů modulů**, **typy parametrů**, **názvy parametrů**, **hodnoty parametrů**, **Čísla řádků** a **posuny bajtů**) kliknutím pravým tlačítkem myši v **zásobník volání** okna.

     Modré zvýraznění kolem pole označuje, že aktuální vlákno je součástí tohoto pole. Aktuální vlákno je také označeny tučně zásobníku v popisu. Pokud dvakrát kliknete na hlavní vlákno v okně vlákna, můžete sledovat, která modré zvýraznění v **paralelní zásobníky** okno přesune odpovídajícím způsobem.

     ![Zvýrazněný hlavní vlákno v okna paralelní zásobníky](../debugger/media/pdb_walkthrough_1c.png "PDB_Walkthrough_1C")

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Chcete-li pokračovat v provádění, dokud druhý zarážku

1. Provádění pokračovat, dokud druhý dosažení zarážky, na **ladění** nabídky, klikněte na tlačítko **pokračovat**. Následující obrázek znázorňuje strom vlákno na druhý zarážce.

     ![Paralelní zásobníky okno, které ukazuje mnoho větví](../debugger/media/pdb_walkthrough_2.png "PDB_Walkthrough_2")

     Na první zarážce všechny čtyři vlákna absolvovanou z adresu S.A S.B S.C metod. Informace, které musí stále zobrazená v **paralelní zásobníky** okna, ale čtyři vlákna pokročila dále. Jeden z nich nadále S.D a potom S.E. Jiné nadále S.F S.G a S.H. Dvěma dalšími pokračování S.I a S.J a z existovat jeden z nich absolvovanou S.K a druhý nadále externí neuživatelský kód.

     Například myší nad pole záhlaví, **1 vlákno** nebo **2 vláknech**, abyste si zobrazili vlákno ID vlákna. Při najetí myší nad rámec zásobníku zobrazíte vlákna ID a dalších podrobnostech rámce. Modré zvýraznění označuje aktuální vlákno a žlutá šipka označuje aktivní blok zásobníku aktuálního vlákna.

     Ikona látky vláken (interweaved řádky) označují aktivní zásobník snímků vlákny. V **zásobník volání** okna, dvakrát klikněte na panel S.B rámce přepínačů. **Paralelní zásobníky** okno označuje aktuální rámec zásobníku aktuálního vlákna s ikonou zelené šipky zakřivené.

     V **vlákna** okně přepínat mezi vlákny a zda se zobrazila zpráva zobrazení **paralelní zásobníky** aktualizovat okno.

     Můžete přepnout do jiného vlákna, nebo na jiný rámec z jiného vlákna, pomocí místní nabídky **paralelní zásobníky** okna. Například, klikněte pravým tlačítkem na S.J, přejděte na **přepnout na rámec**a potom klikněte na příkaz.

     ![Paralelních zásobníků cesta provádění](../debugger/media/pdb_walkthrough_2b.png "PDB_Walkthrough_2B")

     Klikněte pravým tlačítkem na S.C a přejděte na **přepnout na rámec**. Jeden z příkazů má zaškrtávací políčko, která indikuje rámec zásobníku aktuálního vlákna. Můžete přepnout na tento rámec stejné vlákna (zelená šipka se přesune) nebo můžete přepnout do jiného podprocesu (modré zvýraznění se přesune také). Následující obrázek znázorňuje podnabídky.

     ![Zásobníky nabídky 2 možnosti v C je aktuální J](../debugger/media/pdb_walkthrough_3.png "PDB_Walkthrough_3")

     Když metoda kontext je spojen s jedním zásobníku, zobrazí záhlaví pole **1 vlákno** a k němu můžete přepnout na něj poklikejte. Pokud dvakrát kliknete na metodu kontext, který má více než 1 blok s ním spojená, pak v nabídce automaticky otevře. Když najedete ukazatelem metoda kontextů, Všimněte si, že na černý trojúhelník na pravé straně. Kliknutím na tuto trojúhelník také zobrazí v místní nabídce.

     Pro velké aplikace, které mají mnoho vláken můžete chtít zaměřit pouze podmnožinu vláken. **Paralelní zásobníky** okna můžete zobrazit zásobníky volání pouze pro vlákna s příznakem. Označit vlákna, použijte nabídku nebo první buňky vlákna.

     Na panelu nástrojů klikněte na tlačítko **zobrazit pouze označená příznakem** tlačítko vedle pole se seznamem.

     ![Paralelní zásobníky okna a popisu](../debugger/media/pdb_walkthrough_3a.png "PDB_Walkthrough_3A")

     Nyní pouze vlákno s příznakem objeví **paralelní zásobníky** okna.

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Chcete-li pokračovat v provádění, dokud třetí zarážku

1. Provádění pokračovat, dokud třetí dosažení zarážky, na **ladění** nabídky, klikněte na tlačítko **pokračovat**.

     Při více vláken jsou ve stejné metody, ale nebyla na začátek zásobníku volání metody, metoda se zobrazí v různých polí. Příklad na aktuální zarážce je S.L, který v sobě obsahuje tři vlákna a zobrazí se tří polí. Dvakrát klikněte na panel j.

     ![Cesta provedení v okna paralelní zásobníky](../debugger/media/pdb_walkthrough_3b.png "PDB_Walkthrough_3B")

     Všimněte si, že S.L je tak, abyste viděli, kde se zobrazí tučně ve dvou polích. Pokud chcete zobrazit volání do S.L rámce, který a které snímků je volání, klikněte na tlačítko **přepnout zobrazení metody** tlačítko na panelu nástrojů. Následující obrázek znázorňuje přehled metody **paralelní zásobníky** okna.

     ![Zobrazení metody v okna paralelní zásobníky](../debugger/media/pdb_walkthrough_4.png "PDW_Walkthrough_4")

     Všimněte si, jak diagramu neseskupené na vybrané metodě a umístěna do své vlastní pole uprostřed zobrazení. Volané a volající zobrazí v horní a dolní části. Klikněte na tlačítko **přepnout zobrazení metody** tlačítka opustit tento režim.

     Nabídku **paralelní zásobníky** okno má také následující další položky.

    - **Hexadecimální zobrazení** přepíná čísel v popiscích mezi desetinných míst a šestnáctkové číslo.

    - **Symbol nastavení** otevřete příslušné dialogových oknech.

    - **Zobrazit vlákna ve zdroji** Přepíná zobrazení značky vlákna ve zdrojovém kódu, která zobrazuje umístění vlákna ve zdrojovém kódu.

    - **Zobrazit externí kód** zobrazí všechny snímky, i když nejsou v uživatelském kódu. Vyzkoušejte si to chcete zobrazit diagram rozšířit, aby odpovídala další snímky (která může být neaktivní, protože nemáte symboly pro ně).

2. V **paralelní zásobníky** okno, ujistěte se, že **automaticky přejít na aktuální rámec zásobníku** nachází na panelu nástrojů.

     Pokud máte velké diagramy a přejdete na další zarážku, můžete zobrazení tak, aby automaticky přejít na aktivní blok zásobníku aktuálního vlákna; To znamená, že vlákno, které první narazí zarážku.

3. Než budete pokračovat, v **paralelní zásobníky** okno, přejděte úplně vlevo a úplně dolů.

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Chcete-li pokračovat v provádění, dokud čtvrtý zarážku

1. Chcete-li obnovit spuštění, dokud čtvrtý dosažení zarážky, na **ladění** nabídky, klikněte na **pokračovat**.

     Všimněte si, že jak autoscrolled zobrazení na místě. Přepnout vlákna v **vlákna** okno nebo přepínač zásobník snímků v **zásobník volání** okno a Všimněte si, že jak zobrazení vždy autoscrolls správný snímek. Vypnout **automaticky přejít na aktuální rámec nástroj** možnost a zobrazit rozdíl.

     **Pohled z ptačí perspektivy** také pomáhá s velkých diagramů v **paralelní zásobníky** okna. Ve výchozím nastavení **pohled z ptačí perspektivy** zapnutý. Ale můžete přepínat ho kliknutím na tlačítko mezi posuvníků v pravém dolním rohu okna, jak je znázorněno na následujícím obrázku.

     ![Zobrazení z ptačí perspektivy&#45;oční zobrazení okna paralelní zásobníky](../debugger/media/pdb_walkthrough_5.png "PDB_Walkthrough_5")

     Pohled z ptačí perspektivy lze přesunout obdélník rychlé posouvání zobrazení diagramu.

     Klikněte na prázdnou oblast na diagramu a přetáhněte ji na požadované místo je jiný způsob, jak přesunout diagramu vede libovolným směrem.

     Chcete-li přiblížení a oddálení diagramu, stiskněte a podržte klávesu CTRL a kolečka myši přesunete. Alternativně klepněte na tlačítko lupy na panelu nástrojů a pak pomocí nástroje přiblížení.

     Můžete také zobrazit zásobníky shora dolů směrem místo zdola nahoru, kliknutím **nástroje** nabídky, kliknutím na **možnosti**a poté zaškrtněte nebo zrušte zaškrtnutí možnosti v části **ladění** uzlu.

2. Než budete pokračovat, na **ladění** nabídky, klikněte na tlačítko **Zastavit ladění** k ukončení provádění.

## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>Použití okna paralelní úlohy a úkoly zobrazení okna paralelní zásobníky
 Doporučujeme dokončení předchozích postupů, než budete pokračovat.

#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>Restartujte aplikaci až k první zarážce přístupů

1. Na **ladění** nabídky, klikněte na tlačítko **spustit ladění** a počkejte první zarážce.

2. Na **ladění** nabídky, přejděte k **Windows** a potom klikněte na tlačítko **vlákna**. Ukotvit **vlákna** okno v dolní části sady Visual Studio.

3. Na **ladění** nabídky, přejděte k **Windows** a klikněte na tlačítko **zásobník volání**. Ukotvit **zásobník volání** okno v dolní části sady Visual Studio.

4. Klikněte dvakrát na vlákno v **vlákna** okna je aktuální. Aktuální vlákna mají žlutou šipkou. Při změně aktuální vlákno, se aktualizují ostatní okna. V dalším kroku prozkoumáme úlohy.

5. Na **ladění** nabídky, přejděte k **Windows**a potom klikněte na tlačítko **úlohy**. Je vidět na následujícím obrázku **úlohy** okna.

     ![Čtyři spouštění úloh v okně úlohy](../debugger/media/pdb_walkthrough_6.png "PDW_Walkthrough_6")

     Pro každý úkol spuštěný si můžete přečíst jeho ID, která je vrácena vlastnost se stejným názvem, ID a název vlákna, na kterém běží, jeho umístění (ukazatel myši tuto zobrazí popis tlačítka, který má v zásobníku volání celé). Také **úloh** sloupce, můžete zobrazit metody, která byla předána do úkolu; jinými slovy, výchozím bodem.

     Libovolný sloupec lze seřadit. Všimněte si, že piktogram setřídit, která označuje sloupec pro řazení a směr. Můžete také změnit uspořádání sloupců jejich přetažením doleva nebo doprava.

     Žlutá šipka označuje aktuální úlohu. Dvojitým kliknutím na úlohu nebo v místní nabídce můžete přepnout úkoly. Při přepínání úloh podkladové vlákno nebude aktuální a ostatní okna se aktualizují.

     Při ruční přepínání z jednoho úkolu do druhého, žlutá šipka se přesune, ale bílé šipku stále zobrazuje úlohy, která způsobila přerušení ladicího programu.

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Chcete-li pokračovat v provádění, dokud druhý zarážku

1. Provádění pokračovat, dokud druhý dosažení zarážky, na **ladění** nabídky, klikněte na tlačítko **pokračovat**.

     Dříve **stav** sloupec jsme si ukázali, všechny úlohy jako aktivní, ale teď dvě úlohy jsou zablokované. Úkoly mohou být blokovány mnoho různých důvodů. V **stav** sloupce, podržte ukazatel myši nad úkol čekání se dozvíte, proč je zablokovaný. Na následujícím obrázku je například úloha 3 čekání na úloha 4.

     ![Dvě úlohy čekání v okně úlohy](../debugger/media/pdb_walkthrough_7.png "PDB_Walkthrough_7")

     Úloha 4, pak čeká na monitorování vlastněný vláknem přiřazen k úloze 2. (Klikněte pravým tlačítkem na záhlaví a zvolte **sloupce** > **přiřazení vlákna** k zobrazení hodnoty přiřazení vlákna pro úlohu 2).

     ![Čekání na úkol a popisek v okně úlohy](../debugger/media/pdb_walkthrough_7a.png "PDB_Walkthrough_7A")

     Úlohu můžete označit příznakem, kliknutím na příznak v prvním sloupci **úlohy** okna.

     Označování můžete použít ke sledování úkolů mezi různé zarážek v rámci jedné relace ladění nebo chcete-li filtrovat úlohy, jejichž zásobníky volání jsou uvedeny v **paralelní zásobníky** okna.

     Pokud jste použili **paralelní zásobníky** okno dříve, můžete zobrazit vlákna aplikace. Zobrazení **paralelní zásobníky** okno znovu, tentokrát ale zobrazit úlohy aplikací. To udělat tak, že vyberete **úlohy** v okně na levém horním rohu. Následující obrázek znázorňuje zobrazení úlohy.

     ![Úlohy zobrazení okna paralelní zásobníky](../debugger/media/pdb_walkthrough_8.png "PDB_Walkthrough_8")

     Vlákna, která nejsou aktuálně provádění úlohy se nezobrazují v zobrazení úlohy **paralelní zásobníky** okna. Kromě toho pro vlákna, které jsou spouštěny úkoly, některých rámců zásobníku, které nejsou relevantní pro úlohy jsou filtrovány ze horní a dolní část zásobníku.

     Zobrazení **úlohy** znovu okno. Klikněte pravým tlačítkem na libovolné záhlaví sloupce, chcete-li zobrazit místní nabídku pro sloupec.

     V místní nabídce můžete použít k přidání nebo odebrání sloupců. Například není vybraný sloupec domény aplikace; Proto se nezobrazí v seznamu. Klikněte na tlačítko **nadřazené**. **Nadřazené** se zobrazí sloupec bez hodnot pro všechny čtyři úkoly.

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Chcete-li pokračovat v provádění, dokud třetí zarážku

1. Provádění pokračovat, dokud třetí dosažení zarážky, na **ladění** nabídky, klikněte na tlačítko **pokračovat**.

     Nový úkol, úloha 5, je nyní spuštěna a úloha 4 je nyní čekání. Můžete zobrazit důvod, proč tak, že najedete myší úkol čekání v **stav** okna. V **nadřazené** sloupce, Všimněte si, že úloha 4 je nadřazená úloha 5.

     Pokud chcete lépe vizualizovat relaci nadřazený podřízený, klikněte pravým tlačítkem na záhlaví sloupce a potom klikněte na **nadřazeného a podřízeného prvku**. Měli byste vidět na následujícím obrázku.

     ![Nadřazené&#45;podřízené zobrazení v okně úlohy](../debugger/media/pdb_walkthrough_9.png "PDB_Walkthrough_9")

     Všimněte si, že ve stejném vlákně běží úloha 4 a 5. úkol (Zobrazit **přiřazení vlákna** sloupce, když je skrytý). Tyto informace se nezobrazí v **vlákna** okno; zobrazují, tady je Další výhodou **úlohy** okna. Chcete-li to ověřit, zobrazte **paralelní zásobníky** okna. Ujistěte se, že si prohlížíte **úlohy**. Najít úlohy 4 a 5 dvojitým kliknutím v **úlohy** okna. Když to uděláte, modré zvýraznění **paralelní zásobníky** aktualizovat okno. Můžete také vyhledat úlohy 4 a 5 tím, že kontroluje popisky na **paralelní zásobníky** okna.

     ![Zobrazení v okna paralelní zásobníky úlohy](../debugger/media/pdb_walkthrough_9a.png "PDB_Walkthrough_9A")

     V **paralelní zásobníky** okna, klikněte pravým tlačítkem na S.P a potom klikněte na **přejít na vlákno**. V okně se přepne do zobrazení vláken a odpovídající rámec je příkaz v zobrazení. Obě úlohy si můžete prohlédnout ve stejném vlákně.

     ![Zvýrazněný vlákna v zobrazení vláken](../debugger/media/pdb_walkthrough_9b.png "PDB_Walkthrough_9B")

     Toto je Další výhodou zobrazení úlohy **paralelní zásobníky** okno, ve srovnání s **vlákna** okna.

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Chcete-li pokračovat v provádění, dokud čtvrtý zarážku

1. Provádění pokračovat, dokud třetí dosažení zarážky, na **ladění** nabídky, klikněte na tlačítko **pokračovat**. Klikněte na tlačítko **ID** záhlaví sloupce seřadíte položky podle ID. Měli byste vidět na následujícím obrázku.

     ![Čtyři úlohy státy v okna paralelní zásobníky](../debugger/media/pdb_walkthrough_10.png "PDB_Walkthrough_10")

     Protože byla dokončena úloha 5, se už nezobrazuje. Pokud to není případ v počítači a k zablokování nezobrazuje, krok jednou stisknutím kombinace kláves **F11**.

     Úloha 3 a úloha 4 jsou nyní čeká na sebe navzájem a jsou zablokované. Existují také 5 nových úkolů, které jsou podřízené úlohy 2 a nyní jsou naplánovány. Naplánované úlohy jsou uvedeny úlohy, které byly zahájeny v kódu, ale ještě nebyla spuštěna. Proto jejich **umístění** a **vlákna přiřazení** sloupce jsou prázdné.

     Zobrazení **paralelní zásobníky** znovu okno. Záhlaví každého pole má popisek, který ukazuje názvy a ID vlákna. Přepnout do zobrazení úlohy v **paralelní zásobníky** okna. Najeďte myší na záhlaví zobrazíte ID úkolu a název a stav úlohy, jak je znázorněno na následujícím obrázku.

     ![Popisek záhlaví v okna paralelní zásobníky](../debugger/media/pdb_walkthrough_11.png "PDB_Walkthrough_11")

     Úlohy můžete seskupovat podle sloupce. V **úlohy** okna, klikněte pravým tlačítkem na **stav** záhlaví sloupce a pak klikněte na tlačítko **Seskupit podle stavu**. Je vidět na následujícím obrázku **úlohy** okno seskupených podle stavu.

     ![Seskupených úkolů v okně úlohy](../debugger/media/pdb_walkthrough_12.png "PDB_Walkthrough_12")

     Můžete taky Seskupit podle libovolného sloupce. Seskupení úlohami můžete soustředit na dílčí úkoly. Každá skupina sbalitelné obsahuje počet položek, které jsou seskupeny dohromady.

     Poslední součástí **úlohy** okno k prozkoumání je místní nabídky, která se zobrazí, když kliknete pravým tlačítkem na úlohu.

     V místní nabídce se zobrazí různé příkazy, v závislosti na stavu úlohy. Může zahrnovat příkazy **kopírování**, **Vybrat vše**, **hexadecimální zobrazení**, **přejít k úloze**, **zablokovat přiřazené Vlákno**, **pozastavit všechna vlákna kromě to**, a **uvolnit přiřazené vlákno**, a **příznak**.

     Můžete ukotvit podkladové vlákno úlohu nebo úlohy, nebo můžete zablokovat všechna vlákna kromě přiřazená vlákna. Zmrazené vlákno je vyjádřena v **úlohy** je okno, jako je **vlákna** okno podle modrý *pozastavit* ikonu.

## <a name="summary"></a>Souhrn
 Tento názorný postup jsme vám ukázali **paralelní úlohy** a **paralelní zásobníky** ladicího programu systému windows. Používání těchto oken na skutečné projekty, které používají kódy s více vlákny. Můžete zkoumat, paralelní kód napsaný v C++, C# nebo Visual Basic.

## <a name="see-also"></a>Viz také
- [Ladění vícevláknových aplikací](../debugger/walkthrough-debugging-a-parallel-application.md)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
- [Paralelní programování](/dotnet/standard/parallel-programming/index)
- [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime)
- [Použití okna Paralelní zásobníky](../debugger/using-the-parallel-stacks-window.md)
- [Použití okna úloh](../debugger/using-the-tasks-window.md)