---
title: 'Návod: vytvoření sady SDK pomocí jazyka C++ | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1312d61b2d287a5dd8cb757b73e818a9e9cb2241
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202055"
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Návod: Vytvoření sady SDK pomocí jazyka C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak vytvořit nativní sadu SDK pro C++ Math Library, zabalit sadu SDK jako rozšíření sady Visual Studio (VSIX) a pak ji použít k vytvoření aplikace. Tento návod je rozdělen do těchto kroků:  
  
- [Vytvoření nativní knihovny a knihovny prostředí Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
- [Vytvoření projektu rozšíření NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
- [Vytvoření ukázkové aplikace, která používá knihovnu tříd](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Předpoklady  
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a> Vytvoření nativní knihovny a knihovny prostředí Windows Runtime  
  
1. Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.  
  
2. V seznamu šablon rozbalte **Visual C++**, **Windows Store**a pak vyberte šablonu **DLL (aplikace pro Windows Store)** . Do pole **název** zadejte `NativeMath` a pak klikněte na tlačítko **OK** .  
  
3. Aktualizujte NativeMath. h tak, aby odpovídaly následujícímu kódu.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h#1)]  
  
4. Aktualizujte NativeMath. cpp tak, aby odpovídaly tomuto kódu:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp#2)]  
  
5. V **Průzkumník řešení**otevřete místní nabídku pro **řešení ' NativeMath '** a pak zvolte **Přidat**, **Nový projekt**.  
  
6. V seznamu šablon rozbalte položku **Visual C++** a potom vyberte šablonu **prostředí Windows Runtime součásti** . Do pole **název** zadejte `NativeMathWRT` a pak klikněte na tlačítko **OK** .  
  
7. Aktualizujte Class1. h, aby odpovídal tomuto kódu:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h#3)]  
  
8. Aktualizujte Class1. cpp tak, aby odpovídaly tomuto kódu:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp#4)]  
  
9. Na panelu nabídek vyberte **sestavení**, **řešení sestavení**.  
  
## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> Vytvoření projektu rozšíření NativeMathVSIX  
  
1. V **Průzkumník řešení**otevřete místní nabídku pro **řešení ' NativeMath '** a pak zvolte **Přidat**, **Nový projekt**.  
  
2. V seznamu šablon rozbalte položku **Visual C#**, **rozšiřitelnost**a pak vyberte **balíček VSIX**. Do pole **název** zadejte **NativeMathVSIX**a poté klikněte na tlačítko **OK** .  
  
3. Jakmile se zobrazí Návrhář manifestu VSIX, zavřete ho.  
  
4. V **Průzkumník řešení**otevřete místní nabídku pro **source. extension. vsixmanifest**a pak zvolte **Zobrazit kód**.  
  
5. Pomocí následujícího kódu XML nahraďte existující kód XML.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]
  
6. V **Průzkumník řešení**otevřete místní nabídku pro projekt **NativeMathVSIX** a pak zvolte možnost **Přidat**, **Nová položka**.  
  
7. V seznamu **položek Visual C#** rozbalte položku **data**a pak vyberte **soubor XML**. Do pole **název** zadejte `SDKManifest.xml` a pak klikněte na tlačítko **OK** .  
  
8. Pomocí tohoto XML nahraďte obsah souboru:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml#5)]  
  
9. V **Průzkumník řešení**vytvořte v projektu **NativeMathVSIX** tuto strukturu složek:  
  
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
  
10. V **Průzkumník řešení**otevřete místní nabídku pro **řešení ' NativeMath '** a pak zvolte možnost **Otevřít složku v Průzkumníku souborů**.  
  
11. V **Průzkumníku souborů**zkopírujte \NativeMath\NativeMath.h a potom v **Průzkumník řešení**v projektu **NativeMathVSIX** jej vložte do složky \DesignTime\CommonConfiguration\Neutral\Include\.  
  
     Zkopírujte \Debug\NativeMath\NativeMath.lib a vložte ho do složky \DesignTime\Debug\x86\.  
  
     Zkopírujte \Debug\NativeMath\NativeMath.dll a vložte ho do složky \Redist\Debug\x86\.  
  
     Zkopírujte DebugNativeMathWRTNativeMathWRT.dll a vložte ho do složky RedistDebugx86.  
  
     Zkopírujte DebugNativeMathWRTNativeMathWRT. winmd a vložte ho do složky ReferencesCommonConfigurationNeutral.  
  
     Zkopírujte DebugNativeMathWRTNativeMathWRT. pri a vložte ho do složky ReferencesCommonConfigurationNeutral.  
  
12. Ve složce \DesignTime\Debug\x86\ vytvořte textový soubor s názvem NativeMathSDK. props a vložte do něj následující obsah:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. Na panelu nabídek vyberte možnost **zobrazení**, **ostatní okna**, **okno vlastností** (klávesnice: vyberte klávesu F4).  
  
14. V **Průzkumník řešení**vyberte soubor **NativeMathWRT. winmd** . V okně **vlastnosti** změňte vlastnost **Akce sestavení** na **obsah**a poté změňte vlastnost **Zahrnout v souboru VSIX** na **hodnotu true**.  
  
     Tento postup opakujte pro soubor **SimpleMath. pri** .  
  
     Tento postup opakujte pro soubor **NativeMath. lib** .  
  
     Tento postup opakujte pro soubor **NativeMathSDK. props** .  
  
15. V **Průzkumník řešení**vyberte soubor **NativeMath. h** . V okně **vlastnosti** změňte vlastnost **zahrnout do VSIX** na **hodnotu true**.  
  
     Tento postup opakujte pro soubor **NativeMath.dll** .  
  
     Tento postup opakujte pro soubor **NativeMathWRT.dll** .  
  
     Tento postup opakujte pro soubor **SDKManifest.xml** .  
  
16. Na panelu nabídek vyberte **sestavení**, **řešení sestavení**.  
  
17. V **Průzkumník řešení**otevřete místní nabídku pro projekt **NativeMathVSIX** a pak zvolte možnost **Otevřít složku v Průzkumníku souborů**.  
  
18. V **Průzkumníku souborů**přejděte do složky \bin\Debug\ a spuštěním NativeMathVSIX. vsix spusťte instalaci.  
  
19. Klikněte na tlačítko **instalovat** , počkejte na dokončení instalace a pak restartujte aplikaci Visual Studio.  
  
## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Vytvoření ukázkové aplikace, která používá knihovnu tříd  
  
1. Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.  
  
2. V seznamu šablon rozbalte **Visual C++**, **Windows Store**a pak vyberte **prázdná aplikace**. Do pole **název** zadejte **NativeMathSDKSample**a poté klikněte na tlačítko **OK** .  
  
3. V **Průzkumník řešení**otevřete místní nabídku pro projekt **NativeMathSDKSample** a pak zvolte možnost **Přidat**, **odkaz**.  
  
4. Na stránce **společné vlastnosti**, **Architektura a odkazy** v seznamu typů odkazů rozbalte **okna**a pak vyberte **rozšíření**. V podokně podrobností vyberte **nativní rozšíření matematické sady SDK** a pak klikněte na tlačítko **Přidat nový odkaz** .  
  
5. V dialogovém okně **Přidat odkaz** zaškrtněte políčko **nativní sada matematických SDK** a pak klikněte na tlačítko **OK** .  
  
6. Zobrazí vlastnosti projektu pro NativeMathSDKSample.  
  
    Vlastnosti, které jste definovali v NativeMathSDK. props, byly aplikovány při přidání odkazu. To můžete ověřit kontrolou vlastnosti **adresářů VC + +** **vlastností konfigurace**projektu.  
  
7. V **Průzkumník řešení**otevřete MainPage. XAML a pak použijte následující XAML k nahrazení jeho obsahu:  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml#1)]  
  
8. Aktualizujte MainPage. XAML. h, aby odpovídaly tomuto kódu:  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h#2)]  
  
9. Aktualizujte MainPage. XAML. cpp tak, aby odpovídaly tomuto kódu:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp#3)]  
  
10. Kliknutím na klávesu F5 spusťte aplikaci.  
  
11. V aplikaci zadejte dvě čísla, vyberte operaci a pak klikněte na **=** tlačítko.  
  
     Zobrazí se správný výsledek.  
  
    Tento návod ukázal, jak vytvořit a použít sadu SDK rozšíření pro volání do [!INCLUDE[wrt](../includes/wrt-md.md)] knihovny a ne [!INCLUDE[wrt](../includes/wrt-md.md)] knihovny.  
  
## <a name="next-steps"></a>Další kroky  
  
## <a name="see-also"></a>Viz také  
 [Návod: vytvoření sady SDK pomocí jazyka C# nebo Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Vytvoření sady SDK (Software Development Kit)](../extensibility/creating-a-software-development-kit.md)
