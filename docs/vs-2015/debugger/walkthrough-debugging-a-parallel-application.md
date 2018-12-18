---
title: 'Návod: Ladění paralelní aplikace | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f7c580ed07198f47776ee1edbad23918c03d564
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776717"
---
# <a name="walkthrough-debugging-a-parallel-application"></a>Návod: Ladění paralelní aplikace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak používat **paralelní úlohy** a **paralelní zásobníky** ladění paralelní aplikace systému windows. Tato okna vám pomůžou pochopit a chování za běhu kódu, který se používá ověření [Task Parallel Library (TPL)](http://msdn.microsoft.com/library/b8f99f43-9104-45fd-9bff-385a20488a23) nebo [Concurrency Runtime](http://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c). Tento názorný postup obsahuje ukázkový kód, který má integrovanou zarážky. Poté, co kód přestane fungovat, návodu ukazuje způsob použití **paralelní úlohy** a **paralelní zásobníky** windows jej prozkoumat.  
  
 Tento návod vás naučí tyto úlohy:  
  
-   Jak zobrazit zásobníky volání všech vláken v jednom zobrazení.  
  
-   Postup zobrazení seznamu `System.Threading.Tasks.Task` instancí, které jsou vytvořeny ve vaší aplikaci.  
  
-   Jak zobrazit skutečné volání zásobníků úkolů místo vlákna.  
  
-   Jak se orientovat na kód z **paralelní úlohy** a **paralelní zásobníky** systému windows.  
  
-   Jak windows zvládnout škálování prostřednictvím seskupování, přibližování a další související funkce.  
  
## <a name="prerequisites"></a>Požadavky  
 Tento návod předpokládá, že **pouze můj kód** je povolená. Na **nástroje** nabídky, klikněte na tlačítko **možnosti**, rozbalte **ladění** uzlu, vyberte **Obecné**a pak vyberte **povolit Pouze můj kód (pouze spravované)**. Pokud tato funkce není nastavený, můžete nadále používat Tento názorný postup, ale vaše výsledky můžou lišit od ilustrací.  
  
## <a name="c-sample"></a>Ukázka v jazyce C#  
 Pokud použitím této ukázky jazyka C# Tento názorný Průvodce také předpokládá, že externí kód je skrytá. Určí, zda se zobrazí externí kód, klikněte pravým tlačítkem myši **název** záhlaví tabulky **zásobník volání** okna a poté zaškrtněte nebo zrušte **zobrazit externí kód**. Pokud tato funkce není nastavený, můžete nadále používat Tento názorný postup, ale vaše výsledky můžou lišit od ilustrací.  
  
## <a name="c-sample"></a>Ukázky jazyka C++  
 Pokud používáte ukázkou jazyka C++, můžete ignorovat odkazy na externí kód v tomto tématu. Externí kód vztahuje pouze na ukázky jazyka C#.  
  
## <a name="illustrations"></a>Obrázky  
 Na obrázcích v tomto tématu se zaznamenávají čtyřjádrový procesor počítače spuštěním ukázky jazyka C#. I když ostatní konfigurace můžete použít k dokončení tohoto návodu, obrázky můžou lišit od co se zobrazí ve vašem počítači.  
  
## <a name="creating-the-sample-project"></a>Vytvoření ukázkového projektu  
 Ukázkový kód v tomto názorném postupu se pro aplikaci, která nemá žádný účinek. Cílem je právě pochopit, jak pomocí nástroje systému windows pro ladění paralelní aplikace.  
  
#### <a name="to-create-the-sample-project"></a>K vytvoření ukázkového projektu  
  
1. V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.  
  
2. V **nainstalované šablony** podokně, vyberte buď Visual C#, Visual Basic nebo Visual C++. Pro spravované jazyky, ujistěte se, že [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] se zobrazí v seznamu rozhraní.  
  
3. Vyberte **konzolovou aplikaci** a potom klikněte na tlačítko **OK**. Zůstat v konfiguraci ladění, což je výchozí hodnota.  
  
4. Otevřete soubor kódu .cpp, .cs nebo .vb v projektu. Odstraňte její obsah, chcete-li vytvořit prázdný soubor kódu.  
  
