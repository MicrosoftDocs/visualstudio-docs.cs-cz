---
title: 'Návod: implementace fragmentů kódu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb720589bc9bc31b7cf2a04b05559cb9c9d46961
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201986"
---
# <a name="walkthrough-implementing-code-snippets"></a>Návod: Implementace fragmentů kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete vytvořit fragmenty kódu a zahrnout je do rozšíření editoru, aby je uživatelé rozšíření mohli přidat ke svému vlastnímu kódu.  
  
 Fragment kódu je fragment kódu nebo jiného textu, který lze začlenit do souboru. Chcete-li zobrazit všechny fragmenty, které byly zaregistrovány pro konkrétní programovací jazyky, v nabídce **nástroje** klikněte na **Správce fragmentů kódu**. Chcete-li vložit fragment do souboru, klikněte pravým tlačítkem na místo, kde chcete fragment kódu, klikněte na možnost **Vložit fragment** nebo **obklopit**, Najděte požadovaný fragment a pak na něj dvakrát klikněte. Chcete-li upravit relevantní části fragmentu, stiskněte klávesu TAB nebo SHIFT + TAB a potom stiskněte klávesu ENTER nebo ESC pro přijetí změn. Další informace naleznete v tématu [fragmenty kódu](../ide/code-snippets.md).  
  
 Fragment kódu je obsažen v souboru XML, který má příponu názvu souboru. fragment. Fragment může obsahovat pole, která jsou zvýrazněna po vložení fragmentu, aby ho uživatel mohl najít a změnit. Soubor fragmentů také poskytuje informace pro **Správce fragmentů kódu** , aby mohl zobrazit název fragmentu ve správné kategorii. Informace o schématu fragmentu kódu naleznete v [referenčních informacích o schématu fragmentů kódu](../ide/code-snippets-schema-reference.md).  
  
 Tento návod učí, jak provádět tyto úlohy:  
  
1. Vytvořte a zaregistrujte fragmenty kódu pro konkrétní jazyk.  
  
2. Přidejte příkaz **Vložit fragment** do místní nabídky.  
  
3. Implementujte rozšíření fragmentů.  
  
   Tento návod vychází z [návodu: zobrazení dokončování příkazů](../extensibility/walkthrough-displaying-statement-completion.md).  
  
## <a name="prerequisites"></a>Předpoklady  
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-and-registering-code-snippets"></a>Vytváření a registrace fragmentů kódu  
 Fragmenty kódu jsou obvykle spojeny s registrovanou jazykovou službou. Nicméně není nutné implementovat k <xref:Microsoft.VisualStudio.Package.LanguageService> registraci fragmentů kódu. Místo toho zadejte identifikátor GUID v souboru indexu fragmentu a pak použijte stejný identifikátor GUID v rozhraní <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> , které jste přidali do projektu.  
  
 Následující kroky ukazují, jak vytvořit fragmenty kódu a přidružit je k určitému identifikátoru GUID.  
  
1. Vytvořte následující adresářovou strukturu:  
  
    **%InstallDir%\TestSnippets\Snippets\1033\\**  
  
    kde *% INSTALLDIR%* je instalační složka sady Visual Studio. (I když se tato cesta obvykle používá k instalaci fragmentů kódu, můžete zadat libovolnou cestu.)  
  
2. Ve složce \ 1033 \ vytvořte soubor. XML a pojmenujte jej **TestSnippets.xml**. (I když se tento název obvykle používá pro soubor indexu fragmentů, můžete zadat libovolný název, pokud má příponu názvu souboru. XML.) Přidejte následující text a pak odstraňte zástupný identifikátor GUID a přidejte vlastní.  
  
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
  
3. Ve složce fragmentů kódu vytvořte soubor a pojmenujte ho **test** `.snippet` a pak přidejte následující text:  
  
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
  
   Následující kroky ukazují, jak registrovat fragmenty kódu.  
  
#### <a name="to-register-code-snippets-for-a-specific-guid"></a>Registrace fragmentů kódu pro určitý identifikátor GUID  
  
1. Otevřete projekt **CompletionTest** . Informace o tom, jak vytvořit tento projekt, naleznete v tématu [Návod: zobrazení dokončování příkazů](../extensibility/walkthrough-displaying-statement-completion.md).  
  
2. V projektu přidejte odkazy na následující sestavení:  
  
    - Microsoft. VisualStudio. TextManager. Interop  
  
    - Microsoft. VisualStudio. TextManager. Interop. 8.0  
  
    - Microsoft. MSXML  
  
3. V projektu otevřete soubor source. extension. vsixmanifest.  
  
4. Ujistěte se, že karta **assets** obsahuje typ obsahu **VSPackage** a že **projekt** je nastaven na název projektu.  
  
