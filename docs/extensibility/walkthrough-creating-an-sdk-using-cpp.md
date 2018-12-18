---
title: 'Návod: Vytvoření sady SDK pomocí jazyka C++ | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6311526df299da860c829520a2087ecc8d786600
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930637"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Návod: Vytvoření sady SDK pomocí jazyka C++
Tento návod ukazuje, jak vytvořit nativní C++ matematické knihovny sady SDK, balíčku sady SDK jako Visual Studio Extension (VSIX) a použijte ji k vytvoření aplikace. Návod je rozdělen na tyto kroky:  
  
-   [Chcete-li vytvořit nativní a prostředí Windows Runtime knihovny](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [Chcete-li vytvořit projekt rozšíření NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [K vytvoření ukázkové aplikace, která používá knihovnu tříd](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Požadavky  
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a> Chcete-li vytvořit nativní a prostředí Windows Runtime knihovny  
  
1.  V panelu nabídky zvolte **souboru** > **nový** > **projektu**.  
  
2.  V seznamu šablon rozbalte **Visual C++** > **Windows Universal**a pak vyberte **knihovny DLL (Windows Universal apps)** šablony. V **název** zadejte `NativeMath`a klikněte na tlačítko **OK** tlačítko.  
  
3.  Aktualizace *NativeMath.h* tak, aby odpovídala následující kód.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  Aktualizace *NativeMath.cpp* tak, aby odpovídala takto:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  V **Průzkumníka řešení**, otevřete místní nabídku pro **řešení "NativeMath"** a klikněte na tlačítko **přidat** > **nový projekt**.  
  
6.  V seznamu šablon rozbalte **Visual C++** a pak vyberte **součást prostředí Windows Runtime** šablony. V **název** zadejte `NativeMathWRT`a klikněte na tlačítko **OK** tlačítko.  
  
7.  Aktualizace *Class1.h* tak, aby odpovídala takto:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  Aktualizace *Class1.cpp* tak, aby odpovídala takto:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. V panelu nabídky zvolte **sestavení** > **sestavit řešení**.  
  
##  <a name="createVSIX"></a> Chcete-li vytvořit projekt rozšíření NativeMathVSIX  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro **řešení "NativeMath"** a klikněte na tlačítko **přidat** > **nový projekt**.  
  
2.  V seznamu šablon rozbalte **Visual C#** > **rozšiřitelnost**a pak vyberte **projekt VSIX**. V **název** zadejte **NativeMathVSIX**a klikněte na tlačítko **OK** tlačítko.
  
3.  V **Průzkumníka řešení**, otevřete místní nabídku pro **source.extension.vsixmanifest**a klikněte na tlačítko **zobrazit kód**.  
  
4.  Použijte následující kód XML má nahradit existující soubor XML.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5.  V **Průzkumníka řešení**, otevřete místní nabídku **NativeMathVSIX** projektu a klikněte na tlačítko **přidat** > **nová položka**.  
  
6.  V seznamu **položky Visual C#**, rozbalte **Data**a pak vyberte **soubor XML**. V **název** zadejte `SDKManifest.xml`a klikněte na tlačítko **OK** tlačítko.  
  
7.  Pomocí tohoto XML kódu nahraďte obsah souboru:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
8. V **Průzkumníka řešení**v části **NativeMathVSIX** projekt, vytvořte tuto strukturu složek:  
  
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
  
9. V **Průzkumníka řešení**, otevřete místní nabídku pro **řešení "NativeMath"** a klikněte na tlačítko **otevřít složku v Průzkumníku souborů**.  
  
10. V **Průzkumníka souborů**, kopie *$SolutionRoot$\NativeMath\NativeMath.h*a potom v **Průzkumníka řešení**v části **NativeMathVSIX**projektu, vložte ji *$SolutionRoot$ \NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include\\*  složky.  
  
     Kopírování *$SolutionRoot$\Debug\NativeMath\NativeMath.lib*a vložte jej do *$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\\*  složky.  
  
     Kopírování *$SolutionRoot$\Debug\NativeMath\NativeMath.dll* a vložte ji *$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86\\*  složky.  
  
     Kopírování *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll* a vložte ji *$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86* složky.  
     Kopírování *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd* a vložte ji *$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral* složky.  
  
     Kopírování *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri* a vložte ji *$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral* složky.  
  
11. V *$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\\*  složce vytvořte textový soubor s názvem *NativeMathSDK.props*a pak vložte do něj následující obsah:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
12. V panelu nabídky zvolte **zobrazení** > **ostatní Windows** > **okno vlastností** (klávesnice: Zvolte **F4**klíč).  
  
13. V **Průzkumníka řešení**, vyberte **NativeMathWRT.winmd** souboru. V **vlastnosti** okno Změnit **akce sestavení** vlastnost **obsahu**a potom změňte **zahrnout do VSIX** vlastnost  **Hodnota TRUE**.  
  
     Opakujte tento postup u **NativeMath.h** souboru.  
  
     Opakujte tento postup u **NativeMathWRT.pri** souboru.  
  
     Opakujte tento postup u **NativeMath.Lib** souboru.  
  
     Opakujte tento postup u **NativeMathSDK.props** souboru.  
  
14. V **Průzkumníka řešení**, vyberte **NativeMath.h** souboru. V **vlastnosti** okno Změnit **zahrnout do VSIX** vlastnost **True**.  
  
     Opakujte tento postup u **NativeMath.dll** souboru.  
  
     Opakujte tento postup u **NativeMathWRT.dll** souboru.  
  
     Opakujte tento postup u **SDKManifest.xml** souboru.  
  
15. V panelu nabídky zvolte **sestavení** > **sestavit řešení**.  
  
16. V **Průzkumníka řešení**, otevřete místní nabídku **NativeMathVSIX** projektu a klikněte na tlačítko **otevřít složku v Průzkumníku souborů**.  
  
17. V **Průzkumníka souborů**, přejděte *$SolutionRoot$ \NativeMathVSIX\bin\Debug* složku a potom spusťte *NativeMathVSIX.vsix* a spusťte tak instalaci.  
  
18. Zvolte **nainstalovat** tlačítko, počkejte na dokončení instalace a poté spusťte Visual Studio.  
  
##  <a name="createSample"></a> K vytvoření ukázkové aplikace, která používá knihovnu tříd  
  
1. V panelu nabídky zvolte **souboru** > **nový** > **projektu**.  
  
2. V seznamu šablon rozbalte **Visual C++** > **Windows Universal** a pak vyberte **prázdnou aplikaci**. V **název** zadejte **NativeMathSDKSample**a klikněte na tlačítko **OK** tlačítko.  
  
3. V **Průzkumníka řešení**, otevřete místní nabídku **NativeMathSDKSample** projektu a klikněte na tlačítko **přidat** > **odkaz**.  
  
4. V **přidat odkaz** dialogové okno, v seznamu typy odkazů, rozbalte **Universal Windows**a pak vyberte **rozšíření**. Nakonec vyberte **nativní sadou SDK matematické** zaškrtněte políčko a klikněte na tlačítko **OK** tlačítko.
  
5. Zobrazte vlastnosti projektu pro NativeMathSDKSample.  
  
    Vlastnosti, které jste definovali v *NativeMathSDK.props* byly použity při přidání odkazu. Můžete ověřit kontrolou byly použity vlastnosti **adresáře VC ++** vlastnost projektu **vlastnosti konfigurace**.  
  
6. V **Průzkumníka řešení**, otevřete **MainPage.xaml**a pak pomocí následujících XAML nahraďte jeho obsah:  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
7. Aktualizace *Mainpage.xaml.h* tak, aby odpovídala takto:  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
8. Aktualizace *MainPage.xaml.cpp* tak, aby odpovídala takto:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
9. Zvolte **F5** klíč ke spuštění aplikace.  
  
10. V aplikaci, zadejte jakékoli dvě čísla, vyberte operaci a klikněte na tlačítko **=** tlačítko.  
  
     Správný výsledek se zobrazí.  
  
    Tento průvodce vám ukázal, jak vytvořit a použít rozšiřující sadu SDK pro volání do [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] knihovny a non -[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] knihovny.  
  
## <a name="next-steps"></a>Další kroky  
  
## <a name="see-also"></a>Viz také:  
 [Návod: Vytvoření sady SDK pomocí jazyka C# nebo Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Vytvořit sadu software development kit](../extensibility/creating-a-software-development-kit.md)
