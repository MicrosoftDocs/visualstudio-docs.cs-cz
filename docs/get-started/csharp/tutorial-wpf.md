---
title: 'Hello World aplikace s WPF v C #'
description: Vytvořte jednoduchou aplikaci Windows Desktop .NET v jazyce C# pomocí sady Visual Studio pomocí rozhraní ui služby WPF (Windows Presentation Foundation).
ms.custom: seodec18, get-started
ms.date: 08/09/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ba8a29a75b21351d94c818837f07ff22785a07b5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77579990"
---
# <a name="tutorial-create-a-simple-application-with-c"></a>Kurz: Vytvoření jednoduché aplikace s C\#

Dokončením tohoto kurzu se seznámíte s mnoha nástroji, dialogovými okny a návrháři, které můžete použít při vývoji aplikací s visual studio. Vytvoříte aplikaci "Hello, World", navrhnete ui, přidáte kód a ladíte chyby, zatímco se dozvíte o práci v integrovaném vývojovém prostředí ([IDE](visual-studio-ide.md)).

## <a name="prerequisites"></a>Požadavky

::: moniker range="vs-2017"
Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?) a nainstalujte ji zdarma.
::: moniker-end
::: moniker range=">=vs-2019"

- Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads/) a nainstalujte ji zdarma.
- Pro účely tohoto kurzu můžete použít rozhraní .NET Framework nebo .NET Core. .NET Core je novější, modernější rámec. .NET Core vyžaduje Visual Studio 2019 verze 16.3 nebo novější.
::: moniker-end

## <a name="configure-the-ide"></a>Nastavení integrovaného vývojového prostředí (IDE)

::: moniker range="vs-2017"

Při prvním spuštění sady Visual Studio budete vyzváni k přihlášení. Tento krok je volitelný pro tento kurz. Dále se vám může zobrazit dialogové okno, které vás požádá o výběr nastavení vývoje a barevného motivu. Zachovat výchozí hodnoty a zvolit **Spustit Visual Studio**.

![Dialogové okno Zvolit nastavení](../media/exploreide-settings.png)

Po spuštění sady Visual Studio se zobrazí okna nástrojů, nabídky a panely nástrojů a hlavní prostor okna. Okna nástrojů jsou ukotvena na levé a pravé straně okna aplikace s **panelem snadnéspuštění**, panelu nabídek a standardním panelem nástrojů nahoře. Uprostřed okna aplikace je **úvodní stránka**. Když načtete řešení nebo projekt, editory a návrháři se zobrazí v prostoru, kde je **úvodní stránka.** Když vyvíjíte aplikaci, strávíte většinu svého času v této centrální oblasti.

![IDE sady Visual Studio 2017 s použitým obecným nastavením](../media/exploreide-idewithgeneralsettings.png "Snímek obrazovky s rozhraním IDE sady Visual Studio 2017 s použitým obecným nastavením")

::: moniker-end

::: moniker range=">=vs-2019"

Při spuštění sady Visual Studio se nejprve otevře počáteční okno. Chcete-li otevřít vývojové prostředí, vyberte **možnost Pokračovat bez kódu.** Zobrazí se okna nástrojů, nabídky a panely nástrojů a hlavní prostor okna. Okna nástrojů jsou ukotvena na levé a pravé straně okna aplikace s vyhledávacím polem, panelem nabídek a standardním panelem nástrojů v horní části. Při načtení řešení nebo projektu se v centrálním prostoru okna aplikace zobrazí editory a návrháři. Když vyvíjíte aplikaci, strávíte většinu svého času v této centrální oblasti.

::: moniker-end

## <a name="create-the-project"></a>Vytvoření projektu

Při vytváření aplikace v systému Visual Studio je třeba nejprve vytvořit projekt a řešení. V tomto příkladu vytvoříte projekt Windows Presentation Foundation (WPF).

::: moniker range="vs-2017"

1. Vytvoření nového projektu Na řádku nabídek vyberte **Soubor** > **nového** > **projektu**.

     ![Na řádku nabídek zvolte Soubor, Nový, Projekt](../media/exploreide-filenewproject.png "Snímek obrazovky s panelem nabídek, ve kterém zvolíte Soubor, Nový, Projekt")

