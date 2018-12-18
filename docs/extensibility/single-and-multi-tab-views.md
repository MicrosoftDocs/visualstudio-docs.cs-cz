---
title: Zobrazení jeden a více karta | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 23feeaee14e6a149ad385c9f5e4a0c4b41be1e86
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142972"
---
# <a name="single-and-multi-tab-views"></a>Zobrazení jeden a více karta
Editor můžete vytvořit různé typy zobrazení. Jedním z příkladů je okno editoru kódu, jiné je Návrhář formulářů.  
  
 Zobrazení více kartami je zobrazení, které obsahuje několik karet. Například HTML editor obsahuje dvě karty v dolní části: **návrhu** a **zdroj**, každý logickém zobrazení. Zobrazení návrhu zobrazení vykreslené webové stránky, při dalších zobrazí HTML, který zahrnuje webové stránky.  
  
## <a name="accessing-physical-views"></a>Přístup k fyzické zobrazení  
 Zobrazení fyzického hostitele objekty zobrazení dokumentu, každý představující zobrazení data ve vyrovnávací paměti, jako je například kód nebo formulář. Každý objekt zobrazení dokumentu odpovídajícím způsobem, má fyzické zobrazení (identifikovaný něco známé jako řetězec fyzické zobrazení) a obecně jednoho logického zobrazení.  
  
 V některých případech ale fyzické zobrazení může mít dva nebo více logických zobrazení. Některé příklady jsou editor, který má rozděleném okně s zobrazení vedle sebe nebo Návrhář formulářů, který má grafické uživatelské rozhraní a návrhu zobrazení a zobrazení kódu na pozadí the tvaru.  
  
 Pokud chcete povolit jako editor pro přístup k veškerému dostupné fyzické zobrazení, je nutné vytvořit řetězec jedinečný fyzické zobrazení pro každý typ objektu zobrazení dokumentu, který můžete vytvořit vaše objekt factory editoru. Například [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] objekt factory editoru můžete vytvořit dokument zobrazit objekty pro okno kódu a okno Návrhář formulářů.  
  
## <a name="creating-multi-tabbed-views"></a>Vytváření zobrazení více kartami  
 Přestože objekt zobrazení dokumentu musí být přidružený fyzické zobrazení pomocí řetězce jedinečný fyzické zobrazení, můžete umístit několik karet v rámci fyzické zobrazení povolíte zobrazení dat různými způsoby. V této konfiguraci více kartami všechny karty jsou přidružena do jednoho fyzického zobrazení řetězce, ale každé kartě dostane jiné logické zobrazení identifikátor GUID.  
  
 Vytvoření zobrazení více kartami pro editor, implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> rozhraní a pak přidružit jiné logické zobrazení GUID (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) s každé kartě vytvoříte.  
  
 Editor Visual Studio HTML je příkladem editoru s více kartě zobrazení. Má **návrhu** a **zdroj** karty. Chcete-li povolit, je přidružen každé kartě jiné logické zobrazení `LOGICALVIEWID_TextView` pro **návrhu** kartě a `LOGICALVIEWID_Code` pro **zdroj** kartě.  
  
 Zadáním příslušné logické zobrazení můžete VSPackage přístup k zobrazení, která odpovídá určitý účel, například návrhu formuláře, úpravy kódu nebo ladění kódu. Ale některé z oken, musí být identifikovaný řetězec s hodnotou NULL a to musí odpovídat primární logickém zobrazení (`LOGVIEWID_Primary`).  
  
 Následující tabulka uvádí zobrazení k dispozici logické hodnoty a jejich použití.  
  
|IDENTIFIKÁTOR GUID LOGVIEWID|Doporučené použití|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|Výchozí/primární zobrazení objekt factory editoru.<br /><br /> Tato hodnota musí podporovat všechny objekty Factory editoru. Toto zobrazení musí používat jako jeho fyzické zobrazení řetězce řetězec s hodnotou NULL. Tato hodnota musí být nastavena alespoň jedno logické zobrazení.|  
|`LOGVIEWID_Debugging`|Ladění v zobrazení. Obvykle `LOGVIEWID_Debugging` se mapuje na stejné zobrazení jako `LOGVIEWID_Code`.|  
|`LOGVIEWID_Code`|Zobrazení spuštěn **kód zobrazení** příkaz.|  
|`LOGVIEWID_Designer`|Zobrazení spuštěn **zobrazit formulář** příkaz.|  
|`LOGVIEWID_TextView`|Zobrazení, textový editor. Jedná se o zobrazení, která vrací <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>, ze které je přístupné <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|`LOGVIEWID_UserChooseView`|Vyzývá uživatele k zvolit, které zobrazení použít.|  
|`LOGVIEWID_ProjectSpecificEditor`|Předaná **otevřít v** dialogovém okně<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> Když uživatel vybere položka "(výchozí editor projektu)".|  
  
 I když jsou extensible logickém zobrazení identifikátory GUID, můžete použít pouze identifikátory GUID logickém zobrazení definované v vaší VSPackage.  
  
 Visual Studio na vypnutí, zachová identifikátor GUID objekt factory editoru a řetězců fyzické zobrazení související s okna dokumentu, aby ho bylo možné použít znovu otevřete dokument windows při řešení je znovu otevřít. Pouze systému windows, které jsou otevřené při zavření řešení jsou nastavené jako trvalé soubor řešení (.suo). Tyto hodnoty odpovídají `VSFPROPID_guidEditorType` a `VSFPROPID_pszPhysicalView` hodnoty předané `propid` parametr ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metoda.  
  
## <a name="example"></a>Příklad  
 Tento fragment kódu ukazuje, jak <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> objekt se používá k přístupu k zobrazení, který implementuje `IVsCodeWindow`. V takovém případě <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> služby se používá k volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> a žádosti o `LOGVIEWID_TextView`, který získá ukazatel na rámec okna. Ukazatel na objekt zobrazení dokumentu se získá voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> a zadáte třeba hodnotu `VSFPROPID_DocView`. Z objektu zobrazení dokumentu `QueryInterface` je volána pro `IVsCodeWindow`. Očekávání v tomto případě je, že je vrácen textovém editoru a proto vrácený objekt zobrazení dokumentu v <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metoda je okno kódu.  
  
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
 [Podpora více zobrazení dokumentu](../extensibility/supporting-multiple-document-views.md)   
 [Postupy: zobrazení dokumentů datové připojení](../extensibility/how-to-attach-views-to-document-data.md)   
 [Vytváření vlastních editorů a návrhářů](../extensibility/creating-custom-editors-and-designers.md)