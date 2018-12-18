---
title: Zveřejňování objektů projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9c4af521a8c6044742d69a1d71dcf605145d600d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731416"
---
# <a name="exposing-project-objects"></a>Zveřejňování objektů projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Typy vlastních projektů může poskytovat objekty automatizace Pokud chcete povolit přístup k projektu pomocí rozhraní automatizace. Každý typ projektu se očekává poskytování standardní <xref:EnvDTE.Project> automatizační objekt, který přistupuje z <xref:EnvDTE.Solution>, které obsahuje kolekci všech projektů, které jsou otevřeny v integrovaném vývojovém prostředí. Každá položka v projektu má být vystavené <xref:EnvDTE.ProjectItem> objektu k němu přistupovat pomocí <xref:EnvDTE.Project.ProjectItems>. Kromě těchto objektů automatizace standardní projekty můžete nabídnout objekty automatizace specifické pro projekt.  
  
 Můžete vytvořit vlastní automatizace na kořenové úrovni objekty, ke kterým může přistupovat s pozdní vazbou pomocí objektu DTE kořenové `DTE.<customeObjectName>` nebo `DTE.GetObject(“<customObjectName>”)`. Visual C++ například vytvoří kolekci projektu specifické pro projekt C++ s názvem "Umístěním", který můžete přistupovat pomocí DTE. DTE nebo umístěním. GetObject("VCProjects"). Můžete také vytvořit Project.Object, který je jedinečný pro typ projektu, Project.CodeModel, který může být dotázán pro jeho nejvíce odvozenému objektu, ProjectItem, která zpřístupňuje ProjectItem.Object a ProjectItem.FileCodeModel.  
  
 Je běžné konvence pro projekty vystavit do kolekce projektů vlastní, specifické pro projekt. Například [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] vytvoří kolekci C++ určitého projektu, který potom můžete přistupovat pomocí `DTE.VCProjects` nebo `DTE.GetObject("VCProjects")`. Můžete také vytvořit `Project.Object`, který je jedinečný pro typ projektu `Project.CodeModel`, což může být dotázán na jeho nejvíce odvozenému objektu `ProjectItem`, která zveřejňuje `ProjectItem.Object`a `ProjectItem.FileCodeModel`.  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Abyste mohli přispívat objekt VSPackage specifické pro projekt  
  
1.  Přidejte do souboru .pkgdef vašeho balíčku VSPackage odpovídající klíče.  
  
     Například tady je nastavení .pkgdef pro projekt jazyka C++:  
  
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
  
     Měli byste zvolit jedinečný název pro automatizační objekt. Název je v konfliktu nepředvídatelné a kolize způsobit konfliktní objekt název libovolně vyvolání Pokud více typů projektů, použijte stejný název. Měli byste zahrnout název vaší společnosti nebo některé jedinečné aspekty jeho název produktu, název objektu automatizace.  
  
     Vlastní `Projects` objektu kolekce je vstupním bodem usnadnění práce pro zbývající část váš model automatizace projektu. Je také přístupné z vašeho projektu objekt <xref:EnvDTE.Solution> kolekci projektu. Po vytvoření odpovídající položky kódu a registru, které poskytují zákazníky prostřednictvím `Projects` kolekci objektů, implementace musí poskytovat zbývající standardní objekty modelu projektu. Další informace najdete v tématu [projektu modelování](../../extensibility/internals/project-modeling.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>

