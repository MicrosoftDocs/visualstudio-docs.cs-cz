---
title: Vytvoření programového testu UI
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: fe8bed9c1f1f8aee9ae8e6d1ba460bf226d7b818
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895519"
---
# <a name="walkthrough-create-edit-and-maintain-a-coded-ui-test"></a>Návod: Vytvoření, úpravy a správy programového testu uživatelského rozhraní

V tomto podrobném návodu se dozvíte, jak vytvářet, upravovat a udržovat programového uživatelského rozhraní testu aplikace Windows Presentation Framework (WPF). Návod poskytuje řešení pro opravu testů, které byly poškozeny různými problémy načasování a refaktoring ovládacích prvků.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-wpf-app"></a>Vytvoření aplikace WPF

1.  Na **souboru** nabídky, přejděte k **nový**a pak vyberte **projektu**.

     **Nový projekt** zobrazí se dialogové okno.

2.  V **nainstalováno** podokně rozbalte **Visual C#** a pak vyberte **Windows Desktop**.

3.  Nad prostředním podoknem ověřte, že cílové rozhraní framework rozevíracího seznamu je nastavena na **rozhraní .NET Framework 4.5**.

4.  V prostředním podokně, vyberte **aplikace WPF** šablony.

5.  V **název** textového pole, typ **aplikaci SimpleWPFApp**.

6.  Zvolte složku, do které bude projekt uložen. V **umístění** textové pole, zadejte název složky.

7.  Zvolte **OK**.

     **WPF Designer pro Visual Studio** otevře a zobrazí hlavní okno MainWindow projektu.

8.  Pokud není panel nástrojů otevřen, otevřete jej. Zvolte **zobrazení** nabídky a klikněte na tlačítko **nástrojů**.

9. V části **všechny ovládací prvky WPF** přetáhněte **tlačítko**, **zaškrtávací políčko** a **ProgressBar** ovládacího prvku do hlavního okna MainWindow v návrhu povrchu.

10. Vyberte **tlačítko** ovládacího prvku. V **vlastnosti** okna, změňte hodnotu **název** vlastnost z \<bez názvu > na button1. Změňte hodnotu **obsahu** vlastnost z tlačítka Start.

11. Vyberte **ProgressBar** ovládacího prvku. V **vlastnosti** okna, změňte hodnotu **název** vlastnost z \<bez názvu > na indikátor průběhu 1. Změňte hodnotu **maximální** vlastnost z **100** k **10000**.

12. Vyberte **zaškrtávací políčko** ovládacího prvku. V **vlastnosti** okno, změňte hodnotu **název** vlastnost z \<bez názvu > na checkBox1 a zrušte **IsEnabled** vlastnost.

     ![Jednoduché aplikace WPF](../test/media/codedui_wpfapp.png)

13. Dvakrát klikněte na přidat obslužnou rutinu události click ovládacího prvku tlačítka.

     *MainWindow.xmal.cs* se zobrazí v editoru kódu s kurzorem v nové metodě button1_Click.

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

### <a name="run-the-wpf-app"></a>Spuštění aplikace WPF

1.  Na **ladění** nabídce vyberte možnost **spustit ladění** nebo stiskněte klávesu **F5**.

2.  Všimněte si, že je ovládací prvek zaškrtávací políčko zakázán. Zvolte **Start**.

     Během několika sekund by měl indikátor průběhu ukazovat 100 %.

3.  Teď můžete vybrat ovládací prvek zaškrtávací políčko.

4.  Ukončete aplikaci SimpleWPFApp.

## <a name="create-a-shortcut-to-the-wpf-app"></a>Vytvořit zástupce aplikace WPF

1.  Vyhledejte aplikaci SimpleWPFApp, kterou jste vytvořili dříve.

2.  Vytvořte pro aplikaci SimpleWPFApp zástupce na ploše. Klikněte pravým tlačítkem na *SimpleWPFApp.exe* a zvolte **kopírování**. Na ploše, klikněte pravým tlačítkem a zvolte **Vložit zástupce**.

    > [!TIP]
    > Zástupce aplikace usnadňuje přidávat nebo upravovat programové testy uživatelského rozhraní pro vaši aplikaci, protože umožňuje rychlé spuštění aplikace.

## <a name="create-a-coded-ui-test-for-simplewpfapp"></a>Vytvoření programového testu uživatelského rozhraní pro aplikaci SimpleWPFApp

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na řešení, zvolte **přidat** a pak vyberte **nový projekt**.

     **Přidat nový projekt** zobrazí se dialogové okno.

1. V **nainstalováno** podokně rozbalte **Visual C#** a pak vyberte **Test**.

