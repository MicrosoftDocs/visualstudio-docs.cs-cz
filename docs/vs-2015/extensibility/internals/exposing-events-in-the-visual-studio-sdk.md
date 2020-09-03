---
title: Vystavení událostí v sadě Visual Studio SDK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7056497c505bbb355287416e468e411b4e5a2a62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196692"
---
# <a name="exposing-events-in-the-visual-studio-sdk"></a>Zveřejňování událostí v sadě Visual Studio SDK
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] umožňuje pomocí automatizace použít zdrojové události. Pro projekty a položky projektu doporučujeme použít zdrojové události.  
  
 Události jsou načítány spotřebiteli automatizace z <xref:EnvDTE.DTEClass.Events%2A> objektu nebo <xref:EnvDTE.DTEClass.GetObject%2A> ("EventObjectName"). Volání prostředí `IDispatch::Invoke` pomocí `DISPATCH_METHOD` `DISPATCH_PROPERTYGET` příznaků nebo pro vrácení události.  
  
 Následující postup vysvětluje, jak jsou vráceny události specifické pro VSPackage.  
  
1. Spustí se prostředí.  
  
2. Načte z registru všechny názvy hodnot v rámci automatizace, AutomationEvents a vlastnosti automatizace klíčů všech VSPackage a uloží je do tabulky.  
  
3. Uživatel automatizace volá v tomto příkladu `DTE.Events.AutomationProjectsEvents` nebo `DTE.Events.AutomationProjectItemsEvents` .  
  
4. Prostředí nalezne parametr řetězce v tabulce a načte odpovídající VSPackage.  
  
5. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodu pomocí názvu předaného ve volání; v tomto příkladu AutomationProjectsEvents nebo AutomationProjectItemsEvents.  
  
6. VSPackage vytvoří kořenový objekt, který obsahuje metody jako `get_AutomationProjectsEvents` a `get_AutomationProjectItemEvents` a poté vrátí ukazatel IDispatch objektu.  
  
7. Prostředí volá příslušnou metodu na základě názvu předaného do volání automatizace.  
  
8. `get_`Metoda vytvoří další objekt události založený na rozhraní IDispatch, který implementuje `IConnectionPointContainer` rozhraní i `IConnectionPoint` rozhraní a vrátí IDispatchpointer objektu.  
  
   Chcete-li vystavit událost pomocí automatizace, je nutné reagovat na <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> a sledovat řetězce, které přidáte do registru. V ukázce základního projektu jsou řetězce "BscProjectsEvents" a "BscProjectItemsEvents".  
  
## <a name="registry-entries-from-the-basic-project-sample"></a>Položky registru z ukázky základní projekt  
 V této části se dozvíte, kde přidat do registru hodnoty událostí automatizace.  
  
 [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0\Packages \\<PkgGUID \> \AutomationEvents]  
  
 "AutomationProjectEvents" = "vrátí objekt AutomationProjectEvents"  
  
 "AutomationProjectItemEvents" = "vrátí objekt AutomationProjectItemsEvents"  
  
|Název|Typ|Rozsah|Popis|  
|----------|----------|-----------|-----------------|  
|Výchozí (@)|REG_SZ|Nepoužitý|Nepoužívá se. Pro dokumentaci můžete použít pole data.|  
|AutomationProjectsEvents|REG_SZ|Název objektu události|Je relevantní pouze název klíče. Pro dokumentaci můžete použít pole data.<br /><br /> Tento příklad pochází ze základní ukázky projektu.|  
|AutomationProjectItemEvents|REG_SZ|Název objektu události|Je relevantní pouze název klíče. Pro dokumentaci můžete použít pole data.<br /><br /> Tento příklad pochází ze základní ukázky projektu.|  
  
 Pokud je některý z vašich objektů událostí požadován příjemcem automatizace, vytvořte kořenový objekt, který obsahuje metody pro jakoukoliv událost, kterou VSPackage podporuje. Prostředí volá odpovídající `get_` metodu pro tento objekt. Například pokud `DTE.Events.AutomationProjectsEvents` je volána, je `get_AutomationProjectsEvents` vyvolána metoda na kořenovém objektu.  
  
 ![Události projektu sady Visual Studio](../../extensibility/internals/media/projectevents.gif "ProjectEvents")  
Model automatizace pro události  
  
 Třída `CProjectEventsContainer` reprezentuje zdrojový objekt pro BscProjectsEvents, zatímco `CProjectItemsEventsContainer` představuje zdrojový objekt pro BscProjectItemsEvents.  
  
 Ve většině případů je nutné vrátit nový objekt pro každou žádost o událost, protože většina objektů události vezme objekt Filter. Při vyvolání události zkontrolujte tento filtr a ověřte, zda je volána obslužná rutina události.  
  
 AutomationEvents. h a AutomationEvents. cpp obsahují deklarace a implementace tříd v následující tabulce.  
  
|Třída|Popis|  
|-----------|-----------------|  
|`CAutomationEvents`|Implementuje objekt kořene události, který byl načten z `DTE.Events` objektu.|  
|`CProjectsEventsContainer` a `CProjectItemsEventsContainer`|Implementujte zdrojové objekty události, které aktivují příslušné události.|  
  
 Následující příklad kódu ukazuje, jak reagovat na požadavek na objekt události.  
  
```cpp#  
STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
{  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
    if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)   
        //Is the requested name our Projects object?  
    {  
        return GetAutomationProjects(ppIDispatch);  
        // Gets our Projects object.  
    }  
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        //Is the requested name our ProjectsEvents object?  
    {  
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
          // Gets our ProjectEvents object.  
    }  
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  //Is the requested name our ProjectsItemsEvents object?  
    {  
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
          // Gets our ProjectItemsEvents object.  
    }  
    return E_INVALIDARG;  
}  
```  
  
 Ve výše uvedeném kódu `g_wszAutomationProjects` je název kolekce projektu ("FigProjects"), `g_wszAutomationProjectsEvents` ("FigProjectsEvents") a `g_wszAutomationProjectItemsEvents` ("FigProjectItemEvents") jsou názvy událostí projektu a události položek projektu, které jsou zdrojem z implementace VSPackage.  
  
 Objekty událostí jsou načteny ze stejného centrálního umístění `DTE.Events` objektu. Tímto způsobem jsou všechny objekty událostí seskupené dohromady, aby koncový uživatel nemusel procházet celý objektový model a najít konkrétní událost. To vám také umožní poskytovat konkrétní objekty VSPackage, a ne vyžadovat, abyste implementovali vlastní kód pro události v rámci systému. Nicméně pro koncového uživatele, který musí najít událost pro vaše `ProjectItem` rozhraní, není okamžitě jasné, ze kterého je objekt události načten.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>   
 [Ukázky VSSDK](../../misc/vssdk-samples.md)
