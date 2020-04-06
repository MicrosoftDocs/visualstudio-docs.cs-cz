---
title: 'Návod: Zobrazení nápovědy k podpisu | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f85d7eb3959064468e7583ec0c8a927f3e139daf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697419"
---
# <a name="walkthrough-display-signature-help"></a>Návod: Zobrazit nápovědu k podpisu
Nápověda k podpisu (označovaná také jako *Informace o parametrech)* zobrazí podpis metody v popisku, když uživatel zadá počáteční znak seznamu parametrů (obvykle počáteční závorky). Jako oddělovač parametrů a parametrů (obvykle čárka) jsou aktualizovány popisek zobrazit další parametr tučně. Nápovědu k podpisu můžete definovat následujícími způsoby: v kontextu jazykové služby definujte vlastní příponu názvu souboru a typ obsahu a zobrazte nápovědu k podpisu pouze pro tento typ nebo zobrazte nápovědu k podpisu pro existující typ obsahu (například "text"). Tento návod ukazuje, jak zobrazit nápovědu k podpisu pro typ obsahu "text".

 Nápověda k podpisu se obvykle aktivuje zadáním určitého znaku, například "(" (počáteční závorky) a zakončena zadáním jiného znaku, například ")" (uzavírací závorky). Funkce IntelliSense, které jsou spuštěny zadáním znaku, lze implementovat pomocí <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obslužné rutiny <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> příkazů pro úhozy (rozhraní) a poskytovatele obslužné rutiny, který implementuje rozhraní. Chcete-li vytvořit zdroj nápovědy k podpisu, což je seznam <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> podpisů, které se <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> účastní nápovědy k podpisu, implementujte rozhraní a zdrojového zprostředkovatele, který rozhraní spouští. Zprostředkovatelé jsou součásti architektury spravované rozšiřitelnosti (MEF) a jsou zodpovědní za export tříd zdrojového a <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>kontroleru a import služeb a zprostředkovatelů, například , který umožňuje navigaci v textové vyrovnávací paměti, a <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, který aktivuje relaci nápovědy k podpisu.

 Tento návod ukazuje, jak nastavit nápovědu k podpisu pro pevně zakódovanou sadu identifikátorů. V úplných implementacích je jazyk zodpovědný za poskytování tohoto obsahu.

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015, nenainstalujete Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-mef-project"></a>Vytvoření projektu MEF

#### <a name="to-create-a-mef-project"></a>Vytvoření projektu MEF

1. Vytvořte projekt C# VSIX. (V dialogovém okně **Nový projekt** vyberte možnost **Vizuální C# / Rozšiřitelnost**a potom **v six projectu**.) Pojmenujte `SignatureHelpTest`řešení .

2. Přidejte do projektu šablonu položky třídění editoru. Další informace naleznete [v tématu Vytvoření rozšíření se šablonou položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Odstraňte existující soubory tříd.

4. Přidejte do projektu následující odkazy a ujistěte se, že je nastavena na hodnotu `false` **CopyLocal** :

     Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.Shell.14.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-signature-help-signatures-and-parameters"></a>Implementace podpisů a parametrů nápovědy k podpisu
 Zdroj nápovědy k podpisu je <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>založen na podpisech, <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>které implementují , z nichž každý obsahuje parametry, které implementují . V úplné implementaci by tyto informace byly získány z jazykové dokumentace, ale v tomto příkladu jsou podpisy pevně zakódovány.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Implementace podpisů a parametrů nápovědy k podpisu

1. Přidejte soubor třídy `SignatureHelpSource`a pojmenujte jej .

2. Přidejte následující importy.

     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]

3. Přidejte třídu s názvem, `TestParameter` která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.

     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]

4. Přidejte konstruktor, který nastaví všechny vlastnosti.

     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]

5. Přidejte vlastnosti . <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>

     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]

6. Přidejte třídu s názvem, `TestSignature` která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.

     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]

7. Přidejte některá soukromá pole.

     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]

8. Přidejte konstruktor, který nastaví pole <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> a přihlásí k odběru události.

     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]

9. Deklarujte `CurrentParameterChanged` událost. Tato událost je vyvolána, když uživatel vyplní jeden z parametrů v podpisu.

     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]

10. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> vlastnost tak, `CurrentParameterChanged` aby vyvolá událost při změně hodnoty vlastnosti.

     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]

11. Přidejte metodu, `CurrentParameterChanged` která vyvolá událost.

     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]

12. Přidejte metodu, která vypočítá aktuální parametr porovnáním počtu <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> čárek v počtu čárek v podpisu.

     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]

13. Přidejte obslužnou rutinu <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> události, která volá metodu. `ComputeCurrentParameter()`

     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]

14. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> vlastnost. Tato vlastnost <xref:Microsoft.VisualStudio.Text.ITrackingSpan> obsahuje, který odpovídá rozpětí textu ve vyrovnávací paměti, na které se vztahuje podpis.

     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]

15. Implementujte další parametry.

     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]

## <a name="implement-the-signature-help-source"></a>Implementace zdroje nápovědy k podpisu
 Zdroj nápovědy k podpisu je sada podpisů, pro které poskytujete informace.

