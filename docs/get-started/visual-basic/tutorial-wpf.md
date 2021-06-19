---
title: Hello World aplikace pomocí WPF v Visual Basic
description: Vytvoření jednoduché aplikace Windows Desktop .NET v Visual Basic pomocí sady Visual Studio pomocí architektury uživatelského rozhraní Windows Presentation Foundation (WPF).
ms.custom: vs-acquisition, seodec18, get-started
ms.date: 04/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
dev_langs:
- VB
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e757dc25fe094b1ffa745cd43ad251abbc9448a7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390122"
---
# <a name="tutorial-create-a-simple-application-with-visual-basic"></a>Kurz: Vytvoření jednoduché aplikace pomocí Visual Basic

Po dokončení tohoto kurzu se seznámíte s mnoha nástroji, dialogovými okny a návrháři, které můžete použít při vývoji aplikací pomocí sady Visual Studio. Vytvoříte aplikaci "Hello, World", navrhnete uživatelské rozhraní, přidáte kód a budete ladit chyby, zatímco se naučíte pracovat v integrovaném vývojovém prostředí ([IDE](visual-studio-ide.md)).

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2022"

Pokud jste ještě nenainstalovali Visual Studio 2022 Preview, nainstalujte ho zdarma na stránku [Visual studio 2022 Preview ke stažení](https://visualstudio.microsoft.com/vs/preview/vs2022) .

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

1. Vytvoření nového projektu Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

     ![Na panelu nabídek vyberte možnosti soubor, nový, projekt.](../media/exploreide-filenewproject.png)

2. V dialogovém okně **Nový projekt** vyberte kategorii **nainstalovaná**  >  **Visual Basic**  >  **Windows Desktop** a pak vyberte šablonu **aplikace WPF (.NET Framework)** . Pojmenujte projekt **HelloWPFApp** a vyberte **OK**.

     ![Šablona aplikace WPF v dialogovém okně Nový projekt sady Visual Studio](media/exploreide-newproject-vb.png)

Visual Studio vytvoří projekt a řešení HelloWPFApp a **Průzkumník řešení** zobrazí různé soubory. **Návrhář WPF** zobrazuje návrhové zobrazení a zobrazení XAML souboru *MainWindow. XAML* v rozděleném zobrazení. Posunutí příčky můžete zobrazit více nebo méně z obou zobrazení. Můžete zvolit, zda chcete zobrazit pouze vizuální zobrazení nebo pouze zobrazení XAML. V **Průzkumník řešení** se zobrazí následující položky:

![Průzkumník řešení se načetly soubory HelloWPFApp](../media/exploreide-hellowpfappfiles.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio.

2. Na obrazovce **vytvořit nový projekt** vyhledejte "WPF" a zvolte **aplikace WPF (.NET Framework)** a pak klikněte na tlačítko **Další**.

   ![Šablona aplikace WPF v dialogovém okně Nový projekt sady Visual Studio](media/vs-2019/exploreide-newprojectvb-vs2019.png)

3. Na další obrazovce zadejte název projektu, **HelloWPFApp** a klikněte na **vytvořit**.

Visual Studio vytvoří projekt a řešení HelloWPFApp a **Průzkumník řešení** zobrazí různé soubory. **Návrhář WPF** zobrazuje návrhové zobrazení a zobrazení XAML souboru *MainWindow. XAML* v rozděleném zobrazení. Posunutí příčky můžete zobrazit více nebo méně z obou zobrazení. Můžete zvolit, zda chcete zobrazit pouze vizuální zobrazení nebo pouze zobrazení XAML. V **Průzkumník řešení** se zobrazí následující položky:

![Průzkumník řešení se načetly soubory HelloWPFApp](../media/vs-2019/exploreide-hellowpfappfiles.png)

::: moniker-end

> [!NOTE]
> Další informace o jazyce XAML (eXtensible Application Markup Language) naleznete na stránce [Přehled XAML pro WPF](/dotnet/framework/wpf/advanced/xaml-overview-wpf) .

Poté, co jste projekt vytvořili, jej můžete upravit. Pomocí okna **vlastnosti** (naleznete v nabídce **zobrazení** ) můžete zobrazit a změnit možnosti položek projektu, ovládacích prvků a dalších položek v aplikaci.

### <a name="change-the-name-of-mainwindowxaml"></a>Změna názvu souboru MainWindow. XAML

Pojďme dát MainWindow konkrétnější název. V **Průzkumník řešení** klikněte pravým tlačítkem na *MainWindow. XAML* a vyberte **Přejmenovat**. Přejmenujte soubor na *Greetings. XAML*.

## <a name="design-the-user-interface-ui"></a>Návrh uživatelského rozhraní (UI)

Pokud návrhář není otevřen, vyberte možnost *Greetings. XAML* v **Průzkumník řešení** a stisknutím klávesy **SHIFT** + **F7** Otevřete návrháře.

Do této aplikace přidáme tři typy ovládacích prvků: <xref:System.Windows.Controls.TextBlock> ovládací prvek, dva <xref:System.Windows.Controls.RadioButton> ovládací prvky a <xref:System.Windows.Controls.Button> ovládací prvek.

### <a name="add-a-textblock-control"></a>Přidání ovládacího prvku TextBlock

1. Stisknutím klávesy **CTRL** + **Q** aktivujte vyhledávací pole a zadejte **sadu nástrojů**. V seznamu výsledků vyberte možnost **zobrazit > sada nástrojů** .

2. V **sadě nástrojů** rozbalte uzel **běžné ovládací prvky WPF** pro zobrazení ovládacího prvku TextBlock.

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

### <a name="add-radio-buttons"></a>Přidání tlačítek přepínače

1. V **sadě nástrojů** Najděte ovládací prvek **RadioButton** .

     ![Okno panelu nástrojů s vybraným ovládacím prvkem RadioButton](../media/exploreide-radiobuttontoolbox.png)

2. Přidejte dva ovládací prvky RadioButton na návrhovou plochu tak, že vyberete položku **RadioButton** a přetáhnete ji do okna na návrhové ploše. Přesuňte tlačítka (tak, že je vyberete a použijete klávesy se šipkami), aby se tlačítka zobrazovala vedle sebe pod ovládacím prvkem TextBlock. Použijte červené pokyny pro zarovnání ovládacích prvků.

     Okno aplikace by mělo vypadat takto:

     ![Formulář s pozdravem s ovládacím prvkem TextBlock a dvěma přepínači](../media/exploreide-greetingswithradiobuttons.png)

3. V okně **vlastnosti** levého ovládacího prvku RadioButton změňte vlastnost **Name** (vlastnost v horní části okna **vlastnosti** ) na `HelloButton` .

     ![Okno vlastností RadioButton](../media/exploreide-buttonproperties.png)

4. V okně **vlastnosti** pravého ovládacího prvku RadioButton změňte vlastnost **Name** na a `GoodbyeButton` uložte provedené změny.

Nyní můžete zadat text k zobrazení u obou ovládacích prvků RadioButton. Následující postup aktualizuje vlastnost **obsah** ovládacího prvku RadioButton.

### <a name="add-display-text-for-each-radio-button"></a>Přidat text zobrazení pro každý přepínač

Aktualizujte atribut **obsahu** pro `HelloButton` a a `GoodbyeButton` `"Hello"` `"Goodbye"` v jazyce XAML. Kód XAML by teď měl vypadat podobně jako v následujícím příkladu:

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

1. V sadě **nástrojů** vyhledejte ovládací prvek **tlačítko** a poté jej přidejte do návrhové plochy v ovládacích prvcích RadioButton přetažením do formuláře v zobrazení Návrh. Pokud používáte Visual Studio 2019 nebo novější, vám červená čára pomůže zarovnat na střed ovládacího prvku.

2. V zobrazení XAML změňte hodnotu **obsahu** pro ovládací prvek tlačítko z `Content="Button"` na a `Content="Display"` poté změny uložte.

     Kód by měl vypadat podobně jako v následujícím příkladu:   `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`

     Okno aplikace by mělo vypadat jako na následujícím obrázku.

     ![Formulář Greetings s popisky ovládacích prvku](../media/exploreide-greetingswithcontrollabels.png)

### <a name="add-code-to-the-display-button"></a>Přidání kódu do tlačítka zobrazení

Když se tato aplikace spustí, zobrazí se okno se zprávou, když uživatel zvolí přepínač a pak zvolí **tlačítko** Zobrazit. Objeví se jedno okno se zprávou pro Hello a druhé se zprávou pro Goodbye. Toto chování vytvoříte tak, že do události přidáte kód v `Button_Click` *souboru Greetings.xaml.vb* nebo *Greetings.xaml.cs.*

1. Na návrhové ploše poklikejte na **tlačítko Zobrazit.**

     *Otevře se soubor Greetings.xaml.vb* s kurzorem v `Button_Click` události .

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

Dále budete ladit aplikaci a hledat chyby a testovat, jestli se obě pole zpráv zobrazují správně. Následující pokyny vás informují, jak sestavit a spustit ladicí program, ale později si můžete přečíst témata Sestavení aplikace [WPF (WPF) a](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) [Ladění WPF,](../../debugger/debugging-wpf.md) kde najdete další informace.

### <a name="find-and-fix-errors"></a>Vyhledání a oprava chyb

V tomto kroku najdete chybu, kterou jsme dříve způsobili změnou názvu souboru *MainWindow.xaml.*

#### <a name="start-debugging-and-find-the-error"></a>Spusťte ladění a vyhledejte chybu.

1. Spusťte ladicí program stisknutím **klávesy F5** nebo **výběrem možnosti Ladit** a **pak spustit ladění.**

   Zobrazí **se okno Režim** přerušení a okno **Výstup** indikuje, že došlo k výjimce IOException: Nelze najít prostředek mainwindow.xaml.

   ![Snímek obrazovky se zprávou O výjimce IOException](../media/exploreide-ioexception.png)

2. Zastavte ladicí program tak, že **zvolíte**  >  **Ladit Zastavit ladění.**

Na začátku tohoto kurzu jsme *mainwindow.xaml* přejmenováváme na *Greetings.xaml,* ale kód stále odkazuje na *MainWindow.xaml* jako na spouštěcí identifikátor URI aplikace, takže projekt nemůže začít.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Jako spouštěcí identifikátor URI zadejte Greetings.xaml.

1. V **Průzkumník řešení** otevřete soubor *Application.xaml.*

2. Změňte `StartupUri="MainWindow.xaml"` na a pak změny `StartupUri="Greetings.xaml"` uložte.

Znovu spusťte ladicí program (stiskněte **F5**). Mělo by se **zobrazit okno Greetings** aplikace.

::: moniker range="vs-2017"
![Snímek obrazovky se spuštěnou aplikací](media/exploreide-wpf-running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Snímek obrazovky se spuštěnou aplikací](media/vs-2019/exploreide-wpf-running-app.png)
::: moniker-end

 Teď zavřete okno aplikace a ukončete ladění.

### <a name="debug-with-breakpoints&quot;></a>Ladění pomocí zarážek

Kód můžete během ladění otestovat přidáním některých zarážek. Zarážky můžete přidat tak, že zvolíte Přepnout zarážku pro ladění, kliknutím na levý okraj editoru vedle řádku kódu, kde chcete přerušení prolomit, nebo stisknutím  >   **klávesy F9**.

#### <a name=&quot;add-breakpoints&quot;></a>Přidání zarážek

1. Otevřete *soubor Greetings.xaml.vb* a vyberte následující řádek: `MessageBox.Show(&quot;Hello.")`

2. Stisknutím klávesy F9 nebo z nabídky **přidejte** zarážku tak, že vyberete **Ladit** a pak **Přepínáte zarážku**.

   Na levém okraji okna editoru se vedle řádku kódu zobrazí červený kruh.

3. Vyberte následující řádek: `MessageBox.Show("Goodbye.")` .

4. Stisknutím **klávesy F9** přidejte zarážku a stisknutím **klávesy F5** spusťte ladění.

5. V **okně Greetings** zvolte přepínač **Hello** a pak zvolte **tlačítko** Zobrazit.

   Řádek je `MessageBox.Show("Hello.")` zvýrazněný žlutou barvou. V dolní části integrovaného vývojového prostředí jsou okna Automatické hodnoty, Místní hodnoty a Sledování ukotvená společně na levé straně a na pravé straně jsou ukotvená okna Zásobník volání, Zarážky, Nastavení výjimek, Příkaz, Okamžité a Výstup.

   ![Snímek obrazovky se zarážkou v ladicím programu](media/exploreide-debugbreakpoint.png)

6. Na řádku nabídek zvolte **Ladit**  >  **krok ven.**

     Aplikace pokračuje v provádění a zobrazí se okno se zprávou se slovem "Hello".

7. Kliknutím na **tlačítko OK** v okně se zprávou ho zavřete.

8. V okně **Greetings** (Pozdrav) zvolte přepínač **Goodbye (Rozloučení)** a pak zvolte **tlačítko Display (Zobrazit).**

     Řádek je `MessageBox.Show("Goodbye.")` zvýrazněný žlutou barvou.

9. Pokud chcete pokračovat v ladění, zvolte klávesu **F5.** Jakmile se zobrazí okno se zprávou, zavřete ho kliknutím na tlačítko **OK** v okně se zprávou.

10. Zavřete okno aplikace, aby se zastavilo ladění.

11. Na řádku nabídek zvolte **Ladit**  >  **Zakázat všechny zarážky.**

### <a name="view-a-representation-of-the-ui-elements"></a>Zobrazení reprezentace prvků uživatelského rozhraní

Ve spuštěné aplikaci byste měli vidět widget, který se zobrazí v horní části okna. Jedná se o pomocný modul runtime, který poskytuje rychlý přístup k některým užitečným funkcím ladění. Klikněte na první tlačítko Přejít **na živý vizuální strom.** Mělo by se zobrazit okno se stromem, který obsahuje všechny vizuální prvky stránky. Rozbalte uzly a vyhledejte tlačítka, která jste přidali.

![Snímek obrazovky s oknem Live Visual Tree](media/vs-2019/exploreide-live-visual-tree.png)

### <a name="build-a-release-version-of-the-application"></a>Sestavení verze pro vydání aplikace

Teď, když jste ověřili, že všechno funguje, můžete připravit sestavení aplikace pro vydání.

1. V hlavní nabídce vyberte Build  >  **Clean solution (Sestavit** čisté řešení) a odstraňte zprostředkující soubory a výstupní soubory vytvořené během předchozích sestavení. To není nutné, ale vyčistí výstupy sestavení ladění.

2. Pomocí ovládacího prvku rozevíracího  seznamu  na panelu nástrojů změňte konfiguraci sestavení pro HelloWPFApp z Ladit na Vypustit (aktuálně se zobrazí Ladění).

3. Sestavte řešení výběrem možnosti **Sestavit**  >  **řešení sestavení.**

Blahopřejeme k dokončení tohoto kurzu! Soubor, který *jste.exe,* najdete v adresáři vašeho řešení a projektu (*...\HelloWPFApp\HelloWPFApp\bin\Release).*

## <a name="see-also"></a>Viz také

::: moniker range="vs-2017"

- [Novinky v sadě Visual Studio 2017](../../ide/whats-new-visual-studio-2017.md)
- [Tipy pro vyšší produktivitu](../../ide/productivity-features.md)

::: moniker-end

::: moniker range="vs-2019"

- [Co je nového v Visual Studio 2019](../../ide/whats-new-visual-studio-2019.md)
- [Tipy pro vyšší produktivitu](../../ide/productivity-features.md)

::: moniker-end

::: moniker range="vs-2022"

- [Tipy pro vyšší produktivitu](../../ide/productivity-features.md)

::: moniker-end
