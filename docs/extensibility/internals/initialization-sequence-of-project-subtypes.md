---
title: Posloupnost inicializace podtypů projektu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05a3c312f61dd2b2c63c3f38ef8bac2203b326db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707634"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Inicializační sekvence podtypů projektů
Prostředí vytvoří projekt voláním implementace továrny <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>základního projektu . Konstrukce podtypu projektu se spustí, když prostředí určí, že seznam GUID typu projektu pro příponu souboru projektu není prázdný. Přípona souboru projektu a identifikátor GUID projektu určují, zda je projekt [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] typu projektu nebo typu [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projektu. Například rozšíření .vbproj a {F184B08F-C81C-45F6-A57F-5ABD9991F28F} [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] identifikují projekt.

## <a name="environments-initialization-of-project-subtypes"></a>Inicializace podtypů projektu prostředí
 Následující postup podrobně popisuje sekvenci inicializace pro systém projektu agregovaný více podtypy projektu.

1. Prostředí volá základní projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, a zatímco projekt analyzuje soubor projektu zjistí, že agregační seznam `null`guid typu projektu není . Projekt přerušuje přímo vytváření svého projektu.

2. Projekt vyzývá `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> službu k vytvoření podtypu projektu pomocí prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> implementace metody. V rámci této metody prostředí umožňuje rekurzivní funkce <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> implementace aplikace a metody při chůzi seznam identifikátorů GUID typu projektu, počínaje nejvzdálenější podtyp projektu.

     Následující podrobnosti kroky inicializace.

    1. Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> metody prostředí volá metodu `HrCreateInnerProj` s následující deklarací funkce:

         \<CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Pokud je tato funkce volána poprvé, to znamená pro nejvzdálenější podtyp `pOwner` projektu, `null` parametry a jsou předány `pOuter` `IUnknown` jako `pOuter`a funkce nastaví podtyp projektu na .

    2. Dále volání `HrCreateInnerProj` prostředí funkce s druhým typem typu projektu GUID v seznamu. Tento identifikátor GUID odpovídá druhému podtypu vnitřního projektu, který vstupuje směrem k základnímu projektu v sekvenci agregace.

    3. Nyní `pOuter` `IUnknown` ukazuje na nejvzdálenější podtyp projektu a `HrCreateInnerProj` volá implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> následuje volání implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>aplikace . V <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> metodě předáváte řízení `IUnknown` nejkrajnějšího `pOuter`podtypu projektu . Vlastněný projekt (podtyp vnitřního projektu) musí vytvořit svůj agregační objekt projektu zde. V <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> implementaci metody předáte ukazatel `IUnknown` na vnitřní projekt, který je právě agregována. Tyto dvě metody vytvořit objekt agregace a implementace je třeba dodržovat pravidla agregace COM zajistit, že podtyp projektu neskončí drží počet odkazů na sebe.

    4. `HrCreateInnerProj`volá implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>aplikace . V této metodě projekt podtyp provádí jeho inicializační práce. Můžete například zaregistrovat události <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>řešení v .

    5. `HrCreateInnerProj`se nazývá rekurzivně, dokud není dosaženo posledníguid (základní projekt) v seznamu. Pro každý z těchto volání se opakují kroky c až d. `pOuter`odkazuje na nejvzdálenější podtyp `IUnknown` projektu pro každou úroveň agregace.

## <a name="example"></a>Příklad

Následující příklad podrobně popisuje programový proces v <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> přibližné reprezentaci metody, jak je implementována prostředím. Kód je pouze příklad; není určena ke kompilaci a všechny kontroly chyb byla odebrána pro přehlednost.

```cpp
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

- <xref:Microsoft.VisualStudio.Shell.Flavor>
- [Podtypy projektů](../../extensibility/internals/project-subtypes.md)
