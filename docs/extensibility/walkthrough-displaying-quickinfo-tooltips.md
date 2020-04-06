---
title: 'Návod: Zobrazení popisů rychlých informací | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 47a14ca0692ad0338b56fd1d372307fb0e2ccc4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697441"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>Návod: Zobrazení popisů rychlých informací
QuickInfo je funkce Technologie IntelliSense, která zobrazuje podpisy a popisy metod, když uživatel přesune ukazatel nad názvem metody. Můžete implementovat funkce založené na jazyce, jako je například QuickInfo definováním identifikátorů, pro které chcete poskytnout popisy QuickInfo a potom vytvořit popis, ve kterém chcete zobrazit obsah. Funkci QuickInfo můžete definovat v kontextu jazykové služby nebo můžete definovat vlastní příponu názvu souboru a typ obsahu a zobrazit quickinfo pouze pro tento typ, nebo můžete zobrazit QuickInfo pro existující typ obsahu (například "text"). Tento návod ukazuje, jak zobrazit QuickInfo pro typ obsahu "text".

 Příklad QuickInfo v tomto návodu zobrazí popisky, když uživatel přesune ukazatel nad název metody. Tento návrh vyžaduje implementaci těchto čtyř rozhraní:

- zdrojové rozhraní

- rozhraní zdrojového zprostředkovatele

- rozhraní řadiče

- rozhraní zprostředkovatele řadiče

  Zprostředkovatelé zdrojového a řídicího systému jsou součásti architektury metenzbility (Managed Extensibility Framework) a jsou <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>zodpovědní za export tříd zdrojového a kontroleru a importslužeb a zprostředkovatelů, jako je například , která vytvoří textovou vyrovnávací paměť popisu a <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, která aktivuje relaci QuickInfo.

  V tomto příkladu zdroj QuickInfo používá pevně zakódovaný seznam názvů metod a popisů, ale v úplných implementacích je za poskytování tohoto obsahu zodpovědná jazyková služba a jazyková dokumentace.

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015, není nutné instalovat Visual Studio SDK ze služby Stažení softwaru. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Vytvoření projektu MEF

### <a name="to-create-a-mef-project"></a>Vytvoření projektu MEF

1. Vytvořte projekt C# VSIX. (V dialogovém okně **Nový projekt** vyberte možnost **Vizuální C# / Rozšiřitelnost**a potom **v six projectu**.) Pojmenujte `QuickInfoTest`řešení .

2. Přidejte do projektu šablonu položky třídění editoru. Další informace naleznete [v tématu Vytvoření rozšíření se šablonou položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Odstraňte existující soubory tříd.

## <a name="implement-the-quickinfo-source"></a>Implementace zdroje QuickInfo
 Zdroj QuickInfo je zodpovědný za shromažďování sadu identifikátorů a jejich popisy a přidání obsahu do vyrovnávací paměti textu popisek, když je zjištěn jeden z identifikátorů. V tomto příkladu jsou identifikátory a jejich popisy právě přidány do zdrojového konstruktoru.

#### <a name="to-implement-the-quickinfo-source"></a>Implementace zdroje QuickInfo

1. Přidejte soubor třídy `TestQuickInfoSource`a pojmenujte jej .

2. Přidejte odkaz na *Microsoft.VisualStudio.Language.IntelliSense*.

3. Přidejte následující importy.

     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]

4. Deklarujte třídu, která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>, a pojmenujte ji `TestQuickInfoSource`.

     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]

5. Přidejte pole pro zdrojového zprostředkovatele QuickInfo, textovou vyrovnávací paměť a sadu názvů metod a podpisů metod. V tomto příkladu jsou v `TestQuickInfoSource` konstruktoru inicializovány názvy metod a podpisy.

     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]

6. Přidejte konstruktor, který nastaví zdrojového zprostředkovatele QuickInfo a textovou vyrovnávací paměť a naplní sadu názvů metod a podpisů a popisů metod.

     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]

7. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> metodu. V tomto příkladu metoda najde aktuální slovo nebo předchozí slovo, pokud je kurzor na konci řádku nebo textové vyrovnávací paměti. Pokud je slovo jedním z názvů metod, je popis tohoto názvu metody přidán do obsahu QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]

