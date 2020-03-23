---
title: Aplikace Hello World s WPF v jazyce Visual Basic
description: Vytvořte jednoduchou aplikaci Windows Desktop .NET v jazyce Visual Basic pomocí sady Visual Studio pomocí rozhraní ui služby WPF (Windows Presentation Foundation).
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77579946"
---
# <a name="tutorial-create-a-simple-application-with-visual-basic"></a>Kurz: Vytvoření jednoduché aplikace pomocí jazyka Visual Basic

Dokončením tohoto kurzu se seznámíte s mnoha nástroji, dialogovými okny a návrháři, které můžete použít při vývoji aplikací s visual studio. Vytvoříte aplikaci "Hello, World", navrhnete ui, přidáte kód a ladíte chyby, zatímco se dozvíte o práci v integrovaném vývojovém prostředí ([IDE](visual-studio-ide.md)).

::: moniker range="vs-2017"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ji zdarma.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ji zdarma.

::: moniker-end

## <a name="configure-the-ide"></a>Nastavení integrovaného vývojového prostředí (IDE)

::: moniker range="vs-2017"

Při prvním spuštění sady Visual Studio budete vyzváni k přihlášení. Tento krok je volitelný pro tento kurz. Dále se vám může zobrazit dialogové okno, které vás požádá o výběr nastavení vývoje a barevného motivu. Zachovat výchozí hodnoty a zvolit **Spustit Visual Studio**.

![Dialogové okno Zvolit nastavení](../media/exploreide-settings.png)

Po spuštění sady Visual Studio se zobrazí okna nástrojů, nabídky a panely nástrojů a hlavní prostor okna. Okna nástrojů jsou ukotvena na levé a pravé straně okna aplikace s **panelem snadnéspuštění**, panelu nabídek a standardním panelem nástrojů nahoře. Uprostřed okna aplikace je **úvodní stránka**. Když načtete řešení nebo projekt, editory a návrháři se zobrazí v prostoru, kde je **úvodní stránka.** Když vyvíjíte aplikaci, strávíte většinu svého času v této centrální oblasti.

![IDE sady Visual Studio 2017 s použitým obecným nastavením](../media/exploreide-idewithgeneralsettings.png)

::: moniker-end

::: moniker range=">=vs-2019"

Při spuštění sady Visual Studio se nejprve otevře počáteční okno. Chcete-li otevřít vývojové prostředí, vyberte **možnost Pokračovat bez kódu.** Zobrazí se okna nástrojů, nabídky a panely nástrojů a hlavní prostor okna. Okna nástrojů jsou ukotvena na levé a pravé straně okna aplikace s vyhledávacím polem, panelem nabídek a standardním panelem nástrojů v horní části. Při načtení řešení nebo projektu se v centrálním prostoru okna aplikace zobrazí editory a návrháři. Když vyvíjíte aplikaci, strávíte většinu svého času v této centrální oblasti.

::: moniker-end

## <a name="create-the-project"></a>Vytvoření projektu

Při vytváření aplikace v systému Visual Studio je třeba nejprve vytvořit projekt a řešení. V tomto příkladu vytvoříte projekt Windows Presentation Foundation (WPF).

::: moniker range="vs-2017"

1. Vytvoření nového projektu Na řádku nabídek vyberte **Soubor** > **nového** > **projektu**.

     ![Na řádku nabídek zvolte Soubor, Nový, Projekt](../media/exploreide-filenewproject.png)

2. V dialogovém okně **Nový projekt** vyberte kategorii **Nainstalovaná** > plocha**systému Windows v jazyce Visual Basic** > **Windows Desktop** a potom vyberte šablonu **aplikace WPF (.NET Framework).** Pojmenujte projekt **HelloWPFApp**a vyberte **OK**.

     ![Šablona aplikace WPF v dialogovém okně Nový projekt Visual Studia](media/exploreide-newproject-vb.png)

Visual Studio vytvoří projekt a řešení HelloWPFApp a **Průzkumník řešení** zobrazí různé soubory. **WPF Designer** zobrazuje návrhové zobrazení a zobrazení XAML *MainWindow.xaml* v rozděleném zobrazení. Posunutím rozdělovače můžete zobrazit více či méně z obou zobrazení. Můžete zvolit zobrazení pouze vizuálního zobrazení nebo pouze zobrazení XAML. V **Průzkumníku řešení**se zobrazí následující položky :

![Průzkumník řešení s načtenými soubory HelloWPFApp](../media/exploreide-hellowpfappfiles.png)

::: moniker-end

::: moniker range="vs-2019"

1. Otevřete Visual Studio 2019.

