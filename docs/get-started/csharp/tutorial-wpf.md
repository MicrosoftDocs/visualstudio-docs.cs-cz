---
title: 'Hello World aplikace pomocí WPF v jazyce C #'
description: Vytvořte jednoduchou aplikaci pro Windows Desktop .NET v jazyce C# se sadou Visual Studio pomocí architektury rozhraní Windows Presentation Foundation (WPF).
ms.custom: seodec18, get-started
ms.date: 02/10/2021
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: tutorial
dev_langs:
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 1f3232ad0a8b7cc34abbe6d49c05944c066226da
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2021
ms.locfileid: "101682852"
---
# <a name="tutorial-create-a-simple-application-with-c"></a>Kurz: Vytvoření jednoduché aplikace pomocí jazyka C\#

Po dokončení tohoto kurzu se seznámíte s mnoha nástroji, dialogovými okny a návrháři, které můžete použít při vývoji aplikací pomocí sady Visual Studio. Vytvoříte aplikaci "Hello, World", navrhnete uživatelské rozhraní, přidáte kód a budete ladit chyby, zatímco se naučíte pracovat v integrovaném vývojovém prostředí ([IDE](visual-studio-ide.md)).

## <a name="prerequisites"></a>Požadavky

::: moniker range="vs-2017"
Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?) a nainstalujte si ji zdarma.
::: moniker-end
::: moniker range=">=vs-2019"

- Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/) a nainstalujte si ji zdarma.
- Pro tento kurz můžete použít buď .NET Framework, nebo .NET Core. .NET Core je novější, moderní rozhraní. .NET Core vyžaduje Visual Studio 2019 verze 16,3 nebo novější.
::: moniker-end

## <a name="configure-the-ide"></a>Nastavení integrovaného vývojového prostředí (IDE)

::: moniker range="vs-2017"

Při prvním otevření aplikace Visual Studio budete vyzváni k přihlášení. Tento krok je pro tento kurz volitelný. V dalším kroku se zobrazí dialogové okno s výzvou, abyste si zvolili vývojové nastavení a barevný motiv. Ponechte výchozí nastavení a klikněte na **Spustit Visual Studio**.

![Dialogové okno zvolit nastavení](../media/exploreide-settings.png)

Po spuštění sady Visual Studio se zobrazí okna nástrojů, nabídky a panely nástrojů a prostor hlavního okna. Okna nástrojů jsou ukotvena na levé a pravé straně okna aplikace, s možností **snadného spuštění**, řádku nabídek a standardní panel nástrojů v horní části. Ve středu okna aplikace je **Úvodní stránka**. Při načítání řešení nebo projektu se zobrazí editory a návrháři v prostoru, kde je **Úvodní stránka** . Při vývoji aplikace strávíte nejvíce času v této centrální oblasti.

![Integrované vývojové prostředí (IDE) sady Visual Studio 2017 s obecným nastavením](../media/exploreide-idewithgeneralsettings.png "Snímek obrazovky s prostředím IDE sady Visual Studio 2017 s použitým obecným nastavením")

::: moniker-end

::: moniker range=">=vs-2019"

Při spuštění sady Visual Studio se nejprve otevře okno Start. Pokud chcete otevřít vývojové prostředí, vyberte **pokračovat bez kódu** . Zobrazí se okna nástrojů, nabídky a panely nástrojů a prostor hlavního okna. Okna nástrojů jsou ukotvena na levé a pravé straně okna aplikace, pomocí vyhledávacího pole, řádku nabídek a standardního panelu nástrojů v horní části. Při načítání řešení nebo projektu se editory a návrháře zobrazí v centrálním prostoru okna aplikace. Při vývoji aplikace strávíte nejvíce času v této centrální oblasti.

::: moniker-end

## <a name="create-the-project"></a>Vytvoření projektu

Při vytváření aplikace v systému Visual Studio je třeba nejprve vytvořit projekt a řešení. V tomto příkladu vytvoříte projekt Windows Presentation Foundation (WPF).

::: moniker range="vs-2017"

1. Vytvoření nového projektu Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

     ![Na panelu nabídek vyberte možnosti soubor, nový, projekt.](../media/exploreide-filenewproject.png "Snímek obrazovky s panelem nabídek, kde si zvolíte soubor, nový, projekt")

