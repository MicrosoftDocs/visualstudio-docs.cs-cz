---
title: Vystavení objektů projektu | Microsoft Docs
description: Zjistěte, jak zveřejnit objekty pro vlastní typy projektů v Visual Studio tím, že poskytuje objekty automatizace, které umožňují přístup k projektu pomocí rozhraní automatizace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c3e89b4c80d64bedb77e68c648ba993794f8b658
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898289"
---
# <a name="expose-project-objects"></a>Vystavení objektů projektu

Vlastní typy projektů mohou poskytovat objekty automatizace, aby umožnily přístup k projektu pomocí rozhraní automatizace. Očekává se, že každý typ projektu poskytne standardní objekt automatizace, ke kterému se přistupuje z , který obsahuje kolekci všech projektů, které jsou v integrovaném vývojovém prostředí <xref:EnvDTE.Project> <xref:EnvDTE.Solution> otevřené. Očekává se, že každá položka v projektu bude zpřístupněna <xref:EnvDTE.ProjectItem> objektem, ke kterým se přistupuje pomocí `Project.ProjectItems` . Kromě těchto standardních objektů automatizace mohou projekty nabízet objekty automatizace specifické pro projekt.

Pomocí nebo můžete vytvořit vlastní objekty automatizace na kořenové úrovni, ke které máte přístup s pozdní vazbou z kořenového objektu `DTE.<customObjectName>` `DTE.GetObject("<customObjectName>")` DTE. Například když Visual C++ kolekci projektu C++ s názvem *VCProjects,* ke které můžete přistupovat pomocí `DTE.VCProjects` nebo `DTE.GetObject("VCProjects")` . Můžete také vytvořit , který je jedinečný pro typ projektu, , který lze dotazovat na jeho nejvíce odvozený objekt, a , který zpřístupňuje `Project.Object` `Project.CodeModel` a `ProjectItem` `ProjectItem.Object` `ProjectItem.FileCodeModel` .

Pro projekty se běžně používá konvence, která zveřejňuje vlastní kolekci projektů specifickou pro projekt. Například vytvoří kolekci [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektu specifickou pro jazyk C++, ke které pak budete mít přístup pomocí `DTE.VCProjects` nebo `DTE.GetObject("VCProjects")` . Můžete také vytvořit , který je jedinečný pro typ projektu, , který lze dotazovat na jeho nejvíce odvozený objekt, , který zpřístupňuje `Project.Object` `Project.CodeModel` , a `ProjectItem` `ProjectItem.Object` `ProjectItem.FileCodeModel` .

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Přispívání objektu specifického pro VSPackage pro projekt

1. Přidejte příslušné klíče do *souboru .pkgdef* vašeho balíčku VSPackage.

     Tady jsou například nastavení *.pkgdef* pro projekt jazyka C++:

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. Implementujte kód v <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodě jako v následujícím příkladu.

    ```cpp
    STDMETHODIMP CVsPackage::GetAutomationObject(
    /* [in]  */ LPCOLESTR       pszPropName,
    /* [out] */ IDispatch **    ppIDispatch)
    {
    ExpectedPtrRet(pszPropName);
    ExpectedPtrRet(ppIDispatch);
    *ppIDispatch = NULL;

        if (m_fZombie)
            return E_UNEXPECTED;

        if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)
        {
            return GetAutomationProjects(ppIDispatch);
        }
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)
        {
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);
        }
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)
        {
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);
        }
        return E_INVALIDARG;
    }
    ```

     V kódu `g_wszAutomationProjects` je název kolekce projektu. Metoda vytvoří objekt, který implementuje rozhraní a vrátí ukazatel na volající objekt, jak je znázorněno v `GetAutomationProjects` `Projects` následujícím `IDispatch` příkladu kódu.

    ```cpp
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch)
    {
        ExpectedPtrRet(ppIDispatch);
        *ppIDispatch = NULL;

        if (!m_srpAutomationProjects)
        {
            HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects);
            IfFailRet(hr);
            ExpectedExprRet(m_srpAutomationProjects != NULL);
        }
        return m_srpAutomationProjects.CopyTo(ppIDispatch);
    }
    ```

     Zvolte jedinečný název objektu automatizace. Konflikty názvů jsou nepředvídatelné a kolize způsobí, že konfliktní název objektu bude libovolně vyvolán, pokud více typů projektů používá stejný název. Název vaší společnosti nebo nějaký jedinečný aspekt názvu produktu byste měli zahrnout do názvu objektu automatizace.

     Objekt vlastní kolekce je vstupním bodem pro zbývající `Projects` část modelu automatizace projektu. Objekt projektu je také přístupný z <xref:EnvDTE.Solution> kolekce projektu. Po vytvoření příslušných položek kódu a registru, které poskytují spotřebitelům objekty kolekce, musí vaše implementace poskytnout zbývající standardní objekty `Projects` pro model projektu. Další informace najdete v tématu [Project modeling](../../extensibility/internals/project-modeling.md).

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
