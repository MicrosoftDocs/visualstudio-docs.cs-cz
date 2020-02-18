---
title: Ladění paralelní aplikace | Dokumentace Microsoftu
description: Ladění pomocí okna paralelních úloh a Paralelní zásobníky v sadě Visual Studio
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
ms.openlocfilehash: c9079fc17da9f89ceae61cbd7d4f086f1db133cf
ms.sourcegitcommit: 6ef52c2030b37ea7a64fddb32f050ecfb77dd918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416422"
---
# <a name="walkthrough-debugging-a-parallel-application-in-visual-studio-c-visual-basic-c"></a>Návod: ladění paralelní aplikace v aplikaci Visual Studio (C#, Visual Basic, C++)

Tento návod ukazuje, jak použít **Paralelní úlohy** a okna **paralelních zásobníků** k ladění paralelní aplikace. Tato okna vám pomůžou pochopit a ověřit chování kódu, který používá [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) nebo [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime). Tento názorný postup obsahuje ukázkový kód, který má integrovanou zarážky. Po zalomení kódu návod ukazuje, jak použít **Paralelní úlohy** a okna **paralelní zásobníky** k její kontrole.

 Tento návod vás naučí tyto úlohy:

- Jak zobrazit zásobníky volání všech vláken v jednom zobrazení.

- Jak zobrazit seznam instancí `System.Threading.Tasks.Task`, které jsou vytvořeny ve vaší aplikaci.

- Jak zobrazit skutečné volání zásobníků úkolů místo vlákna.

- Jak přejít na kód z okna **Paralelní úlohy** a **paralelní zásobníky**

- Jak windows zvládnout škálování prostřednictvím seskupování, přibližování a další související funkce.

## <a name="prerequisites"></a>Požadavky
 Tento návod předpokládá, že je povolený **pouze můj kód** (ve výchozím nastavení je povolený v novějších verzích sady Visual Studio). V nabídce **nástroje** klikněte na položku **Možnosti**, rozbalte uzel **ladění** , vyberte možnost **Obecné**a poté vyberte možnost **Povolit pouze můj kód (pouze spravované)** . Pokud tato funkce není nastavený, můžete nadále používat Tento názorný postup, ale vaše výsledky můžou lišit od ilustrací.

## <a name="c-sample"></a>Ukázka v jazyce C#
 Pokud použitím této ukázky jazyka C# Tento názorný Průvodce také předpokládá, že externí kód je skrytá. Chcete-li přepnout, zda je zobrazen externí kód, klikněte pravým tlačítkem **myši na záhlaví tabulky v** okně **zásobník volání** a potom vyberte nebo zrušte zaškrtnutí **Zobrazit externí kód**. Pokud tato funkce není nastavený, můžete nadále používat Tento názorný postup, ale vaše výsledky můžou lišit od ilustrací.

## <a name="c-sample"></a>Ukázky jazyka C++
 Pokud používáte ukázkou jazyka C++, můžete ignorovat odkazy na externí kód v tomto tématu. Externí kód vztahuje pouze na ukázky jazyka C#.

## <a name="illustrations"></a>Obrázky
 Na obrázcích v tomto tématu se zaznamenávají čtyřjádrový procesor počítače spuštěním ukázky jazyka C#. I když ostatní konfigurace můžete použít k dokončení tohoto návodu, obrázky můžou lišit od co se zobrazí ve vašem počítači.

## <a name="creating-the-sample-project"></a>Vytvoření ukázkového projektu
 Ukázkový kód v tomto názorném postupu se pro aplikaci, která nemá žádný účinek. Cílem je právě pochopit, jak pomocí nástroje systému windows pro ladění paralelní aplikace.

#### <a name="to-create-the-sample-project"></a>K vytvoření ukázkového projektu

