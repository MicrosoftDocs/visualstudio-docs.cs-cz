---
title: 'Návod: zobrazení inteligentních přehledů | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - smart tags
ms.assetid: 10bb4f69-b259-41f0-b91a-69b04385d9a5
caps.latest.revision: 31
manager: jillfra
ms.openlocfilehash: 116f76324a2150413c0ae6d08bc99e114efcc50e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64805580"
---
# <a name="walkthrough-displaying-smarttags"></a>Návod: zobrazení inteligentních inteligentních zobrazení
Inteligentní značky jsou zastaralé ve prospěch žárovek. Viz [Návod: zobrazení návrhů na žárovku](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
 Inteligentní značky jsou značky na textu, který se rozbalí, aby se zobrazila sada akcí. Například v projektu Visual Basic nebo Visual C# se červená čára zobrazí pod slovem při přejmenování identifikátoru, jako je název proměnné. Když přesunete ukazatel na podtržení, zobrazí se vedle ukazatele tlačítko. Pokud kliknete na tlačítko, zobrazí se navrhovaná akce, například **přejmenujte čtení na hodnotu jen pro čtení**. Pokud kliknete na akci, všechny odkazy na **přečtení** v projektu jsou přejmenovány na **jen pro čtení**.  
  
 I když jsou inteligentní značky součástí implementace technologie IntelliSense v editoru, můžete implementovat inteligentní značky pomocí podtříd <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> a poté implementovat <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> rozhraní a <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> rozhraní.  
  
> [!NOTE]
> Podobným způsobem je možné implementovat jiné druhy značek.  
  
 Následující návod ukazuje, jak vytvořit inteligentní značku, která se zobrazí na aktuálním slově a má dvě navrhované akce: **převést na velká písmena** a **převést na malá písmena**.  
  
## <a name="prerequisites"></a>Předpoklady  
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Vytvoření projektu Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Vytvoření projektu MEF  
  
1. Vytvořte projekt klasifikátoru editoru. Pojmenujte řešení `SmartTagTest` .  
  
2. V editoru manifestu VSIX otevřete soubor source. extension. vsixmanifest.  
  
3. Ujistěte se, že část **assets** obsahuje `Microsoft.VisualStudio.MefComponent` typ, **zdroj** je nastaven na hodnotu `A project in current solution` a **projekt** je nastaven na SmartTagTest.dll.  
  
4. Uložte a zavřete source. extension. vsixmanifest.  
  
5. Do projektu přidejte následující odkaz a nastavte **CopyLocal** na `false` :  
  
     Microsoft. VisualStudio. Language. IntelliSense  
  
6. Odstraňte existující soubory třídy.  
  
## <a name="implementing-a-tagger-for-smart-tags"></a>Implementace autor značky pro inteligentní značky  
  
#### <a name="to-implement-a-tagger-for-smart-tags"></a>Implementace autor značky pro inteligentní značky  
  
1. Přidejte soubor třídy a pojmenujte ho `TestSmartTag` .  
  
2. Přidejte následující importy:  
  
     [!code-csharp[VSSDKSmartTagTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#1)]
     [!code-vb[VSSDKSmartTagTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#1)]  
  
3. Přidejte třídu s názvem `TestSmartTag` , ze které dědí <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> .  
  
     [!code-csharp[VSSDKSmartTagTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#2)]
     [!code-vb[VSSDKSmartTagTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#2)]  
  
4. Přidejte konstruktor pro tuto třídu, která volá základní konstruktor s a <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> , což způsobí, že se pod prvním znakem slova zobrazí modrá čára. (Pokud použijete <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> , zobrazí se pod posledním znakem slova červená čára.)  
  
     [!code-csharp[VSSDKSmartTagTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#3)]
     [!code-vb[VSSDKSmartTagTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#3)]  
  
5. Přidejte třídu s názvem `TestSmartTagger` , která dědí z <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typu `TestSmartTag` a implementuje <xref:System.IDisposable> .  
  
     [!code-csharp[VSSDKSmartTagTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#4)]
     [!code-vb[VSSDKSmartTagTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#4)]  
  
6. Do třídy autor značky přidejte následující soukromá pole.  
  
     [!code-csharp[VSSDKSmartTagTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#5)]
     [!code-vb[VSSDKSmartTagTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#5)]  
  
7. Přidejte konstruktor, který nastaví soukromá pole, a přihlaste se k odběru <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> události.  
  
     [!code-csharp[VSSDKSmartTagTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#6)]
     [!code-vb[VSSDKSmartTagTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#6)]  
  
8. Implementujte, aby se <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> pro aktuální slovo vytvořila značka. (Tato metoda také volá soukromou metodu `GetSmartTagActions` , která je vysvětlena později.)  
  
     [!code-csharp[VSSDKSmartTagTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#7)]
     [!code-vb[VSSDKSmartTagTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#7)]  
  
9. Přidejte `GetSmartTagActions` metodu pro nastavení akcí inteligentních značek. Vlastní akce jsou implementovány v pozdějších krocích.  
  
     [!code-csharp[VSSDKSmartTagTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#8)]
     [!code-vb[VSSDKSmartTagTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#8)]  
  
10. Deklarujte `SmartTagsChanged` událost.  
  
     [!code-csharp[VSSDKSmartTagTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#9)]
     [!code-vb[VSSDKSmartTagTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#9)]  
  
11. Implementací `OnLayoutChanged` obslužné rutiny události vyvolejte `TagsChanged` událost, která vyvolá <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> volání.  
  
     [!code-csharp[VSSDKSmartTagTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#10)]
     [!code-vb[VSSDKSmartTagTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#10)]  
  
12. Implementujte <xref:System.IDisposable.Dispose%2A> metodu tak, aby odhlásila odběr <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> události.  
  
     [!code-csharp[VSSDKSmartTagTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#11)]
     [!code-vb[VSSDKSmartTagTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#11)]  
  
## <a name="implementing-the-smart-tag-tagger-provider"></a>Implementace poskytovatele autor značky inteligentních značek  
  
#### <a name="to-implement-the-smart-tag-tagger-provider"></a>Implementace poskytovatele inteligentních značek autor značky  
  
1. Přidejte třídu s názvem `TestSmartTagTaggerProvider` , ze které dědí <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> . Exportujte je pomocí <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> textu "text", a <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> před = "výchozí" a a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> .  
  
     [!code-csharp[VSSDKSmartTagTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#12)]
     [!code-vb[VSSDKSmartTagTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#12)]  
  
2. Importujte <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> jako vlastnost.  
  
     [!code-csharp[VSSDKSmartTagTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#13)]
     [!code-vb[VSSDKSmartTagTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#13)]  
  
3. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metodu.  
  
     [!code-csharp[VSSDKSmartTagTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#14)]
     [!code-vb[VSSDKSmartTagTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#14)]  
  
## <a name="implementing-smart-tag-actions"></a>Implementace akcí inteligentních značek  
  
#### <a name="to-implement-smart-tag-actions"></a>Implementace akcí inteligentních značek  
  
1. Vytvořte dvě třídy, první pojmenovaný `UpperCaseSmartTagAction` a druhý s názvem `LowerCaseSmartTagAction` . Obě třídy implementují <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction> .  
  
    [!code-csharp[VSSDKSmartTagTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#15)]
    [!code-vb[VSSDKSmartTagTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#15)]  
  
    [!code-csharp[VSSDKSmartTagTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#16)]
    [!code-vb[VSSDKSmartTagTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#16)]  
  
   Obě třídy jsou podobné s tím rozdílem, že jedno volání <xref:System.String.ToUpper%2A> a další volání <xref:System.String.ToLower%2A> . Následující postup pokrývá pouze velké třídy akcí, ale je nutné implementovat obě třídy. Použijte postup pro implementaci velkých a malých písmen jako vzor pro implementaci akce s malými písmeny.  
  
2. Deklarovat sadu privátních polí  
  
    [!code-csharp[VSSDKSmartTagTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#17)]
    [!code-vb[VSSDKSmartTagTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#17)]  
  
3. Přidejte konstruktor, který nastaví pole.  
  
    [!code-csharp[VSSDKSmartTagTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#18)]
    [!code-vb[VSSDKSmartTagTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#18)]  
  
4. Implementujte vlastnosti následujícím způsobem.  
  
    [!code-csharp[VSSDKSmartTagTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#19)]
    [!code-vb[VSSDKSmartTagTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#19)]  
  
5. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction.Invoke%2A> metodu tak, že nahradíte text v rozpětí velkými ekvivalenty.  
  
    [!code-csharp[VSSDKSmartTagTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#20)]
    [!code-vb[VSSDKSmartTagTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#20)]  
  
## <a name="building-and-testing-the-code"></a>Sestavování a testování kódu  
 Chcete-li otestovat tento kód, sestavte řešení SmartTagTest a spusťte ho v experimentální instanci.  
  
#### <a name="to-build-and-test-the-smarttagtest-solution"></a>Sestavení a testování řešení SmartTagTest  
  
1. Sestavte řešení.  
  
2. Při spuštění tohoto projektu v ladicím programu je vytvořena instance druhé instance aplikace Visual Studio.  
  
3. Vytvořte textový soubor a zadejte nějaký text.  
  
     Pod prvním písmenem prvního slova textu by se měla zobrazit modrá čára.  
  
4. Přesuňte ukazatel myši na modrou čáru.  
  
     Tlačítko by mělo být zobrazeno blízko ukazatele.  
  
5. Po kliknutí na tlačítko by se měla zobrazit dvě navrhované akce: **převést na velká písmena** a **převést na malá písmena**. Pokud kliknete na první akci, veškerý text v aktuálním slově by se měl převést na velká písmena. Pokud kliknete na druhou akci, veškerý text by měl být převeden na malá písmena.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)