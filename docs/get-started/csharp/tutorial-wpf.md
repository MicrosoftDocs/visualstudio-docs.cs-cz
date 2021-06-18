---
title: 'Hello World aplikace s WPF v jazyce C #'
description: Vytvořte jednoduchou desktopovou aplikaci .NET pro Windows v jazyce C# s Visual Studio s využitím rozhraní Windows Presentation Foundation (WPF).
ms.custom: seodec18, get-started
ms.date: 02/10/2021
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: tutorial
dev_langs:
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: ee7b5ecc023d1319f4d7551e0e7b186d76d86741
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308477"
---
# <a name="tutorial-create-a-simple-application-with-c"></a>Kurz: Vytvoření jednoduché aplikace pomocí jazyka C\#

Po dokončení tohoto kurzu se seznámíte s mnoha nástroji, dialogy a návrháři, které můžete použít při vývoji aplikací s Visual Studio. Vytvoříte aplikaci "Hello, World", navrhovat uživatelské rozhraní, přidat kód a ladit chyby, zatímco se seznámíte s prací v integrovaném vývojovém prostředí[(IDE).](visual-studio-ide.md)

## <a name="prerequisites"></a>Požadavky

::: moniker range="vs-2017"
Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/vs/older-downloads/?) a nainstalujte si ho zdarma.
::: moniker-end
::: moniker range=">=vs-2019"

- Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/downloads/) a nainstalujte si ho zdarma.
- Pro tento kurz můžete .NET Framework nebo .NET Core. .NET Core je novější, modernější rozhraní. .NET Core vyžaduje Visual Studio 2019 verze 16.3 nebo novější.
::: moniker-end

## <a name="configure-the-ide"></a>Nastavení integrovaného vývojového prostředí (IDE)

::: moniker range="vs-2017"

Při prvním Visual Studio se zobrazí výzva k přihlášení. Tento krok je pro tento kurz volitelný. V dalším kroku se může zobrazit dialogové okno s výběrem nastavení vývoje a barevného motivu. Podržte výchozí hodnoty a zvolte **Spustit Visual Studio**.

![Dialogové okno Zvolit nastavení](../media/exploreide-settings.png)

Po Visual Studio se zobrazí okna nástrojů, nabídky a panely nástrojů a prostor hlavního okna. Okna nástrojů jsou ukotvená na levé a pravé straně okna aplikace s **Snadné spuštění**, panelem nabídek a standardním panelem nástrojů v horní části. Uprostřed okna aplikace je úvodní **stránka**. Když načtete řešení nebo projekt, zobrazí se v prostoru, kde se nachází úvodní stránka, editory a **návrháři.** Při vývoji aplikace strávíte většinu času v této centrální oblasti.

![Visual Studio integrovaného vývojového prostředí (IDE) 2017 s použitým obecným nastavením](../media/exploreide-idewithgeneralsettings.png "Snímek obrazovky s prostředím IDE sady Visual Studio 2017 s použitým obecným nastavením")

::: moniker-end

::: moniker range=">=vs-2019"

Při spuštění Visual Studio se jako první otevře úvodní okno. Výběrem **možnosti Pokračovat bez** kódu otevřete vývojové prostředí. Zobrazí se okna nástrojů, nabídky a panely nástrojů a prostor hlavního okna. Okna nástrojů jsou ukotvená na levé a pravé straně okna aplikace s vyhledávacím polem, panelem nabídek a standardním panelem nástrojů v horní části. Při načítání řešení nebo projektu se v centrálním prostoru okna aplikace zobrazí editory a návrháři. Při vývoji aplikace strávíte většinu času v této centrální oblasti.

::: moniker-end

## <a name="create-the-project"></a>Vytvoření projektu

Při vytváření aplikace v systému Visual Studio je třeba nejprve vytvořit projekt a řešení. V tomto příkladu vytvoříte projekt Windows Presentation Foundation (WPF).

::: moniker range="vs-2017"

1. Vytvoření nového projektu V řádku nabídek vyberte **File** New Project  >  **(Soubor nový**  >  **projekt).**

     ![V řádku nabídek zvolte Soubor, Nový, Projekt.](../media/exploreide-filenewproject.png "Snímek obrazovky s panelem nabídek, kde si zvolíte soubor, nový, projekt")

1. V dialogovém **okně Nový** projekt vyberte kategorii **Nainstalovaná** plocha Windows v jazyce Visual C# a pak vyberte šablonu  >    >   Aplikace **WPF (.NET Framework).** Pojmnujte **projekt HelloWPFApp** a vyberte **OK**.

     ![Šablona aplikace WPF v dialogovém Visual Studio nový projekt](media/exploreide-newprojectcsharp.png "Snímek obrazovky šablony aplikace WPF v dialogovém okně Nový projekt")

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio.

1. V úvodním okně zvolte **Vytvořit nový projekt.**

   ![Zobrazení okna Vytvořit nový projekt](../../get-started/media/vs-2019/start-window-create-new-project.png "Snímek obrazovky okna vytvořit nový projekt")

