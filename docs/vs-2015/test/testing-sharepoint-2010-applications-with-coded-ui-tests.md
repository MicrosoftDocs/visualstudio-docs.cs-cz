---
title: Testování aplikací SharePoint 2010 pomocí programových testů uživatelského rozhraní | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 51b53778-469c-4cc9-854c-4e4992d6389b
caps.latest.revision: 32
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0ec4c0a9594202b6755500d683c426238264aec3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "82586982"
---
# <a name="testing-sharepoint-2010-applications-with-coded-ui-tests"></a>Testování aplikací pro SharePoint 2010 pomocí programových testů uživatelského rozhraní
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zahrnutí programových testů uživatelského rozhraní do aplikace SharePoint umožňuje ověřit, že celá aplikace, včetně ovládacích prvků uživatelského rozhraní, funguje správně. Programové testy UI mohou také ověřovat hodnoty a logiku v uživatelském rozhraní.

 **Požadavky**

- Visual Studio Enterprise

## <a name="what-else-should-i-know-about-coded-ui-tests"></a>Co dalšího by měl vědět o programových testech UI?
 Další informace o výhodách použití programových testů UI naleznete v tématu [použití automatizace uživatelského rozhraní k otestování kódu](../test/use-ui-automation-to-test-your-code.md) a [testování pro nepřetržité doručování pomocí sady Visual Studio 2012 – Kapitola 5 automatizace systémových testů](https://msdn.microsoft.com/library/jj159335.aspx).

 **Poznámky**

- ![Prerequsite](../test/media/prereq.png "Požadavků ohlásila") Programové testy uživatelského rozhraní pro aplikace SharePoint jsou podporovány pouze se službou SharePoint 2010.

- ![Prerequsite](../test/media/prereq.png "Požadavků ohlásila") Podpora ovládacích prvků Visio a PowerPoint 2010 v aplikaci SharePoint není podporována.

## <a name="creating-a-coded-ui-test-for-your-sharepoint-app"></a>Vytvoření programového testu uživatelského rozhraní pro aplikaci služby SharePoint
 [Vytváření programových testů uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) pro aplikace SharePoint 2010 je stejné jako vytváření testů pro jiné typy aplikací. Záznam a přehrávání jsou podporovány pro všechny ovládací prvky v rozhraní pro úpravy webu. Rozhraní pro výběr kategorií a webových částí jsou všechny standardní webové ovládací prvky.

 ![Webové části služby SharePoint](../test/media/cuit-sharepoint.png "CUIT_SharePoint")

> [!NOTE]
> Pokud zaznamenáte akci, před generováním kódu ověřte akce. Vzhledem k tomu, že existuje několik chování přidružených k ukazateli myši, je ve výchozím nastavení zapnuté. Buďte opatrní, abyste z vašich programových testů UI odebrali nadbytečné ukazatele myši. To lze provést úpravou kódu pro test nebo pomocí editoru programového [testu UI](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

## <a name="including-testing-of-office-2010-controls-within-your-sharepoint-app"></a>Včetně testování ovládacích prvků Office 2010 v rámci aplikace SharePoint
 Chcete-li povolit automatizaci některých webových částí sady Office 2010 v aplikaci SharePoint, je nutné provést některé drobné změny kódu.

> [!WARNING]
> Podpora ovládacích prvků Visio a PowerPoint 2010 není podporována.

### <a name="excel-2010-cell-controls"></a>Ovládací prvky buňky Excelu 2010
 Chcete-li zahrnout ovládací prvky buňky aplikace Excel, je nutné provést některé změny v kódu kódovaného testu uživatelského rozhraní.

> [!WARNING]
> Zadání textu v libovolné buňce aplikace Excel, za kterým následuje akce se šipkou klávesou, není správně zaznamenáváno. Buňky můžete vybrat pomocí myši.

 Pokud zaznamenáváte akce do prázdné buňky, je nutné upravit kód dvojitým kliknutím na buňku a následným prováděním operace set text. To je potřeba, protože kliknutím na buňku, za kterou se aktivuje jakákoli akce klávesnice, aktivuje `textarea` v rámci buňky. Pouhým záznamem `setvalue` v prázdné buňce bude hledání, které není k `editbox` dispozici, dokud nekliknete na buňku. Příklad:

```csharp
Mouse.DoubliClick(uiItemCell,new Point(31,14));
uiGridKeyboardInputEdit.Text=value;
```

 Pokud provádíte zaznamenávání akcí na neprázdné buňce, znamená to, že nahrávání bude trochu složitější, protože okamžik, kdy do buňky přidáte text, \<div> je nový ovládací prvek přidán jako podřízený objekt buňky. Nový \<div> ovládací prvek obsahuje text, který jste právě zadali. Zapisovač musí zaznamenávat akce na novém \<div> ovládacím prvku, ale nelze jej, protože nový \<div> ovládací prvek neexistuje, dokud není test zadán. Chcete-li tento problém vyřešit, je nutné ručně provést následující změny kódu.

1. Přejít k inicializaci buňky a nastavit `RowIndex` a `ColumnIndex` primární vlastnosti:

    ```csharp
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";
    ```

2. Najděte `HtmlDiv` podřízenou buňku:

    ```csharp
    private UITestControl getControlToDoubleClick(HtmlCell cell)
    {
         if (String.IsNullOrEmpty(cell.InnerText)) return cell;
         HtmlDiv pane = new HtmlDiv(cell);
         pane.FilterProperties[HtmlDiv.PropertyNames.InnerText] = cell.InnerText;
         // Class is an important property in finding pane
         pane.FilterProperties[HtmlDiv.PropertyNames.Class] = "cv-nwr";
         UITestControlCollection panes = pane.FindMatchingControls();
         return panes[0];
    }

    ```

3. Přidejte kód pro akci dvojitého kliknutí myši na `HtmlDiv` :

    ```csharp
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )
    ```

4. Přidejte kód pro nastavení textu `TextArea` :

    ```csharp
    uIGridKeyboardInputEdit.Text = value; }
    ```

## <a name="enabling-coded-ui-testing-of-silverlight-web-parts-in-your-sharepoint-2010-app"></a>Povolení programového testování uživatelského rozhraní pro webové části Silverlight v aplikaci SharePoint 2010
 Testování Silverlight není v aplikaci Visual Studio 2012 a novějších podporováno. Pokud ale chcete testovat webové části Silverlight v aplikaci SharePoint 2010, můžete nainstalovat samostatný modul plug-in Silverlight z galerie sady Visual Studio.

#### <a name="setting-up-your-machine"></a>Nastavení počítače

1. Ujistěte se, že máte nainstalovanou aplikaci Visual Studio 2012,1 nebo novější.

2. Nainstalujte [modul plug-in test uživatelského rozhraní Microsoft Visual Studio pro Silverlight](https://marketplace.visualstudio.com/items?itemName=PrachiBoraMSFT.MicrosoftVisualStudioUITestPluginforSilverlight).

3. Nainstalujte [Fiddler](http://www.fiddler2.com/fiddler2/). Toto je jednoduše nástroj, který zachycuje a protokoluje přenosy HTTP.

4. Stáhněte si [projekt fiddlerXap](https://40jajy3iyl373v772m19fybm-wpengine.netdna-ssl.com/wp-content/uploads/sites/6/2019/02/FiddlerXapProxy.zip). Rozbalte ji, sestavte ji a spusťte skript "CopySLHelper.bat" pro instalaci pomocné knihovny DLL, která je požadována k testování webových částí technologie Silverlight při použití nástroje Fiddler Tool.

   Po nastavení počítače začněte testovat aplikaci SharePoint 2010 s webovými částmi technologie Silverlight, a to pomocí následujících kroků:

#### <a name="testing-silverlight-web-parts"></a>Testování webových částí technologie Silverlight

1. Spusťte aplikaci Fiddler.

2. Vymažte mezipaměť prohlížeče. To je nezbytné proto, že soubor XAP, který obsahuje pomocnou knihovnu DLL pro automatizaci uživatelského rozhraní Silverlight, je obvykle uložen v mezipaměti. Musíme zajistit, aby byl upravený soubor XAP vyzvednutý, a proto vymažeme mezipaměť prohlížeče.

3. Otevřete webovou stránku.

4. Spusťte zapisovač a vygenerujte kód jako při běžném testování webových aplikací.

5. Měli byste ověřit, že generovaný kód odkazuje na Microsoft.VisualStudio.TestTools.UITest.Extension.Silverlight.dll.

     Další informace najdete v tématu [testování uživatelského rozhraní SharePoint 2010 se sadou Visual Studio 2012](https://devblogs.microsoft.com/devops/ui-testing-sharepoint-2010-with-visual-studio-2012/) .

## <a name="external-resources"></a>Externí zdroje

### <a name="blogs"></a>Blogy
 [Testování uživatelského rozhraní SharePoint 2010 se sadou Visual Studio 2012](https://devblogs.microsoft.com/devops/ui-testing-sharepoint-2010-with-visual-studio-2012/)

 [Porozumění logice hledání pro ovládací prvky Silverlight v programovém testu uživatelského rozhraní](https://tapas-techsnips.blogspot.com/)

 [Načítají se vlastnosti ovládacího prvku Silverlight.](https://tapas-techsnips.blogspot.com/)

 [Index obsahu pro programový test uživatelského rozhraní](https://blogs.msdn.microsoft.com/mathew_aniyan/2013/02/18/content-index-for-coded-ui-test/)

### <a name="guidance"></a>Doprovodné materiály
 [Testování pro průběžné doručování pomocí sady Visual Studio 2012 – Kapitola 5 automatizace systémových testů](https://msdn.microsoft.com/library/jj159335.aspx)

### <a name="forum"></a>Fórum
 [Blog sady Visual Studio ALM + Team Foundation Server](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)

## <a name="see-also"></a>Viz také
 [Použití automatizace uživatelského rozhraní k otestování](../test/use-ui-automation-to-test-your-code.md) [výkonu webu kódu a zátěžového testování aplikací sharepoint 2010 a 2013](https://msdn.microsoft.com/library/20c2e469-0e4e-4296-a739-c0e8fff36e54) [vytvoření řešení SharePoint](https://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631) [ověřování a ladění vytváření a ladění kódu SharePointu](https://msdn.microsoft.com/library/b5f3bce2-6a51-41b1-a292-9e384bae420c) [Building and Debugging SharePoint Solutions](https://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae) [profilace výkonu aplikací SharePoint](https://msdn.microsoft.com/library/61ae02e7-3f37-4230-bae1-54a498c2fae8)
