---
title: Hello World aplikace pomocí WPF v Visual Basic
description: Vytvoření jednoduché aplikace Windows Desktop .NET v Visual Basic pomocí sady Visual Studio pomocí architektury uživatelského rozhraní Windows Presentation Foundation (WPF).
ms.custom: seodec18, get-started
ms.date: 04/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: conceptual
dev_langs:
- VB
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d850f709921120fcb85f78f46eb0307d29801d11
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579946"
---
# <a name="tutorial-create-a-simple-application-with-visual-basic"></a>Kurz: Vytvoření jednoduché aplikace pomocí Visual Basic

Po dokončení tohoto kurzu se seznámíte s mnoha nástroji, dialogovými okny a návrháři, které můžete použít při vývoji aplikací pomocí sady Visual Studio. Vytvoříte aplikaci "Hello, World", navrhnete uživatelské rozhraní, přidáte kód a budete ladit chyby, zatímco se naučíte pracovat v integrovaném vývojovém prostředí ([IDE](visual-studio-ide.md)).

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

## <a name="configure-the-ide"></a>Nastavení integrovaného vývojového prostředí (IDE)

::: moniker range="vs-2017"

Při prvním otevření aplikace Visual Studio budete vyzváni k přihlášení. Tento krok je pro tento kurz volitelný. V dalším kroku se zobrazí dialogové okno s výzvou, abyste si zvolili vývojové nastavení a barevný motiv. Ponechte výchozí nastavení a klikněte na **Spustit Visual Studio**.

![Dialogové okno zvolit nastavení](../media/exploreide-settings.png)

Po spuštění sady Visual Studio se zobrazí okna nástrojů, nabídky a panely nástrojů a prostor hlavního okna. Okna nástrojů jsou ukotvena na levé a pravé straně okna aplikace, s možností **snadného spuštění**, řádku nabídek a standardní panel nástrojů v horní části. Ve středu okna aplikace je **Úvodní stránka**. Při načítání řešení nebo projektu se zobrazí editory a návrháři v prostoru, kde je **Úvodní stránka** . Při vývoji aplikace strávíte nejvíce času v této centrální oblasti.

![Integrované vývojové prostředí (IDE) sady Visual Studio 2017 s obecným nastavením](../media/exploreide-idewithgeneralsettings.png)

::: moniker-end

::: moniker range=">=vs-2019"

Při spuštění sady Visual Studio se nejprve otevře okno Start. Pokud chcete otevřít vývojové prostředí, vyberte **pokračovat bez kódu** . Zobrazí se okna nástrojů, nabídky a panely nástrojů a prostor hlavního okna. Okna nástrojů jsou ukotvena na levé a pravé straně okna aplikace, pomocí vyhledávacího pole, řádku nabídek a standardního panelu nástrojů v horní části. Při načítání řešení nebo projektu se editory a návrháře zobrazí v centrálním prostoru okna aplikace. Při vývoji aplikace strávíte nejvíce času v této centrální oblasti.

::: moniker-end

## <a name="create-the-project"></a>Vytvoření projektu

Při vytváření aplikace v systému Visual Studio je třeba nejprve vytvořit projekt a řešení. V tomto příkladu vytvoříte projekt Windows Presentation Foundation (WPF).

::: moniker range="vs-2017"

1. Vytvoření nového projektu Na panelu nabídek vyberte **soubor** > **Nový** > **projekt**.

     ![Na panelu nabídek vyberte možnosti soubor, nový, projekt.](../media/exploreide-filenewproject.png)

2. V dialogovém okně **Nový projekt** vyberte možnost **nainstalované** > **Visual Basic** > kategorii **Desktop systému Windows** a vyberte šablonu **aplikace WPF (.NET Framework)** . Pojmenujte projekt **HelloWPFApp**a vyberte **OK**.

     ![Šablona aplikace WPF v dialogovém okně Nový projekt sady Visual Studio](media/exploreide-newproject-vb.png)

