---
title: 'Návod: Vytvoření sady SDK pomocí jazyka C# nebo jazyka Visual Basic | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 16eb20452601a65c498ff112ea996f2d93559940
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697560"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>Návod: Vytvoření sady SDK pomocí jazyka C# nebo jazyka Visual Basic
V tomto návodu se dozvíte, jak vytvořit jednoduchou sadku Math Library SDK pomocí sady Visual C# a potom zabalit sadu SDK jako rozšíření sady Visual Studio (VSIX). Budete dokončit následující postupy:

- [Vytvoření komponenty SimpleMath Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [Vytvoření projektu rozšíření SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [Vytvoření ukázkové aplikace, která používá knihovnu tříd](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>Požadavky
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sady Visual Studio SDK. Další informace naleznete v [tématu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a>Vytvoření komponenty SimpleMath Windows Runtime

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**.

2. V seznamu šablon rozbalte **visual c#** nebo **visual basic**, zvolte uzel Windows **Store** a pak zvolte šablonu **komponenty Windows Runtime.**

3. Do pole **Název** zadejte **SimpleMath**a pak zvolte tlačítko **OK.**

4. V **Průzkumníku řešení**otevřete místní nabídku pro uzel projektu **SimpleMath** a pak zvolte **Vlastnosti**.

5. Přejmenujte **Class1.cs** na **Arithmetic.cs** a aktualizujte tak, aby odpovídala následujícímu kódu:

    [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
    [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]

6. V **Průzkumníku řešení**otevřete místní nabídku uzlu **Řešení SimpleMath** a pak zvolte **Configuration Manager**.

    Otevře se dialogové okno **Správce konfigurace.**

7. V seznamu **Konfigurace aktivního řešení** zvolte **Uvolnit**.

8. Ve **sloupci Konfigurace** ověřte, zda je řádek **SimpleMath** nastavený na **Release**, a pak zvolte tlačítko **Zavřít,** chcete-li změnu přijmout.

   > [!IMPORTANT]
   > Sada SDK pro komponentu SimpleMath obsahuje pouze jednu konfiguraci. Tato konfigurace musí být sestavení verze nebo aplikace, které používají [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]komponentu neprojde certifikací pro .

9. V **Průzkumníku řešení**otevřete místní nabídku pro uzel projektu **SimpleMath** a pak zvolte **Build**.

## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a>Vytvoření projektu rozšíření SimpleMathVSIX

1. V místní nabídce uzlu **Řešení SimpleMath** zvolte **Přidat** > **nový projekt**.

2. V seznamu šablon rozbalte **Visual C#** nebo **Visual Basic**, zvolte uzel **Rozšiřitelnost** a pak zvolte šablonu **Projektu VSIX.**

3. Do pole **Název** zadejte **SimpleMathVSIX**a pak zvolte tlačítko **OK.**

4. V **Průzkumníku řešení**zvolte položku **source.extension.vsixmanifest.**

5. Na řádku nabídek zvolte **Zobrazit** > **kód**.

6. Nahraďte existující xml následujícím xml:

     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]

7. V **Průzkumníku řešení**zvolte projekt **SimpleMathVSIX.**

8. Na řádku nabídek zvolte Přidat**novou položku** **projektu** > .

9. V seznamu **běžných položek**rozbalte **položku Data**a pak zvolte **Soubor XML**.

10. Do pole **Název** `SDKManifest.xml`zadejte a pak zvolte tlačítko **Přidat.**

11. V **Průzkumníku řešení**otevřete `SDKManifest.xml`místní nabídku pro , zvolte **Vlastnosti**a změňte hodnotu **vlastnosti Zahrnout do vSIX** na **Hodnotu True**.

12. Nahraďte obsah souboru následujícím xml:

    **C #**

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

13. V **Průzkumníku řešení**otevřete místní nabídku pro projekt **SimpleMathVSIX,** zvolte **Přidat**a pak zvolte **Nová složka**.

14. Přejmenujte složku `references`na .

15. Otevřete místní nabídku pro složku **Reference,** zvolte **Přidat**a pak zvolte **Nová složka**.

16. Podsložku přejmenujte `commonconfiguration`na , vytvořte v ní podsložku a pojmenujte `neutral`ji .

17. Opakujte předchozí čtyři kroky, tentokrát přejmenování `redist`první složky na .

     Projekt nyní obsahuje následující strukturu složek:

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. V **Průzkumníku řešení**otevřete místní nabídku pro projekt **SimpleMath** a pak **v Průzkumníkovi souborů**zvolte Otevřít složku .

19. V **Průzkumníkovi souborů**přejděte do složky *bin\Release,* otevřete místní nabídku souboru **SimpleMath.winmd** a zvolte **Kopírovat**.

20. V **Průzkumníku řešení**vložte soubor do *složky references\commonconfiguration\neutral* v projektu **SimpleMathVSIX.**

21. Opakujte předchozí krok a vnesete soubor **SimpleMath.pri** do složky *redist\commonconfiguration\neutral* v projektu **SimpleMathVSIX.**

22. V **Průzkumníku řešení**zvolte **SimpleMath.winmd**.

23. Na řádku nabídek zvolte **Zobrazit** > **vlastnosti** (Klávesnice: Zvolte klávesu **F4).**

24. V okně **Vlastnosti** změňte vlastnost **Akce sestavení** na **obsah**a potom změňte vlastnost Zahrnout **do vSIX** na **Hodnotu True**.

25. V **Průzkumníku řešení**opakujte tento postup pro **soubor SimpleMath.pri**.

26. V **Průzkumníku řešení**zvolte projekt **SimpleMathVSIX.**

27. Na řádku nabídek zvolte **Build** > **Build SimpleMathVSIX**.

28. V **Průzkumníku řešení**otevřete místní nabídku pro projekt **SimpleMathVSIX** a pak zvolte **Otevřít složku v Průzkumníkovi souborů**.

29. V **Průzkumníkovi souborů**přejděte do složky *\bin\Release* a spusťte soubor *SimpleMathVSIX.vsix* a nainstalujte ji.

30. Zvolte tlačítko **Instalovat,** počkejte na dokončení instalace a restartujte visual studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>Vytvoření ukázkové aplikace, která používá knihovnu tříd

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**.

2. V seznamu šablon rozbalte **Visual C#** nebo **Visual Basic**a pak zvolte uzel Windows **Store.**

3. Zvolte šablonu **Blank App,** pojmenujte projekt **AritmeticUI**a pak zvolte tlačítko **OK.**

4. V **Průzkumníku řešení**otevřete místní nabídku pro projekt **AritmeticUI** a pak zvolte **Přidat** > **odkaz**.

5. V seznamu typů odkazů rozbalte **windows**a pak zvolte **Rozšíření**.

6. V podokně podrobností zvolte rozšíření **WinRT Math Library.**

    Zobrazí se další informace o sdk. Můžete zvolit odkaz **Další informace,** který chcete otevřít https://msdn.microsoft.com/, jak jste zadali v souboru SDKManifest.xml dříve v tomto návodu.

7. V dialogovém okně **Správce odkazů** zaškrtněte políčko **WinRT Math Library** a pak zvolte tlačítko **OK.**

8. Na řádku nabídek zvolte **Zobrazit** > **prohlížeč objektů**.

9. V seznamu **Procházet** zvolte **Jednoduchá matematika**.

     Nyní můžete prozkoumat, co je v sdk.

10. V **Průzkumníku řešení**otevřete **soubor MainPage.xaml**a nahraďte jeho obsah následujícím jazykem XAML:

    **C #**

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

11. Aktualizujte **MainPage.xaml.cs** tak, aby odpovídaly následujícímu kódu:

     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]

12. Zvolte klávesu **F5** pro spuštění aplikace.

13. V aplikaci zadejte libovolná dvě čísla, zvolte operaci a pak zvolte **=** tlačítko.

     Zobrazí se správný výsledek.

    Úspěšně jste vytvořili a použili sadu SDK rozšíření.

## <a name="see-also"></a>Viz také
- [Návod: Vytvoření sady SDK pomocí jazyka C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Návod: Vytvoření sady SDK pomocí JavaScriptu](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [Vytvoření sady SDK (Software Development Kit)](../extensibility/creating-a-software-development-kit.md)