1. V dialogovém okně **Nový projekt** vyberte kategorii **nainstalovaná** aplikace  >  **Visual C#** pro  >  **stolní počítače** a pak vyberte šablonu **aplikace WPF (.NET Framework)** . Pojmenujte projekt **HelloWPFApp** a vyberte **OK**.

     ![Šablona aplikace WPF v dialogovém okně Nový projekt sady Visual Studio](media/exploreide-newprojectcsharp.png "Snímek obrazovky šablony aplikace WPF v dialogovém okně Nový projekt")

::: moniker-end

::: moniker range="vs-2019"

1. Otevřete Visual Studio 2019.

1. V okně Start vyberte možnost **vytvořit nový projekt**.

   ![Zobrazit okno vytvořit nový projekt](../../get-started/media/vs-2019/start-window-create-new-project.png "Snímek obrazovky okna vytvořit nový projekt")

1. Na obrazovce **vytvořit nový projekt** vyhledejte "WPF", zvolte **aplikace WPF** a pak zvolte **Další**.

   :::image type="content" source="media/vs-2019/explore-ide-new-project-csharp-vs-2019.png" alt-text="Šablona aplikace WPF v dialogovém okně vytvořit nový projekt":::

1. Na další obrazovce zadejte název projektu, **HelloWPFApp** a klikněte na tlačítko **Další**.

   :::image type="content" source="./media/vs-2019/explore-ide-name-project.png" alt-text="Pojmenujte projekt HelloWPFApp.":::

1. V okně **Další informace** by měl být **.NET Core 3,1** již vybraný pro vaši cílovou architekturu. Pokud ne, vyberte **.NET Core 3,1**. Pak zvolte **vytvořit**.

   :::image type="content" source="./media/vs-2019/wpf-target-framework.png" alt-text="V okně Další informace se ujistěte, že je vybraná možnost .NET Core 3,1.":::

::: moniker-end

Visual Studio vytvoří projekt a řešení HelloWPFApp a **Průzkumník řešení** zobrazí různé soubory. **Návrhář WPF** zobrazuje návrhové zobrazení a zobrazení XAML souboru *MainWindow. XAML* v rozděleném zobrazení. Posunutí příčky můžete zobrazit více nebo méně z obou zobrazení. Můžete zvolit, zda chcete zobrazit pouze vizuální zobrazení nebo pouze zobrazení XAML.

![Projekt a řešení WPF v integrovaném vývojovém prostředí](media/exploreide-wpfproject-cs.png "Snímek obrazovky s projektem a řešením WPF v integrovaném vývojovém prostředí")

> [!NOTE]
> Další informace o jazyce XAML (eXtensible Application Markup Language) naleznete na stránce [Přehled XAML pro WPF](/dotnet/framework/wpf/advanced/xaml-overview-wpf) .

Poté, co jste projekt vytvořili, jej můžete upravit. Provedete to tak, že v nabídce **zobrazení** kliknete na **okno Vlastnosti** nebo stisknete **F4**. Pak můžete zobrazit a změnit možnosti položek projektu, ovládacích prvků a dalších položek v aplikaci.

   ![Vlastnosti – okno](../media/exploreide-hellowpfappfiles.png "Snímek obrazovky okno Vlastnosti s názvy aplikací WPF souborů")   

### <a name="change-the-name-of-mainwindowxaml"></a>Změna názvu souboru MainWindow. XAML

Pojďme dát MainWindow konkrétnější název. V **Průzkumník řešení** klikněte pravým tlačítkem na *MainWindow. XAML* a vyberte **Přejmenovat**. Přejmenujte soubor na *Greetings. XAML*.

## <a name="design-the-user-interface-ui"></a>Návrh uživatelského rozhraní (UI)

Pokud návrhář není otevřen, vyberte možnost *Greetings. XAML* a stisknutím klávesy **SHIFT** + **F7** Otevřete návrháře.

Do této aplikace přidáme tři typy ovládacích prvků: <xref:System.Windows.Controls.TextBlock> ovládací prvek, dva <xref:System.Windows.Controls.RadioButton> ovládací prvky a <xref:System.Windows.Controls.Button> ovládací prvek.

### <a name="add-a-textblock-control"></a>Přidání ovládacího prvku TextBlock

1. Stisknutím klávesy **CTRL** + **Q** aktivujte vyhledávací pole a zadejte **sadu nástrojů**. V seznamu výsledků vyberte možnost **zobrazit > sada nástrojů** .