Visual Studio vytvoří projekt a řešení HelloWPFApp a **Průzkumník řešení** zobrazí různé soubory. **Návrhář WPF** zobrazuje návrhové zobrazení a zobrazení XAML souboru *MainWindow. XAML* v rozděleném zobrazení. Posunutí příčky můžete zobrazit více nebo méně z obou zobrazení. Můžete zvolit, zda chcete zobrazit pouze vizuální zobrazení nebo pouze zobrazení XAML. V **Průzkumník řešení**se zobrazí následující položky:

![Průzkumník řešení se načetly soubory HelloWPFApp](../media/exploreide-hellowpfappfiles.png)

::: moniker-end

::: moniker range="vs-2019"

1. Otevřete Visual Studio 2019.

2. Na obrazovce **vytvořit nový projekt** vyhledejte "WPF" a zvolte **aplikace WPF (.NET Framework)** a pak klikněte na tlačítko **Další**.

   ![Šablona aplikace WPF v dialogovém okně Nový projekt sady Visual Studio](media/vs-2019/exploreide-newprojectvb-vs2019.png)

3. Na další obrazovce zadejte název projektu, **HelloWPFApp**a klikněte na **vytvořit**.

Visual Studio vytvoří projekt a řešení HelloWPFApp a **Průzkumník řešení** zobrazí různé soubory. **Návrhář WPF** zobrazuje návrhové zobrazení a zobrazení XAML souboru *MainWindow. XAML* v rozděleném zobrazení. Posunutí příčky můžete zobrazit více nebo méně z obou zobrazení. Můžete zvolit, zda chcete zobrazit pouze vizuální zobrazení nebo pouze zobrazení XAML. V **Průzkumník řešení**se zobrazí následující položky:

![Průzkumník řešení se načetly soubory HelloWPFApp](../media/vs-2019/exploreide-hellowpfappfiles.png)

::: moniker-end

> [!NOTE]
> Další informace o jazyce XAML (eXtensible Application Markup Language) naleznete na stránce [Přehled XAML pro WPF](/dotnet/framework/wpf/advanced/xaml-overview-wpf) .

Poté, co jste projekt vytvořili, jej můžete upravit. Pomocí okna **vlastnosti** (naleznete v nabídce **zobrazení** ) můžete zobrazit a změnit možnosti položek projektu, ovládacích prvků a dalších položek v aplikaci.

### <a name="change-the-name-of-mainwindowxaml"></a>Změna názvu souboru MainWindow. XAML

Pojďme dát MainWindow konkrétnější název. V **Průzkumník řešení**klikněte pravým tlačítkem na *MainWindow. XAML* a vyberte **Přejmenovat**. Přejmenujte soubor na *Greetings. XAML*.

## <a name="design-the-user-interface-ui"></a>Návrh uživatelského rozhraní (UI)

Pokud návrhář není otevřen, vyberte možnost *Greetings. XAML* v **Průzkumník řešení**a stisknutím klávesy **SHIFT**+**F7** Otevřete návrháře.

Do této aplikace přidáme tři typy ovládacích prvků: ovládací prvek <xref:System.Windows.Controls.TextBlock>, dva ovládací prvky <xref:System.Windows.Controls.RadioButton> a ovládací prvek <xref:System.Windows.Controls.Button>.

### <a name="add-a-textblock-control"></a>Přidání ovládacího prvku TextBlock

1. Stisknutím klávesy **Ctrl**+**Q** aktivujte vyhledávací pole a zadejte **sadu nástrojů**. V seznamu výsledků vyberte možnost **zobrazit > sada nástrojů** .

2. V **sadě nástrojů**rozbalte uzel **běžné ovládací prvky WPF** pro zobrazení ovládacího prvku TextBlock.

     ![Sada nástrojů se zvýrazněným ovládacím prvkem TextBlock](../media/exploreide-textblocktoolbox.png)

3. Přidejte ovládací prvek TextBlock do návrhové plochy tak, že vyberete položku **TextBlock** a přetáhnete ji do okna na návrhové ploše. Vycentrovat ovládací prvek v horní části okna. V aplikaci Visual Studio 2019 a novějších můžete použít červené pokyny k centrování ovládacího prvku.

