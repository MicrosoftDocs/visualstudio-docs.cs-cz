---
title: Vytváření rozšíření pomocí šablony položky editoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a13c62d9fadfe105bd8e645ba6e7758c2b3195a3
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500899"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>Vytváření rozšíření pomocí šablony položky editoru
Můžete použít šablony položek, které jsou zahrnuty v sadě Visual Studio SDK vytvořit rozšíření základního editoru, které aplikacím dodávají třídění, vylepšení a okraje editoru. Šablony položky editoru jsou k dispozici pro projekty Visual C# nebo Visual Basic VSIX.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-classifier-extension"></a>Jak vytvořit rozšíření třídění  
 Šablony položky editoru třídění vytvoří editor klasifikátor, který barvy odpovídající text (v tomto případě všechno, co) v jakékoli textový soubor.  
  
1.  V **nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic** a potom klikněte na tlačítko **rozšiřitelnost**. V **šablony** vyberte **projekt VSIX**. V **název** zadejte `TestClassifier`. Klikněte na tlačítko **OK**.  
  
2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte **přidat** > **nová položka**. Přejděte do aplikace Visual C# **rozšiřitelnost** uzel a vyberte možnost **Editor třídění**. Ponechte výchozí název souboru (*EditorClassifier1.cs*).  
  
3.  Existují čtyři soubory kódu, následujícím způsobem:  
  
    -   *EditorClassifier1.cs* obsahuje `EditorClassifier1` třídy.  
  
    -   *EditorClassifier1ClassificationDefinition.cs* obsahuje `EditorClassifier1ClassificationDefinition` třídy.  
  
    -   *EditorClassifier1Format.cs* obsahuje `EditorClassifier1Format` třídy.  
  
    -   *EditorClassifier1Provider.cs* obsahuje `EditorClassifier1Provider` třídy.  
  
4.  Sestavte projekt a spusťte ladění. Experimentální instanci sady Visual Studio se zobrazí.  
  
     Pokud otevřete textový soubor, je celý text podtržené fialového pozadí.  
  
## <a name="create-a-text-relative-adornment-extension"></a>Vytvoření dalších úprav textu relativní rozšíření  
 Šablona dalších úprav editoru textu vytvoří dalších úprav textu relativní, který upraví všechny výskyty znaků textu "a" s použitím pole, které má červené ohraničení a modrým pozadím. Je text relativní vzhledem k tomu, pole vždy překrytí "a" znaky, i když se přesunout nebo přeformátovali.  
  
1.  V **nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic** a potom klikněte na tlačítko **rozšiřitelnost**. V **šablony** vyberte **projekt VSIX**. V **název** zadejte `TestAdornment`. Klikněte na tlačítko **OK**.  
  
2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte **přidat** > **nová položka**. Přejděte do aplikace Visual C# **rozšiřitelnost** uzel a vyberte možnost **dalších úprav editoru textu**. Ponechte výchozí název souboru (*TextAdornment1.cs/vb*).  
  
3.  Existují dva soubory kódu, následujícím způsobem:  
  
    -   *TextAdornment1.cs* obsahuje `TextAdornment1` třídy.  
  
    -   *TextAdornment1TextViewCreationListener.cs* obsahuje `TextAdornment1TextViewCreationListener` třídy.  
  
4.  Sestavte projekt a spusťte ladění. Zobrazí se experimentální instance. Pokud otevřete textový soubor, jsou uvedeny všechny "a" znaky v textu v červené, modré pozadí.  
  
## <a name="create-a-viewport-relative-adornment-extension"></a>Vytvoření grafického doplňku zobrazení relativní rozšíření  
 Šablona grafického doplňku zobrazení editoru vytvoří relativní k zobrazení dalších úprav, který přidá fialového pole, která má červené ohraničení na pravém horním rohu zobrazení.  
  
> [!NOTE]
>  **Zobrazení** je oblast, která je právě otevřeno zobrazení textu.  
  
### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Chcete-li vytvořit rozšíření grafického doplňku zobrazení s použitím šablony grafického doplňku zobrazení editoru  
  
1.  V **nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic** a potom klikněte na tlačítko **rozšiřitelnost**. V **šablony** vyberte **projekt VSIX**. V **název** zadejte `ViewportAdornment`. Klikněte na tlačítko **OK**.  
  
2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte **přidat** > **nová položka**. Přejděte do aplikace Visual C# **rozšiřitelnost** uzel a vyberte možnost **grafického doplňku zobrazení editoru**. Ponechte výchozí název souboru (*ViewportAdornment1.cs/vb*).  
  
3.  Existují dva soubory kódu, následujícím způsobem:  
  
    -   *ViewportAdornment1.cs* obsahuje `ViewportAdornment1` třídy.  
  
    -   *ViewportAdornment1TextViewCreationListener.cs* obsahuje `ViewportAdornment1TextViewCreationListener` třídy  
  
4.  Sestavte projekt a spusťte ladění. Zobrazí se experimentální instance. Pokud vytvoříte nový textový soubor, zobrazí se v pravém horním rohu zobrazení fialového pole, která má červené ohraničení.  
  
## <a name="create-a-margin-extension"></a>Jak vytvořit rozšíření okraj  
 Šablona okraj editoru vytvoří zelené okraj, který se zobrazí spolu s slova **Hello world!* pod vodorovný posuvník.  
  
### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Chcete-li vytvořit okraj rozšíření pomocí šablony okraj editoru  
  
1.  V **nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic** a potom klikněte na tlačítko **rozšiřitelnost**. V **šablony** vyberte **projekt VSIX**. V **název** zadejte `MarginExtension`. Klikněte na tlačítko **OK**.  
  
2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte **přidat** > **nová položka**. Přejděte do aplikace Visual C# **rozšiřitelnost** uzel a vyberte možnost **okraj editoru**. Ponechte výchozí název souboru (EditorMargin1.cs/vb).  
  
3.  Existují dva soubory kódu, následujícím způsobem:  
  
    -   *EditorMargin1.cs* obsahuje `EditorMargin1` třídy.  
  
    -   *EditorMargin1Factory.cs* obsahuje `EditorMargin1Factory` třídy.  
  
4.  Tento projekt sestavit a spustit ladění. Zobrazí se experimentální instance. Pokud otevřete textový soubor, zelenou okraj, který má slova **Hello EditorMargin1** se zobrazí pod vodorovný posuvník.  
  
## <a name="see-also"></a>Viz také:  
 [Jazykové služby a editor Rozšiřovací body](../extensibility/language-service-and-editor-extension-points.md)
