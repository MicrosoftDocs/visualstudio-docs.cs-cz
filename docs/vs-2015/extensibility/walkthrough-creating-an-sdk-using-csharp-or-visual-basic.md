---
title: 'Návod: Vytvoření sady SDK pomocí jazyka C# nebo Visual Basic | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3e0bc88c8581b29f43e7efc55ee86019e1f1c3fb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736762"
---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>Návod: Vytvoření sady SDK pomocí jazyka C# nebo Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto podrobném návodu se dozvíte, jak pomocí Visual C# vytvořit na sadu SDK jednoduché matematické knihovny a pak balíček sady SDK jako Visual Studio Extension (VSIX). Dokončíte následující postupy:  
  
-   [Chcete-li vytvořit komponentu SimpleMath Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
-   [Chcete-li vytvořit projekt rozšíření SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
-   [K vytvoření ukázkové aplikace, která používá knihovnu tříd](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Požadavky  
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a> Chcete-li vytvořit komponentu SimpleMath Windows Runtime  
  
1.  V panelu nabídky zvolte **souboru**, **nový**, **nový projekt**.  
  
2.  V seznamu šablon rozbalte **Visual C#** nebo **jazyka Visual Basic**, zvolte **Windows Store** uzel a klikněte na tlačítko **součástprostředíWindowsRuntime** šablony.  
  
3.  V **název** zadejte **SimpleMath**a klikněte na tlačítko **OK** tlačítko.  
  
4.  V **Průzkumníka řešení**, otevřete místní nabídku **SimpleMath** uzel projektu a klikněte na tlačítko **vlastnosti**.  
  
5.  Přejmenovat **Class1.cs** k **Arithmetic.cs** a aktualizovat ho tak, aby odpovídala následující kód:  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs#3)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb#3)]  
  
6.  V **Průzkumníka řešení**, otevřete místní nabídku **řešení "SimpleMath"** uzel a klikněte na tlačítko **nástroje Configuration Manager**.  
  
     **Nástroje Configuration Manager** zobrazí se dialogové okno.  
  
7.  V **konfigurace aktivního řešení** klikněte na položku **vydání**.  
  
8.  V **konfigurace** sloupce, ověřte, že **SimpleMath** řádek je nastavena na **vydání**a klikněte na tlačítko **Zavřít** tlačítko tak, aby přijímal Změňte.  
  
    > [!IMPORTANT]
    >  Sada SDK pro komponentu SimpleMath obsahuje pouze jednu konfiguraci. Tato konfigurace musí být sestavení pro vydání, nebo aplikace, které používají součást nebudou předávat certifikaci[!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)].  
  
9. V **Průzkumníka řešení**, otevřete místní nabídku **SimpleMath** uzel projektu a klikněte na tlačítko **sestavení**.  
  
##  <a name="createVSIX"></a> Chcete-li vytvořit projekt rozšíření SimpleMathVSIX  
  
1.  V místní nabídce pro **řešení "SimpleMath"** uzlu, vyberte **přidat**, **nový projekt**.  
  
2.  V seznamu šablon rozbalte **Visual C#** nebo **jazyka Visual Basic**, zvolte **rozšiřitelnost** uzel a klikněte na tlačítko **projekt VSIX** Šablona.  
  
3.  V **název** zadejte **SimpleMathVSIX**a klikněte na tlačítko **OK** tlačítko.  
  
4.  V **Průzkumníka řešení**, zvolte **source.extension.vsixmanifest** položky.  
  
5.  V panelu nabídky zvolte **zobrazení**, **kód**.  
  
6.  Nahraďte stávající kód XML následující kód XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7.  V **Průzkumníka řešení**, zvolte **SimpleMathVSIX** projektu.  
  
8.  V panelu nabídky zvolte **projektu**, **přidat novou položku**.  
  
9. V seznamu **společné položky**, rozbalte **Data**a klikněte na tlačítko **soubor XML**.  
  
10. V **název** zadejte `SDKManifest.xml`a klikněte na tlačítko **přidat** tlačítko.  
  
11. V **Průzkumníka řešení**, otevřete místní nabídku pro `SDKManifest.xml`, zvolte **vlastnosti**a potom změňte hodnotu **zahrnout do VSIX** vlastnost **True**.  
  
12. Nahraďte obsah souboru následující kód XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmathvsix/sdkmanifest.xml#1)]
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmathvsix/sdkmanifest.xml#1)]  
  
13. V **Průzkumníka řešení**, otevřete místní nabídku **SimpleMathVSIX** projektu, zvolte **přidat**a klikněte na tlačítko **novou složku**.  
  
14. Přejmenovat složku, do které `references`.  
  
15. Otevřete místní nabídku **odkazy** složky, zvolte **přidat**a klikněte na tlačítko **novou složku**.  
  
16. Přejmenovat podsložky `commonconfiguration`, vytvořte podsložku v rámci něj a název podsložky `neutral`.  
  
17. Zopakujte předchozí čtyři kroky, tentokrát přejmenování složce první `redist`.  
  
     Projekt nyní obsahuje následující strukturu složek:  
  
    ```  
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. V **Průzkumníka řešení**, otevřete místní nabídku **SimpleMath** projektu a klikněte na tlačítko **otevřít složku v Průzkumníku souborů**.  
  
19. V **Průzkumníka souborů**, přejděte ke složce bin\Release, otevřete místní nabídku pro soubor SimpleMath.winmd a klikněte na tlačítko **kopírování**.  
  
20. V **Průzkumníka řešení**, vložte ho do složky references\commonconfiguration\neutral **SimpleMathVSIX** projektu.  
  
21. Opakujte předchozí krok, vkládání SimpleMath.pri soubor do složky redist\commonconfiguration\neutral **SimpleMathVSIX** projektu.  
  
22. V **Průzkumníka řešení**, zvolte **SimpleMath.winmd**.  
  
23. V panelu nabídky zvolte **zobrazení**, **vlastnosti** (klávesnice: klávesou F4).  
  
24. V **vlastnosti** okno Změnit **akce sestavení** vlastnost **obsahu**a potom změňte **zahrnout do VSIX** vlastnost  **Hodnota TRUE**.  
  
25. V **Průzkumníka řešení**, opakujte tento postup u **SimpleMath.pri**.  
  
26. V **Průzkumníka řešení**, zvolte **SimpleMathVSIX** projektu.  
  
27. V panelu nabídky zvolte **sestavení**, **sestavení SimpleMathVSIX**.  
  
28. V **Průzkumníka řešení**, otevřete místní nabídku **SimpleMathVSIX** projektu a klikněte na tlačítko **otevřít složku v Průzkumníku souborů**.  
  
29. V **Průzkumníka souborů**, přejděte do složky \bin\Release, a pak spusťte SimpleMathVSIX.vsix k její instalaci.  
  
30. Zvolte **nainstalovat** tlačítko, počkejte na dokončení instalace a potom restartujte Visual Studio.  
  
##  <a name="createSample"></a> K vytvoření ukázkové aplikace, která používá knihovnu tříd  
  
1. V panelu nabídky zvolte **souboru**, **nový**, **nový projekt**.  
  
2. V seznamu šablon rozbalte **Visual C#** nebo **jazyka Visual Basic**a klikněte na tlačítko **Windows Store** uzlu.  
  
3. Zvolte **prázdnou aplikaci** šablony, pojmenujte projekt **ArithmeticUI**a klikněte na tlačítko **OK** tlačítko.  
  
4. V **Průzkumníka řešení**, otevřete místní nabídku **ArithmeticUI** projektu a klikněte na tlačítko **přidat**, **odkaz**.  
  
5. V seznamu typů odkazů, rozbalte **Windows**a klikněte na tlačítko **rozšíření**.  
  
6. V podokně podrobností vyberte **jednoduché matematické SDK** rozšíření.  
  
    Zobrazí se další informace o vaši sadu SDK. Můžete použít **. Další informace** odkaz k otevření http://www.msdn.microsoft.com, jak jste zadali v souboru SDKManifest.xml dříve v tomto návodu.  
  
7. V **správce odkazů** dialogové okno, vyberte **jednoduché matematické SDK** zaškrtněte políčko a klikněte na tlačítko **OK** tlačítko.  
  
8. V panelu nabídky zvolte **zobrazení**, **prohlížeče objektů**.  
  
9. V **Procházet** klikněte na položku **jednoduchých matematických**.  
  
     Nyní můžete prozkoumat, co je v sadě SDK.  
  
10. V **Průzkumníka řešení**, otevřete MainPage.xaml a jeho obsah nahraďte následujícím XAML:  
  
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml#1)]
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml#1)]  
  
11. Aktualizace MainPage.xaml.cs tak, aby odpovídala následující kód:  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml.cs#2)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml.vb#2)]  
  
12. Stisknutím klávesy F5 spusťte aplikaci.  
  
13. V aplikaci, zadejte jakékoli dvě čísla, zvolit operaci a klikněte na tlačítko **=** tlačítko.  
  
     Správný výsledek se zobrazí.  
  
    Úspěšně jste vytvořili a používat sady SDK rozšíření.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vytvoření sady SDK pomocí jazyka C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Návod: Vytvoření sady SDK pomocí jazyka JavaScript](http://msdn.microsoft.com/en-us/6195ff56-4a27-45fc-bd29-4b0451225f4b)   
 [Vytvoření sady SDK (Software Development Kit)](../extensibility/creating-a-software-development-kit.md)

