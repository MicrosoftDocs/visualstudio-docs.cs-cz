---
title: Vystavení událostí v Visual Studio SDK | Microsoft Docs
description: Seznamte se s Visual Studio SDK a položkami registru, které zpřístupňuje události pro projekty a položky projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 99298329b969df3b9d7dbb46a3f4b9e7d4ed7091
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898328"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Vystavení událostí v Visual Studio SDK
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] umožňuje vytvářet události pomocí automatizace. Pro projekty a položky projektu doporučujeme za zdroj událostí.

 Události se načítá spotřebiteli automatizace z objektu nebo <xref:EnvDTE.DTEClass.Events%2A> <xref:EnvDTE.DTEClass.GetObject%2A> (například `GetObject("EventObjectName")` ). Prostředí volá `IDispatch::Invoke` pomocí příznaků nebo , aby `DISPATCH_METHOD` `DISPATCH_PROPERTYGET` vrátilo událost.

 Následující proces vysvětluje, jak se vrací události specifické pro balíček VSPackage.

1. Spustí se prostředí.

2. Z registru načte všechny názvy hodnot v klíčích **Automation**, **AutomationEvents** a **AutomationProperties** všech VSPackages a tyto názvy uloží do tabulky.

3. Příjemce automatizace volá v tomto příkladu `DTE.Events.AutomationProjectsEvents` nebo `DTE.Events.AutomationProjectItemsEvents` .

4. Prostředí najde v tabulce parametr řetězce a načte odpovídající balíček VSPackage.

5. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodu pomocí názvu předaního ve volání ; v tomto příkladu `AutomationProjectsEvents` nebo `AutomationProjectItemsEvents` .

6. Balíček VSPackage vytvoří kořenový objekt, který obsahuje metody, jako je a , a poté vrátí ukazatel `get_AutomationProjectsEvents` `get_AutomationProjectItemEvents` IDispatch na objekt.

7. Prostředí volá příslušnou metodu na základě názvu předaných do volání automatizace.

8. Metoda `get_` vytvoří další objekt události založený na IDispatch, který implementuje rozhraní i rozhraní a vrací objekt do objektu `IConnectionPointContainer` `IConnectionPoint` `IDispatchpointer` .

   Pokud chcete událost zveřejnit pomocí automatizace, musíte reagovat na řetězce, které přidáte do registru, a sledovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> je. V ukázce základního projektu jsou řetězce *BscProjectsEvents* a *BscProjectItemsEvents*.

## <a name="registry-entries-from-the-basic-project-sample"></a>Položky registru z ukázky základního projektu
 Tato část ukazuje, kam do registru přidat hodnoty událostí automatizace.

 **[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\<PkgGUID \> \AutomationEvents]**

 **AutomationProjectEvents** = Vrátí `AutomationProjectEvents` objekt .

 **AutomationProjectItemEvents** = Vrátí `AutomationProjectItemsEvents` objekt .

|Název|Typ|Rozsah|Description|
|----------|----------|-----------|-----------------|
|Výchozí (@)|REG_SZ|Nepoužitý|Nepoužívá se. K dokumentaci můžete použít datové pole.|
|*AutomationProjectsEvents*|REG_SZ|Název objektu události.|Relevantní je pouze název klíče. K dokumentaci můžete použít datové pole.<br /><br /> Tento příklad pochází z ukázky základního projektu.|
|*AutomationProjectItemEvents*|REG_SZ|Název objektu události|Relevantní je pouze název klíče. K dokumentaci můžete použít datové pole.<br /><br /> Tento příklad pochází z ukázky základního projektu.|

 Pokud příjemce automatizace požaduje některý z objektů událostí, vytvořte kořenový objekt, který obsahuje metody pro všechny události, které váš balíček VSPackage podporuje. Prostředí volá pro tento `get_` objekt příslušnou metodu. Pokud je například `DTE.Events.AutomationProjectsEvents` volána metoda `get_AutomationProjectsEvents` u kořenového objektu, je vyvolána.

 ![Visual Studio událostí projektu](../../extensibility/internals/media/projectevents.gif "Události projektu") Model automatizace pro události

 Třída představuje `CProjectEventsContainer` zdrojový objekt pro *BscProjectsEvents* a představuje zdrojový `CProjectItemsEventsContainer` objekt pro *BscProjectItemsEvents*.

 Ve většině případů je nutné vrátit nový objekt pro každý požadavek události, protože většina objektů událostí vezme objekt filtru. Když událost vyžádáte, zkontrolujte tento filtr a ověřte, že se volá obslužná rutina události.

 *Soubory AutomationEvents.h* a *AutomationEvents.cpp* obsahují deklarace a implementace tříd v následující tabulce.

|Třída|Popis|
|-----------|-----------------|
|`CAutomationEvents`|Implementuje kořenový objekt události načtený z `DTE.Events` objektu .|
|`CProjectsEventsContainer` a `CProjectItemsEventsContainer`|Implementujte objekty zdroje událostí, které vyhodí odpovídající události.|

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

 Ve výše uvedeném kódu je název vaší kolekce projektu `g_wszAutomationProjects` *(ProjectProjects*), `g_wszAutomationProjectsEvents` *(ProjectProjectsEvents*) a `g_wszAutomationProjectItemsEvents` *(ProjectProjectItemEvents*) jsou názvy událostí projektu a položek projektu, které jsou zdrojem z vaší implementace VSPackage.

 Objekty událostí se načítá ze stejného centrálního umístění, objektu `DTE.Events` . Tímto způsobem jsou všechny objekty událostí seskupeny dohromady, takže koncový uživatel nemusí procházet celý objektový model, aby našel konkrétní událost. To také umožňuje zadat konkrétní objekty VSPackage místo toho, abyste pro události celého systému vyžadovat vlastní kód. Pro koncového uživatele, který musí najít událost pro vaše rozhraní, však není hned jasné, odkud je `ProjectItem` objekt události načten.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
