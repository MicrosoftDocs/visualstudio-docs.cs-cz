---
title: 'Návod: Uložení uživatelských nastavení na úvodní stránce | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 8c791bb33d6c6a3952c14d5073857b0c3131cecf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697077"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>Návod: Uložení uživatelských nastavení na úvodní stránce

Můžete zachovat uživatelská nastavení úvodní stránky. Podle tohoto návodu můžete vytvořit ovládací prvek, který uloží nastavení do registru, když uživatel klepne na tlačítko, a poté toto nastavení načte při každém načtení úvodní stránky. Vzhledem k tomu, že šablona projektu Úvodní stránka obsahuje přizpůsobitelný uživatelský ovládací prvek a výchozí počáteční stránka XAML tento ovládací prvek volá, nemusíte měnit samotnou úvodní stránku.

Úložiště nastavení, které je vytvořena v tomto návodu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> je instancí rozhraní, které čte a zapisuje do následujícího umístění registru, když se nazývá: **HKCU\Software\Microsoft\VisualStudio\14.0\\\<CollectionName>**

Když je spuštěnv experimentální instanci sady Visual Studio, úložiště nastavení čte a zapisuje do **HKCU\Software\Microsoft\VisualStudio\14.0Exp\\\<CollectionName>.**

Další informace o zachování nastavení naleznete v [tématu Rozšíření uživatelských nastavení a možností](../extensibility/extending-user-settings-and-options.md).

## <a name="prerequisites"></a>Požadavky

> [!NOTE]
> Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sady Visual Studio SDK. Další informace naleznete v [tématu Visual Studio SDK](../extensibility/visual-studio-sdk.md).
>
> Šablonu projektu Úvodní stránka si můžete stáhnout pomocí **Správce rozšíření**.

## <a name="set-up-the-project"></a>Nastavení projektu

1. Vytvořte projekt Úvodní stránka, jak je popsáno v [úvodní stránce Vytvoření vlastní úvodní stránky](creating-a-custom-start-page.md). Pojmenujte projekt **SaveMySettings**.

2. V **Průzkumníku řešení**přidejte do projektu StartPageControl následující odkazy na sestavení:

    - EnvDTE

    - EnvDTE80

    - Microsoft.VisualStudio.OLE.Interop

    - Microsoft.VisualStudio.Shell.Interop.11.0

3. Otevřete *soubor MyControl.xaml*.

4. Z podokna XAML v definici prvku nejvyšší úrovně <xref:System.Windows.Controls.UserControl> přidejte následující deklaraci události za deklarace oboru názvů.

    ```xml
    Loaded="OnLoaded"
    ```

5. V podokně návrhu klepněte na hlavní oblast ovládacího prvku a stiskněte **klávesu Delete**.

     Tento krok odebere <xref:System.Windows.Controls.Border> prvek a vše v něm <xref:System.Windows.Controls.Grid> a ponechá pouze prvek nejvyšší úrovně.

6. Z **panelu nástrojů** <xref:System.Windows.Controls.StackPanel> přetáhněte ovládací prvek do mřížky.

7. Nyní přetáhněte <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.TextBox>tlačítko , a <xref:System.Windows.Controls.StackPanel>a button na .

8. Přidejte atribut **x:Name** pro <xref:System.Windows.Controls.TextBox> `Click` a událost <xref:System.Windows.Controls.Button>pro , jak je znázorněno v následujícím příkladu.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Implementace uživatelského ovládacího prvku

1. V podokně XAML klepněte `Click` pravým <xref:System.Windows.Controls.Button> tlačítkem myši na atribut prvku a potom klepněte na **příkaz Přejít na obslužnou rutinu události**.

     Tento krok otevře *MyControl.xaml.cs*a vytvoří obslužnou rutinu se zakázaným inzerováním `Button_Click` pro událost.

2. Přidejte `using` následující direktivy do horní části souboru.

     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]

