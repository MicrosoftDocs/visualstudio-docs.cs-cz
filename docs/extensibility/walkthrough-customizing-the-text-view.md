---
title: 'Návod: Přizpůsobení zobrazení textu | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d99f9201761bbe079c34ccf61339158863509dd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697459"
---
# <a name="walkthrough-customize-the-text-view"></a>Návod: Přizpůsobení zobrazení textu
Zobrazení textu můžete přizpůsobit úpravou některé z následujících vlastností v mapě ve formátu editoru:

- Ukazatel marže

- Insertion stříška

- Přepsat stříšku

- Vybraný text

- Neaktivní vybraný text (to znamená vybraný text, který ztratil fokus)

- Viditelné prázdné znaky

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Vytvoření projektu MEF

1. Vytvořte projekt C# VSIX. (V dialogovém okně **Nový projekt** vyberte možnost **Vizuální C# / Rozšiřitelnost**a potom **v six projectu**.) Pojmenujte `ViewPropertyTest`řešení .

2. Přidejte do projektu šablonu položky třídění editoru. Další informace naleznete [v tématu Vytvoření rozšíření se šablonou položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Odstraňte existující soubory tříd.

## <a name="define-the-content-type"></a>Definování typu obsahu

1. Přidejte soubor třídy `ViewPropertyModifier`a pojmenujte jej .

2. Přidejte `using` následující direktivy:

    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]

3. Deklarujte `TestViewCreationListener` třídu <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>s názvem, která dědí z . Exportujte tuto třídu s následujícími atributy:

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>určit typ obsahu, na který se tento naslouchací proces vztahuje.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>určit roli tohoto naslouchací proces.

     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]

4. V této třídě <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>importujte .

    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]

## <a name="change-the-view-properties"></a>Změna vlastností zobrazení

1. Nastavte metodu <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> tak, aby se vlastnosti zobrazení při otevření zobrazení změnily. Chcete-li provést změnu, nejprve <xref:System.Windows.ResourceDictionary> najděte, který odpovídá aspektu zobrazení, který chcete najít. Potom změňte příslušnou vlastnost ve slovníku prostředků a nastavte vlastnosti. Dávky volání <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> metody voláním <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> metody před nastavením vlastnosti a potom <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> po nastavení vlastností.

     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]

## <a name="build-and-test-the-code"></a>Sestavení a testování kódu

1. Sestavte řešení.

     Při spuštění tohoto projektu v ladicím programu je spuštěna druhá instance sady Visual Studio.

2. Vytvořte textový soubor a zadejte nějaký text.

    - Insertion stříška by měla být purpurová a přepsat stříška by měla být tyrkysová.

    - Okraj ukazatele (vlevo od zobrazení textu) by měl být světle zelený.

3. Vyberte text, který jste zadali. Barva vybraného textu by měla být světle růžová.

4. Když je text vybraný, klepněte na libovolné místo mimo textové okno. Barva vybraného textu by měla být tmavě růžová.

5. Zapněte viditelné prázdné znaky. (V nabídce **Úpravy** přejděte na **Upřesnit** a klikněte na **Zobrazit prázdné místo).** Do textu zadejte některé karty. Měly by být zobrazeny červené šipky, které představují karty.

## <a name="see-also"></a>Viz také
- [Jazykové služby a rozšiřující body editoru](../extensibility/language-service-and-editor-extension-points.md)