1. V dialogovém okně **Nový projekt** vyberte kategorii **Nainstalovaná** > **visual c#** > plocha**systému Windows** a potom vyberte šablonu aplikace **WPF (.NET Framework).** Pojmenujte projekt **HelloWPFApp**a vyberte **OK**.

     ![Šablona aplikace WPF v dialogovém okně Nový projekt Visual Studia](media/exploreide-newprojectcsharp.png "Snímek obrazovky se šablonou aplikace WPF v dialogovém okně Nový projekt")

::: moniker-end

::: moniker range="vs-2019"

1. Otevřete Visual Studio 2019.

1. V počátečním okně zvolte **Vytvořit nový projekt**.

   ![Zobrazit okno Vytvořit nový projekt](../../get-started/media/vs-2019/start-window-create-new-project.png "Snímek obrazovky s oknem Vytvoření nového projektu")

1. Na obrazovce **Vytvořit nový projekt** vyhledejte "WPF", zvolte **WPF App (.NET Core)** a pak zvolte **Další**.

   ![Šablona aplikace WPF v dialogovém okně Vytvořit nový projekt](media/vs-2019/exploreide-newprojectcsharp-vs2019.png "Snímek obrazovky se šablonou aplikace WPF v dialogovém okně Vytvořit nový projekt")

   > [!NOTE]
   > Můžete najít dvě šablony plochy WPF, jednu pro rozhraní .NET Framework a druhou pro rozhraní .NET Core. Šablona .NET Core je k dispozici ve Visual Studiu 2019 verze 16.3 a novější. Můžete použít jeden z nich pro tento kurz, ale doporučujeme .NET Core pro nový vývoj.

1. Na další obrazovce pojmenujte projekt **HelloWPFApp**a zvolte **Vytvořit**.

   ![Pojmenujte svůj projekt 'HelloWPFApp'](./media/vs-2019/exploreide-nameproject.png "Snímek obrazovky s oknem, ve kterém pojmenujete projekt")

::: moniker-end

Visual Studio vytvoří projekt a řešení HelloWPFApp a **Průzkumník řešení** zobrazí různé soubory. **WPF Designer** zobrazuje návrhové zobrazení a zobrazení XAML *MainWindow.xaml* v rozděleném zobrazení. Posunutím rozdělovače můžete zobrazit více či méně z obou zobrazení. Můžete zvolit zobrazení pouze vizuálního zobrazení nebo pouze zobrazení XAML.

![WPF projekt a řešení v IDE](media/exploreide-wpfproject-cs.png "Snímek obrazovky s projektem WPF a řešením v rozhraní IDE")

> [!NOTE]
> Další informace o XAML (eXtensible Application Markup Language) najdete v [přehledu XAML pro](/dotnet/framework/wpf/advanced/xaml-overview-wpf) stránku WPF.

Poté, co jste projekt vytvořili, jej můžete upravit. Chcete-li tak učinit, zvolte **Okno vlastností** z nabídky **Zobrazení** nebo stiskněte **klávesu F4**. Potom můžete zobrazit a změnit možnosti pro položky projektu, ovládací prvky a další položky v aplikaci.

   ![Okno Vlastnosti](../media/exploreide-hellowpfappfiles.png "Snímek obrazovky okna Vlastnosti s názvy aplikací souborů WPF")   

### <a name="change-the-name-of-mainwindowxaml"></a>Změna názvu souboru MainWindow.xaml

Dejme MainWindow konkrétnější název. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na *soubor MainWindow.xaml* a zvolte **Přejmenovat**. Přejmenujte soubor na *Greetings.xaml*.

## <a name="design-the-user-interface-ui"></a>Návrh uživatelského rozhraní (UI)

Pokud návrhář není otevřený, vyberte *Greetings.xaml* a stisknutím **shift**+**F7** otevřete návrháře.

Do této aplikace přidáme tři typy <xref:System.Windows.Controls.TextBlock> ovládacích <xref:System.Windows.Controls.RadioButton> prvků: ovládací <xref:System.Windows.Controls.Button> prvek, dva ovládací prvky a ovládací prvek.

### <a name="add-a-textblock-control"></a>Přidání ovládacího prvku TextBlock

1. Stisknutím **klávesy Ctrl**+**Q** aktivujte vyhledávací pole a zadejte panel **nástrojů**. Ze seznamu výsledků zvolte **Zobrazit > panel nástrojů.**

