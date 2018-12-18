---
title: 'Návod: Vytváření, úpravy a údržba programového testu UI | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c25ba7-5c9c-455b-9242-701cda56f90c
caps.latest.revision: 43
ms.author: gewarren
manager: douge
ms.openlocfilehash: aff0363b1fe554e55cae7b58d79cd8f765e76d68
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49257527"
---
# <a name="walkthrough-creating-editing-and-maintaining-a-coded-ui-test"></a>Návod: Vytváření, upravování a údržba programového testu UI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto návodu vytvoříte jednoduchou aplikaci Windows Presentation Foundation (WPF) pro demonstraci vytvoření, úpravy a správy programového testu uživatelského rozhraní. Návod poskytuje řešení pro opravu testů, které byly poškozeny různými chybami časování a refaktoringem ovládacích prvků.  
  
## <a name="prerequisites"></a>Požadavky  
 Přitom budete potřebovat:  
  
-   Visual Studio Enterprise  
  
### <a name="create-a-simple-wpf-application"></a>Vytvoření jednoduché aplikace WPF  
  
1.  Na **souboru** nabídky, přejděte k **nový**a pak vyberte **projektu**.  
  
     **Nový projekt** zobrazí se dialogové okno.  
  
2.  V **nainstalováno** podokně rozbalte **Visual C#** a pak vyberte **Windows Desktop**.  
  
3.  Nad prostředním podoknem ověřte, že cílové rozhraní framework rozevíracího seznamu je nastavena na **rozhraní .NET Framework 4.5**.  
  
4.  V prostředním podokně, vyberte **aplikace WPF** šablony.  
  
5.  V **název** textového pole, typ **aplikaci SimpleWPFApp**.  
  
6.  Zvolte složku, do které bude projekt uložen. V **umístění** textové pole, zadejte název složky.  
  
7.  Zvolte **OK**.  
  
     WPF Designer pro sadu Visual Studio otevře a zobrazí hlavní okno MainWindow projektu.  
  
8.  Pokud není panel nástrojů otevřen, otevřete jej. Zvolte **zobrazení** nabídky a klikněte na tlačítko **nástrojů**.  
  
9. V části **všechny ovládací prvky WPF** přetáhněte **tlačítko**, **zaškrtávací políčko** a **ProgressBar** ovládacího prvku do hlavního okna MainWindow v návrhu povrchu.  
  
10. Vyberte ovládací prvek Tlačítko. V okně Vlastnosti změňte hodnotu **název** vlastnost z \<bez názvu > na button1. Změňte hodnotu **obsahu** vlastnost z tlačítka Start.  
  
11. Vyberte ovládací prvek Indikátor průběhu. V okně Vlastnosti změňte hodnotu pro hodnotu **název** vlastnost z \<bez názvu > na indikátor průběhu 1. Změňte hodnotu **maximální** vlastnost z **100** k **10000**.  
  
12. Vyberte ovládací prvek Zaškrtávací políčko. V okně Vlastnosti změňte hodnotu **název** vlastnost z \<bez názvu > na checkBox1 a zrušte **IsEnabled** vlastnost.  
  
     ![Jednoduché aplikace WPF](../test/media/codedui-wpfapp.png "CodedUI_WPFApp")  
  
13. Dvakrát klikněte na přidat obslužnou rutinu události click ovládacího prvku tlačítka.  
  
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
  
1.  Na **ladění** nabídce vyberte možnost **spustit ladění** nebo stiskněte klávesu **F5**.  
  
2.  Všimněte si, že je ovládací prvek zaškrtávací políčko zakázán. Zvolte **Start**.  
  
     Během několika sekund by měl indikátor průběhu ukazovat 100 %.  
  
3.  Teď můžete vybrat ovládací prvek zaškrtávací políčko.  
  
4.  Ukončete aplikaci SimpleWPFApp.  
  
