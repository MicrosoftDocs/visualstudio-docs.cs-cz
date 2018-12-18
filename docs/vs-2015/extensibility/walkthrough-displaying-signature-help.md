---
title: 'Návod: Zobrazení vyhrazené nápovědy | Dokumentace Microsoftu'
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
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a3b902c32563da6bc21778a09b4aeaebaeabeaa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734633"
---
# <a name="walkthrough-displaying-signature-help"></a>Návod: Zobrazení vyhrazené nápovědy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Signaturám (označované také jako *informace o parametru*) zobrazí v popisku podpis metody, když uživatel zadá znak start seznamu parametrů (obvykle Levá závorka). Jako parametr a oddělovač parametr (obvykle čárku) jsou zadány, popisek se aktualizuje a zobrazí další parametr tučným písmem. Pomoc při podpisu můžete definovat v rámci služby jazyka, nebo můžete definovat vlastní název souboru příponu a obsah zadejte a zobrazit nápovědu k podpisu pro právě tento typ, nebo můžete zobrazit pomoc při podpisu pro existující typ obsahu (například "text"). Tento návod ukazuje, jak zobrazit nápovědu k podpisu pro typ obsahu "text".  
  
 Nápověda k podpisu se obvykle aktivuje zadáním konkrétní znak, například "(" (levá závorka) a zrušit tak, že zadáte další znak, například ")" (ukončovací závorka). Funkce technologie IntelliSense, které jsou aktivovány psaní znak může být implementována pomocí obslužná rutina příkazu stisknutí kláves ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní) a zprostředkovatele obslužná rutina, která implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> rozhraní. Chcete-li vytvořit zdroj pomoc při podpisu, který je uvedený seznam podpisy, které jsou součástí pomoc při podpisu, implementovat <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> rozhraní a poskytovatele zdroj, který implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> rozhraní. Poskytovatelé jsou součástí Managed Extensibility Framework (MEF) a jsou zodpovědné za třídy zdroje a kontroler exportu a importu služby a zprostředkovatelů, například <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, která umožňuje navigaci ve vyrovnávací paměti textu a <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, která spustí relaci pomoc při podpisu.  
  
 Tento návod ukazuje, jak implementovat pomoc při podpisu pro pevně zakódované sadu identifikátorů. V úplné implementace jazyka zodpovídá za poskytování obsahu.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
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
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>Implementace podpis podpisy a parametry  
 Pomoc při podpisu zdroje je založen na podpisy, které implementují <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, z nichž každý obsahuje parametry, které implementují <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. V úplnou implementaci tyto informace by byl získán z dokumentace k jazyku, ale v tomto příkladu jsou pevně zakódované podpisy.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>K implementaci pomoc při podpisu podpisy a parametry  
  
1.  Přidejte soubor třídy a pojmenujte ho `SignatureHelpSource`.  
  