1. V prostředním podokně, vyberte **projekt programového testu UI** šablony.

   > [!NOTE]
   > Pokud se nezobrazí **projekt testu uživatelského rozhraní programového** šablony, budete muset [nainstalovat komponentu programového testu uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

1. Zvolte **OK**.

     Nový projekt programového testu UI s názvem **CodedUITestProject1** se přidá do vašeho řešení.

     **Generovat kód pro programový Test uživatelského rozhraní** zobrazí se dialogové okno.

1. Vyberte **zaznamenat akce, upravit mapu uživatelského rozhraní nebo přidat kontrolní výrazy** možnost a vyberte **OK**.

     **UIMap – Tvůrce programového testu UI** se zobrazí dialogové okno a minimalizovat okno sady Visual Studio.

     Další informace o možnostech v dialogovém okně najdete v tématu [vytvořit kódované testy uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md).

1. Zvolte **spustit záznam** na **UIMap – Tvůrce programového testu UI** dialogového okna.

     ![Spustit záznam](../test/media/cuit_builder_record.png)

     Je možné pozastavit nahrávání, v případě potřeby, například pokud budete muset řešit příchozí pošty.

     ![Pozastavit záznam](../test/media/cuit_.png)

    > [!WARNING]
    > Všechny akce provedené v klientských počítačích, bude zaznamenán. Pozastavte záznam, pokud provádíte akce, které může vést k citlivá data nebudou zahrnuty v záznamu.

1. Spusťte aplikaci SimpleWPFApp pomocí zástupce na ploše.

     Stejně jako předtím Všimněte si, že je ovládací prvek zaškrtávací políčko zakázán.

1. V aplikaci SimpleWPFApp zvolte **Start**.

     Během několika sekund by měl indikátor průběhu ukazovat 100 %.

1. Zkontrolujte ovládací prvek zaškrtávací políčko, která je nyní povolena.

1. Ukončete aplikaci SimpleWPFApp.

1. Na **UIMap – Tvůrce programového testu UI** dialogovém okně zvolte **generovat kód**.

1. V **název metody** zadejte **SimpleAppTest** a zvolte **přidat a vytvořit**. Během několika sekund programový test uživatelského rozhraní se zobrazí a je přidán do řešení.

1. Zavřít **UIMap – Tvůrce programového testu UI**.

     *CodedUITest1.cs* souboru se zobrazí v editoru kódu.

1. Uložte projekt.

### <a name="run-the-test"></a>Spuštění testu

1. Z **testovací** nabídce zvolte **Windows** a klikněte na tlačítko **Průzkumník testů**.

2. Z **sestavení** nabídce zvolte **sestavit řešení**.

3. V *CodedUITest1.cs* souboru, vyhledejte **CodedUITestMethod** metodu, klikněte pravým tlačítkem a vyberte **spustit testy**, nebo spustit test z **Průzkumníka testů**.

   V průběhu programového testu uživatelského rozhraní je zobrazena aplikace SimpleWPFApp. Provádí kroky, které jste učinili v předchozí proceduře. Však při test pokouší vybrat zaškrtávací políčko pro ovládací prvek zaškrtávací políčko **výsledky testu** okno zobrazuje, že se test nezdařil. Toto je vzhledem k tomu, že test pokouší vybrat zaškrtávací políčko, ale neví, že je ovládací prvek zaškrtávací políčko zakázán, dokud indikátor průběhu ukazovat 100 %. Můžete tento problém můžete vyřešit a podobné problémy s použitím různých `UITestControl.WaitForControlXXX()` metody, které jsou k dispozici pro programové testování uživatelského rozhraní. Další postup vám ukáže pomocí `WaitForControlEnabled()` metody, chcete-li opravit problém, který způsobil selhání testu. Další informace najdete v tématu [vytvořit kódované testy uživatelského rozhraní čekání na konkrétní události při přehrávání](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

## <a name="edit-and-rerun-the-coded-ui-test"></a>Úprava a opětovné spuštění programového testu uživatelského rozhraní

1.  V **Průzkumníka testů** okna, vyberte neúspěšných testů a **trasování zásobníku** zvolte první odkaz na **UIMap.SimpleAppTest()**.

2.  *UIMap.Designer.cs* soubor se otevře s bodem chyby v kódu zvýrazněno:

    ```csharp
    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

3.  Chcete-li tento problém, můžete vytvořit programový test uživatelského rozhraní čekal pro ovládací prvek zaškrtávací políčko Povolit před pokračováním tohoto řádku pomocí `WaitForControlEnabled()` metody.

    > [!WARNING]
    > Neprovádějte žádné změny *UIMap.Designer.cs* souboru. Žádné změny, které provedete, bude přepsán při každém generování kódu pomocí kódu **UIMap – Tvůrce programového testu UI**. Pokud je třeba změnit zaznamenanou metodu, zkopírujte ho do *UIMap.cs* souboru a přejmenujte jej. *UIMap.cs* soubor lze použít k přepsání metod a vlastností v *UIMapDesigner.cs* souboru. Je nutné odebrat odkaz na původní metodu v *CodedUITest.cs* soubor a nahradit ji názvem přejmenované metody.

4.  V **Průzkumníka řešení**, vyhledejte *UIMap.uitest* v projektu programového testu UI.

5.  Otevřete místní nabídku pro *UIMap.uitest* a zvolte **otevřít**.

     Programový test uživatelského rozhraní se zobrazí v Editoru programového testu uživatelského rozhraní. Nyní můžete zobrazit a upravit programový test uživatelského rozhraní.

6.  V **akce uživatelského rozhraní** podokně, vyberte testovací metody (SimpleAppTest), který chcete přesunout *UIMap.cs* nebo *UIMap.vb* souboru. Přesunutí metody do jiného souboru umožňuje přidat vlastní kód, který nebude přepsány při testovací kód je znovu zkompilovat.

7.  Zvolte **přesunout kód** tlačítko **editoru programového testu UI** nástrojů.

8.  Zobrazí se dialogové okno aplikace Microsoft Visual Studio. Upozorňuje vás, že metoda bude přesunuta ze *UIMap.uitest* do souboru *UIMap.cs* souboru a že již budete moci upravit metodu pomocí editoru programového testu uživatelského rozhraní. Zvolte **Ano**.

     Testovací metoda je odebrána z *UIMap.uitest* souboru a už nebude zobrazovat v podokně Akce uživatelského rozhraní. Chcete-li upravit přesunutý soubor testu, otevřete *UIMap.cs* souboru z **Průzkumníka řešení**.

9. Na panelu nástrojů sady Visual Studio **Uložit**.

     Aktualizace testovací metody jsou uloženy v *UIMap.Designer* souboru.

    > [!WARNING]
    > Po přesunutí metody ji nemůžete nadále upravovat pomocí Editoru programového testu uživatelského rozhraní. Musíte přidat vlastní kód a spravovat jej pomocí Editoru kódu.

10. Přejmenujte metodu z `SimpleAppTest()` do `ModifiedSimpleAppTest()`

11. Přidejte do souboru následující příkaz Using:

    ```csharp
    using Microsoft.VisualStudio.TestTools.UITesting.WpfControls;
    ```

12. Přidejte následující `WaitForControlEnabled()` metoda před problematický řádek kódu byl dříve identifikován:

    ```csharp
    uICheckBoxCheckBox.WaitForControlEnabled();

    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

13. V *CodedUITest1.cs* souboru, vyhledejte **CodedUITestMethod** metoda a buď okomentovat nebo přejmenujte odkaz na původní metodu SimpleAppTest() a poté ji nahraďte novou Metodou ModifiedSimpleAppTest():

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

14. Na **sestavení** nabídce zvolte **sestavit řešení**.

15. Klikněte pravým tlačítkem myši **CodedUITestMethod** metody a vyberte **spustit testy**.

16. Tentokrát programový test uživatelského rozhraní úspěšně dokončí všechny kroky v testu, a **proběhl** se zobrazí **Průzkumníka testů** okno.

## <a name="refactor-a-control-in-simplewpfapp"></a>Refaktorování ovládacího prvku v aplikaci SimpleWPFApp

1.  V *souboru MainWindow.xaml* souboru, v Návrháři vyberte ovládací prvek tlačítko.

2.  V horní části **vlastnosti** okno Změnit **název** hodnota vlastnosti z **button1** k **Tlačítkoa**.

3.  Na **sestavení** nabídce zvolte **sestavit řešení**.

4.  V **Průzkumník testů**spusťte **CodedUITestMethod1**.

     Test se nezdaří, protože programový test uživatelského rozhraní nemůže najít ovládací prvek Tlačítko, který byl původně namapován ve třídě UIMap jako Tlačítko1. Refaktoring může tímto způsobem ovlivnit programové testy uživatelského rozhraní.

5.  V **Průzkumník testů**v **trasování zásobníku** zvolte první odkaz vedle položky **(UIMpa.ModifiedSimpleAppTest)**.

     *UIMap.cs* soubor otevře. Místo chyby bude v kódu zvýrazněno:

    ```csharp
    // Click 'Start' button
    Mouse.Click(uIStartButton, new Point(27, 10));
    ```

     Všimněte si, že řádek kódu dříve v tomto postupu používá `UiStartButton`, což je název třídy UIMap předtím, než byla refaktorována.

     Chcete-li tento problém, můžete přidat refaktorovaný ovládací prvek do třídy UIMap pomocí **Tvůrce programového testu UI**. Můžete aktualizovat kód testu tak, aby použil tento kód, jak je ukázáno v následujícím postupu.

## <a name="map-refactored-control-rerun-the-test"></a>Mapování refaktorovaného ovládacího prvku znovu spustit test

1.  V *CodedUITest1.cs* souboru **CodedUITestMethod1()** metody, klikněte pravým tlačítkem, vyberte **generovat kód pro programový Test uživatelského rozhraní** a klikněte na tlačítko **použití Tvůrce programového testu UI**.

     **UIMap – Tvůrce programového testu UI** se zobrazí.

2.  Pomocí zástupce na ploše, kterou jste vytvořili dříve, spusťte aplikaci SimpleWPFApp, kterou jste vytvořili dříve.

3.  Na **UIMap – Tvůrce programového testu UI** dialogového okna, přetáhněte ikonu křížku na **Start** tlačítko v aplikaci SimpleWPFApp.

     **Start** tlačítko je ohraničeno modrým polem. **Tvůrce programového testu UI** trvá několik sekund na zpracování dat pro vybraný ovládací prvek a zobrazení vlastností ovládacího prvku. Všimněte si, že hodnota **AutomationUId** je **Tlačítkoa**.

4.  Ve vlastnostech ovládacího prvku vyberte šipku v levém horním rohu a rozbalte mapování ovládacího prvku uživatelského rozhraní. Všimněte si, že **UIStartButton1** zaškrtnuto.

5.  Na panelu nástrojů položku **přidat ovládací prvek do mapování ovládacích prvků uživatelského rozhraní**.

     Stav v dolní části okna ověří akci zobrazením **vybraný ovládací prvek byl přidán do mapování ovládacích prvků uživatelského rozhraní**.

6.  Na **UIMap – Tvůrce programového testu UI** dialogovém okně zvolte **generovat kód**.

     **Tvůrce programového testu UI – vytvořit kód** s poznámku určující, že žádná nová metoda nevyžadují, a tento kód bude vytvořen pouze pro změny mapování ovládacího prvku uživatelského rozhraní se zobrazí dialogové okno.

7.  Zvolte **generovat**.

8.  Ukončete aplikaci SimpleWPFApp.

9. Zavřít **UIMap – Tvůrce programového testu UI**.

10. V **Průzkumníka řešení**, otevřete *UIMap.Designer.cs* souboru.

11. V *UIMap.Designer.cs* souboru, vyhledejte **UIStartButton1** vlastnost. Všimněte si, že `SearchProperties` je nastavena na `"buttonA"`:

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

     Nyní můžete upravit programový test uživatelského rozhraní tak, aby používal nově namapovaný ovládací prvek. Jak bylo uvedeno v předchozím postupu. Pokud chcete přepsat jakékoliv metody nebo vlastnosti v programovém testu uživatelského rozhraní, musíte udělat, *UIMap.cs* souboru.

12. V *UIMap.cs* souboru, přidejte konstruktor a zadejte `SearchProperties` vlastnost `UIStartButton` použít vlastnost `AutomationID` vlastnost s hodnotou `"buttonA":`

    ```csharp
    public UIMap()
            {
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
            }
    ```

13. Na **sestavení** nabídce zvolte **sestavit řešení**.

14. V **Průzkumník testů**spusťte **CodedUITestMethod1**.

     Tentokrát programový test uživatelského rozhraní úspěšně dokončí všechny kroky v testu. V **výsledky testů** okně se zobrazí stav **proběhl**.

## <a name="videos"></a>Videa

![odkaz na video](../data-tools/media/playvideo.gif) [začít pomocí programových testů uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=230573)

![odkaz na video](../data-tools/media/playvideo.gif) [Údržba a ladění kódované testy uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=230574)

![odkaz na video](../data-tools/media/playvideo.gif) [ručního kódování kódované testy uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=230575)

## <a name="faq"></a>Nejčastější dotazy

[Programové testy UI – nejčastější dotazy](https://social.msdn.microsoft.com/Forums/vsautotest/3a74dd2c-cef8-4923-abbf-7a91f489e6c4/faqs)

## <a name="see-also"></a>Viz také:

- [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)
- [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Úprava programových testů UI pomocí editoru programového testu UI](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
