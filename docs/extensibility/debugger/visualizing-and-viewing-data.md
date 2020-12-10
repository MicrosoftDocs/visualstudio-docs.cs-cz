---
title: Vizualizace a zobrazování dat | Microsoft Docs
description: Naučte se, jak typy vizualizací a vlastní čtenáři prezentují data vývojáři. Vyhodnocovací filtr výrazů podporuje vizualizace typu třetích stran.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 856788546e10e69a8bb7e2787558505937f9effd
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995444"
---
# <a name="visualizing-and-viewing-data"></a>Vizualizace a zobrazování dat
Typy vizualizací a vlastní čtenáři prezentují data způsobem, který je pro vývojáře snadno smysluplný. Vyhodnocovací filtr výrazů (EE) může podporovat vizualizace typu třetích stran a poskytovat vlastní diváky.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Určuje, kolik typů vizualizací a vlastních prohlížečů je přidruženo k typu objektu voláním metody [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) . Pokud je k dispozici alespoň jeden Vizualizér typu nebo vlastní prohlížeč, aplikace Visual Studio zavolá metodu [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) , aby načetla seznam těchto vizualizují a prohlížečů (ve skutečnosti seznam s implementuje vizualizace a prohlížeče) a prezentuje je uživateli.

## <a name="supporting-type-visualizers"></a>Podpora typů vizualizací
 Existuje mnoho rozhraní, které musí v EE implementovat pro podporu typů vizualizací. Tato rozhraní lze rozdělit do dvou hlavních kategorií: rozhraní, která uvádějí typy vizualizací a rozhraní, které přistupují k datům vlastností.

### <a name="listing-type-visualizers"></a>Výpis typů vizualizací
 EE podporuje výpisy typů, které jsou v implementaci `IDebugProperty3::GetCustomViewerCount` a `IDebugProperty3::GetCustomViewerList` . Tyto metody přejdou volání odpovídajících metod [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) a [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).

 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) se získá voláním [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Tato metoda vyžaduje rozhraní [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) , které je získáno z rozhraní [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) předaného do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService` vyžaduje také rozhraní [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) a [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) , která byla předána `IDebugParsedExpression::EvaluateSync` . Konečné rozhraní potřebné k vytvoření `IEEVisualizerService` rozhraní je rozhraní [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) , které v et implementuje. Toto rozhraní umožňuje provádět změny ve vizuální vlastnosti. Všechna data vlastnosti jsou zapouzdřena v rozhraní [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) , které je také implementováno v EE.

### <a name="accessing-property-data"></a>Přístup k datům vlastností
 Přístup k datům vlastností se provádí prostřednictvím rozhraní [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) . Chcete-li získat toto rozhraní, Visual Studio zavolá [QueryInterface](/cpp/atl/queryinterface) na objekt Property, aby získal rozhraní [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) (implementované na stejném objektu, který implementuje rozhraní [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) ) a poté volá metodu [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) pro získání `IPropertyProxyEESide` rozhraní.

 Všechna data předaná a odcházející z `IPropertyProxyEESide` rozhraní jsou zapouzdřena v rozhraní [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) . Toto rozhraní představuje pole bajtů a je implementováno v rámci sady Visual Studio i v EE. Když je třeba změnit data vlastnosti, aplikace Visual Studio vytvoří `IEEDataStorage` objekt s novými daty a volá [funkce CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) s tímto datovým objektem, aby získal nový `IEEDataStorage` objekt, který je zase předán [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) za účelem aktualizace dat vlastnosti. `IPropertyProxyEESide::CreateReplacementObject` umožňuje službě EE vytvořit instanci své vlastní třídy, která implementuje `IEEDataStorage` rozhraní.

## <a name="supporting-custom-viewers"></a>Podpora vlastních prohlížečů
 Příznak `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` je nastaven v `dwAttrib` poli struktury [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) (vrácený voláním metody [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)), aby označoval, že k objektu je přidružen vlastní prohlížeč. Pokud je tento příznak nastaven, sada Visual Studio získá rozhraní [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) z rozhraní [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) pomocí [QueryInterface](/cpp/atl/queryinterface).

 Pokud uživatel vybere vlastní prohlížeč, Visual Studio vytvoří instanci vlastního prohlížeče pomocí prohlížeče `CLSID` zadaného `IDebugProperty3::GetCustomViewerList` metodou. Visual Studio potom zavolá [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) , aby zobrazila hodnotu pro uživatele.

 Normálně `IDebugCustomViewer::DisplayValue` prezentuje zobrazení dat jen pro čtení. Aby bylo možné v datech měnit, musí v EE být implementováno vlastní rozhraní, které podporuje změnu dat objektu vlastnosti. `IDebugCustomViewer::DisplayValue`Metoda používá toto vlastní rozhraní pro podporu změny dat. Metoda hledá vlastní rozhraní v `IDebugProperty2` rozhraní předaném jako `pDebugProperty` argument.

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Podpora vizualizací typů i vlastních prohlížečů
 EE může podporovat jak vizualizace typu, tak i vlastní prohlížeče v metodách [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) a [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) . V poli EE se za prvé přidá počet vlastních návštěvníků, na které odkazuje hodnota vrácená metodou [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) . Sekunda EE připojí vlastní `CLSID` diváky k seznamu vrácenému metodou [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) .

## <a name="see-also"></a>Viz také
- [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md)
- [Vizualizér typů a vlastní prohlížeč](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
