---
title: 'Návod: Zobrazení dokončování příkazů | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bdd96c124dafabf5584dfa13547cdea1e2b843b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879321"
---
# <a name="walkthrough-display-statement-completion"></a>Návod: Zobrazení dokončování příkazů
Doplňování výrazů založený na jazyce lze implementovat definováním identifikátory, pro které chcete poskytnout dokončení a potom aktivuje relace dokončení. Můžete definovat dokončování příkazů v rámci služby jazyka, definovat vlastní příponu názvu souboru a typu obsahu a pak zobrazí dokončení právě daného typu. Nebo můžete aktivovat dokončování pro existující typ obsahu, například "ve formátu prostého textu". Tento návod ukazuje, jak aktivovat doplňování výrazů pro typ obsahu "jako prostý text", což je typ obsahu textových souborů. Typ obsahu "text" je nadřazeného člena pro všechny ostatní typy obsahu, včetně kódu a soubory XML.  
  
 Dokončení příkazu se obvykle aktivuje po zadání určitých znaků, třeba tak, že zadáte počáteční identifikátor jako "pomocí". Obvykle se zavře stisknutím klávesy **MEZERNÍK**, **kartu**, nebo **Enter** klíč potvrďte výběr. Můžete implementovat funkce technologie IntelliSense, které aktivují při psaní znak pomocí obslužná rutina příkazu stisknutí kláves ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní) a zprostředkovatele obslužná rutina, která implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> rozhraní. Chcete-li vytvořit zdroj dokončení, což je seznam identifikátorů, které jsou součástí dokončení, implementovat <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> rozhraní a Zprostředkovatel zdroje dokončení ( <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> rozhraní). Poskytovatelé jsou součástí Managed Extensibility Framework (MEF). Odpovídají třídy zdroje a kontroler exportu a importu služby a můžou být zprostředkovatelé – například <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, která umožňuje navigaci ve vyrovnávací paměti textu a <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, která aktivuje relace dokončení.  
  
 Tento návod ukazuje, jak implementovat doplňování výrazů pro pevně zakódované sadu identifikátorů. V úplné implementací služba jazyka a dokumentace k jazyku odpovídají za poskytování obsahu.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnutý jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-mef-project"></a>Vytvořit projekt rozhraní MEF  
  
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
  
## <a name="implement-the-completion-source"></a>Implementace zdroje dokončení  
 Dokončení zdroje je zodpovědná za shromažďování sadu identifikátorů a přidávat obsah do okna dokončování, když uživatel zadá aktivační událost dokončení, jako je například prvních písmen identifikátoru. V tomto příkladu identifikátory a jejich popisy jsou pevně zakódované v <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metody. Ve většině využívá reálné můžete využít analyzátoru jazyka pro k získání tokenů k naplnění seznamu dokončení.  
  
### <a name="to-implement-the-completion-source"></a>K implementaci zdroji dokončení  
  
1.  Přidejte soubor třídy a pojmenujte ho `TestCompletionSource`.  
  
2.  Přidejte tyto importy:  
  
     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]  
  
3.  Upravte deklaraci třídy pro `TestCompletionSource` tak, aby implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]  
  
4.  Přidat soukromé pole pro poskytovatele zdrojového kódu, textovou vyrovnávací paměť a seznam <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> objekty (které odpovídají identifikátory, které se účastní relace dokončení):  
  
     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]  
  
5.  Přidáte konstruktor, který nastaví poskytovatel správy zdrojových a vyrovnávací paměti. `TestCompletionSourceProvider` Třída je definována v dalších krocích:  
  
     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]  
  
6.  Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metodu tak, že přidáte dokončení sady, která obsahuje dokončování, které chcete poskytnout v kontextu. Každá sada dokončení obsahuje sadu <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> dokončování a odpovídá na kartě okna dokončování. (V projektech Visual Basic jsou pojmenovány karty okna dokončování **běžné** a **všechny**.) `FindTokenSpanAtPosition` Metoda je definována v dalším kroku.  
  
     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]  
  
7.  Tyto metody slouží k vyhledání aktuálního slova z pozice kurzoru:  
  
     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]  
  
8.  Implementace `Dispose()` metody:  
  
     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]  
  
## <a name="implement-the-completion-source-provider"></a>Implementace zprostředkovatele zdrojového dokončení  
 Poskytovatel správy zdrojových dokončení je součást MEF, která vytváří instanci zdroje dokončení.  
  
### <a name="to-implement-the-completion-source-provider"></a>Pro implementaci zprostředkovatele zdroje dokončení  
  
1.  Přidejte třídu pojmenovanou `TestCompletionSourceProvider` , který implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Tato třída se exportovat <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "prostého textu" a <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "dokončení testu".  
  
     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]  
  
