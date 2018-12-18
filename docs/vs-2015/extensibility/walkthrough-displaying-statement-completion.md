---
title: 'Návod: Zobrazení dokončování příkazů | Dokumentace Microsoftu'
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
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 097cb671e15b75edd7e61f7860cf3a0c03123c9b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733041"
---
# <a name="walkthrough-displaying-statement-completion"></a>Návod: Zobrazení dokončování příkazů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Doplňování výrazů založený na jazyce lze implementovat definováním identifikátory, pro které chcete poskytnout dokončení a potom aktivuje relace dokončení. Můžete definovat dokončování příkazů v rámci služby jazyka, definovat vlastní příponu názvu souboru a typu obsahu a pak zobrazí dokončení právě daného typu, nebo můžete aktivovat dokončování pro existující typ obsahu, například "ve formátu prostého textu". Tento návod ukazuje, jak aktivovat doplňování výrazů pro typ obsahu "jako prostý text", což je typ obsahu textových souborů. Typ obsahu "text" je nadřazeného člena pro všechny ostatní typy obsahu, včetně kódu a soubory XML.  
  
 Dokončení příkazu se obvykle aktivuje po zadání určitých znaků, třeba tak, že zadáte počáteční identifikátor jako "pomocí". To je obvykle zrušená stisknutím klávesy MEZERNÍK, tabulátor nebo Enter k potvrzení výběru. Můžete implementovat funkce technologie IntelliSense, které jsou aktivovány zadáním znaku s použitím obslužná rutina příkazu stisknutí kláves ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní) a zprostředkovatele obslužná rutina, která implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> rozhraní. Chcete-li vytvořit zdroj dokončení, což je seznam identifikátorů, které jsou součástí dokončení, implementovat <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> rozhraní a Zprostředkovatel zdroje dokončení ( <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> rozhraní). Poskytovatelé jsou součástí Managed Extensibility Framework (MEF). Zodpovídají za třídy zdroje a kontroler exportu a importu služby a můžou být zprostředkovatelé – například <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, která umožňuje navigaci ve vyrovnávací paměti textu a <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, která aktivuje relace dokončení.  
  
 Tento návod ukazuje, jak implementovat doplňování výrazů pro pevně zakódované sadu identifikátorů. V úplné implementací služba jazyka a dokumentace k jazyku odpovídají za poskytování obsahu.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Vytvoření projektu rozhraní MEF  
  
#### <a name="to-create-a-mef-project"></a>Chcete-li vytvořit projekt rozhraní MEF  
  
1.  Vytvořte projekt VSIX C#. (V **nový projekt** dialogového okna, vyberte **Visual C# / rozšíření**, pak **projekt VSIX**.) Pojmenujte řešení `CompletionTest`.  
  
