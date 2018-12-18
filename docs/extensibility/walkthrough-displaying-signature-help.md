---
title: 'Návod: Zobrazení vyhrazené nápovědy | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cc260fe45bf4c6cf801718c2f4c3bbaa98842dd6
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498900"
---
# <a name="walkthrough-display-signature-help"></a>Návod: Zobrazení vyhrazené nápovědy
Signaturám (označované také jako *informace o parametru*) zobrazí v popisku podpis metody, když uživatel zadá znak start seznamu parametrů (obvykle Levá závorka). Jako parametr a oddělovač parametr (obvykle čárku) jsou zadány, popisek se aktualizuje a zobrazí další parametr tučným písmem. Pomoc při podpisu můžete definovat takto: v rámci služby jazyka, definovat vlastní příponu názvu souboru a typu obsahu a zobrazení pomoc při podpisu pro právě tento typ nebo zobrazit pomoc při podpisu pro existující typ obsahu (například "text"). Tento návod ukazuje, jak zobrazit nápovědu k podpisu pro typ obsahu "text".  
  
 Nápověda k podpisu se obvykle aktivuje zadáním konkrétní znak, například "(" (levá závorka) a zrušit tak, že zadáte další znak, například ")" (ukončovací závorka). Funkce technologie IntelliSense, které jsou aktivovány psaní znak může být implementována pomocí obslužná rutina příkazu stisknutí kláves ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní) a zprostředkovatele obslužná rutina, která implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> rozhraní. Chcete-li vytvořit zdroj pomoc při podpisu, který je uvedený seznam podpisy, které jsou součástí pomoc při podpisu, implementovat <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> rozhraní a poskytovatele zdroj, který běží <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> rozhraní. Poskytovatelé jsou součástí Managed Extensibility Framework (MEF) a jsou zodpovědné za třídy zdroje a kontroler exportu a importu služby a zprostředkovatelů, například <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, která umožňuje navigaci ve vyrovnávací paměti textu a <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, která spustí relaci pomoc při podpisu.  
  
 Tento návod ukazuje, jak nastavit pomoc při podpisu pro pevně zakódované sadu identifikátorů. V úplné implementace jazyka zodpovídá za poskytování obsahu.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnutý jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Vytvoření projektu rozhraní MEF  
  
#### <a name="to-create-a-mef-project"></a>Chcete-li vytvořit projekt rozhraní MEF  
  
1.  Vytvořte projekt VSIX C#. (V **nový projekt** dialogového okna, vyberte **Visual C# / rozšíření**, pak **projekt VSIX**.) Pojmenujte řešení `SignatureHelpTest`.  
  