### <a name="create-and-run-a-coded-ui-test-for-simplewpfapp"></a>Vytvoření a spuštění programového testu uživatelského rozhraní pro aplikaci SimpleWPFApp  
  
1.  Vyhledejte aplikaci SimpleWPFApp, kterou jste vytvořili dříve. Ve výchozím nastavení, aplikace se umístí na C:\Users\\< uživatelské jméno\>\Documents\Visual Studio \<verze > \Projects\SimpleWPFApp\SimpleWPFApp\bin\Debug\SimpleWPFApp.exe  
  
2.  Vytvořte pro aplikaci SimpleWPFApp zástupce na ploše. Klikněte pravým tlačítkem na SimpleWPFApp.exe a zvolte **kopírování**. Na ploše, klikněte pravým tlačítkem a zvolte **Vložit zástupce**.  
  
    > [!TIP]
    >  Zástupce aplikace usnadňuje přidávání nebo úpravu programových testů uživatelského rozhraní pro vaši aplikaci, protože umožňuje rychlé spuštění aplikace.  
  
3.  V Průzkumníku řešení klikněte pravým tlačítkem na řešení, zvolte **přidat** a pak vyberte **nový projekt**.  
  
     **Přidat nový projekt** zobrazí se dialogové okno.  
  
4.  V **nainstalováno** podokně rozbalte **Visual C#** a pak vyberte **Test**.  
  
5.  V prostředním podokně, vyberte **projekt programového testu UI** šablony.  
  
6.  Zvolte **OK**.  
  
     V Průzkumníku řešení nový projekt programového testu UI s názvem **CodedUITestProject1** se přidá do vašeho řešení.  
  
     **Generovat kód pro programový Test uživatelského rozhraní** zobrazí se dialogové okno.  
  