Okno aplikace by mělo vypadat jako na následujícím obrázku:

![TextBlock ovládacího prvku na formuláři Greetings](../media/exploreide-greetingswithtextblockonly.png)

Značka XAML by měla vypadat podobně jako v následujícím příkladu:

```xaml
<TextBlock HorizontalAlignment="Left" Margin="381,100,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
```

### <a name="customize-the-text-in-the-text-block"></a>Přizpůsobení textu v textovém bloku

1. V zobrazení XAML vyhledejte značku pro TextBlock a změňte atribut text:

   ```xaml
   Text="Select a message option and then choose the Display button."
   ```

2. V případě potřeby TextBlock zarovnat znovu na střed a uložte změny stisknutím kombinace kláves CTRL + S nebo pomocí položky nabídky **soubor** .

Dále do formuláře přidejte dva ovládací prvky [RadioButton](/dotnet/framework/wpf/controls/radiobutton) .

### <a name="add-radio-buttons"></a>Přidat přepínače

1. V **sadě nástrojů**Najděte ovládací prvek **RadioButton** .

     ![Okno panelu nástrojů s vybraným ovládacím prvkem RadioButton](../media/exploreide-radiobuttontoolbox.png)

2. Přidejte dva ovládací prvky RadioButton na návrhovou plochu tak, že vyberete položku **RadioButton** a přetáhnete ji do okna na návrhové ploše. Přesuňte tlačítka (tak, že je vyberete a použijete klávesy se šipkami), aby se tlačítka zobrazovala vedle sebe pod ovládacím prvkem TextBlock. Použijte červené pokyny pro zarovnání ovládacích prvků.

     Okno aplikace by mělo vypadat takto:

     ![Formulář s pozdravem s ovládacím prvkem TextBlock a dvěma přepínači](../media/exploreide-greetingswithradiobuttons.png)

3. V okně **vlastnosti** levého ovládacího prvku RadioButton změňte vlastnost **Name** (vlastnost v horní části okna **vlastnosti** ) na `HelloButton`.

     ![Okno vlastností RadioButton](../media/exploreide-buttonproperties.png)

4. V okně **vlastnosti** pravého ovládacího prvku RadioButton změňte vlastnost **Name** na `GoodbyeButton`a uložte provedené změny.

Nyní můžete zadat text k zobrazení u obou ovládacích prvků RadioButton. Následující postup aktualizuje vlastnost **obsah** ovládacího prvku RadioButton.

### <a name="add-display-text-for-each-radio-button"></a>Přidat text zobrazení pro každý přepínač

Aktualizujte atribut **obsahu** pro `HelloButton` a `GoodbyeButton` na `"Hello"` a `"Goodbye"` v jazyce XAML. Kód XAML by teď měl vypadat podobně jako v následujícím příkladu:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Nastaví přepínač pro kontrolu ve výchozím nastavení.

V tomto kroku nastavíme HelloButton, aby se kontrolovaly ve výchozím nastavení, takže se vždycky vybrala jedna z těchto dvou přepínačů.

V zobrazení XAML vyhledejte značku pro HelloButton a přidejte atribut- **checked** :

```xaml
IsChecked="True"
```

Konečný prvek uživatelského rozhraní, který přidáte, je ovládací prvek [tlačítko](/dotnet/framework/wpf/controls/button) .

### <a name="add-the-button-control"></a>Přidání ovládacího prvku tlačítko

1. V sadě **nástrojů**vyhledejte ovládací prvek **tlačítko** a poté jej přidejte do návrhové plochy v ovládacích prvcích RadioButton přetažením do formuláře v zobrazení Návrh. Pokud používáte Visual Studio 2019 nebo novější, vám červená čára pomůže zarovnat na střed ovládacího prvku.

2. V zobrazení XAML změňte hodnotu **obsahu** pro ovládací prvek tlačítko z `Content="Button"` na `Content="Display"`a pak změny uložte.

     Značka by měla vypadat podobně jako v následujícím příkladu: `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`

     Okno aplikace by mělo vypadat jako na následujícím obrázku.

     ![Formulář s pozdravem s popisky ovládacích prvků](../media/exploreide-greetingswithcontrollabels.png)