1. V **panelu nástrojů**rozbalte uzel **Common WPF Controls** a zobejít ovládací prvek TextBlock.

     ![Panel nástrojů se zvýrazněným ovládacím prvkem TextBlock](../media/exploreide-textblocktoolbox.png "Snímek obrazovky okna Panelu nástrojů se zvýrazněným ovládacím prvkem TextBlock")

1. Přidejte ovládací prvek TextBlock do návrhové plochy výběrem položky **TextBlock** a přetažením do okna na návrhové ploše. Vystředit ovládací prvek v horní části okna. Ve Visual Studiu 2019 a novějších můžete ovládací prvek vystředit pomocí červených pokynů.

    Okno aplikace by mělo vypadat jako na následujícím obrázku:

    ![Ovládací prvek TextBlock ve formuláři Pozdravy](../media/exploreide-greetingswithtextblockonly.png "Snímek obrazovky s ovládacím prvkem TextBlock ve formuláři Pozdravy")

   Značky XAML by měly vypadat podobně jako v následujícím příkladu:

    ```xaml
    <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
    </Grid>
    ```

### <a name="customize-the-text-in-the-text-block"></a>Přizpůsobení textu v textovém bloku

1. V zobrazení XAML vyhledejte značky pro **TextBlock** a `TextBox` změňte atribut **Text** z na`Select a message option and then choose the Display button.`

   Značky XAML by měly vypadat podobně jako v následujícím příkladu:

   ```xaml
   <Grid>
       <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
   </Grid>
   ```

1. Pokud chcete, znovu zastředte textový blok a uložte změny stisknutím **ctrl+s** nebo pomocí položky nabídky **Soubor.**

Dále přidáte do formuláře dva ovládací prvky [RadioButton.](/dotnet/framework/wpf/controls/radiobutton)

### <a name="add-radio-buttons"></a>Přidání tlačítek přepínače

1. V **panelu nástrojů**vyhledejte ovládací prvek **RadioButton.**

     ![Okno panelu nástrojů s vybraným ovládacím prvkem RadioButton](../media/exploreide-radiobuttontoolbox.png "Snímek obrazovky okna Panelu nástrojů s vybraným ovládacím prvkem RadioButton")

1. Přidejte dva ovládací prvky RadioButton k návrhové ploše výběrem položky **RadioButton** a přetažením do okna na návrhové ploše. Přesuňte tlačítka (jejich výběrem a pomocí kláves se šipkami), aby se tlačítka zobrazovala vedle sebe pod ovládacím prvkem TextBlock. K zarovnání ovládacích prvků použijte červené pokyny.

   Okno aplikace by mělo vypadat takto:

   ![Formulář Pozdravy s TextBlock a dvěma tlačítky](../media/exploreide-greetingswithradiobuttons.png "Snímek obrazovky s formulářem Pozdravy s textovým blokem a dvěma přepínači")

1. V okně **Vlastnosti** pro levý ovládací prvek RadioButton změňte vlastnost **Name** (vlastnost `HelloButton`v horní části okna **Vlastnosti)** na .

    ![Okno vlastností RadioButton](../media/exploreide-buttonproperties.png "Snímek obrazovky okna vlastností RadioButton")

1. V okně **Vlastnosti** pro pravý ovládací prvek RadioButton změňte vlastnost **Name** na `GoodbyeButton`a uložte změny.

Dále přidáte zobrazovaný text pro každý ovládací prvek RadioButton. Následující postup aktualizuje vlastnost **Content** pro ovládací prvek RadioButton.

### <a name="add-display-text-for-each-radio-button"></a>Přidání textu zobrazení pro každé přepínací tlačítko

1. Aktualizujte **Content** atribut Content `HelloButton` `GoodbyeButton` pro `"Hello"` `"Goodbye"` xaml a do a v ní. Značky XAML by nyní měly vypadat podobně jako v následujícím příkladu:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Nastavení přepínače, které má být ve výchozím nastavení zkontrolováno

V tomto kroku nastavíme HelloButton, který má být ve výchozím nastavení zkontrolován tak, aby bylo vždy vybráno jedno ze dvou přepínacích tlačítek.

1. V zobrazení XAML vyhledejte značky pro HelloButton.

1. Přidejte atribut **IsChecked** a nastavte jej na **hodnotu True**. Konkrétně přidejte `IsChecked="True"`.

   Značky XAML by nyní měly vypadat podobně jako v následujícím příkladu:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

Konečný prvek ui, který přidáte, je ovládací prvek [Button.](/dotnet/framework/wpf/controls/button)

