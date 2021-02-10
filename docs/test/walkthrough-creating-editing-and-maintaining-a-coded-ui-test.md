---
title: Vytvoření programového testu uživatelského rozhraní
description: Naučte se používat programový test uživatelského rozhraní pro aplikaci Windows Presentation Framework a Prohlédněte si řešení pro testy s časováním problémů a refaktoringem ovládacích prvků.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: b2c14869fa8e4a14a209f8fe5ad440d3ae0e569b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967953"
---
# <a name="walkthrough-create-edit-and-maintain-a-coded-ui-test"></a>Návod: vytvoření, úprava a údržba kódovaného testu uživatelského rozhraní

V tomto návodu se dozvíte, jak vytvořit, upravit a udržovat programový test UI pro otestování aplikace WPF (Windows Presentation Framework). Návod obsahuje řešení pro opravy testů, které byly přerušeny různými problémy časování a refaktoringem ovládacích prvků.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-wpf-app"></a>Vytvoření aplikace WPF

1. Vytvořte nový projekt **aplikace WPF (.NET Framework)** a pojmenujte ho **aplikaci SimpleWPFApp**.

     Otevře se **Návrhář WPF** a zobrazí MainWindow projektu.

2. Pokud není panel nástrojů otevřen, otevřete jej. Zvolte nabídku **zobrazení** a pak zvolte možnost **Sada nástrojů**.

3. V části **všechny ovládací prvky WPF** přetáhněte **tlačítko**, **CheckBox** a ovládací prvek **ProgressBar** na MainWindow na návrhové ploše.

4. Vyberte ovládací prvek **tlačítko** . V okně **vlastnosti** změňte hodnotu vlastnosti **název** z \<No Name> na Button1. Pak změňte hodnotu vlastnosti **obsah** z tlačítka na spustit.

5. Vyberte ovládací prvek **ProgressBar** . V okně **vlastnosti** změňte hodnotu vlastnosti **název** z \<No Name> na ProgressBar1. Pak změňte hodnotu vlastnosti **Maximum** z **100** na **10000**.

6. Vyberte ovládací prvek **CheckBox** . V okně **vlastnosti** změňte hodnotu vlastnosti **název** z \<No Name> na CheckBox1 a zrušte zaškrtnutí vlastnosti **Nepovoleno** .

     ![Jednoduchá aplikace WPF](../test/media/codedui_wpfapp.png)

7. Dvakrát klikněte na ovládací prvek tlačítko a přidejte obslužnou rutinu události Click.

     *MainWindow.xmal.cs* se zobrazí v editoru kódu s kurzorem v nové metodě Button1_Click.

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

10. Soubor uložte.

### <a name="run-the-wpf-app"></a>Spuštění aplikace WPF

1. V nabídce **ladění** vyberte **Spustit ladění** nebo stiskněte klávesu **F5**.

2. Všimněte si, že je ovládací prvek zaškrtávací políčko zakázán. Klikněte na tlačítko **Spustit**.

     Během několika sekund by měl indikátor průběhu ukazovat 100 %.

3. Nyní můžete zaškrtnout ovládací prvek zaškrtávací políčko.

4. Ukončete aplikaci SimpleWPFApp.

## <a name="create-a-shortcut-to-the-wpf-app"></a>Vytvoření zástupce aplikace WPF

1. Vyhledejte aplikaci aplikaci SimpleWPFApp, kterou jste vytvořili dříve.

2. Vytvořte pro aplikaci SimpleWPFApp zástupce na ploše. Klikněte pravým tlačítkem na *SimpleWPFApp.exe* a vyberte **Kopírovat**. Na ploše klikněte pravým tlačítkem myši a vyberte možnost **Vložit zástupce**.

    > [!TIP]
    > Zástupce aplikace usnadňuje přidávání a úpravy programových testů uživatelského rozhraní pro vaši aplikaci, protože umožňuje rychlé spuštění aplikace.

## <a name="create-a-coded-ui-test-for-simplewpfapp"></a>Vytvoření programového testu UI pro aplikaci SimpleWPFApp

1. V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte možnost **Přidat**  >  **Nový projekt**.

2. Vyhledejte a vyberte šablonu projektu programového **testu uživatelského rozhraní** a pokračujte postupem, dokud se projekt nevytvoří.

   > [!NOTE]
   > Pokud nevidíte šablonu **projektu programový test uživatelského rozhraní** , je nutné [nainstalovat komponentu PROGRAMového testu uživatelského](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component)rozhraní.

     Do vašeho řešení se přidá nový projekt programového testu UI s názvem **CodedUITestProject1** a zobrazí se dialogové okno **generovat kód pro programový test uživatelského rozhraní** .

