---
title: 'Návod: zobrazení informace o podpisu | Microsoft Docs'
description: V tomto návodu se dozvíte, jak zobrazit nápovědu k podpisu pro typ textového obsahu. Nápověda k podpisu zobrazí podpis metody v popisu tlačítka.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be324ab48d42e859678ccf01d8c75faae6cea381
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876243"
---
# <a name="walkthrough-display-signature-help"></a>Návod: zobrazení podpisu – Help
Nápověda k podpisu (označovaná také jako *informace o parametrech*) zobrazuje podpis metody v popisu tlačítka, když uživatel zadá spouštěcí znak seznamu parametrů (obvykle levou závorku). Jako parametr a oddělovač parametrů (obvykle čárka) se zadávají popisy pro zobrazení dalšího parametru tučným písmem. Nápovědu k podpisu můžete definovat následujícími způsoby: v kontextu jazykové služby definujte vlastní příponu názvu souboru a typ obsahu a nápovědu pro zobrazení podpisu pro daný typ, nebo zobrazte nápovědu k podpisu pro existující typ obsahu (například "text"). Tento návod ukazuje, jak zobrazit nápovědu k podpisu pro typ obsahu "text".

 Podpisovou nápovědu je obvykle spouštěna zadáním konkrétního znaku, například "(" (levá závorka) a zavřena, zadáním jiného znaku, například ")" (pravá závorka). Funkce IntelliSense, které jsou aktivovány zadáním znaku, lze implementovat pomocí obslužné rutiny příkazu pro stisknutí kláves ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní) a zprostředkovatele obslužné rutiny, který implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> rozhraní. Chcete-li vytvořit zdroj Help signatury, který je seznamem podpisů, které se účastní v nápovědě k podpisům, implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> rozhraní a poskytovatele zdroje, který spouští <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> rozhraní. Poskytovatelé jsou části komponent Managed Extensibility Framework (MEF) a zodpovídá za exportování tříd source a Controller a k importu služeb a zprostředkovatelů, například <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , který umožňuje navigaci ve vyrovnávací paměti textu a na <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> , který spouští relaci s podpisem.

 Tento návod ukazuje, jak nastavit podpisovou nápovědu pro pevně zakódovanou sadu identifikátorů. V úplných implementacích je jazyk zodpovědný za poskytování obsahu.

## <a name="prerequisites"></a>Předpoklady
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-mef-project"></a>Vytvoření projektu MEF

#### <a name="to-create-a-mef-project"></a>Vytvoření projektu MEF

1. Vytvoří projekt VSIX v jazyce C#. (V dialogovém okně **Nový projekt** vyberte **Visual C#/rozšiřitelnost** a potom **projekt VSIX**.) Pojmenujte řešení `SignatureHelpTest` .

2. Přidejte do projektu šablonu položky klasifikátoru editoru. Další informace naleznete v tématu [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Odstraňte existující soubory třídy.

4. Do projektu přidejte následující odkazy a ujistěte se, že je **CopyLocal** nastavené na `false` :

     Microsoft. VisualStudio. Editor

     Microsoft. VisualStudio. Language. IntelliSense

     Microsoft. VisualStudio. OLE. Interop

     Microsoft. VisualStudio. Shell. 14.0

     Microsoft. VisualStudio. TextManager. Interop

## <a name="implement-signature-help-signatures-and-parameters"></a>Implementace podpisů a parametrů signatury
 Zdroj Help Signature je založen na signaturách, které implementují <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> , z nichž každá obsahuje parametry, které implementují <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> . V plné implementaci se tyto informace získávají z dokumentace jazyka, ale v tomto příkladu jsou signatury pevně zakódované.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Implementace podpisů a parametrů signatury

1. Přidejte soubor třídy a pojmenujte ho `SignatureHelpSource` .

2. Přidejte následující importy.

     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]

3. Přidejte třídu s názvem `TestParameter` , která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .

     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]

4. Přidejte konstruktor, který nastaví všechny vlastnosti.

     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]

5. Přidejte vlastnosti <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .

     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]

6. Přidejte třídu s názvem `TestSignature` , která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> .

     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]

7. Přidejte některá soukromá pole.

     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]

8. Přidejte konstruktor, který nastaví pole a přihlásí se k odběru <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> události.

     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]

9. Deklaruje `CurrentParameterChanged` událost. Tato událost se vyvolá, když uživatel vyplní jeden z parametrů v signatuře.

     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]

10. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> vlastnost tak, že vyvolá `CurrentParameterChanged` událost při změně hodnoty vlastnosti.

     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]

11. Přidejte metodu, která vyvolá `CurrentParameterChanged` událost.

     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]

12. Přidejte metodu, která vypočítá aktuální parametr porovnáním počtu čárek v rámci <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> s počtem čárek v signatuře.

     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]

13. Přidejte obslužnou rutinu události pro <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> událost, která volá `ComputeCurrentParameter()` metodu.

     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]

14. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> vlastnost. Tato vlastnost obsahuje objekt <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , který odpovídá rozsahu textu ve vyrovnávací paměti, na který se signatura vztahuje.

     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]

15. Implementujte další parametry.

     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]