### <a name="add-the-button-control"></a>Přidání ovládacího prvku tlačítka

1. V **panelu nástrojů**najděte ovládací prvek **Button** a přidejte jej na návrhovou plochu pod ovládacími prvky RadioButton přetažením do formuláře v návrhovém zobrazení. Pokud používáte Visual Studio 2019 nebo novější, červená čára vám pomůže vystředit ovládací prvek.

1. V zobrazení XAML změňte hodnotu **obsahu** ovládacího prvku Button z `Content="Button"` na `Content="Display"`.

     Okno aplikace by mělo vypadat jako na následujícím obrázku.

     ![Formulář Pozdravy s popisky ovládacích prvků](media/exploreide-greetingswithcontrollabels-cs.png "Snímek obrazovky formuláře Pozdravy s popisky ovládacích prvků")

   Značky XAML by nyní měly vypadat podobně jako v následujícím příkladu:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
        <Button Content="Display" HorizontalAlignment="Left" Margin="377,270,0,0" VerticalAlignment="Top" Width="75"/>
   </Grid>
   ```

### <a name="add-code-to-the-display-button"></a>Přidání kódu do tlačítka zobrazení

Po spuštění této aplikace se zobrazí okno se zprávou poté, co uživatel vybere přepínací tlačítko a pak zvolí tlačítko **Zobrazit.** Objeví se jedno okno se zprávou pro Hello a druhé se zprávou pro Goodbye. Chcete-li vytvořit toto chování, `Button_Click` přidáte kód k události v *Greetings.xaml.cs*.

1. Na návrhové ploše poklepejte na tlačítko **Zobrazit.**

     *Greetings.xaml.cs* otevře, s kurzorem `Button_Click` v události.

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {

    }
    ```

1. Zadejte následující kód:

    ```csharp
    if (HelloButton.IsChecked == true)
    {
         MessageBox.Show("Hello.");
    }
    else if (GoodbyeButton.IsChecked == true)
    {
        MessageBox.Show("Goodbye.");
    }
    ```

1. Uložte aplikaci.

## <a name="debug-and-test-the-application"></a>Ladění a testování aplikace