2. Na obrazovce **Vytvořit nový projekt** vyhledejte "WPF" a zvolte **WPF App (.NET Framework)** a pak zvolte **Další**.

   ![Šablona aplikace WPF v dialogovém okně Nový projekt Visual Studia](media/vs-2019/exploreide-newprojectvb-vs2019.png)

3. Na další obrazovce pojmenujte projekt **HelloWPFApp**a zvolte **Vytvořit**.

Visual Studio vytvoří projekt a řešení HelloWPFApp a **Průzkumník řešení** zobrazí různé soubory. **WPF Designer** zobrazuje návrhové zobrazení a zobrazení XAML *MainWindow.xaml* v rozděleném zobrazení. Posunutím rozdělovače můžete zobrazit více či méně z obou zobrazení. Můžete zvolit zobrazení pouze vizuálního zobrazení nebo pouze zobrazení XAML. V **Průzkumníku řešení**se zobrazí následující položky :

![Průzkumník řešení s načtenými soubory HelloWPFApp](../media/vs-2019/exploreide-hellowpfappfiles.png)

::: moniker-end

> [!NOTE]
> Další informace o XAML (eXtensible Application Markup Language) najdete v [přehledu XAML pro](/dotnet/framework/wpf/advanced/xaml-overview-wpf) stránku WPF.

Poté, co jste projekt vytvořili, jej můžete upravit. Pomocí okna **Vlastnosti** (najdete v nabídce **Zobrazení)** můžete zobrazit a změnit možnosti pro položky projektu, ovládací prvky a další položky v aplikaci.

### <a name="change-the-name-of-mainwindowxaml"></a>Změna názvu souboru MainWindow.xaml

Dejme MainWindow konkrétnější název. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na *soubor MainWindow.xaml* a zvolte **Přejmenovat**. Přejmenujte soubor na *Greetings.xaml*.

## <a name="design-the-user-interface-ui"></a>Návrh uživatelského rozhraní (UI)

Pokud návrhář není otevřený, vyberte v **Průzkumníku řešení** *položku Greetings.xaml* a stisknutím **klávesy Shift**+**F7** návrháře otevřete.

Do této aplikace přidáme tři typy <xref:System.Windows.Controls.TextBlock> ovládacích <xref:System.Windows.Controls.RadioButton> prvků: <xref:System.Windows.Controls.Button> ovládací prvek, dva ovládací prvky a ovládací prvek.

### <a name="add-a-textblock-control"></a>Přidání ovládacího prvku TextBlock

1. Stisknutím **klávesy Ctrl**+**Q** aktivujte vyhledávací pole a zadejte panel **nástrojů**. Ze seznamu výsledků zvolte **Zobrazit > panel nástrojů.**

2. V **panelu nástrojů**rozbalte uzel **Common WPF Controls** a zobejít ovládací prvek TextBlock.

     ![Panel nástrojů se zvýrazněným ovládacím prvkem TextBlock](../media/exploreide-textblocktoolbox.png)

3. Přidejte ovládací prvek TextBlock do návrhové plochy výběrem položky **TextBlock** a přetažením do okna na návrhové ploše. Vystředit ovládací prvek v horní části okna. Ve Visual Studiu 2019 a novějších můžete ovládací prvek vystředit pomocí červených pokynů.

Okno aplikace by mělo vypadat jako na následujícím obrázku:

![Ovládací prvek TextBlock ve formuláři Pozdravy](../media/exploreide-greetingswithtextblockonly.png)

Značky XAML by měly vypadat podobně jako v následujícím příkladu:

```xaml
<TextBlock HorizontalAlignment="Left" Margin="381,100,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
```

### <a name="customize-the-text-in-the-text-block"></a>Přizpůsobení textu v textovém bloku

1. V zobrazení XAML vyhledejte značky pro TextBlock a změňte atribut Text:

   ```xaml
   Text="Select a message option and then choose the Display button."
   ```

2. V případě potřeby textový blok znovu zastředíte a uložte změny stisknutím ctrl+s nebo pomocí položky nabídky **Soubor.**

Dále přidáte do formuláře dva ovládací prvky [RadioButton.](/dotnet/framework/wpf/controls/radiobutton)

### <a name="add-radio-buttons"></a>Přidání tlačítek přepínače

1. V **panelu nástrojů**vyhledejte ovládací prvek **RadioButton.**

     ![Okno panelu nástrojů s vybraným ovládacím prvkem RadioButton](../media/exploreide-radiobuttontoolbox.png)

