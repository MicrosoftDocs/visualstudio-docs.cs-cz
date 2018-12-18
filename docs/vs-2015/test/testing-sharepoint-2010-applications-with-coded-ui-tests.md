---
title: Testování aplikací pro SharePoint 2010 pomocí programových testů uživatelského rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51b53778-469c-4cc9-854c-4e4992d6389b
caps.latest.revision: 32
ms.author: gewarren
manager: douge
ms.openlocfilehash: e450cd333c01e4e2e557013ef106337fe5a80a71
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937275"
---
# <a name="testing-sharepoint-2010-applications-with-coded-ui-tests"></a>Testování aplikací pro SharePoint 2010 pomocí programových testů uživatelského rozhraní
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zahrnutí programových testů UI v aplikaci SharePoint slouží k ověření, že celá aplikace včetně jeho ovládacích prvků uživatelského rozhraní pracuje správně. Programové testy uživatelského rozhraní můžete také ověřit, hodnoty a logiku v uživatelském rozhraní.  
  
 **Požadavky**  
  
-   Visual Studio Enterprise  
  
## <a name="what-else-should-i-know-about-coded-ui-tests"></a>Co dalšího byste vědět o programové testy UI?  
 Další informace o výhodách používání programové testy UI, naleznete v tématu [pomocí uživatelského rozhraní automatizace k testu kódu](../test/use-ui-automation-to-test-your-code.md) a [testování pro nepřetržité dodávky s Visual Studio 2012 – kapitola 5 automatizace systémových testů](http://go.microsoft.com/fwlink/?LinkID=255196).  
  
 **Poznámky**  
  
-   ![Prerequsite](../test/media/prereq.png "požadavky") programové testy uživatelského rozhraní pro aplikace SharePoint jsou podporovány pouze s SharePoint 2010.  
  
-   ![Prerequsite](../test/media/prereq.png "požadavky") není dostupná podpora pro ovládací prvky v aplikaci SharePoint Visio a PowerPoint 2010.  
  
## <a name="creating-a-coded-ui-test-for-your-sharepoint-app"></a>Vytvoření programového testu UI pro aplikace SharePoint  
 [Vytvoření programové testy UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) pro aplikace SharePoint 2010 je stejný jako vytváření testů pro ostatní typy aplikací. Záznam a přehrávání se podporuje pro všechny ovládací prvky na rozhraní webových úprav. Rozhraní pro výběr kategorie a webové části jsou všechny standardní webové ovládací prvky.  
  
 ![Webové části služby SharePoint](../test/media/cuit-sharepoint.png "CUIT_SharePoint")  
  
> [!NOTE]
>  Pokud záznam akce ověření akce před vygenerováním kódu. Vzhledem k tomu, že existují různé chování spojené s myší najedete, je ve výchozím nastavení. Nezapomeňte odebrat redundantní ukazatele z programových testů uživatelského rozhraní. Provedete to tak, že upravíte kód testu, nebo pomocí [editoru programového testu UI](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
## <a name="including-testing-of-office-2010-controls-within-your-sharepoint-app"></a>Včetně testování Office 2010 ovládací prvky v rámci vaší aplikace SharePoint  
 Jak povolit automatizaci pro některé webové části do aplikaci Sharepointu office 2010, budete muset provést některé změny drobné úpravy v kódu.  
  
> [!WARNING]
>  Podpora pro ovládací prvky aplikace Visio a PowerPoint 2010 se nepodporuje.  
  
### <a name="excel-2010-cell-controls"></a>Ovládací prvky aplikace Excel 2010 buňky  
 Zahrnout ovládací prvky Excelu buňky, je třeba provést některé změny v kódu programového testu uživatelského rozhraní.  
  
> [!WARNING]
>  Zadávání textu v libovolnou buňku aplikace Excel, za nímž následuje klíče akci šipku, nezaznamenává správně. Vyberte buňky pomocí myši.  
  
 Záznamu akce na prázdnou buňku, je třeba upravit kód, double klikněte na buňku a následnému provedením operace text nastavení. To je potřeba proto klikněte na buňku, následované žádnou akci klávesnice aktivuje `textarea` v buňce. Jednoduše záznam `setvalue` na prázdnou buňku by vyhledejte `editbox` která není k dispozici, dokud se kliklo na buňku. Příklad:  
  
```csharp  
Mouse.DoubliClick(uiItemCell,new Point(31,14));  
uiGridKeyboardInputEdit.Text=value;  
```  
  
 Pokud se nahrávání akcí na prázdné buňky, pak záznam získá o něco složitější, protože v okamžiku, přidejte text do buňky, nový \<div > ovládací prvek je přidán jako podřízený objekt buňky. Nové \<div > ovládací prvek obsahuje text, který jste právě zadali. Záznam je potřeba zaznamenat akce na novém \<div > ovládací prvek; ale není toho schopen, protože nový \<div > ovládací prvek neexistuje až po zadání testu. Musíte ručně provést následující změny kódu tak, aby vyhovovaly tento problém.  
  
1.  Přejděte do buňky inicializace a ujistěte se, `RowIndex` a `ColumnIndex` primární vlastnosti:  
  
    ```csharp  
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";   
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";  
    ```  
  
2.  Najít `HtmlDiv` podřízené buňky:  
  
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
  
3.  Přidejte kód pro myši dvakrát klikněte na akci na `HtmlDiv`:  
  
    ```csharp  
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )  
    ```  
  
4.  Přidejte kód pro nastavení na text `TextArea`:  
  
    ```csharp  
    uIGridKeyboardInputEdit.Text = value; }  
    ```  
  
## <a name="enabling-coded-ui-testing-of-silverlight-web-parts-in-your-sharepoint-2010-app"></a>Povolení programového testování uživatelského rozhraní pro webové části Silverlight v aplikaci SharePoint 2010  
 Testování Silverlight se nepodporuje v sadě Visual Studio 2012 a novější. Ale pokud chcete testovat webové části Silverlight v aplikaci SharePoint 2010, můžete nainstalovat samostatný modul plug-in aplikace Silverlight z Galerie sady Visual Studio.  
  
#### <a name="setting-up-your-machine"></a>Nastavení vašeho počítače  
  
1. Ujistěte se, že máte Visual Studio 2012.1 nebo novější.  
  
2. Nainstalujte [modul plug-in pro Microsoft Visual Studio uživatelského rozhraní testu pro Silverlight](http://visualstudiogallery.msdn.microsoft.com/28312a61-9451-451a-990c-c9929b751eb4).  
  
3. Nainstalujte [Fiddler](http://www.fiddler2.com/fiddler2/). Toto je jednoduše nástroj, který zachytí a protokoly přenos pomocí protokolu HTTP.  
  
4. Stáhněte si [fiddlerXap projektu](http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-components-postattachments/00-10-36-48-70/FiddlerXapProxy.zip). Ji rozbalte, sestavte ho a spusťte skript "CopySLHelper.bat" instalace pomocné rutiny knihovny DLL, která se vyžaduje k testování webové části Silverlight, když použijete nástroj Fiddler.  
  
   Po nastavení vašeho počítače ke spuštění testování vaší aplikace SharePoint 2010 pomocí webové části Silverlight, postupujte podle těchto kroků:  
  
#### <a name="testing-silverlight-web-parts"></a>Testování webové části Silverlight  
  
1.  Spusťte aplikaci Fiddler.  
  
2.  Vymažte mezipaměť prohlížeče. To je nezbytné, protože soubor XAP, který obsahuje DLL pomocné rutiny automatizace uživatelského rozhraní Silverlight, je obvykle ukládají do mezipaměti. Máme, abyste měli jistotu, že se vybere upravený soubor XAP, proto jsme vymazat mezipaměť prohlížeče.  
  
3.  Otevřete webovou stránku.  
  
4.  Spuštěním záznamu a generování kódu, jako byste to udělali pro běžný webový testování aplikací.  
  
5.  By měl potvrďte, že generovaný kód odkazuje Microsoft.VisualStudio.TestTools.UITest.Extension.Silverlight.dll.  
  
     Další informace najdete v tématu [uživatelského rozhraní testování SharePoint 2010 v sadě Visual Studio 2012](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx)  
  
## <a name="external-resources"></a>Externí zdroje  
  
### <a name="blogs"></a>Blogy  
 [SharePoint 2010 pomocí sady Visual Studio 2012 testování uživatelského rozhraní](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx)  
  
 [Principy logika vyhledávání pro ovládací prvky Silverlight v programový Test uživatelského rozhraní](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/understanding-the-search-logic-for-silverlight-controls-in-coded-ui-test.aspx)  
  
 [Načítají se vlastnosti ovládacího prvku programu Silverlight](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/fetching-property-of-a-silverlight-control.aspx)  
  
 [Index obsahu pro programový Test uživatelského rozhraní](http://blogs.msdn.com/b/mathew_aniyan/archive/2010/02/11/content-index-for-coded-ui-test.aspx)  
  
### <a name="guidance"></a>Doprovodné materiály  
 [Testování pro nepřetržité dodávky s Visual Studio 2012 – kapitola 5 automatizace systémových testů](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### <a name="forum"></a>Fórum  
 [Visual Studio ALM + Team Foundation Server Blog](http://go.microsoft.com/fwlink/?LinkID=254496)  
  
## <a name="see-also"></a>Viz také  
 [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)   
 [Testování výkonnosti webů a zátěžové testování aplikací SharePoint 2010 a 2013](http://msdn.microsoft.com/library/20c2e469-0e4e-4296-a739-c0e8fff36e54)   
 [Vytvoření řešení služby SharePoint](http://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631)   
 [Zobrazení a ladění kódu pro SharePoint](http://msdn.microsoft.com/library/b5f3bce2-6a51-41b1-a292-9e384bae420c)   
 [Sestavování a ladění řešení služby SharePoint](http://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae)   
 [Profilace výkonu aplikací služby SharePoint](http://msdn.microsoft.com/library/61ae02e7-3f37-4230-bae1-54a498c2fae8)



