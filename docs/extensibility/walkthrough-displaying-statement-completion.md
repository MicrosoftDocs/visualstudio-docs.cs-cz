---
title: 'Návod: Zobrazení dokončení výkazu | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 1d2f5499511c9dc0bbb6711d0da630315384f8e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697417"
---
# <a name="walkthrough-display-statement-completion"></a>Návod: Zobrazení dokončení příkazu
Dokončení příkazu založeného na jazyce můžete implementovat definováním identifikátorů, pro které chcete poskytnout dokončení, a aktivací relace dokončení. Můžete definovat dokončení příkazu v kontextu jazykové služby, definovat vlastní příponu názvu souboru a typ obsahu a potom zobrazit dokončení právě pro tento typ. Nebo můžete aktivovat dokončování pro existující typ obsahu – například "prostý text". Tento návod ukazuje, jak aktivovat dokončení příkazu pro typ obsahu "ve formátu prostého textu", což je typ obsahu textových souborů. Typ obsahu "text" je předchůdcem všech ostatních typů obsahu, včetně kódu a souborů XML.

 Dokončení příkazu se obvykle spouští zadáním určitých znaků – například zadáním začátku identifikátoru, například "using". Obvykle se zavře stisknutím **mezerníku**, **tabulátoru**nebo **klávesy Enter** pro potvrzení výběru. Můžete implementovat funkce IntelliSense, které se aktivují při psaní znaku <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pomocí obslužné rutiny <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> příkazů pro úhozy (rozhraní) a poskytovatele obslužné rutiny, který implementuje rozhraní. Chcete-li vytvořit zdroj dokončení, což je seznam identifikátorů, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> které se účastní dokončení, implementujte rozhraní a zprostředkovatele zdroje dokončení <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> (rozhraní). Zprostředkovatelé jsou součásti architektury spravované rozšiřitelnosti (MEF). Jsou zodpovědní za export tříd zdrojového a kontroleru a import služeb <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>a zprostředkovatelů – například <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, který umožňuje navigaci v textové vyrovnávací paměti, a , který aktivuje relaci dokončení.

 Tento návod ukazuje, jak implementovat dokončení příkazu pro pevně zakódovanou sadu identifikátorů. V úplných implementacích je za poskytnutí tohoto obsahu zodpovědná jazyková služba a jazyková dokumentace.

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015, nenainstalujete Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Vytvoření projektu MEF

#### <a name="to-create-a-mef-project"></a>Vytvoření projektu MEF

1. Vytvořte projekt C# VSIX. (V dialogovém okně **Nový projekt** vyberte možnost **Vizuální C# / Rozšiřitelnost**a potom **v six projectu**.) Pojmenujte `CompletionTest`řešení .

