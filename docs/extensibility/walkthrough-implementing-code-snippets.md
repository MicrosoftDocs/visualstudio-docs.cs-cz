---
title: 'Návod: Implementace fragmentů kódu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bd4a22dc63f0304cc8afa98e35c5f7afd6cac011
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921981"
---
# <a name="walkthrough-implement-code-snippets"></a>Návod: Implementace kódu
Můžete vytvořit fragmenty kódu a zahrnout je do editoru rozšíření tak, aby uživatelé rozšíření můžete přidat do vlastní kód.  
  
 Fragment kódu je fragment kódu nebo jiný text, který může být zahrnut do souboru. Chcete-li zobrazit všechny fragmenty kódu, které jsou zaregistrovány pro konkrétní programovací jazyky, na **nástroje** nabídky, klikněte na tlačítko **Správce fragmentů kódů**. Vložení fragmentu kódu v souboru, kde chcete fragment, klikněte pravým tlačítkem klikněte na tlačítko Vložit fragment kódu nebo **obklopit fragmentem**, vyhledejte chcete, aby fragment kódu a poklepejte na něj. Stisknutím klávesy **kartu** nebo **Shift**+**kartu** relevantní části fragmentu kódu upravit a potom stiskněte klávesu **Enter** nebo **Esc** přijmout. Další informace najdete v tématu [fragmenty kódu](../ide/code-snippets.md).  
  
 Fragment kódu je obsažen v souboru XML, který má příponu názvu souboru .snippet *. Fragment kódu může obsahovat pole, která je zvýrazněná po vložení fragmentu kódu tak, aby uživatel můžete najít a změnit. Soubor výstřižku také obsahuje informace o **Správce fragmentů kódů** tak, aby ho zobrazit název fragmentu kódu v správnou kategorii. Informace o schématu fragmentu kódu najdete v tématu [referenční dokumentace schématu fragmentů kódu](../ide/code-snippets-schema-reference.md).  
  
 Tento návod se naučíte k provedení následujících úkolů:  
  
1. Vytvoření a registrace fragmenty kódu pro konkrétní jazyk.  
  
2. Přidat **Vložit fragment** příkazu do místní nabídky.  
  
3. Implementace fragment kódu rozšíření.  
  
   Tento názorný postup je založen na [návod: zobrazení dokončování příkazů](../extensibility/walkthrough-displaying-statement-completion.md).  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnutý jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-and-register-code-snippets"></a>Vytvoření a registrace fragmenty kódu  
 Fragmenty kódu jsou obvykle přidružená služba registrované jazyka. Ale nemáte k implementaci <xref:Microsoft.VisualStudio.Package.LanguageService> zaregistrovat fragmenty kódu. Místo toho stačí zadat identifikátor GUID v souboru fragmentu kódu indexu a pak použijte stejný identifikátor GUID v <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> , který přidáte do projektu.  
  
 Následující kroky ukazují, jak vytvářet fragmenty kódu a přidružit konkrétní identifikátor GUID.  
  
1. Vytvořte následující adresářovou strukturu:  
  
    **%InstallDir%\TestSnippets\Snippets\1033\\**  
  
    kde *InstallDir %* je instalační složky sady Visual Studio. (I když se tato cesta se obvykle používá k instalaci fragmenty kódu, můžete jakoukoli cestu.)  
  
2. Ve složce \1033\ vytvořit *.xml* soubor a pojmenujte ho **TestSnippets.xml**. (I když tento název se obvykle používá pro soubor indexu fragment kódu, můžete zadat libovolný název, jako má *.xml* příponu názvu souboru.) Přidejte následující text a odstraňovat zástupný identifikátor GUID a přidejte vlastní.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8" ?>  
   <SnippetCollection>  
       <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}">  
           <SnippetDir>  
               <OnOff>On</OnOff>  
               <Installed>true</Installed>  
               <Locale>1033</Locale>  
               <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath>  
               <LocalizedName>Snippets</LocalizedName>  
           </SnippetDir>  
       </Language>  
   </SnippetCollection>  
   ```  
  
3. Vytvořte soubor do složky fragmentů kódu, pojmenujte ho **testování**`.snippet`a poté přidejte následující text:  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8" ?>  
   <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
       <CodeSnippet Format="1.0.0">  
           <Header>  
               <Title>Test replacement fields</Title>  
               <Shortcut>test</Shortcut>  
               <Description>Code snippet for testing replacement fields</Description>  
               <Author>MSIT</Author>  
               <SnippetTypes>  
                   <SnippetType>Expansion</SnippetType>  
               </SnippetTypes>  
           </Header>  
           <Snippet>  
               <Declarations>  
                   <Literal>  
                     <ID>param1</ID>  
                       <ToolTip>First field</ToolTip>  
                       <Default>first</Default>  
                   </Literal>  
                   <Literal>  
                       <ID>param2</ID>  
                       <ToolTip>Second field</ToolTip>  
                       <Default>second</Default>  
                   </Literal>  
               </Declarations>  
               <References>  
                  <Reference>  
                      <Assembly>System.Windows.Forms.dll</Assembly>  
                  </Reference>  
               </References>  
               <Code Language="TestSnippets">  
                   <![CDATA[MessageBox.Show("$param1$");  
        MessageBox.Show("$param2$");]]>  
               </Code>    
           </Snippet>  
       </CodeSnippet>  
   </CodeSnippets>  
   ```  
  
   Následující kroky ukazují, jak zaregistrovat fragmenty kódu.  
  
