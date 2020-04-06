---
title: Vizualizace a zobrazení dat | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 2b5f984e6c6a3c1c8f3835dfa93a8679ae16680a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712380"
---
# <a name="visualizing-and-viewing-data"></a>Vizualizace a zobrazení dat
Zadejte vizualizéry a vlastní prohlížeče prezentují data způsobem, který je pro vývojáře rychle smysluplný. Vyhodnocení výrazu (EE) může podporovat vizualizéry typu třetích stran a také poskytovat vlastní prohlížeče.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]určuje, kolik vizualizérů typu a vlastních prohlížečů je přidruženo k typu objektu voláním metody [GetCustomViewerCount.](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) Pokud je k dispozici alespoň jeden typ vizualizéru nebo vlastní prohlížeč, Visual Studio volá [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) metoda načíst seznam těchto vizualizérů a prohlížečů (ve skutečnosti seznam s, který implementuje vizualizéry a prohlížeče) a představuje je uživateli.

## <a name="supporting-type-visualizers"></a>Podpůrné vizualizéry typů
 Existuje několik rozhraní, které ee musí implementovat pro podporu typu vizualizéry. Tato rozhraní lze rozdělit do dvou širokých kategorií: rozhraní, která seznam typu vizualizéry a rozhraní, které přístup k datům vlastností.

### <a name="listing-type-visualizers"></a>Výpis vizualizérů typu
 EE podporuje výpis typu vizualizéry `IDebugProperty3::GetCustomViewerCount` `IDebugProperty3::GetCustomViewerList`v jeho provádění a . Tyto metody předat volání odpovídající metody [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) a [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).

 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) je získán voláním [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Tato metoda vyžaduje rozhraní [IDebugBinder3,](../../extensibility/debugger/reference/idebugbinder3.md) které je získáno z rozhraní [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) předané [hodnotě EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService`také vyžaduje [rozhraní IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) a [IDebugAddress,](../../extensibility/debugger/reference/idebugaddress.md) `IDebugParsedExpression::EvaluateSync`které byly předány . Konečné rozhraní potřebné k `IEEVisualizerService` vytvoření rozhraní je [rozhraní IEEVisualizerDataProvider,](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) které implementuje EE. Toto rozhraní umožňuje změny, které mají být provedeny na vlastnost, která je vizualizována. Všechna data vlastností jsou zapouzdřena v rozhraní [IDebugObject,](../../extensibility/debugger/reference/idebugobject.md) které je také implementováno EE.

### <a name="accessing-property-data"></a>Přístup k datům vlastností
 Přístup k datům vlastností se provádí prostřednictvím rozhraní [IPropertyProxyEESide.](../../extensibility/debugger/reference/ipropertyproxyeeside.md) Chcete-li získat toto rozhraní, Visual Studio volá [QueryInterface](/cpp/atl/queryinterface) na objekt vlastnosti získat rozhraní [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) (implementováno na stejný objekt, který `IPropertyProxyEESide` implementuje rozhraní [IDebugProperty3)](../../extensibility/debugger/reference/idebugproperty3.md) a pak volá [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) metoda získat rozhraní.

 Všechna data předávaná do a z `IPropertyProxyEESide` rozhraní jsou zapouzdřena v rozhraní [IEEDataStorage.](../../extensibility/debugger/reference/ieedatastorage.md) Toto rozhraní představuje pole bajtů a je implementováno visual studio a EE. Při změně dat vlastnosti Visual Studio vytvoří `IEEDataStorage` objekt, který obsahuje nová data a volá [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) s `IEEDataStorage` tímto datovým objektem, aby získal nový objekt, který je zase předán [inplaceupdateobject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) aktualizovat data vlastnosti. `IPropertyProxyEESide::CreateReplacementObject`umožňuje EE k vytvoření instance vlastní třídy, `IEEDataStorage` která implementuje rozhraní.

## <a name="supporting-custom-viewers"></a>Podpora vlastních prohlížečů
 Příznak `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` je nastaven `dwAttrib` v poli [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) struktury (vrácené [volánígetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) k označení, že objekt má vlastní prohlížeč s ním spojené. Pokud je tento příznak nastaven, Visual Studio získá rozhraní [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) z rozhraní [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) pomocí [queryinterface](/cpp/atl/queryinterface).

 Pokud uživatel vybere vlastní prohlížeč, Visual Studio instance vlastní prohlížeč pomocí `CLSID` prohlížeče dodané `IDebugProperty3::GetCustomViewerList` metodou. Visual Studio pak volá [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) zobrazit hodnotu pro uživatele.

 Obvykle `IDebugCustomViewer::DisplayValue` představuje zobrazení dat jen pro čtení. Chcete-li povolit změny dat, musí EE implementovat vlastní rozhraní, které podporuje změnu dat na objektvlastnosti. Metoda `IDebugCustomViewer::DisplayValue` používá toto vlastní rozhraní pro podporu změny dat. Metoda hledá vlastní rozhraní na `IDebugProperty2` rozhraní předané `pDebugProperty` jako argument.

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Podpora vizualizérů typů i vlastních prohlížečů
 EE může podporovat vizualizéry typu i vlastní prohlížeče v [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) a [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) metody. Nejprve EE přidá počet vlastních prohlížečů, které dodává na hodnotu vrácenou metodou [GetCustomViewerCount.](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) Za druhé, EE `CLSID`připojí s své vlastní prohlížeče do seznamu vrácené [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) metoda.

## <a name="see-also"></a>Viz také
- [Ladění úkolů](../../extensibility/debugger/debugging-tasks.md)
- [Typ vizualizéru a vlastního prohlížeče](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
