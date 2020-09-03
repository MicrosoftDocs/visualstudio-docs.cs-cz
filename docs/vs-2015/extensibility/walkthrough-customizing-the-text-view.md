---
title: 'Návod: přizpůsobení zobrazení textu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e96bb177d3cfa90b2c80304eabfd93d1bea76d5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202027"
---
# <a name="walkthrough-customizing-the-text-view"></a>Návod: Přizpůsobení zobrazení textu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Změnou kterékoli z následujících vlastností v její mapě formátu editoru můžete upravit zobrazení textu:  
  
- Okraj indikátoru  
  
- Vložení blikajícího kurzoru  
  
- Přepsat blikající kurzor  
  
- Vybraný text  
  
- Neaktivní vybraný text (tj. vybraný text, který ztratil fokus)  
  
- Viditelné prázdné znaky  
  
## <a name="prerequisites"></a>Předpoklady  
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Vytvoření projektu MEF  
  
1. Vytvoří projekt VSIX v jazyce C#. (V dialogovém okně **Nový projekt** vyberte **Visual C#/rozšiřitelnost**a potom **projekt VSIX**.) Pojmenujte řešení `ViewPropertyTest` .  
  
2. Přidejte do projektu šablonu položky klasifikátoru editoru. Další informace naleznete v tématu [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Odstraňte existující soubory třídy.  
  
## <a name="defining-the-content-type"></a>Definování typu obsahu  
  
1. Přidejte soubor třídy a pojmenujte ho `ViewPropertyModifier` .  
  
2. Přidejte následující `using` direktivy:  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#1)]
    [!code-vb[VSSDKViewPropertyTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#1)]  
  
3. Deklarujte třídu s názvem `TestViewCreationListener` , která dědí z <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> . Exportujte tuto třídu s následujícími atributy:  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> k určení typu obsahu, na který se bude tento naslouchací proces vztahovat.  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> pro určení role tohoto naslouchacího procesu.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#2)]
     [!code-vb[VSSDKViewPropertyTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#2)]  
  
4. V této třídě importujte <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> .  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#3)]
    [!code-vb[VSSDKViewPropertyTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#3)]  
  
## <a name="changing-the-view-properties"></a>Změna vlastností zobrazení  
  
1. Implementujte <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodu tak, aby se vlastnosti zobrazení po otevření zobrazení změnily. Chcete-li provést změnu, nejprve vyhledejte odpovídající <xref:System.Windows.ResourceDictionary> aspekty zobrazení, které chcete najít. Pak změňte příslušnou vlastnost ve slovníku prostředků a nastavte vlastnosti. Dávkujte volání <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> metody voláním <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> metody před nastavením vlastností a poté <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> po nastavení vlastností.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#4)]
     [!code-vb[VSSDKViewPropertyTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#4)]  
  
## <a name="building-and-testing-the-code"></a>Sestavování a testování kódu  
  
1. Sestavte řešení.  
  
     Při spuštění tohoto projektu v ladicím programu je vytvořena instance druhé instance aplikace Visual Studio.  
  
2. Vytvořte textový soubor a zadejte nějaký text.  
  
    - Stříška pro vložení by měla být fialová a měla by být tyrkysová stříška.  
  
    - Okraj indikátoru (nalevo od textového zobrazení) by měl být světle zelený.  
  
3. Vyberte text, který jste právě zadali. Barva vybraného textu by měla být světle růžová.  
  
4. Když je vybraný text, klikněte kamkoli mimo textové okno. Barva vybraného textu by měla být tmavě růžová.  
  
5. Zapněte viditelné prázdné znaky. (V nabídce **Upravit** přejděte na položku **Upřesnit** a potom klikněte na možnost **Zobrazit prázdné znaky**). Zadejte v textu některé tabulátory. Měly by se zobrazit červené šipky, které reprezentují karty.  
  
## <a name="see-also"></a>Viz také  
 [Rozšiřovací body služeb jazyka a editoru](../extensibility/language-service-and-editor-extension-points.md)