1. V **sadě nástrojů** rozbalte uzel **běžné ovládací prvky WPF** pro zobrazení ovládacího prvku TextBlock.

     ![Sada nástrojů se zvýrazněným ovládacím prvkem TextBlock](../media/exploreide-textblocktoolbox.png "Snímek obrazovky okna panelu nástrojů se zvýrazněným ovládacím prvkem TextBlock")

1. Přidejte ovládací prvek TextBlock do návrhové plochy tak, že vyberete položku **TextBlock** a přetáhnete ji do okna na návrhové ploše. Vycentrovat ovládací prvek v horní části okna. V aplikaci Visual Studio 2019 a novějších můžete použít červené pokyny k centrování ovládacího prvku.

    Okno aplikace by mělo vypadat jako na následujícím obrázku:

    ![TextBlock ovládacího prvku na formuláři Greetings](../media/exploreide-greetingswithtextblockonly.png "Snímek obrazovky ovládacího prvku TextBlock na formuláři Greetings")

   Značka XAML by měla vypadat podobně jako v následujícím příkladu:

    ```xaml
    <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
    </Grid>
    ```

### <a name="customize-the-text-in-the-text-block"></a>Přizpůsobení textu v textovém bloku

1. V zobrazení XAML vyhledejte značku pro **TextBlock** a změňte atribut **text** z `TextBox` na `Select a message option and then choose the Display button.`

   Značka XAML by měla vypadat podobně jako v následujícím příkladu:

   ```xaml
   <Grid>
       <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
   </Grid>
   ```

1. Vycentrovat TextBlock znovu, pokud chcete, a potom změny uložte stisknutím **kláves CTRL + S** nebo pomocí položky nabídky **soubor** .

Dále do formuláře přidejte dva ovládací prvky [RadioButton](/dotnet/framework/wpf/controls/radiobutton) .

### <a name="add-radio-buttons"></a>Přidání tlačítek přepínače

1. V **sadě nástrojů** Najděte ovládací prvek **RadioButton** .

     ![Okno panelu nástrojů s vybraným ovládacím prvkem RadioButton](../media/exploreide-radiobuttontoolbox.png "Snímek obrazovky okna panelu nástrojů s vybraným ovládacím prvkem RadioButton")

1. Přidejte dva ovládací prvky RadioButton na návrhovou plochu tak, že vyberete položku **RadioButton** a přetáhnete ji do okna na návrhové ploše. Přesuňte tlačítka (tak, že je vyberete a použijete klávesy se šipkami), aby se tlačítka zobrazovala vedle sebe pod ovládacím prvkem TextBlock. Použijte červené pokyny pro zarovnání ovládacích prvků.

   Okno aplikace by mělo vypadat takto:

   ![Formulář s pozdravem s TextBlock a dvěma přepínači](../media/exploreide-greetingswithradiobuttons.png "Snímek formuláře s pozdravem s TextBlock a dvěma přepínači")

1. V okně **vlastnosti** levého ovládacího prvku RadioButton změňte vlastnost **Name** (vlastnost v horní části okna **vlastnosti** ) na `HelloButton` .

    ![Okno vlastností RadioButton](../media/exploreide-buttonproperties.png "Snímek obrazovky okna vlastností RadioButton")

1. V okně **vlastnosti** pravého ovládacího prvku RadioButton změňte vlastnost **Name** na a `GoodbyeButton` uložte provedené změny.

Dále přidáte zobrazený text pro každý ovládací prvek RadioButton. Následující postup aktualizuje vlastnost **obsah** ovládacího prvku RadioButton.

### <a name="add-display-text-for-each-radio-button"></a>Přidat text zobrazení pro každý přepínač

1. Aktualizujte atribut **obsahu** pro `HelloButton` a a `GoodbyeButton` `"Hello"` `"Goodbye"` v jazyce XAML. Kód XAML by teď měl vypadat podobně jako v následujícím příkladu:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Nastaví přepínač pro kontrolu ve výchozím nastavení.

V tomto kroku nastavíme HelloButton, aby se kontrolovaly ve výchozím nastavení, takže se vždycky vybrala jedna z těchto dvou přepínačů.

1. V zobrazení XAML vyhledejte značku pro HelloButton.