8. Musíte také implementovat Dispose() <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> metoda, <xref:System.IDisposable>protože implementuje :

     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]

## <a name="implement-a-quickinfo-source-provider"></a>Implementace zdrojového zprostředkovatele Rychlých informací
 Zprostředkovatel zdroje QuickInfo slouží především k exportu sebe sama jako součást mef a k vytvoření instance zdroje QuickInfo. Protože se jedná o součást MEF, může importovat další součásti MEF.

#### <a name="to-implement-a-quickinfo-source-provider"></a>Implementace zdrojového zprostředkovatele QuickInfo

1. Deklarujte zdrojového `TestQuickInfoSourceProvider` zprostředkovatele <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>QuickInfo s <xref:Microsoft.VisualStudio.Utilities.NameAttribute> názvem, který implementuje , <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> a exportujte jej pomocí <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Zdroje rychlých informací v popisu", "před="výchozí", a a "text".

     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]

2. Importujte dvě <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> služby editoru a <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>jako vlastnosti aplikace `TestQuickInfoSourceProvider`.

     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]

3. Implementovat <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> vrátit `TestQuickInfoSource`nový .

     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]

## <a name="implement-a-quickinfo-controller"></a>Implementace řadiče QuickInfo
 Kontroly QuickInfo určují, kdy se zobrazí funkce QuickInfo. V tomto příkladu se funkce QuickInfo zobrazí, když je ukazatel nad slovem, které odpovídá jednomu z názvů metod. Kontroler QuickInfo implementuje obslužnou rutinu události při pohyblivém ukazateli myši, která aktivuje relaci QuickInfo.

### <a name="to-implement-a-quickinfo-controller"></a>Implementace řadiče QuickInfo

1. Deklarujte třídu, která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>, a pojmenujte ji `TestQuickInfoController`.

     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]

2. Přidejte soukromá pole pro zobrazení textu, textové vyrovnávací paměti reprezentované v textovém zobrazení, relaci QuickInfo a zprostředkovatele řadiče QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]

3. Přidejte konstruktor, který nastaví pole a přidá obslužnou rutinu události myši.

     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]

4. Přidejte obslužnou rutinu události myši, která aktivuje relaci QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]

5. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> metodu tak, aby odebrala obslužnou rutinu události myši při odpojení řadiče od textového zobrazení.

     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]

6. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> metodu <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> a metodu jako prázdné metody pro tento příklad.

     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]

## <a name="implementing-the-quickinfo-controller-provider"></a>Implementace zprostředkovatele řadiče QuickInfo
 Zprostředkovatel řadiče QuickInfo slouží především k exportu sebe sama jako součást mef a k vytvoření instance řadiče QuickInfo. Protože se jedná o součást MEF, může importovat další součásti MEF.

### <a name="to-implement-the-quickinfo-controller-provider"></a>Implementace zprostředkovatele řadiče QuickInfo

1. Deklarujte `TestQuickInfoControllerProvider` třídu <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>s názvem, <xref:Microsoft.VisualStudio.Utilities.NameAttribute> která implementuje , a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> exportujte ji pomocí "ToolTip QuickInfo Controller" a a "text":

     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]

2. Importujte <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> jako vlastnost.

     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]

3. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> metodu vytvořením instance řadiče QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]

## <a name="build-and-test-the-code"></a>Sestavení a testování kódu
 Chcete-li tento kód otestovat, vytvořte řešení QuickInfoTest a spusťte jej v experimentální instanci.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>Vytvoření a testování řešení QuickInfoTest

1. Sestavte řešení.

2. Při spuštění tohoto projektu v ladicím programu je spuštěna druhá instance sady Visual Studio.

3. Vytvořte textový soubor a zadejte text, který obsahuje slova "přidat" a "odečíst".

4. Přesuňte ukazatel nad jeden z výskytů "přidat". Podpis a popis `add` metody by měly být zobrazeny.

## <a name="see-also"></a>Viz také
- [Návod: Propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