5. Vložte následující kód pro zvolený jazyk do souboru prázdný kód.  
  
   [!code-cpp[Debugger#1](../snippets/cpp/VS_Snippets_Misc/debugger/cpp/beta2_native.cpp#1)]
   [!code-csharp[Debugger#1](../snippets/csharp/VS_Snippets_Misc/debugger/cs/s.cs#1)]
   [!code-vb[Debugger#1](../snippets/visualbasic/VS_Snippets_Misc/debugger/vb/module1.vb#1)]  
  
6. Na **souboru** nabídky, klikněte na tlačítko **Uložit vše**.  
  
7. Na **sestavení** nabídky, klikněte na tlačítko **znovu sestavit řešení**.  
  
    Všimněte si, že existují čtyři volání `Debugger.Break` (`DebugBreak` v C++ ukázce) proto není potřeba vložit zarážky; jednoduše spuštěním aplikace způsobí jeho přerušení v ladicím programu až čtyřikrát.  
  
## <a name="using-the-parallel-stacks-window-threads-view"></a>Použití paralelních zásobníků okna: zobrazení vlákna  
 Na **ladění** nabídky, klikněte na tlačítko **spustit ladění**. Počkejte první zarážce.  
  
#### <a name="to-view-the-call-stack-of-a-single-thread"></a>Chcete-li zobrazit zásobník volání z jednoho vlákna  
  
1.  Na **ladění** nabídky, přejděte k **Windows** a potom klikněte na tlačítko **vlákna**. Ukotvit **vlákna** okno v dolní části sady Visual Studio.  
  
2.  Na **ladění** nabídky, přejděte k **Windows** a potom klikněte na tlačítko **zásobník volání**. Ukotvit **zásobník volání** okno v dolní části sady Visual Studio.  
  
3.  Klikněte dvakrát na vlákno v **vlákna** okna, aby byl aktuální. Aktuální vlákna mají žlutá šipka. Při změně aktuálního vlákna, zobrazí se jeho zásobník volání v **zásobník volání** okna.  
  
#### <a name="to-examine-the-parallel-stacks-window"></a>Prozkoumat okna paralelní zásobníky  
  
1.  Na **ladění** nabídky, přejděte k **Windows** a potom klikněte na tlačítko **paralelní zásobníky**. Ujistěte se, že **vlákna** je vybraná pole v levém horním rohu.  
  
     S použitím **paralelní zásobníky** můžete zobrazit více zásobníky volání ve stejnou dobu v jednom zobrazení. Je vidět na následujícím obrázku **paralelní zásobníky** okno výše **zásobník volání** okna.  
  
     ![Zobrazení okna paralelní zásobníky vlákna](../debugger/media/pdb-walkthrough-1.png "PDB_Walkthrough_1")  
  
     V jednom poli se zobrazí zásobník volání z hlavního vlákna a zásobníky volání pro čtyři vlákna jsou seskupené do jiného pole. Čtyři vlákna jsou seskupeny dohromady, protože jejich rámce zásobníku sdílet stejnou metodu kontexty; To znamená, že jsou ve stejné metody: `A`, `B`, a `C`. K zobrazení ID vlákna a názvy vláken, které sdílejí stejné pole, najeďte myší na záhlaví (**4 vlákna**). Aktuální vlákno se zobrazí tučně, jak je znázorněno na následujícím obrázku.  
  
     ![Popisek, který ukazuje názvy a ID vlákna](../debugger/media/pdb-walkthrough-1a.png "PDB_Walkthrough_1A")  
  
     Žlutá šipka označuje aktivní blok zásobníku aktuálního vlákna. Pokud chcete získat další informace, najeďte myší nad ním  
  
     ![Popisek tlačítka na aktivní blok zásobníku](../debugger/media/pdb-walkthrough-1b.png "PDB_Walkthrough_1B")  
  
     Můžete nastavit, kolik detailů chcete zobrazit pro rámce zásobníku (**názvů modulů**, **typy parametrů**, **názvy parametrů**, **hodnoty parametrů**, **Čísla řádků** a **posuny bajtů**) kliknutím pravým tlačítkem myši v **zásobník volání** okna.  
  
     Modré zvýraznění kolem pole označuje, že aktuální vlákno je součástí tohoto pole. Aktuální vlákno je také označeny tučně zásobníku v popisu. Pokud dvakrát kliknete na hlavní vlákno v okně vlákna, můžete sledovat, která modré zvýraznění v **paralelní zásobníky** okno přesune odpovídajícím způsobem.  
  
     ![Zvýrazněný hlavní vlákno v okna paralelní zásobníky](../debugger/media/pdb-walkthrough-1c.png "PDB_Walkthrough_1C")  
  
#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Chcete-li pokračovat v provádění, dokud druhý zarážku  
  
1.  Provádění pokračovat, dokud druhý dosažení zarážky, na **ladění** nabídky, klikněte na tlačítko **pokračovat**. Následující obrázek znázorňuje strom vlákno na druhý zarážce.  
  
     ![Paralelní zásobníky okno, které ukazuje mnoho větví](../debugger/media/pdb-walkthrough-2.png "PDB_Walkthrough_2")  
  
     Na první zarážce všechny čtyři vlákna absolvovanou z adresu S.A S.B S.C metod. Informace, které musí stále zobrazená v **paralelní zásobníky** okna, ale čtyři vlákna pokročila dále. Jeden z nich nadále S.D a potom S.E. Jiné nadále S.F S.G a S.H. Dvěma dalšími pokračování S.I a S.J a z existovat jeden z nich absolvovanou S.K a druhý nadále externí neuživatelský kód.  
  
     Například myší nad pole záhlaví, **1 vlákno** nebo **2 vláknech**, abyste si zobrazili vlákno ID vlákna. Při najetí myší nad rámec zásobníku zobrazíte vlákna ID a dalších podrobnostech rámce. Modré zvýraznění označuje aktuální vlákno a žlutá šipka označuje aktivní blok zásobníku aktuálního vlákna.  
  
     Ikona látky vláken (překrývající se modrý a červený waved řádky) označují aktivní zásobník snímků vlákny. V **zásobník volání** okna, dvakrát klikněte na panel S.B rámce přepínačů. **Paralelní zásobníky** okno označuje aktuální rámec zásobníku aktuálního vlákna s ikonou zelené šipky zakřivené.  
  
     V **vlákna** okně přepínat mezi vlákny a zda se zobrazila zpráva zobrazení **paralelní zásobníky** aktualizovat okno.  
  
     Můžete přepnout do jiného vlákna, nebo na jiný rámec z jiného vlákna, pomocí místní nabídky **paralelní zásobníky** okna. Například, klikněte pravým tlačítkem na S.J, přejděte na **přepnout na rámec**a potom klikněte na příkaz.  
  
     ![Paralelních zásobníků cesta provádění](../debugger/media/pdb-walkthrough-2b.png "PDB_Walkthrough_2B")  
  
     Klikněte pravým tlačítkem na S.C a přejděte na **přepnout na rámec**. Jeden z příkazů má zaškrtávací políčko, která indikuje rámec zásobníku aktuálního vlákna. Můžete přepnout na tento rámec stejné vlákna (zelená šipka se přesune) nebo můžete přepnout do jiného podprocesu (modré zvýraznění se přesune také). Následující obrázek znázorňuje podnabídky.  
  
     ![Zásobníky nabídky 2 možnosti v C je aktuální J](../debugger/media/pdb-walkthrough-3.png "PDB_Walkthrough_3")  
  
     Když metoda kontext je spojen s jedním zásobníku, zobrazí záhlaví pole **1 vlákno** a k němu můžete přepnout na něj poklikejte. Pokud dvakrát kliknete na metodu kontext, který má více než 1 blok s ním spojená, pak v nabídce automaticky otevře. Když najedete ukazatelem metoda kontextů, Všimněte si, že na černý trojúhelník na pravé straně. Kliknutím na tuto trojúhelník také zobrazí v místní nabídce.  
  
     Pro velké aplikace, které mají mnoho vláken můžete chtít zaměřit pouze podmnožinu vláken. **Paralelní zásobníky** okna můžete zobrazit zásobníky volání pouze pro vlákna s příznakem. Na panelu nástrojů klikněte na tlačítko **zobrazit pouze označená příznakem** tlačítko vedle pole se seznamem.  
  
     ![Prázdné okno paralelních zásobníků a popis](../debugger/media/pdb-walkthrough-3a.png "PDB_Walkthrough_3A")  
  
     Dále v **vlákna** okně příznak vlákna jednu po druhé podívejte, jak v zobrazily svých zásobníků volání **paralelní zásobníky** okna. Označit vlákna, použijte nabídku nebo první buňky vlákna. Klikněte na tlačítko **zobrazit pouze označená příznakem** tlačítka panelu nástrojů znovu a zobrazit všechna vlákna.  
  
#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Chcete-li pokračovat v provádění, dokud třetí zarážku  
  
1. Provádění pokračovat, dokud třetí dosažení zarážky, na **ladění** nabídky, klikněte na tlačítko **pokračovat**.  
  
    Při více vláken jsou ve stejné metody, ale nebyla na začátek zásobníku volání metody, metoda se zobrazí v různých polí. Příklad na aktuální zarážce je S.L, který v sobě obsahuje tři vlákna a zobrazí se tří polí. Dvakrát klikněte na panel j.  
  
    ![Cesta provedení v okna paralelní zásobníky](../debugger/media/pdb-walkthrough-3b.png "PDB_Walkthrough_3B")  
  
    Všimněte si, že S.L je tak, abyste viděli, kde se zobrazí tučně ve dvou polích. Pokud chcete zobrazit volání do S.L rámce, který a které snímků je volání, klikněte na tlačítko **přepnout zobrazení metody** tlačítko na panelu nástrojů. Následující obrázek znázorňuje přehled metody **paralelní zásobníky** okna.  
  
    ![Zobrazení metody v okna paralelní zásobníky](../debugger/media/pdw-walkthrough-4.png "PDW_Walkthrough_4")  
  
    Všimněte si, jak diagramu neseskupené na vybrané metodě a umístěna do své vlastní pole uprostřed zobrazení. Volané a volající zobrazí v horní a dolní části. Klikněte na tlačítko **přepnout zobrazení metody** tlačítka opustit tento režim.  
  
    Nabídku **paralelní zásobníky** okno má také následující další položky.  
  
   - **Hexadecimální zobrazení** přepíná čísel v popiscích mezi desetinných míst a šestnáctkové číslo.  
  
   - **Načíst informace o symbolech** a **nastavení symbolu** otevřete příslušné dialogových oknech.  
  
   - **Přejít ke zdrojovému kódu** a **přejít na zpětný překlad** přejděte v editoru na vybrané metody.  
  
   - **Zobrazit externí kód** zobrazí všechny snímky, i když nejsou v uživatelském kódu. Vyzkoušejte si to chcete zobrazit diagram rozšířit, aby odpovídala další snímky (která může být neaktivní, protože nemáte symboly pro ně).  
  
     Pokud máte velké diagramy a přejdete na další zarážku, můžete zobrazení tak, aby automaticky přejít na aktivní blok zásobníku aktuálního vlákna; To znamená, že vlákno, které první narazí zarážku. V **paralelní zásobníky** okno, ujistěte se, že **automaticky přejít na aktuální rámec zásobníku** nachází na panelu nástrojů.  
  
     ![Automatické procházení v okna paralelní zásobníky](../debugger/media/pdb-walkthrough-4a.png "PDB_Walkthrough_4A")  
  
2. Než budete pokračovat, v **paralelní zásobníky** okno, přejděte úplně vlevo a úplně dolů.  
  
#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Chcete-li pokračovat v provádění, dokud čtvrtý zarážku  
  
1.  Chcete-li obnovit spuštění, dokud čtvrtý dosažení zarážky, na **ladění** nabídky, klikněte na **pokračovat**.  
  
     Všimněte si, že jak autoscrolled zobrazení na místě. Přepnout vlákna v **vlákna** okno nebo přepínač zásobník snímků v **zásobník volání** okno a Všimněte si, že jak zobrazení vždy autoscrolls správný snímek. Vypnout **automaticky přejít na aktuální rámec nástroj** možnost a zobrazit rozdíl.  
  
     **Pohled z ptačí perspektivy** také pomáhá s velkých diagramů v **paralelní zásobníky** okna. Zobrazí se **pohled z ptačí perspektivy** kliknutím na tlačítko mezi posuvníků v pravém dolním rohu okna, jak je znázorněno na následujícím obrázku.  
  
     ![Zobrazení z ptačí perspektivy&#45;oční zobrazení okna paralelní zásobníky](../debugger/media/pdb-walkthrough-5.png "PDB_Walkthrough_5")  
  
     Můžete přesunout obdélník rychlé posouvání zobrazení diagramu.  
  
     Klikněte na prázdnou oblast na diagramu a přetáhněte ji na požadované místo je jiný způsob, jak přesunout diagramu vede libovolným směrem.  
  
     Chcete-li přiblížení a oddálení diagramu, stiskněte a podržte klávesu CTRL a kolečka myši přesunete. Alternativně klepněte na tlačítko lupy na panelu nástrojů a pak pomocí nástroje přiblížení.  
  
     ![Zásobníky v okna paralelní zásobníky v měřítku](../debugger/media/pdb-walkthrough-5a.png "PDB_Walkthrough_5A")  
  
     Můžete také zobrazit zásobníky shora dolů směrem místo zdola nahoru, kliknutím **nástroje** nabídky, kliknutím na **možnosti**a poté zaškrtněte nebo zrušte zaškrtnutí možnosti v části **ladění** uzlu.  
  
2.  Než budete pokračovat, na **ladění** nabídky, klikněte na tlačítko **Zastavit ladění** k ukončení provádění.  
  
## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>Použití okna paralelní úlohy a úkoly zobrazení okna paralelní zásobníky  
 Doporučujeme dokončení předchozích postupů, než budete pokračovat.  
  
#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>Restartujte aplikaci až k první zarážce přístupů  
  
1.  Na **ladění** nabídky, klikněte na tlačítko **spustit ladění** a počkejte první zarážce.  
  
2.  Na **ladění** nabídky, přejděte k **Windows** a potom klikněte na tlačítko **vlákna**. Ukotvit **vlákna** okno v dolní části sady Visual Studio.  
  
3.  Na **ladění** nabídky, přejděte k **Windows** a klikněte na tlačítko **zásobník volání**. Ukotvit **zásobník volání** okno v dolní části sady Visual Studio.  
  
4.  Klikněte dvakrát na vlákno v **vlákna** okna je aktuální. Aktuální vlákna mají žlutou šipkou. Při změně aktuální vlákno, se aktualizují ostatní okna. V dalším kroku prozkoumáme úlohy.  
  
5.  Na **ladění** nabídky, přejděte k **Windows** a potom klikněte na tlačítko **paralelní úlohy**. Je vidět na následujícím obrázku **paralelní úlohy** okna.  
  
     ![Čtyři spouštění úloh v okno paralelní úkoly](../debugger/media/pdw-walkthrough-6.png "PDW_Walkthrough_6")  
  
     Pro každý úkol spuštěný si můžete přečíst jeho ID, která je vrácena vlastnost se stejným názvem, ID a název vlákna, na kterém běží, jeho umístění (ukazatel myši tuto zobrazí popis tlačítka, který má v zásobníku volání celé). Také **úloh** sloupce, můžete zobrazit metody, která byla předána do úkolu; jinými slovy, výchozím bodem.  
  
     Libovolný sloupec lze seřadit. Všimněte si, že piktogram setřídit, která označuje sloupec pro řazení a směr. Můžete také změnit uspořádání sloupců jejich přetažením doleva nebo doprava.  
  
     Žlutá šipka označuje aktuální úlohu. Dvojitým kliknutím na úlohu nebo v místní nabídce můžete přepnout úkoly. Při přepínání úloh podkladové vlákno nebude aktuální a ostatní okna se aktualizují.  
  
     Při ruční přepínání z jednoho úkolu do druhého, žlutá šipka se přesune, ale bílé šipku stále zobrazuje úlohy, která způsobila přerušení ladicího programu.  
  
#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Chcete-li pokračovat v provádění, dokud druhý zarážku  
  
1.  Provádění pokračovat, dokud druhý dosažení zarážky, na **ladění** nabídky, klikněte na tlačítko **pokračovat**.  
  
     Dříve **stav** sloupec jsme si ukázali, všechny úlohy jako spuštění, ale teď dvě úlohy čekají na přiřazení. Úkoly mohou být blokovány mnoho různých důvodů. V **stav** sloupce, podržte ukazatel myši nad úkol čekání se dozvíte, proč je zablokovaný. Na následujícím obrázku je například úloha 3 čekání na úloha 4.  
  
     ![Dvě úlohy čekání v okno paralelní úkoly](../debugger/media/pdb-walkthrough-7.png "PDB_Walkthrough_7")  
  
     Úloha 4, pak čeká na monitorování vlastněný vláknem přiřazen k úloze 2.  
  
     ![Čekání na úkol a popisek v okně úlohy](../debugger/media/pdb-walkthrough-7a.png "PDB_Walkthrough_7A")  
  
     Úlohu můžete označit příznakem, kliknutím na příznak v prvním sloupci **paralelní úlohy** okna.  
  
     Označování můžete použít ke sledování úkolů mezi různé zarážek v rámci jedné relace ladění nebo chcete-li filtrovat úlohy, jejichž zásobníky volání jsou uvedeny v **paralelní zásobníky** okna.  
  
     Pokud jste použili **paralelní zásobníky** okno dříve, můžete zobrazit vlákna aplikace. Zobrazení **paralelní zásobníky** okno znovu, tentokrát ale zobrazit úlohy aplikací. To udělat tak, že vyberete **úlohy** v okně na levém horním rohu. Následující obrázek znázorňuje zobrazení úlohy.  
  
     ![Zobrazení okna paralelní zásobníky vlákna](../debugger/media/pdb-walkthrough-8.png "PDB_Walkthrough_8")  
  
     Vlákna, která nejsou aktuálně provádění úlohy se nezobrazují v zobrazení úlohy **paralelní zásobníky** okna. Kromě toho pro vlákna, které jsou spouštěny úkoly, některých rámců zásobníku, které nejsou relevantní pro úlohy jsou filtrovány ze horní a dolní část zásobníku.  
  
     Zobrazení **paralelní úlohy** znovu okno. Klikněte pravým tlačítkem na libovolné záhlaví sloupce, chcete-li zobrazit místní nabídku pro sloupec.  
  
     ![Zobrazit nabídku v okno paralelní úkoly](../debugger/media/pdb-walkthrough-8a.png "PDB_Walkthrough_8A")  
  
     V místní nabídce můžete použít k přidání nebo odebrání sloupců. Například není vybraný sloupec domény aplikace; Proto se nezobrazí v seznamu. Klikněte na tlačítko **nadřazené**. **Nadřazené** se zobrazí sloupec bez hodnot pro všechny čtyři úkoly.  
  
#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Chcete-li pokračovat v provádění, dokud třetí zarážku  
  
1.  Provádění pokračovat, dokud třetí dosažení zarážky, na **ladění** nabídky, klikněte na tlačítko **pokračovat**.  
  
     Nový úkol, úloha 5, je nyní spuštěna a úloha 4 je nyní čekání. Můžete zobrazit důvod, proč tak, že najedete myší úkol čekání v **stav** okna. V **nadřazené** sloupce, Všimněte si, že úloha 4 je nadřazená úloha 5.  
  
     Lepší vizualizace hierarchických vztahů, klikněte pravým tlačítkem myši **nadřazené** záhlaví sloupce a pak klikněte na tlačítko **nadřazeného a podřízeného prvku**. Měli byste vidět na následujícím obrázku.  
  
     ![Nadřazené&#45;podřízené zobrazení, v okno paralelní úkoly](../debugger/media/pdb-walkthrough-9.png "PDB_Walkthrough_9")  
  
     Všimněte si, že úloha 4 a 5. úkol běží ve stejném vlákně. Tyto informace se nezobrazí v **vlákna** okno; zobrazují, tady je Další výhodou **paralelní úlohy** okna. Chcete-li to ověřit, zobrazte **paralelní zásobníky** okna. Ujistěte se, že si prohlížíte **úlohy**. Najít úlohy 4 a 5 dvojitým kliknutím v **paralelní úlohy** okna. Když to uděláte, modré zvýraznění **paralelní zásobníky** aktualizovat okno. Můžete také vyhledat úlohy 4 a 5 tím, že kontroluje popisky na **paralelní zásobníky** okna.  
  
     ![Zobrazení v okna paralelní zásobníky úlohy](../debugger/media/pdb-walkthrough-9a.png "PDB_Walkthrough_9A")  
  
     V **paralelní zásobníky** okna, klikněte pravým tlačítkem na S.P a potom klikněte na **přejít na vlákno**. V okně se přepne do zobrazení vláken a odpovídající rámec je příkaz v zobrazení. Obě úlohy si můžete prohlédnout ve stejném vlákně.  
  
     ![Zvýrazněný vlákna v zobrazení vláken](../debugger/media/pdb-walkthrough-9b.png "PDB_Walkthrough_9B")  
  
     Toto je Další výhodou zobrazení úlohy **paralelní zásobníky** okno, ve srovnání s **vlákna** okna.  
  
#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Chcete-li pokračovat v provádění, dokud čtvrtý zarážku  
  
1.  Provádění pokračovat, dokud třetí dosažení zarážky, na **ladění** nabídky, klikněte na tlačítko **pokračovat**. Klikněte na tlačítko **ID** záhlaví sloupce seřadíte položky podle ID. Měli byste vidět na následujícím obrázku.  
  
     ![Čtyři úlohy státy v okna paralelní zásobníky](../debugger/media/pdb-walkthrough-10.png "PDB_Walkthrough_10")  
  
     Protože byla dokončena úloha 5, se už nezobrazuje. Pokud to není případ v počítači a k zablokování nezobrazuje, krok stisknutím klávesy F11 jednou.  
  
     Úloha 3 a úloha 4 jsou nyní čeká na sebe navzájem a jsou zablokována. Existují také 5 nových úkolů, které jsou podřízené úlohy 2 a nyní jsou naplánovány. Naplánované úlohy jsou uvedeny úlohy, které byly zahájeny v kódu, ale ještě nebyla spuštěna. Proto jejich **umístění** a **vlákna přiřazení** sloupce jsou prázdné.  
  
     Zobrazení **paralelní zásobníky** znovu okno. Záhlaví každého pole má popisek, který ukazuje názvy a ID vlákna. Přepnout do zobrazení úlohy v **paralelní zásobníky** okna. Najeďte myší na záhlaví zobrazíte ID úkolu a název a stav úlohy, jak je znázorněno na následujícím obrázku.  
  
     ![Popisek záhlaví v okna paralelní zásobníky](../debugger/media/pdb-walkthrough-11.png "PDB_Walkthrough_11")  
  
     Úlohy můžete seskupovat podle sloupce. V **paralelní úlohy** okna, klikněte pravým tlačítkem na **stav** záhlaví sloupce a pak klikněte na tlačítko **Seskupit podle stavu**. Je vidět na následujícím obrázku **paralelní úlohy** okno seskupených podle stavu.  
  
     ![Seskupených úkolů v okno paralelní úkoly](../debugger/media/pdb-walkthrough-12.png "PDB_Walkthrough_12")  
  
     Můžete taky Seskupit podle libovolného sloupce. Seskupení úlohami můžete soustředit na dílčí úkoly. Každá skupina sbalitelné obsahuje počet položek, které jsou seskupeny dohromady. Všechny položky ve skupině můžete také rychle příznak kliknutím **příznak** tlačítko vpravo od **sbalit** tlačítko.  
  
     ![Seskupené zásobníky v okna paralelní zásobníky](../debugger/media/pdb-walkthrough-12a.png "PDB_Walkthrough_12A")  
  
     Poslední součástí **paralelní úlohy** okno k prozkoumání je místní nabídky, která se zobrazí, když kliknete pravým tlačítkem na úlohu.  
  
     ![Místní nabídce v paralelních úlohy](../debugger/media/pdb-walkthrough-12b.png "PDB_Walkthrough_12B")  
  
     V místní nabídce se zobrazí různé příkazy, v závislosti na stavu úlohy. Může zahrnovat příkazy **kopírování**, **Vybrat vše**, **hexadecimální zobrazení**, **přejít k úloze**, **zablokovat přiřazené Vlákno**, **pozastavit všechna vlákna kromě to**, a **uvolnit přiřazené vlákno**, a **příznak**.  
  
     Můžete ukotvit podkladové vlákno úlohu nebo úlohy, nebo můžete zablokovat všechna vlákna kromě přiřazená vlákna. Zmrazené vlákno je vyjádřena v **paralelní úlohy** je okno, jako je **vlákna** okno podle modrý *pozastavit* ikonu.  
  
## <a name="summary"></a>Souhrn  
 Tento názorný postup jsme vám ukázali **paralelní úlohy** a **paralelní zásobníky** ladicího programu systému windows. Používání těchto oken na skutečné projekty, které používají kódy s více vlákny. Můžete zkoumat, paralelní kód napsaný v C++, C# nebo Visual Basic.  
  
## <a name="see-also"></a>Viz také  
 [Ladění vícevláknových aplikací](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Základy ladicího programu](../debugger/debugger-basics.md)   
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)   
 [Paralelní programování](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [Concurrency Runtime](http://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)   
 [Použití okna paralelní zásobníky](../debugger/using-the-parallel-stacks-window.md)   
 [Použití okna úloh](../debugger/using-the-tasks-window.md)



