---
title: Vystavení objektů projektu | Microsoft Docs
description: Přečtěte si, jak vystavit objekty pro vlastní typy projektů v aplikaci Visual Studio poskytnutím automatizačních objektů, které umožňují přístup k projektu pomocí rozhraní automatizace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c0ad045cb2cc46577c06d65e3ac1236228c870a9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069683"
---
# <a name="expose-project-objects"></a>Vystavení objektů projektu

Vlastní typy projektů mohou poskytovat automatizační objekty, aby umožnily přístup k projektu pomocí rozhraní automatizace. U každého typu projektu se očekává poskytnutí standardního <xref:EnvDTE.Project> automatizačního objektu, který je k dispozici z <xref:EnvDTE.Solution> , který obsahuje kolekci všech projektů, které jsou otevřeny v INTEGROVANÉm vývojovém prostředí. U každé položky v projektu je očekáváno zveřejnění objektu, který je <xref:EnvDTE.ProjectItem> k dispozici `Project.ProjectItems` . Kromě těchto standardních automatizačních objektů se můžou projekty vybrat k nabídnutí automatizačních objektů specifických pro projekt.

Můžete vytvořit vlastní automatizační objekty na úrovni root, ke kterým můžete získat přístup s pozdní vazbou z kořenového objektu DTE pomocí `DTE.<customObjectName>` nebo `DTE.GetObject("<customObjectName>")` . Například Visual C++ vytvoří kolekci projektů C++ specifickou pro projekt s názvem *VCProjects* , ke které máte přístup pomocí `DTE.VCProjects` nebo `DTE.GetObject("VCProjects")` . Můžete také vytvořit `Project.Object` , který je jedinečný pro typ projektu, `Project.CodeModel` , který je možné dotazovat na největší odvozený objekt a `ProjectItem` , který zpřístupňuje `ProjectItem.Object` a `ProjectItem.FileCodeModel` .

Jedná se o běžnou konvenci pro projekty k vystavení vlastní kolekce projektů specifických pro projekt. Například [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vytvoří kolekci projektů specifickou pro jazyk C++, ke které můžete následně přistupovat pomocí `DTE.VCProjects` nebo `DTE.GetObject("VCProjects")` . Můžete také vytvořit `Project.Object` , který je jedinečný pro typ projektu, `Project.CodeModel` , který je možné dotazovat pro jeho největší odvozený objekt, `ProjectItem` , který zpřístupňuje `ProjectItem.Object` a `ProjectItem.FileCodeModel` .

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Přispívání objektu pro konkrétní VSPackage pro projekt

1. Přidejte příslušné klíče do souboru *. pkgdef* vaší sady VSPackage.

     Tady je například nastavení *. pkgdef* pro projekt jazyka C++:

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. Implementujte kód v <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodě, jak je uvedeno v následujícím příkladu.

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

     V kódu `g_wszAutomationProjects` je název kolekce projektu. `GetAutomationProjects`Metoda vytvoří objekt, který implementuje `Projects` rozhraní a vrátí `IDispatch` ukazatel na volající objekt, jak je znázorněno v následujícím příkladu kódu.

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

     Vyberte jedinečný název pro objekt automatizace. Konflikty názvů nejsou předvídatelné a kolize způsobují konflikt názvů objektů, pokud více typů projektu používá stejný název. Do názvu objektu automatizace byste měli zahrnout firemní název nebo nějaký jedinečný aspekt jeho názvu produktu.

     Vlastní `Projects` objekt kolekce je pohodlný vstupní bod pro zbývající část modelu automatizace projektu. Váš objekt projektu je také přístupný z <xref:EnvDTE.Solution> kolekce projektu. Po vytvoření příslušného kódu a položek registru, které poskytují uživatelům `Projects` objekty kolekce, musí vaše implementace poskytnout zbývající standardní objekty pro model projektu. Další informace najdete v tématu [modelování projektu](../../extensibility/internals/project-modeling.md).

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
