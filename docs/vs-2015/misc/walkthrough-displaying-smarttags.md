---
title: 'Návod: Zobrazení inteligentní značky | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - smart tags
ms.assetid: 10bb4f69-b259-41f0-b91a-69b04385d9a5
caps.latest.revision: 31
manager: douge
ms.openlocfilehash: 459530726628819587a3c228910baa3b902ae865
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939095"
---
# <a name="walkthrough-displaying-smarttags"></a>Návod: Zobrazení inteligentní značky
Inteligentní značky jsou zastaralé a místo toho použití žárovky. Zobrazit [návod: zobrazení návrhů](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
 Inteligentní značky jsou pro text značky, které se rozbalí a zobrazí sadu akcí. Například v projektu jazyka Visual Basic nebo Visual C#, červenou čáru se zobrazí v části slovo při přejmenování identifikátor jako název proměnné. Při přesunutí ukazatele myši podtržení, zobrazí se tlačítko téměř ukazatel. Pokud kliknete na tlačítko, navrhované akce se zobrazí, například **přejmenovat IsRead IsReady**. Pokud kliknete akce, všechny odkazy na **IsRead** v projektu jsou přejmenované **IsReady**.  
  
 I když se inteligentní značky jsou součástí implementace technologie IntelliSense v editoru, inteligentní značky můžete implementovat podle vytváření podtříd <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>a potom provádění <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> rozhraní a <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> rozhraní.  
  
> [!NOTE]
>  Podobným způsobem je možné implementovat další druhy značky.  
  
 Následující návod ukazuje, jak vytvořit inteligentní značky, které se zobrazí na aktuální slovo a má dvě navrhovaných akcí: **převést na velká písmena** a **převést na malá písmena**.  
  
## <a name="prerequisites"></a>Požadavky  
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Vytvoření projektu Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Chcete-li vytvořit projekt rozhraní MEF  
  
1.  Vytvořte projekt klasifikace Editor. Pojmenujte řešení `SmartTagTest`.  
  
2.  Otevřete soubor source.extension.vsixmanifest v editoru manifestu VSIX.  
  
3.  Ujistěte se, že **prostředky** oddíl obsahuje `Microsoft.VisualStudio.MefComponent` typ, **zdroj** je nastavena na `A project in current solution`, a **projektu** je nastavena na SmartTagTest.dll.  
  
4.  Uložte a zavřete source.extension.vsixmanifest.  
  
5.  Přidejte následující odkaz na projekt a nastavte **CopyLocal** k `false`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
6.  Odstraníte existující soubory tříd.  
  
## <a name="implementing-a-tagger-for-smart-tags"></a>Implementace Označovatel pro inteligentní značky  
  
#### <a name="to-implement-a-tagger-for-smart-tags"></a>K implementaci označovatel pro inteligentní značky  
  
1.  Přidejte soubor třídy a pojmenujte ho `TestSmartTag`.  
  
2.  Přidejte následující importy:  
  
     [!code-csharp[VSSDKSmartTagTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#1)]
     [!code-vb[VSSDKSmartTagTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#1)]  
  
3.  Přidejte třídu pojmenovanou `TestSmartTag` , která dědí z <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-csharp[VSSDKSmartTagTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#2)]
     [!code-vb[VSSDKSmartTagTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#2)]  
  
4.  Přidejte konstruktor pro tuto třídu, která volá základní konstruktor <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> z <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, což způsobí, že se zobrazí v rámci prvního znaku slova modrou čáru. (Pokud používáte <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, zobrazí se červená čára v posledním znakem slova.)  
  
     [!code-csharp[VSSDKSmartTagTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#3)]
     [!code-vb[VSSDKSmartTagTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#3)]  
  
5.  Přidejte třídu pojmenovanou `TestSmartTagger` , která dědí z <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typu `TestSmartTag`a implementuje <xref:System.IDisposable>.  
  
     [!code-csharp[VSSDKSmartTagTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#4)]
     [!code-vb[VSSDKSmartTagTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#4)]  
  
6.  Přidejte následující soukromé pole ke třídě označovatel.  
  
     [!code-csharp[VSSDKSmartTagTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#5)]
     [!code-vb[VSSDKSmartTagTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#5)]  
  
7.  Přidat konstruktor, který nastaví privátní pole a přihlásí se k odběru <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> událostí.  
  
     [!code-csharp[VSSDKSmartTagTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#6)]
     [!code-vb[VSSDKSmartTagTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#6)]  
  
8.  Implementace <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> tak, aby se vytvoří značku pro aktuálního slova. (Tato metoda také volá soukromou metodu `GetSmartTagActions` , který je vysvětlen později.)  
  
     [!code-csharp[VSSDKSmartTagTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#7)]
     [!code-vb[VSSDKSmartTagTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#7)]  
  
9. Přidat `GetSmartTagActions` metoda nastavení akce inteligentních značek. Akce, které sami jsou implementovány v dalších krocích.  
  
     [!code-csharp[VSSDKSmartTagTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#8)]
     [!code-vb[VSSDKSmartTagTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#8)]  
  
10. Deklarovat `SmartTagsChanged` událostí.  
  
     [!code-csharp[VSSDKSmartTagTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#9)]
     [!code-vb[VSSDKSmartTagTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#9)]  
  
11. Implementace `OnLayoutChanged` obslužnou rutinu události pro vyvolání `TagsChanged` událost, což způsobí, že <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> volat.  
  
     [!code-csharp[VSSDKSmartTagTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#10)]
     [!code-vb[VSSDKSmartTagTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#10)]  
  
12. Implementace <xref:System.IDisposable.Dispose%2A> metoda tak odhlásí, že <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> událostí.  
  
     [!code-csharp[VSSDKSmartTagTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#11)]
     [!code-vb[VSSDKSmartTagTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#11)]  
  
## <a name="implementing-the-smart-tag-tagger-provider"></a>Implementace zprostředkovatele Označovatel inteligentních značek  
  
#### <a name="to-implement-the-smart-tag-tagger-provider"></a>Pro implementaci zprostředkovatele označovatel inteligentních značek  
  
1.  Přidejte třídu pojmenovanou `TestSmartTagTaggerProvider` , která dědí z <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>. Exportujte ho pomocí <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text", <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> z před = "Výchozí" a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> z <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-csharp[VSSDKSmartTagTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#12)]
     [!code-vb[VSSDKSmartTagTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#12)]  
  
2.  Import <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> jako vlastnost.  
  
     [!code-csharp[VSSDKSmartTagTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#13)]
     [!code-vb[VSSDKSmartTagTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#13)]  
  
3.  Implementace <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metody.  
  
     [!code-csharp[VSSDKSmartTagTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#14)]
     [!code-vb[VSSDKSmartTagTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#14)]  
  
## <a name="implementing-smart-tag-actions"></a>Implementace akce inteligentních značek  
  
#### <a name="to-implement-smart-tag-actions"></a>K provedení akce inteligentních značek  
  
1. Vytvořte dvě třídy s názvem první `UpperCaseSmartTagAction` a druhé s názvem `LowerCaseSmartTagAction`. Implementovat obě třídy <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction>.  
  
    [!code-csharp[VSSDKSmartTagTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#15)]
    [!code-vb[VSSDKSmartTagTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#15)]  
  
    [!code-csharp[VSSDKSmartTagTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#16)]
    [!code-vb[VSSDKSmartTagTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#16)]  
  
   Obě třídy jsou stejné s tím rozdílem, že jeden volá <xref:System.String.ToUpper%2A> a jiných volání <xref:System.String.ToLower%2A>. Následujících krocích se dozvíte pouze třídu velká akce, ale je nutné implementovat obě třídy. Pomocí postupu pro implementaci velká akce jako vzor pro implementování malá akce.  
  
2. Deklarujte sadu privátní pole.  
  
    [!code-csharp[VSSDKSmartTagTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#17)]
    [!code-vb[VSSDKSmartTagTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#17)]  
  
3. Přidáte konstruktor, který nastaví pole.  
  
    [!code-csharp[VSSDKSmartTagTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#18)]
    [!code-vb[VSSDKSmartTagTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#18)]  
  
4. Implementace vlastnosti následujícím způsobem.  
  
    [!code-csharp[VSSDKSmartTagTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#19)]
    [!code-vb[VSSDKSmartTagTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#19)]  
  
5. Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction.Invoke%2A> metodu nahrazením text v rozsahu ekvivalentem velká písmena.  
  
    [!code-csharp[VSSDKSmartTagTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#20)]
    [!code-vb[VSSDKSmartTagTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#20)]  
  
## <a name="building-and-testing-the-code"></a>Vytváření a testování kódu  
 K otestování tohoto kódu sestavte řešení SmartTagTest a spusťte v experimentální instanci.  
  
#### <a name="to-build-and-test-the-smarttagtest-solution"></a>Pro vytváření a testování SmartTagTest řešení  
  
1.  Sestavte řešení.  
  
2.  Při spuštění tohoto projektu v ladicím programu, je vytvořena instance druhou instanci aplikace Visual Studio.  
  
3.  Vytvořte textový soubor a zadejte nějaký text.  
  
     V rámci první písmeno prvního slova textu má být zobrazena modrá čára.  
  
4.  Přesuňte ukazatel nad modrá čára.  
  
     Tlačítko má být zobrazena téměř ukazatel.  
  
5.  Když kliknete na tlačítko, dva navrhované akce má být zobrazena: **převést na velká písmena** a **převést na malá písmena**. Pokud kliknete na první akci, veškerý text v aktuálního slova mají být převedeny na velká písmena. Pokud kliknete na druhou akci, veškerý text mají být převedeny na malá písmena.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)