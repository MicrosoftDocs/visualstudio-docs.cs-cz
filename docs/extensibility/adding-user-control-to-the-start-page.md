---
title: Přidání uživatelského ovládacího prvku na úvodní stránku | Microsoft Docs
description: Naučte se, jak přidat uživatelský ovládací prvek Windows Presentation Foundation (WPF) na úvodní stránku v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: fa812b477f88b03b8f0d4bdcba6c69f009ec2894
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597545"
---
# <a name="add-user-control-to-the-start-page"></a>Přidání uživatelského ovládacího prvku na úvodní stránku

Tento návod ukazuje, jak přidat odkaz knihovny DLL na vlastní úvodní stránku. Tento příklad přidá uživatelský ovládací prvek do řešení, sestaví uživatelský ovládací prvek a potom odkazuje na sestavené sestavení ze souboru úvodní stránky *. XAML* . Nová karta hostuje uživatelský ovládací prvek, který funguje jako základní webový prohlížeč.

Stejný postup můžete použít k přidání libovolného sestavení, které lze volat ze souboru *. XAML* .

## <a name="add-a-wpf-user-control-to-the-solution"></a>Přidání uživatelského ovládacího prvku WPF do řešení

Nejprve přidejte uživatelský ovládací prvek Windows Presentation Foundation (WPF) do řešení úvodní stránky.

1. Vytvořte úvodní stránku pomocí jsme vytvořili na [stránce vytvořit vlastní úvodní stránku](../extensibility/creating-a-custom-start-page.md).

2. V **Průzkumník řešení** klikněte pravým tlačítkem myši na řešení, klikněte na tlačítko **Přidat** a poté klikněte na možnost **Nový projekt**.

3. V levém podokně dialogového okna **Nový projekt** rozbalte uzel **Visual Basic** nebo **Visual C#** a klikněte na tlačítko **Windows**. V prostředním podokně vyberte možnost **Knihovna uživatelských ovládacích prvků WPF**.

4. Pojmenujte ovládací prvek `WebUserControl` a pak klikněte na **OK**.

## <a name="implement-the-user-control"></a>Implementace uživatelského ovládacího prvku

Chcete-li implementovat uživatelský ovládací prvek WPF, sestavte uživatelské rozhraní (UI) v jazyce XAML a potom zapište události kódu na pozadí v jazyce C# nebo v jiném jazyce rozhraní .NET.

### <a name="to-write-the-xaml-for-the-user-control"></a>Zápis XAML pro uživatelský ovládací prvek

1. Otevřete soubor XAML pro uživatelský ovládací prvek. V `<Grid>` elementu přidejte do ovládacího prvku následující definice řádků.

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. Do hlavního `<Grid>` elementu přidejte následující nový `<Grid>` prvek, který obsahuje textové pole pro zadání webových adres a tlačítko pro nastavení nové adresy.

    ```xml
    <Grid Grid.Row="0">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*" />
            <ColumnDefinition Width="Auto" />
        </Grid.ColumnDefinitions>
        <TextBox x:Name="UserSource" Grid.Column="0" />
        <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
    </Grid>
    ```

3. Do prvku nejvyšší úrovně přidejte následující rámec `<Grid>` hned za `<Grid>` prvek, který obsahuje tlačítko a textové pole.

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. Následující příklad ukazuje dokončený kód XAML pro uživatelský ovládací prvek.

    ```xml
    <UserControl x:Class="WebUserControl.UserControl1"
                 xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
                 xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
                 mc:Ignorable="d"
                 d:DesignHeight="300" d:DesignWidth="300">
        <Grid>
            <Grid.RowDefinitions>
                <RowDefinition Height="Auto"/>
                <RowDefinition Height="*" />
            </Grid.RowDefinitions>
            <Grid Grid.Row="0">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>
                <TextBox x:Name="UserSource" Grid.Column="0" />
                <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
            </Grid>
            <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
        </Grid>
    </UserControl>

    ```

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Zápis událostí kódu na pozadí pro uživatelský ovládací prvek

1. V Návrháři XAML poklikejte na tlačítko **nastavit adresu** , které jste přidali k ovládacímu prvku.

    V editoru kódu se otevře soubor *UserControl1.cs* .

