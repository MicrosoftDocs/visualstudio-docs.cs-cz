---
title: 'Návod: vytvoření sady SDK pomocí jazyka C++ | Microsoft Docs'
description: naučte se vytvořit nativní C++ sdk pro matematické knihovny, zabalit sadu sdk jako rozšíření Visual Studio a pak ji použít k vytvoření aplikace pomocí tohoto návodu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6a52322e575dc201a6bf1648af93d813828e0b17
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2021
ms.locfileid: "113223004"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Návod: vytvoření sady SDK pomocí jazyka C++
tento návod ukazuje, jak vytvořit nativní sadu sdk pro C++ math library, zabalit sadu sdk jako rozšíření Visual Studio (VSIX) a pak ji použít k vytvoření aplikace. Tento návod je rozdělen do těchto kroků:

- [vytvoření nativní knihovny a knihovny prostředí Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [Vytvoření projektu rozšíření NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [Vytvoření ukázkové aplikace, která používá knihovnu tříd](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Požadavky
 chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>vytvoření nativní knihovny a knihovny prostředí Windows Runtime

1. na panelu nabídek vyberte **soubor**  >  **nový**  >  **Project**.

2. v seznamu šablon rozbalte **Visual C++**  >  **Windows Universal** a pak vyberte šablonu **DLL (Windows univerzální aplikace)** . Do pole **název** zadejte `NativeMath` a pak klikněte na tlačítko **OK** .

3. Aktualizujte *NativeMath. h* tak, aby odpovídaly následujícímu kódu.

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h" id="Snippet1":::

4. Aktualizujte *NativeMath. cpp* tak, aby odpovídaly tomuto kódu:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp" id="Snippet2":::

5. v **Průzkumník řešení** otevřete místní nabídku pro **řešení "NativeMath"** a pak zvolte **přidat**  >  **nové Project**.

6. v seznamu šablon rozbalte položku **Visual C++** a potom vyberte šablonu **prostředí Windows Runtime součásti** . Do pole **název** zadejte `NativeMathWRT` a pak klikněte na tlačítko **OK** .

7. Aktualizujte *Class1. h* , aby odpovídal tomuto kódu:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h" id="Snippet3":::

8. Aktualizujte *Class1. cpp* tak, aby odpovídaly tomuto kódu:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp" id="Snippet4":::

9. Na řádku nabídek klikněte na **sestavit** sestavení  >  **řešení**.

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> Vytvoření projektu rozšíření NativeMathVSIX

1. v **Průzkumník řešení** otevřete místní nabídku pro **řešení "NativeMath"** a pak zvolte **přidat**  >  **nové Project**.

2. v seznamu šablon rozbalte rozšíření **Visual C#**  >  a pak vyberte **VSIX Project**. Do pole **název** zadejte **NativeMathVSIX** a poté klikněte na tlačítko **OK** .

3. V **Průzkumník řešení** otevřete místní nabídku pro **source. extension. vsixmanifest** a pak zvolte **Zobrazit kód**.

4. Pomocí následujícího kódu XML nahraďte existující kód XML.

    ```xml
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
      <Metadata>
        <Identity Id="NativeMathVSIX..c6b3cae1-e7e2-4e71-90f6-21017ea0dff7" Version="1.0" Language="en-US" Publisher="MyName" />
        <DisplayName>Native Math SDK</DisplayName>
        <Description>Native Math Library w/ Windows Runtime Additions</Description>
      </Metadata>
      <Installation Scope="Global" AllUsers="true">
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="NativeMathSDK" SdkVersion="1.0" />
      </Installation>
      <Dependencies>
      </Dependencies>
      <Assets>
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
      </Assets>
    </PackageManifest>
    ```

5. V **Průzkumník řešení** otevřete místní nabídku pro projekt **NativeMathVSIX** a pak zvolte možnost **Přidat**  >  **novou položku**.

6. V seznamu **položek Visual C#** rozbalte položku **data** a pak vyberte **soubor XML**. Do pole **název** zadejte `SDKManifest.xml` a pak klikněte na tlačítko **OK** .

7. Pomocí tohoto XML nahraďte obsah souboru:

    :::code language="xml" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml" id="Snippet5":::

8. V **Průzkumník řešení** v projektu **NativeMathVSIX** vytvořte tuto strukturu složek:

    ```xml
    \DesignTime
          \CommonConfiguration
                \Neutral
                      \Include
          \Debug
                \x86
    \Redist
          \Debug
                \x86
    \References
          \CommonConfiguration
                \Neutral
    ```

9. V **Průzkumník řešení** otevřete místní nabídku pro **řešení ' NativeMath '** a pak zvolte možnost **Otevřít složku v Průzkumníku souborů**.

10. V **Průzkumníku souborů** zkopírujte *$SolutionRoot $ \NativeMath\NativeMath.h* a potom v **Průzkumník řešení** v rámci projektu **NativeMathVSIX** ho vložte do složky *$SolutionRoot $ \NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include \\* .

     Zkopírujte *$SolutionRoot $ \Debug\NativeMath\NativeMath.lib* a vložte ji do složky *$SolutionRoot $ \NativeMathVSIX\DesignTime\Debug\x86 \\* .

     Zkopírujte *$SolutionRoot $\Debug\NativeMath\NativeMath.dll* a vložte ji do složky *$SolutionRoot $ \NativeMathVSIX\Redist\Debug\x86 \\* .

     Zkopírujte *$SolutionRoot $\Debug\NativeMathWRT\NativeMathWRT.dll* a vložte ji do složky *$SolutionRoot $ \NativeMathVSIX\Redist\Debug\x86* .
     Zkopírujte *$SolutionRoot $ \Debug\NativeMathWRT\NativeMathWRT.winmd* a vložte ji do složky *$SolutionRoot $ \NativeMathVSIX\References\CommonConfiguration\Neutral* .

     Zkopírujte *$SolutionRoot $ \Debug\NativeMathWRT\NativeMathWRT.pri* a vložte ji do složky *$SolutionRoot $ \NativeMathVSIX\References\CommonConfiguration\Neutral* .

11. Ve složce *$SolutionRoot $ \NativeMathVSIX\DesignTime\Debug\x86 \\* vytvořte textový soubor s názvem *NativeMathSDK. props* a vložte do něj následující obsah:
   
    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <NativeMathSDKPath>$(FrameworkSDKRoot)\..\..\UAP\v0.8.0.0\ExtensionSDKs\NativeMathSDK\1.0\</NativeMathSDKPath>
        <IncludePath>$(NativeMathSDKPath)DesignTime\CommonConfiguration\Neutral\Include;$(IncludePath)</IncludePath>
        <LibraryPath>$(NativeMathSDKPath)DesignTime\Debug\x86;$(LibraryPath)</LibraryPath>
      </PropertyGroup>
      <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
         <Link>
           <AdditionalDependencies>NativeMath.lib;%(AdditionalDependencies)</AdditionalDependencies>
         </Link>
      </ItemDefinitionGroup>
    </Project>
    ```

12. na panelu nabídek vyberte možnost **zobrazit**  >  **ostatní Windows**  >  **okno vlastností** (klávesnice: vyberte klávesu **F4** ).

13. V **Průzkumník řešení** vyberte soubor **NativeMathWRT. winmd** . V okně **vlastnosti** změňte vlastnost **Akce sestavení** na **obsah** a poté změňte vlastnost **Zahrnout v souboru VSIX** na **hodnotu true**.

     Tento postup opakujte pro soubor **NativeMath. h** .

     Tento postup opakujte pro soubor **NativeMathWRT. pri** .

     Tento postup opakujte pro soubor **NativeMath. lib** .

     Tento postup opakujte pro soubor **NativeMathSDK. props** .

14. V **Průzkumník řešení** vyberte soubor **NativeMath. h** . V okně **vlastnosti** změňte vlastnost **zahrnout do VSIX** na **hodnotu true**.

     Tento postup opakujte pro soubor **NativeMath.dll** .

     Tento postup opakujte pro soubor **NativeMathWRT.dll** .

     Tento postup opakujte pro soubor **SDKManifest.xml** .

15. Na řádku nabídek klikněte na **sestavit** sestavení  >  **řešení**.

16. V **Průzkumník řešení** otevřete místní nabídku pro projekt **NativeMathVSIX** a pak zvolte možnost **Otevřít složku v Průzkumníku souborů**.

17. V **Průzkumníku souborů** přejděte do složky *$SolutionRoot $ \NativeMathVSIX\bin\Debug* a spusťte instalaci *NativeMathVSIX. vsix* .

18. Klikněte na tlačítko **instalovat** , počkejte na dokončení instalace a pak otevřete Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Vytvoření ukázkové aplikace, která používá knihovnu tříd

1. na panelu nabídek vyberte **soubor**  >  **nový**  >  **Project**.

2. v seznamu šablon rozbalte **Visual C++**  >  **Windows Universal** a pak vyberte **prázdná aplikace**. Do pole **název** zadejte **NativeMathSDKSample** a poté klikněte na tlačítko **OK** .

3. V **Průzkumník řešení** otevřete místní nabídku pro projekt **NativeMathSDKSample** a pak zvolte možnost **Přidat**  >  **odkaz**.

4. v dialogovém okně **přidat odkaz** , v seznamu typů odkazů rozbalte položku **univerzální Windows** a pak vyberte možnost **rozšíření**. Nakonec zaškrtněte políčko **nativní sada matematických SDK** a pak klikněte na tlačítko **OK** .

5. Zobrazí vlastnosti projektu pro NativeMathSDKSample.

    Vlastnosti, které jste definovali v *NativeMathSDK. props* , byly aplikovány při přidání odkazu. Vlastnosti, které byly aplikovány, lze ověřit kontrolou vlastnosti **adresářů VC + +** **vlastností konfigurace** projektu.

6. V **Průzkumník řešení** otevřete **MainPage. XAML** a pak použijte následující XAML k nahrazení jeho obsahu:

    :::code language="xml" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml" id="Snippet1":::

7. Aktualizujte *MainPage. XAML. h* , aby odpovídaly tomuto kódu:

    :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h" id="Snippet2":::

8. Aktualizujte *MainPage. XAML. cpp* tak, aby odpovídaly tomuto kódu:

    :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp" id="Snippet3":::

9. Kliknutím na klávesu **F5** spusťte aplikaci.

10. V aplikaci zadejte dvě čísla, vyberte operaci a pak klikněte na **=** tlačítko.

     Zobrazí se správný výsledek.

    Tento návod ukázal, jak vytvořit a použít sadu SDK rozšíření pro volání do [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] knihovny a ne [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] knihovny.

## <a name="next-steps"></a>Další kroky

## <a name="see-also"></a>Viz také
- [Návod: vytvoření sady SDK pomocí jazyka C# nebo Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Vytvoření sady SDK (Software Development Kit)](../extensibility/creating-a-software-development-kit.md)
