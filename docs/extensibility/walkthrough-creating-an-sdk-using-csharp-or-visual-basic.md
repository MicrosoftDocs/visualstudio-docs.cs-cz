---
title: 'Návod: vytvoření sady SDK pomocí jazyka C# nebo Visual Basic | Microsoft Docs'
description: Přečtěte si, jak vytvořit jednoduchou sadu SDK pro matematické knihovny pomocí jazyka Visual C# a pak zabalit sadu SDK jako rozšíření sady Visual Studio pomocí tohoto návodu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 5b44566e4a8df323af6132128a8881b54c6f493f
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217291"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>Návod: vytvoření sady SDK pomocí jazyka C# nebo Visual Basic
V tomto návodu se dozvíte, jak vytvořit jednoduchou sadu SDK pro matematické knihovny pomocí jazyka Visual C# a pak zabalit sadu SDK jako rozšíření sady Visual Studio (VSIX). Dokončete následující postupy:

- [Vytvoření součásti prostředí Windows Runtime SimpleMath](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [Vytvoření projektu rozšíření SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [Vytvoření ukázkové aplikace, která používá knihovnu tříd](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>Požadavky
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a> Vytvoření součásti prostředí Windows Runtime SimpleMath

1. Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

2. V seznamu šablon rozbalte položku **Visual C#** nebo **Visual Basic**, zvolte uzel **Windows Store** a poté vyberte šablonu **součásti prostředí Windows Runtime** .

3. Do pole **název** zadejte **SimpleMath** a poté klikněte na tlačítko **OK** .

4. V **Průzkumník řešení** otevřete místní nabídku uzlu projektu **SimpleMath** a poté zvolte možnost **vlastnosti**.

5. Přejmenujte **Class1. cs** na **aritmetické. cs** a aktualizujte je tak, aby odpovídaly následujícímu kódu:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs" id="Snippet3":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb" id="Snippet3":::

6. V **Průzkumník řešení** otevřete místní nabídku uzlu **řešení ' SimpleMath '** a pak zvolte možnost **Configuration Manager**.

    Otevře se dialogové okno **Configuration Manager** .

7. V seznamu **aktivní konfigurace řešení** vyberte možnost **verze**.

8. Ve sloupci **Konfigurace** ověřte, že je na řádku **SimpleMath** nastavená **verze**, a pak kliknutím na tlačítko **Zavřít** tuto změnu potvrďte.

   > [!IMPORTANT]
   > Sada SDK pro komponentu SimpleMath zahrnuje pouze jednu konfiguraci. Tato konfigurace musí být sestavení pro vydání, nebo aplikace, které tuto komponentu používají, nebudou dodávat certifikaci pro [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] .

9. V **Průzkumník řešení** otevřete místní nabídku uzlu projektu **SimpleMath** a pak zvolte možnost **sestavit**.

## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a> Vytvoření projektu rozšíření SimpleMathVSIX

1. V místní nabídce uzlu **řešení ' SimpleMath '** vyberte možnost **Přidat**  >  **Nový projekt**.

2. V seznamu šablon rozbalte položku **Visual C#** nebo **Visual Basic**, zvolte uzel **rozšiřitelnost** a pak zvolte šablonu **projektu VSIX** .

3. Do pole **název** zadejte **SimpleMathVSIX** a poté klikněte na tlačítko **OK** .

4. V **Průzkumník řešení** vyberte položku **zdroj. extension. vsixmanifest** .

5. Na panelu nabídek vyberte možnost **Zobrazit**  >  **kód**.

6. Existující XML nahraďte následujícím kódem XML:

   ```xml
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Metadata>
       <Identity Id="SimpleMath" Version="1.0" Language="en-US" Publisher="[YourName]" />
       <DisplayName>SimpleMath Library</DisplayName>
       <Description xml:space="preserve">Basic arithmetic operations in a WinRT-compatible library. Implemented in C#.</Description>
     </Metadata>
     <Installation Scope="Global" AllUsers="true">
       <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />
     </Installation>
     <Prerequisites>
       <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[14.0,16.0]" />
     </Prerequisites>
     <Dependencies>
       <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />
     </Dependencies>
     <Assets>
       <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
     </Assets>
   </PackageManifest>
   ```

7. V **Průzkumník řešení** vyberte projekt **SimpleMathVSIX** .

8. Na řádku nabídek klikněte na položku **projekt**  >  **Přidat novou položku**.

9. V seznamu **běžných položek** rozbalte položku **data** a pak zvolte možnost **soubor XML**.

10. Do pole **název** zadejte `SDKManifest.xml` a pak klikněte na tlačítko **Přidat** .

11. V **Průzkumník řešení** otevřete místní nabídku pro `SDKManifest.xml` , zvolte **vlastnosti** a pak změňte hodnotu vlastnosti **zahrnout do VSIX** na **true**.

12. Obsah souboru nahraďte následujícím kódem XML:

    **C#**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

    **Visual Basic**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (VB)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

13. V **Průzkumník řešení** otevřete místní nabídku pro projekt **SimpleMathVSIX** , zvolte možnost **Přidat** a pak zvolte možnost **Nová složka**.

14. Přejmenujte složku na `references` .

15. Otevřete místní nabídku složky **odkazy** , zvolte možnost **Přidat** a pak zvolte možnost **Nová složka**.

16. Přejmenujte podsložku na `commonconfiguration` , vytvořte v ní podsložku a pojmenujte ji `neutral` .

17. Opakujte předchozí čtyři kroky, čímž pojmenujete první složku na `redist` .

     Projekt teď obsahuje následující strukturu složek:

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. V **Průzkumník řešení** otevřete místní nabídku pro projekt **SimpleMath** a pak zvolte možnost **Otevřít složku v Průzkumníku souborů**.

19. V **Průzkumníku souborů** přejděte do složky *bin\Release* , otevřete místní nabídku pro soubor **SimpleMath. winmd** a pak zvolte **Kopírovat**.

20. V **Průzkumník řešení** vložte soubor do složky *References\commonconfiguration\neutral* v projektu **SimpleMathVSIX** .

21. Opakujte předchozí krok a vložte soubor **SimpleMath. pri** do složky *Redist\commonconfiguration\neutral* v projektu **SimpleMathVSIX** .

22. V **Průzkumník řešení** vyberte **SimpleMath. winmd**.

23. Na panelu nabídek vyberte možnost **Zobrazit**  >  **vlastnosti** (klávesnice: vyberte klávesu **F4** ).

24. V okně **vlastnosti** změňte vlastnost **Akce sestavení** na **obsah** a poté změňte vlastnost **Zahrnout v souboru VSIX** na **hodnotu true**.

25. V **Průzkumník řešení** opakujte tento postup pro **SimpleMath. pri**.

26. V **Průzkumník řešení** vyberte projekt **SimpleMathVSIX** .

27. Na panelu nabídek vyberte sestavení sestavení   >  **SimpleMathVSIX**.

28. V **Průzkumník řešení** otevřete místní nabídku pro projekt **SimpleMathVSIX** a pak zvolte možnost **Otevřít složku v Průzkumníku souborů**.

29. V **Průzkumníku souborů** přejděte do složky *\bin\Release* a potom spusťte *SimpleMathVSIX. vsix* a nainstalujte ji.

30. Klikněte na tlačítko **instalovat** , počkejte na dokončení instalace a pak restartujte aplikaci Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Vytvoření ukázkové aplikace, která používá knihovnu tříd

1. Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

2. V seznamu šablon rozbalte položku **Visual C#** nebo **Visual Basic** a pak vyberte uzel **Windows Store** .

3. Zvolte šablonu **prázdná aplikace** , pojmenujte projekt **ArithmeticUI** a pak klikněte na tlačítko **OK** .

4. V **Průzkumník řešení** otevřete místní nabídku pro projekt **ArithmeticUI** a pak zvolte možnost **Přidat**  >  **odkaz**.

5. V seznamu typů odkazů rozbalte **okna** a pak zvolte **rozšíření**.

6. V podokně podrobností vyberte rozšíření pro **matematické knihovny WinRT** .

    Zobrazí se další informace o sadě SDK. Můžete zvolit odkaz **Další informace** pro otevření https://msdn.microsoft.com/ , jak je uvedeno v souboru SDKManifest.xml výše v tomto návodu.

7. V dialogovém okně **Správce odkazů** vyberte zaškrtávací políčko **WinRT Math Library** a pak klikněte na tlačítko **OK** .

8. Na panelu nabídek vyberte možnost **Zobrazit**  >  **Prohlížeč objektů**.

9. V seznamu **Procházet** vyberte **jednoduché matematické**.

     Teď můžete prozkoumat, co je v sadě SDK.

10. V **Průzkumník řešení** otevřete **MainPage. XAML** a nahraďte jeho obsah následujícím XAML:

    **C#**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

    **Visual Basic**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

11. Aktualizujte **MainPage. XAML. cs** tak, aby odpovídaly následujícímu kódu:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Windows.Foundation;
using Windows.Foundation.Collections;
using Windows.UI.Xaml;
using Windows.UI.Xaml.Controls;
using Windows.UI.Xaml.Controls.Primitives;
using Windows.UI.Xaml.Data;
using Windows.UI.Xaml.Input;
using Windows.UI.Xaml.Media;
using Windows.UI.Xaml.Navigation;

// The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238

namespace ArithmeticUI
{
    /// <summary>
    /// An empty page that can be used on its own or navigated to within a Frame.
    /// </summary>
    public sealed partial class MainPage : Page
    {
        public static string operation = null;

        public MainPage()
        {
            this.InitializeComponent();
        }

        /// <summary>
        /// Invoked when this page is about to be displayed in a Frame.
        /// </summary>
        /// <param name="e">Event data that describes how this page was reached.  The Parameter
        /// property is typically used to configure the page.</param>
        protected override void OnNavigatedTo(NavigationEventArgs e)
        {
        }

        /// <summary>
        /// Sets the operator chosen by the user
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void OnOperatorClick(object sender, RoutedEventArgs e)
        {
            operation = (sender as Button).Content.ToString();
        }

        /// <summary>
        /// Calls the SimpleMath SDK to do simple arithmetic
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void OnResultsClick(object sender, RoutedEventArgs e)
        {
            try
            {
                float firstNumber = float.Parse(this._firstNumber.Text);
                float secondNumber = float.Parse(this._secondNumber.Text);

                SimpleMath.Arithmetic math = new SimpleMath.Arithmetic();

                switch (operation)
                {
                    case "+":
                        this._result.Text = (math.add(firstNumber, secondNumber)).ToString();
                        break;
                    case "-":
                        this._result.Text = (math.subtract(firstNumber, secondNumber)).ToString();
                        break;
                    case "*":
                        this._result.Text = (math.multiply(firstNumber, secondNumber)).ToString();
                        break;
                    case "/":
                        this._result.Text = (math.divide(firstNumber, secondNumber)).ToString();
                        break;
                    default:
                        this._result.Text = "Choose operator";
                        break;
                }
            }
            catch
            {
                this._result.Text = "Enter valid #";
            }
        }
    }
}
```

```vb
' The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238

''' <summary>
''' An empty page that can be used on its own or navigated to within a Frame.
''' </summary>
Public NotInheritable Class MainPage
    Inherits Page

    ''' <summary>
    ''' Invoked when this page is about to be displayed in a Frame.
    ''' </summary>
    ''' <param name="e">Event data that describes how this page was reached.  The Parameter
    ''' property is typically used to configure the page.</param>
    Protected Overrides Sub OnNavigatedTo(e As Navigation.NavigationEventArgs)
    
    End Sub

    Public Shared operation As String = Nothing

    ''' <summary>
    ''' Sets the operator chosen by the user
    ''' </summary>
    ''' <param name="sender"></param>
    ''' <param name="e"></param>
    Private Sub OnOperatorClick(ByVal sender As Object, ByVal e As RoutedEventArgs)
        operation = If(TypeOf sender Is Button, CType(sender, Button), Nothing).Content.ToString()
    End Sub


    ''' <summary>
    ''' Calls the SimpleMath SDK to do simple arithmetic
    ''' </summary>
    ''' <param name="sender"></param>
    ''' <param name="e"></param>
    Private Sub OnResultsClick(ByVal sender As Object, ByVal e As RoutedEventArgs)

        Try

            Dim firstNumber As Single = Single.Parse(Me._firstNumber.Text)
            Dim secondNumber As Single = Single.Parse(Me._secondNumber.Text)

            Dim math As New SimpleMath.Arithmetic()

            Select Case (operation)

                Case "+"
                    Me._result.Text = (math.Add(firstNumber, secondNumber)).ToString()

                Case "-"
                    Me._result.Text = (math.Subtract(firstNumber, secondNumber)).ToString()
                Case "*"
                    Me._result.Text = (math.Multiply(firstNumber, secondNumber)).ToString()
                Case "/"
                    Me._result.Text = (math.Divide(firstNumber, secondNumber)).ToString()
                Case Else
                    Me._result.Text = "Choose operator"

            End Select

        Catch
            Me._result.Text = "Enter valid #"
        End Try
    End Sub
End Class
```

12. Kliknutím na klávesu **F5** spusťte aplikaci.

13. V aplikaci zadejte dvě čísla, zvolte operaci a pak klikněte na **=** tlačítko.

     Zobrazí se správný výsledek.

    Úspěšně jste vytvořili a použili sadu SDK rozšíření.

## <a name="see-also"></a>Viz také
- [Návod: vytvoření sady SDK pomocí jazyka C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Návod: vytvoření sady SDK pomocí JavaScriptu](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [Vytvoření sady SDK (Software Development Kit)](../extensibility/creating-a-software-development-kit.md)
