---
title: 'Návod: vytváření, úpravy a údržba programového testu UI | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: f7c25ba7-5c9c-455b-9242-701cda56f90c
caps.latest.revision: 43
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d14de396e24874f39a09172a483ebef81a5886f2
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851233"
---
# <a name="walkthrough-creating-editing-and-maintaining-a-coded-ui-test"></a>Návod: Vytváření, upravování a údržba programového testu UI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto návodu vytvoříte jednoduchou aplikaci Windows Presentation Foundation (WPF) pro demonstraci vytvoření, úpravy a správy programového testu uživatelského rozhraní. Návod poskytuje řešení pro opravu testů, které byly poškozeny různými chybami časování a refaktoringem ovládacích prvků.

## <a name="prerequisites"></a>Požadavky
 Přitom budete potřebovat:

- Visual Studio Enterprise

### <a name="create-a-simple-wpf-application"></a>Vytvoření jednoduché aplikace WPF

1. V nabídce **soubor** přejděte na příkaz **Nový**a vyberte možnost **projekt**.

     **Nový projekt** zobrazí se dialogové okno.

2. V podokně **nainstalováno** rozbalte položku **Visual C#** a pak vyberte možnost **desktopová plocha systému Windows**.

3. V prostředním podokně ověřte, že rozevírací seznam cílové rozhraní je nastaven na **.NET Framework 4,5**.

4. V prostředním podokně vyberte šablonu **aplikace WPF** .

5. Do textového pole **název** zadejte **aplikaci SimpleWPFApp**.

6. Zvolte složku, do které bude projekt uložen. Do textového pole **umístění** zadejte název složky.

7. Vyberte **OK**.

     WPF Designer pro sadu Visual Studio otevře a zobrazí hlavní okno MainWindow projektu.

8. Pokud není panel nástrojů otevřen, otevřete jej. Zvolte nabídku **zobrazení** a pak zvolte možnost **Sada nástrojů**.

9. V části **všechny ovládací prvky WPF** přetáhněte **tlačítko**, **CheckBox** a ovládací prvek **ProgressBar** na MainWindow na návrhové ploše.

10. Vyberte ovládací prvek Tlačítko. V okno Vlastnosti změňte hodnotu vlastnosti **název** z \<bez názvu > na Button1. Pak změňte hodnotu vlastnosti **obsah** z tlačítka na spustit.

11. Vyberte ovládací prvek Indikátor průběhu. V okno Vlastnosti změňte hodnotu vlastnosti **název** z \<bez názvu > na ProgressBar1. Pak změňte hodnotu vlastnosti **Maximum** z **100** na **10000**.

12. Vyberte ovládací prvek Zaškrtávací políčko. V okno Vlastnosti změňte hodnotu vlastnosti **název** z \<bez názvu > na možnost CheckBox1 a zrušte zaškrtnutí vlastnosti **Nepovoleno** .

     ![Jednoduchá aplikace WPF](../test/media/codedui-wpfapp.png "CodedUI_WPFApp")

13. Dvakrát klikněte na ovládací prvek tlačítko a přidejte obslužnou rutinu události Click.

     V editoru kódu se zobrazí MainWindow.xmal.cs s kurzorem v nové metodě button1_Click.

14. V horní části třídy hlavního okna MainWindow přidejte delegáta. Delegát bude použit pro indikátor průběhu. Chcete-li přidat delegáta, přidejte následující kód:

    ```csharp
    public partial class MainWindow : Window
    {
            private delegate void ProgressBarDelegate(System.Windows.DependencyProperty dp, Object value);

        public MainWindow()
        {

            InitializeComponent();
        }

    ```

15. V metodě button1_Click přidejte následující kód:

    ```csharp
    private void button1_Click(object sender, RoutedEventArgs e)
    {
        double progress = 0;

        ProgressBarDelegate updatePbDelegate =
            new ProgressBarDelegate(progressBar1.SetValue);

        do
        {
            progress ++;

            Dispatcher.Invoke(updatePbDelegate,
                System.Windows.Threading.DispatcherPriority.Background,
                new object[] { ProgressBar.ValueProperty, progress });
            progressBar1.Value = progress;
        }
        while (progressBar1.Value != progressBar1.Maximum);

        checkBox1.IsEnabled = true;
    }

    ```

16. Uložte soubor.

### <a name="verify-the-wpf-application-runs-correctly"></a>Ověření správného běhu aplikace WPF

1. V nabídce **ladění** vyberte **Spustit ladění** nebo stiskněte klávesu **F5**.

