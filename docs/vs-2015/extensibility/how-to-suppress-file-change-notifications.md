---
title: 'Postupy: potlačení oznámení o změně souboru | Dokumentace Microsoftu'
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
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e4f82fd90d95a595d39403d2ee131285034b95d0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51808255"
---
# <a name="how-to-suppress-file-change-notifications"></a>Postupy: potlačení oznámení o změně souborů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při změně fyzického souboru představující textovou vyrovnávací paměť, dialogové okno zobrazí se zpráva **chcete uložit změny následujících položek?** To se označuje jako oznámení o změně souboru. Pokud mnoho změn se bude do souboru, ale toto dialogové okno zobrazení tytéž může být nepříjemné.  
  
 Toto dialogové okno pomocí následujícího postupu můžete potlačit prostřednictvím kódu programu. Tímto způsobem můžete znovu načíst soubor okamžitě bez nutnosti uživateli výzvu k uložení změn pokaždé, když.  
  
### <a name="to-suppress-file-change-notification"></a>Potlačit oznámení o změně souboru  
  
1.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metodou ke zjištění, které textové vyrovnávací paměti objekt je přidružený otevřený soubor.  
  
2.  S přímým přístupem <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objekt, který je v paměti pro ignorování sledování změn souborů prostřednictvím provedeného <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> rozhraní z <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objektu (data dokumentu) a potom provádění <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> metodu s `fIgnore` parametr Nastavte na `true`.  
  
3.  Volání metody na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> rozhraní aktualizovat v paměťově <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objekt se změny souborů (například při přidání pole do komponenty).  
  
4.  Aktualizujte soubor na disku se změnami bez zohlednění čekající úpravy, které uživatelé mohou být v průběhu.  
  
     Tímto způsobem, když je <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> upozornění na změnu objektu, který chcete pokračovat v monitorování pro soubor, vyrovnávací paměť textu v paměti odráží změny, které jste vygenerovali, a také všechny čekající změny. Nejnovější kód vygenerovaný vám odráží souboru na disku a všechny dříve uložené změny uživatelem v kódu uživatele upravit.  
  
5.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> metoda upozornit <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objektu, který chcete pokračovat v monitorování pro oznámení o změně souborů nastavením `fIgnore` parametr `false`.  
  
6.  Pokud máte v plánu provést několik změn do souboru, jako v případě správy zdrojového kódu (SCC), je zapotřebí sdělit globálního souboru služby změnit dočasně pozastavit oznámení o změně souboru.  
  
     Například pokud přepsat soubor a potom změňte časové razítko, musí pozastavit oznámení o změně souborů, jako přepsání a timestample operací, každý se počítají jako události změny do samostatného souboru. Povolit oznámení o změně globálního souboru místo toho byste měli volat <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> metody.  
  
## <a name="example"></a>Příklad  
 Následující ukazuje, jak můžete potlačit oznámení o změně souboru.  
  
```cpp#  
//Misc. helper classes  
  
CSuspendFileChanges::CSuspendFileChanges(  
    /* [in] */ const CString& strMkDocument,   
    /* [in] */ BOOL fSuspendNow /* = TRUE */)   
:  
    m_strMkDocument(strMkDocument),  
    m_fFileChangeSuspended(FALSE)  
{  
    if(fSuspendNow)  
        Suspend();  
}  
CSuspendFileChanges::~CSuspendFileChanges()  
{  
    Resume();  
}  
void CSuspendFileChanges::Suspend()  
{  
    USES_CONVERSION;  
  
    // Prevent suspend from suspending more than once.  
    if(m_fFileChangeSuspended)  
        return;  
  
    IVsRunningDocumentTable* pRDT =   
      _VxModule.GetIVsRunningDocumentTable();  
    ASSERT(pRDT);  
    if (!pRDT)  
        return;  
  
    CComPtr<IUnknown> srpDocData;  
    VSCOOKIE vscookie = VSCOOKIE_NIL;  
    pRDT->FindAndLockDocument(RDT_NoLock, T2COLE(m_strMkDocument),    
      NULL, NULL, &srpDocData, &vscookie);  
    if ( (vscookie == VSCOOKIE_NIL) || !srpDocData)  
        return;  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
    {  
        m_fFileChangeSuspended = TRUE;  
        srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, TRUE);   
        srpDocData->QueryInterface(IID_IVsDocDataFileChangeControl,   
          (void**)&m_srpIVsDocDataFileChangeControl);  
        if(m_srpIVsDocDataFileChangeControl)  
            m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(TRUE);  
    }  
}  
void CSuspendFileChanges::Resume()  
{  
    if(!m_fFileChangeSuspended)  
        return;  
  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
  
    srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, FALSE);   
    if(m_srpIVsDocDataFileChangeControl)  
        m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(FALSE);  
    m_fFileChangeSuspended = FALSE;  
    m_srpIVsDocDataFileChangeControl.Release();  
}  
// Misc. helper classes  
```  
  
## <a name="robust-programming"></a>Robustní programování  
 Pokud váš případ zahrnuje více změn do souboru, jako v případě SCC, je potřeba obnovit oznámení o změnách globálního souboru než se dokument dat. Chcete pokračovat v monitorování pro změny souborů.

