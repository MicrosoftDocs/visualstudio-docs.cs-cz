---
title: Vytváření rozšíření pomocí šablony položky editoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab22549550c0564f7e27b88adae4627f24ab9acc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772739"
---
# <a name="creating-an-extension-with-an-editor-item-template"></a>Vytváření rozšíření pomocí šablony položky editoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít šablony položek, které jsou zahrnuty v sadě Visual Studio SDK vytvořit rozšíření základního editoru, které aplikacím dodávají třídění, vylepšení a okraje editoru. Šablony položky editoru jsou k dispozici pro projekty Visual C# nebo Visual Basic VSIX.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-classifier-extension"></a>Vytváření rozšíření pro třídění  
 Šablony položky editoru třídění vytvoří editor klasifikátor, který barvy odpovídající text (v tomto případě všechno, co) v jakékoli textový soubor.  
  
1.  V **nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic** a potom klikněte na tlačítko **rozšiřitelnost**. V **šablony** vyberte **projekt VSIX**. V **název** zadejte `TestClassifier`. Klikněte na tlačítko **OK**.  
  
2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte **Add / nová položka**. Přejděte do aplikace Visual C# **rozšiřitelnost** uzel a vyberte možnost **Editor třídění**. Ponechte výchozí název souboru (EditorClassifier1.cs).  
  
3.  Existují tři soubory kódu, následujícím způsobem:  
  
    -   Obsahuje EditorClassifier1.cs `EditorClassifier1` třídy.  
  
    -   Obsahuje EditorClassifier1ClassificationDefinition.cs `OEditorClassifier1ClassificationDefinition` třídy.  
  
    -   Obsahuje EditorClassifier1Format.cs `EditorClassifier1Format` třídy.  
  
    -   Obsahuje EditorClassifier1Provider.cs `EditorClassifier1Provider` třídy.  
  
4.  Sestavte projekt a spusťte ladění. Experimentální instanci sady Visual Studio se zobrazí.  
  
     Pokud otevřete textový soubor, je celý text podtržené fialového pozadí.  
  
## <a name="creating-a-text-relative-adornment-extension"></a>Vytvoření dalších úprav textu relativní rozšíření  
 Šablona dalších úprav editoru textu vytvoří dalších úprav textu relativní, který upraví všechny výskyty znaků textu "a" s použitím pole, které má červené ohraničení a modrým pozadím. Je text relativní vzhledem k tomu, pole vždy překrytí "a" znaky, i když se přesunout nebo přeformátovali.  
  
1.  V **nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic** a potom klikněte na tlačítko **rozšiřitelnost**. V **šablony** vyberte **projekt VSIX**. V **název** zadejte `TestAdornment`. Klikněte na tlačítko **OK**.  
  
2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte **Add / nová položka**. Přejděte do aplikace Visual C# **rozšiřitelnost** uzel a vyberte možnost **dalších úprav editoru textu**. Ponechte výchozí název souboru (TextAdornment1.cs/vb).  
  
3.  Existují dva soubory kódu, následujícím způsobem:  
  
    -   Obsahuje TextAdornment1.cs `TextAdornment1` třídy.  
  
    -   obsahuje extAdornment1TextViewCreationListener.cs `TextAdornment1TextViewCreationListener` třídy.  
  
4.  Sestavte projekt a spusťte ladění. Zobrazí se experimentální instance. Pokud otevřete textový soubor, jsou uvedeny všechny "a" znaky v textu v červené, modré pozadí.  
  
## <a name="creating-a-viewport-relative-adornment-extension"></a>Vytvoření grafického doplňku zobrazení relativní rozšíření  
 Šablona grafického doplňku zobrazení editoru vytvoří relativní k zobrazení dalších úprav, který přidá fialového pole, která má červené ohraničení na pravém horním rohu zobrazení.  
  
> [!NOTE]
>  *Zobrazení* je oblast, která je právě otevřeno zobrazení textu.  
  
#### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Chcete-li vytvořit rozšíření grafického doplňku zobrazení s použitím šablony grafického doplňku zobrazení editoru  
  
1.  V **nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic** a potom klikněte na tlačítko **rozšiřitelnost**. V **šablony** vyberte **projekt VSIX**. V **název** zadejte `ViewportAdornment`. Klikněte na tlačítko **OK**.  
  
2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte **Add / nová položka**. Přejděte do aplikace Visual C# **rozšiřitelnost** uzel a vyberte možnost **grafického doplňku zobrazení editoru**. Ponechte výchozí název souboru (ViewportAdornment1.cs/vb).  
  
3.  Existují dva soubory kódu, následujícím způsobem:  
  
    -   Obsahuje ViewportAdornment1.cs `ViewportAdornment1` třídy.  
  
    -   Obsahuje ViewportAdornment1TextViewCreationListener.cs `ViewportAdornment1TextViewCreationListener` třídy  
  
4.  Sestavte projekt a spusťte ladění. Zobrazí se experimentální instance. Pokud vytvoříte nový textový soubor, zobrazí se v pravém horním rohu zobrazení fialového pole, která má červené ohraničení.  
  
## <a name="creating-a-margin-extension"></a>Vytváření rozšíření pro rozpětí  
 Šablona okraj editoru vytvoří zelené okraj, který se zobrazí spolu s slova "Hello world!" pod vodorovný posuvník.  
  
#### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Chcete-li vytvořit okraj rozšíření pomocí šablony okraj editoru  
  
1.  V **nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic** a potom klikněte na tlačítko **rozšiřitelnost**. V **šablony** vyberte **projekt VSIX**. V **název** zadejte `MarginExtension`. Klikněte na tlačítko **OK**.  
  
2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte **Add / nová položka**. Přejděte do aplikace Visual C# **rozšiřitelnost** uzel a vyberte možnost **grafického doplňku zobrazení editoru**. Ponechte výchozí název souboru (EditorMargin1.cs/vb).  
  
3.  Existují dva soubory kódu, následujícím způsobem:  
  
    -   Obsahuje EditorMargin1.cs `EditorMargin1` třídy.  
  
    -   Obsahuje EditorMargin1Factory.cs `EditorMargin1Factory` třídy.  
  
4.  Tento projekt sestavit a spustit ladění. Zobrazí se experimentální instance. Pokud otevřete textový soubor, zobrazí se zelené okraj obsahující slova "Hello EditorMargin1" níže vodorovný posuvník.  
  
## <a name="see-also"></a>Viz také  
 [Rozšiřovací body služeb jazyka a editoru](../extensibility/language-service-and-editor-extension-points.md)

