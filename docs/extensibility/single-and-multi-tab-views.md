---
title: Zobrazení s jedním a více kartami | Microsoft Docs
description: Naučte se implementovat zobrazení na více kartách v editorech, jako jsou například okna editoru kódu a Návrhář formulářů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7c23693b5ae622912695c139714c7e818ed0e868
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056321"
---
# <a name="single-and-multi-tab-views"></a>Zobrazení jedné a více karet
Editor může vytvářet různé typy zobrazení. Jedním z příkladů je okno editoru kódu, další je Návrhář formulářů.

 Zobrazení s více kartami je zobrazení, které obsahuje několik karet. Například editor HTML má dvě karty dole: **design** a **source**, každé logické zobrazení. V zobrazení Návrh se zobrazí vykreslená webová stránka, zatímco druhá zobrazí kód HTML, který se skládá z webové stránky.

## <a name="accessing-physical-views"></a>Přístup k fyzickým zobrazením
 Fyzická zobrazení hostují objekty zobrazení dokumentu, z nichž každý představuje zobrazení dat ve vyrovnávací paměti, jako je například kód nebo formulář. Proto každý objekt zobrazení dokumentu má fyzické zobrazení (identifikované něčím jako řetězec fyzického zobrazení) a obecně jediné logické zobrazení.

 V některých případech může ale fyzické zobrazení obsahovat dvě nebo více logických zobrazení. Příkladem může být Editor, který má rozdělené okno s souběžnými zobrazeními, nebo Návrhář formulářů, který má grafické rozhraní nebo návrhové zobrazení a kód na pozadí.

 Chcete-li povolit editoru přístup ke všem dostupným fyzickým zobrazením, je nutné vytvořit jedinečný řetězec fyzického zobrazení pro každý typ objektu zobrazení dokumentu, který může objekt pro vytváření editoru vytvořit. Například objekt [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] pro vytváření editoru může vytvořit objekty zobrazení dokumentu pro okno kódu a okno návrháře formulářů.

## <a name="creating-multi-tabbed-views"></a>Vytváření zobrazení s více kartami
 Přestože objekt zobrazení dokumentu musí být přidružen k fyzickému zobrazení prostřednictvím jedinečného řetězce fyzického zobrazení, můžete umístit více karet v rámci fyzického zobrazení, aby bylo možné zobrazit data různými způsoby. V této konfiguraci s více kartami jsou všechny karty přidruženy ke stejnému fyzickému řetězci zobrazení, ale na každé kartě je uveden jiný identifikátor GUID logického zobrazení.

 Chcete-li vytvořit zobrazení s více kartami pro Editor, implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> rozhraní a pak přidružte jiný identifikátor GUID logického zobrazení ( <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID> ) pomocí každé karty, kterou vytvoříte.

 Editor HTML sady Visual Studio je příkladem editoru s zobrazením více karet. Má karty **design** a **source** . Chcete-li tuto možnost povolit, je pro každou kartu přidruženo jiné logické zobrazení, a to na `LOGICALVIEWID_TextView` kartě **Návrh** a na `LOGICALVIEWID_Code` kartě **zdroj** .

 Zadáním vhodného logického zobrazení může VSPackage získat přístup k zobrazení, které odpovídá konkrétnímu účelu, jako je například navrhování formuláře, úpravy kódu nebo ladění kódu. Jeden z oken však musí být identifikován řetězcem NULL a musí odpovídat primárnímu logickému zobrazení ( `LOGVIEWID_Primary` ).

 V následující tabulce jsou uvedeny dostupné hodnoty logického zobrazení a jejich použití.

|LOGVIEWID GUID|Doporučené použití|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|Výchozí/primární zobrazení objektu pro vytváření editoru<br /><br /> Všechny továrny editoru musí tuto hodnotu podporovat. Toto zobrazení musí jako řetězec fyzického zobrazení používat řetězec s hodnotou NULL. Aspoň jedno logické zobrazení musí být nastavené na tuto hodnotu.|
|`LOGVIEWID_Debugging`|Zobrazení ladění. Obvykle se `LOGVIEWID_Debugging` mapuje ke stejnému zobrazení jako `LOGVIEWID_Code` .|
|`LOGVIEWID_Code`|Zobrazení spouštěné příkazem **Zobrazit kód**|
|`LOGVIEWID_Designer`|Zobrazení spouštěné příkazem **formuláře zobrazení**|
|`LOGVIEWID_TextView`|Textový editor – zobrazení Toto zobrazení vrátí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> , ze kterého můžete získat přístup <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|
|`LOGVIEWID_UserChooseView`|Vyzve uživatele k výběru zobrazení, které se má použít.|
|`LOGVIEWID_ProjectSpecificEditor`|Předáno dialogovým oknem **otevřít v** pro<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> Když uživatel zvolí položku "(výchozí editor projektu)".|

 I když jsou identifikátory GUID logického zobrazení rozšiřitelné, můžete použít jenom identifikátory GUID logického zobrazení definované v VSPackage.

 Při vypnutí aplikace Visual Studio zachová GUID objektu pro vytváření editoru a fyzických zobrazení řetězců přidružených k oknu dokumentu, aby jej bylo možné použít k opětovnému otevření oken dokumentů při opětovném otevření řešení. V souboru řešení (. suo) jsou trvalé pouze okna, která jsou otevřena při zavření řešení. Tyto hodnoty odpovídají `VSFPROPID_guidEditorType` `VSFPROPID_pszPhysicalView` hodnotám a předaným v `propid` parametru v <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodě.

## <a name="example"></a>Příklad
 Tento fragment kódu ukazuje, jak <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> se objekt používá pro přístup k zobrazení, které implementuje `IVsCodeWindow` . V tomto případě se <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> služba používá k volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> a vyžádání `LOGVIEWID_TextView` , který získá ukazatel na rámec okna. Ukazatel na objekt zobrazení dokumentu je získán voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> a zadáním hodnoty `VSFPROPID_DocView` . Z objektu zobrazení dokumentu `QueryInterface` je volána pro `IVsCodeWindow` . Očekává se, že v tomto případě se vrátí textový editor, takže objekt zobrazení dokumentu vrácený v <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodě je okno kódu.

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
