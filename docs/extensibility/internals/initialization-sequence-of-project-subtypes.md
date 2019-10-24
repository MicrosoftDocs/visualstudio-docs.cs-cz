---
title: Inicializační sekvence podtypů projektů | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 678f704c73a39cdf2130d36fcfb1a74925dd89d1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726880"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Inicializační sekvence podtypů projektů
Prostředí vytvoří projekt voláním základní implementace výroby projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>. Konstrukce podtypu projektu začíná, když prostředí určí, že seznam identifikátorů GUID typu projektu pro rozšíření souboru projektu není prázdný. Přípona souboru projektu a GUID projektu určují, zda se jedná o typ projektu [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] nebo [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Například rozšíření. vbproj a {F184B08F-C81C-45F6-A57F-5ABD9991F28F} identifikují projekt [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)].

## <a name="environments-initialization-of-project-subtypes"></a>Inicializace podtypů projektu v prostředí
 Následující postup podrobně popisuje sekvenci inicializace pro systém projektu agregovaný více podtypy projektu.

1. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> základního projektu a zatímco projekt analyzuje svůj soubor projektu, zjistí, že seznam identifikátorů GUID typu agregace projektu není `null`. Projekt nepokračuje přímo v vytváření projektu.

2. Projekt volá `QueryService` ve službě <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> k vytvoření podtypu projektu pomocí implementace metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> prostředí. V rámci této metody prostředí provádí rekurzivní volání funkcí do vašich implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> metody při procházení seznamu identifikátorů GUID typu projektu, počínaje podtypem vnějšího projektu.

     Následující podrobnosti popisují kroky inicializace.

    1. Implementace metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> v prostředí volá metodu `HrCreateInnerProj` s následující deklarací funkce:

         \<CodeContentPlaceHolder > 0 </CodeContentPlaceHolder>

         Při prvním volání této funkce, tj. pro podtyp vnějšího projektu, jsou parametry `pOuter` a `pOwner` předány jako `null` a funkce nastaví `IUnknown` podtypu projektu na hodnotu `pOuter`.

    2. V dalším prostředí volá `HrCreateInnerProj` Function s druhým typem GUID typu projektu v seznamu. Tento identifikátor GUID odpovídá druhému krokování vnějšího typu projektu v rámci směrem k základnímu projektu v agregační sekvenci.

    3. @No__t_0 nyní odkazuje na `IUnknown` vnějšího typu projektu a `HrCreateInnerProj` volá vaši implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> následovanou voláním implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>. V <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> metoda předáváte `IUnknown` podtypu vnějšího projektu `pOuter`. Vlastněný projekt (podtyp vnitřního projektu) musí vytvořit svůj agregovaný objekt projektu zde. V implementaci metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> předáte ukazatel na `IUnknown` vnitřního projektu, který je agregován. Tyto dvě metody vytvoří agregační objekt a vaše implementace musí dodržovat pravidla agregace modelu COM, aby se zajistilo, že podtyp projektu neukončí podíl počtu odkazů sám na sebe.

    4. `HrCreateInnerProj` volá vaši implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>. V této metodě je dílčí typ projektu svou inicializační prací. Můžete například zaregistrovat události řešení v <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>.

    5. `HrCreateInnerProj` se volá rekurzivně, dokud se nedosáhne posledního GUID (základní projekt) v seznamu. Pro každé z těchto volání se kroky, c až d, opakují. `pOuter` odkazuje na vnější podtyp projektu `IUnknown` pro každou úroveň agregace.

## <a name="example"></a>Příklad

Následující příklad podrobně popisuje programový proces v přibližné reprezentaci metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>, jak je implementováno v prostředí. Kód je pouze příkladem; není určeno k zkompilování a veškerá kontrola chyb byla odebrána pro přehlednost.

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

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.Shell.Flavor>
- [Podtypy projektů](../../extensibility/internals/project-subtypes.md)