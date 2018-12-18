---
title: 'Návod: Ukládání uživatelských nastavení na úvodní stránce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bdba9506b15b0d11f2c741c8651af2098b2f9da4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763295"
---
# <a name="walkthrough-saving-user-settings-on-a-start-page"></a>Návod: Ukládání uživatelských nastavení na úvodní stránce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zachování uživatelského nastavení pro úvodní stránku. Podle tohoto postupu můžete vytvořit ovládací prvek, který se nastavení uloží do registru, když uživatel klikne na tlačítko a pak načte nastavení pokaždé, když se načte úvodní stránky. Vzhledem k tomu, že šablona projektu úvodní stránka obsahuje přizpůsobitelný uživatelského ovládacího prvku a výchozí spuštění stránky XAML volá tento ovládací prvek, není nutné upravit vlastní úvodní stránky.  
  
 Nastavení úložiště, která je vytvořena instance v tomto návodu je instance <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> rozhraní, která čte a zapisuje do následujícího umístění registru, když je volána: HKCU\Software\Microsoft\VisualStudio\14.0\\  *CollectionName*  
  
 Když je spuštěn v experimentální instanci sady Visual Studio, úložiště nastavení čte a zapisuje do HKCU\Software\Microsoft\VisualStudio\14.0Exp\\*CollectionName.*  
  
 Další informace o tom, jak zachovat nastavení najdete v tématu [rozšíření uživatelská nastavení a možnosti](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="prerequisites"></a>Požadavky  
  
> [!NOTE]
>  Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
>   
>  Šablona projektu úvodní stránku můžete stáhnout pomocí **Správce rozšíření**.  
  
## <a name="setting-up-the-project"></a>Nastavení projektu  
  
#### <a name="to-configure-the-project-for-this-walkthrough"></a>Ke konfiguraci projektu pro Tento názorný postup  
  
1.  Vytvoření projektu úvodní stránky pomocí šablony projektu úvodní stránku, jak je popsáno v [vytváření svůj vlastní úvodní stránku](../misc/creating-your-own-start-page.md). Pojmenujte projekt **SaveMySettings**.  
  
2.  V **Průzkumníka řešení**, přidejte následující odkazy na sestavení do projektu StartPageControl:  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Sestavení Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
3.  Otevřete MyControl.xaml.  
  
4.  Z podokna XAML na nejvyšší úrovni <xref:System.Windows.Controls.UserControl> definice prvku, přidejte následující deklarace události po deklarace oboru názvů.  
  
    ```  
    Loaded="OnLoaded"  
    ```  
  
5.  V podokně návrhu klikněte na hlavní oblasti ovládacího prvku a stiskněte klávesu DELETE.  
  
     Tím <xref:System.Windows.Controls.Border> elementu a všechno, co v a ponechá pouze na nejvyšší úrovni <xref:System.Windows.Controls.Grid> elementu.  
  
6.  Z **nástrojů**, přetáhněte <xref:System.Windows.Controls.StackPanel> ovládací prvek mřížky.  
  
7.  Nyní přetáhněte <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.TextBox>a potom tlačítko <xref:System.Windows.Controls.StackPanel>.  
  
8.  Přidat **x: Name** atribut pro <xref:System.Windows.Controls.TextBox>a `Click` události <xref:System.Windows.Controls.Button>, jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implementing-the-user-control"></a>Implementace uživatelského ovládacího prvku  
  
#### <a name="to-implement-the-user-control"></a>K implementaci uživatelského ovládacího prvku  
  
1.  V podokně XAML, klikněte pravým tlačítkem myši `Click` atribut <xref:System.Windows.Controls.Button> element a pak klikněte na tlačítko **Navigovat do obslužné rutiny události**.  
  
     Tím se otevře MyControl.xaml.cs a vytvoří obslužnou rutinu zástupné procedury pro `Button_Click` událostí.  
  
2.  Přidejte následující `using` příkazy do horní části souboru.  
  
     [!code-csharp[StartPageDTE#11](../snippets/csharp/VS_Snippets_VSSDK/startpagedte/cs/startpagecontrol/mycontrol.xaml.cs#11)]  
  
3.  Přidat soukromé `SettingsStore` vlastnost, jak je znázorněno v následujícím příkladu.  
  
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
  
     Nejprve získá odkaz na tuto vlastnost <xref:EnvDTE80.DTE2> rozhraní, které obsahuje model objektu automatizace z <xref:System.Windows.FrameworkElement.DataContext%2A> uživatelský ovládací prvek a pak používá DTE k získání instance typu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> rozhraní. Potom použije tuto instanci vrátit nastavení aktuálního uživatele.  
  
4.  Vyplňte `Button_Click` událostí následujícím způsobem.  
  
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
  
     To zapíše obsah textového pole na pole "MySetting" v kolekci "MySettings" v registru. Pokud kolekce buď neexistuje, vytvoří se.  
  
5.  Přidejte následující obslužnou rutinu pro `OnLoaded` události uživatelského ovládacího prvku.  
  
    ```csharp  
    private void OnLoaded(Object sender, RoutedEventArgs e)  
    {  
        string value;  
        SettingsStore.GetStringOrDefault(  
            "MySettings", "MySetting", "", out value);  
        txtblk.Text = value;  
    }  
    ```  
  
     Tím se nastaví text do textového pole na aktuální hodnotu "MySetting".  
  
6.  Vytvoření uživatelského ovládacího prvku.  
  
7.  V **Průzkumníka řešení**, otevřete source.extension.vsixmanifest.  
  
8.  V editoru manifestu nastavte **název produktu** k **uložit Moje nastavení úvodní stránka**.  
  
     Tím se nastaví na název úvodní stránky jak se má zobrazit v **přizpůsobit úvodní stránku** v seznamu **možnosti** dialogové okno.  
  
9. Vytvářejte StartPage.xaml.  
  
## <a name="testing-the-control"></a>Testování ovládacího prvku  
  
#### <a name="to-test-the-user-control"></a>Pro testování uživatelského ovládacího prvku  
  
1.  Stiskněte klávesu F5.  
  
     Otevře se experimentální instanci sady Visual Studio.  
  
2.  V experimentální instanci na **nástroje** nabídky, klikněte na tlačítko **možnosti**.  
  
3.  V **prostředí** uzel, klikněte na tlačítko **spuštění**a pak na **přizpůsobit úvodní stránku** seznamu vyberte **[nainstalované rozšíření] uložit Moje nastavení úvodní stránka** .  
  
     Klikněte na tlačítko **OK**.  
  
4.  Zavřít úvodní stránku, pokud je otevřený a potom na **zobrazení** nabídky, klikněte na tlačítko **úvodní stránka**.  
  
5.  Na úvodní stránce klikněte na tlačítko **MůjOvládacíPrvek** kartu.  
  
6.  V textovém poli zadejte **Cat**a potom klikněte na tlačítko **uložit Moje nastavení**.  
  
7.  Zavřít úvodní stránku a znovu ji spusťte.  
  
     Slovo "Cat" má být zobrazena v textovém poli.  
  
8.  Nahraďte slovo "Cat" slova "Pes". Neklikejte na tlačítko.  
  
9. Zavřít úvodní stránku a znovu ji spusťte.  
  
     Slovo "Pes" má být zobrazena v textovém poli, i v případě, že nastavení nebyla uložena. To je způsobeno udržuje okna nástrojů Visual Studio v paměti, i když se zavřou, dokud není zavřena samotnou sadu Visual Studio.  
  
10. Ukončete experimentální instanci sady Visual Studio.  
  
11. Stiskněte klávesu F5 a znovu otevřete experimentální instanci aplikace.  
  
12. Slovo "Cat" má být zobrazena v textovém poli.  
  
## <a name="next-steps"></a>Další kroky  
 Můžete upravit tento uživatelský ovládací prvek pro uložení a načtení libovolný počet vlastních nastavení s použitím různých hodnot z obslužné rutiny událostí různých k získání a nastavení `SettingsStore` vlastnost. Za předpokladu, můžete použít jinou `propertyName` parametr pro každé volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>, nepřepíše navzájem hodnoty v registru.  
  
## <a name="see-also"></a>Viz také  
 <xref:EnvDTE80.DTE2?displayProperty=fullName>   
 [Vytvoření vlastní úvodní stránky](../misc/creating-your-own-start-page.md)   
 [Přidání příkazů sady Visual Studio na úvodní stránku](../extensibility/adding-visual-studio-commands-to-a-start-page.md)