1. Vyberte možnosti **záznamu akce, upravit mapu uživatelského rozhraní nebo přidat kontrolní výrazy** a zvolte **OK**.

     Zobrazí se dialogové okno Tvůrce programového **testu uživatelského rozhraní UIMap** a okno Visual Studio je minimalizováno.

     Další informace o možnostech v dialogovém okně najdete v tématu vytváření programových [testů uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md).

1. V dialogovém okně Tvůrce programového **testu uživatelského rozhraní v UIMap** vyberte **Spustit záznam** .

     ![Spustit záznam](../test/media/cuit_builder_record.png)

     V případě potřeby můžete nahrávání pozastavit, například pokud se budete muset zabývat příchozí poštou.

     ![Pozastavit záznam](../test/media/cuit_.png)

    > [!WARNING]
    > Budou zaznamenány všechny akce prováděné na ploše. Pozastaví nahrávání, pokud provádíte akce, které mohou vést k zahrnutí citlivých dat do záznamu.

1. Spusťte aplikaci SimpleWPFApp pomocí zástupce na ploše.

     Stejně jako dřív si všimněte, že je ovládací prvek zaškrtávací políčko zakázaný.

1. V aplikaci SimpleWPFApp klikněte na tlačítko **Spustit**.

     Během několika sekund by měl indikátor průběhu ukazovat 100 %.

1. Zaškrtněte políčko u ovládacího prvku zaškrtávací políčko, které je nyní povoleno.

1. Ukončete aplikaci SimpleWPFApp.

1. V dialogovém okně Tvůrce programového **testu uživatelského rozhraní UIMap** vyberte **generovat kód**.

1. Do pole **název metody** zadejte **SimpleAppTest** a klikněte na **Přidat a generovat**. Během několika sekund se programový test uživatelského rozhraní zobrazí a přidá do řešení.

1. Zavřete **UIMap – Tvůrce programového testu uživatelského rozhraní**.

     Soubor *CodedUITest1.cs* se zobrazí v editoru kódu.

1. Projekt uložte.

### <a name="run-the-test"></a>Spuštění testu

1. V nabídce **test** zvolte možnost **okna** a pak zvolte možnost **Průzkumník testů**.

2. V nabídce **sestavení** klikněte na příkaz **Sestavit řešení**.

