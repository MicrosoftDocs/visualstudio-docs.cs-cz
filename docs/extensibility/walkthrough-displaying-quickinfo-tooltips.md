---
title: 'Návod: zobrazení QuickInfoch popisků | Microsoft Docs'
description: Přečtěte si, jak zobrazit QuickInfo pro textový obsah pomocí tohoto návodu. QuickInfo zobrazí signatury a popisy metod pro název metody.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: d374aa41d85b1d64b6623cb99f6183787a2afc53
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217252"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>Návod: zobrazení QuickInfoch popisků
QuickInfo je funkce technologie IntelliSense, která zobrazuje signatury a popisy metod, když uživatel přesune ukazatel myši na název metody. Můžete implementovat funkce založené na jazyce, jako je například QuickInfo, definováním identifikátorů, pro které chcete zadat QuickInfo popisy, a následným vytvořením popisu, ve kterém chcete zobrazit obsah. QuickInfo můžete definovat v kontextu jazykové služby nebo můžete definovat vlastní příponu názvu souboru a typ obsahu a zobrazit QuickInfo pouze pro tento typ, nebo můžete zobrazit QuickInfo pro existující typ obsahu (například "text"). Tento návod ukazuje, jak zobrazit QuickInfo pro typ obsahu "text".

 Příklad QuickInfo v tomto návodu zobrazuje popisy tlačítek, když uživatel přesune ukazatel myši na název metody. Tento návrh vyžaduje, abyste implementovali tato čtyři rozhraní:

- zdrojové rozhraní

- rozhraní poskytovatele zdroje

- rozhraní kontroleru

- rozhraní poskytovatele kontroleru

  Zprostředkovatelé zdrojového kódu a řadiče jsou Managed Extensibility Framework (MEF) částí komponenty a jsou odpovědni za exportování tříd source a Controller a k importu služeb a zprostředkovatelů, jako je <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> , což vytvoří textovou vyrovnávací paměť popisku a <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> spustí relaci QuickInfo.

  V tomto příkladu používá zdroj QuickInfo pevně zakódovaný seznam názvů a popisů metod, ale v úplných implementacích je za poskytnutí tohoto obsahu zodpovědný jazyková služba a jazyková dokumentace.

## <a name="prerequisites"></a>Požadavky
 Od sady Visual Studio 2015 není nutné instalovat sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Vytvořit projekt MEF

### <a name="to-create-a-mef-project"></a>Vytvoření projektu MEF

1. Vytvoří projekt VSIX v jazyce C#. (V dialogovém okně **Nový projekt** vyberte **Visual C#/rozšiřitelnost** a potom **projekt VSIX**.) Pojmenujte řešení `QuickInfoTest` .