2. Přidejte dva ovládací prvky RadioButton k návrhové ploše výběrem položky **RadioButton** a přetažením do okna na návrhové ploše. Přesuňte tlačítka (jejich výběrem a pomocí kláves se šipkami), aby se tlačítka zobrazovala vedle sebe pod ovládacím prvkem TextBlock. K zarovnání ovládacích prvků použijte červené pokyny.

     Okno aplikace by mělo vypadat takto:

     ![Formulář Pozdravy s ovládáním TextBlock a dvěma tlačítky](../media/exploreide-greetingswithradiobuttons.png)

3. V okně **Vlastnosti** pro levý ovládací prvek RadioButton změňte vlastnost **Name** (vlastnost `HelloButton`v horní části okna **Vlastnosti)** na .

     ![Okno vlastností RadioButton](../media/exploreide-buttonproperties.png)

4. V okně **Vlastnosti** pro pravý ovládací prvek RadioButton změňte vlastnost **Name** na `GoodbyeButton`a uložte změny.

Nyní můžete zadat text k zobrazení u obou ovládacích prvků RadioButton. Následující postup aktualizuje vlastnost **Content** pro ovládací prvek RadioButton.

### <a name="add-display-text-for-each-radio-button"></a>Přidání textu zobrazení pro každé přepínací tlačítko

Aktualizujte **Content** atribut Content `HelloButton` `GoodbyeButton` pro `"Hello"` `"Goodbye"` xaml a do a v ní. Značky XAML by nyní měly vypadat podobně jako v následujícím příkladu:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Nastavení přepínače, které má být ve výchozím nastavení zkontrolováno

V tomto kroku nastavíme HelloButton, který má být ve výchozím nastavení zkontrolován tak, aby bylo vždy vybráno jedno ze dvou přepínacích tlačítek.

V zobrazení XAML vyhledejte značku pro HelloButton a přidejte atribut **IsChecked:**

```xaml
IsChecked="True"
```

Konečný prvek ui, který přidáte, je ovládací prvek [Button.](/dotnet/framework/wpf/controls/button)

### <a name="add-the-button-control"></a>Přidání ovládacího prvku tlačítka

1. V **panelu nástrojů**najděte ovládací prvek **Button** a přidejte jej na návrhovou plochu pod ovládacími prvky RadioButton přetažením do formuláře v návrhovém zobrazení. Pokud používáte Visual Studio 2019 nebo novější, červená čára vám pomůže vystředit ovládací prvek.

2. V zobrazení XAML změňte hodnotu **obsahu** ovládacího prvku Button z `Content="Button"` na `Content="Display"`.

     Značky by se měly podobat následujícímu příkladu:`<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`

     Okno aplikace by mělo vypadat jako na následujícím obrázku.

     ![Formulář Pozdravy s popisky ovládacích prvků](../media/exploreide-greetingswithcontrollabels.png)

### <a name="add-code-to-the-display-button"></a>Přidání kódu do tlačítka zobrazení

Po spuštění této aplikace se zobrazí okno se zprávou poté, co uživatel vybere přepínací tlačítko a pak zvolí tlačítko **Zobrazit.** Objeví se jedno okno se zprávou pro Hello a druhé se zprávou pro Goodbye. Chcete-li vytvořit toto chování, `Button_Click` přidáte kód k události v *Greetings.xaml.vb* nebo *Greetings.xaml.cs*.

1. Na návrhové ploše poklepejte na tlačítko **Zobrazit.**

     *Greetings.xaml.vb* otevře, s kurzorem `Button_Click` v události.

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

