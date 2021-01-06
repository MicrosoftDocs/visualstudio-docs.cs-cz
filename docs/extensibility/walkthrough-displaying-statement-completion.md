---
title: 'Návod: zobrazení dokončování příkazů | Microsoft Docs'
description: V tomto návodu se naučíte implementovat dokončování příkazů založeného na jazyce pro obsah v prostém textu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: d05d33074f48e59e365792fda63897b1d38cd585
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877153"
---
# <a name="walkthrough-display-statement-completion"></a>Návod: dokončování příkazů zobrazení
Doplňování příkazů založeného na jazyce můžete implementovat definováním identifikátorů, pro které chcete poskytnout dokončení, a následnou aktivací relace dokončení. Můžete definovat dokončování příkazů v kontextu jazykové služby, definovat vlastní příponu názvu souboru a typ obsahu a pak zobrazit dokončování pouze pro tento typ. Nebo můžete aktivovat dokončování pro existující typ obsahu, například "prostý text". Tento návod ukazuje, jak aktivovat dokončování příkazů pro typ obsahu "prostý text", což je typ obsahu textových souborů. Typ obsahu "text" je nadřazeným prvkem všech dalších typů obsahu, včetně kódu a souborů XML.

 Dokončení příkazu se obvykle aktivuje zadáním určitých znaků, například zadáním začátku identifikátoru, jako je "using". Obvykle se neodesílá, když stisknete klávesu **MEZERNÍK**, **TAB** nebo **ENTER** , potvrďte výběr. Můžete implementovat funkce technologie IntelliSense, které se aktivují při zadávání znaku pomocí obslužné rutiny příkazu pro stisknutí kláves ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní) a zprostředkovatele obslužné rutiny, který implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> rozhraní. Chcete-li vytvořit zdroj dokončení, což je seznam identifikátorů, které se účastní dokončení, implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> rozhraní a poskytovatele zdroje dokončení ( <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> rozhraní). Poskytovatelé jsou součásti komponenty Managed Extensibility Framework (MEF). Zodpovídá za exportování tříd source a Controller a importu služeb a zprostředkovatelů – například <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , který umožňuje navigaci ve vyrovnávací paměti textu a na <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> , který spouští relaci dokončení.

 Tento návod ukazuje, jak implementovat dokončování příkazů pro pevně zakódovanou sadu identifikátorů. V úplných implementacích zodpovídá služba jazyka a jazykovou dokumentaci za poskytnutí tohoto obsahu.

## <a name="prerequisites"></a>Předpoklady
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Vytvořit projekt MEF

#### <a name="to-create-a-mef-project"></a>Vytvoření projektu MEF

1. Vytvoří projekt VSIX v jazyce C#. (V dialogovém okně **Nový projekt** vyberte **Visual C#/rozšiřitelnost** a potom **projekt VSIX**.) Pojmenujte řešení `CompletionTest` .

