---
title: 'Návod: zobrazení QuickInfoch popisků | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3b349f0293071dfa30677b7558ca93985d16d55e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64808174"
---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>Návod: Zobrazení popisů tlačítek s rychlými informacemi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

QuickInfo je funkce technologie IntelliSense, která zobrazuje signatury a popisy metod, když uživatel přesune ukazatel myši na název metody. Můžete implementovat funkce založené na jazyce, jako je například QuickInfo, definováním identifikátorů, pro které chcete zadat QuickInfo popisy, a následným vytvořením popisu, ve kterém chcete zobrazit obsah. QuickInfo můžete definovat v kontextu jazykové služby nebo můžete definovat vlastní příponu názvu souboru a typ obsahu a zobrazit QuickInfo pouze pro tento typ, nebo můžete zobrazit QuickInfo pro existující typ obsahu (například "text"). Tento návod ukazuje, jak zobrazit QuickInfo pro typ obsahu "text".  
  
 Příklad QuickInfo v tomto návodu zobrazuje popisy tlačítek, když uživatel přesune ukazatel myši na název metody. Tento návrh vyžaduje, abyste implementovali tato čtyři rozhraní:  
  
- zdrojové rozhraní  
  
- rozhraní poskytovatele zdroje  
  
- rozhraní kontroleru  
  
- rozhraní poskytovatele kontroleru  
  
  Zprostředkovatelé zdrojového kódu a řadiče jsou Managed Extensibility Framework (MEF) částí komponenty a jsou odpovědni za exportování tříd source a Controller a k importu služeb a zprostředkovatelů, jako je <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> , což vytvoří textovou vyrovnávací paměť popisku a <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> spustí relaci QuickInfo.  
  
  V tomto příkladu používá zdroj QuickInfo pevně zakódovaný seznam názvů a popisů metod, ale v úplných implementacích je za poskytnutí tohoto obsahu zodpovědný jazyková služba a jazyková dokumentace.  
  
## <a name="prerequisites"></a>Předpoklady  
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Vytvoření projektu MEF  
  
#### <a name="to-create-a-mef-project"></a>Vytvoření projektu MEF  
  
1. Vytvoří projekt VSIX v jazyce C#. (V dialogovém okně **Nový projekt** vyberte **Visual C#/rozšiřitelnost**a potom **projekt VSIX**.) Pojmenujte řešení `QuickInfoTest` .  
  