2.  Přidejte následující importy.  
  
     [!code-csharp[VSSDKSignatureHelpTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#1)]
     [!code-vb[VSSDKSignatureHelpTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#1)]  
  
3.  Přidejte třídu pojmenovanou `TestParameter` , který implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#2)]
     [!code-vb[VSSDKSignatureHelpTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#2)]  
  
4.  Přidáte konstruktor, který nastaví všechny vlastnosti.  
  
     [!code-csharp[VSSDKSignatureHelpTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#3)]
     [!code-vb[VSSDKSignatureHelpTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#3)]  
  
5.  Přidání vlastnosti <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#4)]
     [!code-vb[VSSDKSignatureHelpTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#4)]  
  
6.  Přidejte třídu pojmenovanou `TestSignature` , který implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#5)]
     [!code-vb[VSSDKSignatureHelpTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#5)]  
  
7.  Přidáte některé soukromé pole.  
  
     [!code-csharp[VSSDKSignatureHelpTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#6)]
     [!code-vb[VSSDKSignatureHelpTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#6)]  
  
8.  Přidat konstruktor, který nastaví pole a přihlásí se k odběru <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> událostí.  
  
     [!code-csharp[VSSDKSignatureHelpTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#7)]
     [!code-vb[VSSDKSignatureHelpTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#7)]  
  
9. Deklarace `CurrentParameterChanged` událostí. Tato událost je aktivována, když uživatel vyplní jeden z parametrů v signatuře.  
  
     [!code-csharp[VSSDKSignatureHelpTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#8)]
     [!code-vb[VSSDKSignatureHelpTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#8)]  
  
10. Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> vlastnost tak, že vyvolá `CurrentParameterChanged` události při změně hodnoty vlastnosti.  
  
     [!code-csharp[VSSDKSignatureHelpTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#9)]
     [!code-vb[VSSDKSignatureHelpTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#9)]  
  
11. Přidejte metodu, která vyvolá `CurrentParameterChanged` událostí.  
  
     [!code-csharp[VSSDKSignatureHelpTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#10)]
     [!code-vb[VSSDKSignatureHelpTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#10)]  
  
12. Přidejte metodu, která vypočítá aktuální parametr porovnáním počet čárek ve <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> počtu čárkami v podpisu.  
  
     [!code-csharp[VSSDKSignatureHelpTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#11)]
     [!code-vb[VSSDKSignatureHelpTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#11)]  
  
13. Přidat obslužnou rutinu události pro <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> událost, která volá `ComputeCurrentParameter()` metody.  
  
     [!code-csharp[VSSDKSignatureHelpTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#12)]
     [!code-vb[VSSDKSignatureHelpTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#12)]  
  
14. Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> vlastnost. Tato vlastnost obsahuje <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , který odpovídá rozsah textu ve vyrovnávací paměti, ke kterému se vztahuje podpis.  
  
     [!code-csharp[VSSDKSignatureHelpTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#13)]
     [!code-vb[VSSDKSignatureHelpTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#13)]  
  
15. Implementujte další parametry.  
  
     [!code-csharp[VSSDKSignatureHelpTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#14)]
     [!code-vb[VSSDKSignatureHelpTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#14)]  
  
## <a name="implementing-the-signature-help-source"></a>Implementace zdroje nápovědy podpis  
 Pomoc při podpisu zdroje je sada podpisy, pro které poskytnete informace.  
  
#### <a name="to-implement-the-signature-help-source"></a>K implementaci zdroji pomoc při podpisu  
  
1.  Přidejte třídu pojmenovanou `TestSignatureHelpSource` , který implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#15)]
     [!code-vb[VSSDKSignatureHelpTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#15)]  
  
2.  Přidejte odkaz na textovou vyrovnávací paměť.  
  
     [!code-csharp[VSSDKSignatureHelpTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#16)]
     [!code-vb[VSSDKSignatureHelpTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#16)]  
  
3.  Přidáte konstruktor, který nastaví textové vyrovnávací paměti a poskytovatel správy zdrojových pomoc při podpisu.  
  
     [!code-csharp[VSSDKSignatureHelpTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#17)]
     [!code-vb[VSSDKSignatureHelpTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#17)]  
  
4.  Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> metody. V tomto příkladu podpisy jsou pevně zakódované, ale v úplnou implementaci byste získat tyto informace z dokumentace k jazyku.  
  
     [!code-csharp[VSSDKSignatureHelpTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#18)]
     [!code-vb[VSSDKSignatureHelpTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#18)]  
  
5.  Pomocná metoda `CreateSignature()` je k dispozici pouze pro ilustraci.  
  
     [!code-csharp[VSSDKSignatureHelpTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#19)]
     [!code-vb[VSSDKSignatureHelpTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#19)]  
  
6.  Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> metody. V tomto příkladu jsou jenom dvě podpisy, z nichž každá má dva parametry. Proto tato metoda se nevyžaduje. Tato metoda se v plnější implementaci, ve kterém je více než jeden podpis pomoci zdroj k dispozici, používá se rozhodnout, zda zdroj pomoc při podpisu nejvyšší prioritou lze zadat odpovídající signaturou. V případě nedostupnosti, metoda vrátí hodnotu null a zdroji další nejvyšší prioritou je vyzván k zadání shoda.  
  
     [!code-csharp[VSSDKSignatureHelpTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#20)]
     [!code-vb[VSSDKSignatureHelpTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#20)]  
  
7.  Implementace metody Dispose():  
  
     [!code-csharp[VSSDKSignatureHelpTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#21)]
     [!code-vb[VSSDKSignatureHelpTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#21)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>Implementace zprostředkovatele zdroje nápovědy podpis  
 Pomoc při podpisu poskytovatel správy zdrojových je odpovědný za export součást Managed Extensibility Framework (MEF) a pro vytvoření instance zdroje pomoc při podpisu.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>Pro implementaci zprostředkovatele zdroje pomoc při podpisu  
  
1.  Přidejte třídu pojmenovanou `TestSignatureHelpSourceProvider` , který implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>a exportujte ho pomocí <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" a <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> z před = "Výchozí".  
  
     [!code-csharp[VSSDKSignatureHelpTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#22)]
     [!code-vb[VSSDKSignatureHelpTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#22)]  
  
2.  Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> po vytvoření instance `TestSignatureHelpSource`.  
  
     [!code-csharp[VSSDKSignatureHelpTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#23)]
     [!code-vb[VSSDKSignatureHelpTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#23)]  
  
## <a name="implementing-the-command-handler"></a>Implementace obslužné rutiny příkazu  
 Nápovědu k signatuře obvykle aktivuje (znak a zavřených pomocí) znaků. Implementací dokáže zpracovat tyto stisknutí kláves <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> tak, aby se aktivuje při přijetí relace pomoc při podpisu (znak předchází název metody známé a zavře relace, když přijme) znaků.  
  
#### <a name="to-implement-the-command-handler"></a>K implementaci obslužná rutina příkazu  
  
1.  Přidejte třídu pojmenovanou `TestSignatureHelpCommand` , který implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#24)]
     [!code-vb[VSSDKSignatureHelpTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#24)]  
  
2.  Přidat soukromé pole pro <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> adaptéru (který můžete přidat obslužná rutina příkazu do obslužné rutiny příkazů z řetězce), zobrazení textu, pomoc při podpisu zprostředkovatele a relace, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>a dalších <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#25)]
     [!code-vb[VSSDKSignatureHelpTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#25)]  
  
3.  Přidejte konstruktor a tato pole inicializovat přidat filtr příkazu pro příkaz z řetězu filtrů.  
  
     [!code-csharp[VSSDKSignatureHelpTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#26)]
     [!code-vb[VSSDKSignatureHelpTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#26)]  
  
4.  Implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metoda k aktivaci pomoc při podpisu relace, jakmile přijme příkaz filtru (znak po jednoho ze známých metoda názvy a zavřete relaci, když obdrží) znak je stále aktivní relace. V každém případě je předán příkazu.  
  
     [!code-csharp[VSSDKSignatureHelpTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#27)]
     [!code-vb[VSSDKSignatureHelpTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#27)]  
  
5.  Implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu tak, že vždycky předá příkazu.  
  
     [!code-csharp[VSSDKSignatureHelpTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#28)]
     [!code-vb[VSSDKSignatureHelpTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#28)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>Implementace zprostředkovatele příkazu podpis nápovědy  
 Můžete zadat příkaz pomoc při podpisu pomocí implementace <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> pro vytvoření instance obslužná rutina příkazu, když se vytvoří zobrazení textu.  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>Pro implementaci zprostředkovatele příkaz pomoc při podpisu  
  
1.  Přidejte třídu pojmenovanou `TestSignatureHelpController` , který implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> a exportujte ho pomocí <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, a <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#29)]
     [!code-vb[VSSDKSignatureHelpTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#29)]  
  
2.  Import <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (použít k získání <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, daný <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objektu), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (používá se k nalezení aktuálního slova) a <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (pro aktivaci relace pomoc při podpisu).  
  
     [!code-csharp[VSSDKSignatureHelpTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#30)]
     [!code-vb[VSSDKSignatureHelpTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#30)]  
  
3.  Implementace <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metoda po vytvoření instance `TestSignatureCommandHandler`.  
  
     [!code-csharp[VSSDKSignatureHelpTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#31)]
     [!code-vb[VSSDKSignatureHelpTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#31)]  
  
## <a name="building-and-testing-the-code"></a>Vytváření a testování kódu  
 K otestování tohoto kódu sestavte řešení SignatureHelpTest a spusťte v experimentální instanci.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Pro vytváření a testování SignatureHelpTest řešení  
  
1.  Sestavte řešení.  
  
2.  Při spuštění tohoto projektu v ladicím programu, je vytvořena instance druhou instanci aplikace Visual Studio.  
  
3.  Vytvoření textového souboru a zadejte nějaký text, který obsahuje slovo "Přidat" a levou závorku.  
  
4.  Po zadání levou závorku, měli byste vidět popisu, který se zobrazí seznam dvou podpisy `add()` metody.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

