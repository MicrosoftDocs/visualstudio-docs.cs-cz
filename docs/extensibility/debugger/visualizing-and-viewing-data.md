---
title: Vizualizace a zobrazení dat | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 50325281fcca92394df5db28cc590cfa1e85f651
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276790"
---
# <a name="visualizing-and-viewing-data"></a>Vizualizace a zobrazení dat
Vizualizérů typů a vlastních prohlížečů k dispozici data způsobem, který je rychle smysl pro vývojáře. Chyba při vyhodnocování výrazu (EE) můžete vizualizérů typů třetích stran taky zadat vlastní vlastních prohlížečů.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Určuje, kolik vizualizérů typů a vlastních prohlížečů jsou spojeny s typem objektu voláním [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) metody. Pokud je alespoň jeden typ vizualizéru nebo vlastní prohlížeč k dispozici, zavolá sady Visual Studio [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) metodu pro načtení seznamu těchto vizualizérů a prohlížeče (ve skutečnosti, seznam, které implementuje vizualizérů a prohlížeče) a zobrazí uživateli.  
  
## <a name="supporting-type-visualizers"></a>Podpora vizualizérů typů  
 Existuje mnoho rozhraní, která EE musí implementovat pro podporu vizualizérů typů. Tato rozhraní je možné rozdělit do dvou rozsáhlých kategorií: rozhraní, které uvádějí vizualizérů typů a rozhraní, která přístup k datům vlastnost.  
  
### <a name="listing-type-visualizers"></a>Výpis vizualizérů typů  
 EE podporuje výpis vizualizérů typů v jeho provádění `IDebugProperty3::GetCustomViewerCount` a `IDebugProperty3::GetCustomViewerList`. Tyto metody proběhly úspěšně volání metody odpovídající [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) a [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).  
  
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) je získán voláním [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Tato metoda vyžaduje [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) rozhraní, které se získává z [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) předán rozhraní [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService` také vyžaduje [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) a [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) rozhraní, které byly předány `IDebugParsedExpression::EvaluateSync`. Poslední rozhraní potřebný k vytvoření `IEEVisualizerService` rozhraní je [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) rozhraní, která implementuje EE. Toto rozhraní umožňuje, aby změny provést, vlastnosti, který je právě vizualizován. Všechny vlastnosti data zapouzdřena v [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) rozhraní, které je také implementováno pomocí EE.  
  
### <a name="accessing-property-data"></a>Přístup k datům vlastnost  
 Přístup k datům vlastnost se provádí prostřednictvím [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) rozhraní. Pro získání toto rozhraní, sady Visual Studio volá [QueryInterface](/cpp/atl/queryinterface) na vlastnosti objektu zobrazíte [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) rozhraní (implementovat na stejný objekt, který implementuje [ IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) rozhraní) a pak zavolá [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) metodu k získání `IPropertyProxyEESide` rozhraní.  
  
 Všechna data předaná do a z celkového počtu `IPropertyProxyEESide` rozhraní, je zapouzdřena v [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) rozhraní. Toto rozhraní představuje pole bajtů a je implementována pomocí sady Visual Studio a EE. Vlastnosti dat se změnit, vytvoří Visual Studio `IEEDataStorage` objektu, že nová data a volání [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) s tímto objektem data, aby bylo možné získat nový `IEEDataStorage` objekt, který je dále Předaný [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) k aktualizaci dat vlastnost. `IPropertyProxyEESide::CreateReplacementObject` Umožňuje EE k vytvoření vlastní instance třídy, která implementuje `IEEDataStorage` rozhraní.  
  
## <a name="supporting-custom-viewers"></a>Podpora vlastních prohlížečů  
 Příznak `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` je nastavena v `dwAttrib` pole [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) strukturu (vrácený voláním [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) k označení, že objekt má vlastní prohlížeč související s ním. Pokud je tento příznak nastaven, získá sady Visual Studio [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) rozhraní z [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) rozhraní pomocí [QueryInterface](/cpp/atl/queryinterface).  
  
 Pokud si uživatel vybere vlastní prohlížeč, vytvoří Visual Studio vlastní vieweru. použijte v prohlížeči `CLSID` poskytnutých `IDebugProperty3::GetCustomViewerList` metody. Visual Studio pak zavolá [položky DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) k zobrazení hodnoty pro uživatele.  
  
 Za normálních okolností `IDebugCustomViewer::DisplayValue` představuje zobrazení dat jen pro čtení. Povolit změny dat, musí EE implementovat vlastní rozhraní, která podporuje se měnících dat na vlastnost objektu. `IDebugCustomViewer::DisplayValue` Metoda používá toto vlastní rozhraní pro podporu se měnícími daty. Metoda hledá vlastní rozhraní na `IDebugProperty2` rozhraní předaný jako `pDebugProperty` argument.  
  
## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Podpora vizualizérů typů a vlastních prohlížečů  
 EE může podporovat vizualizérů typů a vlastních prohlížečů v [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) a [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) metody. Nejprve EE přidá počet vlastních prohlížečů, které je poskytnutí hodnoty vrácené [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) metody. Za druhé, připojí EE `CLSID`s vlastním vlastních prohlížečů do seznamu vrácených [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) metody.  
  
## <a name="see-also"></a>Viz také:  
 [Ladění úloh](../../extensibility/debugger/debugging-tasks.md)   
 [Vizualizér typů a vlastní prohlížeč](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)