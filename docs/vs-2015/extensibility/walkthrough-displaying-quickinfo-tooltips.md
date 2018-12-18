---
title: 'Návod: Zobrazení popisky rychlé informace | Dokumentace Microsoftu'
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
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9cd0e331536c194acdde95bdd74e5f41668a23e1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51806279"
---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>Návod: Zobrazení popisů tlačítek s rychlými informacemi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rychlé informace je funkce technologie IntelliSense, která zobrazuje podpisy metod a popisy, když se uživatel přesune ukazatel myši název metody. Založený na jazyce funkce, jako je rychlé informace lze implementovat definováním identifikátory, pro které chcete poskytnout QuickInfo popisy a následného vytvoření popisu, ve kterém chcete zobrazit obsah. Rychlé informace lze definovat v kontextu jazykové služby, nebo můžete definovat vlastní název souboru příponu a obsah zadejte a zobrazit rychlé informace pro právě tento typ nebo můžete zobrazit rychlé informace pro existující typ obsahu (jako je například "text"). Tento návod ukazuje, jak zobrazit rychlé informace pro typ obsahu "text".  
  
 Příklad rychlých informací v tomto názorném postupu zobrazí popisky, když uživatel přesune ukazatel myši název metody. Tento návrh je potřeba implementovat tyto čtyři rozhraní:  
  
- zdrojové rozhraní  
  
- zdrojové rozhraní poskytovatele  
  
- kontroler rozhraní  
  
- rozhraní poskytovatele řadiče  
  
  Zprostředkovatele zdroje a řadiče jsou součásti Managed Extensibility Framework (MEF) a zodpovídají za export tříd zdroje a kontroler a importu služby zprostředkovatelé, jako <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, která vytvoří text popisku vyrovnávací paměť a <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, která aktivuje QuickInfo relace.  
  
  V tomto příkladu zdroj QuickInfo používá pevně zakódovaný seznamu popisů a názvů metody, ale v úplné implementací, služba jazyka a dokumentace k jazyku odpovídají za poskytování obsahu.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Vytvoření projektu rozhraní MEF  
  
#### <a name="to-create-a-mef-project"></a>Chcete-li vytvořit projekt rozhraní MEF  
  
1.  Vytvořte projekt VSIX C#. (V **nový projekt** dialogového okna, vyberte **Visual C# / rozšíření**, pak **projekt VSIX**.) Pojmenujte řešení `QuickInfoTest`.  
  
