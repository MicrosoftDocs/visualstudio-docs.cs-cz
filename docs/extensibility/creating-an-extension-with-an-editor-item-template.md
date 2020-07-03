---
title: Vytvoření rozšíření pomocí šablony položky editoru | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91daa7e195435f33b93e6286cb19d820b4418d48
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903838"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>Vytvoření rozšíření pomocí šablony položky editoru
Šablony položek, které jsou součástí sady Visual Studio SDK, můžete použít k vytvoření základních rozšíření editoru, která přidávají do editoru třídění, doplňky a okraje. Šablony položek editoru jsou k dispozici pro projekty v jazyce Visual C# nebo Visual Basic VSIX.

## <a name="prerequisites"></a>Požadavky
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-classifier-extension"></a>Vytvoření rozšíření klasifikátoru
 Šablona položky klasifikátoru editoru vytvoří klasifikátor editoru, který barevně vybarví příslušný text (v tomto případě vše) v libovolném textovém souboru.

1. V dialogovém okně **Nový projekt** rozbalte položku **Visual C#** nebo **Visual Basic** a potom klikněte na možnost **rozšiřitelnost**. V podokně **šablony** vyberte **projekt VSIX**. Do pole **Název** zadejte `TestClassifier`. Klikněte na **OK**.

2. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Přidat**  >  **novou položku**. Přejít na uzel **rozšiřitelnosti** Visual C# a vyberte **klasifikátor editoru**. Ponechte výchozí název souboru (*EditorClassifier1.cs*).

3. Existují čtyři soubory kódu, a to následujícím způsobem:

    - *EditorClassifier1.cs* obsahuje `EditorClassifier1` třídu.

    - *EditorClassifier1ClassificationDefinition.cs* obsahuje `EditorClassifier1ClassificationDefinition` třídu.

    - *EditorClassifier1Format.cs* obsahuje `EditorClassifier1Format` třídu.

    - *EditorClassifier1Provider.cs* obsahuje `EditorClassifier1Provider` třídu.

4. Sestavte projekt a spusťte ladění. Zobrazí se experimentální instance aplikace Visual Studio.

     Pokud otevřete textový soubor, veškerý text bude podtržený na fialovém pozadí.

## <a name="create-a-text-relative-adornment-extension"></a>Vytvoření rozšíření pro vytváření relativních textů
 Šablona ovládacího prvku text v editoru vytvoří návrhově-relativní vzhled, který upraví všechny výskyty textového znaku ' a ' pomocí pole, které má červený obrys a modrého pozadí. Je relativní vzhledem k textu, protože pole vždycky překrývá znaky a, i když jsou přesunuté nebo přeformátované.

1. V dialogovém okně **Nový projekt** rozbalte položku **Visual C#** nebo **Visual Basic** a potom klikněte na možnost **rozšiřitelnost**. V podokně **šablony** vyberte **projekt VSIX**. Do pole **Název** zadejte `TestAdornment`. Klikněte na **OK**.

2. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Přidat**  >  **novou položku**. Přejít na uzel **rozšiřitelnosti** v jazyce Visual C# a vyberte možnost **Editor textu editoru**. Ponechte výchozí název souboru (*TextAdornment1.cs/VB*).

3. Existují dva soubory kódu, a to následujícím způsobem:

    - *TextAdornment1.cs* obsahuje `TextAdornment1` třídu.

    - *TextAdornment1TextViewCreationListener.cs* obsahuje `TextAdornment1TextViewCreationListener` třídu.

4. Sestavte projekt a spusťte ladění. Objeví se experimentální instance. Pokud otevřete textový soubor, jsou všechny znaky a v textu červeně zvýrazněny na modrém pozadí.

## <a name="create-a-viewport-relative-adornment-extension"></a>Vytvoření rozšíření pro vytváření relativních zobrazení
 Šablona doplňku pro zobrazení editoru vytvoří relativní vzhled, který přidá fialové pole, které má červený obrys v pravém horním rohu zobrazení.

> [!NOTE]
> Zobrazení **je oblast** aktuálně zobrazeného textu.

### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Vytvoření rozšíření pro rozšíření zobrazení pomocí šablony zobrazení editoru

1. V dialogovém okně **Nový projekt** rozbalte položku **Visual C#** nebo **Visual Basic** a potom klikněte na možnost **rozšiřitelnost**. V podokně **šablony** vyberte **projekt VSIX**. Do pole **Název** zadejte `ViewportAdornment`. Klikněte na **OK**.

2. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Přidat**  >  **novou položku**. Přejít na uzel **rozšiřitelnosti** Visual C# a výběr vizuálního **zobrazení editoru**. Ponechte výchozí název souboru (*ViewportAdornment1.cs/VB*).

3. Existují dva soubory kódu, a to následujícím způsobem:

    - *ViewportAdornment1.cs* obsahuje `ViewportAdornment1` třídu.

    - *ViewportAdornment1TextViewCreationListener.cs* obsahuje `ViewportAdornment1TextViewCreationListener` třídu

4. Sestavte projekt a spusťte ladění. Objeví se experimentální instance. Pokud vytvoříte nový textový soubor, v pravém horním rohu zobrazení se zobrazí fialové pole s červeným obrysem.

## <a name="create-a-margin-extension"></a>Vytvoření rozšíření marže
 Šablona okraje editoru vytvoří zelený okraj, který se zobrazí spolu se slovy **Hello World!* pod vodorovným posuvníkem.

### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Vytvoření rozšíření marže pomocí šablony okraje editoru

1. V dialogovém okně **Nový projekt** rozbalte položku **Visual C#** nebo **Visual Basic** a potom klikněte na možnost **rozšiřitelnost**. V podokně **šablony** vyberte **projekt VSIX**. Do pole **Název** zadejte `MarginExtension`. Klikněte na **OK**.

2. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Přidat**  >  **novou položku**. Přejít do uzlu **rozšiřitelnost** v jazyce Visual C# a vybrat **okraj editoru**. Ponechte výchozí název souboru (EditorMargin1.cs/vb).

3. Existují dva soubory kódu, a to následujícím způsobem:

    - *EditorMargin1.cs* obsahuje `EditorMargin1` třídu.

    - *EditorMargin1Factory.cs* obsahuje `EditorMargin1Factory` třídu.

4. Sestavte tento projekt a spusťte ladění. Objeví se experimentální instance. Pokud otevřete textový soubor, zobrazí se pod vodorovným posuvníkem zelený okraj, který obsahuje slova **Hello EditorMargin1** .

## <a name="see-also"></a>Viz také
- [Rozšiřovací body služby jazyka a editoru](../extensibility/language-service-and-editor-extension-points.md)
