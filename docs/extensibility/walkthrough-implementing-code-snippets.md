---
title: 'Návod: Implementace fragmentů kódu | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: ba1b6e0852c1ec1b306938b791eed78e79d211ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697101"
---
# <a name="walkthrough-implement-code-snippets"></a>Návod: Implementace fragmentů kódu
Můžete vytvořit fragmenty kódu a zahrnout je do rozšíření editoru, aby je uživatelé rozšíření mohli přidat do vlastního kódu.

 Fragment kódu je fragment kódu nebo jiného textu, který lze začlenit do souboru. Chcete-li zobrazit všechny úryvky, které byly zaregistrovány pro určité programovací jazyky, klepněte v nabídce **Nástroje** na **položku Správce výstřižků kódu**. Pokud chcete vložit úryvek do souboru, klikněte pravým tlačítkem myši na místo, kam chcete úryvek vložit, klikněte na Vložit úryvek nebo **Obklopit**do , vyhledejte požadovaný úryvek a poklikejte na něj. Stisknutím **klávesy Tab** nebo **Shift**+**Shift** upravte příslušné části úryvku a pak ho přijměte stisknutím **klávesenter** nebo **Esc.** Další informace naleznete v [tématu Fragmenty kódu](../ide/code-snippets.md).

 Fragment kódu je obsažen v souboru XML, který má příponu .snippet* název souboru. Úryvek může obsahovat pole, která jsou zvýrazněna po vložení fragmentu, aby je uživatel mohl najít a změnit. Výstřižek soubor také poskytuje informace pro **správce fragmentu kódu** tak, aby jej můžete zobrazit název výstřižku ve správné kategorii. Informace o schématu úryvku naleznete v [tématu Code snippets odkaz na schéma](../ide/code-snippets-schema-reference.md).

 Tento návod učí, jak provádět tyto úkoly:

1. Vytvořte a zaregistrujte fragmenty kódu pro určitý jazyk.

2. Přidejte příkaz **Vložit úryvek** do místní nabídky.

3. Implementujte rozšíření fragmentu.

   Tento návod je založen na [návodu: Zobrazení dokončení příkazu](../extensibility/walkthrough-displaying-statement-completion.md).

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015, nenainstalujete Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-and-register-code-snippets"></a>Vytvoření a registrace fragmentů kódu
 Fragmenty kódu jsou obvykle přidruženy k registrované jazykové službě. Však není třeba implementovat <xref:Microsoft.VisualStudio.Package.LanguageService> k registraci fragmenty kódu. Místo toho stačí zadat identifikátor GUID v souboru indexu úryvku <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> a potom použít stejný identifikátor GUID v aplikaci, kterou přidáte do projektu.

 Následující kroky ukazují, jak vytvořit fragmenty kódu a přidružit je k určitému identifikátoru GUID.

1. Vytvořte následující adresářovou strukturu:

    **%InstallDir%\TestSnippets\Úryvky\1033\\**

    kde *%InstallDir%* je instalační složka sady Visual Studio. (I když se tato cesta obvykle používá k instalaci fragmentů kódu, můžete zadat libovolnou cestu.)

2. Ve složce \1033\ vytvořte soubor *XML* a pojmenujte jej **TestSnippets.xml**. (I když se tento název obvykle používá pro soubor indexu výstřižku, můžete zadat libovolný název, pokud má příponu *XML.)* Přidejte následující text a odstraňte zástupný identifikátor GUID a přidejte vlastní.

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

3. Vytvořte soubor ve složce složek úryvku, pojmenujte jej **a**`.snippet`přidejte následující text:

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

### <a name="to-register-code-snippets-for-a-specific-guid"></a>Registrace fragmentů kódu pro konkrétní identifikátor GUID

1. Otevřete projekt **CompletionTest.** Informace o tom, jak vytvořit tento projekt, naleznete [v tématu Návod: Zobrazení dokončení příkazu](../extensibility/walkthrough-displaying-statement-completion.md).

2. V projektu přidejte odkazy na následující sestavení:

    - Microsoft.VisualStudio.TextManager.Interop

    - Microsoft.VisualStudio.TextManager.Interop.8.0

    - soubor Microsoft.msxml

3. V projektu otevřete soubor **source.extension.vsixmanifest.**

4. Ujistěte se, že **karta Prostředky** obsahuje typ obsahu **VsPackage** a že **aplikace Project** je nastavena na název projektu.

5. Vyberte projekt CompletionTest a v sadě vlastností **vyberte hodnotu Generate Pkgdef File** to **true**. Uložte projekt.

6. Přidejte `SnippetUtilities` statickou třídu do projektu.

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7. Ve třídě SnippetUtilities definujte identifikátor GUID a přiřazujte mu hodnotu, kterou jste použili v souboru *SnippetsIndex.xml.*

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8. Přidejte <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> do `TestCompletionHandler` třídy. Tento atribut lze přidat do libovolné veřejné nebo interní (nestatické) třídy v projektu. (Bude pravděpodobně muset `using` přidat direktivu pro obor názvů Microsoft.VisualStudio.Shell.)

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. Sestavení a spuštění projektu. V experimentální instanci sady Visual Studio, která začíná při spuštění projektu, by měl být fragment, který jste právě zaregistrovali, zobrazen ve **Správci fragmentů kódu** v **jazyce TestSnippets.**

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Přidání příkazu Vložit úryvek do místní nabídky
 Příkaz **Vložit úryvek** není v místní nabídce textového souboru zahrnut. Proto je nutné povolit příkaz.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Přidání příkazu Vložit úryvek do místní nabídky

