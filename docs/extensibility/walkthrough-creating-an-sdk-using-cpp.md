---
title: 'Návod: vytvoření sady SDK pomocí jazyka C++ | Microsoft Docs'
description: Naučte se vytvořit nativní C++ SDK pro matematické knihovny, zabalit sadu SDK jako rozšíření sady Visual Studio a pak ji použít k vytvoření aplikace pomocí tohoto návodu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f3f9b9efc625b435f304b192d3ca52f514e682e8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951911"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Návod: vytvoření sady SDK pomocí jazyka C++
Tento návod ukazuje, jak vytvořit nativní sadu SDK pro C++ Math Library, zabalit sadu SDK jako rozšíření sady Visual Studio (VSIX) a pak ji použít k vytvoření aplikace. Tento návod je rozdělen do těchto kroků:

- [Vytvoření nativní knihovny a knihovny prostředí Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [Vytvoření projektu rozšíření NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [Vytvoření ukázkové aplikace, která používá knihovnu tříd](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Požadavky
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a> Vytvoření nativní knihovny a knihovny prostředí Windows Runtime

1. Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

2. V seznamu šablon rozbalte **Visual C++**  >  **Windows Universal** a pak vyberte šablonu **DLL (univerzální aplikace pro Windows)** . Do pole **název** zadejte `NativeMath` a pak klikněte na tlačítko **OK** .

3. Aktualizujte *NativeMath. h* tak, aby odpovídaly následujícímu kódu.

     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]

4. Aktualizujte *NativeMath. cpp* tak, aby odpovídaly tomuto kódu:

     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]

5. V **Průzkumník řešení** otevřete místní nabídku pro **řešení ' NativeMath '** a pak zvolte **Přidat**  >  **Nový projekt**.

6. V seznamu šablon rozbalte položku **Visual C++** a potom vyberte šablonu **prostředí Windows Runtime součásti** . Do pole **název** zadejte `NativeMathWRT` a pak klikněte na tlačítko **OK** .

7. Aktualizujte *Class1. h* , aby odpovídal tomuto kódu:

     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]

8. Aktualizujte *Class1. cpp* tak, aby odpovídaly tomuto kódu:

     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]

9. Na řádku nabídek klikněte na **sestavit** sestavení  >  **řešení**.

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> Vytvoření projektu rozšíření NativeMathVSIX

1. V **Průzkumník řešení** otevřete místní nabídku pro **řešení ' NativeMath '** a pak zvolte **Přidat**  >  **Nový projekt**.

2. V seznamu šablon rozbalte rozšíření **Visual C#**  >  a pak vyberte **projekt VSIX**. Do pole **název** zadejte **NativeMathVSIX** a poté klikněte na tlačítko **OK** .

3. V **Průzkumník řešení** otevřete místní nabídku pro **source. extension. vsixmanifest** a pak zvolte **Zobrazit kód**.

4. Pomocí následujícího kódu XML nahraďte existující kód XML.

    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5. V **Průzkumník řešení** otevřete místní nabídku pro projekt **NativeMathVSIX** a pak zvolte možnost **Přidat**  >  **novou položku**.

6. V seznamu **položek Visual C#** rozbalte položku **data** a pak vyberte **soubor XML**. Do pole **název** zadejte `SDKManifest.xml` a pak klikněte na tlačítko **OK** .

7. Pomocí tohoto XML nahraďte obsah souboru:

     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]

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

    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]

12. Na panelu nabídek vyberte možnost **Zobrazit**  >  **Další**  >  **okna vlastnosti** systému Windows (klávesnice: vyberte klávesu **F4** ).

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

18. Klikněte na tlačítko **instalovat** , počkejte na dokončení instalace a poté otevřete aplikaci Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Vytvoření ukázkové aplikace, která používá knihovnu tříd

1. Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

2. V seznamu šablon rozbalte **Visual C++**  >  **univerzální pro Windows** a pak vyberte **prázdná aplikace**. Do pole **název** zadejte **NativeMathSDKSample** a poté klikněte na tlačítko **OK** .

3. V **Průzkumník řešení** otevřete místní nabídku pro projekt **NativeMathSDKSample** a pak zvolte možnost **Přidat**  >  **odkaz**.

4. V dialogovém okně **Přidat odkaz** v seznamu typů odkazů rozbalte možnost **univerzální pro Windows** a pak vyberte **rozšíření**. Nakonec zaškrtněte políčko **nativní sada matematických SDK** a pak klikněte na tlačítko **OK** .

5. Zobrazí vlastnosti projektu pro NativeMathSDKSample.

    Vlastnosti, které jste definovali v *NativeMathSDK. props* , byly aplikovány při přidání odkazu. Vlastnosti, které byly aplikovány, lze ověřit kontrolou vlastnosti **adresářů VC + +** **vlastností konfigurace** projektu.

6. V **Průzkumník řešení** otevřete **MainPage. XAML** a pak použijte následující XAML k nahrazení jeho obsahu:

    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]

7. Aktualizujte *MainPage. XAML. h* , aby odpovídaly tomuto kódu:

    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]

8. Aktualizujte *MainPage. XAML. cpp* tak, aby odpovídaly tomuto kódu:

     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]

9. Kliknutím na klávesu **F5** spusťte aplikaci.

10. V aplikaci zadejte dvě čísla, vyberte operaci a pak klikněte na **=** tlačítko.

     Zobrazí se správný výsledek.

    Tento návod ukázal, jak vytvořit a použít sadu SDK rozšíření pro volání do [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] knihovny a ne [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] knihovny.

## <a name="next-steps"></a>Další kroky

## <a name="see-also"></a>Viz také
- [Návod: vytvoření sady SDK pomocí jazyka C# nebo Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Vytvoření sady SDK (Software Development Kit)](../extensibility/creating-a-software-development-kit.md)