2.  Přidejte do projektu šablony položky editoru třídění. Další informace najdete v tématu [vytváření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Odstraníte existující soubory tříd.  
  
4.  Přidejte následující odkazy do projektu a ujistěte se, že **CopyLocal** je nastavena na `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Sestavení Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implement-signature-help-signatures-and-parameters"></a>Implementace pomoc při podpisu podpisy a parametry  
 Pomoc při podpisu zdroje je založen na podpisy, které implementují <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, z nichž každý obsahuje parametry, které implementují <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. V úplnou implementaci tyto informace by byl získán z dokumentace k jazyku, ale v tomto příkladu jsou pevně zakódované podpisy.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>K implementaci pomoc při podpisu podpisy a parametry  
  
1.  Přidejte soubor třídy a pojmenujte ho `SignatureHelpSource`.  
  
2.  Přidejte následující importy.  
  
     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]  
  
3.  Přidejte třídu pojmenovanou `TestParameter` , který implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]  
  
4.  Přidáte konstruktor, který nastaví všechny vlastnosti.  
  
     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]  
  
5.  Přidání vlastnosti <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]  
  
6.  Přidejte třídu pojmenovanou `TestSignature` , který implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.  
  
     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]  
  
7.  Přidáte některé soukromé pole.  
  
     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]  
  
8.  Přidat konstruktor, který nastaví pole a přihlásí se k odběru <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> událostí.  
  
     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]  
  
9. Deklarace `CurrentParameterChanged` událostí. Tato událost je aktivována, když uživatel vyplní jeden z parametrů v signatuře.  
  
     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]  
  
10. Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> vlastnost tak, že vyvolá `CurrentParameterChanged` události při změně hodnoty vlastnosti.  
  
     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]  
  
11. Přidejte metodu, která vyvolá `CurrentParameterChanged` událostí.  
  
     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]  
  
12. Přidejte metodu, která vypočítá aktuální parametr porovnáním počet čárek ve <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> počtu čárkami v podpisu.  
  
     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]  
  
13. Přidat obslužnou rutinu události pro <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> událost, která volá `ComputeCurrentParameter()` metody.  
  
     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]  
  
14. Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> vlastnost. Tato vlastnost obsahuje <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , který odpovídá rozsah textu ve vyrovnávací paměti, ke kterému se vztahuje podpis.  
  
     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]  
  
15. Implementujte další parametry.  
  
     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]  
  
## <a name="implement-the-signature-help-source"></a>Implementace zdroje pomoc při podpisu  
 Pomoc při podpisu zdroje je sada podpisy, pro které poskytnete informace.  
  
#### <a name="to-implement-the-signature-help-source"></a>K implementaci zdroji pomoc při podpisu  
  
1.  Přidejte třídu pojmenovanou `TestSignatureHelpSource` , který implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.  
  
     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]  
  
2.  Přidejte odkaz na textovou vyrovnávací paměť.  
  
     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]  
  
3.  Přidáte konstruktor, který nastaví textové vyrovnávací paměti a poskytovatel správy zdrojových pomoc při podpisu.  
  
     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]  
  
4.  Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> metody. V tomto příkladu podpisy jsou pevně zakódované, ale v úplnou implementaci byste získat tyto informace z dokumentace k jazyku.  
  
     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]  
  
5.  Pomocná metoda `CreateSignature()` je k dispozici pouze pro ilustraci.  
  
     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]  
  
6.  Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> metody. V tomto příkladu jsou jenom dvě podpisy, z nichž každá má dva parametry. Proto tato metoda se nevyžaduje. Tato metoda se v plnější implementaci, ve kterém je více než jeden podpis pomoci zdroj k dispozici, používá se rozhodnout, zda zdroj pomoc při podpisu nejvyšší prioritou lze zadat odpovídající signaturou. V případě nedostupnosti, metoda vrátí hodnotu null a zdroji další nejvyšší prioritou je vyzván k zadání shoda.  
  
     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]  
  
7.  Implementace `Dispose()` metody:  
  
     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]  
  
## <a name="implement-the-signature-help-source-provider"></a>Implementace zprostředkovatele zdrojového pomoc při podpisu  
 Pomoc při podpisu poskytovatel správy zdrojových je odpovědný za export součást Managed Extensibility Framework (MEF) a pro vytvoření instance zdroje pomoc při podpisu.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>Pro implementaci zprostředkovatele zdroje pomoc při podpisu  
  
1.  Přidejte třídu pojmenovanou `TestSignatureHelpSourceProvider` , který implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>a exportujte ho pomocí <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" a <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> z před = "Výchozí".  
  
     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]  
  
2.  Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> po vytvoření instance `TestSignatureHelpSource`.  
  
     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]  
  
## <a name="implement-the-command-handler"></a>Implementujte obslužnou rutinu příkazu  
 Nápověda k podpisu se obvykle aktivuje levou závorku znak "(" znak a zavřených uzavírací závorku")". Tyto stisknutí kláves můžete zpracovat spuštěním <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> tak, aby se aktivuje při přijetí počáteční relace pomoc při podpisu znak závorky předchází název metody známé a zavře relace, když obdrží znak pravé závorky znak.  
  
#### <a name="to-implement-the-command-handler"></a>K implementaci obslužná rutina příkazu  
  
1.  Přidejte třídu pojmenovanou `TestSignatureHelpCommand` , který implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]  
  
2.  Přidat soukromé pole pro <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> adaptéru (který můžete přidat obslužná rutina příkazu do obslužné rutiny příkazů z řetězce), zobrazení textu, pomoc při podpisu zprostředkovatele a relace, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>a dalších <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]  
  
3.  Přidejte konstruktor a tato pole inicializovat přidat filtr příkazu pro příkaz z řetězu filtrů.  
  
     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]  
  
4.  Implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody k aktivaci pomoc při podpisu relace, když filtr příkaz obdrží levou závorku znak "(" znak po jednoho ze známých metoda názvy a zavřete relaci, když obdrží pravou závorku")" relace je pořád aktivní. V každém případě je předán příkazu.  
  
     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]  
  
5.  Implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu tak, že vždycky předá příkazu.  
  
     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]  
  
## <a name="implement-the-signature-help-command-provider"></a>Implementace zprostředkovatele příkazu pomoc při podpisu  
 Můžete zadat příkaz pomoc při podpisu pomocí implementace <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> pro vytvoření instance obslužná rutina příkazu, když se vytvoří zobrazení textu.  
  
### <a name="to-implement-the-signature-help-command-provider"></a>Pro implementaci zprostředkovatele příkaz pomoc při podpisu  
  
1.  Přidejte třídu pojmenovanou `TestSignatureHelpController` , který implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> a exportujte ho pomocí <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, a <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.  
  
     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]  
  
2.  Import <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (použít k získání <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, daný <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objektu), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (používá se k nalezení aktuálního slova) a <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (pro aktivaci relace pomoc při podpisu).  
  
     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]  
  
3.  Implementace <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metoda po vytvoření instance `TestSignatureCommandHandler`.  
  
     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]  
  
## <a name="build-and-test-the-code"></a>Vytváření a testování kódu  
 K otestování tohoto kódu sestavte řešení SignatureHelpTest a spusťte v experimentální instanci.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Pro vytváření a testování SignatureHelpTest řešení  
  
1.  Sestavte řešení.  
  
2.  Při spuštění tohoto projektu v ladicím programu se spustí druhé instanci aplikace Visual Studio.  
  
3.  Vytvoření textového souboru a zadejte nějaký text, který obsahuje slovo "Přidat" a levou závorku.  
  
4.  Po zadání levou závorku, měli byste vidět popisu, který se zobrazí seznam dvou podpisy `add()` metody.  
  
## <a name="see-also"></a>Viz také:  
 [Návod: Propojení typ obsahu, který má příponu názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)