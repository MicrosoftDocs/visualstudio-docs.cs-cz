---
title: Zveřejňování událostí v sadě Visual Studio SDK | Dokumentace Microsoftu
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
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4c65220114328f1630ef9c9457a3c971b730957b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761484"
---
# <a name="exposing-events-in-the-visual-studio-sdk"></a>Zveřejňování událostí v sadě Visual Studio SDK
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Umožňuje zdroje událostí pomocí služby automation. Doporučujeme vám, že zdroj události pro projekty a položky projektu.  
  
 Události jsou načteny spotřebiteli automatizace z <xref:EnvDTE.DTEClass.Events%2A> objektu nebo <xref:EnvDTE.DTEClass.GetObject%2A> ("EventObjectName"). Prostředí volá `IDispatch::Invoke` pomocí `DISPATCH_METHOD` nebo `DISPATCH_PROPERTYGET` příznaky vrátit událost.  
  
 Následující postup vysvětluje, jak jsou vráceny VSPackage konkrétní události.  
  
1. Spustí se prostředí.  
  
2. Načte všechny názvy hodnot klíčů služby Automation, AutomationEvents a AutomationProperties všechny balíčky VSPackages z registru a ukládá názvy v tabulce.  
  
3. Spotřebitel automatizace volá, v tomto příkladu `DTE.Events.AutomationProjectsEvents` nebo `DTE.Events.AutomationProjectItemsEvents`.  
  
4. Prostředí parametr řetězec najde v tabulce a načte odpovídající VSPackage.  
  
5. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metody pomocí názvu předané ve volání; v tomto příkladu AutomationProjectsEvents nebo AutomationProjectItemsEvents.  
  
6. Vytvoří kořenový objekt, který obsahuje metody, jako sady VSPackage `get_AutomationProjectsEvents` a `get_AutomationProjectItemEvents` a vrátí ukazatel rozhraní IDispatch objektu.  
  
7. Prostředí volá odpovídající metodu na základě názvu předaná do volání služby automation.  
  
8. `get_` Metoda vytvoří jiné události rozhraní IDispatch objekt, který implementuje oba `IConnectionPointContainer` rozhraní a `IConnectionPoint` rozhraní a vrací IDispatchpointer na objekt.  
  
   Vystavení události pomocí automatizace, musí odpovědět na <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> a sledujte pro řetězce, které přidáte do registru. V ukázce základního projektu jsou řetězce "BscProjectsEvents" a "BscProjectItemsEvents".  
  
## <a name="registry-entries-from-the-basic-project-sample"></a>Položky registru z ukázky základního projektu  
 V této části ukazuje, kde chcete-li přidat hodnoty událostí automatizace do registru.  
  
 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\< PkgGUID\>\AutomationEvents]  
  
 "AutomationProjectEvents"="vrátí objekt AutomationProjectEvents"  
  
 "AutomationProjectItemEvents"="vrátí objekt AutomationProjectItemsEvents"  
  
|Název|Typ|Rozsah|Popis|  
|----------|----------|-----------|-----------------|  
|Výchozí (@)|REG_SZ|Nepoužitý|Nevyužité. Datové pole můžete použít pro dokumentaci.|  
|AutomationProjectsEvents|REG_SZ|Název objektu události.|Pouze název klíče je relevantní. Datové pole můžete použít pro dokumentaci.<br /><br /> V tomto příkladu pochází z ukázkové základního projektu.|  
|AutomationProjectItemEvents|REG_SZ|Název objektu události|Pouze název klíče je relevantní. Datové pole můžete použít pro dokumentaci.<br /><br /> V tomto příkladu pochází z ukázkové základního projektu.|  
  
 Když některé objekty událostí jsou požadovány klientem služby automation, vytvořte kořenový objekt, který má metody pro událost, která podporuje vaše VSPackage. Prostředí volá odpovídající `get_` metoda u tohoto objektu. Například pokud `DTE.Events.AutomationProjectsEvents` je volána, `get_AutomationProjectsEvents` vyvolání metody na kořenový objekt.  
  
 ![Události projektu sady Visual Studio](../../extensibility/internals/media/projectevents.gif "ProjectEvents")  
Model automatizace pro události  
  
 Třída `CProjectEventsContainer` reprezentuje zdrojový objekt pro BscProjectsEvents, zatímco `CProjectItemsEventsContainer` reprezentuje zdrojový objekt pro BscProjectItemsEvents.  
  
 Ve většině případů musí vrátit objekt pro každý požadavek na události, protože většinu objektů událostí získat objekt filtru. Pokud jste vyvolat události, zkontrolujte tento filtr k ověření, že obslužná rutina události je volána.  
  
 AutomationEvents.h a AutomationEvents.cpp obsahují deklarace a implementaci tříd v následující tabulce.  
  
|Třída|Popis|  
|-----------|-----------------|  
|`CAutomationEvents`|Implementuje objekt kořenového události získaných `DTE.Events` objektu.|  
|`CProjectsEventsContainer` a `CProjectItemsEventsContainer`|Implementace objektů zdroj událostí, které se aktivují odpovídající události.|  
  
 Následující příklad kódu ukazuje, jak reagovat na požadavek pro objekt události.  
  
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
  
 Ve výše uvedeném kódu `g_wszAutomationProjects` je název vaší kolekce projektu ("FigProjects"), `g_wszAutomationProjectsEvents` ("FigProjectsEvents") a `g_wszAutomationProjectItemsEvents` ("FigProjectItemEvents") jsou názvy projektových událostí a události, které pocházejí z položky projektu vaší Implementace VSPackage.  
  
 Objekty událostí jsou načteny ze stejného centrální umístění, `DTE.Events` objektu. Tímto způsobem všechny objekty událostí jsou seskupené dohromady tak, aby koncový uživatel nebude muset procházet celý objekt modelu najít konkrétní události. To také umožňuje poskytovat konkrétní objekty VSPackage, nemusíte mít můžete implementovat vlastní kód pro systémové události. Ale pro koncového uživatele, kteří musí najít událost pro vaše `ProjectItem` rozhraní, není okamžitě jasné, ze kterých se tento objekt událost načítají.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>   
 [Ukázky VSSDK](../../misc/vssdk-samples.md)

