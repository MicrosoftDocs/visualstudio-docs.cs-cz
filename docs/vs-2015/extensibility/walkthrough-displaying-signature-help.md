---
title: 'Návod: zobrazení informace o podpisu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 280b5b517089ad9e5b38cb00dc9b14c68253d1e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202049"
---
# <a name="walkthrough-displaying-signature-help"></a>Návod: Zobrazení vyhrazené nápovědy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nápověda k podpisu (označovaná také jako *informace o parametrech*) zobrazuje podpis metody v popisu tlačítka, když uživatel zadá spouštěcí znak seznamu parametrů (obvykle levou závorku). Jako parametr a oddělovač parametrů (obvykle čárka) se zadávají popisy pro zobrazení dalšího parametru tučným písmem. Můžete definovat nápovědu k podpisu v kontextu jazykové služby nebo můžete definovat vlastní příponu názvu souboru a typ obsahu a zobrazit nápovědu pro tento typ, nebo můžete zobrazit nápovědu k podpisu pro existující typ obsahu (například "text"). Tento návod ukazuje, jak zobrazit nápovědu k podpisu pro typ obsahu "text".  
  
 Podpisovou nápovědu je obvykle spouštěna zadáním konkrétního znaku, například "(" (levá závorka) a zavřena, zadáním jiného znaku, například ")" (pravá závorka). Funkce IntelliSense, které jsou aktivovány zadáním znaku, lze implementovat pomocí obslužné rutiny příkazu pro stisknutí kláves ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní) a zprostředkovatele obslužné rutiny, který implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> rozhraní. Chcete-li vytvořit zdroj Help signatury, který je seznamem podpisů, které se účastní v nápovědě k podpisu, implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> rozhraní a poskytovatele zdroje, který implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> rozhraní. Poskytovatelé jsou části komponent Managed Extensibility Framework (MEF) a zodpovídá za exportování tříd source a Controller a k importu služeb a zprostředkovatelů, například <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , který umožňuje navigaci ve vyrovnávací paměti textu a na <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> , který spouští relaci s podpisem.  
  
 Tento návod ukazuje, jak implementovat podpisovou nápovědu pro pevně zakódovanou sadu identifikátorů. V úplných implementacích je jazyk zodpovědný za poskytování obsahu.  
  
## <a name="prerequisites"></a>Předpoklady  
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Vytvoření projektu MEF  
  
#### <a name="to-create-a-mef-project"></a>Vytvoření projektu MEF  
  
1. Vytvoří projekt VSIX v jazyce C#. (V dialogovém okně **Nový projekt** vyberte **Visual C#/rozšiřitelnost**a potom **projekt VSIX**.) Pojmenujte řešení `SignatureHelpTest` .  
  