2. Přidejte do projektu šablonu položky klasifikátoru editoru. Další informace naleznete v tématu [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Odstraňte existující soubory třídy.  
  
## <a name="implementing-the-quickinfo-source"></a>Implementace zdroje QuickInfo  
 Zdroj QuickInfo zodpovídá za shromáždění sady identifikátorů a jejich popisů a přidání obsahu do textové vyrovnávací paměti popisku, pokud je zjištěn jeden z identifikátorů. V tomto příkladu se identifikátory a jejich popisy přidávají pouze do zdrojového konstruktoru.  
  
#### <a name="to-implement-the-quickinfo-source"></a>Implementace zdroje QuickInfo  
  
1. Přidejte soubor třídy a pojmenujte ho `TestQuickInfoSource` .  
  
2. Přidejte odkaz na Microsoft. VisualStudio. Language. IntelliSense.  
  
3. Přidejte následující importy.  
  
     [!code-csharp[VSSDKQuickInfoTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#1)]
     [!code-vb[VSSDKQuickInfoTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#1)]  
  
4. Deklarujte třídu, která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> , a pojmenujte ji `TestQuickInfoSource` .  
  
     [!code-csharp[VSSDKQuickInfoTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#2)]
     [!code-vb[VSSDKQuickInfoTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#2)]  
  
5. Přidejte pole pro poskytovatele zdroje QuickInfo, vyrovnávací paměť textu a sadu názvů metod a signatur metod. V tomto příkladu jsou názvy metod a signatury inicializovány v `TestQuickInfoSource` konstruktoru.  
  
     [!code-csharp[VSSDKQuickInfoTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#3)]
     [!code-vb[VSSDKQuickInfoTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#3)]  
  
6. Přidejte konstruktor, který nastaví poskytovatele zdroje QuickInfo a textové vyrovnávací paměti, a naplní sadu názvů metod a signatury a popisy metod.  
  
     [!code-csharp[VSSDKQuickInfoTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#4)]
     [!code-vb[VSSDKQuickInfoTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#4)]  
  
7. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> metodu. V tomto příkladu metoda najde aktuální slovo nebo předchozí slovo, pokud se ukazatel myši nachází na konci řádku nebo v textové vyrovnávací paměti. Pokud je slovo jedním z názvů metod, popis tohoto názvu metody se přidá do obsahu QuickInfo.  
  
     [!code-csharp[VSSDKQuickInfoTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#5)]
     [!code-vb[VSSDKQuickInfoTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#5)]  
  
8. Je také nutné implementovat metodu Dispose (), protože <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementuje <xref:System.IDisposable> :  
  
     [!code-csharp[VSSDKQuickInfoTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#6)]
     [!code-vb[VSSDKQuickInfoTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#6)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>Implementace poskytovatele zdroje QuickInfo  
 Poskytovatel zdroje QuickInfo slouží primárně pro export sebe sama jako součást MEF a vytvoření instance zdroje QuickInfo. Vzhledem k tomu, že se jedná o součást MEF, může importovat jiné části komponenty MEF.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>Implementace poskytovatele zdroje QuickInfo  
  
1. Deklarujte poskytovatele zdroje QuickInfo s názvem `TestQuickInfoSourceProvider` , který implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider> , a exportujte ho s <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ToolTip QuickInfo source", a <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> před = "default" a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text".  
  
     [!code-csharp[VSSDKQuickInfoTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#7)]
     [!code-vb[VSSDKQuickInfoTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#7)]  
  
2. Importujte dvě služby editoru <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> a <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> jako vlastnosti `TestQuickInfoSourceProvider` .  
  
     [!code-csharp[VSSDKQuickInfoTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#8)]
     [!code-vb[VSSDKQuickInfoTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#8)]  
  
3. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> pro vrácení nového `TestQuickInfoSource` .  
  
     [!code-csharp[VSSDKQuickInfoTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#9)]
     [!code-vb[VSSDKQuickInfoTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#9)]  
  
## <a name="implementing-a-quickinfo-controller"></a>Implementace kontroleru QuickInfo  
 Řadiče QuickInfo určují, kdy se má zobrazit QuickInfo. V tomto příkladu se QuickInfo zobrazí, pokud je ukazatel na slovo, které odpovídá jednomu z názvů metod. Kontroler QuickInfo implementuje obslužnou rutinu události při přechodu myší, která spustí relaci QuickInfo.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>Implementace kontroleru QuickInfo  
  
1. Deklarujte třídu, která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> , a pojmenujte ji `TestQuickInfoController` .  
  
     [!code-csharp[VSSDKQuickInfoTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#10)]
     [!code-vb[VSSDKQuickInfoTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#10)]  
  
2. Přidejte soukromá pole pro textové zobrazení, textové vyrovnávací paměti reprezentované v zobrazení text, v relaci QuickInfo a ve zprostředkovateli QuickInfo Controller.  
  
     [!code-csharp[VSSDKQuickInfoTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#11)]
     [!code-vb[VSSDKQuickInfoTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#11)]  
  
3. Přidejte konstruktor, který nastaví pole a přidá obslužnou rutinu události při přechodu myší.  
  
     [!code-csharp[VSSDKQuickInfoTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#12)]
     [!code-vb[VSSDKQuickInfoTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#12)]  
  
4. Přidejte obslužnou rutinu události při přechodu myší, která spustí relaci QuickInfo.  
  
     [!code-csharp[VSSDKQuickInfoTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#13)]
     [!code-vb[VSSDKQuickInfoTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#13)]  
  
5. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> metodu tak, aby odebrala obslužnou rutinu události při přechodu myší, když je kontroler odpojen z textového zobrazení.  
  
     [!code-csharp[VSSDKQuickInfoTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#14)]
     [!code-vb[VSSDKQuickInfoTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#14)]  
  
6. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> metodu a <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> metodu jako prázdné metody pro tento příklad.  
  
     [!code-csharp[VSSDKQuickInfoTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#15)]
     [!code-vb[VSSDKQuickInfoTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#15)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>Implementace poskytovatele kontroleru QuickInfo  
 Poskytovatel řadiče QuickInfo slouží primárně pro export sebe sama jako součást MEF a vytvoření instance řadiče QuickInfo. Vzhledem k tomu, že se jedná o součást MEF, může importovat jiné části komponenty MEF.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>Implementace poskytovatele kontroleru QuickInfo  
  
1. Deklarujte třídu s názvem `TestQuickInfoControllerProvider` , která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider> , a exportujte ji pomocí <xref:Microsoft.VisualStudio.Utilities.NameAttribute> příkazu "ToolTip QuickInfo Controller" a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text":  
  
     [!code-csharp[VSSDKQuickInfoTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#16)]
     [!code-vb[VSSDKQuickInfoTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#16)]  
  
2. Importujte <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> jako vlastnost.  
  
     [!code-csharp[VSSDKQuickInfoTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#17)]
     [!code-vb[VSSDKQuickInfoTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#17)]  
  
3. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> metodu vytvořením instance kontroleru QuickInfo.  
  
     [!code-csharp[VSSDKQuickInfoTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#18)]
     [!code-vb[VSSDKQuickInfoTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#18)]  
  
## <a name="building-and-testing-the-code"></a>Sestavování a testování kódu  
 Chcete-li otestovat tento kód, sestavte řešení QuickInfoTest a spusťte ho v experimentální instanci.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>Sestavení a testování řešení QuickInfoTest  
  
1. Sestavte řešení.  
  
2. Při spuštění tohoto projektu v ladicím programu je vytvořena instance druhé instance aplikace Visual Studio.  
  
3. Vytvořte textový soubor a zadejte nějaký text, který obsahuje slova "Add" a "odečíst".  
  
4. Přesuňte ukazatel myši na jeden z výskytů "Přidat". Měl by se zobrazit signatura a popis `add` metody.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