1. Na **obrazovce Vytvořit nový** projekt vyhledejte "WPF", zvolte **Aplikace WPF** a pak zvolte **Další.**

   :::image type="content" source="media/vs-2019/explore-ide-new-project-csharp-vs-2019.png" alt-text="Šablona aplikace WPF v dialogovém okně Vytvořit nový projekt":::

1. Na další obrazovce zadejte název projektu **HelloWPFApp** a zvolte **Další.**

   :::image type="content" source="./media/vs-2019/explore-ide-name-project.png" alt-text="Pojmete svůj projekt HelloWPFApp.":::

1. V okně **Další informace** by už mělo být pro cílovou rozhraní vybrané **rozhraní .NET Core 3.1.** Pokud ne, vyberte **.NET Core 3.1.** Pak zvolte **Vytvořit.**

   :::image type="content" source="./media/vs-2019/wpf-target-framework.png" alt-text="V okně Další informace se ujistěte, že je vybraná možnost .NET Core 3.1.":::

::: moniker-end

Visual Studio vytvoří projekt a řešení HelloWPFApp **a Průzkumník řešení** různé soubory. Návrhář **WPF zobrazuje** zobrazení návrhu a zobrazení XAML souboru *MainWindow.xaml* v rozdělené zobrazení. Rozdělením můžete vysunout a zobrazit více nebo méně zobrazení. Můžete zvolit zobrazení vizuálu nebo jenom zobrazení XAML.

![Projekt WPF a řešení v integrovaném vývojovém prostředí (IDE)](media/exploreide-wpfproject-cs.png "Snímek obrazovky s projektem a řešením WPF v integrovaném vývojovém prostředí")

> [!NOTE]
> Další informace o jazyce XAML (eXtensible Application Markup Language) najdete na stránce [Přehled XAML pro WPF.](/dotnet/framework/wpf/advanced/xaml-overview-wpf)

Poté, co jste projekt vytvořili, jej můžete upravit. To můžete udělat tak, že v nabídce View **(Zobrazení)** **zvolíte Properties** Window (Okno Vlastnosti) nebo **stisknete klávesu F4**. Potom můžete zobrazit a změnit možnosti položek projektu, ovládacích prvků a dalších položek v aplikaci.

   ![Vlastnosti – okno](../media/exploreide-hellowpfappfiles.png "Snímek obrazovky okno Vlastnosti s názvy aplikací WPF souborů")   

### <a name="change-the-name-of-mainwindowxaml"></a>Změna názvu mainwindow.xaml

Pojďme mainwindow dát konkrétnější název. V Průzkumník řešení klikněte pravým tlačítkem na *MainWindow.xaml* **a** zvolte **Přejmenovat.** Přejmenujte soubor *na Greetings.xaml.*

## <a name="design-the-user-interface-ui"></a>Návrh uživatelského rozhraní (UI)

Pokud návrhář není otevřený, vyberte *Greetings.xaml* a stisknutím **klávesy Shift** + **F7** návrháře otevřete.

Do této aplikace přidáme tři typy ovládacích prvků: ovládací prvek, dva ovládací prvky <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.RadioButton> a ovládací <xref:System.Windows.Controls.Button> prvek.

### <a name="add-a-textblock-control"></a>Přidání ovládacího prvku TextBlock

1. Stisknutím **kláves Ctrl** + **Q** aktivujte vyhledávací pole a zadejte Panel **nástrojů.** Ze **seznamu výsledků > Zobrazit** panel nástrojů.

1. V **sadě nástrojů** rozbalte uzel Běžné ovládací prvky **WPF,** abyste viděli ovládací prvek TextBlock.

     ![Panel nástrojů se zvýrazněnou ovládacím prvku TextBlock](../media/exploreide-textblocktoolbox.png "Snímek obrazovky okna panelu nástrojů se zvýrazněným ovládacím prvkem TextBlock")

1. Přidejte na návrhovou plochu ovládací prvek TextBlock tak, že zvolíte **položku TextBlock** a přetáhnete ji do okna na návrhové ploše. Na střed ovládacího prvku v horní části okna. V Visual Studio 2019 a novějších verzích můžete použít červené pokyny k vy středování ovládacího prvku.

    Okno aplikace by mělo vypadat jako na následujícím obrázku:

    ![Ovládací prvek TextBlock ve formuláři Greetings](../media/exploreide-greetingswithtextblockonly.png "Snímek obrazovky ovládacího prvku TextBlock na formuláři Greetings")

   Kód XAML by měl vypadat podobně jako v následujícím příkladu:

    ```xaml
    <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
    </Grid>
    ```

### <a name="customize-the-text-in-the-text-block"></a>Přizpůsobení textu v textovém bloku

1. V zobrazení XAML vyhledejte kód pro **TextBlock** a změňte **atribut Text** z `TextBox` na . `Select a message option and then choose the Display button.`

   Kód XAML by měl vypadat podobně jako v následujícím příkladu:

   ```xaml
   <Grid>
       <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
   </Grid>
   ```

1. Pokud chcete, na střed znovu zablokujte TextBlock a pak změny uložte stisknutím **kombinace kláves Ctrl+S** nebo **pomocí položky nabídky** Soubor.