3. Přidejte `SettingsStore` soukromou vlastnost, jak je znázorněno v následujícím příkladu.

    ```csharp
    private IVsWritableSettingsStore _settingsStore = null;
    private IVsWritableSettingsStore SettingsStore
    {
        get
        {
            if (_settingsStore == null)
            {
                // Get a reference to the DTE from the DataContext.
                var typeDescriptor = DataContext as ICustomTypeDescriptor;
                var propertyCollection = typeDescriptor.GetProperties();
                var dte = propertyCollection.Find("DTE", false).GetValue(
                    DataContext) as DTE2;

                // Get the settings manager from the DTE.
                var serviceProvider = new ServiceProvider(
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
                var settingsManager = serviceProvider.GetService(
                    typeof(SVsSettingsManager)) as IVsSettingsManager;

                // Write the user settings to _settingsStore.
                settingsManager.GetWritableSettingsStore(
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,
                    out _settingsStore);
            }
            return _settingsStore;
        }
    }
    ```

     Tato vlastnost nejprve získá <xref:EnvDTE80.DTE2> odkaz na rozhraní, které obsahuje <xref:System.Windows.FrameworkElement.DataContext%2A> objektový model Automation, z uživatelského ovládacího <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> prvku a potom používá DTE získat instanci rozhraní. Potom použije tuto instanci k vrácení aktuálního uživatelského nastavení.

4. Vyplňte `Button_Click` událost následujícím způsobem.

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {
        int exists = 0;
        SettingsStore.CollectionExists("MySettings", out exists);
        if (exists != 1)
        {
            SettingsStore.CreateCollection("MySettings");
        }
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);
    }
    ```

     To zapíše obsah textového pole do pole "MySetting" v kolekci "MySettings" v registru. Pokud kolekce neexistuje, je vytvořena.

5. Přidejte následující obslužnou rutinu `OnLoaded` pro událost uživatelského ovládacího prvku.

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     Tento kód nastaví text textového pole na aktuální hodnotu "MySetting".

6. Vytvořte uživatelský ovládací prvek.

7. V **Průzkumníku řešení**, open *source.extension.vsixmanifest*.

8. V editoru manifestu nastavte **název produktu** na **Uložit úvodní stránku nastavení**.

     Tato funkce nastaví název úvodní stránky tak, aby se zobrazila v seznamu **Přizpůsobit úvodní stránku** v dialogovém okně **Možnosti.**

9. Sestavení *souboru StartPage.xaml*.

## <a name="test-the-control"></a>Otestujte ovládací prvek

1. Stiskněte **klávesu F5**.

     Otevře se experimentální instance sady Visual Studio.

2. V experimentální instanci klikněte v nabídce **Nástroje** na **položku Možnosti**.

3. V uzlu **Prostředí** klepněte na **položku Spustit**a potom v seznamu **Přizpůsobit úvodní stránku** vyberte **možnost [Nainstalované rozšíření] Uložit úvodní stránku nastavení**.

     Klikněte na tlačítko **OK**.

4. Zavřete úvodní stránku, pokud je otevřená, a potom v nabídce **Zobrazení** klikněte na **Úvodní stránka**.

5. Na úvodní stránce klikněte na kartu **MyControl.**

6. Do textového pole zadejte **Kata**a klikněte na **Uložit moje nastavení**.

7. Zavřete úvodní stránku a znovu ji otevřete.

     V textovém poli by mělo být zobrazeno slovo "Kočka".

8. Nahraďte slovo "Kočka" slovem "Pes". Neklikejte na tlačítko.

9. Zavřete úvodní stránku a znovu ji otevřete.

     Slovo "Pes" by měla být zobrazena v textovém poli, i když jste neuložili nastavení, protože Visual Studio udržuje okna nástrojů v paměti, i když jsou uzavřeny, dokud Visual Studio sám zavře.

10. Zavřete experimentální instanci sady Visual Studio.

11. Stisknutím **klávesy F5** znovu otevřete experimentální instanci.

12. V textovém poli by mělo být zobrazeno slovo "Kočka".

## <a name="next-steps"></a>Další kroky

Tento uživatelský ovládací prvek můžete upravit tak, aby uklápěl a načítaný libovolný počet vlastních nastavení pomocí různých hodnot z různých obslužných rutin událostí, abyste získali a nastavili `SettingsStore` vlastnost. Tak dlouho, dokud `propertyName` použijete jiný <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>parametr pro každé volání , hodnoty nejsou přepsat navzájem v registru.

## <a name="see-also"></a>Viz také

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Přidání příkazů sady Visual Studio na úvodní stránku](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
