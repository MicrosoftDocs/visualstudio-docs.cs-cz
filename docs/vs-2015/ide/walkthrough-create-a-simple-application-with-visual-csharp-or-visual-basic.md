---
title: 'Návod: Vytvoření jednoduché aplikace s Visual C# nebo Visual Basic | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 51fc073046833165097a8a9a4fb2f169ed3a04e7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851683"
---
# <a name="walkthrough-create-a-simple-application-with-visual-c-or-visual-basic"></a>Návod: Vytvoření jednoduché aplikace s použitím jazyka Visual C# nebo Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto návodu se seznámíte s mnoha nástroji, dialogovými okny a návrháři, které lze použít při vývoji aplikací pomocí systému Visual Studio. Vytvoříte jednoduchou aplikaci ve stylu „Hello World“, navrhnete uživatelské rozhraní (UI), vložíte kód a budete ladit chyby. A přitom získáte zkušenosti s prací v integrovaném vývojovém prostředí (IDE).  
  
 Toto téma obsahuje následující oddíly:  
  
 [Konfigurace integrovaného vývojového prostředí](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_ConfigureIDE)  
  
 [Vytvoření jednoduché aplikace](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_CreateApp)  
  
 [Ladění a testování aplikace](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_DebugTest)  
  
> [!NOTE]
>  Tento návod vychází ze systému Visual Studio Professional, který nabízí šablonu aplikace WPF, na které vytvoříte projekt pro tento návod. Visual Studio Express pro stolní počítače se systémem Windows tuto šablonu nabízí také, ale Visual Studio Express pro Windows a Visual Studio Express pro Web nikoli. Úvodní informace o tom, jak používat Visual Studio Express pro Windows, najdete v článku [středisko pro vývojáře pro Windows Store apps](http://msdn.microsoft.com/windows/apps/br229519). Úvodní informace o tom, jak používat Visual Studio Express for Web [Začínáme s rozhraním ASP.NET](http://www.asp.net/get-started). Vaše verze aplikace Visual Studio a nastavení, která používáte, určují také názvy a umístění některých prvků uživatelského rozhraní. Zobrazit [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
##  <a name="BKMK_ConfigureIDE"></a> Konfigurace integrovaného vývojového prostředí  
 Při prvním spuštění aplikace Visual Studio, Visual Studio vás vyzve k přihlášení pomocí služba účtu Microsoft (MSA), [Přihlaste se k sadě Visual Studio](http://blogs.msdn.com/b/visualstudio/archive/2013/06/28/welcome-sign-in-to-visual-studio.aspx). Není nutné se přihlásit a můžete provést později.  
  
 Při spuštění vaší aplikace Visual Studio dále musíte vybrat kombinaci nastavení, která aplikuje sadu předdefinovaných nastavení rozhraní IDE. Každá kombinace nastavení byla navržena za účelem usnadnění vývoje aplikací.  
  
 Tento návod předpokládá, můžete použít **obecným vývojovým nastavením**, které nastaví minimální množství vlastního nastavení rozhraní IDE. Pokud jste již vybrali C# nebo Visual Basic (obojí jsou vhodná rozhodnutí), není nutné nastavení změnit.  Pokud chcete změnit nastavení, můžete použít **Průvodce importem a exportem nastavení**. Zobrazit [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Po otevření sady Visual Studio lze rozeznat okna nástrojů, nabídky, panely nástrojů a prostor hlavního okna. Okna nástrojů jsou ukotveny na levé a pravé straně okna aplikace s **Snadné spuštění**, nabídek a běžný panel nástrojů v horní části. Ve střední části okna aplikace se nachází **úvodní stránka**. Při načítání řešení nebo projektu, v prostoru zobrazí editory a návrháře kde **úvodní stránka** je. Při vývoji aplikace strávíte nejvíce času v této centrální oblasti.  
  
 Obrázek 2: Integrované vývojové prostředí (IDE) systému Visual Studio  
  
 ![Integrované vývojové prostředí s použitými nastaveními Obecné](../ide/media/exploreide-idewithgeneralsettings.png "ExploreIDE IDEwithgeneralsettings")  
  
 Můžete vytvořit další úpravy sady Visual Studio, jako jsou například změny řezu písma a velikost textu v editoru či barvy motivu rozhraní IDE, s použitím **možnosti** dialogové okno. V závislosti na kombinaci použitého nastavení se některé položky v tomto dialogovém okně nemusejí automaticky zobrazit. Abyste měli jistotu, že všechny možnosti zobrazit výběrem **zobrazit všechna nastavení** zaškrtávací políčko.  
  
 Obrázek 3: Dialogové okno Možnosti  
  
 ![Wirh pole dialogové okno Možnosti zobrazit všechny možnosti nastavení](../ide/media/exploreide-optionsdialogbox.png "ExploreIDE Optionsdialogbox")  
  
 V tomto příkladu změníte barevný motiv integrovaného vývojového prostředí (IDE) ze světlého na tmavé.  Můžete přeskočit k části Pokud chcete vytvořit projekt.  
  
#### <a name="to-change-the-color-theme-of-the-ide"></a>Změna barevného motivu prostředí IDE  
  
1. Otevřít **možnosti** dialogové okno kliknutím **nástroje** nabídce v horní části a pak **možnosti...** položka.  
  
    ![Možnosti příkazu v nabídce Nástroje](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE ToolsOptionsmenu")  
  
2. Změnit **barevný motiv** k **tmavě**, pak klikněte na tlačítko **OK**.  
  
    ![Motiv tmavé barvy vybrané](../ide/media/exploreide-darkthemeoptionsdlgbox.png "ExploreIDE Darkthemeoptionsdlgbox")  
  
   Barvy v systému Visual Studio by měly odpovídat následujícímu obrázku:  
  
   ![Integrované vývojové prostředí s tmavý motiv](../ide/media/exploreide-darkthemeide.png "ExploreIDE DarkThemeIDE")  
  
   Barevný motiv použit pro obrázky ve zbývající části tohoto návodu je světlý motiv. Další informace o úpravách rozhraní IDE naleznete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
##  <a name="BKMK_CreateApp"></a> Vytvoření jednoduché aplikace  
  
### <a name="create-the-project"></a>Vytvoření projektu  
 Při vytváření aplikace v systému Visual Studio je třeba nejprve vytvořit projekt a řešení. V tomto příkladu vytvoříte projekt Windows Presentation Foundation (WPF).  
  
##### <a name="to-create-the-wpf-project"></a>Vytvoření projektu WPF  
  
1. Vytvořte nový projekt. V panelu nabídky zvolte **souboru**, **nový**, **projektu...** .  
  
    ![Na panelu nabídek zvolte soubor, nový, projekt](../ide/media/exploreide-filenewproject.png "ExploreIDE FileNewProject")  
  
    Můžete také zadat **nový projekt** v **Snadné spuštění** pole stejnou věc udělat.  
  
    ![V dialogovém okně Snadné spuštění zadat nový projekt](../ide/media/exploreide-quicklaunchnewprojectsmall.png "ExploreIDE QuickLaunchNewProjectsmall")  
  
2. Výběrem v levém podokně vyberte šablonu aplikace WPF Visual C# nebo Visual Basic **nainstalováno**, **šablony**, **Visual C#**, **Windows**, například a následným výběrem aplikace WPF v prostředním podokně.  Projekt pojmenujte HelloWPFApp v dolní části dialogového okna Nový projekt.  
  
    ![Vytvoření projektu WPF Visual Basic, HelloWPFApp](../ide/media/exploreide-newprojectvb.png "ExploreIDE NewProjectVB")  
  
    NEBO  
  
    ![Vytvoření a Visual C&#35; projekt WPF, HelloWPFApp](../ide/media/exploreide-newprojectcsharp.png "ExploreIDE NewProjectcsharp")  
  
   Visual Studio vytvoří projekt aplikace HelloWPFApp a řešení a **Průzkumníka řešení** zobrazuje různé soubory. Návrhář WPF ukazuje v rozděleném zobrazení návrhové a XAML přehled souboru MainWindow.xaml. Můžete snímků rozdělovač, abyste viděli víc nebo míň buď zobrazení.  Můžete zobrazit pouze vizuální zobrazení nebo pouze zobrazení XAML. (Další informace najdete v tématu [WPF Designer pro Windows Forms vývojáři](http://msdn.microsoft.com/en-us/47ad0909-e89b-4996-b4ac-874d929f94ca)). Následující položky se zobrazí v **Průzkumníka řešení**:  
  
   Obrázek 5: Položky projektu  
  
   ![Průzkumník řešení se soubory HelloWPFApp načíst](../ide/media/exploreide-hellowpfappfiles.png "ExploreIDE HelloWPFAppFiles")  
  
   Poté, co jste projekt vytvořili, jej můžete upravit. S použitím **vlastnosti** okna (v **zobrazení** nabídky), můžete zobrazit a změnit možnosti položek projektu, ovládacích prvků a dalších položek v aplikaci. Pomocí vlastností projektu a stránek vlastností můžete zobrazit a změnit možnosti projektů a řešení.  
  
##### <a name="to-change-the-name-of-mainwindowxaml"></a>Změna názvu souboru MainWindow.xaml  
  
1. V následujícím postupu pojmenujete okno MainWindow konkrétněji. V **Průzkumníka řešení**, vyberte soubor MainWindow.xaml. By se měla zobrazit **vlastnosti** okna, ale pokud ne, zvolte **zobrazení** nabídky a **okně s vlastnostmi** položky. Změnit **název_souboru** vlastnost `Greetings.xaml`.  
  
    ![Okno vlastností se zvýrazněným názvem souboru](../ide/media/exploreide-filenameinpropertieswindow.png "ExploreIDE FilenameinPropertiesWindow")  
  
    **Průzkumník řešení** ukazuje, že název souboru je nyní Greetings.xaml, a pokud rozbalte soubor MainWindow.xaml uzlu (o vložení fokus v uzlu a stisknutím klávesy šipka vpravo), zobrazí se název souboru MainWindow.xaml.vb nebo MainWindow.xaml.cs je nyní Greetings.XAML.vb, případně Greetings.xaml.cs. Souboru s tímto kódem je vnořená v uzlu souboru .xaml lze zobrazit, že jsou velmi úzce souvisí k sobě navzájem.  
  
   > [!WARNING]
   >  Tato změna způsobí chybu, kterou zjistíte později během ladění a opravování.  
  
2. V **Průzkumníka řešení**, otevřete soubor Greetings.xaml v Návrháři (stisknutím klávesy Enter během uzel má fokus) a klikněte do záhlaví okna pomocí myši.  
  
3. V **vlastnosti** okna, změňte hodnotu **Title** vlastnost `Greetings`.  
  
   V záhlaví okna souboru MainWindow.xaml je nyní napsáno Greetings.  
  
### <a name="design-the-user-interface-ui"></a>Návrh uživatelského rozhraní (UI)  
 Nyní do této aplikace přidáme tři typy ovládacích prvků: ovládací prvek TextBlock, dva ovládací prvky RadioButton a ovládací prvek Button.  
  
##### <a name="to-add-a-textblock-control"></a>Přidání ovládacího prvku TextBlock  
  
1. Otevřít **nástrojů** okno výběrem **zobrazení** nabídky a **nástrojů** položky.  
  
2. V **nástrojů**, vyhledejte ovládací prvek TextBlock.  
  
    ![Panel nástrojů s zvýrazněný ovládací prvek TextBlock](../ide/media/exploreide-textblocktoolbox.png "ExploreIDE TextBlockToolbox")  
  
3. Přidejte ovládací prvek TextBlock do návrhové plochy výběrem položky TextBlock a jeho přetažením na návrhové ploše v okně.  Vycentrujte v horní části okna.  
  
   Okno aplikace by mělo vypadat jako na následujícím obrázku:  
  
   Obrázek 7: Okno Greetings s ovládacím prvkem TextBlock  
  
   ![TextBlock – ovládací prvek na formuláři Greetings](../ide/media/exploreide-greetingswithtextblockonly.png "ExploreIDE GreetingswithTextblockonly")  
  
   Značka XAML by měla vypadat následovně:  
  
```  
<TextBlock HorizontalAlignment="Center" TextWrapping="Wrap" VerticalAlignment="Center" RenderTransformOrigin="4.08,2.312" Margin="237,57,221,238"><Run Text="TextBlock"/><InlineUIContainer><TextBlock TextWrapping="Wrap" Text="TextBlock"/>  
```  
  
##### <a name="to-customize-the-text-in-the-text-block"></a>Úprava textu v textovém bloku  
  
1. V XAML zobrazení najděte značku pro TextBlock a změňte atributu Text: `Text=”Select a message option and then choose the Display button.”`  
  
2. Pokud ovládacím prvku TextBlock v návrhovém zobrazení podle Nerozbaluje, zvětšete TextBlock – ovládací prvek (s použitím zobrazily úchyty na okrajích) tak, aby zobrazil celý text.  
  
3. Uložte změny stisknutím Ctrl + s nebo pomocí **souboru** položky nabídky.  
  
   V dalším kroku přidejte dva [RadioButton](http://msdn.microsoft.com/library/6c9ba847-eab7-4bba-9c74-6b56ef72067b) ovládací prvky do formuláře.  
  
##### <a name="to-add-radio-buttons"></a>Přidání přepínačů  
  
1. V **nástrojů**, vyhledejte ovládací prvek RadioButton.  
  
    ![Okno nástrojů s vybraným ovládacím prvkem RadioButton](../ide/media/exploreide-radiobuttontoolbox.png "ExploreIDE RadioButtonToolbox")  
  
2. Přidejte dva ovládací prvky RadioButton návrhu surface výběr položek ovládacího prvku RadioButton a jeho přetažením na okno na návrhové ploše dvakrát a přesunete tlačítka (tak, že je vyberete a pomocí šipkových kláves) tak, aby tlačítek se zobrazí vedle sebe v ovládacím prvku TextBlock ovládací prvek.  
  
    Okno aplikace by mělo vypadat takto:  
  
    Obrázek 8: Přepínače v okně Greetings.  
  
    ![Greetings formuláře s textblock a dvě radiobuttons](../ide/media/exploreide-greetingswithradiobuttons.png "ExploreIDE Greetingswithradiobuttons")  
  
3. V **vlastnosti** okně levém ovládacího prvku RadioButton přepište **název** vlastností (vlastnost v horní části **vlastnosti** okno) k `RadioButton1`.  Ujistěte se, že jste zvolili ovládací prvek RadioButton a nikoli na pozadí mřížky na formuláři. pole s typem okna vlastností. název pole by mělo být uvedeno RadioButton.  
  
4. V **vlastnosti** okno pravého ovládacího prvku RadioButton, změna **název** vlastnost `RadioButton2`a potom uložte změny stisknutím Ctrl + s nebo pomocí **souboru**položky nabídky.  Ujistěte se, že je vybraný ovládací prvek RadioButton před změnou a ukládání.  
  
   Nyní můžete zadat text k zobrazení u obou ovládacích prvků RadioButton. Následující postup aktualizuje **obsahu** vlastnost ovládacího prvku RadioButton.  
  
##### <a name="to-add-display-text-for-each-radio-button"></a>Přidání textu k zobrazení u obou přepínačů  
  
1. Na návrhové ploše otevřete místní nabídku ovládacího prvku radiobutton1 stisknutím pravého tlačítka myši při výběru ovládacího prvku RadioButton1, vyberte možnost **upravit Text**a pak zadejte `Hello`.  
  
2. Otevřete místní nabídku ovládacího prvku RadioButton2 stisknutím pravého tlačítka myši při výběru ovládacího prvku RadioButton2, vyberte možnost **upravit Text**a pak zadejte `Goodbye`.  
  
   Je poslední prvek uživatelského rozhraní, které přidáte [tlačítko](http://msdn.microsoft.com/library/a9d8f5a5-c98c-463e-808a-5a4e63173098) ovládacího prvku.  
  
##### <a name="to-add-the-button-control"></a>Přidání ovládacího prvku tlačítka  
  
1. V **nástrojů**, vyhledejte **tlačítko** ovládací prvek a pak přidat na návrhovou plochu pod ovládací prvky RadioButton tlačítka a jeho přetažením na formulář v nástrojích pro zobrazení návrhu.  
  
2. V XAML zobrazení, změňte hodnotu **obsahu** ovládacího prvku tlačítko z `Content=”Button”` k `Content=”Display”`a následně změny uložte (Ctrl + s nebo použití **souboru** nabídky).  
  
    Kód by měl vypadat podobně jako v následujícím příkladu: `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`  
  
   Okno aplikace by mělo vypadat jako na následujícím obrázku.  
  
   Obrázek 9: Konečné uživatelské rozhraní aplikace Greetings  
  
   ![S popisky ovládacích prvků formuláře Greetings](../ide/media/exploreide-greetingswithconrollabels.png "ExploreIDE Greetingswithconrollabels")  
  
### <a name="add-code-to-the-display-button"></a>Přidání kódu k tlačítku Zobrazit  
 Po spuštění aplikace se zobrazí okno se zprávou poté, co uživatel poprvé zvolí přepínač a následně klikne **zobrazení** tlačítko. Objeví se jedno okno se zprávou pro Hello a druhé se zprávou pro Goodbye. Pro vytvoření tohoto chování je nutné do události Button_Click v souboru Greetings.xaml.vb, případně Greetings.xaml.cs, přidat kód.  
  
##### <a name="add-code-to-display-message-boxes"></a>Přidání kódu pro zobrazení oken se zprávami  
  
1.  Na návrhové ploše, poklikejte **zobrazení** tlačítko.  
  
     Otevře se okno s obsahem souboru Greetings.xaml.vb, případně Greetings.xaml.cs, s kurzorem umístěným v události Button_Click. Obslužnou rutinu události click můžete také přidat takto (Pokud vloženého kódu červená vlnovka pod názvy, pravděpodobně není vybrat ovládací prvky RadioButton na návrhové ploše a je přejmenovat):  
  
     V jazyce Visual Basic by měla obslužná rutina události vypadat takto:  
  
    ```vb  
    Private Sub Button_Click_1(sender As Object, e As RoutedEventArgs)  
  
    End Sub  
    ```  
  
     V jazyce Visual C# by měla obslužná rutina události vypadat takto:  
  
    ```csharp  
    private void Button_Click_1(object sender, RoutedEventArgs e)  
    {  
  
    }  
    ```  
  
2.  Pro jazyk Visual Basic zadejte následující kód:  
  
    ```vb  
    If RadioButton1.IsChecked = True Then  
        MessageBox.Show("Hello.")  
    Else RadioButton2.IsChecked = True  
        MessageBox.Show("Goodbye.")  
    End If  
  
    ```  
  
     Pro jazyk Visual C# zadejte následující kód:  
  
    ```  
    if (RadioButton1.IsChecked == true)  
    {  
        MessageBox.Show("Hello.");  
    }  
    else  
    {  
        RadioButton2.IsChecked = true;  
        MessageBox.Show("Goodbye.");  
    }  
    ```  
  
3.  Uložte aplikaci.  
  
##  <a name="BKMK_DebugTest"></a> Ladění a testování aplikace  
 Dále budeme ladit aplikaci, abychom vyhledali chyby a vyzkoušeli, zda se obě okna se zprávami zobrazila správně. V následujících pokynech se dozvíte, jak sestavit a spustit ladicí program, ale později si může přečíst [vytváření aplikací WPF (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c) a [ladění WPF](../debugger/debugging-wpf.md) Další informace.  
  
### <a name="find-and-fix-errors"></a>Vyhledání a oprava chyb  
 V tomto kroku zjistíte chybu, kterou jsme dříve způsobili změnou názvu souboru XAML v hlavním okně.  
  
##### <a name="to-start-debugging-and-find-the-error"></a>Spuštění ladění a vyhledání chyby  
  
1. Spusťte ladicí program výběrem **ladění**, pak **spustit ladění**.  
  
    ![Spuštění ladění příkaz v nabídce ladění](../ide/media/exploreide-startdebugging.png "ExploreIDE StartDebugging")  
  
    Zobrazí se dialogové okno označující, že došlo k výjimce IOException: Nelze najít zdroj „mainwindow.xaml“.  
  
2. Zvolte **OK** tlačítko a následně ukončete ladicí program.  
  
    ![Zastavit ladění příkaz v nabídce ladění](../ide/media/exploreide-stopdebugging.png "ExploreIDE StopDebugging")  
  
   Jsme přejmenovali soubor Mainwindow.xaml na Greetings.xaml na začátku tohoto názorného postupu, ale kód stále odkazuje na soubor Mainwindow.xaml jako spouštěcího identifikátoru URI pro aplikace, takže projekt nemůže spustit.  
  
##### <a name="to-specify-greetingsxaml-as-the-startup-uri"></a>Určení souboru Greetings.xaml jako spouštěcího identifikátoru URI  
  
1. V **Průzkumníka řešení**, otevřete soubor App.xaml (C# projekt) nebo Application.XAML (v projektu jazyka Visual Basic) v zobrazení XAML (nemůže být otevřen v návrhovém zobrazení), výběr souboru a stisknutím klávesy Enter nebo double že na něj kliknete.  
  
2. Změna `StartupUri="MainWindow.xaml"` k `StartupUri="Greetings.xaml"`a následně změny uložte pomocí Ctrl + s.  
  
   Spuštění ladicího programu znovu (stisknutím klávesy F5). Měli byste vidět okno Greetings aplikace.  
  
### <a name="to-debug-with-breakpoints"></a>Ladění se zarážkami  
 Přidáním zarážek lze otestovat kód během ladění. Zarážky lze přidat zvolením **ladění** v hlavní nabídce pak **Přepnout zarážku** nebo kliknutím do levého okraje editoru vedle řádku kódu, kde chcete, aby se zarážka objevila.  
  
##### <a name="to-add-breakpoints"></a>Přidání zarážek  
  
1.  Otevřete soubor Greetings.xaml.vb, případně Greetings.xaml.cs a vyberte následující řádek: `MessageBox.Show("Hello.")`  
  
2.  Přidáte zarážku z nabídky vyberte **ladění**, pak **Přepnout zarážku**.  
  
     ![Přepnout zarážku – příkaz v nabídce ladění](../ide/media/exploreide-togglebreakpoint.png "ExploreIDE togglebreakpoint –")  
  
     Na levém okraji okna editoru se vedle řádku kódu zobrazí červený kruh.  
  
3.  Vyberte následující řádek: `MessageBox.Show("Goodbye.")`.  
  
4.  Stiskněte klávesu F9 pro přidání zarážky a potom stiskněte klávesu F5 pro spuštění ladění.  
  
5.  V **Greetings** okna, vyberte **Hello** přepínač a klikněte na tlačítko **zobrazení** tlačítko.  
  
     Na řádku `MessageBox.Show("Hello.")` je zvýrazněn žlutě. V dolní části rozhraní IDE, automatické hodnoty, místní hodnoty a sledování systému windows jsou ukotveny na levé straně a okna zásobník volání, zarážky, příkaz, okamžité a výstup jsou ukotveny na pravé straně.  
  
6.  V panelu nabídky zvolte **ladění**, **Krokovat s Vystoupením**.  
  
     Aplikace bude pokračovat v provádění a zobrazí se okno se zprávou obsahující slovo „Hello“.  
  
7.  Zvolte **OK** tlačítko na okno zpráv zavřete ho.  
  
8.  V **Greetings** okna, vyberte **Goodbye** přepínač a klikněte na tlačítko **zobrazení** tlačítko.  
  
     Na řádku `MessageBox.Show("Goodbye.")` je zvýrazněn žlutě.  
  
9. Pro pokračování v ladění stiskněte klávesu F5. Když se objeví okno se zprávou, klikněte **OK** tlačítko na okno zpráv zavřete ho.  
  
10. Stiskněte SHIFT + F5 klíče (stiskněte klávesu shift nejprve a podržte stisknutou klávesu F5) pro zastavení ladění.  
  
11. V panelu nabídky zvolte **ladění**, **zakázat všechny zarážky**.  
  
### <a name="build-a-release-version-of-the-application"></a>Sestavení verze pro vydání aplikace  
 Nyní poté, co jste ověřili, že vše funguje, jak má, lze připravit sestavení pro vydání aplikace.  
  
##### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Vyčištění souborů řešení a sestavení verze pro vydání  
  
1. V hlavní nabídce vyberte **sestavení**, pak **Vyčistit řešení** k odstranění pomocných a výstupních souborů, které byly během předchozích sestavení vytvořeny.  To není nezbytné, ale jeho vyčistí výstupy sestavení ladění.  
  
    ![Příkaz Vyčistit řešení v nabídce sestavení](../ide/media/exploreide-cleansolution.png "ExploreIDE CleanSolution")  
  
2. Změňte nastavení sestavení aplikace hellowpfapp z **ladění** k **vydání** pomocí ovládacího prvku rozevíracího seznamu na panelu nástrojů (stavu "Ladění" aktuálně).  
  
    ![Standardní panel nástrojů verze vybraná](../ide/media/exploreide-releaseversion.png "ExploreIDE ReleaseVersion")  
  
3. Sestavte řešení výběrem **sestavení**, pak **sestavit řešení** nebo stiskněte klávesu F6.  
  
    ![Sestavit řešení – příkaz v nabídce sestavení](../ide/media/exploreide-buildsolution.png "ExploreIDE BuildSolution")  
  
   Blahopřejeme k dokončení tohoto návodu! Můžete najít .exe vytvořeným v adresáři řešení a projektu (...\HelloWPFApp\HelloWPFApp\bin\Release\\). Pokud budete chtít projít Další příklady, přečtěte si téma [ukázky sady Visual Studio](../ide/visual-studio-samples.md).  
  
## <a name="see-also"></a>Viz také  
 [Co je nového v sadě Visual Studio 2015](../what-s-new-in-visual-studio-2015.md)   
 [Začněte s vývojem pomocí sady Visual Studio](../ide/get-started-developing-with-visual-studio.md)   
 [Tipy pro vyšší produktivitu](../ide/productivity-tips-for-visual-studio.md)