2. V obslužné rutině události SetButton_Click zadejte následující.

    ```csharp
    private void SetButton_Click(object sender, RoutedEventArgs e)
    {
        try
        {
            this.WebFrame.Source = new Uri(this.UserSource.Text, UriKind.Absolute);
        }
        catch (Exception error)
        {
            MessageBox.Show(error.Message);
        }
    }
    ```

    Tento kód nastaví webovou adresu, která je zadána v textovém poli jako cíl pro webový prohlížeč. Pokud adresa není platná, kód vyvolá chybu.

3. Také je nutné zpracovat událost WebFrame_Navigated:

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. Sestavte řešení.

## <a name="add-the-user-control-to-the-start-page"></a>Přidání uživatelského ovládacího prvku na úvodní stránku

Chcete-li zpřístupnit tento ovládací prvek projektu úvodní stránky, v souboru projektu úvodní stránky přidejte odkaz na novou knihovnu ovládacích prvků. Potom můžete přidat ovládací prvek do kódu XAML úvodní stránky.

1. V **Průzkumník řešení** v projektu úvodní stránky klikněte pravým tlačítkem na **odkazy** a pak klikněte na **Přidat odkaz**.

2. Na kartě **projekty** vyberte prvek **WebUserControl** a pak klikněte na tlačítko **OK**.

3. V nabídce **Sestavení** klikněte na **Sestavit řešení**.

    Sestavení řešení zpřístupní uživatelský ovládací prvek IntelliSense pro jiné soubory v řešení.

    Chcete-li přidat ovládací prvek do kódu jazyka XAML pro úvodní stránku, přidejte do sestavení odkaz na obor názvů a pak ovládací prvek vložte na stránku.

### <a name="to-add-the-control-to-the-markup"></a>Přidání ovládacího prvku do značky

1. V **Průzkumník řešení** otevřete soubor úvodní stránky *. XAML* .

2. V podokně **XAML** přidejte následující deklaraci oboru názvů do elementu nejvyšší úrovně <xref:System.Windows.Controls.Grid> .

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. V podokně **XAML** přejděte k \<Grid> části.

    Oddíl obsahuje <xref:System.Windows.Controls.TabControl> element v <xref:System.Windows.Controls.Grid> elementu.

4. Přidejte \<TabControl> element obsahující a obsahující \<TabItem> odkaz na uživatelský ovládací prvek.

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    Nyní můžete otestovat ovládací prvek.

## <a name="test-a-manually-created-custom-start-page"></a>Testování ručně vytvořené vlastní úvodní stránky

1. Zkopírujte soubor XAML a všechny podpůrné textové soubory nebo soubory s označením do složky *%USERPROFILE%\My Documents\Visual Studio 2015 \ StartPages \\* .

2. Pokud Úvodní stránka odkazuje na jakékoli ovládací prvky nebo typy v sestaveních, která nejsou nainstalována aplikací Visual Studio, zkopírujte sestavení a vložte je do _instalační složky sady Visual Studio_**\Common7\IDE\PrivateAssemblies \\**.

3. Na příkazovém řádku sady Visual Studio zadejte **devenv/rootsuffix exp** a otevřete experimentální instanci sady Visual Studio.

4. V experimentální instanci přejdete na **Tools**  >  **Options**  >  **Environment**  >  **spouštěcí** stránku prostředí možnosti nástrojů a v rozevíracím seznamu **Přizpůsobit úvodní stránku** vyberete svůj soubor XAML.

5. V nabídce **zobrazení** klikněte na možnost **Úvodní stránka**.

    Měla by se zobrazit vaše vlastní úvodní stránka. Pokud chcete změnit nějaké soubory, musíte zavřít experimentální instanci, provést změny, zkopírovat změněné soubory a potom znovu otevřít experimentální instanci a zobrazit změny.

## <a name="see-also"></a>Viz také

- [Ovládací prvky kontejneru WPF](/previous-versions/bb675291(v=vs.110))
- [Návod: Přidání vlastního kódu XAML na úvodní stránku](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)