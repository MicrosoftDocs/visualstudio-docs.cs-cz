---
title: Přidání uživatelského ovládacího prvku na úvodní stránku | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: b426cfbbfca2e301797644a1fc73f188054d0cfa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740125"
---
# <a name="add-user-control-to-the-start-page"></a>Přidání uživatelského ovládacího prvku na úvodní stránku

Tento návod ukazuje, jak přidat odkaz dll na vlastní úvodní stránku. Příklad přidá uživatelský ovládací prvek do řešení, vytvoří uživatelský ovládací prvek a potom odkazuje na sestavení ze souboru Start Page *.xaml.* Nová karta je hostitelem uživatelského ovládacího prvku, který funguje jako základní webový prohlížeč.

Stejný proces můžete použít k přidání libovolného sestavení, které lze volat ze souboru *Xaml.*

## <a name="add-a-wpf-user-control-to-the-solution"></a>Přidání uživatelského ovládacího prvku WPF do řešení

Nejprve přidejte uživatelský ovládací prvek Windows Presentation Foundation (WPF) do řešení Úvodní stránka.

1. Vytvořte úvodní stránku pomocí vytvoření v [aplikaci Vytvořit vlastní úvodní stránku](../extensibility/creating-a-custom-start-page.md).

2. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na řešení, klikněte na **přidat**a potom klikněte na **Nový projekt**.

3. V levém podokně dialogového okna **Nový projekt** rozbalte uzel **Visual Basic** nebo **Visual C#** a klepněte na příkaz **Windows**. V prostředním podokně vyberte **knihovnu uživatelských ovládacích prveků WPF**.

4. Pojmenujte `WebUserControl` ovládací prvek a klepněte na tlačítko **OK**.

## <a name="implement-the-user-control"></a>Implementace uživatelského ovládacího prvku

Chcete-li implementovat uživatelský ovládací prvek WPF, vytvořte uživatelské rozhraní (UI) v jazyce XAML a pak napište události na pozadí kódu v jazyce C# nebo jiném jazyce .NET.

### <a name="to-write-the-xaml-for-the-user-control"></a>Zápis xaml pro uživatelský ovládací prvek

1. Otevřete soubor XAML pro uživatelský ovládací prvek. V `<Grid>` elementu přidejte do ovládacího prvku následující definice řádků.

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. Do hlavního `<Grid>` prvku přidejte `<Grid>` následující nový prvek, který obsahuje textové pole pro zadávání webových adres a tlačítko pro nastavení nové adresy.

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

3. Přidejte následující rámeček do `<Grid>` elementu `<Grid>` nejvyšší úrovně těsně za element, který obsahuje tlačítko a textové pole.

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. Následující příklad ukazuje dokončené XAML pro uživatelský ovládací prvek.

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

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Zápis událostí na pozadí kódu pro uživatelský ovládací prvek

1. V návrháři XAML poklikejte na tlačítko **Nastavit adresu,** které jste přidali do ovládacího prvku.

    V editoru kódu se otevře *soubor UserControl1.cs.*

2. Vyplňte obslužnou rutinu události SetButton_Click následujícím způsobem.

    ```csharp
    private void SetButton_Click(object sender, RoutedEventArgs e)
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

    Tento kód nastaví webovou adresu, která je zadána do textového pole jako cíl pro webový prohlížeč. Pokud adresa není platná, kód vyvolá chybu.

3. Musíte také zpracovat WebFrame_Navigated událost:

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. Sestavte řešení.

## <a name="add-the-user-control-to-the-start-page"></a>Přidání uživatelského ovládacího prvku na úvodní stránku

Chcete-li tento ovládací prvek zpřístupnit projektu Úvodní stránka, přidejte v souboru projektu Úvodní stránka odkaz na novou knihovnu ovládacích prvku. Potom můžete přidat ovládací prvek do značky XAML úvodní stránky.

1. V **Průzkumníku řešení**klikněte v projektu Úvodní stránka pravým tlačítkem myši na **reference** a potom klikněte na **přidat odkaz**.

2. Na kartě **Projekty** vyberte **WebUserControl** a klepněte na tlačítko **OK**.

3. V nabídce **Sestavení** klikněte na **Sestavit řešení**.

    Vytváření řešení zpřístupňuje uživatelský ovládací prvek společnosti IntelliSense pro další soubory v řešení.

    Chcete-li přidat ovládací prvek do značky XAML úvodní stránky, přidejte odkaz na obor názvů do sestavení a potom ovládací prvek vložte na stránku.

### <a name="to-add-the-control-to-the-markup"></a>Přidání ovládacího prvku do značky

1. V **Průzkumníku řešení**otevřete soubor *Xaml* úvodní stránky.

2. V podokně **XAML** přidejte do elementu nejvyšší <xref:System.Windows.Controls.Grid> úrovně následující deklaraci oboru názvů.

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. V podokně **XAML** přejděte do \<části Grid>.

    Oddíl obsahuje <xref:System.Windows.Controls.TabControl> prvek v <xref:System.Windows.Controls.Grid> prvku.

4. Přidejte \<prvek TabControl> \<obsahující> TabItem, který obsahuje odkaz na uživatelský ovládací prvek.

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    Nyní můžete otestovat ovládací prvek.

## <a name="test-a-manually-created-custom-start-page"></a>Testování ručně vytvořené vlastní úvodní stránky

1. Zkopírujte soubor XAML a všechny podpůrné textové soubory nebo soubory značek do složky *%USERPROFILE%\My\\ Documents\Visual Studio 2015\StartPages.*

2. Pokud úvodní stránka odkazuje na ovládací prvky nebo typy v sestaveních, které nejsou nainstalovány aplikací Visual Studio, zkopírujte sestavení a vložte je do _instalační složky sady Visual Studio_**\Common7\IDE\PrivateAssemblies\\**.

3. Na příkazovém řádku sady Visual Studio zadejte **příkaz devenv /rootsuffix Exp,** chcete-li otevřít experimentální instanci sady Visual Studio.

4. V experimentální instanci přejděte na**úvodní** stránku**prostředí** >  **Tools** > **Options** > Environment a vyberte soubor XAML v rozevíracím seznamu Přizpůsobit úvodní **stránku.**

5. V nabídce **Zobrazení** klepněte na tlačítko **Úvodní stránka**.

    Měla by být zobrazena vlastní úvodní stránka. Pokud chcete změnit všechny soubory, musíte zavřít experimentální instanci, provést změny, zkopírovat a vložit změněné soubory a pak znovu otevřít experimentální instanci pro zobrazení změn.

## <a name="see-also"></a>Viz také

- [Ovládací prvky kontejneru WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
- [Návod: Přidání vlastního xaml na úvodní stránku](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
