---
title: Přidání uživatelského ovládacího prvku na úvodní stránku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 96b280221ba7efdefd3023f015bd4075b8c03aaa
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910485"
---
# <a name="add-user-control-to-the-start-page"></a>Přidat uživatelský ovládací prvek na úvodní stránku
Tento návod ukazuje, jak přidat knihovnu DLL odkaz na vlastní úvodní stránky. V příkladu přidá uživatelský ovládací prvek do řešení, vytvoří uživatelský ovládací prvek a potom odkazuje na sestavení z úvodní stránky *.xaml* souboru. Na nové kartě hostuje uživatelský ovládací prvek, který funguje jako základní webový prohlížeč.  
  
 Stejný postup můžete přidat libovolné sestavení, kterou lze volat z *.xaml* souboru.  
  
## <a name="add-a-wpf-user-control-to-the-solution"></a>Do řešení přidat uživatelský ovládací prvek WPF  
 Nejprve přidejte uživatelský ovládací prvek Windows Presentation Foundation (WPF) úvodní stránka řešení.  
  
1.  Vytvořit úvodní stránka s použitím, který jsme vytvořili v [vytvořit vlastní úvodní stránky](../extensibility/creating-a-custom-start-page.md).  
  
2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na řešení, klikněte na tlačítko **přidat**a potom klikněte na tlačítko **nový projekt**.  
  
3.  V levém podokně **nový projekt** dialogového okna rozbalte buď **jazyka Visual Basic** nebo **Visual C#** uzel a klikněte na tlačítko **Windows**. V prostředním podokně vyberte **Knihovna uživatelských ovládacích prvků WPF**.  
  
4.  Pojmenujte ovládací prvek `WebUserControl` a potom klikněte na tlačítko **OK**.  
  
## <a name="implement-the-user-control"></a>Implementace uživatelského ovládacího prvku  
 K implementaci uživatelského ovládacího prvku WPF, vytvářet uživatelské rozhraní (UI) v XAML a pak napište použití modelu code-behind události v jazyce C# nebo jiný jazyk .NET.  
  
### <a name="to-write-the-xaml-for-the-user-control"></a>Zápis XAML pro uživatelský ovládací prvek  
  
1.  Otevřete soubor XAML pro uživatelský ovládací prvek. V `<Grid>` prvku, přidejte následující definice řádku do ovládacího prvku.  
  
    ```vb  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition Height="*" />  
    </Grid.RowDefinitions>  
  
    ```  
  
2.  V hlavním `<Grid>` prvku, přidejte tento nový `<Grid>` element, který obsahuje textové pole pro zadání webové adresy a tlačítko pro nastavení novou adresu.  
  
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
  
3.  Přidejte následující rámce na nejvyšší úrovni `<Grid>` element hned za `<Grid>` element, který obsahuje tlačítko a textové pole.  
  
    ```vb  
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
    ```  
  
4.  Následující příklad ukazuje dokončené XAML pro uživatelský ovládací prvek.  
  
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
  
### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Zapsat události použití modelu code-behind uživatelského ovládacího prvku  
  
1.  V Návrháři XAML, dvakrát klikněte **nastavit adresu** přidání do ovládacího prvku tlačítka.  
  
     *UserControl1.cs* soubor se otevře v editoru kódu.  
  
2.  Obslužná rutina události SetButton_Click vyplňte následujícím způsobem.  
  
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
  
     Tento kód nastaví webovou adresu, který je zadán v textovém poli jako cíl pro webový prohlížeč. Pokud adresa není platná, kód vyvolá chybu.  
  
3.  Musíte také zpracovávat události WebFrame_Navigated:  
  
    ```csharp  
    private void WebFrame_Navigated(object sender, EventArgs e)  
    { }  
    ```  
  
4.  Sestavte řešení.  
  
## <a name="add-the-user-control-to-the-start-page"></a>Přidat uživatelský ovládací prvek na úvodní stránku  
 Do tohoto ovládacího prvku zpřístupnit na úvodní stránce projektu v souboru projektu úvodní stránku, přidejte odkaz na nové knihovny ovládacích prvků. Potom můžete přidat ovládací prvek kód spuštění stránky XAML.  
  
1. V **Průzkumníka řešení**, v úvodní stránce projektu klikněte pravým tlačítkem na **odkazy** a potom klikněte na tlačítko **přidat odkaz**.  
  
2. Na **projekty** kartu, vyberte možnost **WebUserControl** a potom klikněte na tlačítko **OK**.  
  
3. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
    Sestavování řešení zpřístupní uživatelského ovládacího prvku IntelliSense pro další soubory v řešení.  
  
   Přidání ovládacího prvku kód spuštění stránky XAML, přidejte obor názvů odkaz na sestavení a pak umístit ovládací prvek na stránce.  
  
### <a name="to-add-the-control-to-the-markup"></a>Chcete-li přidat ovládací prvek značky  
  
1. V **Průzkumníka řešení**, otevřete úvodní stránka *.xaml* souboru.  
  
2. V **XAML** podokno, přidejte následující deklarace oboru názvů na nejvyšší úrovni <xref:System.Windows.Controls.Grid> elementu.  
  
   ```xml  
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
   ```  
  
3. V **XAML** podokno, posuňte se \<mřížky > oddílu.  
  
    Oddíl obsahuje <xref:System.Windows.Controls.TabControl> prvek <xref:System.Windows.Controls.Grid> elementu.  
  
4. Přidat \<TabControl > element obsahující \<TabItem >, která obsahuje odkaz na uživatelský ovládací prvek.  
  
   ```xml  
  
   <TabItem Header="Web" Height="Auto">  
       <vsc:UserControl1 />  
   </TabItem>  
  
   ```  
  
   Nyní můžete otestovat ovládacího prvku.  
  
## <a name="test-a-manually-created-custom-start-page"></a>Testování ručně vytvořené vlastní úvodní stránky  
  
1.  Zkopírujte soubor XAML a všechny podpůrné textové soubory nebo značky soubory do *%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\*  složky.  
  
2.  Pokud úvodní stránky odkazuje na všechny ovládací prvky nebo typy v sestavení, které nejsou nainstalované Visual Studio, zkopírujte sestavení a vložte je do _instalační složky sady Visual Studio_**\Common7\IDE\ PrivateAssemblies\\**.  
  
3.  Na příkazovém řádku aplikace Visual Studio, zadejte **devenv /rootsuffix Exp** otevřete experimentální instanci sady Visual Studio.  
  
4.  V experimentální instanci aplikace, přejděte **nástroje** > **možnosti** > **prostředí** > **spuštění** stránky a vyberte soubor XAML z **přizpůsobit úvodní stránku** rozevíracího seznamu.  
  
5.  Na **zobrazení** nabídky, klikněte na tlačítko **úvodní stránka**.  
  
     Vlastní úvodní stránku má být zobrazena. Pokud chcete změnit všechny soubory, můžete musí Ukončete experimentální instanci, proveďte požadované změny, zkopírujte a vložte změněných souborů a znovu otevřete experimentální instanci a zobrazte změny.  
  
## <a name="see-also"></a>Viz také:  
 [Kontejner ovládacích prvků WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)   
 [Návod: Přidání vlastních XAML na úvodní stránku](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)