2. Přidejte do projektu šablonu položky klasifikátoru editoru. Další informace naleznete v tématu [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Odstraňte existující soubory třídy.

4. Do projektu přidejte následující odkazy a ujistěte se, že je **CopyLocal** nastavené na `false` :

     Microsoft. VisualStudio. Editor

     Microsoft. VisualStudio. Language. IntelliSense

     Microsoft. VisualStudio. OLE. Interop

     Microsoft. VisualStudio. Shell. 15.0

     Microsoft. VisualStudio. Shell. unmutable. 10.0

     Microsoft. VisualStudio. TextManager. Interop

## <a name="implement-the-completion-source"></a>Implementace zdroje dokončení
 Zdroj dokončení zodpovídá za shromáždění sady identifikátorů a přidání obsahu do okna dokončení, když uživatel zadá aktivační událost dokončení, například první písmena identifikátoru. V tomto příkladu jsou identifikátory a jejich popisy pevně kódované v <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metodě. Ve většině reálných použití byste pomocí analyzátoru jazyka získali tokeny k naplnění seznamu dokončení.

### <a name="to-implement-the-completion-source"></a>Implementace zdroje dokončení

1. Přidejte soubor třídy a pojmenujte ho `TestCompletionSource` .

2. Přidejte tyto importy:

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. Upravte deklaraci třídy pro `TestCompletionSource` tak, aby implementovala <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> :

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. Přidejte soukromá pole pro poskytovatele zdroje, textovou vyrovnávací paměť a seznam <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> objektů (které odpovídají identifikátorům, které se budou podílet na relaci dokončení):

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. Přidejte konstruktor, který nastaví zprostředkovatele zdroje a vyrovnávací paměť. `TestCompletionSourceProvider`Třída je definována v pozdějších krocích:

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metodu přidáním sady dokončení, která obsahuje dokončování, které chcete zadat v kontextu. Každá sada dokončení obsahuje sadu <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> dokončovacích operací a odpovídá kartě okna dokončení. (V Visual Basic projekty karty okna pro dokončení se nazývají **Common** a **All**.) `FindTokenSpanAtPosition` Metoda je definována v dalším kroku.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. Následující metoda slouží k vyhledání aktuálního slova z pozice kurzoru:

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. Implementujte `Dispose()` metodu:

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>Implementace poskytovatele zdroje dokončení
 Poskytovatel zdroje dokončení je část komponenty MEF, která vytvoří instanci zdroje dokončení.

### <a name="to-implement-the-completion-source-provider"></a>Implementace poskytovatele zdroje dokončení

1. Přidejte třídu s názvem `TestCompletionSourceProvider` , která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> . Exportujte tuto třídu s použitím <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "prostého textu" a typu <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "dokončení testu".

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. Importujte <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , který najde aktuální slovo ve zdroji dokončení.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. Implementací <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> metody vytvořte instanci zdroje dokončení.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>Implementace zprostředkovatele obslužné rutiny příkazu pro dokončení
 Zprostředkovatel obslužné rutiny příkazu pro dokončení je odvozen z typu <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> , který naslouchá události vytváření zobrazení textu a převádí zobrazení z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> , což umožňuje přidání příkazu do řetězce příkazu prostředí sady Visual Studio – do <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . Vzhledem k tomu, že tato třída je exportem MEF, můžete ji také použít k importu služeb, které jsou vyžadovány samotným obslužnou rutinou příkazu.

#### <a name="to-implement-the-completion-command-handler-provider"></a>Implementace zprostředkovatele obslužných rutin příkazu pro dokončení

1. Přidejte soubor s názvem `TestCompletionCommandHandler` .

2. Přidejte tyto direktivy direktivy using:

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. Přidejte třídu s názvem `TestCompletionHandlerProvider` , která implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . Exportujte tuto třídu s <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "obslužným rutinou dokončení tokenu", <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "prostého textu" a <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> a <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable> .

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. Importujte <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , který umožňuje převod z typu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> na <xref:Microsoft.VisualStudio.Text.Editor.ITextView> , a, a, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> který umožňuje přístup ke standardním službám sady Visual Studio.

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. Implementujte <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metodu pro vytvoření instance obslužné rutiny příkazu.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>Implementace obslužné rutiny příkazu pro dokončení
 Vzhledem k tomu, že dokončování příkazů se spouští pomocí klávesových úhozů, je nutné implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní pro příjem a zpracování klávesových úhozů, které aktivují, potvrzují a odstavují relaci dokončení.

#### <a name="to-implement-the-completion-command-handler"></a>Implementace obslužné rutiny příkazu pro dokončení

1. Přidejte třídu s názvem `TestCompletionCommandHandler` , která implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. Přidejte soukromá pole pro následující obslužnou rutinu příkazu (do kterého předáte příkaz), textové zobrazení, zprostředkovatele obslužné rutiny příkazů (umožňující přístup k různým službám) a relaci dokončení:

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. Přidejte konstruktor, který nastaví textové zobrazení a pole poskytovatele a přidá příkaz do řetězce příkazu:

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. Implementujte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu předáním příkazu společně:

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. Implementujte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodu. Pokud tato metoda obdrží klávesovou zkratku, musí provést jednu z následujících akcí:

   - Umožňuje zapsat znak do vyrovnávací paměti a pak aktivovat nebo filtrovat dokončení. (Tisk znaků.)

   - Potvrďte dokončení, ale nepovolujte, aby byl znak zapsaný do vyrovnávací paměti. (Prázdný znak, **tabulátor** a **Zadejte** , když se zobrazí relace dokončování.)

   - Povolí předání příkazu k další obslužné rutině. (Všechny ostatní příkazy.)

     Vzhledem k tomu, že tato metoda může zobrazit uživatelské rozhraní, zavolejte <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> a ujistěte se, že není volána v kontextu automatizace:

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. Tento kód je soukromá metoda, která spustí relaci dokončení:

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. Dalším příkladem je soukromá metoda, která odhlašuje odběr <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> události:

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>Sestavení a testování kódu
 Chcete-li otestovat tento kód, sestavte řešení CompletionTest a spusťte ho v experimentální instanci.

#### <a name="to-build-and-test-the-completiontest-solution"></a>Sestavení a testování řešení CompletionTest

1. Sestavte řešení.

2. Při spuštění tohoto projektu v ladicím programu se spustí druhá instance sady Visual Studio.

3. Vytvořte textový soubor a zadejte nějaký text, který obsahuje slovo "Přidat".

4. Když zadáte první "a" a potom "d", zobrazí se seznam obsahující "sčítání" a "přizpůsobení". Všimněte si, že je vybraná možnost přidání. Když zadáte jiný text "d", seznam by měl obsahovat pouze "sčítání", které jsou nyní vybrány. Kliknutím na klávesu **MEZERNÍK**, **TAB** nebo **ENTER** můžete potvrdit "sčítání", nebo můžete seznam zavřít zadáním klávesy ESC nebo jiného klíče.

## <a name="see-also"></a>Viz také
- [Návod: propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