2. Přidejte do projektu šablonu položky klasifikátoru editoru. Další informace naleznete v tématu [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Odstraňte existující soubory třídy.

## <a name="implement-the-quickinfo-source"></a>Implementace zdroje QuickInfo
 Zdroj QuickInfo zodpovídá za shromáždění sady identifikátorů a jejich popisů a přidání obsahu do textové vyrovnávací paměti popisku, pokud je zjištěn jeden z identifikátorů. V tomto příkladu se identifikátory a jejich popisy přidávají pouze do zdrojového konstruktoru.

#### <a name="to-implement-the-quickinfo-source"></a>Implementace zdroje QuickInfo

1. Přidejte soubor třídy a pojmenujte ho `TestQuickInfoSource` .

2. Přidejte odkaz na *Microsoft. VisualStudio. Language. IntelliSense*.

3. Přidejte následující importy.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet1":::

4. Deklarujte třídu, která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> , a pojmenujte ji `TestQuickInfoSource` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet2":::

5. Přidejte pole pro poskytovatele zdroje QuickInfo, vyrovnávací paměť textu a sadu názvů metod a signatur metod. V tomto příkladu jsou názvy metod a signatury inicializovány v `TestQuickInfoSource` konstruktoru.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet3":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet3":::

6. Přidejte konstruktor, který nastaví poskytovatele zdroje QuickInfo a textové vyrovnávací paměti, a naplní sadu názvů metod a signatury a popisy metod.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet4":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet4":::

7. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> metodu. V tomto příkladu metoda najde aktuální slovo nebo předchozí slovo, pokud se ukazatel myši nachází na konci řádku nebo v textové vyrovnávací paměti. Pokud je slovo jedním z názvů metod, popis tohoto názvu metody se přidá do obsahu QuickInfo.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet5":::

8. Je také nutné implementovat metodu Dispose (), protože <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementuje <xref:System.IDisposable> :

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet6":::

## <a name="implement-a-quickinfo-source-provider"></a>Implementace poskytovatele zdroje QuickInfo
 Poskytovatel zdroje QuickInfo slouží primárně pro export sebe sama jako součást MEF a vytvoření instance zdroje QuickInfo. Vzhledem k tomu, že se jedná o součást MEF, může importovat jiné části komponenty MEF.

#### <a name="to-implement-a-quickinfo-source-provider"></a>Implementace poskytovatele zdroje QuickInfo

1. Deklarujte poskytovatele zdroje QuickInfo s názvem `TestQuickInfoSourceProvider` , který implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider> , a exportujte ho s <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ToolTip QuickInfo source", a <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> před = "default" a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text".

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet7":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet7":::

2. Importujte dvě služby editoru <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> a <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> jako vlastnosti `TestQuickInfoSourceProvider` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet8":::

3. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> pro vrácení nového `TestQuickInfoSource` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet9":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet9":::

## <a name="implement-a-quickinfo-controller"></a>Implementace kontroleru QuickInfo
 QuickInfo řadiče určují, kdy se zobrazí QuickInfo. V tomto příkladu se QuickInfo zobrazí, když je ukazatel na slovo, které odpovídá jednomu z názvů metod. Kontroler QuickInfo implementuje obslužnou rutinu události při přechodu myší, která spustí relaci QuickInfo.

### <a name="to-implement-a-quickinfo-controller"></a>Implementace kontroleru QuickInfo

1. Deklarujte třídu, která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> , a pojmenujte ji `TestQuickInfoController` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet10":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet10":::

2. Přidejte soukromá pole pro textové zobrazení, textové vyrovnávací paměti reprezentované v zobrazení text, v relaci QuickInfo a ve zprostředkovateli QuickInfo Controller.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet11":::

3. Přidejte konstruktor, který nastaví pole a přidá obslužnou rutinu události při přechodu myší.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet12":::

4. Přidejte obslužnou rutinu události při přechodu myší, která spustí relaci QuickInfo.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet13":::

5. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> metodu tak, aby odebrala obslužnou rutinu události při přechodu myší, když je kontroler odpojen z textového zobrazení.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet14":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet14":::

6. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> metodu a <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> metodu jako prázdné metody pro tento příklad.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet15":::

## <a name="implementing-the-quickinfo-controller-provider"></a>Implementace poskytovatele kontroleru QuickInfo
 Poskytovatel řadiče QuickInfo slouží primárně pro export sebe sama jako součást MEF a vytvoření instance řadiče QuickInfo. Vzhledem k tomu, že se jedná o součást MEF, může importovat jiné části komponenty MEF.

### <a name="to-implement-the-quickinfo-controller-provider"></a>Implementace poskytovatele kontroleru QuickInfo

1. Deklarujte třídu s názvem `TestQuickInfoControllerProvider` , která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider> , a exportujte ji pomocí <xref:Microsoft.VisualStudio.Utilities.NameAttribute> příkazu "ToolTip QuickInfo Controller" a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text":

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet16":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet16":::

2. Importujte <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> jako vlastnost.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet17":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet17":::

3. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> metodu vytvořením instance kontroleru QuickInfo.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet18":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet18":::

## <a name="build-and-test-the-code"></a>Sestavení a testování kódu
 Chcete-li otestovat tento kód, sestavte řešení QuickInfoTest a spusťte ho v experimentální instanci.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>Sestavení a testování řešení QuickInfoTest

1. Sestavte řešení.

2. Při spuštění tohoto projektu v ladicím programu se spustí druhá instance sady Visual Studio.

3. Vytvořte textový soubor a zadejte nějaký text, který obsahuje slova "Add" a "odečíst".

4. Přesuňte ukazatel myši na jeden z výskytů "Přidat". Měl by se zobrazit signatura a popis `add` metody.

## <a name="see-also"></a>Viz také
- [Návod: propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
