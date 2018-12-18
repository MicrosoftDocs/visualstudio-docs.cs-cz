---
title: Zobrazení jedné a více karet | Dokumentace Microsoftu
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
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8231581761199be4df9c368494fb27bdc7926c51
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51748985"
---
# <a name="single-and-multi-tab-views"></a>Zobrazení jedné a více karet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor lze vytvořit různé typy zobrazení. Jedním z příkladů je okno editoru kódu, další je Návrhář formulářů.  
  
 Zobrazení s kartami s více je zobrazení, které obsahuje několik karet. Například HTML editor obsahuje dvě karty v dolní části: **návrhu** a **zdroj**, každé logické zobrazení. Návrhové zobrazení se zobrazí vykreslení webové stránky, druhý zobrazuje kód HTML, který se skládá z webové stránky.  
  
## <a name="accessing-physical-views"></a>Přístup k fyzické náhledy  
 Fyzické náhledy hostovat objekty zobrazení dokumentu, každý představující zobrazení data ve vyrovnávací paměti, jako je například kód nebo formuláře. Odpovídajícím způsobem každý objekt zobrazení dokumentu má fyzické zobrazení (identifikovaných podle něco jako řetězec fyzické zobrazení) a obecně jedné logické zobrazení.  
  
 V některých případech však fyzické zobrazení může mít dvě nebo více logických zobrazení. Mezi příklady patří editor, který má rozděleného okna se zobrazeními vedle sebe nebo Návrhář formulářů, který má grafické uživatelské rozhraní/návrhové zobrazení a zobrazení kódu na pozadí the tvaru.  
  
 Pokud chcete povolit přístup ke všem dostupné fyzické náhledy editoru, musíte vytvořit jedinečný fyzické zobrazení řetězce pro každý typ zobrazení objektu dokumentu, který můžete vytvořit objekt pro vytváření editoru. Například [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] objekt pro vytváření editoru můžete vytvořit dokument zobrazit objekty pro okno kódu a okno návrháře formulářů.  
  
## <a name="creating-multi-tabbed-views"></a>Vytváření s kartami s více zobrazení  
 I když objekt zobrazení dokumentu musí být přidružen fyzické zobrazení pomocí řetězce jedinečné fyzické zobrazení, můžete umístit několik karet v rámci fyzické zobrazení umožňují zobrazení dat různými způsoby. V této konfiguraci s kartami s více všechny karty jsou přidruženy stejném řetězci fyzické zobrazení, ale každá karta je uveden jiné logické zobrazení identifikátor GUID.  
  
 Chcete-li vytvořit zobrazení s kartami s více editoru, implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> rozhraní a přidružte jiné logické zobrazení GUID (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) se každé kartě můžete vytvářet.  
  
 Editor HTML aplikace Visual Studio je příkladem editoru pomocí zobrazení více karet. Má **návrhu** a **zdroj** karty. Pokud chcete povolit, jiné logické zobrazení souvisí s každou kartu `LOGICALVIEWID_TextView` pro **návrhu** kartu a `LOGICALVIEWID_Code` pro **zdroj** kartu.  
  
 Zadáním příslušné logické zobrazení VSPackage můžete zobrazit, který odpovídá konkrétní účel, jako je například návrhu formuláře úprav kódu a ladění kódu. Však jeden z okna musí být označeny NULL řetězcem, a to musí odpovídat primární logické zobrazení (`LOGVIEWID_Primary`).  
  
 V následující tabulce jsou uvedeny dostupné logické zobrazení hodnot a jejich použití.  
  
|IDENTIFIKÁTOR GUID LOGVIEWID|Doporučené použití|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|Primární výchozí zobrazení objektu pro vytváření editoru.<br /><br /> Tato hodnota musí podporovat všechny objekty pro vytváření editoru. Toto zobrazení musíte použít prázdný řetězec jako jeho fyzické zobrazení řetězce. Alespoň jedno logické zobrazení musí být nastavena na tuto hodnotu.|  
|`LOGVIEWID_Debugging`|Ladění v zobrazení. Obvykle `LOGVIEWID_Debugging` mapuje na stejném zobrazení jako `LOGVIEWID_Code`.|  
|`LOGVIEWID_Code`|Zobrazení spustí **zobrazit kód** příkazu.|  
|`LOGVIEWID_Designer`|Zobrazení spustí **zobrazit formulář** příkazu.|  
|`LOGVIEWID_TextView`|Zobrazení textového editoru. Toto je zobrazení, která vrací <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>, ze které můžete přistupovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|`LOGVIEWID_UserChooseView`|Se zobrazí výzva k výběru, kterého zobrazení má použít.|  
|`LOGVIEWID_ProjectSpecificEditor`|Předávány **otevřít v** dialogové okno<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> Když uživatel stiskne položka "(výchozí editor projektu)".|  
  
 I když jsou logické zobrazení identifikátory GUID rozšiřitelné, můžete použít jenom identifikátory GUID logické zobrazení definované ve vašich VSPackage.  
  
 Visual Studio při ukončení, zachová identifikátor GUID objektu pro vytváření editoru a fyzické zobrazení řetězce přidružený k oknu dokumentu tak, že je možné znovu otevřít okna dokumentu, když je toto řešení znovu otevřít. Pouze systému windows, které jsou otevřené po zavření řešení jsou zachované v souboru řešení (.suo). Tyto hodnoty odpovídají `VSFPROPID_guidEditorType` a `VSFPROPID_pszPhysicalView` hodnoty předané `propid` parametr v <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metody.  
  
## <a name="example"></a>Příklad  
 Tento fragment kódu ukazuje, jak <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> objektu se používá pro přístup k zobrazení, které implementuje `IVsCodeWindow`. V takovém případě <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> služby slouží k volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> a žádost o `LOGVIEWID_TextView`, který získá ukazatel na rámec okna. Ukazatel na objekt zobrazení dokumentu je získán voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> a zadáte třeba hodnotu `VSFPROPID_DocView`. Z objektu zobrazení dokumentu `QueryInterface` se volá pro `IVsCodeWindow`. V tomto případě je očekává, že se vrátí v textovém editoru a tak vrácený objekt zobrazení dokumentu v <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metoda je okno kódu.  
  
```cpp#  
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
 [Podpora více zobrazení dokumentů](../extensibility/supporting-multiple-document-views.md)   
 [Postupy: připojení zobrazení k datům dokumentů](../extensibility/how-to-attach-views-to-document-data.md)   
 [Vytváření vlastních editorů a návrhářů](../extensibility/creating-custom-editors-and-designers.md)