2.  Přidejte do projektu šablony položky editoru třídění. Další informace najdete v tématu [vytváření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Odstraníte existující soubory tříd.  
  
## <a name="implementing-the-quickinfo-source"></a>Implementace zdroje rychlé informace  
 Rychlé informace zdroje je zodpovědná za shromažďování sadu identifikátorů a jejich popisy a jeden z identifikátorů došlo k přidání obsahu do vyrovnávací paměti textu popisku. V tomto příkladu jsou identifikátory a jejich popisy právě přidali v konstruktoru zdroje.  
  
#### <a name="to-implement-the-quickinfo-source"></a>K implementaci zdroji rychlé informace  
  
1.  Přidejte soubor třídy a pojmenujte ho `TestQuickInfoSource`.  
  
2.  Přidejte odkaz na Microsoft.VisualStudio.Language.IntelliSense.  
  
3.  Přidejte následující importy.  
  
     [!code-csharp[VSSDKQuickInfoTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#1)]
     [!code-vb[VSSDKQuickInfoTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#1)]  
  
4.  Deklarace třídy, která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>a pojmenujte ho `TestQuickInfoSource`.  
  
     [!code-csharp[VSSDKQuickInfoTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#2)]
     [!code-vb[VSSDKQuickInfoTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#2)]  
  
5.  Přidání polí pro QuickInfo poskytovatel správy zdrojových, textovou vyrovnávací paměť a sadu metoda názvy a podpisy metod. V tomto příkladu metoda názvy a podpisy jsou inicializovány v `TestQuickInfoSource` konstruktoru.  
  
     [!code-csharp[VSSDKQuickInfoTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#3)]
     [!code-vb[VSSDKQuickInfoTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#3)]  
  
6.  Přidejte konstruktor, který nastaví poskytovatele QuickInfo zdrojového kódu a textové vyrovnávací paměti a naplní sadu metoda názvy a podpisy metod a popisy.  
  
     [!code-csharp[VSSDKQuickInfoTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#4)]
     [!code-vb[VSSDKQuickInfoTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#4)]  
  
7.  Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> metody. V tomto příkladu metoda vyhledá aktuálního slova nebo předchozí slovo kurzor je na konci čáry nebo textovou vyrovnávací paměť. Pokud slovo je jednou z názvy metod, popis pro tento název metody je přidána do QuickInfo obsah.  
  
     [!code-csharp[VSSDKQuickInfoTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#5)]
     [!code-vb[VSSDKQuickInfoTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#5)]  
  
8.  Musíte také implementovat metodu Dispose() od té doby <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementuje <xref:System.IDisposable>:  
  
     [!code-csharp[VSSDKQuickInfoTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#6)]
     [!code-vb[VSSDKQuickInfoTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#6)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>Implementace zprostředkovatele zdroje rychlé informace  
 Zprostředkovatele zdroje rychlých informací primárně slouží jako samotný exportovat jako součást MEF a vytvoření instance QuickInfo zdroje. Protože je součást MEF, můžete importovat jinými částmi MEF komponenty.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>Pro implementaci zprostředkovatele zdroje rychlé informace  
  
1.  Deklarovat zprostředkovatele QuickInfo zdroj s názvem `TestQuickInfoSourceProvider` , který implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>a exportujte ho pomocí <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "Popisek rychlé informace zdroje" <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> z před = "Výchozí" a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text".  
  
     [!code-csharp[VSSDKQuickInfoTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#7)]
     [!code-vb[VSSDKQuickInfoTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#7)]  
  
2.  Importovat dvě služby editor <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> a <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, jako vlastnosti `TestQuickInfoSourceProvider`.  
  
     [!code-csharp[VSSDKQuickInfoTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#8)]
     [!code-vb[VSSDKQuickInfoTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#8)]  
  
3.  Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> se vraťte novou `TestQuickInfoSource`.  
  
     [!code-csharp[VSSDKQuickInfoTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#9)]
     [!code-vb[VSSDKQuickInfoTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#9)]  
  
## <a name="implementing-a-quickinfo-controller"></a>Implementace QuickInfo Kontroleru  
 Rychlé informace řadiče určují, kdy má být zobrazena rychlé informace. V tomto příkladu je rychlé informace zobrazí, když ukazatel myši je nad slovo, které odpovídá jednomu z názvy metod. Kontroler QuickInfo implementuje myši při najetí myší obslužnou rutinu události, které spustí relaci rychlé informace.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>K implementaci QuickInfo kontroleru  
  
1.  Deklarace třídy, která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>a pojmenujte ho `TestQuickInfoController`.  
  
     [!code-csharp[VSSDKQuickInfoTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#10)]
     [!code-vb[VSSDKQuickInfoTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#10)]  
  
2.  Přidejte privátní pole pro zobrazení textu v zobrazení textu, relace QuickInfo a zprostředkovatele kontroleru QuickInfo vyrovnávací paměti textu.  
  
     [!code-csharp[VSSDKQuickInfoTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#11)]
     [!code-vb[VSSDKQuickInfoTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#11)]  
  
3.  Přidáte konstruktor, který nastaví pole a přidá obslužnou rutinu události myši při najetí myší.  
  
     [!code-csharp[VSSDKQuickInfoTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#12)]
     [!code-vb[VSSDKQuickInfoTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#12)]  
  
4.  Přidáte obslužnou rutinu události myši při najetí myší, která aktivuje QuickInfo relace.  
  
     [!code-csharp[VSSDKQuickInfoTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#13)]
     [!code-vb[VSSDKQuickInfoTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#13)]  
  
5.  Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> metodu tak, že se odstraní obslužná rutina události myši při najetí myší kontroleru je odpojeno od zobrazení textu.  
  
     [!code-csharp[VSSDKQuickInfoTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#14)]
     [!code-vb[VSSDKQuickInfoTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#14)]  
  
6.  Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> metoda a <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> metody jako prázdný metod v tomto příkladu.  
  
     [!code-csharp[VSSDKQuickInfoTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#15)]
     [!code-vb[VSSDKQuickInfoTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#15)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>Implementace zprostředkovatele QuickInfo Kontroleru  
 Zprostředkovatel QuickInfo řadič slouží především k samotné exportovat jako součást MEF a vytvoření instancí kontroleru QuickInfo. Protože je součást MEF, můžete importovat jinými částmi MEF komponenty.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>K implementaci zprostředkovatele kontroleru rychlé informace  
  
1.  Deklarovat třídu s názvem `TestQuickInfoControllerProvider` , který implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>a exportujte ho pomocí <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "Řadiče popisek rychlé informace" a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text":  
  
     [!code-csharp[VSSDKQuickInfoTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#16)]
     [!code-vb[VSSDKQuickInfoTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#16)]  
  
2.  Import <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> jako vlastnost.  
  
     [!code-csharp[VSSDKQuickInfoTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#17)]
     [!code-vb[VSSDKQuickInfoTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#17)]  
  
3.  Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> metoda po vytvoření instance kontroleru rychlé informace.  
  
     [!code-csharp[VSSDKQuickInfoTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#18)]
     [!code-vb[VSSDKQuickInfoTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#18)]  
  
## <a name="building-and-testing-the-code"></a>Vytváření a testování kódu  
 K otestování tohoto kódu sestavte řešení QuickInfoTest a spusťte v experimentální instanci.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>Pro vytváření a testování QuickInfoTest řešení  
  
1.  Sestavte řešení.  
  
2.  Při spuštění tohoto projektu v ladicím programu, je vytvořena instance druhou instanci aplikace Visual Studio.  
  
3.  Vytvoření textového souboru a typu text, který obsahuje slova "Přidat" a "odečíst".  
  
4.  Přesuňte ukazatel nad jedno z výskytů "Přidání". Podpis a popis `add` metoda má být zobrazena.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

