---
title: Vystavení událostí v sadě Visual Studio SDK | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 48f1e0ea0dcd07bbc26fc89d5c61a6a5941d4727
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708491"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Vystavit události v sadě Visual Studio SDK
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]umožňuje zdroj událostí pomocí automatizace. Doporučujeme, abyste zdroje události pro projekty a položky projektu.

 Události jsou načteny příjemci <xref:EnvDTE.DTEClass.Events%2A> automatizace z objektu nebo <xref:EnvDTE.DTEClass.GetObject%2A> `GetObject("EventObjectName")`(například). Prostředí volá `IDispatch::Invoke` pomocí `DISPATCH_METHOD` příznaků `DISPATCH_PROPERTYGET` nebo vrátit událost.

 Následující proces vysvětluje, jak jsou vráceny události specifické pro VSPackage.

1. Prostředí se spustí.

2. Čte z registru všechny názvy hodnot pod **Automation**, **AutomationEvents**a **AutomationProperties** klíče všech VSPackages a ukládá tyto názvy v tabulce.

3. Spotřebitel automatizace volání, v `DTE.Events.AutomationProjectsEvents` `DTE.Events.AutomationProjectItemsEvents`tomto příkladu nebo .

4. Prostředí najde parametr řetězce v tabulce a načte odpovídající VSPackage.

5. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodu pomocí názvu předaný ve volání; v tomto `AutomationProjectsEvents` příkladu, nebo `AutomationProjectItemsEvents`.

6. VSPackage vytvoří kořenový objekt, který `get_AutomationProjectsEvents` `get_AutomationProjectItemEvents` má metody, jako je například a a pak vrátí ukazatel IDispatch na objekt.

7. Prostředí volá příslušnou metodu založenou na názvu předaném do volání automatizace.

8. Metoda `get_` vytvoří jiný objekt události založený na IDispatch, který implementuje `IConnectionPointContainer` rozhraní i `IConnectionPoint` rozhraní a vrátí `IDispatchpointer` objektu.

   Chcete-li vystavit událost pomocí automatizace, musíte reagovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> a sledovat řetězce, které přidáte do registru. V ukázce základního projektu jsou řetězce *BscProjectsEvents* a *BscProjectItemsEvents*.

## <a name="registry-entries-from-the-basic-project-sample"></a>Položky registru z ukázky základního projektu
 Tato část ukazuje, kde přidat hodnoty událostí automatizace do registru.

 **[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Balíčky\\<PkgGUID\>\AutomationEvents]**

 **AutomationProjectEvents** = `AutomationProjectEvents` Vrátí objekt.

 **AutomationProjectItemEvents** = `AutomationProjectItemsEvents` Vrátí objekt.

|Name (Název)|Typ|Rozsah|Popis|
|----------|----------|-----------|-----------------|
|Výchozí (@)|REG_SZ|Nepoužitý|Nepoužívá se. Datové pole můžete použít pro dokumentaci.|
|*AutomationProjectsEvents*|REG_SZ|Název objektu události.|Relevantní je pouze název klíče. Datové pole můžete použít pro dokumentaci.<br /><br /> Tento příklad pochází z ukázky základního projektu.|
|*AutomationProjectItemEvents*|REG_SZ|Název objektu události|Relevantní je pouze název klíče. Datové pole můžete použít pro dokumentaci.<br /><br /> Tento příklad pochází z ukázky základního projektu.|

 Pokud některý z vašich objektů události jsou požadovány příjemce automatizace, vytvořte kořenový objekt, který má metody pro všechny události, které podporuje Váš VSPackage. Prostředí volá příslušnou `get_` metodu pro tento objekt. Například pokud `DTE.Events.AutomationProjectsEvents` je volána, `get_AutomationProjectsEvents` metoda na kořenový objekt je vyvolána.

 ![Události projektu visual studia](../../extensibility/internals/media/projectevents.gif "Události projektu") Model automatizace pro události

 Třída `CProjectEventsContainer` představuje zdrojový objekt pro *BscProjectsEvents*a `CProjectItemsEventsContainer` představuje zdrojový objekt pro *BscProjectItemsEvents*.

 Ve většině případů je nutné vrátit nový objekt pro každý požadavek na událost, protože většina objektů události převzít objekt filtru. Při vyvolaní události zkontrolujte tento filtr a ověřte, zda je volána obslužná rutina události.

 *AutomationEvents.h* a *AutomationEvents.cpp* obsahují deklarace a implementace tříd v následující tabulce.

|Třída|Popis|
|-----------|-----------------|
|`CAutomationEvents`|Implementuje kořenový objekt události `DTE.Events` načtený z objektu.|
|`CProjectsEventsContainer` a `CProjectItemsEventsContainer`|Implementujte objekty zdroje událostí, které sfire odpovídající události.|

 Následující příklad kódu ukazuje, jak reagovat na požadavek na objekt události.

```cpp
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

 Ve výše uvedeném `g_wszAutomationProjects` kódu je název kolekce projektu (*FigProjects*) `g_wszAutomationProjectsEvents` (*FigProjectsEvents*) a `g_wszAutomationProjectItemsEvents` (*FigProjectItemEvents*) jsou názvy událostí projektu a událostí položek projektu, které jsou získávány z implementace VSPackage.

 Objekty událostí jsou načteny ze `DTE.Events` stejného centrálního umístění, objektu. Tímto způsobem jsou všechny objekty událostí seskupeny tak, aby koncový uživatel nemusel procházet celý objektový model, aby našel konkrétní událost. To také umožňuje poskytnout konkrétní Objekty VSPackage, namísto nutnosti implementovat vlastní kód pro události celého systému. Však pro koncového uživatele, který musí `ProjectItem` najít událost pro vaše rozhraní, není okamžitě jasné, odkud je načten objekt události.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
