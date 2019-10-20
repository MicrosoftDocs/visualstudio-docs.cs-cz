---
title: 'Návod: ukládání uživatelských nastavení na úvodní stránce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: fe3d1040089a4b78368a4da94933a4a1440afafd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647912"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>Návod: uložení uživatelských nastavení na úvodní stránce

Můžete zachovat nastavení uživatele pro úvodní stránku. Pomocí tohoto návodu můžete vytvořit ovládací prvek, který uloží nastavení do registru, když uživatel klikne na tlačítko, a pak toto nastavení načte při každém načtení úvodní stránky. Vzhledem k tomu, že šablona projektu úvodní stránka obsahuje přizpůsobitelný uživatelský ovládací prvek a výchozí úvodní stránka XAML volá tento ovládací prvek, nemusíte upravovat úvodní stránku.

Úložiště nastavení, které je vytvořena v tomto návodu, je instance rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore>, která čte a zapisuje do následujícího umístění registru, když je volána: **HKCU\Software\Microsoft\VisualStudio\14.0 \\ \<CollectionName >**

Když je spuštěn v experimentální instanci aplikace Visual Studio, uloží nastavení čtení a zápisy do **HKCU\Software\Microsoft\VisualStudio\14.0Exp \\ \<CollectionName >.**

Další informace o tom, jak zachovat nastavení, najdete v tématu [rozšíření uživatelských nastavení a možností](../extensibility/extending-user-settings-and-options.md).

## <a name="prerequisites"></a>Požadavky

> [!NOTE]
> Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).
>
> Šablonu projektu úvodní stránky si můžete stáhnout pomocí **Správce rozšíření**.

## <a name="set-up-the-project"></a>Nastavení projektu

1. Vytvořte projekt úvodní stránky, jak je popsáno v tématu [Vytvoření vlastní úvodní stránky](creating-a-custom-start-page.md). Pojmenujte projekt **SaveMySettings**.

2. V **Průzkumník řešení**přidejte do projektu StartPageControl následující odkazy na sestavení:

    - EnvDTE

    - EnvDTE80

    - Microsoft. VisualStudio. OLE. Interop

    - Microsoft. VisualStudio. Shell. Interop. 11.0

3. Otevřete *MyControl. XAML*.

4. V podokně XAML v definici elementu nejvyšší úrovně <xref:System.Windows.Controls.UserControl> přidejte následující deklaraci události po deklaraci oboru názvů.

    ```xml
    Loaded="OnLoaded"
    ```

5. V podokně návrh klikněte na hlavní oblast ovládacího prvku a potom stiskněte klávesu **Delete**.

     Tento krok odstraní prvek <xref:System.Windows.Controls.Border> a vše v něm a ponechá pouze element nejvyšší úrovně <xref:System.Windows.Controls.Grid>.

6. Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Controls.StackPanel> do mřížky.

7. Nyní přetáhněte <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.TextBox> a tlačítko na <xref:System.Windows.Controls.StackPanel>.

8. Přidejte atribut **x:Name** pro <xref:System.Windows.Controls.TextBox> a událost `Click` pro <xref:System.Windows.Controls.Button>, jak je znázorněno v následujícím příkladu.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Implementace uživatelského ovládacího prvku

1. V podokně XAML klikněte pravým tlačítkem myši na atribut `Click` prvku <xref:System.Windows.Controls.Button> a pak klikněte na možnost **Přejít k obslužné rutině události**.

     Tento krok otevře *MyControl.XAML.cs*a vytvoří obslužnou rutinu zástupných procedur pro událost `Button_Click`.

2. Do horní části souboru přidejte následující direktivy `using`.

     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]

3. Přidejte vlastnost Private `SettingsStore`, jak je znázorněno v následujícím příkladu.

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

     Tato vlastnost nejprve získá odkaz na rozhraní <xref:EnvDTE80.DTE2>, které obsahuje model automatizačních objektů, z <xref:System.Windows.FrameworkElement.DataContext%2A> uživatelského ovládacího prvku a poté používá DTE k získání instance rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>. Pak použije tuto instanci k vrácení aktuálního nastavení uživatele.

4. Následujícím způsobem zadejte událost `Button_Click`.

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

     Tím se zapíše obsah textového pole do pole "MySetting" v kolekci "MySettings" v registru. Pokud kolekce neexistuje, je vytvořena.

5. Přidejte následující obslužnou rutinu pro událost `OnLoaded` uživatelského ovládacího prvku.

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

6. Sestavte uživatelský ovládací prvek.

7. V **Průzkumník řešení**otevřete *source. extension. vsixmanifest*.

8. V editoru manifestu nastavte **název produktu** na **Uložit úvodní stránku nastavení**.

     Tato funkce nastaví název úvodní stránky tak, jak se má zobrazit v seznamu **přizpůsobení úvodní stránky** v dialogovém okně **Možnosti** .

9. Sestavte *StartPage. XAML*.

## <a name="test-the-control"></a>Testování ovládacího prvku

1. Stiskněte klávesu **F5**.

     Otevře se experimentální instance aplikace Visual Studio.

2. V experimentální instanci v nabídce **nástroje** klikněte na **Možnosti**.

3. V uzlu **prostředí** klikněte na **spouštění**a potom v seznamu **Přizpůsobit úvodní stránku** vyberte **[nainstalované rozšíření] Úvodní stránka pro uložení nastavení**.

     Klikněte na tlačítko **OK**.

4. Zavřete úvodní stránku, pokud je otevřená, a potom v nabídce **zobrazení** klikněte na možnost **Úvodní stránka**.

5. Na úvodní stránce klikněte na kartu **MyControl** .

6. Do textového pole zadejte **Cat**a pak klikněte na **Uložit moje nastavení**.

7. Zavřete úvodní stránku a znovu ji otevřete.

     V textovém poli by se mělo zobrazit slovo "Cat".

8. Nahradí slovo "Cat" slovem "pes". Neklepejte na tlačítko.

9. Zavřete úvodní stránku a znovu ji otevřete.

     V textovém poli by se mělo zobrazit slovo "pes", a to i v případě, že jste nastavení neuložili, protože Visual Studio uchovává okna nástrojů v paměti, i když jsou zavřené, dokud se Visual Studio sám nezavře.

10. Zavřete experimentální instanci sady Visual Studio.

11. Stisknutím klávesy **F5** znovu otevřete experimentální instanci.

12. V textovém poli by se mělo zobrazit slovo "Cat".

## <a name="next-steps"></a>Další kroky

Tento uživatelský ovládací prvek lze upravit tak, aby ušetřil a načetl libovolný počet vlastních nastavení pomocí různých hodnot z různých obslužných rutin událostí pro získání a nastavení vlastnosti `SettingsStore`. Pokud pro každé volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A> použijete jiný parametr `propertyName`, hodnoty nejsou v registru navzájem přepsány.

## <a name="see-also"></a>Viz také:

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Přidávání příkazů sady Visual Studio na úvodní stránku](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
