---
title: 'Návod: Vytvoření sady SDK pomocí jazyka C++ | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0932759213d064c3df717b7b6735c1201e62ce14
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773467"
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Návod: Vytvoření sady SDK pomocí jazyka C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak vytvořit nativní C++ matematické knihovny sady SDK, balíčku sady SDK jako Visual Studio Extension (VSIX) a použijte ji k vytvoření aplikace. Návod je rozdělen na tyto kroky:  
  
-   [Chcete-li vytvořit nativní a prostředí Windows Runtime knihovny](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [Chcete-li vytvořit projekt rozšíření NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [K vytvoření ukázkové aplikace, která používá knihovnu tříd](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Požadavky  
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a> Chcete-li vytvořit nativní a prostředí Windows Runtime knihovny  
  
1.  V panelu nabídky zvolte **souboru**, **nový**, **projektu**.  
  
2.  V seznamu šablon rozbalte **Visual C++**, **Windows Store**a pak vyberte **knihovny DLL (aplikace pro Windows Store)** šablony. V **název** zadejte `NativeMath`a klikněte na tlačítko **OK** tlačítko.  
  
3.  Aktualizujte NativeMath.h tak, aby odpovídala následující kód.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h#1)]  
  
4.  Aktualizace NativeMath.cpp tak, aby odpovídala takto:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp#2)]  
  
5.  V **Průzkumníka řešení**, otevřete místní nabídku pro **řešení "NativeMath"** a klikněte na tlačítko **přidat**, **nový projekt**.  
  
6.  V seznamu šablon rozbalte **Visual C++** a pak vyberte **součást prostředí Windows Runtime** šablony. V **název** zadejte `NativeMathWRT`a klikněte na tlačítko **OK** tlačítko.  
  
7.  Aktualizace Class1.h tak, aby odpovídala takto:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h#3)]  
  
8.  Aktualizace Class1.cpp tak, aby odpovídala takto:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp#4)]  
  
9. V panelu nabídky zvolte **sestavení**, **sestavit řešení**.  
  
##  <a name="createVSIX"></a> Chcete-li vytvořit projekt rozšíření NativeMathVSIX  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro **řešení "NativeMath"** a klikněte na tlačítko **přidat**, **nový projekt**.  
  
2.  V seznamu šablon rozbalte **Visual C#**, **rozšiřitelnost**a pak vyberte **balíčku VSIX**. V **název** zadejte **NativeMathVSIX**a klikněte na tlačítko **OK** tlačítko.  
  
3.  Jakmile se zobrazí Návrhář manifestů VSIX, zavřete ho.  
  
4.  V **Průzkumníka řešení**, otevřete místní nabídku pro **source.extension.vsixmanifest**a klikněte na tlačítko **zobrazit kód**.  
  
5.  Použijte následující kód XML má nahradit existující soubor XML.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]
  
6.  V **Průzkumníka řešení**, otevřete místní nabídku **NativeMathVSIX** projektu a klikněte na tlačítko **přidat**, **nová položka**.  
  
7.  V seznamu **položky Visual C#**, rozbalte **Data**a pak vyberte **soubor XML**. V **název** zadejte `SDKManifest.xml`a klikněte na tlačítko **OK** tlačítko.  
  
8.  Pomocí tohoto XML kódu nahraďte obsah souboru:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml#5)]  
  
9. V **Průzkumníka řešení**v **NativeMathVSIX** projekt, vytvořte tuto strukturu složek:  
  
    ```  
  
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
  
10. V **Průzkumníka řešení**, otevřete místní nabídku pro **řešení "NativeMath"** a klikněte na tlačítko **otevřít složku v Průzkumníku souborů**.  
  
11. V **Průzkumníka souborů**, zkopírujte \NativeMath\NativeMath.h a potom v **Průzkumníka řešení**v **NativeMathVSIX** projektu, vložte ji \DesignTime\ CommonConfiguration\Neutral\Include\ složky.  
  
     \Debug\NativeMath\NativeMath.lib zkopírujte a vložte ho do složky \DesignTime\Debug\x86\.  
  
     \Debug\NativeMath\NativeMath.dll zkopírujte a vložte ho do složky \Redist\Debug\x86\.  
  
     DebugNativeMathWRTNativeMathWRT.dll zkopírujte a vložte ho do složky RedistDebugx86.  
  
     DebugNativeMathWRTNativeMathWRT.winmd zkopírujte a vložte ho do složky ReferencesCommonConfigurationNeutral.  
  
     DebugNativeMathWRTNativeMathWRT.pri zkopírujte a vložte ho do složky ReferencesCommonConfigurationNeutral.  
  
12. Ve složce \DesignTime\Debug\x86\ vytvořte textový soubor s názvem NativeMathSDK.props a pak do něj vložte následující obsah:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. V panelu nabídek zvolte **zobrazení**, **ostatní Windows**, **okno Vlastnosti** (klávesnice: klávesou F4).  
  
14. V **Průzkumníka řešení**, vyberte **NativeMathWRT.winmd** souboru. V **vlastnosti** okno Změnit **akce sestavení** vlastnost **obsahu**a potom změňte **zahrnout do VSIX** vlastnost  **Hodnota TRUE**.  
  
     Opakujte tento postup u **SimpleMath.pri** souboru.  
  
     Opakujte tento postup u **NativeMath.Lib** souboru.  
  
     Opakujte tento postup u **NativeMathSDK.props** souboru.  
  
15. V **Průzkumníka řešení**, vyberte **NativeMath.h** souboru. V **vlastnosti** okno Změnit **zahrnout do VSIX** vlastnost **True**.  
  
     Opakujte tento postup u **NativeMath.dll** souboru.  
  
     Opakujte tento postup u **NativeMathWRT.dll** souboru.  
  
     Opakujte tento postup u **SDKManifest.xml** souboru.  
  
16. V panelu nabídky zvolte **sestavení**, **sestavit řešení**.  
  
17. V **Průzkumníka řešení**, otevřete místní nabídku **NativeMathVSIX** projektu a klikněte na tlačítko **otevřít složku v Průzkumníku souborů**.  
  
18. V **Průzkumníka souborů**, přejděte do složky \bin\Debug\, a pak spusťte NativeMathVSIX.vsix a spusťte tak instalaci.  
  
19. Zvolte **nainstalovat** tlačítko, počkejte na dokončení instalace a potom restartujte Visual Studio.  
  
##  <a name="createSample"></a> K vytvoření ukázkové aplikace, která používá knihovnu tříd  
  
1. V panelu nabídky zvolte **souboru**, **nový**, **projektu**.  
  
2. V seznamu šablon rozbalte **Visual C++**, **Windows Store**a pak vyberte **prázdnou aplikaci**. V **název** zadejte **NativeMathSDKSample**a klikněte na tlačítko **OK** tlačítko.  
  
3. V **Průzkumníka řešení**, otevřete místní nabídku **NativeMathSDKSample** projektu a klikněte na tlačítko **přidat**, **odkaz**.  
  
4. Na **společné vlastnosti**, **rámec a odkazy** rozbalte stránku vlastností v seznamu typy odkazů, **Windows**a pak vyberte **rozšíření** . V podokně podrobností vyberte **nativní sadou SDK matematické** rozšíření a klikněte na tlačítko **přidat nový odkaz** tlačítko.  
  
5. V **přidat odkaz** dialogové okno, vyberte **nativní sadou SDK matematické** zaškrtněte políčko a klikněte na tlačítko **OK** tlačítko.  
  
6. Zobrazte vlastnosti projektu pro NativeMathSDKSample.  
  
    Vlastnosti, které jste definovali v NativeMathSDK.props byly použity při přidání odkazu. To můžete ověřit kontrolou **adresáře VC ++** vlastnost projektu **vlastnosti konfigurace**.  
  
7. V **Průzkumníka řešení**, otevřete MainPage.xaml a pak pomocí následujících XAML nahraďte jeho obsah:  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml#1)]  
  
8. Aktualizace Mainpage.xaml.h tak, aby odpovídala takto:  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h#2)]  
  
9. Aktualizace MainPage.xaml.cpp tak, aby odpovídala takto:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp#3)]  
  
10. Stisknutím klávesy F5 spusťte aplikaci.  
  
11. V aplikaci, zadejte jakékoli dvě čísla, vyberte operaci a klikněte na tlačítko **=** tlačítko.  
  
     Správný výsledek se zobrazí.  
  
    Tento průvodce vám ukázal, jak vytvořit a použít rozšiřující sadu SDK pro volání do [!INCLUDE[wrt](../includes/wrt-md.md)] knihovny a non -[!INCLUDE[wrt](../includes/wrt-md.md)] knihovny.  
  
## <a name="next-steps"></a>Další kroky  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vytvoření sady SDK pomocí jazyka C# nebo Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Vytvoření sady SDK (Software Development Kit)](../extensibility/creating-a-software-development-kit.md)