1. Otevřete Visual Studio a vytvořte nový projekt.

   ::: moniker range=">=vs-2019"

   Pokud okno Start není otevřeno, vyberte **soubor** > **Spustit okno**.

   V okně Start vyberte možnost **vytvořit nový projekt**.

   V okně **vytvořit nový projekt** zadejte do vyhledávacího pole nebo zadejte *Console* . Dále v seznamu **C#** jazyk **C++** vyberte, nebo **Visual Basic** a v seznamu platforma zvolte možnost **Windows** . 

   Po použití filtrů jazyků a platforem zvolte **Konzolová aplikace (.NET Core)** nebo, pro C++šablonu **Konzolová aplikace** a klikněte na tlačítko **Další**.

   > [!NOTE]
   > Pokud nevidíte správnou šablonu, přejděte na **nástroje** > **získat nástroje a funkce...** , který otevře instalační program pro Visual Studio. Zvolte možnost vývoj **desktopových** aplikací pro .NET nebo **Desktop C++**  a zvolte možnost **Upravit**.

   V okně **Konfigurovat nový projekt** zadejte název nebo použijte výchozí název v poli **název projektu** . Pak zvolte **vytvořit**.

   ::: moniker-end
   ::: moniker range="vs-2017"
   V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**. V levém podokně dialogového okna **Nový projekt** vyberte následující:

   - V případě C# aplikace v části **vizuál C#** zvolte **Windows Desktop**a potom v prostředním podokně zvolte **Konzolová aplikace (.NET Framework)** .
   - V případě aplikace Visual Basic vyberte v části **Visual Basic**možnost **plocha Windows**a potom v prostředním podokně zvolte **Konzolová aplikace (.NET Framework)** .
   - V případě C++ aplikace v části **vizuál C++** zvolte **plocha Windows**, a pak zvolte **Konzolová aplikace Windows**.

   Pokud se nezobrazuje **Konzolová aplikace (.NET Core)** nebo, pro C++šablonu projektu **Konzolová aplikace** , přejděte do části **nástroje** > **získat nástroje a funkce...** , který otevře instalační program pro Visual Studio. Zvolte možnost vývoj **desktopových** aplikací pro .NET nebo **Desktop C++**  a zvolte možnost **Upravit**.

   Pak zadejte název nebo použijte výchozí název a klikněte na **OK**.

   Vyberte **OK**.
   ::: moniker-end

   Zobrazí se nový projekt konzoly. Po vytvoření projektu se zobrazí zdrojový soubor.

1. Otevřete soubor kódu .cpp, .cs nebo .vb v projektu. Odstraňte její obsah, chcete-li vytvořit prázdný soubor kódu.

