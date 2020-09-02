---
title: Inicializační sekvence podtypů projektů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c5594d54c188c2f561dd66229e808e48068ba41a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192655"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Inicializační sekvence podtypů projektů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Prostředí vytvoří projekt voláním základní implementace výroby projektu systému <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> . Konstrukce podtypu projektu začíná, když prostředí určí, že seznam identifikátorů GUID typu projektu pro rozšíření souboru projektu není prázdný. Přípona souboru projektu a GUID projektu určují, zda je projekt [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] typu projektu nebo. Například rozšíření. vbproj a {F184B08F-C81C-45F6-A57F-5ABD9991F28F} identifikují [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projekt.  
  
## <a name="environments-initialization-of-project-subtypes"></a>Inicializace podtypů projektu v prostředí  
 Následující postup podrobně popisuje sekvenci inicializace pro systém projektu agregovaný více podtypy projektu.  
  
1. Prostředí volá základní projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> a i když projekt analyzuje svůj projektový soubor, zjistí, že seznam identifikátorů GUID typu agregace projektu není `null` . Projekt nepokračuje přímo v vytváření projektu.  
  
2. Projekt volá `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> službu pro vytvoření podtypu projektu pomocí implementace metody v prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> . V rámci této metody prostředí zpřístupňuje rekurzivní volání funkcí do vašich implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> `M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)` a <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> metody, když je prochází seznamem identifikátorů GUID typu projektu, počínaje podtypem vnějšího projektu.  
  
    Následující podrobnosti popisují kroky inicializace.  
  
   1. Implementace metody v prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> volá metodu HrCreateInnerProj s následující deklarací funkce:  
  
       ```  
       HRESULT HrCreateInnerProj  
       (  
           WCHAR *pwszGuids,  
           IUnknown *pOuter,  
           IVsAggregatableProject *pOwner,  
           LPCOLESTR pszFilename,  
           LPCOLESTR pszLocation,  
           LPCOLESTR pszName,  
           VSCREATEPROJFLAGS grfCreateFlags,  
           IUnknown **ppInner,  
           BOOL *pfCancelled  
       )  
       ```  
  
        Při prvním volání této funkce, tj. pro podtyp vnějšího projektu, parametry `pOuter` a `pOwner` jsou předány jako `null` a funkce nastaví podtyp vnějšího projektu `IUnknown` na `pOuter` .  
  
   2. V dalším prostředí volá `HrCreateInnerProj` funkce v seznamu druhý identifikátor GUID typu projektu. Tento identifikátor GUID odpovídá druhému krokování vnějšího typu projektu v rámci směrem k základnímu projektu v agregační sekvenci.  
  
   3. Nyní odkazuje na `pOuter` `IUnknown` podtyp vnějšího projektu a `HrCreateInnerProj` volá vaši implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> následovanou voláním implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> . V <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> metodě předáte řízení `IUnknown` vnějšího typu projektu `pOuter` . Vlastněný projekt (podtyp vnitřního projektu) musí vytvořit svůj agregovaný objekt projektu zde. V <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> implementaci metody předáte ukazatel na `IUnknown` vnitřní projekt, který je agregován. Tyto dvě metody vytvoří agregační objekt a vaše implementace musí dodržovat pravidla agregace modelu COM, aby se zajistilo, že podtyp projektu neukončí podíl počtu odkazů sám na sebe.  
  
   4. `HrCreateInnerProj` volá vaši implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> . V této metodě je dílčí typ projektu svou inicializační prací. Můžete například zaregistrovat události řešení v <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> .  
  
   5. `HrCreateInnerProj` se volá rekurzivně, dokud se nedosáhne posledního GUID (základní projekt) v seznamu. Pro každé z těchto volání se kroky, c až d, opakují. `pOuter` odkazuje na podtyp vnějšího projektu `IUnknown` pro každou úroveň agregace.  
  
   Následující příklad podrobně popisuje programový proces v přibližné reprezentaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> metody, jak je implementováno v prostředí. Kód je pouze příkladem; není určeno k zkompilování a veškerá kontrola chyb byla odebrána pro přehlednost.  
  
## <a name="example"></a>Příklad  
  
### <a name="code"></a>Kód  
  
```  
HRESULT CreateAggregateProject  
(  
    LPCOLESTR lpstrGuids,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    REFIID iidProject,   
    void **ppvProject)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpunkProj;  
    CComPtr<IVsAggregatableProject> srpAggProject;  
    CComBSTR bstrGuids = lpstrGuids;  
    BOOL fCanceled = FALSE;  
    *ppvProject = NULL;  
  
    HrCreateInnerProj(  
         bstrGuids, NULL, NULL, pszFilename, pszLocation,   
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);  
    srpunkProj->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggProject));  
    srpAggProject->OnAggregationComplete();  
    srpunkProj->QueryInterface(iidProject, ppvProject);  
}  
  
HRESULT HrCreateInnerProj  
(  
    WCHAR *pwszGuids,   
    IUnknown *pOuter,   
    IVsAggregatableProject *pOwner,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    IUnknown **ppInner,   
    BOOL *pfCanceled  
)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpInner;  
    CComPtr<IVsAggregatableProject> srpAggInner;  
    CComPtr<IVsProjectFactory> srpProjectFactory;  
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;  
    GUID guid = GUID_NULL;  
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');  
    WCHAR wszText[_MAX_PATH+150] = L"";  
  
    if (pwszNextGuids)  
    {  
        *pwszNextGuids++ = 0;  
    }  
  
    CLSIDFromString(pwszGuids, &guid);  
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(  
        guid, &srpProjectFactory);  
    srpProjectFactory->QueryInterface(  
        IID_IVsAggregatableProjectFactory,   
        (void **)&srpAggPF);  
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);  
    srpInner->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggInner);  
  
    if (pOwner)  
    {  
        IfFailGo(pOwner->SetInnerProject(srpInner));  
    }  
  
    if (pwszNextGuids)  
    {  
        CComPtr<IUnknown> srpNextInner;  
        HrCreateInnerProj(  
            pwszNextGuids, pOuter ? pOuter : srpInner,   
            srpAggInner, pszFilename, pszLocation, pszName,   
            grfCreateFlags, &srpNextInner, pfCanceled);  
    }  
  
    return srpAggInner->InitializeForOuter(  
        pszFilename, pszLocation, pszName, grfCreateFlags,   
        IID_IUnknown, (void **)ppInner, pfCanceled);  
}  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Flavor>   
 [Podtypy projektů](../../extensibility/internals/project-subtypes.md)
