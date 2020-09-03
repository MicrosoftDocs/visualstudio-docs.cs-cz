---
title: 'Návod: vytvoření sady SDK pomocí jazyka C# nebo Visual Basic | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a604e3500c0ea438c987c4cf07ded98a5e03dd61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77558206"
---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>Návod: Vytvoření sady SDK pomocí jazyka C# nebo Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto návodu se dozvíte, jak vytvořit jednoduchou sadu SDK pro matematické knihovny pomocí jazyka Visual C# a pak zabalit sadu SDK jako rozšíření sady Visual Studio (VSIX). Dokončete následující postupy:  
  
- [Vytvoření součásti prostředí Windows Runtime SimpleMath](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
- [Vytvoření projektu rozšíření SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
- [Vytvoření ukázkové aplikace, která používá knihovnu tříd](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Předpoklady  
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a> Vytvoření součásti prostředí Windows Runtime SimpleMath  
  
1. Na panelu nabídek vyberte položku **soubor**, **Nový**, **Nový projekt**.  
  
2. V seznamu šablon rozbalte položku **Visual C#** nebo **Visual Basic**, zvolte uzel **Windows Store** a poté vyberte šablonu **součásti prostředí Windows Runtime** .  
  
3. Do pole **název** zadejte **SimpleMath**a poté klikněte na tlačítko **OK** .  
  
4. V **Průzkumník řešení**otevřete místní nabídku uzlu projektu **SimpleMath** a poté zvolte možnost **vlastnosti**.  
  
5. Přejmenujte **Class1.cs** na **arithmetic.cs** a aktualizujte ji tak, aby odpovídala následujícímu kódu:  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs#3)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb#3)]  
  
6. V **Průzkumník řešení**otevřete místní nabídku uzlu **řešení ' SimpleMath '** a pak zvolte možnost **Configuration Manager**.  
  
     Otevře se dialogové okno **Configuration Manager** .  
  
7. V seznamu **aktivní konfigurace řešení** vyberte možnost **verze**.  
  
8. Ve sloupci **Konfigurace** ověřte, že je na řádku **SimpleMath** nastavená **verze**, a pak kliknutím na tlačítko **Zavřít** tuto změnu potvrďte.  
  
    > [!IMPORTANT]
    > Sada SDK pro komponentu SimpleMath zahrnuje pouze jednu konfiguraci. Tato konfigurace musí být sestavení pro vydání, nebo aplikace, které tuto komponentu používají, nebudou dodávat certifikaci pro [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)] .  
  
9. V **Průzkumník řešení**otevřete místní nabídku uzlu projektu **SimpleMath** a pak zvolte možnost **sestavit**.  
  
## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a> Vytvoření projektu rozšíření SimpleMathVSIX  
  
1. V místní nabídce uzlu **řešení ' SimpleMath '** vyberte možnost **Přidat**, **Nový projekt**.  
  
2. V seznamu šablon rozbalte položku **Visual C#** nebo **Visual Basic**, zvolte uzel **rozšiřitelnost** a pak zvolte šablonu **projektu VSIX** .  
  
3. Do pole **název** zadejte **SimpleMathVSIX**a poté klikněte na tlačítko **OK** .  
  
4. V **Průzkumník řešení**vyberte položku **zdroj. extension. vsixmanifest** .  
  
5. Na panelu nabídek vyberte možnost **zobrazení**, **kód**.  
  
6. Existující XML nahraďte následujícím kódem XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7. V **Průzkumník řešení**vyberte projekt **SimpleMathVSIX** .  
  
8. Na panelu nabídek vyberte možnost **projekt**, **Přidat novou položku**.  
  
9. V seznamu **běžných položek**rozbalte položku **data**a pak zvolte možnost **soubor XML**.  
  
10. Do pole **název** zadejte `SDKManifest.xml` a pak klikněte na tlačítko **Přidat** .  
  
11. V **Průzkumník řešení**otevřete místní nabídku pro `SDKManifest.xml` , zvolte **vlastnosti**a pak změňte hodnotu vlastnosti **zahrnout do VSIX** na **true**.  
  
12. Obsah souboru nahraďte následujícím kódem XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmathvsix/sdkmanifest.xml#1)]
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmathvsix/sdkmanifest.xml#1)]  
  
13. V **Průzkumník řešení**otevřete místní nabídku pro projekt **SimpleMathVSIX** , zvolte možnost **Přidat**a pak zvolte možnost **Nová složka**.  
  
14. Přejmenujte složku na `references` .  
  
15. Otevřete místní nabídku složky **odkazy** , zvolte možnost **Přidat**a pak zvolte možnost **Nová složka**.  
  
16. Přejmenujte podsložku na `commonconfiguration` , vytvořte v ní podsložku a pojmenujte ji `neutral` .  
  
17. Opakujte předchozí čtyři kroky, čímž pojmenujete první složku na `redist` .  
  
     Projekt teď obsahuje následující strukturu složek:  
  
    ```  
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. V **Průzkumník řešení**otevřete místní nabídku pro projekt **SimpleMath** a pak zvolte možnost **Otevřít složku v Průzkumníku souborů**.  
  
19. V **Průzkumníku souborů**přejděte do složky bin\Release, otevřete místní nabídku pro soubor SimpleMath. winmd a pak zvolte **Kopírovat**.  
  
20. V **Průzkumník řešení**vložte soubor do složky references\commonconfiguration\neutral v projektu **SimpleMathVSIX** .  
  
21. Opakujte předchozí krok a vložte soubor SimpleMath. pri do složky redist\commonconfiguration\neutral v projektu **SimpleMathVSIX** .  
  
22. V **Průzkumník řešení**vyberte **SimpleMath. winmd**.  
  
23. Na panelu nabídek vyberte možnost **zobrazení**, **vlastnosti** (klávesnice: vyberte klávesu F4).  
  
24. V okně **vlastnosti** změňte vlastnost **Akce sestavení** na **obsah**a poté změňte vlastnost **Zahrnout v souboru VSIX** na **hodnotu true**.  
  
25. V **Průzkumník řešení**opakujte tento postup pro **SimpleMath. pri**.  
  
26. V **Průzkumník řešení**vyberte projekt **SimpleMathVSIX** .  
  
27. Na řádku nabídek klikněte na položku **sestavit**, **sestavit SimpleMathVSIX**.  
  
28. V **Průzkumník řešení**otevřete místní nabídku pro projekt **SimpleMathVSIX** a pak zvolte možnost **Otevřít složku v Průzkumníku souborů**.  
  
29. V **Průzkumníku souborů**přejděte do složky \bin\Release a potom spusťte SimpleMathVSIX. vsix a nainstalujte ji.  
  
30. Klikněte na tlačítko **instalovat** , počkejte na dokončení instalace a pak restartujte aplikaci Visual Studio.  
  
## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Vytvoření ukázkové aplikace, která používá knihovnu tříd  
  
1. Na panelu nabídek vyberte položku **soubor**, **Nový**, **Nový projekt**.  
  
2. V seznamu šablon rozbalte položku **Visual C#** nebo **Visual Basic**a pak vyberte uzel **Windows Store** .  
  
3. Zvolte šablonu **prázdná aplikace** , pojmenujte projekt **ArithmeticUI**a pak klikněte na tlačítko **OK** .  
  
4. V **Průzkumník řešení**otevřete místní nabídku pro projekt **ArithmeticUI** a pak zvolte možnost **Přidat**, **odkaz**.  
  
5. V seznamu typů odkazů rozbalte **okna**a pak zvolte **rozšíření**.  
  
6. V podokně podrobností vyberte **jednoduché rozšíření matematické sady SDK** .  
  
    Zobrazí se další informace o sadě SDK. Můžete zvolit odkaz **Další informace** pro otevření https://docs.microsoft.com , jak je uvedeno v souboru SDKManifest.xml výše v tomto návodu.  
  
7. V dialogovém okně **Správce odkazů** zaškrtněte políčko **Jednoduchá sada Math SDK** a pak klikněte na tlačítko **OK** .  
  
8. Na panelu nabídek vyberte možnost **zobrazení**, **Prohlížeč objektů**.  
  
9. V seznamu **Procházet** vyberte **jednoduché matematické**.  
  
     Teď můžete prozkoumat, co je v sadě SDK.  
  
10. V **Průzkumník řešení**otevřete MainPage. XAML a nahraďte jeho obsah následujícím XAML:  
  
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml#1)]
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml#1)]  
  
11. Aktualizujte MainPage.xaml.cs tak, aby odpovídaly následujícímu kódu:  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml.cs#2)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml.vb#2)]  
  
12. Kliknutím na klávesu F5 spusťte aplikaci.  
  
13. V aplikaci zadejte dvě čísla, zvolte operaci a pak klikněte na **=** tlačítko.  
  
     Zobrazí se správný výsledek.  
  
    Úspěšně jste vytvořili a použili sadu SDK rozšíření.  
  
## <a name="see-also"></a>Viz také  
 [Návod: vytvoření sady SDK pomocí jazyka C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Návod: vytvoření sady SDK pomocí JavaScriptu](walkthrough-creating-an-sdk-using-javascript.md)   
 [Vytvoření sady SDK (Software Development Kit)](../extensibility/creating-a-software-development-kit.md)