2. Všimněte si, že je ovládací prvek zaškrtávací políčko zakázán. Klikněte na tlačítko **Spustit**.

     Během několika sekund by měl indikátor průběhu ukazovat 100 %.

3. Nyní můžete zaškrtnout ovládací prvek zaškrtávací políčko.

4. Ukončete aplikaci SimpleWPFApp.

### <a name="create-and-run-a-coded-ui-test-for-simplewpfapp"></a>Vytvoření a spuštění programového testu uživatelského rozhraní pro aplikaci SimpleWPFApp

1. Vyhledejte aplikaci aplikaci SimpleWPFApp, kterou jste vytvořili dříve. Ve výchozím nastavení se aplikace nachází v umístění C:\Users\\< uživatelské jméno\>\Documents\Visual Studio \<verze > \Projects\SimpleWPFApp\SimpleWPFApp\bin\Debug\SimpleWPFApp.exe

2. Vytvořte pro aplikaci SimpleWPFApp zástupce na ploše. Klikněte pravým tlačítkem na aplikaci SimpleWPFApp. exe a vyberte **Kopírovat**. Na ploše klikněte pravým tlačítkem myši a vyberte možnost **Vložit zástupce**.

    > [!TIP]
    > Zástupce aplikace usnadňuje přidávání nebo úpravu programových testů uživatelského rozhraní pro vaši aplikaci, protože umožňuje rychlé spuštění aplikace.

3. V Průzkumník řešení klikněte pravým tlačítkem myši na řešení, vyberte možnost **Přidat** a poté vyberte možnost **Nový projekt**.

     Zobrazí se dialogové okno **Přidat nový projekt** .

4. V podokně **nainstalováno** rozbalte položku **Visual C#** a pak vyberte možnost **test**.

5. V prostředním podokně vyberte šablonu **projektu programový test uživatelského rozhraní** .

6. Vyberte **OK**.

     V Průzkumník řešení do vašeho řešení se přidá nový projekt programového testu UI s názvem **CodedUITestProject1** .

     Zobrazí se dialogové okno **generovat kód pro programový test uživatelského rozhraní** .

7. Vyberte možnosti **záznamu akce, upravit mapu uživatelského rozhraní nebo přidat kontrolní výrazy** a zvolte **OK**.

     Zobrazí se nástroj UIMap – Tvůrce programového testu uživatelského rozhraní a okno sady Visual Studio je minimalizováno.

     Další informace o možnostech v dialogovém okně naleznete v tématu vytváření programových [testů uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).

8. Vyberte možnost **Spustit záznam** na UIMap – Tvůrce programového testu uživatelského rozhraní.

     ![Spustit záznam](../test/media/cuit-builder-record.png "CUIT_Builder_Record")

     V případě potřeby můžete nahrávání pozastavit, například pokud se budete muset zabývat příchozí poštou.

     ![Pozastavit záznam](../test/media/cuit.png "CUIT_")

    > [!WARNING]
    > Budou zaznamenány všechny akce prováděné na ploše. Pozastaví nahrávání, pokud provádíte akce, které mohou vést k zahrnutí citlivých dat do záznamu.

9. Spusťte aplikaci SimpleWPFApp pomocí zástupce na ploše.

     Stejně jako dřív si všimněte, že je ovládací prvek zaškrtávací políčko zakázaný.

10. V aplikaci SimpleWPFApp klikněte na tlačítko **Spustit**.

     Během několika sekund by měl indikátor průběhu ukazovat 100 %.

11. Zaškrtněte políčko u ovládacího prvku zaškrtávací políčko, které je nyní povoleno.

12. Ukončete aplikaci SimpleWPFApp.

13. V nástroji Tvůrce programového testu uživatelského rozhraní UIMap vyberte **generovat kód**.

14. Do pole název metody zadejte **SimpleAppTest** a klikněte na **Přidat a generovat**. Během několika sekund se programový test uživatelského rozhraní zobrazí a přidá k řešení.

15. Ukončete nástroj UIMap – Tvůrce programového testu UI.

     V Editoru kódu se zobrazí soubor CodedUITest1.cs.

16. Uložte projekt.

### <a name="run-the-coded-ui-test"></a>Spuštění programového testu uživatelského rozhraní

1. V nabídce **test** zvolte možnost **okna** a pak zvolte možnost **Průzkumník testů**.

2. V nabídce **sestavení** klikněte na příkaz **Sestavit řešení**.

