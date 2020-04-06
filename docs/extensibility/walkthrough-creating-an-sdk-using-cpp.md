---
title: 'Návod: Vytvoření sady SDK pomocí jazyka C++ | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65643e65490eacb79eea4d76aa49ff10d6cccf66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697636"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Návod: Vytvoření sady SDK pomocí jazyka C++
Tento návod ukazuje, jak vytvořit nativní matematickou knihovnu C++, zabalit sdk jako rozšíření Visual Studio Extension (VSIX) a pak ji použít k vytvoření aplikace. Návod je rozdělen do následujících kroků:

- [Vytvoření nativních knihoven a knihoven prostředí Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [Vytvoření projektu rozšíření NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [Vytvoření ukázkové aplikace, která používá knihovnu tříd](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Požadavky
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sady Visual Studio SDK. Další informace naleznete v [tématu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>Vytvoření nativních knihoven a knihoven prostředí Windows Runtime

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**.

2. V seznamu šablon rozbalte **visual c++** > **Windows Universal**a vyberte šablonu **DLL (Windows Universal apps).** Do pole **Název** `NativeMath`zadejte a pak zvolte tlačítko **OK.**

3. Aktualizujte *nativemath.h* tak, aby odpovídala následující kód.

     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]

4. Aktualizujte *nativemath.cpp* tak, aby odpovídala tomuto kódu:

     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]

5. V **Průzkumníku řešení**otevřete místní nabídku **řešení NativeMath**a pak zvolte **Přidat** > **nový projekt**.

6. V seznamu šablon rozbalte **visual c++** a vyberte šablonu **komponenty Prostředí Windows Runtime.** Do pole **Název** `NativeMathWRT`zadejte a pak zvolte tlačítko **OK.**

7. Aktualizujte *class1.h* tak, aby odpovídala tomuto kódu:

     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]

8. Aktualizujte *class1.cpp* tak, aby odpovídala tomuto kódu:

     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]

9. Na řádku nabídek zvolte **Build** > **Build Build Solution**.

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a>Vytvoření projektu rozšíření NativeMathVSIX

1. V **Průzkumníku řešení**otevřete místní nabídku **řešení NativeMath**a pak zvolte **Přidat** > **nový projekt**.

2. V seznamu šablon rozbalte položku**Rozšiřitelnost** **jazyka Visual C#** > a vyberte **možnost Projekt VSIX**. Do pole **Název** zadejte **NativeMathVSIX**a pak zvolte tlačítko **OK.**

3. V **Průzkumníku řešení**otevřete místní nabídku pro **source.extension.vsixmanifest**a pak zvolte **Zobrazit kód**.

4. K nahrazení existujícího xml použijte následující kód XML.

    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5. V **Průzkumníku řešení**otevřete místní nabídku pro projekt **NativeMathVSIX** a pak zvolte **Přidat** > **novou položku**.

6. V seznamu **položek visual c#** rozbalte **položku Data**a vyberte **soubor XML**. Do pole **Název** `SDKManifest.xml`zadejte a pak zvolte tlačítko **OK.**

7. Tento kód XML slouží k nahrazení obsahu souboru:

     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]

8. V **Průzkumníku řešení**v rámci projektu **NativeMathVSIX** vytvořte tuto strukturu složek:

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

9. V **Průzkumníku řešení**otevřete místní nabídku **řešení NativeMath**a pak **v Průzkumníkovi souborů**zvolte Otevřít složku .

10. V **Průzkumníkovi souborů**zkopírujte *$SolutionRoot$\NativeMath\NativeMath.h*a potom v **Průzkumníku řešení**v rámci projektu **NativeMathVSIX** jej vložte do složky *\\ $SolutionRoot$\NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include.*

     Zkopírujte *$SolutionRoot$\Debug\NativeMath\NativeMath.lib*a vložte jej do složky *\\ $SolutionRoot$\NativeMathVSIX\DesignTime\Debug\x86.*

     Zkopírujte *soubor $SolutionRoot$\Debug\NativeMath\NativeMath.dll* a vložte jej do složky *$SolutionRoot$\NativeMathVSIX\Redist\Debug\x86.\\ *

     Zkopírujte *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll* a vložte ji do složky *$SolutionRoot$\NativeMathVSIX\Redist\Debug\x86.*
     Zkopírujte *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd* a vložte jej do složky *$SolutionRoot$\NativeMathVSIX\References\CommonConfiguration\Neutral.*

     Zkopírujte *soubor $SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri* a vložte jej do složky *$SolutionRoot$\NativeMathVSIX\References\CommonConfiguration\Neutral.*

