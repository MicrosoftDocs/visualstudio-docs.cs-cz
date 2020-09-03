---
title: 'Návod: zobrazení dokončování příkazů | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 37
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: db4e63beb1e3d4ff53e547492ae9eae7ee8001e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202015"
---
# <a name="walkthrough-displaying-statement-completion"></a>Návod: Zobrazení dokončování příkazů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Doplňování příkazů založeného na jazyce můžete implementovat definováním identifikátorů, pro které chcete poskytnout dokončení, a následnou aktivací relace dokončení. Můžete definovat dokončování příkazů v kontextu jazykové služby, definovat vlastní příponu názvu souboru a typ obsahu a pak zobrazit dokončení pouze pro tento typ, nebo můžete spustit dokončení pro existující typ obsahu, například "prostý text". Tento návod ukazuje, jak aktivovat dokončování příkazů pro typ obsahu "prostý text", což je typ obsahu textových souborů. Typ obsahu "text" je nadřazeným prvkem všech dalších typů obsahu, včetně kódu a souborů XML.  
  
 Dokončení příkazu se obvykle aktivuje zadáním určitých znaků, například zadáním začátku identifikátoru, jako je "using". Obvykle se vynechává, když stisknete klávesu MEZERNÍK, TAB nebo ENTER, potvrďte výběr. Můžete implementovat funkce technologie IntelliSense, které jsou aktivovány zadáním znaku pomocí obslužné rutiny příkazu pro stisknutí kláves ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní) a zprostředkovatele obslužné rutiny, který implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> rozhraní. Chcete-li vytvořit zdroj dokončení, což je seznam identifikátorů, které se účastní dokončení, implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> rozhraní a poskytovatele zdroje dokončení ( <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> rozhraní). Poskytovatelé jsou součásti komponenty Managed Extensibility Framework (MEF). Zodpovídá za exportování tříd source a Controller a importu služeb a zprostředkovatelů – například <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , který umožňuje navigaci ve vyrovnávací paměti textu a na <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> , který spouští relaci dokončení.  
  
 Tento návod ukazuje, jak implementovat dokončování příkazů pro pevně zakódovanou sadu identifikátorů. V úplných implementacích zodpovídá služba jazyka a jazykovou dokumentaci za poskytnutí tohoto obsahu.  
  
## <a name="prerequisites"></a>Předpoklady  
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Vytvoření projektu MEF  
  
#### <a name="to-create-a-mef-project"></a>Vytvoření projektu MEF  
  
1. Vytvoří projekt VSIX v jazyce C#. (V dialogovém okně **Nový projekt** vyberte **Visual C#/rozšiřitelnost**a potom **projekt VSIX**.) Pojmenujte řešení `CompletionTest` .  
  
