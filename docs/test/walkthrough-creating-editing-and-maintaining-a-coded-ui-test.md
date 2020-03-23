---
title: Vytvoření programového testu ui
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: f1e22a39035e5d3500f4dd45481319e1daecfa04
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592058"
---
# <a name="walkthrough-create-edit-and-maintain-a-coded-ui-test"></a>Návod: Vytvoření, úprava a údržba kódovaného testu ui

V tomto návodu se dozvíte, jak vytvořit, upravit a udržovat kódovaný test ui pro testování aplikace WPF (Windows Presentation Framework). Návod poskytuje řešení pro opravy testů, které byly přerušeny různé problémy časování a refaktoring ovládacích prvků.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-wpf-app"></a>Vytvoření aplikace WPF

1. Vytvořte nový projekt **wpf aplikace (.NET Framework)** a pojmenujte jej **SimpleWPFApp**.

     WPF **Designer** otevře a zobrazí MainWindow projektu.

2. Pokud není panel nástrojů otevřen, otevřete jej. Zvolte nabídku **Zobrazení** a pak zvolte **Panel nástrojů**.

3. V části **Všechny ovládací prvky WPF** přetáhněte ovládací **prvek Button**, **CheckBox** a **ProgressBar** na hlavní okno v návrhové ploše.

4. Vyberte ovládací prvek **Button.** V okně **Vlastnosti** změňte **Name** hodnotu \<vlastnosti Name z no name> na button1. Potom změňte hodnotu vlastnosti **Content** z Button na Start.

5. Vyberte ovládací prvek **ProgressBar.** V okně **Vlastnosti** změňte **Name** hodnotu \<vlastnosti Name z No Name> na progressBar1. Potom změňte hodnotu vlastnosti **Maximum** ze **100** na **10000**.

6. Vyberte ovládací **prvek Zaškrtávací políčko.** V okně **Vlastnosti** změňte **Name** hodnotu \<vlastnosti Name z no name> na checkBox1 a zrušte zaškrtnutí vlastnosti **IsEnabled.**

     ![Jednoduchá aplikace WPF](../test/media/codedui_wpfapp.png)

7. Poklepáním na ovládací prvek tlačítka přidejte obslužnou rutinu události kliknutí.

     MainWindow.xmal.cs *MainWindow.xmal.cs* se zobrazí v Editoru kódu s kurzorem v nové metodě button1_Click.

8. V horní části třídy hlavního okna MainWindow přidejte delegáta. Delegát bude použit pro indikátor průběhu. Chcete-li přidat delegáta, přidejte následující kód:

    ```csharp
    public partial class MainWindow : Window
    {
            private delegate void ProgressBarDelegate(System.Windows.DependencyProperty dp, Object value);

        public MainWindow()
        {

            InitializeComponent();
        }
    ```

9. V metodě button1_Click přidejte následující kód:

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

10. Uložte soubor.

### <a name="run-the-wpf-app"></a>Spuštění aplikace WPF

1. V nabídce **Ladění** vyberte **Spustit ladění** nebo stiskněte **klávesu F5**.

2. Všimněte si, že ovládací prvek zaškrtávacího políčka je zakázán. Zvolte **Start**.

     Během několika sekund by měl indikátor průběhu ukazovat 100 %.

3. Nyní můžete zaškrtnout ovládací prvek zaškrtávacího políčka.

4. Ukončete aplikaci SimpleWPFApp.

## <a name="create-a-shortcut-to-the-wpf-app"></a>Vytvoření zástupce aplikace WPF

1. Vyhledejte aplikaci SimpleWPFApp, kterou jste vytvořili dříve.

2. Vytvořte pro aplikaci SimpleWPFApp zástupce na ploše. Klepněte pravým tlačítkem myši na *soubor SimpleWPFApp.exe* a zvolte **Kopírovat**. Na ploše klikněte pravým tlačítkem myši a zvolte **Vložit zástupce**.

    > [!TIP]
    > Zástupce aplikace usnadňuje přidávání nebo úpravy kódovaných testů rozhraní pro vaši aplikaci, protože umožňuje rychle spustit aplikaci.

## <a name="create-a-coded-ui-test-for-simplewpfapp"></a>Vytvoření kódovaného testu ui pro SimpleWPFApp

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na řešení a zvolte **Přidat** > **nový projekt**.