#### <a name="to-implement-the-signature-help-source"></a>Implementace zdroje nápovědy k podpisu

1. Přidejte třídu s názvem, `TestSignatureHelpSource` která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.

     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]

2. Přidejte odkaz na textovou vyrovnávací paměť.

     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]

3. Přidejte konstruktor, který nastaví vyrovnávací paměť textu a zdrojového zprostředkovatele nápovědy k podpisu.

     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]

4. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> metodu. V tomto příkladu jsou podpisy pevně zakódovány, ale v úplné implementaci byste tyto informace získali z jazykové dokumentace.

     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]

5. Pomocná metoda `CreateSignature()` je k dispozici pouze pro ilustraci.

     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]

6. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> metodu. V tomto příkladu jsou pouze dva podpisy, z nichž každý má dva parametry. Proto tato metoda není vyžadována. V plnější implementaci, ve které je k dispozici více než jeden zdroj nápovědy k podpisu, se tato metoda používá k rozhodnutí, zda zdroj nápovědy k podpisu s nejvyšší prioritou může poskytnout odpovídající podpis. Pokud nemůže, metoda vrátí hodnotu null a zdroj s další nejvyšší prioritou je požádán o zadání shody.

     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]

7. Zavést `Dispose()` metodu:

     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]

## <a name="implement-the-signature-help-source-provider"></a>Implementace zprostředkovatele zdroje nápovědy k podpisu
 Zprostředkovatel zdroje nápovědy k podpisu je zodpovědný za export součásti Mef (Managed Extensibility Framework) a za vytvoření instance zdroje nápovědy k podpisu.

#### <a name="to-implement-the-signature-help-source-provider"></a>Implementace zprostředkovatele zdroje nápovědy k podpisu

1. Přidejte třídu `TestSignatureHelpSourceProvider` s <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>názvem, která <xref:Microsoft.VisualStudio.Utilities.NameAttribute>implementuje , a exportujte ji s , a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" a <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> before="default".

     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]

2. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> vytvořením instance `TestSignatureHelpSource`.

     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]

## <a name="implement-the-command-handler"></a>Implementace obslužné rutiny příkazu
 Nápověda k podpisu je obvykle spuštěna znakem počáteční závorky "(" a zakončena znakem uzavírací závorky ")". Tyto úhozy můžete zpracovat spuštěním <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> tak, aby se spustila relace nápovědy k podpisu, když obdrží znak počáteční závorky předchází název známé metody a zavře relace, když obdrží znak uzavírací závorky.

#### <a name="to-implement-the-command-handler"></a>Implementace obslužné rutiny příkazu

1. Přidejte třídu s názvem, `TestSignatureHelpCommand` která implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.

     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]

2. Přidejte soukromá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> pole adaptéru (který umožňuje přidat obslužnou rutinu příkazu do řetězce obslužných rutin příkazů), zobrazení textu, zprostředkovatele nápovědy k podpisu <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>a relace, a a další <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.

     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]

3. Přidejte konstruktor pro inicializaci těchto polí a přidání filtru příkazů do řetězce filtrů příkazů.

     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]

4. Implementujte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodu pro aktivaci relace nápovědy k podpisu, když filtr příkazů obdrží počáteční závorku "(" znak za jedním z názvů známých metod a zavřete relaci, když obdrží uzavírací závorku ")" znak, zatímco relace je stále aktivní. V každém případě je příkaz předán dál.

     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]

5. Implementujte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu tak, aby vždy předá příkaz.

     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]

## <a name="implement-the-signature-help-command-provider"></a>Implementace zprostředkovatele příkazu Nápověda k podpisu
 Příkaz Nápověda k podpisu můžete <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> zadat implementací instance obslužné rutiny příkazu při vytvoření textového zobrazení.

### <a name="to-implement-the-signature-help-command-provider"></a>Implementace zprostředkovatele příkazu Nápověda k podpisu

1. Přidejte třídu `TestSignatureHelpController` s <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> názvem, která <xref:Microsoft.VisualStudio.Utilities.NameAttribute> <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>implementuje a exportovat s , a <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.

     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]

2. Importovat <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (slouží k <xref:Microsoft.VisualStudio.Text.Editor.ITextView>získání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> , daný <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> objekt), (slouží k nalezení <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> aktuální slovo) a (chcete-li spustit relaci nápovědy k podpisu).

     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]

3. Implementujte <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metodu vytvořením `TestSignatureCommandHandler`instance .

     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]

## <a name="build-and-test-the-code"></a>Sestavení a testování kódu
 Chcete-li tento kód otestovat, vytvořte řešení SignatureHelpTest a spusťte jej v experimentální instanci.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Vytvoření a testování řešení SignatureHelpTest

1. Sestavte řešení.

2. Při spuštění tohoto projektu v ladicím programu je spuštěna druhá instance sady Visual Studio.

3. Vytvořte textový soubor a zadejte text, který obsahuje slovo "přidat" plus počáteční závorku.

4. Po zadání počáteční závorky by se měl zobrazit popisek, který zobrazí `add()` seznam dvou podpisů metody.

## <a name="see-also"></a>Viz také
- [Návod: Propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