2.  Import <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, který vyhledá aktuálního slova ve zdroji dokončení.  
  
     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]  
  
3.  Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> metoda pro vytvoření instance zdroje dokončení.  
  
     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]  
  
## <a name="implement-the-completion-command-handler-provider"></a>Implementace zprostředkovatele obslužné rutiny dokončení příkazu  
 Zprostředkovatele obslužné rutiny dokončení příkazu je odvozen z <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, který čeká událost vytvoření zobrazení textu a převede zobrazení z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>– což umožňuje přidání příkazu do řetězce příkazového prostředí nástroje Visual Studio – do <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Protože tato třída je MEF export, slouží také k importu služby, které jsou vyžadované samotná obslužná rutina příkazu.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Pro implementaci zprostředkovatele obslužné rutiny dokončení příkazu  
  
1.  Přidejte do ní soubor `TestCompletionCommandHandler`.  
  
2.  Přidejte tyto pomocí příkazů:  
  
     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]  
  
3.  Přidejte třídu pojmenovanou `TestCompletionHandlerProvider` , který implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Exportovat pomocí této třídy <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "obslužné rutiny tokenů dokončení", <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "prostého textu" a <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> z <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.  
  
     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]  
  
4.  Import <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, což umožňuje převod z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> k <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>a <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> , která umožňuje přístup ke standardním službám Visual Studio.  
  
     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]  
  
5.  Implementace <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metoda pro vytvoření instance obslužná rutina příkazu.  
  
     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]  
  
## <a name="implement-the-completion-command-handler"></a>Implementace obslužné rutiny dokončení příkazu  
 Vzhledem k tomu, že dokončení příkazu se aktivuje úhozy na klávesnici, musí implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní pro příjem a zpracování stisknutí kláves, které aktivují, potvrdit a zavřít relace dokončení.  
  
#### <a name="to-implement-the-completion-command-handler"></a>K implementaci obslužné rutiny dokončení příkazu  
  
1. Přidejte třídu pojmenovanou `TestCompletionCommandHandler` , který implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]  
  
2. Přidat soukromé pole pro další obslužná rutina příkazu (pro který předáte příkazu), zobrazení textu, poskytovateli obslužná rutina příkazu (která umožňuje přístup k různým službám) a ukončení relace:  
  
    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]  
  
3. Přidejte konstruktor, který nastaví zobrazení textu a pole zprostředkovatele a přidá příkazu do příkazového řetězce:  
  
    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]  
  
4. Implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu předáním příkaz podél:  
  
    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]  
  
5. Implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody. Když tato metoda obdrží jedním stisknutím tlačítka, musíte udělat jednu z těchto věcí:  
  
   - Povolte znak, který má být zapsána do vyrovnávací paměti a potom aktivovat nebo filtrování dokončení. (Tisk znaků to provést.)  
  
   - Potvrdit dokončení, ale neumožňují znak, který má být zapsána do vyrovnávací paměti. (Prázdné znaky, **kartu**, a **Enter** to dělat, když se zobrazí relace dokončení.)  
  
   - Povolte příkaz, které se mají předat další obslužné rutiny. (Všechny ostatní příkazy.)  
  
     Protože tato metoda může zobrazit uživatelské rozhraní, zavolejte <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> abyste měli jistotu, že není volána v kontextu služby automation:  
  
     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]  
  
6. Tento kód je privátní metodu, která aktivuje relace dokončení:  
  
    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]  
  
7. Následující příklad je privátní metodu, která odhlásí <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> události:  
  
    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]  
  
## <a name="build-and-test-the-code"></a>Vytváření a testování kódu  
 K otestování tohoto kódu sestavte řešení CompletionTest a spusťte v experimentální instanci.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>Pro vytváření a testování CompletionTest řešení  
  
1.  Sestavte řešení.  
  
2.  Při spuštění tohoto projektu v ladicím programu se spustí druhé instanci aplikace Visual Studio.  
  
3.  Vytvořte textový soubor a zadejte nějaký text, který obsahuje slovo "Přidání".  
  
4.  Při psaní nejprve "a" a potom "d", by se zobrazit seznam, který obsahuje "Přidání" a "úpravy". Všimněte si, že je vybraná sčítání. Pokud zadáte jiný "d", v seznamu by měla obsahovat pouze "Přidání", který je teď vybrán. Můžete potvrdit "Přidání" stisknutím klávesy **MEZERNÍK**, **kartu**, nebo **Enter** klíče, nebo zavřete seznam tak, že zadáte Esc ani jiného klíče.  
  
## <a name="see-also"></a>Viz také:  
 [Návod: Propojení typ obsahu, který má příponu názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)