1. Otevřete `TestCompletionCommandHandler` soubor třídy.

     Vzhledem k <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>tomu, že tato třída implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> , můžete aktivovat příkaz **Vložit úryvek** v metodě. Před povolením příkazu zkontrolujte, zda tato metoda není volána uvnitř funkce automatizace, protože po klepnutí na příkaz **Vložit úryvek** se zobrazí uživatelské rozhraní pro výběr fragmentu (UI).

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2. Sestavení a spuštění projektu. V experimentální instanci otevřete soubor s příponou *.zzz* a klikněte pravým tlačítkem myši na libovolné místo v něm. Příkaz **Vložit úryvek** by se měl objevit v místní nabídce.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Implementace rozšíření fragmentu v uzdu výběru výstřižků
 Tato část ukazuje, jak implementovat rozšíření fragmentu kódu tak, aby se při kliknutí na fragment vložit v místní nabídce zobrazilo ujatého ovládacího **panelu výstřižků.** Fragment kódu je také rozbalen, když uživatel zadá zástupce fragmentu kódu a stiskne **klávesu Tab**.

 Chcete-li zobrazit uživatelské uživatelské tlačítko pro výběr výstřižků a povolit přijetí <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> fragmentu navigace a po vložení, použijte metodu. Vložení samotné je zpracována <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> metodou.

 Implementace rozšíření fragmentu kódu používá <xref:Microsoft.VisualStudio.TextManager.Interop> starší rozhraní. Při překladu z aktuální třídy editoru do staršího kódu, nezapomeňte, že starší rozhraní použít kombinaci čísla řádků a čísla sloupců k určení umístění v textové vyrovnávací paměti, ale aktuální třídy používají jeden index. Proto pokud vyrovnávací paměť má tři řádky, z nichž každý má 10 znaků (plus nový řádek, který se počítá jako jeden znak), čtvrtý znak na třetím řádku je na pozici 27 v aktuální implementaci, ale je na řádku 2, pozice 3 ve staré implementaci.

#### <a name="to-implement-snippet-expansion"></a>Implementace rozšíření úryvku

1. Do souboru, `TestCompletionCommandHandler` který obsahuje třídu, přidejte následující `using` direktivy.

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2. Proveďte `TestCompletionCommandHandler` třídu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> implementovat rozhraní.

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3. Ve `TestCompletionCommandHandlerProvider` třídě importujte <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4. Přidejte některá privátní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>pole pro rozhraní pro rozšíření kódu a rozhraní .

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5. V konstruktoru `TestCompletionCommandHandler` třídy nastavte následující pole.

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6. Chcete-li zobrazit výběr výstřižků, když uživatel klepne na příkaz Vložit <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> **výstřižek,** přidejte k metodě následující kód. (Chcete-li toto vysvětlení `Exec()`čitelnější, kód, který se používá pro dokončení příkazu není zobrazen; místo toho bloky kódu jsou přidány do existující metody.) Za kód, který kontroluje znak, přidejte následující blok kódu.

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7. Pokud úryvek obsahuje pole, která lze procházet, relace rozšíření je zachována otevřená, dokud není rozšíření explicitně přijato; Pokud úryvek nemá žádná pole, relace je `null` uzavřena <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> a je vrácena metodou. V <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodě po kódu uživatelského rozhraní pro výběr fragmentu, který jste přidali v předchozím kroku, přidejte následující kód pro zpracování navigace výstřižků (když uživatel po vložení fragmentu **stiskne kartu Tab** nebo **Shift**+**Tab).**

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8. Chcete-li vložit fragment kódu, když uživatel zadá odpovídajícího zástupce a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> pak stiskne **klávesu Tab**, přidejte do metody kód. Soukromá metoda, která vloží úryvek, se zobrazí v pozdějším kroku. Za navigační kód, který jste přidali v předchozím kroku, přidejte následující kód.

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. Implementujte metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> rozhraní. V této implementaci jsou <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> jedinými <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>způsoby zájmu a . Ostatní metody by <xref:Microsoft.VisualStudio.VSConstants.S_OK>měly jen vrátit .

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. Implementujte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> metodu. Pomocná metoda, která ve skutečnosti vloží rozšíření je popsána v pozdějším kroku. Poskytuje <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> informace o řádcích a sloupcích, které můžete získat z . <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. Následující soukromá metoda vloží fragment kódu, založený buď na zástupce, nebo na názvu a cestě. Potom volá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> metodu s úryvek.

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

## <a name="build-and-test-code-snippet-expansion"></a>Sestavení a testování rozšíření fragmentu kódu
 Můžete otestovat, zda rozšíření fragmentu funguje v projektu.

1. Sestavte řešení. Při spuštění tohoto projektu v ladicím programu je spuštěna druhá instance sady Visual Studio.

2. Otevřete textový soubor a zadejte nějaký text.

3. Klikněte pravým tlačítkem myši na místo v textu a potom klikněte na **Vložit úryvek**.

4. U iniciátoru pro výběr fragmentů by se mělo zobrazit s vyskakovacím vyskakovacím formulářem, který říká **Testovat náhradní pole**. Poklepejte na automaticky otevírané okno.

     Měl by být vložen následující úryvek.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     Nestisknout **klávesu Enter** nebo **Esc**.

5. Stisknutím **kláves YTab** a **Shift**+**Tab** přepínejte mezi "first" a "second".

6. Přijměte vložení stisknutím **klávesy Enter** nebo **Esc**.

7. V jiné části textu zadejte "test" a stiskněte **klávesu Tab**. Vzhledem k tomu, že "test" je zástupce fragmentu kódu, měl by být fragment vložen znovu.

## <a name="next-steps"></a>Další kroky