2. Přidejte do projektu šablonu položky třídění editoru. Další informace naleznete [v tématu Vytvoření rozšíření se šablonou položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Odstraňte existující soubory tříd.

4. Přidejte do projektu následující odkazy a ujistěte se, že **copylocal** je nastavena na `false`:

     Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.Shell.15.0

     Microsoft.VisualStudio.Shell.Immutable.10.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-the-completion-source"></a>Implementace zdroje dokončení
 Zdroj dokončení je zodpovědný za shromažďování sadu identifikátorů a přidání obsahu do okna dokončení, když uživatel zadá aktivační událost dokončení, například první písmena identifikátoru. V tomto příkladu jsou identifikátory a jejich popisy <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> pevně zakódovány v metodě. Ve většině reálných použití byste pomocí analyzátoru jazyka získali tokeny k naplnění seznamu dokončení.

### <a name="to-implement-the-completion-source"></a>Implementace zdroje dokončení

1. Přidejte soubor třídy `TestCompletionSource`a pojmenujte jej .

2. Přidejte tyto importy:

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. Upravte deklaraci `TestCompletionSource` třídy tak, aby implementovala <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. Přidejte soukromá pole pro zdrojového zprostředkovatele, <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> textovou vyrovnávací paměť a seznam objektů (které odpovídají identifikátorům, které se budou účastnit relace dokončení):

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. Přidejte konstruktor, který nastaví zdrojového zprostředkovatele a vyrovnávací paměť. Třída `TestCompletionSourceProvider` je definována v pozdějších krocích:

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metodu přidáním sady dokončení, která obsahuje dokončení, které chcete poskytnout v kontextu. Každá sada dokončení obsahuje <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> sadu dokončení a odpovídá kartě okna dokončení. (V projektech jazyka Visual Basic karty okna dokončení s názvem **Společné** a **Všechny**.) Metoda `FindTokenSpanAtPosition` je definována v dalším kroku.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. Následující metoda se používá k nalezení aktuální ho slova z pozice kurzoru:

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. Zavést `Dispose()` metodu:

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>Implementace zprostředkovatele zdroje dokončení
 Zprostředkovatel zdroje dokončení je součást mef součást, která inkonzí zdroj dokončení.

### <a name="to-implement-the-completion-source-provider"></a>Implementace zprostředkovatele zdroje dokončení

1. Přidejte třídu s názvem, `TestCompletionSourceProvider` která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Exportujte tuto <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> třídu s "prostým textem" <xref:Microsoft.VisualStudio.Utilities.NameAttribute> a "dokončením testu".

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. Importace <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, která vyhledá aktuální slovo ve zdroji dokončení.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> metodu k vytvoření instance zdroje dokončení.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>Implementace zprostředkovatele obslužné rutiny příkazu dokončení
 Zprostředkovatel obslužné rutiny <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>příkazu dokončení je odvozen od aplikace , která <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>naslouchá události vytvoření textového zobrazení a převádí <xref:Microsoft.VisualStudio.Text.Editor.ITextView>zobrazení z –, které umožňuje přidání příkazu do řetězce příkazů prostředí sady Visual Studio – na . Vzhledem k tomu, že tato třída je export MEF, můžete také použít k importu služeb, které jsou vyžadovány obslužnou rutinou příkazu sám.

#### <a name="to-implement-the-completion-command-handler-provider"></a>Implementace zprostředkovatele obslužné rutiny příkazu dokončení

1. Přidejte soubor `TestCompletionCommandHandler`s názvem .

2. Přidejte tyto pomocí direktiv:

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. Přidejte třídu s názvem, `TestCompletionHandlerProvider` která implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Exportovat tuto <xref:Microsoft.VisualStudio.Utilities.NameAttribute> třídu s "obslužné rutiny dokončení tokenu", a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "prostý text" a a <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> . <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. Importovat <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, který umožňuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> převod <xref:Microsoft.VisualStudio.Text.Editor.ITextView>z <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>a <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> , a, a který umožňuje přístup ke standardním službám sady Visual Studio.

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. Implementujte <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metodu k vytvoření instance obslužné rutiny příkazu.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>Implementace obslužné rutiny příkazu dokončení
 Vzhledem k tomu, že dokončení příkazu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> je spuštěno úhozy kláves, je nutné implementovat rozhraní pro příjem a zpracování úhozů, které aktivují, potvrdí a zamítnou relaci dokončení.

#### <a name="to-implement-the-completion-command-handler"></a>Implementace obslužné rutiny příkazu dokončení

1. Přidejte třídu s názvem, `TestCompletionCommandHandler` která implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. Přidejte soukromá pole pro další obslužnou rutinu příkazu (do které příkaz předáte), textové zobrazení, zprostředkovatele obslužné rutiny příkazu (který umožňuje přístup k různým službám) a relaci dokončení:

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. Přidejte konstruktor, který nastaví textové zobrazení a pole zprostředkovatele, a přidá příkaz do řetězce příkazů:

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. Implementujte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu předáním příkazu:

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. Implementujte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodu. Když tato metoda obdrží stisknutí klávesy, musí provést jednu z těchto věcí:

   - Povolit znak, který má být zapsán do vyrovnávací paměti a potom aktivovat nebo filtr dokončení. (Tisk znaků to provést.)

   - Potvrďte dokončení, ale nepovolte znak, který má být zapsán do vyrovnávací paměti. (Mezery, **Tabulátor**a **Enter** to dělají, když se zobrazí relace dokončení.)

   - Povolit předání příkazu další obslužné rutině. (Všechny ostatní příkazy.)

     Vzhledem k tomu, že <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> tato metoda může zobrazit uživatelské rozhraní, volání a ujistěte se, že není volána v kontextu automatizace:

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. Tento kód je soukromá metoda, která aktivuje relaci dokončení:

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. Dalším příkladem je soukromá metoda, která <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> se odhlásí z události:

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>Sestavení a testování kódu
 Chcete-li otestovat tento kód, vytvořte řešení CompletionTest a spusťte jej v experimentální instanci.

#### <a name="to-build-and-test-the-completiontest-solution"></a>Sestavení a testování řešení CompletionTest

1. Sestavte řešení.

2. Při spuštění tohoto projektu v ladicím programu je spuštěna druhá instance sady Visual Studio.

3. Vytvořte textový soubor a zadejte text, který obsahuje slovo "přidat".

4. Při psaní první "a" a pak "d", seznam, který obsahuje "sčítání" a "adaptace" by se měl zobrazit. Všimněte si, že je vybráno přidání. Když zadáte jiné "d", seznam by měl obsahovat pouze "sčítání", který je nyní vybrán. Přidání můžete potvrdit stisknutím **mezerníku**, **tabulátoru**nebo **klávesy Enter** nebo zavřením seznamu zadáním esc nebo jiné klávesy.

## <a name="see-also"></a>Viz také
- [Návod: Propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