2.  Přidejte do projektu šablony položky editoru třídění. Další informace najdete v tématu [vytváření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Odstraníte existující soubory tříd.  
  
4.  Přidejte následující odkazy do projektu a ujistěte se, že **CopyLocal** je nastavena na `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Sestavení Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-the-completion-source"></a>Implementace zdroje dokončení  
 Dokončení zdroje je zodpovědná za shromažďování sadu identifikátorů a přidávat obsah do okna dokončování, když uživatel zadá aktivační událost dokončení, jako je například prvních písmen identifikátoru. V tomto příkladu identifikátory a jejich popisy jsou pevně zakódované v <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metody. Ve většině využívá reálné můžete využít analyzátoru jazyka pro k získání tokenů k naplnění seznamu dokončení.  
  
#### <a name="to-implement-the-completion-source"></a>K implementaci zdroji dokončení  
  
1.  Přidejte soubor třídy a pojmenujte ho `TestCompletionSource`.  
  
2.  Přidejte tyto importy:  
  
     [!code-csharp[VSSDKCompletionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#1)]
     [!code-vb[VSSDKCompletionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#1)]  
  
3.  Upravte deklaraci třídy pro `TestCompletionSource` tak, aby implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-csharp[VSSDKCompletionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#2)]
     [!code-vb[VSSDKCompletionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#2)]  
  
4.  Přidat soukromé pole pro poskytovatele zdrojového kódu, textovou vyrovnávací paměť a seznam <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> objekty (které odpovídají identifikátory, které se účastní relace dokončení):  
  
     [!code-csharp[VSSDKCompletionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#3)]
     [!code-vb[VSSDKCompletionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#3)]  
  
5.  Přidáte konstruktor, který nastaví poskytovatel správy zdrojových a vyrovnávací paměti. `TestCompletionSourceProvider` Třída je definována v dalších krocích:  
  
     [!code-csharp[VSSDKCompletionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#4)]
     [!code-vb[VSSDKCompletionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#4)]  
  
6.  Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metodu tak, že přidáte dokončení sady, která obsahuje dokončování, které chcete poskytnout v kontextu. Každá sada dokončení obsahuje sadu <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> dokončování a odpovídá na kartě okna dokončování. (V projektech Visual Basic jsou pojmenovány karty okna dokončování **běžné** a **všechny**.) Metoda FindTokenSpanAtPosition je definována v dalším kroku.  
  
     [!code-csharp[VSSDKCompletionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#5)]
     [!code-vb[VSSDKCompletionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#5)]  
  
7.  Tyto metody slouží k vyhledání aktuálního slova z pozice kurzoru:  
  
     [!code-csharp[VSSDKCompletionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#6)]
     [!code-vb[VSSDKCompletionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#6)]  
  
8.  Implementace `Dispose()` metody:  
  
     [!code-csharp[VSSDKCompletionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#7)]
     [!code-vb[VSSDKCompletionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#7)]  
  
## <a name="implementing-the-completion-source-provider"></a>Implementace zprostředkovatele zdroje dokončení  
 Poskytovatel správy zdrojových dokončení je součást MEF, která vytváří instanci zdroje dokončení.  
  
#### <a name="to-implement-the-completion-source-provider"></a>Pro implementaci zprostředkovatele zdroje dokončení  
  
1.  Přidejte třídu pojmenovanou `TestCompletionSourceProvider` , který implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Tato třída se exportovat <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "prostého textu" a <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "dokončení testu".  
  
     [!code-csharp[VSSDKCompletionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#8)]
     [!code-vb[VSSDKCompletionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#8)]  
  
2.  Import <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, který se používá k vyhledání ve zdroji dokončování aktuálního slova.  
  
     [!code-csharp[VSSDKCompletionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#9)]
     [!code-vb[VSSDKCompletionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#9)]  
  
3.  Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> metoda pro vytvoření instance zdroje dokončení.  
  
     [!code-csharp[VSSDKCompletionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#10)]
     [!code-vb[VSSDKCompletionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#10)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>Implementace zprostředkovatele obslužné rutiny dokončení příkazu  
 Zprostředkovatele obslužné rutiny dokončení příkazu je odvozen z <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, který čeká událost vytvoření zobrazení textu a převede zobrazení z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>– což umožňuje přidání příkazu do řetězce příkazového prostředí nástroje Visual Studio – do <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Protože tato třída je MEF export, slouží také k importu služby, které jsou vyžadované samotná obslužná rutina příkazu.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Pro implementaci zprostředkovatele obslužné rutiny dokončení příkazu  
  
1.  Přidejte do ní soubor `TestCompletionCommandHandler`.  
  
2.  Přidejte tyto pomocí příkazů:  
  
     [!code-csharp[VSSDKCompletionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#11)]
     [!code-vb[VSSDKCompletionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#11)]  
  
3.  Přidejte třídu pojmenovanou `TestCompletionHandlerProvider` , který implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Exportovat pomocí této třídy <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "obslužné rutiny tokenů dokončení", <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "prostého textu" a <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> z <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.  
  
     [!code-csharp[VSSDKCompletionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#12)]
     [!code-vb[VSSDKCompletionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#12)]  
  
4.  Import <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, což umožňuje převod z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> k <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>a <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> , která umožňuje přístup ke standardním službám Visual Studio.  
  
     [!code-csharp[VSSDKCompletionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#13)]
     [!code-vb[VSSDKCompletionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#13)]  
  
5.  Implementace <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metoda pro vytvoření instance obslužná rutina příkazu.  
  
     [!code-csharp[VSSDKCompletionTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#14)]
     [!code-vb[VSSDKCompletionTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#14)]  
  
## <a name="implementing-the-completion-command-handler"></a>Implementace obslužné rutiny dokončení příkazu  
 Vzhledem k tomu, že dokončení příkazu se aktivuje úhozy na klávesnici, musí implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní pro příjem a zpracování stisknutí kláves, které aktivují, potvrdit a zavřít relace dokončení.  
  
#### <a name="to-implement-the-completion-command-handler"></a>K implementaci obslužné rutiny dokončení příkazu  
  
1. Přidejte třídu pojmenovanou `TestCompletionCommandHandler` , který implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
    [!code-csharp[VSSDKCompletionTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#15)]
    [!code-vb[VSSDKCompletionTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#15)]  
  
2. Přidat soukromé pole pro další obslužná rutina příkazu (pro který předáte příkazu), zobrazení textu, poskytovateli obslužná rutina příkazu (která umožňuje přístup k různým službám) a ukončení relace:  
  
    [!code-csharp[VSSDKCompletionTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#16)]
    [!code-vb[VSSDKCompletionTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#16)]  
  
3. Přidejte konstruktor, který nastaví zobrazení textu a pole zprostředkovatele a přidá příkazu do příkazového řetězce:  
  
    [!code-csharp[VSSDKCompletionTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#17)]
    [!code-vb[VSSDKCompletionTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#17)]  
  
4. Implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu předáním příkaz podél:  
  
    [!code-csharp[VSSDKCompletionTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#18)]
    [!code-vb[VSSDKCompletionTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#18)]  
  
5. Implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody. Když tato metoda obdrží jedním stisknutím tlačítka, musíte udělat jednu z těchto věcí:  
  
   - Povolte znak, který má být zapsána do vyrovnávací paměti a potom aktivovat nebo filtrování dokončení. (Tisk znaků to provést.)  
  
   - Potvrdit dokončení, ale neumožňují znak, který má být zapsána do vyrovnávací paměti. (Prázdné znaky, karty a Enter provést při ukončení relace se zobrazí.)  
  
   - Povolte příkaz, které se mají předat další obslužné rutiny. (Všechny ostatní příkazy.)  
  
     Protože tato metoda může zobrazit uživatelské rozhraní, zavolejte <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> abyste měli jistotu, že není volána v kontextu služby automation:  
  
     [!code-csharp[VSSDKCompletionTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#19)]
     [!code-vb[VSSDKCompletionTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#19)]  
  
6. Tento kód je privátní metodu, která aktivuje relace dokončení:  
  
    [!code-csharp[VSSDKCompletionTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#20)]
    [!code-vb[VSSDKCompletionTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#20)]  
  
7. Následující příklad je privátní metodu, která odhlásí <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> události:  
  
    [!code-csharp[VSSDKCompletionTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#21)]
    [!code-vb[VSSDKCompletionTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#21)]  
  
## <a name="building-and-testing-the-code"></a>Vytváření a testování kódu  
 K otestování tohoto kódu sestavte řešení CompletionTest a spusťte v experimentální instanci.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>Pro vytváření a testování CompletionTest řešení  
  
1.  Sestavte řešení.  
  
2.  Při spuštění tohoto projektu v ladicím programu, je vytvořena instance druhou instanci aplikace Visual Studio.  
  
3.  Vytvořte textový soubor a zadejte nějaký text, který obsahuje slovo "Přidání".  
  
4.  Při psaní nejprve "a" a potom "d", by měl zobrazit seznam, který obsahuje "Přidání" a "úpravy". Všimněte si, že je vybraná sčítání. Pokud zadáte jiný "d", v seznamu by měla obsahovat pouze "Přidání", který je teď vybrán. Můžete potvrdit "Přidání" stisknutím klávesy MEZERNÍK, tabulátor nebo Enter nebo zavřete seznam tak, že zadáte Esc ani jiného klíče.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

