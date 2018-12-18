---
title: 'Návod: Přizpůsobení zobrazení textu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c328925fd558e01138354427a80db7a692753710
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924912"
---
# <a name="walkthrough-customize-the-text-view"></a>Návod: Přizpůsobení zobrazení textu
Zobrazení textu lze přizpůsobit úpravou některý z následujících vlastností v jeho editor formátu mapy:  
  
-   Okraj indikátoru  
  
-   Blikající kurzor o vložení  
  
-   Přepsat blikajícího kurzoru  
  
-   Vybraný text  
  
-   Neaktivní vybraný text (to znamená, že vybraný text, který ztratil fokus)  
  
-   Viditelné prázdné znaky  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnutý jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-mef-project"></a>Vytvořit projekt rozhraní MEF  
  
1.  Vytvořte projekt VSIX C#. (V **nový projekt** dialogového okna, vyberte **Visual C# / rozšíření**, pak **projekt VSIX**.) Pojmenujte řešení `ViewPropertyTest`.  
  
2.  Přidejte do projektu šablony položky editoru třídění. Další informace najdete v tématu [vytváření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Odstraníte existující soubory tříd.  
  
## <a name="define-the-content-type"></a>Typ obsahu definovat  
  
1. Přidejte soubor třídy a pojmenujte ho `ViewPropertyModifier`.  
  
2. Přidejte následující `using` direktivy:  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3. Deklarovat třídu s názvem `TestViewCreationListener` , která dědí z <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Exportujte tuto třídu s následujícími atributy:  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Chcete-li určit typ obsahu, ke kterému se vztahuje tímto naslouchacím procesem.  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> zadání role tohoto naslouchacího procesu.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4. V této třídě import <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="change-the-view-properties"></a>Změna vlastností zobrazení  
  
1.  Nastavit <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodu tak, aby se při otevření zobrazení změní zobrazit vlastnosti. Aby se změna nejprve vyhledat <xref:System.Windows.ResourceDictionary> , který odpovídá aspekt zobrazení, které chcete najít. Potom změnit příslušné vlastnosti ve slovníku prostředků a nastavte vlastnosti. Batch volání <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> metoda voláním <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> metoda před nastavením vlastnosti a pak <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> po nastavení vlastnosti.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="build-and-test-the-code"></a>Vytváření a testování kódu  
  
1.  Sestavte řešení.  
  
     Při spuštění tohoto projektu v ladicím programu se spustí druhé instanci aplikace Visual Studio.  
  
2.  Vytvořte textový soubor a zadejte nějaký text.  
  
    -   Blikající kurzor o vložení by měla být purpurová a přepsat blikající kurzor by měl být tyrkysová.  
  
    -   Okraj indikátoru (nalevo od zobrazení textu) by měl být světle zelená.  
  
3.  Vyberte text, který jste zadali. Barva vybraný text by měl být světle růžová.  
  
4.  Když je vybraný text, klikněte kamkoli mimo časový interval pro text. Tmavě růžový by měl být barvu vybraného textu.  
  
5.  Zapněte viditelné prázdné znaky. (Na **upravit** nabídky, přejděte k **Upřesnit** a potom klikněte na tlačítko **zobrazení prázdných**). Zadejte text, některé karty. Červené šipky, které představují karet má být zobrazena.  
  
## <a name="see-also"></a>Viz také:  
 [Jazykové služby a editor Rozšiřovací body](../extensibility/language-service-and-editor-extension-points.md)