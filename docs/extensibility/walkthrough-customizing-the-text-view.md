---
title: 'Návod: přizpůsobení zobrazení textu | Microsoft Docs'
description: V tomto návodu se dozvíte, jak upravit zobrazení textu změnou kterékoli z několika vlastností v jeho mapě formátu editoru.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 17aa8644fc4823df5b68378e9045fa190980306d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080304"
---
# <a name="walkthrough-customize-the-text-view"></a>Návod: přizpůsobení zobrazení textu
Změnou kterékoli z následujících vlastností v její mapě formátu editoru můžete upravit zobrazení textu:

- Okraj indikátoru

- Vložení blikajícího kurzoru

- Přepsat blikající kurzor

- Vybraný text

- Neaktivní vybraný text (tj. vybraný text, u kterého došlo ke ztrátě fokusu)

- Viditelné prázdné znaky

## <a name="prerequisites"></a>Požadavky
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Vytvořit projekt MEF

1. Vytvoří projekt VSIX v jazyce C#. (V dialogovém okně **Nový projekt** vyberte **Visual C#/rozšiřitelnost** a potom **projekt VSIX**.) Pojmenujte řešení `ViewPropertyTest` .

2. Přidejte do projektu šablonu položky klasifikátoru editoru. Další informace naleznete v tématu [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Odstraňte existující soubory třídy.

## <a name="define-the-content-type"></a>Definovat typ obsahu

1. Přidejte soubor třídy a pojmenujte ho `ViewPropertyModifier` .

2. Přidejte následující `using` direktivy:

    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]

3. Deklarujte třídu s názvem `TestViewCreationListener` , která dědí z <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> . Exportujte tuto třídu s následujícími atributy:

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> k určení typu obsahu, na který se bude tento naslouchací proces vztahovat.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> pro určení role tohoto naslouchacího procesu.

     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]

4. V této třídě importujte <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> .

    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]

## <a name="change-the-view-properties"></a>Změnit vlastnosti zobrazení

1. Nastavte <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodu tak, aby se vlastnosti zobrazení po otevření zobrazení změnily. Chcete-li provést změnu, nejprve vyhledejte odpovídající <xref:System.Windows.ResourceDictionary> aspekty zobrazení, které chcete najít. Pak změňte odpovídající vlastnost ve slovníku prostředků a nastavte vlastnosti. Dávkujte volání <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> metody voláním <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> metody před nastavením vlastností a poté <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> po nastavení vlastností.

     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]

## <a name="build-and-test-the-code"></a>Sestavení a testování kódu

1. Sestavte řešení.

     Při spuštění tohoto projektu v ladicím programu se spustí druhá instance sady Visual Studio.

2. Vytvořte textový soubor a zadejte nějaký text.

    - Stříška pro vložení by měla být fialová a měla by být tyrkysová stříška.

    - Okraj indikátoru (nalevo od textového zobrazení) by měl být světle zelený.

3. Vyberte text, který jste zadali. Barva vybraného textu by měla být světle růžová.

4. Když je vybraný text, klikněte kamkoli mimo textové okno. Barva vybraného textu by měla být tmavě růžová.

5. Zapněte viditelné prázdné znaky. (V nabídce **Upravit** přejděte na položku **Upřesnit** a potom klikněte na možnost **Zobrazit prázdné znaky**). Zadejte v textu některé tabulátory. Měly by se zobrazit červené šipky, které reprezentují karty.

## <a name="see-also"></a>Viz také
- [Rozšiřovací body služby jazyka a editoru](../extensibility/language-service-and-editor-extension-points.md)