3. V souboru *CodedUITest1.cs* vyhledejte metodu **metodu CodedUITestMethod** , klikněte pravým tlačítkem myši a vyberte možnost **Spustit testy** nebo spusťte test z **Průzkumníka testů**.

   V průběhu programového testu uživatelského rozhraní je zobrazena aplikace SimpleWPFApp. Provádí kroky, které jste učinili v předchozí proceduře. Pokud se však test pokusí zaškrtnout políčko ovládacího prvku zaškrtávací políčko, okno **výsledky testů** zobrazí, že test se nezdařil. Důvodem je, že test se pokusí vybrat zaškrtávací políčko, ale nevíte, že je ovládací prvek zaškrtávací políčko zakázán, dokud indikátor průběhu není 100% dokončeno. Tyto a podobné problémy můžete opravit pomocí různých `UITestControl.WaitForControlXXX()` metod, které jsou k dispozici pro programové testování uživatelského rozhraní. Následující postup demonstruje použití `WaitForControlEnabled()` metody k opravě problému, který způsobil selhání tohoto testu. Další informace najdete v tématu [zajištění čekání programových testů uživatelského rozhraní na konkrétní události během přehrávání](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

## <a name="edit-and-rerun-the-coded-ui-test"></a>Úprava a opětovné spuštění kódovaného testu uživatelského rozhraní

1. V okně **Průzkumník testů** vyberte neúspěšný test a v části **trasování zásobníku** zvolte první odkaz na **UIMap. SimpleAppTest ()**.

2. Otevře se soubor *UIMap.Designer.cs* s bodem chyby zvýrazněný v kódu:

    ```csharp
    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

3. Chcete-li tento problém vyřešit, můžete programový test UI počkat, než se aktivuje ovládací prvek CheckBox, než budete pokračovat na tento řádek pomocí `WaitForControlEnabled()` metody.

    > [!WARNING]
    > Neupravujte soubor *UIMap.Designer.cs* . Všechny změny kódu, které provedete, budou přepsány pokaždé, když generujete kód pomocí **UIMap – Tvůrce programového testu uživatelského rozhraní**. Pokud je nutné změnit zaznamenanou metodu, zkopírujte ji do souboru *UIMap.cs* a přejmenujte ji. Soubor *UIMap.cs* lze použít k přepsání metod a vlastností v souboru *UIMapDesigner.cs* . Je nutné odebrat odkaz na původní metodu v souboru *CodedUITest.cs* a nahradit ji názvem metody, kterou jste přejmenovali.

4. V **Průzkumník řešení** v projektu programového testu uživatelského rozhraní vyhledejte *UIMap. UITest* .

5. Otevřete místní nabídku pro *UIMap. UITest* a klikněte na **otevřít**.

     Programový test uživatelského rozhraní se zobrazí v Editoru programového testu uživatelského rozhraní. Nyní můžete zobrazit a upravit programový test uživatelského rozhraní.

6. V podokně **akce uživatelského rozhraní** vyberte testovací metodu (SimpleAppTest), kterou chcete přesunout do souboru *UIMap.cs* nebo *UIMap. vb* . Přesunutí metody do jiného souboru umožňuje přidat vlastní kód, který nebude přepsán, pokud je testovací kód znovu zkompilován.

7. Klikněte na tlačítko **přesunout kód** na panelu nástrojů editoru programového **testu UI** .

8. Zobrazí se dialogové okno aplikace Microsoft Visual Studio. Upozorňuje vás, že metoda bude přesunuta ze souboru *UIMap. UITest* do souboru *UIMap.cs* a že již nebudete moci upravovat metodu pomocí editoru programového testu uživatelského rozhraní. Vyberte **Ano**.

     Testovací metoda je odebrána ze souboru *UIMap. UITest* a již se nezobrazuje v podokně akce uživatelského rozhraní. Chcete-li upravit přesunutý soubor testu, otevřete soubor *UIMap.cs* z **Průzkumník řešení**.

9. Na panelu nástrojů sady Visual Studio klikněte na možnost **Uložit**.

     Aktualizace testovací metody jsou uloženy v souboru *UIMap. Designer* .

    > [!WARNING]
    > Po přesunutí metody ji nemůžete nadále upravovat pomocí Editoru programového testu uživatelského rozhraní. Musíte přidat vlastní kód a spravovat jej pomocí Editoru kódu.

10. Přejmenujte metodu z `SimpleAppTest()` na `ModifiedSimpleAppTest()`

11. Přidejte do souboru následující příkaz Using:

    ```csharp
    using Microsoft.VisualStudio.TestTools.UITesting.WpfControls;
    ```

12. Přidejte následující `WaitForControlEnabled()` metodu před problematický řádek kódu, který byl zjištěn dříve:

    ```csharp
    uICheckBoxCheckBox.WaitForControlEnabled();

    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

13. V souboru *CodedUITest1.cs* vyhledejte metodu **metodu CodedUITestMethod** a buď Odkomentujte, nebo přejmenujte odkaz na původní metodu SimpleAppTest () a pak ji nahraďte novým ModifiedSimpleAppTest ():

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

16. Tentokrát programový test uživatelského rozhraní úspěšně dokončí všechny kroky v testu a **předaný** se zobrazí v okně **Průzkumník testů** .

## <a name="refactor-a-control-in-simplewpfapp"></a>Refaktoring ovládacího prvku v aplikaci SimpleWPFApp

1. V souboru *MainWindow. XAML* v návrháři vyberte ovládací prvek tlačítko.

2. V horní části okna **vlastnosti** změňte hodnotu vlastnosti **název** z možnosti **Button1** na **Button**.

3. V nabídce **sestavení** klikněte na příkaz **Sestavit řešení**.

4. V **Průzkumníku testů** spusťte **CodedUITestMethod1**.

     Test se nezdaří, protože programový test uživatelského rozhraní nemůže najít ovládací prvek Tlačítko, který byl původně namapován ve třídě UIMap jako Tlačítko1. Refaktoring může tímto způsobem ovlivnit programové testy uživatelského rozhraní.

5. V **Průzkumníku testů** v části **trasování zásobníku** vyberte první odkaz vedle **UIMpa. ModifiedSimpleAppTest ()**.

     Otevře se soubor *UIMap.cs* . Místo chyby bude v kódu zvýrazněno:

    ```csharp
    // Click 'Start' button
    Mouse.Click(uIStartButton, new Point(27, 10));
    ```

     Všimněte si, že řádek kódu dříve v tomto postupu používá `UiStartButton` , což je název UIMap před refaktoringem.

     Chcete-li tento problém vyřešit, můžete přidat refaktored Control do UIMap pomocí Tvůrce programového **testu uživatelského rozhraní**. Kód testu můžete aktualizovat tak, aby používal kód, jak je znázorněno v dalším postupu.

## <a name="map-refactored-control-rerun-the-test"></a>Znovu provést mapování refaktoringu ovládacího prvku pro opětovné spuštění testu

1. V souboru *CodedUITest1.cs* , v metodě **CodedUITestMethod1 ()** , klikněte pravým tlačítkem myši, vyberte možnost **generovat kód pro programový test uživatelského rozhraní** a pak zvolte možnost **použít Tvůrce programového testu uživatelského rozhraní**.

     Zobrazí se Tvůrce programového **testu uživatelského rozhraní UIMap** .

2. Pomocí zástupce na ploše, který jste vytvořili dříve, spusťte aplikaci aplikaci SimpleWPFApp, kterou jste vytvořili dříve.

3. V dialogu **Tvůrce programového testu uživatelského rozhraní UIMap** přetáhněte nástroj pro vlasovou čáru na tlačítko **Start** v aplikaci SimpleWPFApp.

     Tlačítko **Start** je uzavřeno v modrém poli. **Tvůrce programového testu uživatelského rozhraní** trvá několik sekund na zpracování dat pro vybraný ovládací prvek a zobrazení vlastností ovládacího prvku. Všimněte si, že hodnota **AutomationUId** je **Button**.

4. Ve vlastnostech ovládacího prvku vyberte šipku v levém horním rohu a rozbalte mapování ovládacího prvku uživatelského rozhraní. Všimněte si, že je vybraná možnost **UIStartButton1** .

5. Na panelu nástrojů klikněte na tlačítko **Přidat ovládací prvek do mapování ovládacích prvků uživatelského rozhraní**.

     Stav v dolní části okna ověří akci zobrazením **vybraného ovládacího prvku, který byl přidán do mapování ovládacích prvků uživatelského rozhraní**.

6. V dialogovém okně Tvůrce programového **testu uživatelského rozhraní UIMap** vyberte **generovat kód**.

     Zobrazí se dialogové okno Tvůrce programového **testu UI – generovat kód** s upozorněním, že není vyžadována žádná nová metoda a že kód bude vygenerován pouze pro změny v mapě ovládacího prvku uživatelského rozhraní.

7. Klikněte na tlačítko **Generovat**.

8. Ukončete aplikaci SimpleWPFApp.

9. Zavřete **UIMap – Tvůrce programového testu uživatelského rozhraní**.

10. V **Průzkumník řešení** otevřete soubor *UIMap.Designer.cs* .

11. V souboru *UIMap.Designer.cs* vyhledejte vlastnost **UIStartButton1** . Všimněte si, že `SearchProperties` je nastavené na `"buttonA"` :

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

     Nyní můžete upravit programový test uživatelského rozhraní tak, aby používal nově namapovaný ovládací prvek. Jak je uvedeno v předchozím postupu, pokud chcete přepsat jakékoli metody nebo vlastnosti v programovém testu UI, musíte to provést v souboru *UIMap.cs* .

12. V souboru *UIMap.cs* přidejte konstruktor a určete `SearchProperties` vlastnost vlastnosti `UIStartButton` pro použití `AutomationID` vlastnosti s hodnotou `"buttonA":`

    ```csharp
    public UIMap()
            {
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
            }
    ```

13. V nabídce **sestavení** klikněte na příkaz **Sestavit řešení**.

14. V **Průzkumníku testů** spusťte **CodedUITestMethod1**.

     Tentokrát programový test uživatelského rozhraní úspěšně dokončí všechny kroky v testu. V okně **výsledky testů** se zobrazí stav **úspěch**.

## <a name="videos"></a>Videa

![odkaz na video ](../data-tools/media/playvideo.gif) [Začínáme s kódovanými testy uživatelského rozhraní](https://onedrive.live.com/?id=2DB0E1EFE1C1D3B8%21110&cid=2DB0E1EFE1C1D3B8)

## <a name="faq"></a>Časté otázky

[Nejčastější dotazy k programovým testům uživatelského rozhraní](https://social.msdn.microsoft.com/Forums/vsautotest/3a74dd2c-cef8-4923-abbf-7a91f489e6c4/faqs)

## <a name="see-also"></a>Viz také

- [Použití automatizace uživatelského rozhraní k otestování kódu](../test/use-ui-automation-to-test-your-code.md)
- [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a záznamy akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Úpravy programových testů uživatelského rozhraní pomocí editoru programových testů uživatelského rozhraní](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