7.  Vyberte **zaznamenat akce, upravit mapu uživatelského rozhraní nebo přidat kontrolní výrazy** možnost a vyberte **OK**.  
  
     Zobrazí se nástroj UIMap – Tvůrce programového testu UI a minimalizovat okno sady Visual Studio.  
  
     Další informace o možnostech v dialogovém okně najdete v tématu [vytváření programových testů UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
8.  Zvolte **spustit záznam** v nástroji UIMap – Tvůrce programového testu UI.  
  
     ![Spustit nahrávání](../test/media/cuit-builder-record.png "CUIT_Builder_Record")  
  
     Je možné pozastavit nahrávání, v případě potřeby, například pokud budete muset řešit příchozí pošty.  
  
     ![Pozastavit záznam](../test/media/cuit.png "CUIT_")  
  
    > [!WARNING]
    >  Všechny akce provedené v klientských počítačích, bude zaznamenán. Pozastavte záznam, pokud provádíte akce, které může vést k citlivá data nebudou zahrnuty v záznamu.  
  
9. Spusťte aplikaci SimpleWPFApp pomocí zástupce na ploše.  
  
     Stejně jako předtím Všimněte si, že je ovládací prvek zaškrtávací políčko zakázán.  
  
10. V aplikaci SimpleWPFApp zvolte **Start**.  
  
     Během několika sekund by měl indikátor průběhu ukazovat 100 %.  
  
11. Zkontrolujte ovládací prvek zaškrtávací políčko, která je nyní povolena.  
  
12. Ukončete aplikaci SimpleWPFApp.  
  
13. V nástroji UIMap – Tvůrce programového testu UI zvolte **generovat kód**.  
  
14. V typu názvu metody **SimpleAppTest** a zvolte **přidat a vytvořit**. Během několika sekund se programový test uživatelského rozhraní zobrazí a přidá k řešení.  
  
15. Ukončete nástroj UIMap – Tvůrce programového testu UI.  
  
     V Editoru kódu se zobrazí soubor CodedUITest1.cs.  
  
16. Uložte projekt.  
  
### <a name="run-the-coded-ui-test"></a>Spuštění programového testu uživatelského rozhraní  
  
1.  Z **testovací** nabídce zvolte **Windows** a klikněte na tlačítko **Průzkumník testů**.  
  
2.  Z **sestavení** nabídce zvolte **sestavit řešení**.  
  
3.  V souboru CodedUITest1.cs vyhledejte **CodedUITestMethod** metodu, klikněte pravým tlačítkem a vyberte **spustit testy**, nebo spustit test pomocí Průzkumníku testů.  
  
     V průběhu programového testu uživatelského rozhraní je zobrazena aplikace SimpleWPFApp. Provádí kroky, které jste učinili v předchozí proceduře. Však test pokusí vybrat zaškrtávací políčko pro ovládací prvek zaškrtávací políčko, v okně Výsledky testu ukazuje, že se test nezdařil. Toto je vzhledem k tomu, že test pokouší vybrat zaškrtávací políčko, ale neví, že je ovládací prvek zaškrtávací políčko zakázán, dokud indikátor průběhu ukazovat 100 %. Můžete tento problém můžete vyřešit a podobné problémy s použitím různých `UITestControl.WaitForControlXXX()` metody, které jsou k dispozici pro programové testování uživatelského rozhraní. Další postup vám ukáže pomocí `WaitForControlEnabled()` metody, chcete-li opravit problém, který způsobil selhání testu. Další informace najdete v tématu [vytváření programového uživatelského rozhraní testy čekat pro konkrétní události při přehrávání](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).  
  
### <a name="edit-and-rerun-the-coded-ui-test"></a>Úprava a opětovné spuštění programového testu uživatelského rozhraní  
  
1.  V okně Průzkumník testu vyberte test, který selhal a **trasování zásobníku** zvolte první odkaz na **UIMap.SimpleAppTest()**.  
  
2.  Otevře se soubor UIMap.Designer.cs se zvýrazněným chybovým místem v kódu:  
  
    ```csharp  
  
    // Select 'CheckBox' check box  
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;  
    ```  
  
3.  Chcete-li tento problém, můžete vytvořit programový test uživatelského rozhraní čekal pro ovládací prvek zaškrtávací políčko Povolit před pokračováním tohoto řádku pomocí `WaitForControlEnabled()` metody.  
  
    > [!WARNING]
    >  Neupravujte soubor UIMap.Designer.cs. Jakékoli změny kódu v souboru UIMapDesigner.cs budou při každém vytvoření kódu pomocí nástroje UIMap – Tvůrce programového testu UI přepsány. Pokud je třeba změnit zaznamenanou metodu, musíte ji zkopírovat do souboru UIMap.cs a přejmenovat ji. Soubor UIMap.cs lze použít k přepsání metod a vlastností v souboru UIMapDesigner.cs. Je třeba odebrat odkaz na původní metodu v kódovaném souboru UITest.cs a nahradit ji názvem přejmenované metody.  
  
4.  V Průzkumníku řešení vyhledejte **UIMap.uitest** v projektu programového testu UI.  
  
5.  Otevřete místní nabídku pro **UIMap.uitest** a zvolte **otevřít**.  
  
     Programový test uživatelského rozhraní se zobrazí v Editoru programového testu uživatelského rozhraní. Nyní můžete zobrazit a upravit programový test uživatelského rozhraní.  
  
6.  V **akce uživatelského rozhraní** podokně, vyberte testovací metody (SimpleAppTest), který chcete přesunout do souboru UIMap.cs nebo UIMap.vb k usnadnění funkce vlastního kódu, který nebude při testovací kód je znovu zkompilovat.  
  
7.  Zvolte **přesunout kód** tlačítko na panelu nástrojů editoru programového testu UI.  
  
8.  Zobrazí se dialogové okno aplikace Microsoft Visual Studio. Upozorňuje vás, že metoda bude přesunuta ze souboru UIMap.uitest do souboru UIMap.cs a že již nebude možné upravit metodu pomocí funkce Editor programového testu uživatelského rozhraní. Zvolte **Ano**.  
  
     Testovací metoda je odebrána ze souboru UIMap.uitest a v podokně Akce uživatelského rozhraní se již nezobrazí. Chcete-li upravit přesunutý soubor testu, otevřete soubor UIMap.cs z Průzkumníku řešení.  
  
9. Na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástrojů, zvolte **Uložit**.  
  
     Aktualizace testovací metody jsou uloženy do souboru UIMap.Designer.  
  
    > [!CAUTION]
    >  Po přesunutí metody ji nemůžete nadále upravovat pomocí Editoru programového testu uživatelského rozhraní. Musíte přidat vlastní kód a spravovat jej pomocí Editoru kódu.  
  
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
  
13. V souboru CodedUITest1.cs vyhledejte **CodedUITestMethod** metoda a buď okomentovat nebo přejmenujte odkaz na původní metodu SimpleAppTest() a poté ji nahraďte novou metodou ModifiedSimpleAppTest():  
  
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
  
16. Tentokrát programový test uživatelského rozhraní úspěšně dokončí všechny kroky v testu a **proběhl** se zobrazí v okně Průzkumníka testů.  
  
### <a name="refactor-a-control-in-the-simplewpfapp"></a>Refaktorování ovládacího prvku v aplikaci SimpleWPFApp  
  
1.  V souboru MainWindow.xaml v položce Návrhář vyberte ovládací prvek Tlačítko.  
  
2.  V horní části okna vlastnosti, změnit **název** hodnota vlastnosti z button1 na Tlačítkoa.  
  
3.  Na **sestavení** nabídce zvolte **sestavit řešení**.  
  
4.  V Průzkumníku testů, spouštění **CodedUITestMethod1**.  
  
     Test se nezdaří, protože programový test uživatelského rozhraní nemůže najít ovládací prvek Tlačítko, který byl původně namapován ve třídě UIMap jako Tlačítko1. Refaktoring může tímto způsobem ovlivnit programové testy uživatelského rozhraní.  
  
5.  V okně Průzkumníka testů v **trasování zásobníku** zvolte první odkaz vedle položky **(UIMpa.ModifiedSimpleAppTest)**.  
  
     Otevře se soubor UIMap.cs. Místo chyby bude v kódu zvýrazněno:  
  
    ```csharp  
  
    // Click 'Start' button  
    Mouse.Click(uIStartButton, new Point(27, 10));  
    ```  
  
     Všimněte si, že řádek kódu dříve v tomto postupu používá `UiStartButton`, což je název třídy UIMap předtím, než byla refaktorována.  
  
     Chcete-li tento problém vyřešit, můžete pomocí položky Tvůrce programového testu UI přidat refaktorovaný ovládací prvek do třídy UIMap. Provedením následujícího postupu můžete aktualizovat kód testu tak, aby použil tento kód.  
  
### <a name="map-refactored-control-and-edit-and-rerun-the-coded-ui-test"></a>Mapování refaktorovaného ovládacího prvku a úprava a opětovné spuštění programového testu uživatelského rozhraní  
  
1.  V souboru CodedUITest1.cs v **CodedUITestMethod1()** metody, klikněte pravým tlačítkem, vyberte **generovat kód pro programový Test uživatelského rozhraní** a klikněte na tlačítko **použití Tvůrce programového testu UI**.  
  
     Zobrazí se nástroj UIMap – Tvůrce programového testu UI.  
  
2.  Pomocí zástupce na ploše, kterou jste vytvořili dříve, spusťte aplikaci SimpleWPFApp, kterou jste vytvořili dříve.  
  
3.  V nástroji UIMap – Tvůrce programového testu UI, přetáhněte ikonu křížku na **Start** tlačítko v aplikaci SimpleWPFApp.  
  
     **Start** tlačítko je ohraničeno modrým polem a Tvůrce programového testu UI trvá několik sekund na zpracování dat pro vybraný ovládací prvek a vlastností ovládacích prvků se zobrazí. Všimněte si, **AutomationUId** jmenuje **Tlačítkoa**.  
  
4.  Ve vlastnostech ovládacího prvku vyberte šipku v levém horním rohu a rozbalte mapování ovládacího prvku uživatelského rozhraní. Všimněte si, že **UIStartButton1** zaškrtnuto.  
  
5.  Na panelu nástrojů položku **přidat ovládací prvek do mapování ovládacích prvků uživatelského rozhraní**.  
  
     Stav v dolní části okna ověří akci zobrazením **vybraný ovládací prvek byl přidán do mapování ovládacích prvků uživatelského rozhraní**.  
  
6.  V nástroji UIMap – Tvůrce programového testu UI, zvolte **generovat kód**.  
  
     Zobrazí se zpráva Tvůrce programového testu UI – Vytvořit kód s poznámkou uvádějící, že není vyžadována žádná nová metoda a že kód bude vytvořen pouze pro změny provedené v mapování ovládacího prvku uživatelského rozhraní.  
  
7.  Zvolte **generovat**.  
  
8.  Ukončete aplikaci SimpleWPFApp.exe.  
  
9. Ukončete nástroj UIMap – Tvůrce programového testu UI.  
  
     Nástroj UIMap – Tvůrce programového testu UI bude potřebovat několik sekund na zpracování změn provedených v mapování ovládacího prvku uživatelského rozhraní.  
  
10. V Průzkumníku řešení otevřete soubor UIMap.Designer.cs.  
  
11. V souboru UIMap.Designer.cs vyhledejte vlastnosti UIStartButton1. Všimněte si, že `SearchProperties` je nastavena na `"buttonA"`:  
  
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
  
12. V souboru UIMap.cs přidejte konstruktor a zadejte `SearchProperties` vlastnost `UIStartButton` použít vlastnost `AutomationID` vlastnost s hodnotou `"buttonA":`  
  
    ```csharp  
  
    public UIMap()  
            {  
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";  
            }  
  
    ```  
  
13. Na **sestavení** nabídce zvolte **sestavit řešení**.  
  
14. V Průzkumníku testů spouštění CodedUITestMethod1.  
  
     Tentokrát programový test uživatelského rozhraní úspěšně dokončí všechny kroky v testu.  V okně Výsledky testu se zobrazí stav **proběhl**.  
  
## <a name="external-resources"></a>Externí zdroje  
  
### <a name="videos"></a>Videa  
 ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") [kódované UI testy – podrobné informace – Episode1-GettingStarted](http://go.microsoft.com/fwlink/?LinkID=230573)  
  
 ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") [kódované UI testy – podrobné informace – část 2 – Údržba a ladění](http://go.microsoft.com/fwlink/?LinkID=230574)  
  
 ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") [kódované UI testy – podrobné informace – část 3 – ruční kódování](http://go.microsoft.com/fwlink/?LinkID=230575)  
  
### <a name="hands-on-lab"></a>Praktické cvičení  
 [Virtuální laboratoř na webu MSDN: Úvod do vytváření programových testů uživatelského rozhraní pomocí sady Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkID=22508)  
  
### <a name="faq"></a>Nejčastější dotazy  
 [Programové testy UI – nejčastější dotazy – 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [Programové testy UI – nejčastější dotazy -2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### <a name="forum"></a>Fórum  
 [Visual Studio automatické testování uživatelského rozhraní (včetně CodedUI)](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## <a name="see-also"></a>Viz také  
 [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)   
 [Začínáme s WPF Designer](http://msdn.microsoft.com/en-us/18e61d03-b96a-4058-a166-8ec6b3f6116b)   
 [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Úpravy programových testů uživatelského rozhraní pomocí Editoru programových testů uživatelského rozhraní](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)