11. Ve složce *$SolutionRoot$\NativeMathVSIX\DesignTime\Debug\x86\\ * vytvořte textový soubor s názvem *NativeMathSDK.props*a vložte do ní následující obsah:

    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]

12. Na řádku nabídek zvolte **Zobrazit** > další**okno vlastností systému** **Windows** > (Klávesnice: Zvolte klávesu **F4).**

13. V **Průzkumníku řešení**vyberte soubor **NativeMathWRT.winmd.** V okně **Vlastnosti** změňte vlastnost **Akce sestavení** na **obsah**a potom změňte vlastnost Zahrnout **do vSIX** na **Hodnotu True**.

     Tento postup opakujte pro soubor **NativeMath.h.**

     Tento postup opakujte pro soubor **NativeMathWRT.pri.**

     Tento postup opakujte pro soubor **NativeMath.Lib.**

     Tento postup opakujte pro soubor **NativeMathSDK.props.**

14. V **Průzkumníku řešení**vyberte soubor **NativeMath.h.** V okně **Vlastnosti** změňte vlastnost **Zahrnout do vSIX** na **True**.

     Tento postup opakujte pro soubor **NativeMath.dll.**

     Tento postup opakujte pro soubor **NativeMathWRT.dll.**

     Tento postup opakujte pro soubor **SDKManifest.xml.**

15. Na řádku nabídek zvolte **Build** > **Build Build Solution**.

16. V **Průzkumníku řešení**otevřete místní nabídku pro projekt **NativeMathVSIX** a pak zvolte **Otevřít složku v Průzkumníkovi souborů**.

17. V **Průzkumníkovi souborů**přejděte do složky *$SolutionRoot$\NativeMathVSIX\bin\Debug* a spusťte program *NativeMathVSIX.vsix* a začínejte s instalací.

18. Zvolte tlačítko **Instalovat,** počkejte na dokončení instalace a otevřete Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>Vytvoření ukázkové aplikace, která používá knihovnu tříd

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**.

2. V seznamu šablon rozbalte **Visual C++** > **Windows Universal** a pak vyberte **Prázdná aplikace**. Do pole **Název** zadejte **NativeMathSDKSample**a pak zvolte tlačítko **OK.**

3. V **Průzkumníku řešení**otevřete místní nabídku projektu **NativeMathSDKSample** a pak zvolte **Přidat** > **odkaz**.

4. V dialogovém okně **Přidat odkaz** rozbalte v seznamu typů odkazů **položku Univerzální systém Windows**a vyberte **položku Rozšíření**. Nakonec zaškrtněte políčko **Nativní matematický sdk** a pak zvolte tlačítko **OK.**

5. Zobrazení vlastností projektu pro nativeMathSDKSample.

    Vlastnosti, které jste definovali v *nativemathsdk.props* byly použity při přidání odkazu. Vlastnosti můžete ověřit kontrolou **vlastností Adresářů VC++** **vlastnosti projektu vlastnosti konfigurace**.

6. V **Průzkumníku řešení**otevřete **soubor MainPage.xaml**a potom jeho obsah nahraďte pomocí následujícího xaml:

    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]

7. Aktualizujte *soubor Mainpage.xaml.h* tak, aby odpovídal tomuto kódu:

    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]

8. Aktualizujte *soubor MainPage.xaml.cpp* tak, aby odpovídal tomuto kódu:

     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]

9. Zvolte klávesu **F5** pro spuštění aplikace.

10. V aplikaci zadejte libovolná dvě čísla, vyberte operaci a pak zvolte **=** tlačítko.

     Zobrazí se správný výsledek.

    Tento návod ukázal, jak vytvořit a použít sada SDK rozšíření pro volání do [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] knihovny a jiné než knihovny.[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)]

## <a name="next-steps"></a>Další kroky

## <a name="see-also"></a>Viz také
- [Návod: Vytvoření sady SDK pomocí jazyka C# nebo jazyka Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Vytvoření sady pro vývoj softwaru](../extensibility/creating-a-software-development-kit.md)