### <a name="to-register-code-snippets-for-a-specific-guid"></a>K registraci fragmenty kódu pro konkrétní identifikátor GUID  
  
1.  Otevřít **CompletionTest** projektu. Informace o tom, jak vytvořit tento projekt, naleznete v tématu [návod: zobrazení dokončování příkazů](../extensibility/walkthrough-displaying-statement-completion.md).  
  
2.  V projektu přidejte odkazy na následující sestavení:  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   Microsoft.MSXML  
  
3.  V projektu, otevřete **source.extension.vsixmanifest** souboru.  
  
4.  Ujistěte se, že **prostředky** obsahuje kartu **VsPackage** obsah typu a, který **projektu** je nastavena na název projektu.  
  
5.  Vyberte projekt CompletionTest a v okně Vlastnosti nastavte **vygenerovat soubor Pkgdef** k **true**. Uložte projekt.  
  
6.  Přidání statického `SnippetUtilities` třídy do projektu.  
  
     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]  
  
7.  Ve třídě SnippetUtilities definovat identifikátor GUID a přiřaďte jí hodnotu, která jste použili v *SnippetsIndex.xml* souboru.  
  
     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]  
  
8.  Přidat <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> k `TestCompletionHandler` třídy. Tento atribut lze přidat k (nestatické) třídy v projektu žádné veřejné nebo interní. (Možná budete muset přidat `using` příkaz pro obor názvů Microsoft.VisualStudio.Shell.)  
  
     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]  
  
9. Sestavte a spusťte projekt. V experimentální instanci sady Visual Studio, který se spustí při spuštění projektu, má být zobrazen v tomto fragmentu kódu, který jste právě zaregistrovali **Správce fragmentů kódů** pod **TestSnippets** jazyka.  
  
## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Přidat příkaz Vložit fragment kódu do místní nabídky  
 **Vložit fragment** příkazu není k dispozici v místní nabídce pro textový soubor. Proto je nutné povolit příkaz.  
  
#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Chcete-li přidat příkaz Vložit fragment kódu do místní nabídky  
  
1.  Otevřít `TestCompletionCommandHandler` souboru třídy.  
  
     Vzhledem k tomu, že tato třída implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, můžete aktivovat **Vložit fragment** v příkaz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metoda. Před povolením příkazu, zkontrolujte, že tato metoda není volána uvnitř funkce služby automation vzhledem k tomu, když **Vložit fragment** dojde ke kliknutí na příkaz, zobrazí se fragment kódu pro výběr uživatelského rozhraní (UI).  
  
     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]  
  
2.  Sestavte a spusťte projekt. V experimentální instanci aplikace, otevřete soubor, který má *s příponou ZZZ* příponu názvu souboru a pak klikněte pravým tlačítkem kamkoli do něj. **Vložit fragment** příkaz se zobrazí v místní nabídce.  
  
## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Implementace rozšíření fragmentu kódu v uživatelském rozhraní pro výběr fragmentu kódu  
 Tato část ukazuje, jak implementovat rozšíření fragment kódu tak, aby nástroje uživatelského rozhraní pro výběr fragmentu kódu zobrazuje, kdy **Vložit fragment** dojde ke kliknutí na v místní nabídce. Fragment kódu je také rozbalená, když uživatel zadá místní fragment kódu a stiskne klávesu **kartu**.  
  
 Chcete-li zobrazit nástroje pro výběr fragmentu kódu uživatelského rozhraní a povolení navigace a přijetí po vložení fragmentu kódu, použijte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody. Vlastní vložení zařizuje služba <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> metody.  
  
 Implementace rozšíření fragment kódu používá starší verze <xref:Microsoft.VisualStudio.TextManager.Interop> rozhraní. Při přeložit z aktuální editor třídy staršímu kódu, mějte na paměti, že starší verze rozhraní použijte kombinaci čísla řádku a sloupce pro určení umístění ve vyrovnávací paměti textu, ale aktuální třídy používají jeden index. Proto pokud vyrovnávací paměť obsahuje tři řádky, z nichž každá má 10 znaků (znaku nového řádku, které se počítá jako jeden znak), čtvrtý znak na třetí řádek je na pozici 27 v aktuální implementaci, ale je na řádku 2, umístěte staré implementace 3.  
  
