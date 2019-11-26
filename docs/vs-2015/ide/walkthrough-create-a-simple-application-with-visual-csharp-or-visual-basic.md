---
title: 'Návod: Vytvoření jednoduché aplikace s jazykem Visual C# nebo Visual Basic | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5e41dbf3422374add68e351da1e4b703772a3a4
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296852"
---
# <a name="walkthrough-create-a-simple-application-with-visual-c-or-visual-basic"></a>Návod: Vytvoření jednoduché aplikace s použitím jazyka Visual C# nebo Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto návodu se seznámíte s mnoha nástroji, dialogovými okny a návrháři, které lze použít při vývoji aplikací pomocí systému Visual Studio. Vytvoříte jednoduchou aplikaci ve stylu „Hello World“, navrhnete uživatelské rozhraní (UI), vložíte kód a budete ladit chyby. A přitom získáte zkušenosti s prací v integrovaném vývojovém prostředí (IDE).

 Toto téma obsahuje následující oddíly:

 [Konfigurace integrovaného vývojového prostředí](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_ConfigureIDE)

 [Vytvoření jednoduché aplikace](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_CreateApp)

 [Ladění a testování aplikace](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_DebugTest)

> [!NOTE]
> Tento návod vychází ze systému Visual Studio Professional, který nabízí šablonu aplikace WPF, na které vytvoříte projekt pro tento návod. Visual Studio Express pro stolní počítače se systémem Windows tuto šablonu nabízí také, ale Visual Studio Express pro Windows a Visual Studio Express pro Web nikoli. Úvodní informace o tom, jak používat Visual Studio Express pro Windows, najdete v [centru pro vývojáře pro aplikace pro Windows Store](https://msdn.microsoft.com/windows/apps/br229519). Úvodní informace o tom, jak používat Visual Studio Express pro web, najdete v tématu Začínáme [s ASP.NET](https://dotnet.microsoft.com/learn/aspnet/hello-world-tutorial/intro). Vaše verze aplikace Visual Studio a nastavení, která používáte, určují také názvy a umístění některých prvků uživatelského rozhraní. Viz [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="BKMK_ConfigureIDE"></a>Konfigurace integrovaného vývojového prostředí
 Při prvním spuštění sady Visual Studio se zobrazí výzva, abyste se přihlásili pomocí účtu služby Microsoft (MSA) a [přihlásili se k aplikaci Visual Studio](https://devblogs.microsoft.com/visualstudio/welcome-sign-in-to-visual-studio/). Nemusíte se přihlašovat a můžete to provést později.

 V sadě Visual Studio Launch (další) musíte zvolit kombinaci nastavení, která aplikuje sadu předdefinovaných úprav na integrované vývojové prostředí (IDE). Každá kombinace nastavení byla navržena za účelem usnadnění vývoje aplikací.

 Tento názorný postup předpokládá, že jste použili **Obecná nastavení pro vývoj**, která v IDE aplikuje nejmenší množství přizpůsobení. Pokud jste už zvolili C# nebo Visual Basici (jsou to dobrá volba), nemusíte měnit nastavení.  Pokud chcete změnit nastavení, můžete použít **Průvodce importem a exportem nastavení**. Viz [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Po otevření sady Visual Studio lze rozeznat okna nástrojů, nabídky, panely nástrojů a prostor hlavního okna. Okna nástrojů jsou ukotvena na levé a pravé straně okna aplikace, s možností **snadného spuštění**, řádku nabídek a standardní panel nástrojů v horní části. Ve středu okna aplikace je **Úvodní stránka**. Při načítání řešení nebo projektu se zobrazí editory a návrháři v prostoru, kde je **Úvodní stránka** . Při vývoji aplikace strávíte nejvíce času v této centrální oblasti.

 Obrázek 2: Integrované vývojové prostředí (IDE) systému Visual Studio

 ![Integrované vývojové prostředí (IDE) s použitím obecného nastavení](../ide/media/exploreide-idewithgeneralsettings.png "ExploreIDE-IDEwithgeneralsettings")

 Můžete provést další úpravy sady Visual Studio, jako je například Změna řezu písma a velikost textu v editoru nebo barevný motiv integrovaného vývojového prostředí (IDE) pomocí dialogového okna **Možnosti** . V závislosti na kombinaci použitého nastavení se některé položky v tomto dialogovém okně nemusejí automaticky zobrazit. Zaškrtnutím políčka **Zobrazit všechna nastavení** můžete zajistit, aby se zobrazily všechny možné možnosti.

 Obrázek 3: Dialogové okno Možnosti

 ![Dialogové okno Možnosti wirh Zobrazit všechna nastavení](../ide/media/exploreide-optionsdialogbox.png "ExploreIDE-Optionsdialogbox")

 V tomto příkladu změníte barevný motiv integrovaného vývojového prostředí (IDE) ze světlého na tmavé.  Pokud chcete, můžete přeskočit na vytvoření projektu.

#### <a name="to-change-the-color-theme-of-the-ide"></a>Změna barevného motivu prostředí IDE

1. Otevřete dialogové okno **Možnosti** tak, že v horní části vyberete nabídku **nástroje** a pak zvolíte **možnost...** položkami.

    ![Příkaz Možnosti v nabídce nástroje](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE-ToolsOptionsmenu")

2. Změňte **barevný motiv** na **tmavý**a pak klikněte na **OK**.

    ![Vybrán tmavý barevný motiv](../ide/media/exploreide-darkthemeoptionsdlgbox.png "ExploreIDE-Darkthemeoptionsdlgbox")

   Barvy v systému Visual Studio by měly odpovídat následujícímu obrázku:

   ![Použité IDE s tmavým motivem](../ide/media/exploreide-darkthemeide.png "ExploreIDE-DarkThemeIDE")

   Barevný motiv, který se používá pro obrázky ve zbývající části tohoto návodu, je světlý motiv. Další informace o přizpůsobení rozhraní IDE naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="BKMK_CreateApp"></a>Vytvoření jednoduché aplikace

### <a name="create-the-project"></a>Vytvoření projektu
 Při vytváření aplikace v systému Visual Studio je třeba nejprve vytvořit projekt a řešení. V tomto příkladu vytvoříte projekt Windows Presentation Foundation (WPF).

##### <a name="to-create-the-wpf-project"></a>Vytvoření projektu WPF

1. Vytvořte nový projekt. Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt...** .

    ![Na panelu nabídek vyberte možnosti soubor, nový, projekt.](../ide/media/exploreide-filenewproject.png "ExploreIDE-FileNewProject")

    Stejný postup můžete provést také zadáním **nového projektu** do pole **Snadné spuštění** .

    ![V poli snadné spuštění zadejte nový projekt.](../ide/media/exploreide-quicklaunchnewprojectsmall.png "ExploreIDE-QuickLaunchNewProjectsmall")

2. Zvolte Visual Basic nebo šablonu aplikace Visual C# WPF výběrem v levém podokně **nainstalovaném**, **šablonách**, **C#vizuálu**, **oknech**, například a volbou aplikace WPF v prostředním podokně.  Pojmenujte projekt HelloWPFApp v dolní části dialogového okna Nový projekt.

    ![Vytvoření projektu Visual Basic WPF, HelloWPFApp](../ide/media/exploreide-newprojectvb.png "ExploreIDE-NewProjectVB")

    NEBO

    ![Vytvoření projektu Visual C++&#35; WPF, HelloWPFApp](../ide/media/exploreide-newprojectcsharp.png "ExploreIDE-NewProjectcsharp")

   Visual Studio vytvoří projekt a řešení HelloWPFApp a **Průzkumník řešení** zobrazí různé soubory. Návrhář WPF zobrazuje návrhové zobrazení a zobrazení XAML souboru MainWindow. XAML v rozděleném zobrazení. Posunutí příčky můžete zobrazit více nebo méně z obou zobrazení.  Můžete zvolit, zda chcete zobrazit pouze vizuální zobrazení nebo pouze zobrazení XAML. (Další informace najdete v tématu [Návrhář WPF pro model Windows Forms vývojáře](https://msdn.microsoft.com/47ad0909-e89b-4996-b4ac-874d929f94ca)). V **Průzkumník řešení**se zobrazí následující položky:

   Obrázek 5: Položky projektu

   ![Průzkumník řešení se načetly soubory HelloWPFApp](../ide/media/exploreide-hellowpfappfiles.png "ExploreIDE-HelloWPFAppFiles")

   Poté, co jste projekt vytvořili, jej můžete upravit. Pomocí okna **vlastnosti** (naleznete v nabídce **zobrazení** ) můžete zobrazit a změnit možnosti položek projektu, ovládacích prvků a dalších položek v aplikaci. Pomocí vlastností projektu a stránek vlastností můžete zobrazit a změnit možnosti projektů a řešení.

##### <a name="to-change-the-name-of-mainwindowxaml"></a>Změna názvu souboru MainWindow.xaml

1. V následujícím postupu pojmenujete okno MainWindow konkrétněji. V **Průzkumník řešení**vyberte MainWindow. XAML. Měli byste vidět okno **vlastnosti** , ale v případě potřeby vyberte nabídku **zobrazení** a položku **okna vlastností** . Změňte vlastnost **název souboru** na `Greetings.xaml`.

    ![okno Vlastnosti se zvýrazněným názvem souboru](../ide/media/exploreide-filenameinpropertieswindow.png "ExploreIDE-FilenameinPropertiesWindow")

    **Průzkumník řešení** ukazuje, že název souboru je nyní Greetings. XAML a když rozbalíte uzel MainWindow. XAML (tak, že umístíte fokus do uzlu a stisknete rightarrow klíč), zobrazí se název MainWindow. XAML. vb nebo MainWindow.XAML.cs je nyní Greetings. XAML. vb nebo Greetings.XAML.cs. Tento soubor kódu je vnořený pod uzlem souboru. XAML, aby zobrazoval, že jsou velmi úzce spojeny.

   > [!WARNING]
   > Tato změna způsobí chybu, kterou zjistíte později během ladění a opravování.

2. V **Průzkumník řešení**otevřete soubor Greetings. XAML v zobrazení návrháře (stisknutím klávesy ENTER, když má uzel fokus) a vyberte záhlaví okna pomocí myši.

3. V okně **vlastnosti** změňte hodnotu vlastnosti **title** na `Greetings`.

   V záhlaví okna souboru MainWindow.xaml je nyní napsáno Greetings.

### <a name="design-the-user-interface-ui"></a>Návrh uživatelského rozhraní (UI)
 Nyní do této aplikace přidáme tři typy ovládacích prvků: ovládací prvek TextBlock, dva ovládací prvky RadioButton a ovládací prvek Button.

##### <a name="to-add-a-textblock-control"></a>Přidání ovládacího prvku TextBlock

1. Otevřete okno **panelu nástrojů** výběrem nabídky **zobrazení** a položky **panelu nástrojů** .

2. V sadě **nástrojů**vyhledejte ovládací prvek TextBlock.

    ![Sada nástrojů se zvýrazněným ovládacím prvkem TextBlock](../ide/media/exploreide-textblocktoolbox.png "ExploreIDE-TextBlockToolbox")

3. Přidejte ovládací prvek TextBlock do návrhové plochy tak, že vyberete položku TextBlock a přetáhnete ji do okna na návrhové ploše.  Vycentrovat ovládací prvek v horní části okna.

   Okno aplikace by mělo vypadat jako na následujícím obrázku:

   Obrázek 7: Okno Greetings s ovládacím prvkem TextBlock

   ![TextBlock ovládacího prvku na formuláři Greetings](../ide/media/exploreide-greetingswithtextblockonly.png "ExploreIDE-GreetingswithTextblockonly")

   Značka XAML by měla vypadat následovně:

```
<TextBlock HorizontalAlignment="Center" TextWrapping="Wrap" VerticalAlignment="Center" RenderTransformOrigin="4.08,2.312" Margin="237,57,221,238"><Run Text="TextBlock"/><InlineUIContainer><TextBlock TextWrapping="Wrap" Text="TextBlock"/>
```

##### <a name="to-customize-the-text-in-the-text-block"></a>Úprava textu v textovém bloku

1. V zobrazení XAML vyhledejte značku pro TextBlock a změňte atribut text: `Text=”Select a message option and then choose the Display button.”`

2. Pokud se TextBlock nerozšíří tak, aby se vešla do zobrazení Návrh, zvětšete ovládací prvek TextBlock (pomocí táhel úchytů na hranách), aby se zobrazil celý text.

3. Změny uložte stisknutím kombinace kláves CTRL + s nebo pomocí položky nabídky **soubor** .

   Dále do formuláře přidejte dva ovládací prvky [RadioButton](https://msdn.microsoft.com/library/6c9ba847-eab7-4bba-9c74-6b56ef72067b) .

##### <a name="to-add-radio-buttons"></a>Přidání přepínačů

1. V sadě **nástrojů**vyhledejte ovládací prvek RadioButton.

    ![Okno panelu nástrojů s vybraným ovládacím prvkem RadioButton](../ide/media/exploreide-radiobuttontoolbox.png "ExploreIDE-RadioButtonToolbox")

2. Přidejte dva ovládací prvky RadioButton na návrhovou plochu tak, že vyberete položku RadioButton a přetáhnete ji do okna na návrhové ploše dvakrát a přesunete tlačítka (tak, že je vyberete a použijete klávesy se šipkami), aby se tlačítka zobrazovala vedle sebe pod TextBlock nad.

    Okno aplikace by mělo vypadat takto:

    Obrázek 8: Přepínače v okně Greetings.

    ![Formulář s pozdravem s TextBlock a dvěma přepínači](../ide/media/exploreide-greetingswithradiobuttons.png "ExploreIDE-Greetingswithradiobuttons")

3. V okně **vlastnosti** levého ovládacího prvku RadioButton změňte vlastnost **Name** (vlastnost v horní části okna **vlastnosti** ) na `RadioButton1`.  Ujistěte se, že jste vybrali přepínač RadioButton a nikoli mřížku na pozadí ve formuláři. pole typ v okně vlastností pod polem název by měl vyslovit RadioButton.

4. V okně **vlastnosti** pravého ovládacího prvku RadioButton změňte vlastnost **Name** na `RadioButton2`a poté změny uložte stisknutím kombinace kláves CTRL-s nebo pomocí položky nabídky **soubor** .  Před změnou a uložením je třeba vybrat přepínač RadioButton.

   Nyní můžete zadat text k zobrazení u obou ovládacích prvků RadioButton. Následující postup aktualizuje vlastnost **obsah** ovládacího prvku RadioButton.

##### <a name="to-add-display-text-for-each-radio-button"></a>Přidání textu k zobrazení u obou přepínačů

1. Na návrhové ploše otevřete místní nabídku pro RadioButton1 tak, že stisknete pravé tlačítko myši a vyberete RadioButton1, zvolíte **Upravit text**a pak zadáte `Hello`.

2. Otevřete místní nabídku pro RadioButton2 tak, že stisknete pravé tlačítko myši a vyberete RadioButton2, zvolíte příkaz **Upravit text**a potom zadáte `Goodbye`.

   Konečný prvek uživatelského rozhraní, který přidáte, je ovládací prvek [tlačítko](https://msdn.microsoft.com/library/a9d8f5a5-c98c-463e-808a-5a4e63173098) .

##### <a name="to-add-the-button-control"></a>Přidání ovládacího prvku tlačítka

1. V sadě **nástrojů**vyhledejte ovládací prvek **tlačítko** a pak ho přidejte na návrhovou plochu pod ovládacími prvky RadioButton tak, že vyberete tlačítko a přetáhnete ho do formuláře v zobrazení Návrh.

2. V zobrazení XAML změňte hodnotu **obsahu** pro ovládací prvek tlačítko z `Content=”Button”` na `Content=”Display”`a pak změny uložte (CTRL + s nebo použijte nabídku **soubor** ).

    Značka by měla vypadat podobně jako v následujícím příkladu: `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`

   Okno aplikace by mělo vypadat jako na následujícím obrázku.

   Obrázek 9: Konečné uživatelské rozhraní aplikace Greetings

   ![Formulář s pozdravem s popisky ovládacích prvků](../ide/media/exploreide-greetingswithconrollabels.png "ExploreIDE-Greetingswithconrollabels")

### <a name="add-code-to-the-display-button"></a>Přidání kódu k tlačítku Zobrazit
 Po spuštění této aplikace se zobrazí okno se zprávou, když uživatel poprvé zvolí přepínač a pak zvolí tlačítko pro **zobrazení** . Objeví se jedno okno se zprávou pro Hello a druhé se zprávou pro Goodbye. Pro vytvoření tohoto chování je nutné do události Button_Click v souboru Greetings.xaml.vb, případně Greetings.xaml.cs, přidat kód.

##### <a name="add-code-to-display-message-boxes"></a>Přidání kódu pro zobrazení oken se zprávami

1. Na návrhové ploše poklikejte na tlačítko **Zobrazit** .

     Otevře se okno s obsahem souboru Greetings.xaml.vb, případně Greetings.xaml.cs, s kurzorem umístěným v události Button_Click. Můžete také přidat obslužnou rutinu události Click následujícím způsobem (Pokud má vložený kód červenou vlnovku pod všemi názvy, pak jste pravděpodobně nevybrali ovládací prvky RadioButton na návrhové ploše a přejmenovaly je):

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

2. Pro jazyk Visual Basic zadejte následující kód:

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

3. Uložte aplikaci.

## <a name="BKMK_DebugTest"></a>Ladění a testování aplikace
 Dále budeme ladit aplikaci, abychom vyhledali chyby a vyzkoušeli, zda se obě okna se zprávami zobrazila správně. V následujících pokynech se dozvíte, jak sestavit a spustit ladicí program, ale později si můžete přečíst téma [Vytvoření aplikace WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c) a [ladění WPF](../debugger/debugging-wpf.md) pro další informace.

### <a name="find-and-fix-errors"></a>Vyhledání a oprava chyb
 V tomto kroku zjistíte chybu, kterou jsme dříve způsobili změnou názvu souboru XAML v hlavním okně.

##### <a name="to-start-debugging-and-find-the-error"></a>Spuštění ladění a vyhledání chyby

1. Spusťte ladicí program tak, že vyberete **ladění**a potom **zahájíte ladění**.

    ![Spustit ladění – příkaz v nabídce ladění](../ide/media/exploreide-startdebugging.png "ExploreIDE-StartDebugging")

    Zobrazí se dialogové okno označující, že došlo k výjimce IOException: Nelze najít zdroj „mainwindow.xaml“.

2. Klikněte na tlačítko **OK** a potom ukončete ladicí program.

    ![Zastavit ladění – příkaz v nabídce ladění](../ide/media/exploreide-stopdebugging.png "ExploreIDE-StopDebugging")

   Přejmenovali jsme MainWindow. XAML na Greetings. XAML na začátku tohoto Názorného postupu, ale kód stále odkazuje na MainWindow. XAML jako spouštěcí identifikátor URI pro aplikaci, takže projekt nejde spustit.

##### <a name="to-specify-greetingsxaml-as-the-startup-uri"></a>Určení souboru Greetings.xaml jako spouštěcího identifikátoru URI

1. V **Průzkumník řešení**otevřete soubor App. XAML (v C# projektu) nebo soubor Application. xaml (v projektu Visual Basic) v zobrazení XAML (nemůže být otevřen v zobrazení Návrh) tím, že ho vyberete a stisknete klávesu ENTER nebo dvakrát kliknete na něj.

2. Změňte `StartupUri="MainWindow.xaml"` na `StartupUri="Greetings.xaml"`a pak změny uložte pomocí kombinace kláves CTRL + s.

   Znovu spusťte ladicí program (stiskněte klávesu F5). Měli byste vidět okno Greetings aplikace.

### <a name="to-debug-with-breakpoints"></a>Ladění se zarážkami
 Přidáním zarážek lze otestovat kód během ladění. Zarážky lze přidat kliknutím na možnost **ladění** v hlavní nabídce a následným kliknutím na položku **Přepnout zarážku** nebo kliknutím na levý okraj editoru vedle řádku kódu, kde chcete, aby došlo k přerušení.

##### <a name="to-add-breakpoints"></a>Přidání zarážek

1. Otevřete soubor Greetings. XAML. vb nebo Greetings.xaml.cs a vyberte následující řádek: `MessageBox.Show("Hello.")`

2. Přidejte zarážku z nabídky tak, že vyberete **ladění**a potom **přepnete zarážku**.

     ![Přepnout zarážku – příkaz v nabídce ladění](../ide/media/exploreide-togglebreakpoint.png "ExploreIDE – Togglebreakpoint –")

     Na levém okraji okna editoru se vedle řádku kódu zobrazí červený kruh.

3. Vyberte následující řádek: `MessageBox.Show("Goodbye.")`.

4. Stisknutím klávesy F9 přidejte zarážku a potom stiskněte klávesu F5 pro spuštění ladění.

5. V okně **Greetings** vyberte přepínač **Hello** a pak klikněte na tlačítko **Zobrazit** .

     Čára `MessageBox.Show("Hello.")` je zvýrazněna žlutou. V dolní části rozhraní IDE jsou okna Automatické hodnoty, místní hodnoty a kukátka ukotvena na levé straně a v oknech zásobník volání, zarážky, příkaz, okamžité a výstup jsou ukotveny na pravé straně.

6. Na řádku nabídek klikněte na položku **ladění**, **Krok ven**.

     Aplikace bude pokračovat v provádění a zobrazí se okno se zprávou obsahující slovo „Hello“.

7. Kliknutím na tlačítko **OK** v okně se zprávou ho zavřete.

8. V okně **Greetings** vyberte přepínač rozdálení a pak **klikněte na tlačítko** **Zobrazit** .

     Čára `MessageBox.Show("Goodbye.")` je zvýrazněna žlutou.

9. Pro pokračování v ladění stiskněte klávesu F5. Když se zobrazí okno se zprávou, zavřete ho kliknutím na tlačítko **OK** v okně se zprávou.

10. Stiskněte klávesy SHIFT + F5 (nejprve stiskněte klávesu SHIFT a při jejich držení stiskněte klávesu F5) pro zastavení ladění.

11. Na řádku nabídek klikněte na položku **ladit**a **zakažte všechny zarážky**.

### <a name="build-a-release-version-of-the-application"></a>Sestavení verze pro vydání aplikace
 Nyní poté, co jste ověřili, že vše funguje, jak má, lze připravit sestavení pro vydání aplikace.

##### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Vyčištění souborů řešení a sestavení verze pro vydání

1. V hlavní nabídce vyberte **sestavit**, **Vyčistit řešení** a odstraňte mezilehlé soubory a výstupní soubory, které byly vytvořeny v předchozích sestaveních.  To není nutné, ale čistí výstupy sestavení ladění.

    ![Příkaz vyčistit řešení v nabídce sestavení](../ide/media/exploreide-cleansolution.png "ExploreIDE-CleanSolution")

2. Změňte konfiguraci sestavení pro HelloWPFApp z **Debug** na **release** pomocí ovládacího prvku rozevíracího seznamu na panelu nástrojů (aktuálně říká "ladit").

    ![Standardní panel nástrojů s vybraným vydáním](../ide/media/exploreide-releaseversion.png "ExploreIDE-ReleaseVersion")

3. Sestavte řešení výběrem možnosti **sestavit**, potom **Sestavte řešení** nebo stiskněte klávesu F6.

    ![Příkaz Sestavit řešení v nabídce sestavení](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")

   Blahopřejeme k dokončení tohoto návodu! Můžete najít soubor. exe, který jste vytvořili v rámci vašeho řešení a adresáře projektu (. ..\HelloWPFApp\HelloWPFApp\bin\Release\\). Pokud chcete prozkoumat další příklady, přečtěte si téma [ukázky sady Visual Studio](../ide/visual-studio-samples.md).

## <a name="see-also"></a>Viz také
 [Novinky v aplikaci Visual studio 2015](../what-s-new-in-visual-studio-2015.md) [Začínáme s vývojem v rámci sady Visual Studio](../ide/get-started-developing-with-visual-studio.md) – [tipy pro produktivitu](../ide/productivity-tips-for-visual-studio.md)