2. Vyhledejte a vyberte šablonu **projektu programového uživatelského upřípravy a** pokračujte kroky, dokud nebude projekt vytvořen.

   > [!NOTE]
   > Pokud nevidíte šablonu **Programového testovacího projektu uživatelského nastavení,** je třeba [nainstalovat kódovku testovací součást uživatelského impodařilose](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

     Nový programový testovací projekt ui s názvem **CodedUITestProject1** je přidán do vašeho řešení a zobrazí se dialogové okno **Generovat kód pro kódovaný test ui.**

1. Vyberte **akce Záznam, upravte mapu rozhraní nebo přidejte** kontrolní výrazy a zvolte **OK**.

     Zobrazí se dialogové okno **UIMap - Coded UI Test Builder** a okno Sady Visual Studio je minimalizováno.

     Další informace o možnostech v dialogovém okně naleznete v [tématu Vytvoření kódovaných testů řízení o novém nastavení](../test/use-ui-automation-to-test-your-code.md).

1. V dialogovém okně **UIMap – Coded UI Test Builder** zvolte **Spustit nahrávání.**

     ![Spustit záznam](../test/media/cuit_builder_record.png)

     V případě potřeby můžete nahrávání pozastavit, například pokud se musíte vypořádat s příchozí poštou.

     ![Pozastavení nahrávání](../test/media/cuit_.png)

    > [!WARNING]
    > Všechny akce prováděné na ploše budou zaznamenány. Pokud provádíte akce, které mohou vést k zahrnutí citlivých dat do záznamu, pozastavte nahrávání.

1. Spusťte SimpleWPFApp pomocí zástupce na ploše.

     Stejně jako dříve si všimněte, že ovládací prvek zaškrtávacího políčka je zakázán.

1. Na SimpleWPFApp zvolte **Start**.

     Během několika sekund by měl indikátor průběhu ukazovat 100 %.

1. Zaškrtněte ovládací prvek, který je nyní povolen.

1. Ukončete aplikaci SimpleWPFApp.

1. V dialogovém okně **UIMap – Coded UI Test Builder** zvolte **Generovat kód**.

1. Do pole **Název metody** zadejte **SimpleAppTest** a zvolte **Přidat a generovat**. Během několika sekund se zobrazí kódovaný test ui a je přidán do řešení.

1. Zavřít **UIMap - Programovaný Tvůrce testů ui**.

     Soubor *CodedUITest1.cs* se zobrazí v editoru kódu.

1. Uložte projekt.

### <a name="run-the-test"></a>Spuštění testu

1. Z nabídky **Test** zvolte **Windows** a pak zvolte **Průzkumník testů**.

2. V nabídce **Sestavení** zvolte **Build Solution**.

3. V *souboru CodedUITest1.cs* vyhledejte metodu **CodedUITestMethod,** klepněte pravým tlačítkem myši a vyberte **spustit testy**nebo spusťte test z **Průzkumníka testů**.

   V průběhu programového testu uživatelského rozhraní je zobrazena aplikace SimpleWPFApp. Provádí kroky, které jste učinili v předchozí proceduře. Pokud se však test pokusí zaškrtnout políčko pro ovládací prvek zaškrtávacího políčka, okno **Výsledky testu** ukazuje, že test se nezdařil. Důvodem je, že test se pokusí zaškrtnout políčko, ale není si vědom, že ovládací prvek zaškrtávacího políčka je zakázáno, dokud indikátor průběhu je 100% kompletní. Můžete opravit tento a podobné problémy pomocí různých `UITestControl.WaitForControlXXX()` metod, které jsou k dispozici pro testování kódovaného rozhraní. Další postup bude demonstrovat pomocí `WaitForControlEnabled()` metody opravit problém, který způsobil selhání tohoto testu. Další informace naleznete [v tématu Make coded UI tests wait for specific events during back .](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md)

## <a name="edit-and-rerun-the-coded-ui-test"></a>Úprava a opětovné spuštění programového testu ui

1. V okně **Průzkumník testů** vyberte neúspěšný test a v části **StackTrace** zvolte první odkaz na **UIMap.SimpleAppTest()**.

2. Soubor *UIMap.Designer.cs* se otevře s bodem chyby zvýrazněným v kódu:

    ```csharp
    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

3. Chcete-li tento problém vyřešit, můžete provést kódovaný test ui čekat na ovládací prvek `WaitForControlEnabled()` CheckBox, který má být povolen před pokračováním na tento řádek pomocí metody.

    > [!WARNING]
    > Neupravujte *soubor UIMap.Designer.cs.* Všechny změny kódu, které provedete, budou přepsány při každém generování kódu pomocí **UIMap - Coded UI Test Builder**. Pokud máte upravit nahranou metodu, zkopírujte ji do *UIMap.cs* souboru a přejmenujte ji. Soubor *UIMap.cs* lze použít k přepsání metod a vlastností v *souboru UIMapDesigner.cs.* Je nutné odebrat odkaz na původní metodu v *souboru CodedUITest.cs* a nahradit ji názvem název metody.

4. V **Průzkumníku řešení**vyhledejte *uIMap.uitest* v projektu test kódovaného ui.

5. Otevřete místní nabídku *pro UIMap.uitest* a zvolte **Otevřít**.

     Programový test uživatelského rozhraní se zobrazí v Editoru programového testu uživatelského rozhraní. Nyní můžete zobrazit a upravit programový test uživatelského rozhraní.

6. V podokně **akcí ui** vyberte testovací metodu (SimpleAppTest), kterou chcete přesunout do souboru *UIMap.cs* nebo *UIMap.vb.* Přesunutí metody do jiného souboru umožňuje přidat vlastní kód, který nebude přepsán při opětovnékompilaci testovacího kódu.

7. Na panelu nástrojů **Editor testů programového nástroje** zvolte **tlačítko Přesunout kód.**

8. Zobrazí se dialogové okno aplikace Microsoft Visual Studio. Varuje vás, že metoda bude přesunuta ze souboru *UIMap.uitest* do souboru *UIMap.cs* a že již nebudete moci upravovat metodu pomocí programového editoru testů ui. Zvolte **Ano**.

     Testovací metoda je odebrána ze souboru *UIMap.uitest* a již se nezobrazuje v podokně Akce ui. Chcete-li soubor přesunutého testu upravit, otevřete *soubor UIMap.cs* z **Průzkumníka řešení**.

9. Na panelu nástrojů Sady Visual Studio zvolte **Uložit**.

     Aktualizace testovací metody jsou uloženy v souboru *UIMap.Designer.*

    > [!WARNING]
    > Po přesunutí metody ji nemůžete nadále upravovat pomocí Editoru programového testu uživatelského rozhraní. Musíte přidat vlastní kód a spravovat jej pomocí Editoru kódu.

10. Přejmenujte metodu z `SimpleAppTest()` na`ModifiedSimpleAppTest()`

11. Přidejte do souboru následující příkaz Using:

    ```csharp
    using Microsoft.VisualStudio.TestTools.UITesting.WpfControls;
    ```

12. K dříve `WaitForControlEnabled()` identifikované problematické řádku kódu přidejte následující metodu:

    ```csharp
    uICheckBoxCheckBox.WaitForControlEnabled();

    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

13. V *souboru CodedUITest1.cs* vyhledejte metodu **CodedUITestMethod** a buď zakomentujte, nebo přejmenujte odkaz na původní metodu SimpleAppTest() a pak ji nahraďte novou Metodou ModifiedSimpleAppTest():

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

14. V nabídce **Build** zvolte **Build Solution**.

15. Klepněte pravým tlačítkem myši na **metodu CodedUITestMethod** a vyberte příkaz **Spustit testy**.

16. Tentokrát kódovaný test ui úspěšně dokončí všechny kroky v testu a **Předáno** se zobrazí v okně **Průzkumník testů.**

## <a name="refactor-a-control-in-simplewpfapp"></a>Refaktoring ovládacího prvku v SimpleWPFApp

1. V souboru *MainWindow.xaml* vyberte v návrháři ovládací prvek tlačítka.

2. V horní části okna **Vlastnosti** změňte hodnotu vlastnosti **Name** z **button1** na **buttonA**.

3. V nabídce **Build** zvolte **Build Solution**.

4. V **Průzkumníku testů**spusťte **CodedUITestMethod1**.

     Test se nezdaří, protože programový test uživatelského rozhraní nemůže najít ovládací prvek Tlačítko, který byl původně namapován ve třídě UIMap jako Tlačítko1. Refaktoring může tímto způsobem ovlivnit programové testy uživatelského rozhraní.

5. V **Průzkumníkovi testů**v části **StackTrace** zvolte první odkaz vedle **UIMpa.ModifiedSimpleAppTest()**.

     Otevře se *soubor UIMap.cs.* Místo chyby bude v kódu zvýrazněno:

    ```csharp
    // Click 'Start' button
    Mouse.Click(uIStartButton, new Point(27, 10));
    ```

     Všimněte si, že řádek kódu `UiStartButton`dříve v tomto postupu používá , což je název UIMap před refaktored.

     Chcete-li problém opravit, můžete přidat refaktorovaný ovládací prvek uIMap pomocí **Programový tvůrce testů ui**. Můžete aktualizovat kód testu použít kód, jak je znázorněno v dalším postupu.

## <a name="map-refactored-control-rerun-the-test"></a>Mapování refaktorovaného ovládacího prvku znovu spustit test

1. V *CodedUITest1.cs* souboru v **metodě CodedUITestMethod1()** klepněte pravým tlačítkem myši na **příkaz Generovat kód pro test kódovaného ui** a pak zvolte Použít **programový tvůrce testů ui**.

     Zobrazí se **Tvůrce testů ui - kódované ui.**

2. Pomocí dříve vytvořeného zástupce na ploše spusťte aplikaci SimpleWPFApp, kterou jste vytvořili dříve.

3. V dialogovém okně **UIMap - Coded UI Test Builder** přetáhněte nástroj nitkového kříže na tlačítko **Start** na SimpleWPFApp.

     Tlačítko **Start** je uzavřeno v modrém poli. **Programové ui Test Builder** trvá několik sekund ke zpracování dat pro vybraný ovládací prvek a zobrazení vlastností ovládacího prvku. Všimněte si, že hodnota **AutomationUId** je **buttonA**.

4. Ve vlastnostech ovládacího prvku vyberte šipku v levém horním rohu a rozbalte mapování ovládacího prvku uživatelského rozhraní. Všimněte si, že je **vybrána možnost UIStartButton1.**

5. Na panelu nástrojů zvolte **Přidat ovládací prvek do mapy ovládacího prvku ui**.

     Stav v dolní části okna ověří akci zobrazením **vybraného ovládacího prvku byl přidán do mapy ovládacího prvku rozhraní**.

6. V dialogovém okně **UIMap – Coded UI Test Builder** zvolte **Generovat kód**.

     Zobrazí se dialogové okno **Coded UI Test Builder - Generate Code** s poznámkou, že není vyžadována žádná nová metoda a že tento kód bude vygenerován pouze pro změny mapy ovládacího prvku rozhraní.

7. Zvolte **Generovat**.

8. Ukončete aplikaci SimpleWPFApp.

9. Zavřít **UIMap - Programovaný Tvůrce testů ui**.

10. V **Průzkumníku řešení**otevřete *soubor UIMap.Designer.cs.*

11. V *souboru UIMap.Designer.cs* vyhledejte vlastnost **UIStartButton1.** Všimněte `SearchProperties` si, `"buttonA"`že je nastavena na :

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

     Nyní můžete upravit programový test uživatelského rozhraní tak, aby používal nově namapovaný ovládací prvek. Jak je uvedeno v předchozím postupu, pokud chcete přepsat všechny metody nebo vlastnosti v testem kódovaného ui, musíte tak učinit v *souboru UIMap.cs.*

12. V *souboru UIMap.cs* přidejte konstruktor `SearchProperties` a `UIStartButton` určete vlastnost `AutomationID` vlastnosti, která má být vlastnosti používána s hodnotou`"buttonA":`

    ```csharp
    public UIMap()
            {
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
            }
    ```

13. V nabídce **Build** zvolte **Build Solution**.

14. V **Průzkumníku testů**spusťte **CodedUITestMethod1**.

     Tentokrát programový test uživatelského rozhraní úspěšně dokončí všechny kroky v testu. V okně **Výsledky testu** se zobrazí stav **Předáno**.

## <a name="videos"></a>Videa

![odkaz na](../data-tools/media/playvideo.gif) video [Začínáme s kódovými testy ui](https://onedrive.live.com/?id=2DB0E1EFE1C1D3B8%21110&cid=2DB0E1EFE1C1D3B8)

## <a name="faq"></a>Nejčastější dotazy

[Kódované testy ui FAQ](https://social.msdn.microsoft.com/Forums/vsautotest/3a74dd2c-cef8-4923-abbf-7a91f489e6c4/faqs)

## <a name="see-also"></a>Viz také

- [Testování kódu pomocí automatizace uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md)
- [Podporované konfigurace a platformy pro kódované testy a záznamy akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Úprava kódovaných testů ui pomocí programového editoru testů ui](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