#### <a name="to-implement-snippet-expansion"></a>K implementaci fragment kódu rozšíření  
  
1.  Soubor, který obsahuje `TestCompletionCommandHandler` třídy, přidejte následující `using` příkazy.  
  
     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]  
  
2.  Ujistěte se, `TestCompletionCommandHandler` implementaci třídy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> rozhraní.  
  
     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]  
  
3.  V `TestCompletionCommandHandlerProvider` třídy, import <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.  
  
     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]  
  
4.  Přidat některé soukromé pole pro rozšíření rozhraní kódu a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]  
  
5.  V konstruktoru `TestCompletionCommandHandler` třídy, nastavte následující pole.  
  
     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]  
  
6.  K zobrazení nástroje pro výběr fragmentu kódu, když uživatel klikne **Vložit fragment** příkazu, přidejte následující kód, který <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody. (Lépe čitelný, aby toto vysvětlení `Exec()`kód, který se používá pro doplňování se nezobrazí; místo toho jsou bloky kódu přidat do existující metodu.) Následující blok kódu přidejte za kód, který vyhledává znak.  
  
     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]  
  
7.  Pokud fragment kódu obsahuje pole, která lze procházet, dokud rozbalení je explicitní přijat, hodnota zůstane otevřené relace rozšíření Pokud fragmentu kódu neobsahuje žádná pole, relace se zavře a je vrácena jako `null` podle <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> metody. V <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody za Sběrač fragmentů kódu uživatelského rozhraní, který jste přidali v předchozím kroku, přidejte následující kód pro zpracování navigace na fragment kódu (když uživatel stiskne **kartu** nebo **Shift** + **Kartu** po vložení fragmentu).  
  
     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]  
  
8.  Vložit fragment kódu, když uživatel zadá odpovídající místní a stiskne klávesu **kartu**, přidejte kód, který <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metoda. Privátní metody, která vloží fragment kódu se zobrazí v pozdějším kroku. Přidejte následující kód za kód pro navigaci, který jste přidali v předchozím kroku.  
  
     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]  
  
9. Implementace metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> rozhraní. V této implementaci jsou pouze metody, které vás zajímají <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Jiné metody by měla vrátit pouze <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]  
  
10. Implementace <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> metody. Pomocná metoda, která ve skutečnosti vloží rozšíření se věnujeme v pozdějším kroku. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Obsahuje řádek a sloupec informace, které můžete získat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]  
  
11. Následující privátní metodu vloží fragment kódu, založené na zástupce nebo na název a cestu. Poté zavolá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> metoda fragmentem kódu.  
  
     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]  
  
## <a name="build-and-test-code-snippet-expansion"></a>Vytváření a testování rozšíření fragmentů kódu  
 Můžete zkontrolovat, zda fragment kódu rozšíření funguje ve vašem projektu.  
  
1.  Sestavte řešení. Při spuštění tohoto projektu v ladicím programu se spustí druhé instanci aplikace Visual Studio.  
  
2.  Otevřete textový soubor a zadejte nějaký text.  
  
3.  Klikněte pravým tlačítkem někde v textu a pak klikněte na **Vložit fragment**.  
  
4.  Sběrač fragmentů by se měla zobrazit uživatelské rozhraní se automaticky otevírané okno s upozorněním **testování nahrazení pole**. Dvakrát klikněte na místní nabídce.  
  
     Následující fragment kódu by měl být vložen.  
  
    ```  
    MessageBox.Show("first");  
    MessageBox.Show("second");  
    ```  
  
     Není stiskněte **Enter** nebo **Esc**.  
  
5.  Stisknutím klávesy **kartu** a **Shift**+**kartu** k přepínání mezi "first" a "druhého".  
  
6.  Stisknutím klávesy buď přijměte vložení **Enter** nebo **Esc**.  
  
7.  V jiné části textu, zadejte "test" a stiskněte klávesu **kartu**. Protože "test" místní fragment kódu je fragment kódu musí být znovu zařazen.  
  
## <a name="next-steps"></a>Další kroky