1. Vložte následující kód pro zvolený jazyk do souboru prázdný kód.

   [!code-csharp[Debugger#1](../debugger/codesnippet/CSharp/walkthrough-debugging-a-parallel-application_1.cs)]
   [!code-cpp[Debugger#1](../debugger/codesnippet/CPP/walkthrough-debugging-a-parallel-application_1.cpp)]
   [!code-vb[Debugger#1](../debugger/codesnippet/VisualBasic/walkthrough-debugging-a-parallel-application_1.vb)]

1. V nabídce **soubor** klikněte na **Uložit vše**.

1. V nabídce **sestavení** klikněte na příkaz **znovu sestavit řešení**.

    Všimněte si, že existují čtyři volání `Debugger.Break` (`DebugBreak` v C++ ukázce), proto není nutné vkládat zarážky; pouhým spuštěním aplikace dojde k přerušení v ladicím programu po dobu až čtyřikrát.

## <a name="using-the-parallel-stacks-window-threads-view"></a>Použití paralelních zásobníků okna: zobrazení vlákna
 V nabídce **ladit** klikněte na **Spustit ladění**. Počkejte první zarážce.

#### <a name="to-view-the-call-stack-of-a-single-thread"></a>Chcete-li zobrazit zásobník volání z jednoho vlákna

1. V nabídce **ladění** přejděte na **okna** a potom klikněte na **vlákna**. Ukotvěte okno **vlákna** v dolní části sady Visual Studio.

2. V nabídce **ladění** přejděte na **okna** a potom klikněte na **zásobník volání**. Ukotvěte okno **zásobník volání** v dolní části sady Visual Studio.

3. Dvakrát klikněte na vlákno v okně **vlákna** , čímž se nastaví jako aktuální. Aktuální vlákna mají žlutá šipka. Když změníte aktuální vlákno, jeho zásobník volání se zobrazí v okně **zásobník volání** .

#### <a name="to-examine-the-parallel-stacks-window"></a>Prozkoumat okna paralelní zásobníky

1. V nabídce **ladění** přejděte na **okna** a potom klikněte na **paralelní zásobníky**. Ujistěte se, že je v poli v levém horním rohu vybraná možnost **vlákna** .

     Pomocí okna **paralelní zásobníky** můžete zobrazit více zásobníků volání současně v jednom zobrazení. Následující ilustrace znázorňuje okno **paralelní zásobníky** nad oknem **zásobník volání** .

     ![Zobrazení vláken v okně paralelní zásobníky](../debugger/media/pdb_walkthrough_1.png "PDB_Walkthrough_1")

     V jednom poli se zobrazí zásobník volání z hlavního vlákna a zásobníky volání pro čtyři vlákna jsou seskupené do jiného pole. Čtyři vlákna jsou seskupena dohromady, protože jejich rámce zásobníku sdílí stejné kontexty metod; To znamená, že jsou stejné metody: `A`, `B`a `C`. Chcete-li zobrazit ID a názvy vláken, která sdílejí stejné pole, umístěte ukazatel myši na pole s hlavičkou (**4 vlákna**). Aktuální vlákno je zobrazená tučným písmem.

     ![Popis, který zobrazuje ID a názvy vláken](../debugger/media/pdb_walkthrough_1a.png "PDB_Walkthrough_1A")

     Žlutá šipka označuje aktivní blok zásobníku aktuálního vlákna.

     Kliknutím pravým tlačítkem myši v okně **zásobník volání** můžete nastavit, kolik podrobností se má zobrazit pro rámce zásobníku (**názvy modulů**, **typy parametrů**, **názvy parametrů**, **hodnoty parametrů**, **čísla řádků** a **posun bajtů**).

     Modré zvýraznění kolem pole označuje, že aktuální vlákno je součástí tohoto pole. Aktuální vlákno je také označeny tučně zásobníku v popisu. Pokud dvakrát kliknete na hlavní vlákno v okně vlákna, můžete si všimnout, že modrý zvýraznění v okně **paralelní zásobníky** se odpovídajícím způsobem přesune.

     ![Zvýrazněné hlavní vlákno v okně paralelní zásobníky](../debugger/media/pdb_walkthrough_1c.png "PDB_Walkthrough_1C")

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Chcete-li pokračovat v provádění, dokud druhý zarážku

1. Chcete-li pokračovat v provádění, dokud nebude dosaženo druhé zarážce, v nabídce **ladění** klikněte na tlačítko **pokračovat**. Následující obrázek znázorňuje strom vlákno na druhý zarážce.

     ![Okno paralelní zásobníky zobrazující mnoho větví](../debugger/media/pdb_walkthrough_2.png "PDB_Walkthrough_2")

     Na první zarážce všechny čtyři vlákna absolvovanou z adresu S.A S.B S.C metod. Tyto informace jsou stále viditelné v okně **paralelní zásobníky** , ale v těchto čtyřech vláknech probíhalo další postup. Jeden z nich nadále S.D a potom S.E. Jiné nadále S.F S.G a S.H. Dvěma dalšími pokračování S.I a S.J a z existovat jeden z nich absolvovanou S.K a druhý nadále externí neuživatelský kód.

     Můžete umístit ukazatel myši na záhlaví pole, například **1 vlákno** nebo **2 vlákna**, a zobrazit tak ID vláken vláken. Při najetí myší nad rámec zásobníku zobrazíte vlákna ID a dalších podrobnostech rámce. Modré zvýraznění označuje aktuální vlákno a žlutá šipka označuje aktivní blok zásobníku aktuálního vlákna.

     Ikona látky vláken (interweaved řádky) označují aktivní zásobník snímků vlákny. V okně **zásobník volání** poklikejte na y. B pro přepínání snímků. Okno **paralelní zásobníky** indikuje aktuální rámec zásobníku aktuálního vlákna pomocí ikony šipky zeleného zahnutého okna.

     V okně **vlákna** přepínejte mezi vlákny a sledujte, že zobrazení v okně **paralelní zásobníky** je aktualizováno.

     Pomocí místní nabídky v okně **paralelní zásobníky** můžete přepnout do jiného vlákna nebo do jiného rámce jiného vlákna. Například klikněte pravým tlačítkem S. J, přejděte na **Přepnout na rámec**a potom klikněte na příkaz.

     ![Cesta k paralelním zásobníkům pro spuštění](../debugger/media/pdb_walkthrough_2b.png "PDB_Walkthrough_2B")

     Klikněte pravým tlačítkem myši na možnost S. C a přejděte na možnost **Přepnout na rámec**. Jeden z příkazů má zaškrtávací políčko, která indikuje rámec zásobníku aktuálního vlákna. Můžete přepnout na tento rámec stejné vlákna (zelená šipka se přesune) nebo můžete přepnout do jiného podprocesu (modré zvýraznění se přesune také). Následující obrázek znázorňuje podnabídky.

     ![Nabídka zásobníků se dvěma možnostmi v C, zatímco J je aktuální.](../debugger/media/pdb_walkthrough_3.png "PDB_Walkthrough_3")

     Když je kontext metody spojen s pouze jedním snímkem zásobníku, zobrazí záhlaví pole **1 vlákno** a můžete na něj přejít dvojitým kliknutím. Pokud dvakrát kliknete na metodu kontext, který má více než 1 blok s ním spojená, pak v nabídce automaticky otevře. Když najedete ukazatelem metoda kontextů, Všimněte si, že na černý trojúhelník na pravé straně. Kliknutím na tuto trojúhelník také zobrazí v místní nabídce.

     Pro velké aplikace, které mají mnoho vláken můžete chtít zaměřit pouze podmnožinu vláken. Okno **paralelní zásobníky** může zobrazit zásobníky volání pouze pro vlákna označená příznakem. Označit vlákna, použijte nabídku nebo první buňky vlákna.

     Na panelu nástrojů klikněte na tlačítko **Zobrazit pouze označené příznakem** vedle rozevíracího seznamu.

     ![Okno paralelní zásobníky a popis tlačítka](../debugger/media/pdb_walkthrough_3a.png "PDB_Walkthrough_3A")

     Nyní se v okně **paralelní zásobníky** zobrazí pouze vlákno s příznakem.

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Chcete-li pokračovat v provádění, dokud třetí zarážku

1. Chcete-li pokračovat v provádění, dokud nebude dosaženo třetí zarážce, v nabídce **ladění** klikněte na tlačítko **pokračovat**.

     Při více vláken jsou ve stejné metody, ale nebyla na začátek zásobníku volání metody, metoda se zobrazí v různých polí. Příklad na aktuální zarážce je S.L, který v sobě obsahuje tři vlákna a zobrazí se tří polí. Dvakrát klikněte na panel j.

     ![Cesta spuštění v okně paralelní zásobníky](../debugger/media/pdb_walkthrough_3b.png "PDB_Walkthrough_3B")

     Všimněte si, že S.L je tak, abyste viděli, kde se zobrazí tučně ve dvou polích. Pokud chcete zjistit, které snímky volají do S. L a které rámce volá, klikněte na tlačítko **zobrazení přepínací metody** na panelu nástrojů. Následující ilustrace znázorňuje zobrazení metody okna **paralelní zásobníky** .

     ![Zobrazení metody v okně paralelních zásobníků](../debugger/media/pdb_walkthrough_4.png "PDW_Walkthrough_4")

     Všimněte si, jak diagramu neseskupené na vybrané metodě a umístěna do své vlastní pole uprostřed zobrazení. Volané a volající zobrazí v horní a dolní části. Pokud chcete tento režim opustit, klikněte znovu na tlačítko **zobrazení metody přepínání** .

     Místní nabídka okna **paralelní zásobníky** má také následující další položky.

    - **Hexadecimální zobrazení** přepíná čísla v popisech mezi desítkovými a šestnáctkovými hodnotami.

    - **Nastavení symbolů** otevře příslušná dialogová okna.

    - **Zobrazit vlákna ve zdroji** Přepíná zobrazení značek vláken ve zdrojovém kódu, který ukazuje umístění vláken ve zdrojovém kódu.

    - **Zobrazit externí kód** zobrazí všechny snímky i v případě, že nejsou v uživatelském kódu. Vyzkoušejte si to chcete zobrazit diagram rozšířit, aby odpovídala další snímky (která může být neaktivní, protože nemáte symboly pro ně).

2. V okně **paralelní zásobníky** se ujistěte, že je na panelu nástrojů zapnuto tlačítko **automaticky přejít na aktuální rámec zásobníku** .

     Pokud máte velké diagramy a přejdete na další zarážku, můžete zobrazení tak, aby automaticky přejít na aktivní blok zásobníku aktuálního vlákna; To znamená, že vlákno, které první narazí zarážku.

3. Než budete pokračovat, v okně **paralelní zásobníky** se posuňte všem směrem doleva a dolů.

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Chcete-li pokračovat v provádění, dokud čtvrtý zarážku

1. Chcete-li pokračovat v provádění, dokud není dosaženo čtvrté zarážky, v nabídce **ladění** klikněte na tlačítko **pokračovat**.

     Všimněte si, že jak autoscrolled zobrazení na místě. Přepněte vlákna v okně **vlákna** nebo přepněte rámce zásobníku v okně **zásobník volání** a Všimněte si, jak se zobrazení vždy automaticky posouvá na správný rámeček. Vypne **automatické posouvání na aktuální možnost snímku nástroje** a zobrazí rozdíl.

     **Pohled na pohled z ptačí perspektivy** také pomáhá s velkými diagramy v okně **paralelní zásobníky** . Ve výchozím nastavení se **zobrazuje pohled na oči** . Ale můžete přepínat ho kliknutím na tlačítko mezi posuvníků v pravém dolním rohu okna, jak je znázorněno na následujícím obrázku.

     ![&#45;Zobrazení perspektivy v okně paralelní zásobníky](../debugger/media/pdb_walkthrough_5.png "PDB_Walkthrough_5")

     Pohled z ptačí perspektivy lze přesunout obdélník rychlé posouvání zobrazení diagramu.

     Klikněte na prázdnou oblast na diagramu a přetáhněte ji na požadované místo je jiný způsob, jak přesunout diagramu vede libovolným směrem.

     Chcete-li přiblížení a oddálení diagramu, stiskněte a podržte klávesu CTRL a kolečka myši přesunete. Alternativně klepněte na tlačítko lupy na panelu nástrojů a pak pomocí nástroje přiblížení.

     Můžete také zobrazit zásobníky v horním směrem dolů, a to tak, že kliknete na nabídku **nástroje** , kliknete na možnost **Možnosti**a pak vyberete nebo zrušíte zaškrtnutí políčka v uzlu **ladění** .

2. Než budete pokračovat, v nabídce **ladění** klikněte na **Zastavit ladění** a ukončete provádění.

## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>Použití okna paralelní úlohy a úkoly zobrazení okna paralelní zásobníky
 Doporučujeme dokončení předchozích postupů, než budete pokračovat.

#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>Restartujte aplikaci až k první zarážce přístupů

1. V nabídce **ladění** klikněte na **Spustit ladění** a počkejte, než se dorazí na první zarážku.

2. V nabídce **ladění** přejděte na **okna** a potom klikněte na **vlákna**. Ukotvěte okno **vlákna** v dolní části sady Visual Studio.

3. V nabídce **ladění** přejděte na **Windows** a klikněte na **zásobník volání**. Ukotvěte okno **zásobník volání** v dolní části sady Visual Studio.

4. Dvakrát klikněte na vlákno v okně **vlákna** , čímž se vytvoří aktuální. Aktuální vlákna mají žlutou šipkou. Při změně aktuální vlákno, se aktualizují ostatní okna. V dalším kroku prozkoumáme úlohy.

5. V nabídce **ladění** vyberte možnost **Windows**a potom klikněte na položku **úlohy**. Následující obrázek znázorňuje okno **úlohy** .

     ![Čtyři spuštěné úlohy v okně úlohy](../debugger/media/pdb_walkthrough_6.png "PDW_Walkthrough_6")

     Pro každý úkol spuštěný si můžete přečíst jeho ID, která je vrácena vlastnost se stejným názvem, ID a název vlákna, na kterém běží, jeho umístění (ukazatel myši tuto zobrazí popis tlačítka, který má v zásobníku volání celé). V rámci sloupce **úlohy** také můžete zobrazit metodu, která byla předána do úlohy. Jinými slovy, počátečním bodem.

     Libovolný sloupec lze seřadit. Všimněte si, že piktogram setřídit, která označuje sloupec pro řazení a směr. Můžete také změnit uspořádání sloupců jejich přetažením doleva nebo doprava.

     Žlutá šipka označuje aktuální úlohu. Dvojitým kliknutím na úlohu nebo v místní nabídce můžete přepnout úkoly. Při přepínání úloh podkladové vlákno nebude aktuální a ostatní okna se aktualizují.

     Při ruční přepínání z jednoho úkolu do druhého, žlutá šipka se přesune, ale bílé šipku stále zobrazuje úlohy, která způsobila přerušení ladicího programu.

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Chcete-li pokračovat v provádění, dokud druhý zarážku

1. Chcete-li pokračovat v provádění, dokud nebude dosaženo druhé zarážce, v nabídce **ladění** klikněte na tlačítko **pokračovat**.

     Dříve se ve sloupci **stav** zobrazily všechny úkoly jako aktivní, ale teď se zablokují dva z těchto úloh. Úkoly mohou být blokovány mnoho různých důvodů. Ve sloupci **stav** najeďte myší na čekající úlohu a zjistěte, proč je zablokovaná. Na následujícím obrázku je například úloha 3 čekání na úloha 4.

     ![Dvě čekající úlohy v okně úlohy](../debugger/media/pdb_walkthrough_7.png "PDB_Walkthrough_7")

     Úloha 4, pak čeká na monitorování vlastněný vláknem přiřazen k úloze 2. (Klikněte pravým tlačítkem na řádek záhlaví a vyberte **sloupce** > **přiřazení vlákna** pro zobrazení hodnoty přiřazení vlákna pro úkol 2).

     ![Úloha a popisek čekání v okně úlohy](../debugger/media/pdb_walkthrough_7a.png "PDB_Walkthrough_7A")

     Úkol můžete označit kliknutím na příznak v prvním sloupci okna **úlohy** .

     Pomocí příznaku můžete sledovat úlohy mezi různými zarážkami ve stejné relaci ladění nebo filtrovat úkoly, jejichž zásobníky volání se zobrazují v okně **paralelní zásobníky** .

     Při předchozím použití okna **paralelní zásobníky** jste zobrazili vlákna aplikace. Zobrazte okno **paralelní zásobníky** znovu, ale tentokrát se zobrazí úlohy aplikace. Provedete to tak, že vyberete **úkoly** v poli vlevo nahoře. Následující obrázek znázorňuje zobrazení úlohy.

     ![Zobrazení úlohy v okně paralelní zásobníky](../debugger/media/pdb_walkthrough_8.png "PDB_Walkthrough_8")

     Vlákna, která aktuálně nespouštějí úlohy, se nezobrazí v zobrazení úlohy okna **paralelní zásobníky** . Kromě toho pro vlákna, které jsou spouštěny úkoly, některých rámců zásobníku, které nejsou relevantní pro úlohy jsou filtrovány ze horní a dolní část zásobníku.

     Znovu zobrazte okno **úlohy** . Klikněte pravým tlačítkem na libovolné záhlaví sloupce, chcete-li zobrazit místní nabídku pro sloupec.

     V místní nabídce můžete použít k přidání nebo odebrání sloupců. Například není vybraný sloupec domény aplikace; Proto se nezobrazí v seznamu. Klikněte na **Nadřazená položka**. **Nadřazený** sloupec se zobrazí bez hodnot pro žádnou ze čtyř úkolů.

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Chcete-li pokračovat v provádění, dokud třetí zarážku

1. Chcete-li pokračovat v provádění, dokud nebude dosaženo třetí zarážce, v nabídce **ladění** klikněte na tlačítko **pokračovat**.

     Nový úkol, úloha 5, je nyní spuštěna a úloha 4 je nyní čekání. Můžete se podívat, proč na čekající úkol ve **stavovém** okně najede myší. V **nadřazeném** sloupci si všimněte, že úloha 4 představuje nadřazený úkol 5.

     Chcete-li lépe vizualizovat vztah nadřazený-podřízený, klikněte pravým tlačítkem myši na řádek záhlaví sloupce a poté klikněte na položku **nadřazené podřízené zobrazení**. Měli byste vidět na následujícím obrázku.

     ![Nadřazené&#45;podřízené zobrazení v okně úlohy](../debugger/media/pdb_walkthrough_9.png "PDB_Walkthrough_9")

     Všimněte si, že úloha 4 a úloha 5 jsou spuštěny ve stejném vlákně (zobrazení sloupce **přiřazení vlákna** , je-li skrytý). Tyto informace nejsou zobrazeny v okně **vlákna** . Podívejte se, že se jedná o další výhody okna **úlohy** . Potvrďte to tak, že zobrazíte okno **paralelní zásobníky** . Ujistěte se, že prohlížíte **úkoly**. Vyhledejte úkoly 4 a 5 dvojitým kliknutím na ně v okně **úlohy** . V takovém případě se modrý zvýraznění v okně **paralelní zásobníky** aktualizuje. Můžete také vyhledat úlohy 4 a 5 kontrolou tlačítek v okně **paralelní zásobníky** .

     ![Zobrazení úloh v paralelních zásobnících okna](../debugger/media/pdb_walkthrough_9a.png "PDB_Walkthrough_9A")

     V okně **paralelní zásobníky** klikněte pravým tlačítkem na S. P a pak klikněte na **Přejít ke vláknu**. V okně se přepne do zobrazení vláken a odpovídající rámec je příkaz v zobrazení. Obě úlohy si můžete prohlédnout ve stejném vlákně.

     ![Zvýrazněné vlákno v zobrazení vláken](../debugger/media/pdb_walkthrough_9b.png "PDB_Walkthrough_9B")

     Toto je další výhodou zobrazení úlohy v okně **paralelní zásobníky** ve srovnání s oknem **vláken** .

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Chcete-li pokračovat v provádění, dokud čtvrtý zarážku

1. Chcete-li pokračovat v provádění, dokud nebude dosaženo třetí zarážce, v nabídce **ladění** klikněte na tlačítko **pokračovat**. Kliknutím na záhlaví sloupce **ID** seřadíte podle ID. Měli byste vidět na následujícím obrázku.

     ![Čtyři stavy úloh v paralelních zásobnících okna](../debugger/media/pdb_walkthrough_10.png "PDB_Walkthrough_10")

     Protože byla dokončena úloha 5, se už nezobrazuje. Pokud se nejedná o případ na vašem počítači a zablokování se nezobrazuje, proveďte krok jednou stisknutím klávesy **F11**.

     Úloha 3 a úloha 4 jsou nyní čeká na sebe navzájem a jsou zablokované. Existují také 5 nových úkolů, které jsou podřízené úlohy 2 a nyní jsou naplánovány. Naplánované úlohy jsou uvedeny úlohy, které byly zahájeny v kódu, ale ještě nebyla spuštěna. Proto jsou sloupce přiřazení **umístění** a **vlákna** prázdné.

     Znovu zobrazte okno **paralelní zásobníky** . Záhlaví každého pole má popisek, který ukazuje názvy a ID vlákna. Přepněte do zobrazení úlohy v okně **paralelní zásobníky** . Najeďte myší na záhlaví zobrazíte ID úkolu a název a stav úlohy, jak je znázorněno na následujícím obrázku.

     ![Popisek záhlaví v okně paralelní zásobníky](../debugger/media/pdb_walkthrough_11.png "PDB_Walkthrough_11")

     Úlohy můžete seskupovat podle sloupce. V okně **úlohy** klikněte pravým tlačítkem myši na záhlaví sloupce **stav** a pak klikněte na možnost **Seskupit podle stav**. Následující ilustrace znázorňuje okno **úlohy** seskupené podle stavu.

     ![Seskupené úkoly v okně úlohy](../debugger/media/pdb_walkthrough_12.png "PDB_Walkthrough_12")

     Můžete taky Seskupit podle libovolného sloupce. Seskupení úlohami můžete soustředit na dílčí úkoly. Každá skupina sbalitelné obsahuje počet položek, které jsou seskupeny dohromady.

     Poslední funkcí okna **úlohy** k prohlédnutí je místní nabídka, která se zobrazí po kliknutí pravým tlačítkem myši na úlohu.

     V místní nabídce se zobrazí různé příkazy, v závislosti na stavu úlohy. Příkazy mohou zahrnovat **kopírování**, **Výběr všech**, **hexadecimálního zobrazení**, **Přepnutí na úlohu**, **zablokování přiřazeného vlákna**, **zablokování všech vláken, ale toto**a **příznak**.

     Můžete ukotvit podkladové vlákno úlohu nebo úlohy, nebo můžete zablokovat všechna vlákna kromě přiřazená vlákna. Zmrazené vlákno je v okně **úlohy** reprezentováno, protože je v okně **vlákna** pomocí modré ikony *pauzy* .

## <a name="summary"></a>Souhrn
 Tento názorný postup ukázal okna **paralelních úkolů** a **paralelních zásobníků** pro ladicí program. Používání těchto oken na skutečné projekty, které používají kódy s více vlákny. Můžete zkoumat, paralelní kód napsaný v C++, C# nebo Visual Basic.

## <a name="see-also"></a>Viz také
- [Ladění vícevláknových aplikací](../debugger/walkthrough-debugging-a-parallel-application.md)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
- [Paralelní programování](/dotnet/standard/parallel-programming/index)
- [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime)
- [Použití okna Paralelní zásobníky](../debugger/using-the-parallel-stacks-window.md)
- [Použití okna úloh](../debugger/using-the-tasks-window.md)