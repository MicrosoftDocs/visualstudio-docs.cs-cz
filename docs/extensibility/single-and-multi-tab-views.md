---
title: Zobrazení na jedné a více kartách | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c308b4d6c7b90456255019ef57c6b9d544aefc77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699981"
---
# <a name="single-and-multi-tab-views"></a>Zobrazení jedné a více karet
Editor může vytvářet různé typy zobrazení. Jedním z příkladů je okno editoru kódu, jiné je návrhář formulářů.

 Zobrazení s více kartami je zobrazení, které má více karet. Například editor HTML má v dolní části dvě karty: **Návrh** a **Zdroj**, každý logický pohled. V návrhovém zobrazení se zobrazí vykreslená webová stránka, zatímco druhá zobrazí kód HTML, který tvoří webovou stránku.

## <a name="accessing-physical-views"></a>Přístup k fyzickým zobrazením
 Fyzická zobrazení objekty zobrazení dokumentu hostitele, z nichž každý představuje zobrazení dat ve vyrovnávací paměti, například kód nebo formulář. V souladu s tím má každý objekt zobrazení dokumentu fyzické zobrazení (identifikované něčím známým jako řetězec fyzického zobrazení) a obecně jeden logický pohled.

 V některých případech však může mít fyzické zobrazení dvě nebo více logických zobrazení. Některé příklady jsou editor, který má rozdělené okno s zobrazení vedle sebe, nebo návrhář formulářů, který má zobrazení GUI/návrh a zobrazení s kódem za formulářem.

 Chcete-li editoru povolit přístup ke všem dostupným fyzickým zobrazením, musíte vytvořit jedinečný řetězec fyzického zobrazení pro každý typ objektu zobrazení dokumentu, který může vytvořit továrna editoru. Například [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] editor factory můžete vytvořit objekty zobrazení dokumentu pro okno kódu a okna návrháře formulářů.

## <a name="creating-multi-tabbed-views"></a>Vytváření zobrazení s více kartami
 Přestože objekt zobrazení dokumentu musí být přidružen k fyzickému zobrazení prostřednictvím jedinečného řetězce fyzického zobrazení, můžete umístit více karet do fyzického zobrazení, abyste mohli zobrazit data různými způsoby. V této konfiguraci s více kartami jsou všechny karty přidruženy ke stejnému řetězci fyzického zobrazení, ale každé záložce je přidělen jiný identifikátor GUID logického zobrazení.

 Chcete-li vytvořit zobrazení s více kartami <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> pro editor, implementujte rozhraní<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>a přidružte ke každé kartě, kterou vytvoříte, jiný identifikátor GUID logického zobrazení ( ).

 Editor HTML sady Visual Studio je příkladem editoru se zobrazením s více kartami. Má **karty Design** a **Source.** Chcete-li to povolit, je ke `LOGICALVIEWID_TextView` každé kartě, `LOGICALVIEWID_Code` na kartě **Návrh** a pro kartu **Zdroj** přidruženo jiné logické zobrazení.

 Zadáním příslušnélogické zobrazení VSPackage přístup k zobrazení, které odpovídá určitému účelu, jako je například návrh formuláře, úpravy kódu nebo ladění kódu. Jedno z oken však musí být označeno řetězcem NULL a`LOGVIEWID_Primary`musí odpovídat primárnímu logickému zobrazení ( ).

 V následující tabulce jsou uvedeny dostupné hodnoty logického zobrazení a jejich použití.

|LOGVIEWID GUID|Doporučené použití|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|Výchozí/primární zobrazení továrny editoru.<br /><br /> Všechny továrny editoru musí podporovat tuto hodnotu. Toto zobrazení musí používat řetězec NULL jako jeho fyzický řetězec zobrazení. Na tuto hodnotu musí být nastaveno alespoň jedno logické zobrazení.|
|`LOGVIEWID_Debugging`|Zobrazení ladění. Obvykle `LOGVIEWID_Debugging` mapuje na stejné `LOGVIEWID_Code`zobrazení jako .|
|`LOGVIEWID_Code`|Zobrazení spuštěné příkazem **Zobrazit kód.**|
|`LOGVIEWID_Designer`|Zobrazení spuštěné příkazem **Zobrazit formulář.**|
|`LOGVIEWID_TextView`|Zobrazení textového editoru. Toto je zobrazení, které vrátí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, ze kterého můžete přistupovat .|
|`LOGVIEWID_UserChooseView`|Vyzve uživatele k výběru zobrazení, které chcete použít.|
|`LOGVIEWID_ProjectSpecificEditor`|Předáno dialogovým **oknem Otevřít s**<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> když uživatel zvolí položku "(Project default editor)".|

 Přestože jsou identifikátory GUID logického zobrazení rozšiřitelné, můžete použít pouze identifikátory GUID logického zobrazení definované v balíčku VSPackage.

 Při vypnutí Visual Studio zachová identifikátor GUID editoru factory a fyzické zobrazení řetězce přidružené k oknu dokumentu tak, aby jej lze použít k opětovnému otevření okna dokumentu při opětovném otevření řešení. V souboru řešení (.suo) jsou zachována pouze okna, která jsou otevřena při zavření řešení. Tyto hodnoty odpovídají `VSFPROPID_guidEditorType` `VSFPROPID_pszPhysicalView` hodnotám a `propid` předaných v parametru v metodě. <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>

