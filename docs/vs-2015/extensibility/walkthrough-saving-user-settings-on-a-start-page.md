---
title: 'Návod: ukládání uživatelských nastavení na úvodní stránce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8976d329f6303d60cc00609bc9ed9471456c1b63
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "64837689"
---
# <a name="walkthrough-saving-user-settings-on-a-start-page"></a>Návod: Ukládání uživatelských nastavení na úvodní stránce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete zachovat nastavení uživatele pro úvodní stránku. Pomocí tohoto návodu můžete vytvořit ovládací prvek, který uloží nastavení do registru, když uživatel klikne na tlačítko, a pak toto nastavení načte při každém načtení úvodní stránky. Vzhledem k tomu, že šablona projektu úvodní stránka obsahuje přizpůsobitelný uživatelský ovládací prvek a výchozí úvodní stránka XAML volá tento ovládací prvek, není nutné upravovat úvodní stránku samotnou.  
  
 Úložiště nastavení, které je vytvořena v tomto návodu, je instancí <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> rozhraní, které čte a zapisuje do následujícího umístění registru při volání: HKCU\Software\Microsoft\VisualStudio\14.0 \\ *CollectionName*  
  
 Pokud je spuštěn v experimentální instanci aplikace Visual Studio, uloží nastavení čtení a zápisy do HKCU\Software\Microsoft\VisualStudio\14.0Exp \\ *CollectionName.*  
  
 Další informace o tom, jak zachovat nastavení, najdete v tématu [rozšíření uživatelských nastavení a možností](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="prerequisites"></a>Požadavky  
  
> [!NOTE]
> Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
>   
> Šablonu projektu úvodní stránky si můžete stáhnout pomocí **Správce rozšíření**.  
  
## <a name="setting-up-the-project"></a>Nastavení projektu  
  
#### <a name="to-configure-the-project-for-this-walkthrough"></a>Konfigurace projektu pro tento návod  
  
1. Vytvořte projekt úvodní stránky pomocí šablony projektu úvodní stránka, jak je popsáno v [tématu Vytvoření vlastní úvodní stránky](../misc/creating-your-own-start-page.md). Pojmenujte projekt **SaveMySettings**.  
  
2. V **Průzkumník řešení**přidejte do projektu StartPageControl následující odkazy na sestavení:  
  
    - EnvDTE  
  
    - EnvDTE80  
  
    - Microsoft. VisualStudio. OLE. Interop  
  
    - Microsoft. VisualStudio. Shell. Interop. 11.0  
  
3. Otevřete MyControl. XAML.  
  
4. V podokně XAML v <xref:System.Windows.Controls.UserControl> definici elementu nejvyšší úrovně přidejte následující deklaraci události po deklaraci oboru názvů.  
  
    ```  
    Loaded="OnLoaded"  
    ```  
  
5. V podokně návrh klikněte na hlavní oblast ovládacího prvku a potom stiskněte klávesu DELETE.  
  
     Tím se <xref:System.Windows.Controls.Border> element a všechno v něm odstraní a opustí jenom element nejvyšší úrovně <xref:System.Windows.Controls.Grid> .  
  
6. Z **panelu nástrojů**přetáhněte <xref:System.Windows.Controls.StackPanel> ovládací prvek do mřížky.  
  
7. Nyní přetáhněte <xref:System.Windows.Controls.TextBlock> tlačítko, a <xref:System.Windows.Controls.TextBox> a na <xref:System.Windows.Controls.StackPanel> .  
  
8. Přidejte atribut **x:Name** pro <xref:System.Windows.Controls.TextBox> a `Click` událost pro <xref:System.Windows.Controls.Button> , jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implementing-the-user-control"></a>Implementace uživatelského ovládacího prvku  
  
#### <a name="to-implement-the-user-control"></a>Implementace uživatelského ovládacího prvku  
  
1. V podokně XAML klikněte pravým tlačítkem na `Click` atribut <xref:System.Windows.Controls.Button> prvku a pak klikněte na **Přejít k obslužné rutině události**.  
  
     Tím se otevře MyControl.xaml.cs a vytvoří se pro událost obslužná rutina se zástupnými procedurami `Button_Click` .  
  
2. `using`Na začátek souboru přidejte následující příkazy.  
  
     [!code-csharp[StartPageDTE#11](../snippets/csharp/VS_Snippets_VSSDK/startpagedte/cs/startpagecontrol/mycontrol.xaml.cs#11)]  
  
3. Přidejte soukromou `SettingsStore` vlastnost, jak je znázorněno v následujícím příkladu.  
  
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
  
     Tato vlastnost nejprve získá odkaz na <xref:EnvDTE80.DTE2> rozhraní, které obsahuje model automatizačních objektů, z <xref:System.Windows.FrameworkElement.DataContext%2A> uživatelského ovládacího prvku a poté používá DTE k získání instance <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> rozhraní. Pak použije tuto instanci k vrácení aktuálního nastavení uživatele.  
  
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
  
     Tím se zapíše obsah textového pole do pole "MySetting" v kolekci "MySettings" v registru. Pokud kolekce neexistuje, vytvoří se.  
  
5. Přidejte následující obslužnou rutinu pro `OnLoaded` událost uživatelského ovládacího prvku.  
  
    ```csharp  
    private void OnLoaded(Object sender, RoutedEventArgs e)  
    {  
        string value;  
        SettingsStore.GetStringOrDefault(  
            "MySettings", "MySetting", "", out value);  
        txtblk.Text = value;  
    }  
    ```  
  
     Tím se nastaví text textového pole na aktuální hodnotu "MySetting".  
  
6. Sestavte uživatelský ovládací prvek.  
  
7. V **Průzkumník řešení**otevřete source. extension. vsixmanifest.  
  
8. V editoru manifestu nastavte **název produktu** na **Uložit úvodní stránku nastavení**.  
  
     Tím se nastaví název úvodní stránky tak, jak se má zobrazit v seznamu **přizpůsobení úvodní stránky** v dialogovém okně **Možnosti** .  
  
9. Sestavte StartPage. XAML.  
  
## <a name="testing-the-control"></a>Testování ovládacího prvku  
  
#### <a name="to-test-the-user-control"></a>Testování uživatelského ovládacího prvku  
  
1. Stiskněte klávesu F5.  
  
     Otevře se experimentální instance aplikace Visual Studio.  
  
2. V experimentální instanci v nabídce **nástroje** klikněte na **Možnosti**.  
  
3. V uzlu **prostředí** klikněte na **spouštění**a potom v seznamu **Přizpůsobit úvodní stránku** vyberte **[nainstalované rozšíření] Úvodní stránka pro uložení nastavení**.  
  
     Klikněte na **OK**.  
  
4. Zavřete úvodní stránku, pokud je otevřená, a pak v nabídce **zobrazení** klikněte na **Úvodní stránka**.  
  
5. Na úvodní stránce klikněte na kartu **MyControl** .  
  
6. Do textového pole zadejte **Cat**a pak klikněte na **Uložit moje nastavení**.  
  
7. Zavřete úvodní stránku a znovu ji otevřete.  
  
     V textovém poli by se mělo zobrazit slovo "Cat".  
  
8. Nahradí slovo "Cat" slovem "pes". Neklepejte na tlačítko.  
  
9. Zavřete úvodní stránku a znovu ji otevřete.  
  
     V textovém poli by se mělo zobrazit slovo "pes", a to i v případě, že se nastavení neuložilo. K tomu dochází, protože Visual Studio uchovává okna nástrojů v paměti, i když jsou zavřené, dokud nebude aplikace Visual Studio sama zavřená.  
  
10. Zavřete experimentální instanci sady Visual Studio.  
  
11. Stisknutím klávesy F5 znovu otevřete experimentální instanci.  
  
12. V textovém poli by se mělo zobrazit slovo "Cat".  
  
## <a name="next-steps"></a>Další kroky  
 Tento uživatelský ovládací prvek lze upravit tak, aby ušetřil a načetl libovolný počet vlastních nastavení pomocí různých hodnot z různých obslužných rutin událostí pro získání a nastavení `SettingsStore` Vlastnosti. Pokud použijete jiný `propertyName` parametr pro každé volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A> , hodnoty nebudou v registru navzájem přepsány.  
  
## <a name="see-also"></a>Viz také  
 <xref:EnvDTE80.DTE2?displayProperty=fullName>   
 [Vytvoření vlastní úvodní stránky](../misc/creating-your-own-start-page.md)   
 [Přidání příkazů sady Visual Studio na úvodní stránku](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
