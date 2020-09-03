---
title: Vystavení objektů projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f40c523c058bf215cc4574b3aa4a2e038c833beb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196646"
---
# <a name="exposing-project-objects"></a>Zveřejňování objektů projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vlastní typy projektů mohou poskytovat automatizační objekty, aby umožnily přístup k projektu pomocí rozhraní automatizace. U každého typu projektu se očekává poskytnutí standardního <xref:EnvDTE.Project> automatizačního objektu, který je k dispozici z <xref:EnvDTE.Solution> , který obsahuje kolekci všech projektů, které jsou otevřeny v INTEGROVANÉm vývojovém prostředí. U každé položky v projektu je očekáváno zveřejnění objektu, který je <xref:EnvDTE.ProjectItem> k dispozici <xref:EnvDTE.Project.ProjectItems> . Kromě těchto standardních automatizačních objektů se můžou projekty vybrat k nabídnutí automatizačních objektů specifických pro projekt.  
  
 Můžete vytvořit vlastní automatizační objekty na úrovni root, ke kterým můžete získat přístup s pozdní vazbou z kořenového objektu DTE pomocí `DTE.<customeObjectName>` nebo `DTE.GetObject(“<customObjectName>”)` . Například Visual C++ vytvoří kolekci projektů C++ specifickou pro projekt s názvem "VCProjects", ke které máte přístup pomocí DTE. VCProjects nebo DTE. GetObject ("VCProjects"). Můžete také vytvořit projekt. Object, který je jedinečný pro typ projektu, Project. CodeModel, který lze dotazovat pro svůj největší odvozený objekt, ProjectItem, který zpřístupňuje ProjectItem. Object a ProjectItem. FileCodeModel.  
  
 Jedná se o běžnou konvenci pro projekty k vystavení vlastní kolekce projektů specifických pro projekt. Například [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] vytvoří kolekci projektů specifickou pro jazyk C++, ke které můžete následně přistupovat pomocí `DTE.VCProjects` nebo `DTE.GetObject("VCProjects")` . Můžete také vytvořit `Project.Object` , který je jedinečný pro typ projektu, `Project.CodeModel` , který je možné dotazovat pro jeho největší odvozený objekt, `ProjectItem` , který zpřístupňuje `ProjectItem.Object` a `ProjectItem.FileCodeModel` .  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Přispívání objektu pro konkrétní VSPackage pro projekt  
  
1. Přidejte příslušné klíče do souboru. pkgdef vaší sady VSPackage.  
  
     Tady je například nastavení. pkgdef pro projekt jazyka C++:  
  
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
  
     Pro objekt automatizace byste měli zvolit jedinečný název. Konflikty názvů nejsou předvídatelné a kolize způsobují konflikt názvů objektů, pokud více typů projektu používá stejný název. Do názvu objektu automatizace byste měli zahrnout firemní název nebo nějaký jedinečný aspekt jeho názvu produktu.  
  
     Vlastní `Projects` objekt kolekce je pohodlný vstupní bod pro zbývající část modelu automatizace projektu. Váš objekt projektu je také přístupný z <xref:EnvDTE.Solution> kolekce projektu. Po vytvoření příslušného kódu a položek registru, které poskytují uživatelům `Projects` objekty kolekce, musí vaše implementace poskytnout zbývající standardní objekty pro model projektu. Další informace najdete v tématu [modelování projektu](../../extensibility/internals/project-modeling.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
