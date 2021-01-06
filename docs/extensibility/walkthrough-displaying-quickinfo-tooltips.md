---
title: 'Návod: zobrazení QuickInfoch popisků | Microsoft Docs'
description: Přečtěte si, jak zobrazit QuickInfo pro textový obsah pomocí tohoto návodu. QuickInfo zobrazí signatury a popisy metod pro název metody.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 34e1bb2c92cd387e979fdaa5746a34ea8d3995fc
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877933"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>Návod: zobrazení QuickInfoch popisků
QuickInfo je funkce technologie IntelliSense, která zobrazuje signatury a popisy metod, když uživatel přesune ukazatel myši na název metody. Můžete implementovat funkce založené na jazyce, jako je například QuickInfo, definováním identifikátorů, pro které chcete zadat QuickInfo popisy, a následným vytvořením popisu, ve kterém chcete zobrazit obsah. QuickInfo můžete definovat v kontextu jazykové služby nebo můžete definovat vlastní příponu názvu souboru a typ obsahu a zobrazit QuickInfo pouze pro tento typ, nebo můžete zobrazit QuickInfo pro existující typ obsahu (například "text"). Tento návod ukazuje, jak zobrazit QuickInfo pro typ obsahu "text".

 Příklad QuickInfo v tomto návodu zobrazuje popisy tlačítek, když uživatel přesune ukazatel myši na název metody. Tento návrh vyžaduje, abyste implementovali tato čtyři rozhraní:

- zdrojové rozhraní

- rozhraní poskytovatele zdroje

- rozhraní kontroleru

- rozhraní poskytovatele kontroleru

  Zprostředkovatelé zdrojového kódu a řadiče jsou Managed Extensibility Framework (MEF) částí komponenty a jsou odpovědni za exportování tříd source a Controller a k importu služeb a zprostředkovatelů, jako je <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> , což vytvoří textovou vyrovnávací paměť popisku a <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> spustí relaci QuickInfo.

  V tomto příkladu používá zdroj QuickInfo pevně zakódovaný seznam názvů a popisů metod, ale v úplných implementacích je za poskytnutí tohoto obsahu zodpovědný jazyková služba a jazyková dokumentace.

## <a name="prerequisites"></a>Předpoklady
 Od sady Visual Studio 2015 není nutné instalovat sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Vytvořit projekt MEF

### <a name="to-create-a-mef-project"></a>Vytvoření projektu MEF

1. Vytvoří projekt VSIX v jazyce C#. (V dialogovém okně **Nový projekt** vyberte **Visual C#/rozšiřitelnost** a potom **projekt VSIX**.) Pojmenujte řešení `QuickInfoTest` .

2. Přidejte do projektu šablonu položky klasifikátoru editoru. Další informace naleznete v tématu [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Odstraňte existující soubory třídy.

## <a name="implement-the-quickinfo-source"></a>Implementace zdroje QuickInfo
 Zdroj QuickInfo zodpovídá za shromáždění sady identifikátorů a jejich popisů a přidání obsahu do textové vyrovnávací paměti popisku, pokud je zjištěn jeden z identifikátorů. V tomto příkladu se identifikátory a jejich popisy přidávají pouze do zdrojového konstruktoru.

#### <a name="to-implement-the-quickinfo-source"></a>Implementace zdroje QuickInfo

1. Přidejte soubor třídy a pojmenujte ho `TestQuickInfoSource` .

2. Přidejte odkaz na *Microsoft. VisualStudio. Language. IntelliSense*.

3. Přidejte následující importy.

     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]

4. Deklarujte třídu, která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> , a pojmenujte ji `TestQuickInfoSource` .

     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]

5. Přidejte pole pro poskytovatele zdroje QuickInfo, vyrovnávací paměť textu a sadu názvů metod a signatur metod. V tomto příkladu jsou názvy metod a signatury inicializovány v `TestQuickInfoSource` konstruktoru.

     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]

6. Přidejte konstruktor, který nastaví poskytovatele zdroje QuickInfo a textové vyrovnávací paměti, a naplní sadu názvů metod a signatury a popisy metod.

     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]

7. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> metodu. V tomto příkladu metoda najde aktuální slovo nebo předchozí slovo, pokud se ukazatel myši nachází na konci řádku nebo v textové vyrovnávací paměti. Pokud je slovo jedním z názvů metod, popis tohoto názvu metody se přidá do obsahu QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]

8. Je také nutné implementovat metodu Dispose (), protože <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementuje <xref:System.IDisposable> :

     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]

## <a name="implement-a-quickinfo-source-provider"></a>Implementace poskytovatele zdroje QuickInfo
 Poskytovatel zdroje QuickInfo slouží primárně pro export sebe sama jako součást MEF a vytvoření instance zdroje QuickInfo. Vzhledem k tomu, že se jedná o součást MEF, může importovat jiné části komponenty MEF.

#### <a name="to-implement-a-quickinfo-source-provider"></a>Implementace poskytovatele zdroje QuickInfo

1. Deklarujte poskytovatele zdroje QuickInfo s názvem `TestQuickInfoSourceProvider` , který implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider> , a exportujte ho s <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ToolTip QuickInfo source", a <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> před = "default" a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text".

     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]

2. Importujte dvě služby editoru <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> a <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> jako vlastnosti `TestQuickInfoSourceProvider` .

     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]

3. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> pro vrácení nového `TestQuickInfoSource` .

     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]

## <a name="implement-a-quickinfo-controller"></a>Implementace kontroleru QuickInfo
 QuickInfo řadiče určují, kdy se zobrazí QuickInfo. V tomto příkladu se QuickInfo zobrazí, když je ukazatel na slovo, které odpovídá jednomu z názvů metod. Kontroler QuickInfo implementuje obslužnou rutinu události při přechodu myší, která spustí relaci QuickInfo.

### <a name="to-implement-a-quickinfo-controller"></a>Implementace kontroleru QuickInfo

1. Deklarujte třídu, která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> , a pojmenujte ji `TestQuickInfoController` .

     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]

2. Přidejte soukromá pole pro textové zobrazení, textové vyrovnávací paměti reprezentované v zobrazení text, v relaci QuickInfo a ve zprostředkovateli QuickInfo Controller.

     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]

3. Přidejte konstruktor, který nastaví pole a přidá obslužnou rutinu události při přechodu myší.

     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]

4. Přidejte obslužnou rutinu události při přechodu myší, která spustí relaci QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]

5. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> metodu tak, aby odebrala obslužnou rutinu události při přechodu myší, když je kontroler odpojen z textového zobrazení.

     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]

6. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> metodu a <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> metodu jako prázdné metody pro tento příklad.

     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]

## <a name="implementing-the-quickinfo-controller-provider"></a>Implementace poskytovatele kontroleru QuickInfo
 Poskytovatel řadiče QuickInfo slouží primárně pro export sebe sama jako součást MEF a vytvoření instance řadiče QuickInfo. Vzhledem k tomu, že se jedná o součást MEF, může importovat jiné části komponenty MEF.

### <a name="to-implement-the-quickinfo-controller-provider"></a>Implementace poskytovatele kontroleru QuickInfo

1. Deklarujte třídu s názvem `TestQuickInfoControllerProvider` , která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider> , a exportujte ji pomocí <xref:Microsoft.VisualStudio.Utilities.NameAttribute> příkazu "ToolTip QuickInfo Controller" a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text":

     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]

2. Importujte <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> jako vlastnost.

     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]

3. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> metodu vytvořením instance kontroleru QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]

## <a name="build-and-test-the-code"></a>Sestavení a testování kódu
 Chcete-li otestovat tento kód, sestavte řešení QuickInfoTest a spusťte ho v experimentální instanci.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>Sestavení a testování řešení QuickInfoTest

1. Sestavte řešení.

2. Při spuštění tohoto projektu v ladicím programu se spustí druhá instance sady Visual Studio.

3. Vytvořte textový soubor a zadejte nějaký text, který obsahuje slova "Add" a "odečíst".

4. Přesuňte ukazatel myši na jeden z výskytů "Přidat". Měl by se zobrazit signatura a popis `add` metody.

## <a name="see-also"></a>Viz také
- [Návod: propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