### <a name="add-code-to-the-display-button"></a>Přidání kódu k tlačítku zobrazit

Po spuštění této aplikace se zobrazí okno se zprávou, když uživatel zvolí přepínač a pak zvolí tlačítko pro **zobrazení** . Objeví se jedno okno se zprávou pro Hello a druhé se zprávou pro Goodbye. Pro vytvoření tohoto chování přidáte kód do události `Button_Click` v souboru *Greetings. XAML. vb* nebo *Greetings.XAML.cs*.

1. Na návrhové ploše poklikejte na tlačítko **Zobrazit** .

     Otevře se *Greetings. XAML. vb* s kurzorem v události `Button_Click`.

    ```vb
    Private Sub Button_Click(sender As Object, e As RoutedEventArgs)

    End Sub
    ```

2. Zadejte následující kód:

    ```vb
    If HelloButton.IsChecked = True Then
        MessageBox.Show("Hello.")
    ElseIf GoodbyeButton.IsChecked = True Then
        MessageBox.Show("Goodbye.")
    End If
    ```

3. Uložte aplikaci.

## <a name="debug-and-test-the-application"></a>Ladění a testování aplikace

V dalším kroku aplikaci provedete tak, aby hledala chyby a otestovali, že se obě okna se zprávou zobrazují správně. V následujících pokynech se dozvíte, jak sestavit a spustit ladicí program, ale později si můžete přečíst [sestavení aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) a [ladění WPF](../../debugger/debugging-wpf.md) pro další informace.

### <a name="find-and-fix-errors"></a>Vyhledání a oprava chyb

V tomto kroku zjistíte chybu, kterou jsme dříve způsobili změnou názvu souboru *MainWindow. XAML* .

#### <a name="start-debugging-and-find-the-error"></a>Spustit ladění a najít chybu

1. Spusťte ladicí program stisknutím klávesy **F5** nebo výběrem možnosti **ladění**a potom **Spusťte ladění**.

   Zobrazí se okno **režim přerušení** a okno **výstup** indikuje, že došlo k IOException: nelze najít prostředek ' MainWindow. XAML '.

   ![Snímek obrazovky IOException zprávy](../media/exploreide-ioexception.png)

2. Ukončete ladicí program výběrem možnosti **ladění** > **Zastavit ladění**.

Na začátku tohoto kurzu jsme přejmenovali *MainWindow.* XAML na *Greetings. XAML* , ale kód pořád odkazuje na *MainWindow. XAML* jako spouštěcí identifikátor URI pro aplikaci, takže projekt nejde spustit.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Jako spouštěcí identifikátor URI zadejte Greetings. XAML.

1. V **Průzkumník řešení**otevřete soubor *Application. XAML* .

2. Změňte `StartupUri="MainWindow.xaml"` na `StartupUri="Greetings.xaml"`a pak změny uložte.

Znovu spusťte ladicí program (stiskněte klávesu **F5**). Měli byste vidět okno **Greetings** aplikace.

::: moniker range="vs-2017"
![Snímek obrazovky běžící aplikace](media/exploreide-wpf-running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Snímek obrazovky běžící aplikace](media/vs-2019/exploreide-wpf-running-app.png)
::: moniker-end

 Nyní zavřete okno aplikace a zastavte ladění.

### <a name="debug-with-breakpoints"></a>Ladění pomocí zarážek

Můžete otestovat kód během ladění přidáním některých zarážek. Zarážky lze přidat výběrem možnosti **ladění** > **Přepnout zarážku**kliknutím na levý okraj editoru vedle řádku kódu, kde chcete, aby došlo k přerušení, nebo stisknutím klávesy **F9**.

#### <a name="add-breakpoints"></a>Přidat zarážky

1. Otevřete soubor *Greetings. XAML. vb*a vyberte následující řádek: `MessageBox.Show("Hello.")`

