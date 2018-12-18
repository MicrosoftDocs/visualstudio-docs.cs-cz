---
title: 'Návod: Přizpůsobení zobrazení textu | Dokumentace Microsoftu'
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
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 38cbd0117f5f49666ee5da42d0f60dadf451ffda
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781813"
---
# <a name="walkthrough-customizing-the-text-view"></a>Návod: Přizpůsobení zobrazení textu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení textu lze přizpůsobit úpravou některý z následujících vlastností v jeho editor formátu mapy:  
  
-   Okraj indikátoru  
  
-   Blikající kurzor o vložení  
  
-   Přepsat blikajícího kurzoru  
  
-   Vybraný text  
  
-   Neaktivní vybraný text (to znamená, že vybraný text, který ztratil fokus)  
  
-   Viditelné prázdné znaky  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Vytvoření projektu rozhraní MEF  
  
1.  Vytvořte projekt VSIX C#. (V **nový projekt** dialogového okna, vyberte **Visual C# / rozšíření**, pak **projekt VSIX**.) Pojmenujte řešení `ViewPropertyTest`.  
  
2.  Přidejte do projektu šablony položky editoru třídění. Další informace najdete v tématu [vytváření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Odstraníte existující soubory tříd.  
  
## <a name="defining-the-content-type"></a>Definování typu obsahu  
  
1. Přidejte soubor třídy a pojmenujte ho `ViewPropertyModifier`.  
  
2. Přidejte následující `using` direktivy:  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#1)]
    [!code-vb[VSSDKViewPropertyTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#1)]  
  
3. Deklarovat třídu s názvem `TestViewCreationListener` , která dědí z <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Exportujte tuto třídu s následujícími atributy:  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Chcete-li určit typ obsahu, ke kterému se vztahuje tímto naslouchacím procesem.  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> zadání role tohoto naslouchacího procesu.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#2)]
     [!code-vb[VSSDKViewPropertyTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#2)]  
  
4. V této třídě import <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#3)]
    [!code-vb[VSSDKViewPropertyTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#3)]  
  
## <a name="changing-the-view-properties"></a>Změna vlastností zobrazení  
  
1.  Implementace <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodu tak, aby se při otevření zobrazení změní zobrazit vlastnosti. Aby se změna nejprve vyhledat <xref:System.Windows.ResourceDictionary> , který odpovídá aspekt zobrazení, které chcete najít. Poté změňte příslušné vlastnosti ve slovníku prostředků a nastavte vlastnosti. Batch volání <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> metoda voláním <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> metoda před nastavením vlastnosti a pak <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> po nastavení vlastnosti.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#4)]
     [!code-vb[VSSDKViewPropertyTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#4)]  
  
## <a name="building-and-testing-the-code"></a>Vytváření a testování kódu  
  
1.  Sestavte řešení.  
  
     Při spuštění tohoto projektu v ladicím programu, je vytvořena instance druhou instanci aplikace Visual Studio.  
  
2.  Vytvořte textový soubor a zadejte nějaký text.  
  
    -   Blikající kurzor o vložení by měla být purpurová a přepsat blikající kurzor by měl být tyrkysová.  
  
    -   Okraj indikátoru (nalevo od zobrazení textu) by měl být světle zelená.  
  
3.  Vyberte text, který jste právě zadali. Barva vybraný text by měl být světle růžová.  
  
4.  Když je vybraný text, klikněte kamkoli mimo časový interval pro text. Tmavě růžový by měl být barvu vybraného textu.  
  
5.  Zapněte viditelné prázdné znaky. (Na **upravit** nabídky, přejděte k **Upřesnit** a potom klikněte na tlačítko **zobrazení prázdných**). Zadejte text, některé karty. Červené šipky, které představují karet má být zobrazena.  
  
## <a name="see-also"></a>Viz také  
 [Rozšiřovací body služeb jazyka a editoru](../extensibility/language-service-and-editor-extension-points.md)