3. V souboru CodedUITest1.cs vyhledejte metodu **metodu CodedUITestMethod** , klikněte pravým tlačítkem myši a vyberte možnost **Spustit testy**nebo spusťte test z Průzkumníka testů.

     V průběhu programového testu uživatelského rozhraní je zobrazena aplikace SimpleWPFApp. Provádí kroky, které jste učinili v předchozí proceduře. Pokud se však test pokusí zaškrtnout políčko ovládacího prvku zaškrtávací políčko, okno Výsledky testů zobrazí, že test se nezdařil. Důvodem je, že test se pokusí vybrat zaškrtávací políčko, ale nevíte, že je ovládací prvek zaškrtávací políčko zakázán, dokud indikátor průběhu není 100% dokončeno. Toto a podobné problémy můžete opravit pomocí různých `UITestControl.WaitForControlXXX()` metod, které jsou k dispozici pro programové testování uživatelského rozhraní. Následující postup demonstruje použití metody `WaitForControlEnabled()` k opravě problému, který způsobil selhání tohoto testu. Další informace najdete v tématu [vytváření programových testů uživatelského rozhraní, které čekají na konkrétní události během přehrávání](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

### <a name="edit-and-rerun-the-coded-ui-test"></a>Úprava a opětovné spuštění programového testu uživatelského rozhraní

1. V okně Průzkumník testů vyberte neúspěšný test a v části **trasování zásobníku** zvolte první odkaz na **UIMap. SimpleAppTest ()** .

2. Otevře se soubor UIMap.Designer.cs se zvýrazněným chybovým místem v kódu:

    ```csharp

    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

3. Chcete-li tento problém vyřešit, můžete programový test UI počkat, než se aktivuje ovládací prvek CheckBox, před pokračováním na tento řádek pomocí metody `WaitForControlEnabled()`.

    > [!WARNING]
    > Neupravujte soubor UIMap.Designer.cs. Jakékoli změny kódu v souboru UIMapDesigner.cs budou při každém vytvoření kódu pomocí nástroje UIMap – Tvůrce programového testu UI přepsány. Pokud je třeba změnit zaznamenanou metodu, musíte ji zkopírovat do souboru UIMap.cs a přejmenovat ji. Soubor UIMap.cs lze použít k přepsání metod a vlastností v souboru UIMapDesigner.cs. Je třeba odebrat odkaz na původní metodu v kódovaném souboru UITest.cs a nahradit ji názvem přejmenované metody.

4. V Průzkumník řešení v projektu programového testu uživatelského rozhraní vyhledejte **UIMap. UITest** .

5. Otevřete místní nabídku pro **UIMap. UITest** a klikněte na **otevřít**.

     Programový test uživatelského rozhraní se zobrazí v Editoru programového testu uživatelského rozhraní. Nyní můžete zobrazit a upravit programový test uživatelského rozhraní.

6. V podokně **akce uživatelského rozhraní** vyberte testovací metodu (SimpleAppTest), kterou chcete přesunout do souboru UIMap.cs nebo UIMap. vb, abyste usnadnili funkci vlastního kódu, která nebude přepsána při překompilování testovacího kódu.

7. Klikněte na tlačítko **přesunout kód** na panelu nástrojů editoru programového testu UI.

8. Zobrazí se dialogové okno aplikace Microsoft Visual Studio. Upozorňuje vás, že metoda bude přesunuta ze souboru UIMap.uitest do souboru UIMap.cs a že již nebude možné upravit metodu pomocí funkce Editor programového testu uživatelského rozhraní. Zvolte **Ano**.

     Testovací metoda je odebrána ze souboru UIMap.uitest a v podokně Akce uživatelského rozhraní se již nezobrazí. Chcete-li upravit přesunutý soubor testu, otevřete soubor UIMap.cs z Průzkumníku řešení.

9. Na panelu nástrojů [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] klikněte na možnost **Uložit**.

     Aktualizace testovací metody jsou uloženy do souboru UIMap.Designer.

    > [!CAUTION]
    > Po přesunutí metody ji nemůžete nadále upravovat pomocí Editoru programového testu uživatelského rozhraní. Musíte přidat vlastní kód a spravovat jej pomocí Editoru kódu.

10. Přejmenujte metodu z `SimpleAppTest()` na `ModifiedSimpleAppTest()`

11. Přidejte do souboru následující příkaz Using:

    ```csharp

    using Microsoft.VisualStudio.TestTools.UITesting.WpfControls;

    ```

12. Přidejte následující metodu `WaitForControlEnabled()` před problematický řádek kódu, který byl zjištěn dříve:

    ```csharp

              uICheckBoxCheckBox.WaitForControlEnabled();

    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;

    ```

13. V souboru CodedUITest1.cs vyhledejte metodu **metodu CodedUITestMethod** a buď Odkomentujte, nebo přejmenujte odkaz na původní metodu SimpleAppTest () a pak ji nahraďte novým ModifiedSimpleAppTest ():

    ```csharp
    [TestMethod]
            public void CodedUITestMethod1()
            {
                // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
                // For more information on generated code, see http://go.microsoft.com/fwlink/?LinkId=179463
                //this.UIMap.SimpleAppTest();
                this.UIMap.ModifiedSimpleAppTest();
            }

    ```

14. V nabídce **sestavení** klikněte na příkaz **Sestavit řešení**.

15. Klikněte pravým tlačítkem na metodu **metodu CodedUITestMethod** a vyberte **Spustit testy**.

16. Tentokrát programový test uživatelského rozhraní úspěšně dokončí všechny kroky v **testu a v** okně Průzkumník testů se zobrazí.

### <a name="refactor-a-control-in-the-simplewpfapp"></a>Refaktorování ovládacího prvku v aplikaci SimpleWPFApp

1. V souboru MainWindow.xaml v položce Návrhář vyberte ovládací prvek Tlačítko.

2. V horní části okno Vlastnosti změňte hodnotu vlastnosti **název** z Button1 na Button.

3. V nabídce **sestavení** klikněte na příkaz **Sestavit řešení**.

4. V Průzkumníku testů spusťte **CodedUITestMethod1**.

     Test se nezdaří, protože programový test uživatelského rozhraní nemůže najít ovládací prvek Tlačítko, který byl původně namapován ve třídě UIMap jako Tlačítko1. Refaktoring může tímto způsobem ovlivnit programové testy uživatelského rozhraní.

5. V okně Průzkumník testů v části **trasování zásobníku** vyberte první odkaz vedle **UIMpa. ModifiedSimpleAppTest ()** .

     Otevře se soubor UIMap.cs. Místo chyby bude v kódu zvýrazněno:

    ```csharp

    // Click 'Start' button
    Mouse.Click(uIStartButton, new Point(27, 10));
    ```

     Všimněte si, že řádek kódu dříve v tomto postupu používá `UiStartButton`, což je název UIMap před jeho refaktoringem.

     Chcete-li tento problém vyřešit, můžete pomocí položky Tvůrce programového testu UI přidat refaktorovaný ovládací prvek do třídy UIMap. Provedením následujícího postupu můžete aktualizovat kód testu tak, aby použil tento kód.

### <a name="map-refactored-control-and-edit-and-rerun-the-coded-ui-test"></a>Mapování refaktorovaného ovládacího prvku a úprava a opětovné spuštění programového testu uživatelského rozhraní

1. V souboru CodedUITest1.cs, v metodě **CodedUITestMethod1 ()** , klikněte pravým tlačítkem myši, vyberte možnost **generovat kód pro programový test uživatelského rozhraní** a pak zvolte možnost **použít Tvůrce programového testu uživatelského rozhraní**.

     Zobrazí se nástroj UIMap – Tvůrce programového testu UI.

2. Pomocí zástupce na ploše, který jste vytvořili dříve, spusťte aplikaci aplikaci SimpleWPFApp, kterou jste vytvořili dříve.

3. V nástroji UIMap – Tvůrce programového testu uživatelského rozhraní přetáhněte nástroj pro vlasovou čáru na tlačítko **Start** na aplikaci SimpleWPFApp.

     Tlačítko **Start** je uzavřeno v modrém poli a Tvůrce programového testu uživatelského rozhraní trvá několik sekund na zpracování dat pro vybraný ovládací prvek a zobrazení vlastností ovládacích prvků. Všimněte si, že **AutomationUId** má název **Button**.

4. Ve vlastnostech ovládacího prvku vyberte šipku v levém horním rohu a rozbalte mapování ovládacího prvku uživatelského rozhraní. Všimněte si, že je vybraná možnost **UIStartButton1** .

5. Na panelu nástrojů klikněte na tlačítko **Přidat ovládací prvek do mapování ovládacích prvků uživatelského rozhraní**.

     Stav v dolní části okna ověří akci zobrazením **vybraného ovládacího prvku, který byl přidán do mapování ovládacích prvků uživatelského rozhraní**.

6. V nástroji UIMap – Tvůrce programového testu uživatelského rozhraní, vyberte možnost **generovat kód**.

     Zobrazí se zpráva Tvůrce programového testu UI – Vytvořit kód s poznámkou uvádějící, že není vyžadována žádná nová metoda a že kód bude vytvořen pouze pro změny provedené v mapování ovládacího prvku uživatelského rozhraní.

7. Klikněte na tlačítko **Generovat**.

8. Ukončete aplikaci SimpleWPFApp.exe.

9. Ukončete nástroj UIMap – Tvůrce programového testu UI.

     Nástroj UIMap – Tvůrce programového testu UI bude potřebovat několik sekund na zpracování změn provedených v mapování ovládacího prvku uživatelského rozhraní.

10. V Průzkumníku řešení otevřete soubor UIMap.Designer.cs.

11. V souboru UIMap.Designer.cs vyhledejte vlastnost UIStartButton1. Všimněte si, že `SearchProperties` je nastavená na `"buttonA"`:

    ```csharp

    public WpfButton UIStartButton1
            {
                get
                {
                    if ((this.mUIStartButton1 == null))
                    {
                        this.mUIStartButton1 = new WpfButton(this);
                        #region Search Criteria
                        this.mUIStartButton1.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
                        this.mUIStartButton1.WindowTitles.Add("MainWindow");
                        #endregion
                    }
                    return this.mUIStartButton1;
                }
            }

    ```

     Nyní můžete upravit programový test uživatelského rozhraní tak, aby používal nově namapovaný ovládací prvek. Jak bylo uvedeno v předchozím postupu, pokud chcete přepsat jakékoliv metody nebo vlastnosti v programovém testu uživatelského rozhraní, musíte tak učinit v souboru UIMap.cs.

12. V souboru UIMap.cs přidejte konstruktor a určete vlastnost `SearchProperties` vlastnosti `UIStartButton` pro použití vlastnosti `AutomationID` s hodnotou `"buttonA":`

    ```csharp

    public UIMap()
            {
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
            }

    ```

13. V nabídce **sestavení** klikněte na příkaz **Sestavit řešení**.

14. V Průzkumníku testů spusťte CodedUITestMethod1.

     Tentokrát programový test uživatelského rozhraní úspěšně dokončí všechny kroky v testu.  V okně Výsledky testů se zobrazí stav **úspěch**.

## <a name="external-resources"></a>Externí prostředky

### <a name="videos"></a>Videa
 ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") [kódované testy uživatelského rozhraní – podrobné-Episode1-soubor GettingStarted](https://skydrive.live.com/?cid=2db0e1efe1c1d3b8&id=2DB0E1EFE1C1D3B8%21118)

 ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") [kódované testy uživatelského rozhraní – podrobné-Episode2-MaintainenceAndDebugging](https://skydrive.live.com/?cid=2db0e1efe1c1d3b8&id=2DB0E1EFE1C1D3B8%21116)

 ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") [kódované testy uživatelského rozhraní – podrobné-Episode3-HandCoding](https://skydrive.live.com/?cid=2db0e1efe1c1d3b8&id=2DB0E1EFE1C1D3B8%21117)

### <a name="hands-on-lab"></a>Praktické cvičení
 [MSDN Virtual Lab: Úvod k vytváření programových testů UI pomocí sady Visual Studio 2010](https://windows.microsoft.com/en-US/windows/products/windows-media-player)

### <a name="faq"></a>Nejčastější dotazy
 [Nejčastější dotazy k programovým testům UI – 1](https://blogs.msdn.com/b/mathew_aniyan/archive/tags/faq/)

 [Nejčastější dotazy k programovým testům UI – 2](https://social.msdn.microsoft.com/Forums/en-US/vsautotest/thread/3a74dd2c-cef8-4923-abbf-7a91f489e6c4)

### <a name="forum"></a>Fórum
 [Testování automatizace uživatelského rozhraní sady Visual Studio (zahrnuje CodedUI)](https://social.msdn.microsoft.com/Forums/en-US/vsautotest)

## <a name="see-also"></a>Viz také
 [Použití automatizace uživatelského rozhraní k otestování kódu](../test/use-ui-automation-to-test-your-code.md) [Začínáme pomocí](https://msdn.microsoft.com/18e61d03-b96a-4058-a166-8ec6b3f6116b) [podporovaných konfigurací a platforem pro programové testy uživatelského rozhraní a záznamů akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md) [úpravou](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md) programových testů UI pomocí editoru programových testů uživatelského rozhraní
