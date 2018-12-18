---
title: Zveřejňování objektů projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae7b34df55593f07adeaffe8d654b59629baaae5
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510907"
---
# <a name="expose-project-objects"></a>Vystavení objektů projektu

Typy vlastních projektů může poskytovat objekty automatizace Pokud chcete povolit přístup k projektu pomocí rozhraní automatizace. Každý typ projektu se očekává poskytování standardní <xref:EnvDTE.Project> automatizační objekt, který přistupuje z <xref:EnvDTE.Solution>, které obsahuje kolekci všech projektů, které jsou otevřeny v integrovaném vývojovém prostředí. Každá položka v projektu má být vystavené <xref:EnvDTE.ProjectItem> objektu k němu přistupovat pomocí `Project.ProjectItems`. Kromě těchto objektů automatizace standardní projekty můžete nabídnout objekty automatizace specifické pro projekt.

Můžete vytvořit vlastní automatizace na kořenové úrovni objekty, ke kterým může přistupovat s pozdní vazbou pomocí objektu DTE kořenové `DTE.<customObjectName>` nebo `DTE.GetObject("<customObjectName>")`. Například Visual C++ vytvoří kolekce projektu specifické pro projekt jazyka C++ s názvem *umístěním* , který můžete přistupovat pomocí `DTE.VCProjects` nebo `DTE.GetObject("VCProjects")`. Můžete také vytvořit `Project.Object`, který je jedinečný pro typ projektu `Project.CodeModel`, což může být dotázán na jeho nejvíce odvozenému objektu a `ProjectItem`, která zveřejňuje `ProjectItem.Object` a `ProjectItem.FileCodeModel`.

Je běžné konvence pro projekty vystavit do kolekce projektů vlastní, specifické pro projekt. Například [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vytvoří kolekci C++ určitého projektu, který potom můžete přistupovat pomocí `DTE.VCProjects` nebo `DTE.GetObject("VCProjects")`. Můžete také vytvořit `Project.Object`, který je jedinečný pro typ projektu `Project.CodeModel`, což může být dotázán na jeho nejvíce odvozenému objektu `ProjectItem`, která zveřejňuje `ProjectItem.Object`a `ProjectItem.FileCodeModel`.  
  
## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Abyste mohli přispívat objekt VSPackage specifické pro projekt  
  
1.  Přidejte příslušné klíče, abyste *.pkgdef* soubor vašeho balíčku VSPackage.  
  
     Tady jsou například *.pkgdef* nastavení pro projekt jazyka C++:  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2.  Implementujte kód v <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metody, jako v následujícím příkladu.  
  
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
  
     V kódu `g_wszAutomationProjects` je název vaší kolekce projektu. `GetAutomationProjects` Metoda vytvoří objekt, který implementuje `Projects` rozhraní a vrátí `IDispatch` ukazatel na volajícím objektem, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
     Vyberte jedinečný název pro automatizační objekt. Název je v konfliktu nepředvídatelné a kolize způsobit konfliktní objekt název libovolně vyvolání Pokud více typů projektů, použijte stejný název. Měli byste zahrnout název vaší společnosti nebo některé jedinečné aspekty jeho název produktu, název objektu automatizace.  
  
     Vlastní `Projects` objektu kolekce je vstupním bodem usnadnění práce pro zbývající část váš model automatizace projektu. Je také přístupné z vašeho projektu objekt <xref:EnvDTE.Solution> kolekci projektu. Po vytvoření odpovídající položky kódu a registru, které poskytují zákazníky prostřednictvím `Projects` kolekci objektů, implementace musí poskytovat zbývající standardní objekty modelu projektu. Další informace najdete v tématu [projektu modelování](../../extensibility/internals/project-modeling.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