## <a name="example"></a>Příklad
 Tento úryvek ukazuje, <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> jak se objekt používá pro `IVsCodeWindow`přístup k zobrazení, které implementuje . V tomto případě <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> se služba <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> používá `LOGVIEWID_TextView`k volání a požadavku , který získá ukazatel na rámec okna. Ukazatel na objekt zobrazení dokumentu se <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> získá voláním `VSFPROPID_DocView`a zadáním hodnoty . Z objektu zobrazení `QueryInterface` dokumentu `IVsCodeWindow`je volána . Očekává se v tomto případě, že textový editor je vrácena, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> a tak objekt zobrazení dokumentu vrácené v metodě je okno kódu.

```cpp
HRESULT CFindTool::GotoFileLocation(const WCHAR * szFile, long iLine, long iStart, long iLen)
{
  HRESULT hr;
  if (NULL == szFile || !*szFile)
    return E_INVALIDARG;

  if (iLine == -1L)
    return S_FALSE;

  VSITEMID                  itemid;
  VARIANT                   var;
  RECT                      rc;
  IVsUIShellOpenDocument *  pOpenDoc    = NULL;
  IVsCodeWindow *           pCodeWin    = NULL;
  IVsTextView *             pTextView   = NULL;
  IVsUIHierarchy *          pHierarchy  = NULL;
  IVsWindowFrame *          pFrame      = NULL;
  IUnknown *                pUnk        = NULL;
  IVsHighlight *            pHighlight  = NULL;

  IfFailGo(CGlobalServiceProvider::HrQueryService(SID_SVsUIShellOpenDocument, IID_IVsUIShellOpenDocument, (void **)&pOpenDoc));
  IfFailGo(pOpenDoc->OpenDocumentViaProject(szFile, LOGVIEWID_TextView, NULL, &pHierarchy, &itemid, &pFrame));
  pFrame->Show();
  VariantInit(&var);
  IfFailGo(pFrame->GetProperty(VSFPROPID_DocView, &var));
  if (VT_UNKNOWN != var.vt) { hr = E_FAIL; goto Error; }
  pUnk = V_UNKNOWN(&var);
  if (NULL != pUnk)
  {
    IfFailGo(pUnk->QueryInterface(IID_IVsCodeWindow, (void **)&pCodeWin));
    if (SUCCEEDED(hr = pCodeWin->GetLastActiveView(&pTextView)) ||
        SUCCEEDED(hr = pCodeWin->GetPrimaryView(&pTextView)) )
    {
      pTextView->SetSelection(iLine, iStart, iLine, iStart + iLen);
      // uncover selection
      IfFailGo(pTextView->QueryInterface(IID_IVsHighlight, (void**)&pHighlight));
      IfFailGo(SUCCEEDED(pHighlight->GetHighlightRect(&rc)));
      UncoverSelectionRect(&rc);
    }
  }

Error:
  CLEARINTERFACE(pHighlight);
  CLEARINTERFACE(pTextView);
  CLEARINTERFACE(pCodeWin);
  CLEARINTERFACE(pUnk);
  CLEARINTERFACE(pFrame);
  CLEARINTERFACE(pOpenDoc);
  CLEARINTERFACE(pHierarchy);
  RedrawWindow(m_hwndResults, NULL, NULL, RDW_ERASE|RDW_FRAME|RDW_INVALIDATE|RDW_ALLCHILDREN);
  return hr;
}
```

## <a name="see-also"></a>Viz také
- [Podpora více zobrazení dokumentů](../extensibility/supporting-multiple-document-views.md)
- [Postupy: Připojení zobrazení k datům dokumentů](../extensibility/how-to-attach-views-to-document-data.md)
- [Vytváření vlastních editorů a návrhářů](../extensibility/creating-custom-editors-and-designers.md)