1. Přidejte atribut- **checked** a nastavte jej na **hodnotu true**. Konkrétně přidejte `IsChecked="True"` .

   Kód XAML by teď měl vypadat podobně jako v následujícím příkladu:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

Konečný prvek uživatelského rozhraní, který přidáte, je ovládací prvek [tlačítko](/dotnet/framework/wpf/controls/button) .

### <a name="add-the-button-control"></a>Přidání ovládacího prvku tlačítko

1. V sadě **nástrojů** vyhledejte ovládací prvek **tlačítko** a poté jej přidejte do návrhové plochy v ovládacích prvcích RadioButton přetažením do formuláře v zobrazení Návrh. Pokud používáte Visual Studio 2019 nebo novější, vám červená čára pomůže zarovnat na střed ovládacího prvku.

1. V zobrazení XAML změňte hodnotu **obsahu** pro ovládací prvek tlačítko z `Content="Button"` na a `Content="Display"` poté změny uložte.

     Okno aplikace by mělo vypadat jako na následujícím obrázku.

     ![Formulář s pozdravem s popisky ovládacích prvků](media/exploreide-greetingswithcontrollabels-cs.png "Snímek formuláře s pozdravy s popisky ovládacích prvků")

   Kód XAML by teď měl vypadat podobně jako v následujícím příkladu:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
        <Button Content="Display" HorizontalAlignment="Left" Margin="377,270,0,0" VerticalAlignment="Top" Width="75"/>
   </Grid>
   ```

### <a name="add-code-to-the-display-button"></a>Přidání kódu k tlačítku zobrazit

Po spuštění této aplikace se zobrazí okno se zprávou, když uživatel zvolí přepínač a pak zvolí tlačítko pro **zobrazení** . Objeví se jedno okno se zprávou pro Hello a druhé se zprávou pro Goodbye. Pro vytvoření tohoto chování přidáte kód do `Button_Click` události v *Greetings.XAML.cs*.

1. Na návrhové ploše poklikejte na tlačítko **Zobrazit** .

     *Greetings.XAML.cs* se otevře s kurzorem v `Button_Click` události.

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

V dalším kroku aplikaci provedete tak, aby hledala chyby a otestovali, že se obě okna se zprávou zobrazují správně. V následujících pokynech se dozvíte, jak sestavit a spustit ladicí program, ale později si můžete přečíst [sestavení aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) a [ladění WPF](../../debugger/debugging-wpf.md) pro další informace.

### <a name="find-and-fix-errors"></a>Vyhledání a oprava chyb

V tomto kroku zjistíte chybu, kterou jsme dříve způsobili změnou názvu souboru *MainWindow. XAML* .

#### <a name="start-debugging-and-find-the-error"></a>Spustit ladění a najít chybu

1. Spusťte ladicí program stisknutím klávesy **F5** nebo výběrem možnosti **ladění** a potom **Spusťte ladění**.

   Zobrazí se okno **režim přerušení** a okno **výstup** indikuje, že došlo k IOException: nelze najít prostředek ' MainWindow. XAML '.

   ![Zpráva IOException](../media/exploreide-ioexception.png "Snímek obrazovky IOException zprávy")

1. Ukončete ladicí program kliknutím na **ladění**  >  **Zastavit ladění**.

Na začátku tohoto kurzu jsme přejmenovali *MainWindow.* XAML na *Greetings. XAML* , ale kód pořád odkazuje na *MainWindow. XAML* jako spouštěcí identifikátor URI pro aplikaci, takže projekt nejde spustit.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Jako spouštěcí identifikátor URI zadejte Greetings. XAML.

1. V **Průzkumník řešení** otevřete soubor *App. XAML* .

1. Změňte `StartupUri="MainWindow.xaml"` na `StartupUri="Greetings.xaml"` a pak změny uložte.

Znovu spusťte ladicí program (stiskněte klávesu **F5**). Měli byste vidět okno **Greetings** aplikace.

::: moniker range="vs-2017"
![Snímek obrazovky běžící aplikace](media/exploreide-wpf-running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Snímek obrazovky běžící aplikace](media/vs-2019/exploreide-wpf-running-app.png)
::: moniker-end

Nyní zavřete okno aplikace a zastavte ladění.

### <a name="debug-with-breakpoints"></a>Ladění pomocí zarážek

Můžete otestovat kód během ladění přidáním některých zarážek. Zarážky můžete **přidat kliknutím na**  >  levý okraj editoru vedle řádku kódu, kde **chcete,** aby došlo k přerušení, nebo stisknutím klávesy **F9**.

#### <a name="add-breakpoints"></a>Přidání zarážek

1. Otevřete *Greetings.XAML.cs* a vyberte následující řádek: `MessageBox.Show("Hello.")`

1. Přidejte zarážku z nabídky tak, že vyberete **ladění** a potom **přepnete zarážku**.

     Na levém okraji okna editoru se vedle řádku kódu zobrazí červený kruh.

1. Vyberte následující řádek: `MessageBox.Show("Goodbye.")` .

1. Stisknutím klávesy **F9** přidejte zarážku a stisknutím klávesy **F5** spusťte ladění.

1. V okně **Greetings** vyberte přepínač **Hello** a pak klikněte na tlačítko **Zobrazit** .

    Řádek `MessageBox.Show("Hello.")` je zvýrazněn žlutě. V dolní části rozhraní IDE jsou okna Automatické hodnoty, místní hodnoty a kukátka ukotvena na levé straně a zásobník volání, zarážky, nastavení výjimek, příkaz, okamžité a výstupní okna jsou ukotveny společně na pravé straně.

    ![Zarážka v ladicím programu](media/exploreide-debugbreakpoint.png "Snímek obrazovky se zarážkou v ladicím programu")

1. Na panelu nabídek vyberte možnost **ladit**  >  **Krok ven**.

     Aplikace bude pokračovat v provádění a zobrazí se okno se zprávou se slovem "Hello".

1. Kliknutím na tlačítko **OK** v okně se zprávou ho zavřete.

1. V okně **Greetings** vyberte přepínač rozdálení a pak **klikněte na tlačítko** **Zobrazit** .

     Řádek `MessageBox.Show("Goodbye.")` je zvýrazněn žlutě.

1. Pokračujte v ladění kliknutím na klávesu **F5** . Když se zobrazí okno se zprávou, zavřete ho kliknutím na tlačítko **OK** v okně se zprávou.

1. Zavřete okno aplikace a zastavte ladění.

1. Na panelu nabídek vyberte možnost **ladit**  >  **Zakázat všechny zarážky**.

### <a name="view-a-representation-of-the-ui-elements"></a>Zobrazit reprezentace prvků uživatelského rozhraní

Ve spuštěné aplikaci byste měli vidět widget, který se zobrazí v horní části okna. Jedná se o pomocníka za běhu, který poskytuje rychlý přístup k některým užitečným funkcím ladění. Klikněte na první tlačítko, **přejděte do živého vizuálního stromu**. Mělo by se zobrazit okno se stromovou strukturou, která obsahuje všechny vizuální prvky vaší stránky. Rozbalením uzlů Najděte tlačítka, která jste přidali.

![Snímek obrazovky okna živého vizuálního stromu](media/vs-2019/exploreide-live-visual-tree.png)

### <a name="build-a-release-version-of-the-application"></a>Sestavení verze pro vydání aplikace

Teď, když jste ověřili, že všechno funguje, můžete připravit sestavení pro vydání aplikace.

1. V hlavní nabídce vyberte **sestavit**  >  **Vyčistit řešení** a odstraňte mezilehlé soubory a výstupní soubory, které byly vytvořeny během předchozích sestavení. To není nutné, ale čistí výstupy sestavení ladění.

1. Změňte konfiguraci sestavení pro HelloWPFApp z **Debug** na **release** pomocí ovládacího prvku rozevíracího seznamu na panelu nástrojů (aktuálně říká "ladit").

1. Sestavte řešení kliknutím na **sestavit** sestavení  >  **řešení**.

Blahopřejeme k dokončení tohoto kurzu! Můžete najít soubor *. exe* , který jste vytvořili v rámci vašeho řešení a adresáře projektu (*. ..\HelloWPFApp\HelloWPFApp\bin\Release*).

## <a name="next-steps"></a>Další kroky

Blahopřejeme k dokončení tohoto kurzu! Pokud se chcete dozvědět ještě víc, pokračujte v následujících kurzech.

> [!div class="nextstepaction"]
> [Pokračovat s dalšími kurzy WPF](/dotnet/framework/wpf/getting-started/wpf-walkthroughs/)

## <a name="see-also"></a>Viz také

- [Tipy pro vyšší produktivitu](../../ide/productivity-features.md)