2. Přidejte do projektu šablonu položky klasifikátoru editoru. Další informace naleznete v tématu [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Odstraňte existující soubory třídy.  
  
4. Do projektu přidejte následující odkazy a ujistěte se, že je **CopyLocal** nastavené na `false` :  
  
     Microsoft. VisualStudio. Editor  
  
     Microsoft. VisualStudio. Language. IntelliSense  
  
     Microsoft. VisualStudio. OLE. Interop  
  
     Microsoft. VisualStudio. Shell. 14.0  
  
     Microsoft. VisualStudio. Shell. unmutable. 10.0  
  
     Microsoft. VisualStudio. TextManager. Interop  
  
## <a name="implementing-the-completion-source"></a>Implementace zdroje dokončení  
 Zdroj dokončení zodpovídá za shromáždění sady identifikátorů a přidání obsahu do okna dokončení, když uživatel zadá aktivační událost dokončení, například první písmena identifikátoru. V tomto příkladu jsou identifikátory a jejich popisy pevně kódované v <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metodě. Ve většině reálných použití byste pomocí analyzátoru jazyka získali tokeny k naplnění seznamu dokončení.  
  
#### <a name="to-implement-the-completion-source"></a>Implementace zdroje dokončení  
  
1. Přidejte soubor třídy a pojmenujte ho `TestCompletionSource` .  
  
2. Přidejte tyto importy:  
  
     [!code-csharp[VSSDKCompletionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#1)]
     [!code-vb[VSSDKCompletionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#1)]  
  
3. Upravte deklaraci třídy pro `TestCompletionSource` tak, aby implementovala <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> :  
  
     [!code-csharp[VSSDKCompletionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#2)]
     [!code-vb[VSSDKCompletionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#2)]  
  
4. Přidejte soukromá pole pro poskytovatele zdroje, textovou vyrovnávací paměť a seznam <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> objektů (které odpovídají identifikátorům, které se budou podílet na relaci dokončení):  
  
     [!code-csharp[VSSDKCompletionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#3)]
     [!code-vb[VSSDKCompletionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#3)]  
  
5. Přidejte konstruktor, který nastaví zprostředkovatele zdroje a vyrovnávací paměť. `TestCompletionSourceProvider`Třída je definována v pozdějších krocích:  
  
     [!code-csharp[VSSDKCompletionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#4)]
     [!code-vb[VSSDKCompletionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#4)]  
  
6. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metodu přidáním sady dokončení, která obsahuje dokončování, které chcete zadat v kontextu. Každá sada dokončení obsahuje sadu <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> dokončovacích operací a odpovídá kartě okna dokončení. (V Visual Basic projekty karty okna pro dokončení se nazývají **Common** a **All**.) Metoda FindTokenSpanAtPosition je definována v dalším kroku.  
  
     [!code-csharp[VSSDKCompletionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#5)]
     [!code-vb[VSSDKCompletionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#5)]  
  
7. Následující metoda slouží k vyhledání aktuálního slova z pozice kurzoru:  
  
     [!code-csharp[VSSDKCompletionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#6)]
     [!code-vb[VSSDKCompletionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#6)]  
  
8. Implementujte `Dispose()` metodu:  
  
     [!code-csharp[VSSDKCompletionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#7)]
     [!code-vb[VSSDKCompletionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#7)]  
  
## <a name="implementing-the-completion-source-provider"></a>Implementace poskytovatele zdroje dokončení  
 Poskytovatel zdroje dokončení je část komponenty MEF, která vytvoří instanci zdroje dokončení.  
  
#### <a name="to-implement-the-completion-source-provider"></a>Implementace poskytovatele zdroje dokončení  
  
1. Přidejte třídu s názvem `TestCompletionSourceProvider` , která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> . Exportujte tuto třídu s použitím <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "prostého textu" a typu <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "dokončení testu".  
  
     [!code-csharp[VSSDKCompletionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#8)]
     [!code-vb[VSSDKCompletionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#8)]  
  
2. Importujte <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , který slouží k vyhledání aktuálního slova ve zdroji dokončení.  
  
     [!code-csharp[VSSDKCompletionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#9)]
     [!code-vb[VSSDKCompletionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#9)]  
  
3. Implementací <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> metody vytvořte instanci zdroje dokončení.  
  
     [!code-csharp[VSSDKCompletionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#10)]
     [!code-vb[VSSDKCompletionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#10)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>Implementace zprostředkovatele obslužné rutiny příkazu pro dokončení  
 Zprostředkovatel obslužné rutiny příkazu pro dokončení je odvozen z typu <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> , který naslouchá události vytváření zobrazení textu a převádí zobrazení z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> , což umožňuje přidání příkazu do řetězce příkazu prostředí sady Visual Studio – do <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . Vzhledem k tomu, že tato třída je exportem MEF, můžete ji také použít k importu služeb, které jsou vyžadovány samotným obslužnou rutinou příkazu.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Implementace zprostředkovatele obslužných rutin příkazu pro dokončení  
  
1. Přidejte soubor s názvem `TestCompletionCommandHandler` .  
  
2. Přidejte tyto příkazy pomocí příkazu:  
  
     [!code-csharp[VSSDKCompletionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#11)]
     [!code-vb[VSSDKCompletionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#11)]  
  
3. Přidejte třídu s názvem `TestCompletionHandlerProvider` , která implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . Exportujte tuto třídu s <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "obslužným rutinou dokončení tokenu", <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "prostého textu" a <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> a <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable> .  
  
     [!code-csharp[VSSDKCompletionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#12)]
     [!code-vb[VSSDKCompletionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#12)]  
  
4. Importujte <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , který umožňuje převod z typu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> na <xref:Microsoft.VisualStudio.Text.Editor.ITextView> , a, a, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> který umožňuje přístup ke standardním službám sady Visual Studio.  
  
     [!code-csharp[VSSDKCompletionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#13)]
     [!code-vb[VSSDKCompletionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#13)]  
  
5. Implementujte <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metodu pro vytvoření instance obslužné rutiny příkazu.  
  
     [!code-csharp[VSSDKCompletionTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#14)]
     [!code-vb[VSSDKCompletionTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#14)]  
  
## <a name="implementing-the-completion-command-handler"></a>Implementace obslužné rutiny příkazu pro dokončení  
 Vzhledem k tomu, že dokončování příkazů se spouští pomocí klávesových úhozů, je nutné implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní pro příjem a zpracování klávesových úhozů, které aktivují, potvrzují a odstavují relaci dokončení.  
  
#### <a name="to-implement-the-completion-command-handler"></a>Implementace obslužné rutiny příkazu pro dokončení  
  
1. Přidejte třídu s názvem `TestCompletionCommandHandler` , která implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :  
  
    [!code-csharp[VSSDKCompletionTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#15)]
    [!code-vb[VSSDKCompletionTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#15)]  
  
2. Přidejte soukromá pole pro následující obslužnou rutinu příkazu (do kterého předáte příkaz), textové zobrazení, zprostředkovatele obslužné rutiny příkazů (umožňující přístup k různým službám) a relaci dokončení:  
  
    [!code-csharp[VSSDKCompletionTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#16)]
    [!code-vb[VSSDKCompletionTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#16)]  
  
3. Přidejte konstruktor, který nastaví textové zobrazení a pole poskytovatele a přidá příkaz do řetězce příkazu:  
  
    [!code-csharp[VSSDKCompletionTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#17)]
    [!code-vb[VSSDKCompletionTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#17)]  
  
4. Implementujte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu předáním příkazu společně:  
  
    [!code-csharp[VSSDKCompletionTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#18)]
    [!code-vb[VSSDKCompletionTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#18)]  
  
5. Implementujte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodu. Pokud tato metoda obdrží klávesovou zkratku, musí provést jednu z následujících akcí:  
  
   - Umožňuje zapsat znak do vyrovnávací paměti a pak aktivovat nebo filtrovat dokončení. (Tisk znaků.)  
  
   - Potvrďte dokončení, ale nepovolujte, aby byl znak zapsaný do vyrovnávací paměti. (Prázdný znak, tabulátor a zadejte, když se zobrazí relace dokončování.)  
  
   - Povolí předání příkazu k další obslužné rutině. (Všechny ostatní příkazy.)  
  
     Vzhledem k tomu, že tato metoda může zobrazit uživatelské rozhraní, zavolejte a ujistěte se <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> , že není volána v kontextu automatizace:  
  
     [!code-csharp[VSSDKCompletionTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#19)]
     [!code-vb[VSSDKCompletionTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#19)]  
  
6. Tento kód je soukromá metoda, která spustí relaci dokončení:  
  
    [!code-csharp[VSSDKCompletionTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#20)]
    [!code-vb[VSSDKCompletionTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#20)]  
  
7. Dalším příkladem je soukromá metoda, která odhlašuje odběr <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> události:  
  
    [!code-csharp[VSSDKCompletionTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#21)]
    [!code-vb[VSSDKCompletionTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#21)]  
  
## <a name="building-and-testing-the-code"></a>Sestavování a testování kódu  
 Chcete-li otestovat tento kód, sestavte řešení CompletionTest a spusťte ho v experimentální instanci.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>Sestavení a testování řešení CompletionTest  
  
1. Sestavte řešení.  
  
2. Při spuštění tohoto projektu v ladicím programu je vytvořena instance druhé instance aplikace Visual Studio.  
  
3. Vytvořte textový soubor a zadejte nějaký text, který obsahuje slovo "Přidat".  
  
4. Když zadáte první "a" a potom "d", zobrazí se seznam obsahující "sčítání" a "přizpůsobení". Všimněte si, že je vybraná možnost přidání. Když zadáte jiný text "d", seznam by měl obsahovat pouze "sčítání", které jsou nyní vybrány. Kliknutím na klávesu MEZERNÍK, TAB nebo ENTER můžete potvrdit "sčítání", nebo můžete seznam zavřít zadáním klávesy ESC nebo jiného klíče.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
