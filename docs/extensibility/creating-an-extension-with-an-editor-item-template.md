---
title: Vytvoření rozšíření se šablonou položky editoru | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ac19d99bf75c79ad011bfd0d5a56ecf3880b100
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739501"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>Vytvoření rozšíření se šablonou položky editoru
Šablony položek, které jsou součástí sady Visual Studio SDK, můžete použít k vytvoření základních rozšíření editoru, která do editoru přidávají klasifikátory, vylepšení a okraje. Šablony položek editoru jsou k dispozici pro projekty Visual C# nebo Visual Basic VSIX.

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-classifier-extension"></a>Vytvoření rozšíření třídění
 Šablona položky třídění editoru vytvoří klasifikátor editoru, který vybarví příslušný text (v tomto případě vše) v libovolném textovém souboru.

1. V dialogovém okně **Nový projekt** rozbalte **položku Visual C#** nebo **Visual Basic** a klepněte na tlačítko **Rozšiřitelnost**. V podokně **Šablony** vyberte **vsix project .** Do pole **Název** zadejte `TestClassifier`. Klikněte na tlačítko **OK**.

2. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu a vyberte **přidat** > **novou položku**. Přejděte na uzel **rozšiřitelnost** jazyka Visual C# a vyberte **klasifikátor editoru**. Ponechte výchozí název souboru (*EditorClassifier1.cs*).

3. Existují čtyři soubory kódu, takto:

    - *EditorClassifier1.cs* obsahuje `EditorClassifier1` třídu.

    - *EditorClassifier1ClassificationDefinition.cs* obsahuje `EditorClassifier1ClassificationDefinition` třídu.

    - *EditorClassifier1Format.cs* obsahuje `EditorClassifier1Format` třídu.

    - *EditorClassifier1Provider.cs* obsahuje `EditorClassifier1Provider` třídu.

4. Sestavení projektu a začít ladění. Zobrazí se experimentální instance sady Visual Studio.

     Pokud otevřete textový soubor, bude celý text podtržen na fialovém pozadí.

## <a name="create-a-text-relative-adornment-extension"></a>Vytvoření rozšíření vylepšení relativního textu
 Editor text vylepšení šablony vytvoří text relativní vylepšení, které zdobí všechny instance znaku textu 'a' pomocí pole, které má červený obrys a modré pozadí. Je relativní k textu, protože pole vždy překryje znaky 'a', i když jsou přesunuty nebo přeformátovány.

1. V dialogovém okně **Nový projekt** rozbalte **položku Visual C#** nebo **Visual Basic** a klepněte na tlačítko **Rozšiřitelnost**. V podokně **Šablony** vyberte **vsix project .** Do pole **Název** zadejte `TestAdornment`. Klikněte na tlačítko **OK**.

2. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu a vyberte **přidat** > **novou položku**. Přejděte na uzel **rozšiřitelnost** jazyka Visual C# a vyberte **vylepšení textu editoru**. Ponechte výchozí název souboru (*TextAdornment1.cs/vb*).

3. Existují dva soubory kódu, takto:

    - *TextAdornment1.cs* obsahuje `TextAdornment1` třídu.

    - *TextAdornment1TextViewCreationListener.cs* obsahuje `TextAdornment1TextViewCreationListener` třídu.

4. Sestavení projektu a začít ladění. Zobrazí se experimentální instance. Pokud otevřete textový soubor, všechny znaky "a" v textu budou na modrém pozadí označeny červeně.

## <a name="create-a-viewport-relative-adornment-extension"></a>Vytvoření rozšíření vylepšení relativního vzhledu
 Šablona Vylepšení výřezu editoru vytvoří vylepšení relativní výřez, který přidá fialové pole, které má červený obrys do pravého horního rohu výřezu.

> [!NOTE]
> **Výřez** je oblast aktuálně zobrazeného zobrazení textu.

### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Vytvoření rozšíření vylepšení výřezu pomocí šablony Editor Viewport Adornment

1. V dialogovém okně **Nový projekt** rozbalte **položku Visual C#** nebo **Visual Basic** a klepněte na tlačítko **Rozšiřitelnost**. V podokně **Šablony** vyberte **vsix project .** Do pole **Název** zadejte `ViewportAdornment`. Klikněte na tlačítko **OK**.

2. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu a vyberte **přidat** > **novou položku**. Přejděte na uzel **rozšiřitelnost** jazyka Visual C# a vyberte **vylepšení výřezu editoru**. Ponechte výchozí název souboru (*ViewportAdornment1.cs/vb*).

3. Existují dva soubory kódu, takto:

    - *ViewportAdornment1.cs* obsahuje `ViewportAdornment1` třídu.

    - *ViewportAdornment1TextViewCreationListener.cs* obsahuje `ViewportAdornment1TextViewCreationListener` třídu

4. Sestavení projektu a začít ladění. Zobrazí se experimentální instance. Pokud vytvoříte nový textový soubor, zobrazí se v pravém horním rohu výřezu fialový rámeček s červeným obrysem.

## <a name="create-a-margin-extension"></a>Vytvoření rozšíření marže
 Šablona Okraje editoru vytvoří zelený okraj, který se zobrazí spolu se slovy **Hello world!* pod vodorovným posuvníkem.

### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Vytvoření rozšíření okrajů pomocí šablony Okraje editoru

1. V dialogovém okně **Nový projekt** rozbalte **položku Visual C#** nebo **Visual Basic** a klepněte na tlačítko **Rozšiřitelnost**. V podokně **Šablony** vyberte **vsix project .** Do pole **Název** zadejte `MarginExtension`. Klikněte na tlačítko **OK**.

2. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu a vyberte **přidat** > **novou položku**. Přejděte na uzel **rozšiřitelnost** jazyka Visual C# a vyberte **okraj editoru**. Ponechte výchozí název souboru (EditorMargin1.cs/vb).

3. Existují dva soubory kódu, takto:

    - *EditorMargin1.cs* obsahuje `EditorMargin1` třídu.

    - *EditorMargin1Factory.cs* obsahuje `EditorMargin1Factory` třídu.

4. Sestavení tohoto projektu a začít ladění. Zobrazí se experimentální instance. Pokud otevřete textový soubor, zelený okraj, který má slova **Hello EditorMargin1** se zobrazí pod vodorovným posuvníkem.

## <a name="see-also"></a>Viz také
- [Jazykové služby a rozšiřující body editoru](../extensibility/language-service-and-editor-extension-points.md)