## <a name="implement-the-signature-help-source"></a>Implementace zdroje Help Signature
 Zdroj Help signatury je sada signatur, pro které zadáte informace.

#### <a name="to-implement-the-signature-help-source"></a>Implementace zdroje Help Signature

1. Přidejte třídu s názvem `TestSignatureHelpSource` , která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> .

     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]

2. Přidejte odkaz na vyrovnávací paměť textu.

     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]

3. Přidejte konstruktor, který nastaví vyrovnávací paměť textu a poskytovatele pro identifikaci zdroje.

     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]

4. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> metodu. V tomto příkladu jsou signatury pevně kódované, ale v plné implementaci byste tyto informace získali z dokumentace jazyka.

     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]

5. Pomocná metoda `CreateSignature()` je k dispozici pouze pro ilustraci.

     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]

6. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> metodu. V tomto příkladu jsou k dispozici pouze dva signatury, z nichž každá má dva parametry. Proto se tato metoda nevyžaduje. V případě úplné implementace, ve které je k dispozici více než jeden zdroj Help signatury, se tato metoda používá k rozhodnutí, zda zdroj v nápovědě s nejvyšší prioritou může dodat shodný podpis. Pokud to nepomůže, metoda vrátí hodnotu null a zdroj s další nejvyšší prioritou se vyzve k zadání shody.

     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]

7. Implementujte `Dispose()` metodu:

     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]

## <a name="implement-the-signature-help-source-provider"></a>Implementace zprostředkovatele zdrojů pro identifikaci
 Poskytovatel zdroje pro nápovědu s podpisem zodpovídá za export součásti komponenty Managed Extensibility Framework (MEF) a pro vytvoření instance zdroje s povýšení signatur.

#### <a name="to-implement-the-signature-help-source-provider"></a>Implementace poskytovatele zdroje pro poidentifikaci

1. Přidejte třídu s názvem, `TestSignatureHelpSourceProvider` která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> , a exportujte ji pomocí typu <xref:Microsoft.VisualStudio.Utilities.NameAttribute> <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" a typu <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> před = "výchozí".

     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]

2. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> pomocí vytvoření instance `TestSignatureHelpSource` .

     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]

## <a name="implement-the-command-handler"></a>Implementace obslužné rutiny příkazu
 Podpisová zpráva je obvykle spouštěna levou závorkou "(" znakem a uzavřenou znakem pravé závorky ")". Tyto úhozy můžete zpracovat spuštěním, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> aby se spustila relace s podpisem, když obdrží otevírací znak závorky, kterému předchází známý název metody, a relace se odvolá, když obdrží znak pravé závorky.

#### <a name="to-implement-the-command-handler"></a>Implementace obslužné rutiny příkazu

1. Přidejte třídu s názvem `TestSignatureHelpCommand` , která implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]

2. Přidejte soukromá pole pro <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> adaptér (což umožňuje přidat obslužnou rutinu příkazu do řetězce obslužných rutin příkazu), textové zobrazení, signaturu, zprostředkovatele a relaci, nápovědu, a <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> Další <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]

3. Přidejte konstruktor pro inicializaci těchto polí a přidejte filtr příkazů do řetězce filtrů příkazů.

     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]

4. Implementujte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodu pro aktivaci relace Help signatury, když filtr příkazu obdrží levou závorku "(" znaku po jednom ze známých názvů metod a odvolá relaci, když obdrží pravou závorku ")", když je relace stále aktivní. V každém případě se příkaz přepošle.

     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]

5. Implementujte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu tak, aby vždy přeposlala příkaz.

     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]

## <a name="implement-the-signature-help-command-provider"></a>Implementace poskytovatele příkazů pro Help signatury
 Pomocí příkazu <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> k vytvoření instance obslužné rutiny příkazu pro vytvoření instance obslužné rutiny příkazového řádku můžete poskytnout příkaz k podpisu.

### <a name="to-implement-the-signature-help-command-provider"></a>Implementace poskytovatele příkazu help Signature

1. Přidejte třídu s názvem `TestSignatureHelpController` , která implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> a exportujte ji pomocí <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> a <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> .

     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]

2. Importujte <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (slouží k získání <xref:Microsoft.VisualStudio.Text.Editor.ITextView> objektu, s daným <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objektem), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (slouží k vyhledání aktuálního slova) a <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (pro aktivaci relace Nápověda podpisu).

     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]

3. Implementujte <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metodu vytvořením instance `TestSignatureCommandHandler` .

     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]

## <a name="build-and-test-the-code"></a>Sestavení a testování kódu
 Chcete-li otestovat tento kód, sestavte řešení SignatureHelpTest a spusťte ho v experimentální instanci.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Sestavení a testování řešení SignatureHelpTest

1. Sestavte řešení.

2. Při spuštění tohoto projektu v ladicím programu se spustí druhá instance sady Visual Studio.

3. Vytvořte textový soubor a napište nějaký text, který obsahuje slovo "Přidat" a levou závorku.

4. Po zadání levé závorky byste měli vidět popis, který zobrazí seznam dvou podpisů `add()` metody.

## <a name="see-also"></a>Viz také
- [Návod: propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