2. Přidejte do projektu šablonu položky klasifikátoru editoru. Další informace naleznete v tématu [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Odstraňte existující soubory třídy.  
  
4. Do projektu přidejte následující odkazy a ujistěte se, že je **CopyLocal** nastavené na `false` :  
  
     Microsoft. VisualStudio. Editor  
  
     Microsoft. VisualStudio. Language. IntelliSense  
  
     Microsoft. VisualStudio. OLE. Interop  
  
     Microsoft. VisualStudio. Shell. 14.0  
  
     Microsoft. VisualStudio. TextManager. Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>Implementace podpisů a parametrů signatury  
 Zdroj Help Signature je založen na signaturách, které implementují <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> , z nichž každá obsahuje parametry, které implementují <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> . V plné implementaci se tyto informace získávají z dokumentace jazyka, ale v tomto příkladu jsou signatury pevně zakódované.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Implementace podpisů a parametrů signatury  
  
1. Přidejte soubor třídy a pojmenujte ho `SignatureHelpSource` .  
  
2. Přidejte následující importy.  
  
     [!code-csharp[VSSDKSignatureHelpTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#1)]
     [!code-vb[VSSDKSignatureHelpTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#1)]  
  
3. Přidejte třídu s názvem `TestParameter` , která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#2)]
     [!code-vb[VSSDKSignatureHelpTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#2)]  
  
4. Přidejte konstruktor, který nastaví všechny vlastnosti.  
  
     [!code-csharp[VSSDKSignatureHelpTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#3)]
     [!code-vb[VSSDKSignatureHelpTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#3)]  
  
5. Přidejte vlastnosti <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#4)]
     [!code-vb[VSSDKSignatureHelpTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#4)]  
  
6. Přidejte třídu s názvem `TestSignature` , která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#5)]
     [!code-vb[VSSDKSignatureHelpTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#5)]  
  
7. Přidejte některá soukromá pole.  
  
     [!code-csharp[VSSDKSignatureHelpTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#6)]
     [!code-vb[VSSDKSignatureHelpTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#6)]  
  
8. Přidejte konstruktor, který nastaví pole a přihlásí se k odběru <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> události.  
  
     [!code-csharp[VSSDKSignatureHelpTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#7)]
     [!code-vb[VSSDKSignatureHelpTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#7)]  
  
9. Deklaruje `CurrentParameterChanged` událost. Tato událost se vyvolá, když uživatel vyplní jeden z parametrů v signatuře.  
  
     [!code-csharp[VSSDKSignatureHelpTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#8)]
     [!code-vb[VSSDKSignatureHelpTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#8)]  
  
10. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> vlastnost tak, že vyvolá `CurrentParameterChanged` událost při změně hodnoty vlastnosti.  
  
     [!code-csharp[VSSDKSignatureHelpTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#9)]
     [!code-vb[VSSDKSignatureHelpTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#9)]  
  
11. Přidejte metodu, která vyvolá `CurrentParameterChanged` událost.  
  
     [!code-csharp[VSSDKSignatureHelpTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#10)]
     [!code-vb[VSSDKSignatureHelpTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#10)]  
  
12. Přidejte metodu, která vypočítá aktuální parametr porovnáním počtu čárek v rámci <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> s počtem čárek v signatuře.  
  
     [!code-csharp[VSSDKSignatureHelpTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#11)]
     [!code-vb[VSSDKSignatureHelpTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#11)]  
  
13. Přidejte obslužnou rutinu události pro <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> událost, která volá `ComputeCurrentParameter()` metodu.  
  
     [!code-csharp[VSSDKSignatureHelpTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#12)]
     [!code-vb[VSSDKSignatureHelpTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#12)]  
  
14. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> vlastnost. Tato vlastnost obsahuje objekt <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , který odpovídá rozsahu textu ve vyrovnávací paměti, na který se signatura vztahuje.  
  
     [!code-csharp[VSSDKSignatureHelpTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#13)]
     [!code-vb[VSSDKSignatureHelpTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#13)]  
  
15. Implementujte další parametry.  
  
     [!code-csharp[VSSDKSignatureHelpTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#14)]
     [!code-vb[VSSDKSignatureHelpTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#14)]  
  
## <a name="implementing-the-signature-help-source"></a>Implementace zdroje Help signatury  
 Zdroj Help signatury je sada signatur, pro které zadáte informace.  
  
#### <a name="to-implement-the-signature-help-source"></a>Implementace zdroje Help Signature  
  
1. Přidejte třídu s názvem `TestSignatureHelpSource` , která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#15)]
     [!code-vb[VSSDKSignatureHelpTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#15)]  
  
2. Přidejte odkaz na vyrovnávací paměť textu.  
  
     [!code-csharp[VSSDKSignatureHelpTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#16)]
     [!code-vb[VSSDKSignatureHelpTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#16)]  
  
3. Přidejte konstruktor, který nastaví vyrovnávací paměť textu a poskytovatele pro identifikaci zdroje.  
  
     [!code-csharp[VSSDKSignatureHelpTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#17)]
     [!code-vb[VSSDKSignatureHelpTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#17)]  
  
4. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> metodu. V tomto příkladu jsou signatury pevně kódované, ale v plné implementaci byste tyto informace získali z dokumentace jazyka.  
  
     [!code-csharp[VSSDKSignatureHelpTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#18)]
     [!code-vb[VSSDKSignatureHelpTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#18)]  
  
5. Pomocná metoda `CreateSignature()` je k dispozici pouze pro ilustraci.  
  
     [!code-csharp[VSSDKSignatureHelpTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#19)]
     [!code-vb[VSSDKSignatureHelpTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#19)]  
  
6. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> metodu. V tomto příkladu jsou k dispozici pouze dva signatury, z nichž každá má dva parametry. Proto se tato metoda nevyžaduje. V případě úplné implementace, ve které je k dispozici více než jeden zdroj Help signatury, se tato metoda používá k rozhodnutí, zda zdroj v nápovědě s nejvyšší prioritou může dodat shodný podpis. Pokud to nemůže, metoda vrátí hodnotu null a zdroj s další nejvyšší prioritou se vyzve k zadání shody.  
  
     [!code-csharp[VSSDKSignatureHelpTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#20)]
     [!code-vb[VSSDKSignatureHelpTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#20)]  
  
7. Implementujte metodu Dispose ():  
  
     [!code-csharp[VSSDKSignatureHelpTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#21)]
     [!code-vb[VSSDKSignatureHelpTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#21)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>Implementace zprostředkovatele zdrojů pro identifikaci  
 Poskytovatel zdroje pro nápovědu s podpisem zodpovídá za export součásti komponenty Managed Extensibility Framework (MEF) a pro vytvoření instance zdroje s povýšení signatur.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>Implementace poskytovatele zdroje pro poidentifikaci  
  
1. Přidejte třídu s názvem, `TestSignatureHelpSourceProvider` která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> , a exportujte ji pomocí typu <xref:Microsoft.VisualStudio.Utilities.NameAttribute> <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" a typu <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> před = "výchozí".  
  
     [!code-csharp[VSSDKSignatureHelpTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#22)]
     [!code-vb[VSSDKSignatureHelpTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#22)]  
  
2. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> pomocí vytvoření instance `TestSignatureHelpSource` .  
  
     [!code-csharp[VSSDKSignatureHelpTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#23)]
     [!code-vb[VSSDKSignatureHelpTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#23)]  
  
## <a name="implementing-the-command-handler"></a>Implementace obslužné rutiny příkazu  
 Podpisové nápovědě je obvykle spouštěna znakem (znak a symbol "). Tyto úhozy můžete zpracovat implementací, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> aby spustila relaci Help signatury, když obdrží (znak předchází známému názvu metody a odvolá relaci při přijetí znaku).  
  
#### <a name="to-implement-the-command-handler"></a>Implementace obslužné rutiny příkazu  
  
1. Přidejte třídu s názvem `TestSignatureHelpCommand` , která implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#24)]
     [!code-vb[VSSDKSignatureHelpTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#24)]  
  
2. Přidejte soukromá pole pro <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> adaptér (což umožňuje přidat obslužnou rutinu příkazu do řetězce obslužných rutin příkazu), textové zobrazení, signaturu, zprostředkovatele a relaci, nápovědu, a <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> Další <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#25)]
     [!code-vb[VSSDKSignatureHelpTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#25)]  
  
3. Přidejte konstruktor pro inicializaci těchto polí a přidejte filtr příkazů do řetězce filtrů příkazů.  
  
     [!code-csharp[VSSDKSignatureHelpTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#26)]
     [!code-vb[VSSDKSignatureHelpTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#26)]  
  
4. Implementujte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodu, která aktivuje relaci Help signatury, když filtr příkazu obdrží (znak po jednom ze známých názvů metod a zavře relaci, když obdrží znak), zatímco relace je stále aktivní. V každém případě se příkaz přepošle.  
  
     [!code-csharp[VSSDKSignatureHelpTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#27)]
     [!code-vb[VSSDKSignatureHelpTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#27)]  
  
5. Implementujte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu tak, aby vždy přeposlala příkaz.  
  
     [!code-csharp[VSSDKSignatureHelpTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#28)]
     [!code-vb[VSSDKSignatureHelpTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#28)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>Implementace poskytovatele příkazů pro Help signaturu  
 Pomocí příkazu <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> k vytvoření instance obslužné rutiny příkazu pro vytvoření instance obslužné rutiny příkazového řádku můžete poskytnout příkaz k podpisu.  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>Implementace poskytovatele příkazu help Signature  
  
1. Přidejte třídu s názvem `TestSignatureHelpController` , která implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> a exportujte ji pomocí <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> a <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#29)]
     [!code-vb[VSSDKSignatureHelpTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#29)]  
  
2. Importujte <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (slouží k získání <xref:Microsoft.VisualStudio.Text.Editor.ITextView> objektu, s daným <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objektem), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (slouží k vyhledání aktuálního slova) a <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (pro aktivaci relace Nápověda podpisu).  
  
     [!code-csharp[VSSDKSignatureHelpTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#30)]
     [!code-vb[VSSDKSignatureHelpTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#30)]  
  
3. Implementujte <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metodu vytvořením instance `TestSignatureCommandHandler` .  
  
     [!code-csharp[VSSDKSignatureHelpTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#31)]
     [!code-vb[VSSDKSignatureHelpTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#31)]  
  
## <a name="building-and-testing-the-code"></a>Sestavování a testování kódu  
 Chcete-li otestovat tento kód, sestavte řešení SignatureHelpTest a spusťte ho v experimentální instanci.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Sestavení a testování řešení SignatureHelpTest  
  
1. Sestavte řešení.  
  
2. Při spuštění tohoto projektu v ladicím programu je vytvořena instance druhé instance aplikace Visual Studio.  
  
3. Vytvořte textový soubor a napište nějaký text, který obsahuje slovo "Přidat" a levou závorku.  
  
4. Po zadání levé závorky byste měli vidět popis, který zobrazí seznam dvou podpisů `add()` metody.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
