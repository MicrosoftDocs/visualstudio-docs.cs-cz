---
title: Pořadí inicializace podtypů projekt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fe7e7a574d04ec9a49252e32e0fbb8b5685778aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131605"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Pořadí inicializace podtypů projektu
Prostředí vytvoří projektu voláním implementace objektu pro vytváření základní projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>. Konstrukce podtypu projektu spustí, když prostředí určuje, že v seznamu projektu typu GUID příponu souboru projektu není prázdná. Přípona souboru projekt a projekt GUID určete, zda je projekt [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] nebo [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] typ projektu. Například rozšíření .vbproj a {F184B08F-C81C-45F6-A57F-5ABD9991F28F} identifikovat [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projektu.

## <a name="environments-initialization-of-project-subtypes"></a>Inicializace struktury prostředí podtypů projektu
 Následující postup popisuje pořadí inicializace pro projekt systému agregaci více podtypů projektu.

1.  Prostředí volá základní projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, a při jeho souboru projektu analyzuje projektu zjistí typ agregace projektu identifikátory GUID seznamu není `null`. Projekt ze přímo vytvoření jeho projektu.

2.  Volání projektu `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> služby pro vytvoření projektu podtypem pomocí implementace v prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> metoda. V rámci této metody prostředí provádí volání rekurzivní funkce na vaší implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> metody při jeho je procházení seznamem projektu zadejte identifikátory GUID, počínaje dílčí nejkrajnější projektu.

     Následující podrobnosti kroků inicializace.

    1.  V prostředí provádění <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> volání metod `HrCreateInnerProj` metoda s deklarace následující funkce:

         <CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Když tato funkce je volána poprvé, tedy pro nejkrajnější projektu dílčí parametry `pOuter` a `pOwner` předaná jako `null` a funkce nastaví dílčí nejkrajnější projektu `IUnknown` k `pOuter`.

    2.  Vedle prostředí volá `HrCreateInnerProj` funkci s druhým typem projektu identifikátor GUID v seznamu. Tento identifikátor GUID odpovídá druhý dílčí vnitřní projektu krokování směrem k základní projekt v pořadí agregace.

    3.  `pOuter` Nyní ukazovat na `IUnknown` podtypu nejkrajnější projektu a `HrCreateInnerProj` volá vaši implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> následuje volání vaši implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>. V <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> metoda, kterou předáte řízení `IUnknown` podtypu nejkrajnější projektu `pOuter`. Vlastní projektu (vnitřní projektu podtyp) potřebuje k vytvoření jeho agregační projektu objekt. V <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> implementace metody, kterou předáte ukazatel na `IUnknown` vnitřní projektu, který je agregaci. Tyto dvě metody vytvoření objektu agregace a vaší implementace muset postupovat podle pravidla agregace COM pro zajištění, že podtypem projektu skončili není podržíte počet odkazů na sebe sama.

    4.  `HrCreateInnerProj` volá vaši implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>. Tato metoda dílčí projektu funguje jeho inicializace. Můžete například zaregistrovat řešení události v <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>.

    5.  `HrCreateInnerProj` rekurzivní je volána, dokud nebude dosaženo poslední GUID (základní projekt) v seznamu. Pro každý z těchto volání jsou kroky, c prostřednictvím d, opakovat. `pOuter` odkazuje na dílčí nejkrajnější projektu `IUnknown` na jednotlivých úrovních agregace.

## <a name="example"></a>Příklad

V následujícím příkladu je podrobně popsán proces programový v přibližnou reprezentace <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> metoda, jak je implementované prostředí. Kód je jenom jako příklad; rozhraní není určeno k zkompilovat a kontrolu všech chyb pro přehlednost odebral.

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