Dále budete ladit aplikace hledat chyby a testování, že obě okna se zprávami se zobrazí správně. Následující pokyny vám řeknou, jak vytvořit a spustit ladicí program, ale později si můžete přečíst [build wpf aplikace (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) a [ladění WPF](../../debugger/debugging-wpf.md) pro další informace.

### <a name="find-and-fix-errors"></a>Vyhledání a oprava chyb

V tomto kroku najdete chybu, kterou jsme způsobili dříve změnou názvu souboru *MainWindow.xaml.*

#### <a name="start-debugging-and-find-the-error"></a>Spusťte ladění a vyhledejte chybu

1. Začněte ladicí program stisknutím **klávesy F5** nebo výběrem **možnosti Ladění**a **potom začněte ladění**.

   Zobrazí se okno **režimu přerušení** a okno **Výstup** označuje, že došlo k výjimce IOException: Nelze najít prostředek mainwindow.xaml.

   ![Snímek obrazovky se zprávou IOException](../media/exploreide-ioexception.png)

2. Stop the debugger by choosing **Debug** > **Stop Debugging**.

Na začátku tohoto kurzu jsme *přejmenovali MainWindow.xaml* na *Greetings.xaml,* ale kód stále odkazuje na *MainWindow.xaml* jako spouštěcí identifikátor URI pro aplikaci, takže projekt nelze spustit.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Zadejte greetings.xaml jako spouštěcí identifikátor URI

1. V **Průzkumníku řešení**otevřete soubor *Application.xaml.*

2. `StartupUri="MainWindow.xaml"` Změňte `StartupUri="Greetings.xaml"`na a uložte změny.

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

1. Otevřete *soubor Greetings.xaml.vb*a vyberte následující řádek:`MessageBox.Show("Hello.")`

2. Přidejte zarážku stisknutím **klávesy F9** nebo z nabídky výběrem **možnosti Ladění**a následnému **přepnutí zarážky**.

   Na levém okraji okna editoru se vedle řádku kódu zobrazí červený kruh.

3. Vyberte následující `MessageBox.Show("Goodbye.")`řádek: .

4. Stisknutím klávesy **F9** přidejte zarážku a stisknutím **klávesy F5** spusťte ladění.

5. V okně **Pozdravy** zvolte **přepínací** tlačítko Hello a pak zvolte tlačítko **Zobrazit.**

   Řádek `MessageBox.Show("Hello.")` je zvýrazněn žlutě. V dolní části ide, autos, místní a sledovat okna jsou ukotveny společně na levé straně a zásobník uvolvolání, zarážky, nastavení výjimek, příkaz, okamžité a výstupní okna jsou ukotveny společně na pravé straně.

   ![Snímek obrazovky s zarážkou v ladicím programu](media/exploreide-debugbreakpoint.png)

6. Na řádku nabídek zvolte **Ladění krok** > **ven**.

     Aplikace pokračuje v provádění a zobrazí se okno se zprávou se slovem "Hello".

7. Chcete-li okno se zprávou zavřít, zvolte tlačítko **OK** na schránce se zprávou.

8. V okně **Pozdravy** zvolte **přepínací** tlačítko Sbohem a pak zvolte tlačítko **Zobrazit.**

     Řádek `MessageBox.Show("Goodbye.")` je zvýrazněn žlutě.

9. Chcete-li pokračovat v ladění, zvolte klávesu **F5.** Když se zobrazí okno se zprávou, zvolte tlačítko **OK** na okno se zprávou zavřít.

10. Zavřete okno aplikace a zastavte ladění.

11. Na řádku nabídek zvolte **Ladit** > **Zakázat všechny zarážky**.

### <a name="view-a-representation-of-the-ui-elements"></a>Zobrazení reprezentace prvků uživatelského rozhraní

V běžící aplikaci byste měli vidět widget, který se zobrazí v horní části okna. Jedná se o pomocníka runtime, který poskytuje rychlý přístup k některým užitečným funkcím ladění. Klikněte na první tlačítko, **Přejít na Live Visual Tree**. Měli byste vidět okno se stromem, který obsahuje všechny vizuální prvky stránky. Rozbalte uzly a vyhledejte přidaná tlačítka.

![Snímek obrazovky s oknem Živé vizuální strom](media/vs-2019/exploreide-live-visual-tree.png)

### <a name="build-a-release-version-of-the-application"></a>Sestavení verze pro vydání aplikace

Teď, když jste ověřili, že vše funguje, můžete připravit sestavení verze aplikace.

1. V hlavní nabídce vyberte **Build** > **Clean řešení,** chcete-li odstranit zprostředkující soubory a výstupní soubory, které byly vytvořeny během předchozích sestavení. To není nutné, ale vyčistí výstupy sestavení ladění.

2. Změňte konfiguraci sestavení pro HelloWPFApp z **ladění** na **vydání** pomocí ovládacího prvku rozevírací seznam na panelu nástrojů (aktuálně se říká "Ladění").

3. Vytvořte řešení výběrem **sestavení** > **sestavení řešení**.

Gratulujeme k dokončení tohoto výukového programu! Soubor EXE, který jste *vytvořili,* najdete pod adresářem řešení a projektu (*...\HelloWPFApp\HelloWPFApp\bin\Release*).

## <a name="see-also"></a>Viz také

::: moniker range="vs-2017"

- [Co je nového ve Visual Studiu 2017](../../ide/whats-new-visual-studio-2017.md)
- [Tipy pro vyšší produktivitu](../../ide/productivity-features.md)

::: moniker-end

::: moniker range="vs-2019"

- [Novinky v sadě Visual Studio 2019](../../ide/whats-new-visual-studio-2019.md)
- [Tipy pro vyšší produktivitu](../../ide/productivity-features.md)

::: moniker-end