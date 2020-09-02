---
title: 'Postupy: potlačení oznámení o změnách souborů | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f045175eae165b75a887ada2716b19f34fc228b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204082"
---
# <a name="how-to-suppress-file-change-notifications"></a>Postupy: Potlačení oznámení o změně souboru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když se změní fyzický soubor představující textovou vyrovnávací paměť, zobrazí se dialogové okno se zprávou chcete **Uložit změny následujících položek?** Tato zpráva se označuje jako oznámení o změně souboru. Pokud se do souboru stane mnoho změn, ale toto dialogové okno, které se bude zobrazovat dál a znovu, se může rychle stát obtěžujícím.  
  
 Pomocí následujícího postupu můžete toto dialogové okno potlačit programově. Tímto způsobem můžete znovu načíst soubor hned bez nutnosti vyzvat uživatele k uložení změn pokaždé.  
  
### <a name="to-suppress-file-change-notification"></a>Postup při potlačení oznámení o změně souboru  
  
1. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metodu pro určení, který objekt textové vyrovnávací paměti je přidružen k vašemu otevřenému souboru.  
  
2. Nasměrujte <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objekt, který je v paměti pro ignorování sledování změn souborů <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> , získáním rozhraní z <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objektu (data dokumentu) a následnou implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> metody s `fIgnore` parametrem nastaveným na `true` .  
  
3. Zavolejte metody na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> rozhraní a a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> aktualizujte objekt v paměti <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> se změnami souborů (například při přidání pole do komponenty).  
  
4. Aktualizuje soubor na disku změnami bez ohledu na to, kdy uživatel provedl nedokončené úpravy.  
  
     Tímto způsobem při nasměrování <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objektu pro pokračování v monitorování oznámení o změnách souborů odráží textová vyrovnávací paměť v paměti změny, které jste vygenerovali, a také všechny ostatní probíhající úpravy. Soubor na disku odráží nejnovější kód vygenerovaný vámi a všechny dříve uložené změny provedené uživatelem v kódu upravovaném uživatelem.  
  
5. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> metodu pro upozornění objektu, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> aby obnovil monitorování oznámení o změnách souborů nastavením `fIgnore` parametru na `false` .  
  
6. Pokud máte v úmyslu provést několik změn v souboru, jako v případě správy zdrojového kódu (SCC), je nutné oznámit globální službě změny souborů, aby dočasně pozastavila oznámení o změnách souborů.  
  
     Například pokud přepíšete soubor a pak změníte časové razítko, musíte pozastavit oznámení o změnách souborů, protože operace přepsání a timestample se každý počítají jako samostatná událost změny souboru. Pokud chcete povolit oznámení o změně globálního souboru, měli byste místo toho zavolat <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> metodu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak potlačit oznamování změn souborů.  
  
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
 Pokud váš případ zahrnuje více změn v souboru, jako v případě SCC, je důležité obnovit globální oznámení o změnách souborů před upozorněním na data dokumentu, aby bylo možné pokračovat v monitorování pro změny souborů.