2. Stisknutím klávesy **F9** nebo z nabídky přidejte zarážku tak, že vyberete **ladění**a potom **přepnete zarážku**.

   Na levém okraji okna editoru se vedle řádku kódu zobrazí červený kruh.

3. Vyberte následující řádek: `MessageBox.Show("Goodbye.")`.

4. Stisknutím klávesy **F9** přidejte zarážku a stisknutím klávesy **F5** spusťte ladění.

5. V okně **Greetings** vyberte přepínač **Hello** a pak klikněte na tlačítko **Zobrazit** .

   Čára `MessageBox.Show("Hello.")` je zvýrazněna žlutou. V dolní části rozhraní IDE jsou okna Automatické hodnoty, místní hodnoty a kukátka ukotvena na levé straně a zásobník volání, zarážky, nastavení výjimek, příkaz, okamžité a výstupní okna jsou ukotveny společně na pravé straně.

   ![Snímek obrazovky se zarážkou v ladicím programu](media/exploreide-debugbreakpoint.png)

6. Na panelu nabídek vyberte možnost **ladění** > **Krok ven**.

     Aplikace bude pokračovat v provádění a zobrazí se okno se zprávou se slovem "Hello".

7. Kliknutím na tlačítko **OK** v okně se zprávou ho zavřete.

8. V okně **Greetings** vyberte přepínač rozdálení a pak **klikněte na tlačítko** **Zobrazit** .

     Čára `MessageBox.Show("Goodbye.")` je zvýrazněna žlutou.

9. Pokračujte v ladění kliknutím na klávesu **F5** . Když se zobrazí okno se zprávou, zavřete ho kliknutím na tlačítko **OK** v okně se zprávou.

10. Zavřete okno aplikace a zastavte ladění.

11. Na panelu nabídek vyberte možnost **ladění** > **zakažte všechny zarážky**.

### <a name="view-a-representation-of-the-ui-elements"></a>Zobrazit reprezentace prvků uživatelského rozhraní

Ve spuštěné aplikaci byste měli vidět widget, který se zobrazí v horní části okna. Jedná se o pomocníka za běhu, který poskytuje rychlý přístup k některým užitečným funkcím ladění. Klikněte na první tlačítko, **přejděte do živého vizuálního stromu**. Mělo by se zobrazit okno se stromovou strukturou, která obsahuje všechny vizuální prvky vaší stránky. Rozbalením uzlů Najděte tlačítka, která jste přidali.

![Snímek obrazovky okna živého vizuálního stromu](media/vs-2019/exploreide-live-visual-tree.png)

### <a name="build-a-release-version-of-the-application"></a>Sestavení verze pro vydání aplikace

Teď, když jste ověřili, že vše funguje, si můžete připravit sestavení pro vydání aplikace.

1. V hlavní nabídce vyberte **sestavit** > **Vyčistit řešení** a odstraňte mezilehlé soubory a výstupní soubory, které byly vytvořeny během předchozích sestavení. To není nutné, ale čistí výstupy sestavení ladění.

2. Změňte konfiguraci sestavení pro HelloWPFApp z **Debug** na **release** pomocí ovládacího prvku rozevíracího seznamu na panelu nástrojů (aktuálně říká "ladit").

3. Sestavte řešení výběrem možnosti **sestavit** > **Sestavit řešení**.

Blahopřejeme k dokončení tohoto kurzu! Můžete najít soubor *. exe* , který jste vytvořili v rámci vašeho řešení a adresáře projektu ( *. ..\HelloWPFApp\HelloWPFApp\bin\Release*).

## <a name="see-also"></a>Viz také

::: moniker range="vs-2017"

- [Co je nového v aplikaci Visual Studio 2017](../../ide/whats-new-visual-studio-2017.md)
- [Tipy pro vyšší produktivitu](../../ide/productivity-features.md)

::: moniker-end

::: moniker range="vs-2019"

- [Co je nového v aplikaci Visual Studio 2019](../../ide/whats-new-visual-studio-2019.md)
- [Tipy pro vyšší produktivitu](../../ide/productivity-features.md)

::: moniker-end