Dále do formuláře přidáte dva [ovládací prvky RadioButton.](/dotnet/framework/wpf/controls/radiobutton)

### <a name="add-radio-buttons"></a>Přidání tlačítek přepínače

1. V **sadě nástrojů** vyhledejte **ovládací prvek RadioButton.**

     ![Okno panelu nástrojů s vybraným ovládacím prvku RadioButton](../media/exploreide-radiobuttontoolbox.png "Snímek obrazovky okna panelu nástrojů s vybraným ovládacím prvkem RadioButton")

1. Na návrhovou plochu přidejte dva ovládací prvky RadioButton tak, že zvolíte položku **RadioButton** a přetáhnete ji do okna na návrhové ploše. Přesuňte tlačítka (tak, že je vyberete a pomocí kláves se šipkami) tak, aby se tlačítka zobrazují vedle sebe pod ovládacím prvku TextBlock. Pomocí červených pokynů zarovnejte ovládací prvky.

   Okno aplikace by mělo vypadat takto:

   ![Formulář Greetings s textemBlock a dvěma přepínači](../media/exploreide-greetingswithradiobuttons.png "Snímek formuláře s pozdravem s TextBlock a dvěma přepínači")

1. V okně **Vlastnosti** levého ovládacího prvku RadioButton změňte vlastnost **Name** (vlastnost v horní části okna **Vlastnosti)** na `HelloButton` .

    ![Okno vlastností RadioButton](../media/exploreide-buttonproperties.png "Snímek obrazovky okna vlastností RadioButton")

1. V okně **Vlastnosti** pravého ovládacího prvku RadioButton změňte vlastnost **Name** na `GoodbyeButton` a pak změny uložte.

Dále přidáte zobrazovaný text pro každý ovládací prvek RadioButton. Následující postup aktualizuje vlastnost **Content** ovládacího prvku RadioButton.

### <a name="add-display-text-for-each-radio-button"></a>Přidání textu zobrazení pro jednotlivá přepínačová tlačítka

1. Aktualizujte **atribut Content** pro a na a v `HelloButton` `GoodbyeButton` `"Hello"` `"Goodbye"` XAML. Kód XAML by teď měl vypadat podobně jako v následujícím příkladu:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Nastavení přepínačů, které se má ve výchozím nastavení zaškrtnuté

V tomto kroku nastavíme, aby se HelloButton ve výchozím nastavení zaškrtl, aby byl vždy vybraný jeden ze dvou přepínačů.

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

Po spuštění této aplikace se zobrazí okno se zprávou, když uživatel zvolí přepínač a pak zvolí tlačítko pro **zobrazení** . Objeví se jedno okno se zprávou pro Hello a druhé se zprávou pro Goodbye. Pro vytvoření tohoto chování přidáte kód k `Button_Click` události v souboru *Greetings. XAML. cs*.

1. Na návrhové ploše poklikejte na tlačítko **Zobrazit** .

     Otevře se *Greetings. XAML. cs* se kurzorem v `Button_Click` události.

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

### <a name="debug-with-breakpoints&quot;></a>Ladění pomocí zarážek

Můžete otestovat kód během ladění přidáním některých zarážek. Zarážky můžete **přidat kliknutím na**  >  levý okraj editoru vedle řádku kódu, kde **chcete,** aby došlo k přerušení, nebo stisknutím klávesy **F9**.

#### <a name=&quot;add-breakpoints&quot;></a>Přidání zarážek

1. Otevřete soubor *Greetings. XAML. cs* a vyberte následující řádek: `MessageBox.Show(&quot;Hello.")`

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

### <a name="build-a-release-version-of-the-application&quot;></a>Sestavení verze pro vydání aplikace

Teď, když jste ověřili, že všechno funguje, můžete připravit sestavení pro vydání aplikace.

1. V hlavní nabídce vyberte **sestavit**  >  **Vyčistit řešení** a odstraňte mezilehlé soubory a výstupní soubory, které byly vytvořeny během předchozích sestavení. To není nutné, ale čistí výstupy sestavení ladění.

1. Změňte konfiguraci sestavení pro HelloWPFApp z **Debug** na **release** pomocí ovládacího prvku rozevíracího seznamu na panelu nástrojů (aktuálně říká &quot;ladit").

1. Sestavte řešení kliknutím na **sestavit** sestavení  >  **řešení**.

Blahopřejeme k dokončení tohoto kurzu! Můžete najít *.exe* , které jste vytvořili v rámci vašeho řešení a adresáře projektu (*. ..\HelloWPFApp\HelloWPFApp\bin\Release*).

## <a name="next-steps"></a>Další kroky

Blahopřejeme k dokončení tohoto kurzu! Pokud se chcete dozvědět ještě víc, pokračujte v následujících kurzech.

> [!div class="nextstepaction"]
> [Pokračovat s dalšími kurzy WPF](/dotnet/framework/wpf/getting-started/wpf-walkthroughs/)

## <a name="see-also"></a>Viz také

- [Tipy pro vyšší produktivitu](../../ide/productivity-features.md)