Dále budete ladit aplikace hledat chyby a testování, že obě okna se zprávami se zobrazí správně. Následující pokyny vám řeknou, jak vytvořit a spustit ladicí program, ale později si můžete přečíst [build wpf aplikace (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) a [ladění WPF](../../debugger/debugging-wpf.md) pro další informace.

### <a name="find-and-fix-errors"></a>Vyhledání a oprava chyb

V tomto kroku najdete chybu, kterou jsme způsobili dříve změnou názvu souboru *MainWindow.xaml.*

#### <a name="start-debugging-and-find-the-error"></a>Spusťte ladění a vyhledejte chybu

1. Začněte ladicí program stisknutím **klávesy F5** nebo výběrem **možnosti Ladění**a **potom začněte ladění**.

   Zobrazí se okno **režimu přerušení** a okno **Výstup** označuje, že došlo k výjimce IOException: Nelze najít prostředek mainwindow.xaml.

   ![Zpráva IOException](../media/exploreide-ioexception.png "Snímek obrazovky se zprávou IOException")

1. Stop the debugger by choosing **Debug** > **Stop Debugging**.

Na začátku tohoto kurzu jsme *přejmenovali MainWindow.xaml* na *Greetings.xaml,* ale kód stále odkazuje na *MainWindow.xaml* jako spouštěcí identifikátor URI pro aplikaci, takže projekt nelze spustit.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Zadejte greetings.xaml jako spouštěcí identifikátor URI

1. V **Průzkumníku řešení**otevřete soubor *App.xaml.*

1. `StartupUri="MainWindow.xaml"` Změňte `StartupUri="Greetings.xaml"`na a uložte změny.

Znovu spusťte ladicí program (stiskněte **klávesu F5).** Měli byste vidět **pozdravy** okno aplikace.

::: moniker range="vs-2017"
![Snímek obrazovky se spuštěnou aplikací](media/exploreide-wpf-running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Snímek obrazovky se spuštěnou aplikací](media/vs-2019/exploreide-wpf-running-app.png)
::: moniker-end

Nyní zavřete okno aplikace a zastavte ladění.

### <a name="debug-with-breakpoints"></a>Ladění s zarážkou

Kód můžete otestovat během ladění přidáním některých zarážek. Zarážky můžete přidat tak, že zvolíte **Ladění** > **přepínací zarážky ,** kliknutím na levý okraj editoru vedle řádku kódu, kde má dojít k přerušení, nebo stisknutím **klávesy F9**.

#### <a name="add-breakpoints"></a>Přidání zarážek

1. Otevřete *Greetings.xaml.cs*a vyberte následující řádek:`MessageBox.Show("Hello.")`

1. Přidejte zarážku z nabídky výběrem **možnosti Ladění**a potom **přepnutí zarážky**.

     Na levém okraji okna editoru se vedle řádku kódu zobrazí červený kruh.

1. Vyberte následující `MessageBox.Show("Goodbye.")`řádek: .

1. Stisknutím klávesy **F9** přidejte zarážku a stisknutím **klávesy F5** spusťte ladění.

1. V okně **Pozdravy** zvolte **přepínací** tlačítko Hello a pak zvolte tlačítko **Zobrazit.**

    Řádek `MessageBox.Show("Hello.")` je zvýrazněn žlutě. V dolní části ide, autos, místní a sledovat okna jsou ukotveny společně na levé straně a zásobník uvolvolání, zarážky, nastavení výjimek, příkaz, okamžité a výstupní okna jsou ukotveny společně na pravé straně.

    ![Zarážka v ladicím programu](media/exploreide-debugbreakpoint.png "Snímek obrazovky s zarážkou v ladicím programu")

1. Na řádku nabídek zvolte **Ladění krok** > **ven**.

     Aplikace pokračuje v provádění a zobrazí se okno se zprávou se slovem "Hello".

1. Chcete-li okno se zprávou zavřít, zvolte tlačítko **OK** na schránce se zprávou.

1. V okně **Pozdravy** zvolte **přepínací** tlačítko Sbohem a pak zvolte tlačítko **Zobrazit.**

     Řádek `MessageBox.Show("Goodbye.")` je zvýrazněn žlutě.

1. Chcete-li pokračovat v ladění, zvolte klávesu **F5.** Když se zobrazí okno se zprávou, zvolte tlačítko **OK** na okno se zprávou zavřít.

1. Zavřete okno aplikace a zastavte ladění.

1. Na řádku nabídek zvolte **Ladit** > **Zakázat všechny zarážky**.

### <a name="view-a-representation-of-the-ui-elements"></a>Zobrazení reprezentace prvků uživatelského rozhraní

V běžící aplikaci byste měli vidět widget, který se zobrazí v horní části okna. Jedná se o pomocníka runtime, který poskytuje rychlý přístup k některým užitečným funkcím ladění. Klikněte na první tlačítko, **Přejít na Live Visual Tree**. Měli byste vidět okno se stromem, který obsahuje všechny vizuální prvky stránky. Rozbalte uzly a vyhledejte přidaná tlačítka.

![Snímek obrazovky s oknem Živé vizuální strom](media/vs-2019/exploreide-live-visual-tree.png)

### <a name="build-a-release-version-of-the-application"></a>Sestavení verze pro vydání aplikace

Teď, když jste ověřili, že vše funguje, můžete připravit sestavení verze aplikace.

1. V hlavní nabídce vyberte **Build** > **Clean řešení,** chcete-li odstranit zprostředkující soubory a výstupní soubory, které byly vytvořeny během předchozích sestavení. To není nutné, ale vyčistí výstupy sestavení ladění.

1. Změňte konfiguraci sestavení pro HelloWPFApp z **ladění** na **vydání** pomocí ovládacího prvku rozevírací seznam na panelu nástrojů (aktuálně se říká "Ladění").

1. Vytvořte řešení výběrem **sestavení** > **sestavení řešení**.

Gratulujeme k dokončení tohoto výukového programu! Soubor EXE, který jste *vytvořili,* najdete pod adresářem řešení a projektu (*...\HelloWPFApp\HelloWPFApp\bin\Release*).

## <a name="next-steps"></a>Další kroky

Gratulujeme k dokončení tohoto výukového programu! Chcete-li se dozvědět ještě více, pokračujte v následujících kurzech.

> [!div class="nextstepaction"]
> [Pokračovat v dalších výukových programech WPF](/dotnet/framework/wpf/getting-started/wpf-walkthroughs/)

## <a name="see-also"></a>Viz také

- [Tipy pro vyšší produktivitu](../../ide/productivity-features.md)