5. Vyberte projekt CompletionTest a ve okno Vlastnosti sadě **Generovat soubor pkgdef** na **hodnotu true**. Uložte projekt.  
  
6. Přidejte `SnippetUtilities` do projektu statickou třídu.  
  
     [!code-csharp[VSSDKCompletionTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#22)]
     [!code-vb[VSSDKCompletionTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#22)]  
  
7. Ve třídě SnippetUtilities definujte identifikátor GUID a poskytněte mu hodnotu, kterou jste použili v souboru SnippetsIndex.xml.  
  
     [!code-csharp[VSSDKCompletionTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#23)]
     [!code-vb[VSSDKCompletionTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#23)]  
  
8. Přidejte <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> do `TestCompletionHandler` třídy. Tento atribut lze přidat do libovolné veřejné nebo interní (nestatické) třídy v projektu. (Je možné, že budete muset přidat `using` příkaz pro obor názvů Microsoft. VisualStudio. Shell.)  
  
     [!code-csharp[VSSDKCompletionTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#24)]
     [!code-vb[VSSDKCompletionTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#24)]  
  
9. Sestavte a spusťte projekt. V experimentální instanci aplikace Visual Studio, která se spustí při spuštění projektu, by měl fragment, který jste právě zaregistrovali, zobrazit ve **Správci fragmentů kódu** v jazyce **TestSnippets** .  
  
## <a name="adding-the-insert-snippet-command-to-the-shortcut-menu"></a>Přidání příkazu Vložit fragment do místní nabídky  
 Příkaz **Vložit fragment** není součástí místní nabídky pro textový soubor. Proto je nutné příkaz Povolit.  
  
#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Přidání příkazu Vložit fragment do místní nabídky  
  
1. Otevřete `TestCompletionCommandHandler` soubor třídy.  
  
     Vzhledem k tomu, že tato třída implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , můžete aktivovat příkaz **Vložit fragment kódu** v <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodě. Před povolením příkazu ověřte, že tato metoda není volána uvnitř funkce automatizace, protože při kliknutí na příkaz **Vložit fragment kódu** se zobrazí uživatelské rozhraní pro výběr fragmentu (UI).  
  
     [!code-csharp[VSSDKCompletionTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#25)]
     [!code-vb[VSSDKCompletionTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#25)]  
  
2. Sestavte a spusťte projekt. V experimentální instanci otevřete soubor s příponou názvu souboru. zzz a potom klikněte pravým tlačítkem myši kdekoli v něm. Příkaz **INSERT fragment** by měl být zobrazen v místní nabídce.  
  
## <a name="implementing-snippet-expansion-in-the-snippet-picker-ui"></a>Implementace rozšíření fragmentů kódu v uživatelském rozhraní výběru fragmentu  
 V této části se dozvíte, jak implementovat rozšíření fragmentů kódu, aby se zobrazilo uživatelské rozhraní pro výběr fragmentu, když se v místní nabídce klikne na **Vložit fragment** kódu. Fragment kódu je také rozbalen, pokud uživatel zadá zástupce fragmentu kódu a pak stiskne kartu.  
  
 Chcete-li zobrazit uživatelské rozhraní pro výběr fragmentu a povolit přecházení navigace a následné vložení, použijte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodu. Samotné vložení je zpracováváno <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> metodou.  
  
 Implementace rozšíření fragmentu kódu používá starší <xref:Microsoft.VisualStudio.TextManager.Interop> rozhraní. Při převodu z aktuálních tříd editoru na starší verzi kódu si pamatujte, že starší rozhraní používají kombinaci čísel řádků a čísel sloupců k určení umístění v textové vyrovnávací paměti, ale aktuální třídy používají jeden index. Proto pokud má vyrovnávací paměť tři řádky, z nichž každý má deset znaků (plus nový řádek, který se počítá jako 1 znak), čtvrtý znak na třetím řádku je na pozici 27 v aktuální implementaci, ale je na řádku 2, pozice 3 ve staré implementaci.  
  
#### <a name="to-implement-snippet-expansion"></a>Implementace rozšíření fragmentů kódu  
  
1. Do souboru, který obsahuje `TestCompletionCommandHandler` třídu, přidejte následující `using` příkazy.  
  
     [!code-csharp[VSSDKCompletionTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#26)]
     [!code-vb[VSSDKCompletionTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#26)]  
  
2. Nastavte `TestCompletionCommandHandler` třídu na implementaci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> rozhraní.  
  
     [!code-csharp[VSSDKCompletionTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#27)]
     [!code-vb[VSSDKCompletionTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#27)]  
  
3. Ve `TestCompletionCommandHandlerProvider` třídě importujte <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> .  
  
     [!code-csharp[VSSDKCompletionTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#28)]
     [!code-vb[VSSDKCompletionTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#28)]  
  
4. Přidejte některá soukromá pole pro rozhraní rozšíření kódu a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  
  
     [!code-csharp[VSSDKCompletionTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#29)]
     [!code-vb[VSSDKCompletionTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#29)]  
  
5. V konstruktoru `TestCompletionCommandHandler` třídy nastavte následující pole.  
  
     [!code-csharp[VSSDKCompletionTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#30)]
     [!code-vb[VSSDKCompletionTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#30)]  
  
6. Chcete-li zobrazit výběr fragmentu, když uživatel klikne na příkaz **Vložit fragment** , přidejte následující kód do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody. (Aby bylo toto vysvětlení čitelnější, kód exec (), který se používá pro dokončování příkazů, není zobrazen. místo toho jsou bloky kódu přidány do existující metody.) Po kódu, který kontroluje znak, přidejte následující blok kódu.  
  
     [!code-csharp[VSSDKCompletionTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#31)]
     [!code-vb[VSSDKCompletionTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#31)]  
  
7. Pokud má fragment kódu pole, která lze procházet, zůstane relace rozšíření otevřená, dokud není rozšíření explicitně přijato; Pokud fragment kódu neobsahuje žádná pole, relace je zavřena a je vrácena jako `null` <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> metoda. V <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodě po kódu uživatelského rozhraní výběru fragmentu, který jste přidali v předchozím kroku, přidejte následující kód pro zpracování navigace fragmentem (když uživatel stiskne klávesu TAB nebo SHIFT + TAB po vložení fragmentu kódu).  
  
     [!code-csharp[VSSDKCompletionTest#32](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#32)]
     [!code-vb[VSSDKCompletionTest#32](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#32)]  
  
8. Chcete-li vložit fragment kódu, když uživatel zadá odpovídající zástupce a pak stiskne kartu, přidejte kód do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody. Soukromá metoda, která vloží fragment kódu, bude zobrazena v pozdějším kroku. Po navigačním kódu, který jste přidali v předchozím kroku, přidejte následující kód.  
  
     [!code-csharp[VSSDKCompletionTest#33](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#33)]
     [!code-vb[VSSDKCompletionTest#33](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#33)]  
  
9. Implementujte metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> rozhraní. V této implementaci jsou jedinými metodami, které vás zajímají, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> . Ostatní metody by měly vracet pouze <xref:Microsoft.VisualStudio.VSConstants.S_OK> .  
  
     [!code-csharp[VSSDKCompletionTest#34](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#34)]
     [!code-vb[VSSDKCompletionTest#34](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#34)]  
  
10. Implementujte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> metodu. Pomocná metoda, která ve skutečnosti vkládá rozšíření, bude zahrnuta v pozdějším kroku. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>Poskytuje informace o řádku a sloupci, které můžete získat z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  
  
     [!code-csharp[VSSDKCompletionTest#35](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#35)]
     [!code-vb[VSSDKCompletionTest#35](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#35)]  
  
11. Následující soukromá metoda vloží fragment kódu na základě zástupce nebo názvu a cesty. Poté volá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> metodu s fragmentem.  
  
     [!code-csharp[VSSDKCompletionTest#36](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#36)]
     [!code-vb[VSSDKCompletionTest#36](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#36)]  
  
## <a name="building-and-testing-code-snippet-expansion"></a>Sestavování a testování rozšíření fragmentů kódu  
 Můžete testovat, zda rozšíření fragmentů funguje ve vašem projektu.  
  
1. Sestavte řešení. Při spuštění tohoto projektu v ladicím programu je vytvořena instance druhé instance aplikace Visual Studio.  
  
2. Otevřete textový soubor a zadejte nějaký text.  
  
3. Klikněte pravým tlačítkem někam do textu a pak klikněte na **Vložit fragment**.  
  
4. Uživatelské rozhraní pro výběr fragmentu by se mělo zobrazit s automaticky otevírané okno, které uvádí **test náhradních polí**. Dvakrát klikněte na automaticky otevírané okno.  
  
     Následující fragment kódu by měl být vložen.  
  
    ```  
    MessageBox.Show("first");  
    MessageBox.Show("second");  
    ```  
  
     Nestiskněte klávesu ENTER nebo ESC.  
  
5. Klávesy TAB a SHIFT + TAB můžete přepínat mezi "First" a "Second".  
  
6. Přijměte vložení stisknutím klávesy ENTER nebo ESC.  
  
7. V jiné části textu zadejte "test" a stiskněte klávesu TAB. Vzhledem k tomu, že "test" je zástupce fragmentu kódu, fragment by měl být vložen znovu.  
  
## <a name="next-steps"></a>Další kroky
