---
title: Vystavení objektů projektu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81446fa582524872b03199ae707f658776787961
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708473"
---
# <a name="expose-project-objects"></a>Vystavit objekty projektu

Vlastní typy projektů můžete poskytnout objekty automatizace s cílem umožnit přístup k projektu pomocí rozhraní automatizace. Očekává se, že každý <xref:EnvDTE.Project> typ projektu poskytne standardní <xref:EnvDTE.Solution>objekt automatizace, který je přístupný z , který obsahuje kolekci všech projektů, které jsou otevřeny v rozhraní IDE. Očekává se, že každá položka v <xref:EnvDTE.ProjectItem> projektu bude `Project.ProjectItems`vystavena objektu, ke kterého má přístup . Kromě těchto standardních objektů automatizace mohou projekty nabízet objekty automatizace specifické pro projekt.

Můžete vytvořit vlastní objekty automatizace kořenové úrovně, které můžete přistupovat pozdě vázané z kořenového objektu DTE pomocí `DTE.<customObjectName>` nebo `DTE.GetObject("<customObjectName>")`. Visual C++ například vytvoří kolekci projektů specifických pro c++ s `DTE.VCProjects` `DTE.GetObject("VCProjects")`názvem *VCProjects,* ke které máte přístup pomocí nebo . Můžete také vytvořit `Project.Object`, který je jedinečný pro `Project.CodeModel`typ projektu, a , který může být `ProjectItem`dotazován na `ProjectItem.Object` jeho `ProjectItem.FileCodeModel`nejvíce odvozený objekt a , který zveřejňuje a .

Je běžné konvence pro projekty vystavit vlastní, kolekce projektu specifické pro projekt. Například [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vytvoří kolekci projektu specifické pro C++, ke které pak můžete přistupovat pomocí `DTE.VCProjects` nebo `DTE.GetObject("VCProjects")`. Můžete také vytvořit `Project.Object`, který je jedinečný pro `Project.CodeModel`typ projektu, a , který může být `ProjectItem`dotazován na `ProjectItem.Object`jeho `ProjectItem.FileCodeModel`nejvíce odvozený objekt, , který zveřejňuje , a .

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Chcete-li přispět objekt specifický pro VSPackage pro projekt

1. Přidejte příslušné klíče do souboru *.pkgdef* vašeho balíčku VSPackage.

     Například zde jsou nastavení *.pkgdef* pro jazykový projekt Jazyka C++:

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. Implementujte kód <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> v metodě, jako v následujícím příkladu.

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

     V kódu `g_wszAutomationProjects` je název kolekce projektu. Metoda `GetAutomationProjects` vytvoří objekt, který `Projects` implementuje `IDispatch` rozhraní a vrátí ukazatel volajícíobjekt, jak je znázorněno v následujícím příkladu kódu.

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

     Zvolte jedinečný název objektu automatizace. Konflikty názvů jsou nepředvídatelné a kolize způsobit konfliktní název objektu, které mají být libovolně vyvolána, pokud více typů projektu použít stejný název. Název společnosti nebo některé jedinečné aspekty jeho názvu produktu byste měli zahrnout do názvu objektu automatizace.

     Vlastní `Projects` objekt kolekce je vstupní bod pohodlí pro zbývající část modelu automatizace projektu. Objekt projektu je také <xref:EnvDTE.Solution> přístupný z kolekce projektu. Po vytvoření příslušného kódu a položek registru, které poskytují spotřebitelům `Projects` kolekce objektů, musí implementace poskytnout zbývající standardní objekty pro model projektu. Další informace naleznete v [tématu Project modeling](../../extensibility/internals/project-modeling.md).

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
