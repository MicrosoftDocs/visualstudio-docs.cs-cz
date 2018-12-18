---
title: DBG_ATTRIB_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 774bef7a3f28c973c9569544556d3033ede0093d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107735"
---
# <a name="dbgattribflags"></a>DBG_ATTRIB_FLAGS
Popisuje různé atributy pro [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nebo [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) rozhraní. Člen [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
#define DBG_ATTRIB_NONE                 0x0000000000000000,  
#define DBG_ATTRIB_ALL                  0x00000000ffffffff,  
  
// Attributes about the object itself  
  
#define DBG_ATTRIB_OBJ_IS_EXPANDABLE    0x0000000000000001,  
#define DBG_ATTRIB_OBJ_HAS_ID           0x0000000000000002,  
#define DBG_ATTRIB_OBJ_CAN_HAVE_ID      0x0000000000000004,  
  
// Attributes about the value of the object  
  
#define DBG_ATTRIB_VALUE_READONLY       0x0000000000000010,  
#define DBG_ATTRIB_VALUE_ERROR          0x0000000000000020,  
#define DBG_ATTRIB_VALUE_SIDE_EFFECT    0x0000000000000040,  
#define DBG_ATTRIB_OVERLOADED_CONTAINER 0x0000000000000080,  
#define DBG_ATTRIB_VALUE_BOOLEAN        0x0000000000000100,  
#define DBG_ATTRIB_VALUE_BOOLEAN_TRUE   0x0000000000000200,  
#define DBG_ATTRIB_VALUE_INVALID        0x0000000000000400,  
#define DBG_ATTRIB_VALUE_NAT            0x0000000000000800,  
#define DBG_ATTRIB_VALUE_AUTOEXPANDED   0x0000000000001000,  
#define DBG_ATTRIB_VALUE_TIMEOUT        0x0000000000002000,  
#define DBG_ATTRIB_VALUE_RAW_STRING     0x0000000000004000,  
#define DBG_ATTRIB_VALUE_CUSTOM_VIEWER  0x0000000000008000,  
  
// Attributes about field access types for the object  
  
#define DBG_ATTRIB_ACCESS_NONE          0x0000000000010000,  
#define DBG_ATTRIB_ACCESS_PUBLIC        0x0000000000020000,  
#define DBG_ATTRIB_ACCESS_PRIVATE       0x0000000000040000,  
#define DBG_ATTRIB_ACCESS_PROTECTED     0x0000000000080000,  
#define DBG_ATTRIB_ACCESS_FINAL         0x0000000000100000,  
#define DBG_ATTRIB_ACCESS_ALL           0x00000000001f0000,  
  
// Attributes for the storage types of the object  
  
#define DBG_ATTRIB_STORAGE_NONE         0x0000000001000000,  
#define DBG_ATTRIB_STORAGE_GLOBAL       0x0000000002000000,  
#define DBG_ATTRIB_STORAGE_STATIC       0x0000000004000000,  
#define DBG_ATTRIB_STORAGE_REGISTER     0x0000000008000000,  
#define DBG_ATTRIB_STORAGE_ALL          0x000000000f000000,  
  
// Attributes for the type modifiers on the object  
  
#define DBG_ATTRIB_TYPE_NONE            0x0000000100000000,  
#define DBG_ATTRIB_TYPE_VIRTUAL         0x0000000200000000,  
#define DBG_ATTRIB_TYPE_CONSTANT        0x0000000400000000,  
#define DBG_ATTRIB_TYPE_SYNCHRONIZED    0x0000000800000000,  
#define DBG_ATTRIB_TYPE_VOLATILE        0x0000001000000000,  
#define DBG_ATTRIB_TYPE_ALL             0x0000001f00000000,  
  
// Attributes that describe the type of object  
  
#define DBG_ATTRIB_DATA                 0x0000010000000000,  
#define DBG_ATTRIB_METHOD               0x0000020000000000,  
#define DBG_ATTRIB_PROPERTY             0x0000040000000000,  
#define DBG_ATTRIB_CLASS                0x0000080000000000,  
#define DBG_ATTRIB_BASECLASS            0x0000100000000000,  
#define DBG_ATTRIB_INTERFACE            0x0000200000000000,  
#define DBG_ATTRIB_INNERCLASS           0x0000400000000000,  
#define DBG_ATTRIB_MOSTDERIVED          0x0000800000000000,  
#define DBG_ATTRIB_CHILD_ALL            0x0000ff0000000000,  
  
// Miscellaneous attributes  
  
#define DBG_ATTRIB_MULTI_CUSTOM_VIEWERS 0x0001000000000000  
  
typedef UINT64 DBG_ATTRIB_FLAGS;  
```  
  
```csharp  
public const int DBG_ATTRIB_NONE                 = 0x0000000000000000,  
public const int DBG_ATTRIB_ALL                  = 0x00000000ffffffff,  
  
// Attributes about the object itself  
  
public const int DBG_ATTRIB_OBJ_IS_EXPANDABLE    = 0x0000000000000001,  
public const int DBG_ATTRIB_OBJ_HAS_ID           = 0x0000000000000002,  
public const int DBG_ATTRIB_OBJ_CAN_HAVE_ID      = 0x0000000000000004,  
  
// Attributes about the value of the object  
  
public const int DBG_ATTRIB_VALUE_READONLY       = 0x0000000000000010,  
public const int DBG_ATTRIB_VALUE_ERROR          = 0x0000000000000020,  
public const int DBG_ATTRIB_VALUE_SIDE_EFFECT    = 0x0000000000000040,  
public const int DBG_ATTRIB_OVERLOADED_CONTAINER = 0x0000000000000080,  
public const int DBG_ATTRIB_VALUE_BOOLEAN        = 0x0000000000000100,  
public const int DBG_ATTRIB_VALUE_BOOLEAN_TRUE   = 0x0000000000000200,  
public const int DBG_ATTRIB_VALUE_INVALID        = 0x0000000000000400,  
public const int DBG_ATTRIB_VALUE_NAT            = 0x0000000000000800,  
public const int DBG_ATTRIB_VALUE_AUTOEXPANDED   = 0x0000000000001000,  
public const int DBG_ATTRIB_VALUE_TIMEOUT        = 0x0000000000002000,  
public const int DBG_ATTRIB_VALUE_RAW_STRING     = 0x0000000000004000,  
public const int DBG_ATTRIB_VALUE_CUSTOM_VIEWER  = 0x0000000000008000,  
  
// Attributes about field access types for the object  
  
public const int DBG_ATTRIB_ACCESS_NONE          = 0x0000000000010000,  
public const int DBG_ATTRIB_ACCESS_PUBLIC        = 0x0000000000020000,  
public const int DBG_ATTRIB_ACCESS_PRIVATE       = 0x0000000000040000,  
public const int DBG_ATTRIB_ACCESS_PROTECTED     = 0x0000000000080000,  
public const int DBG_ATTRIB_ACCESS_FINAL         = 0x0000000000100000,  
public const int DBG_ATTRIB_ACCESS_ALL           = 0x00000000001f0000,  
  
// Attributes for the storage types of the object  
  
public const int DBG_ATTRIB_STORAGE_NONE         = 0x0000000001000000,  
public const int DBG_ATTRIB_STORAGE_GLOBAL       = 0x0000000002000000,  
public const int DBG_ATTRIB_STORAGE_STATIC       = 0x0000000004000000,  
public const int DBG_ATTRIB_STORAGE_REGISTER     = 0x0000000008000000,  
public const int DBG_ATTRIB_STORAGE_ALL          = 0x000000000f000000,  
  
// Attributes for the type modifiers on the object  
  
public const int DBG_ATTRIB_TYPE_NONE            = 0x0000000100000000,  
public const int DBG_ATTRIB_TYPE_VIRTUAL         = 0x0000000200000000,  
public const int DBG_ATTRIB_TYPE_CONSTANT        = 0x0000000400000000,  
public const int DBG_ATTRIB_TYPE_SYNCHRONIZED    = 0x0000000800000000,  
public const int DBG_ATTRIB_TYPE_VOLATILE        = 0x0000001000000000,  
public const int DBG_ATTRIB_TYPE_ALL             = 0x0000001f00000000,  
  
// Attributes that describe the type of object  
  
public const int DBG_ATTRIB_DATA                 = 0x0000010000000000,  
public const int DBG_ATTRIB_METHOD               = 0x0000020000000000,  
public const int DBG_ATTRIB_PROPERTY             = 0x0000040000000000,  
public const int DBG_ATTRIB_CLASS                = 0x0000080000000000,  
public const int DBG_ATTRIB_BASECLASS            = 0x0000100000000000,  
public const int DBG_ATTRIB_INTERFACE            = 0x0000200000000000,  
public const int DBG_ATTRIB_INNERCLASS           = 0x0000400000000000,  
public const int DBG_ATTRIB_MOSTDERIVED          = 0x0000800000000000,  
public const int DBG_ATTRIB_CHILD_ALL            = 0x0000ff0000000000,  
  
// Miscellaneous attributes  
  
public const int DBG_ATTRIB_MULTI_CUSTOM_VIEWERS = 0x0001000000000000  
```  
  
## <a name="members"></a>Členové  
 DBG_ATTRIB_NONE  
 Označuje žádné atributy.  
  
 DBG_ATTRIB_ALL  
 Označuje všechny atributy.  
  
 DBG_ATTRIB_OBJ_IS_EXPANDABLE  
 Určuje, že odkaz nebo vlastnost má podřízené objekty.  
  
 DBG_ATTRIB_OBJ_HAS_ID  
 Označuje, že ID pro tento objekt vytvořen.  
  
 DBG_ATTRIB_OBJ_CAN_HAVE_ID  
 Označuje, že ID pro tento objekt lze vytvořit.  
  
 DBG_ATTRIB_VALUE_READONLY  
 Označuje, že hodnota je jen pro čtení.  
  
 DBG_ATTRIB_VALUE_ERROR  
 Značí, zda je hodnota k chybě.  
  
 DBG_ATTRIB_VALUE_SIDE_EFFECT  
 Naznačuje, když vyhodnocení vedlejším účinkem.  
  
 DBG_ATTRIB_OVERLOADED_CONTAINER  
 Označuje, že tato vlastnost je skutečně kontejner přetížení.  
  
 DBG_ATTRIB_VALUE_BOOLEAN  
 Určuje, že je hodnota v `DEBUG_PROPERTY_INFO::bstrValue` je logická hodnota.  
  
 DBG_ATTRIB_VALUE_BOOLEAN_TRUE  
 Určuje, že je hodnota v `DEBUG_PROPERTY_INFO::bstrValue` je logická hodnota a `TRUE`.  
  
 DBG_ATTRIB_VALUE_INVALID  
 Určuje, že je hodnota v `DEBUG_PROPERTY_INFO::bstrValue` není platný.  
  
 DBG_ATTRIB_VALUE_NAT  
 Určuje, že je hodnota v `DEBUG_PROPERTY_INFO::bstrValue` je "*není co*" (NAT). NAT popisuje registraci v procesory Intel 64-bit označuje příznakem odložené spekulativní výjimky.  
  
 DBG_ATTRIB_VALUE_AUTOEXPANDED  
 Určuje, že je hodnota v `DEBUG_PROPERTY_INFO::bstrValue` byl pravděpodobně automaticky rozšířena.  
  
 DBG_ATTRIB_VALUE_TIMEOUT  
 Určuje, že zkušební verzi vypršel.  
  
 DBG_ATTRIB_VALUE_RAW_STRING  
 Určuje, že je hodnota v `DEBUG_PROPERTY_INFO::bstrValue` může být reprezentovaný Nezpracovaný řetězec.  
  
 DBG_ATTRIB_VALUE_CUSTOM_VIEWER  
 Označuje, že tato vlastnost má alespoň jeden vlastní prohlížeč s ním spojená.  
  
 DBG_ATTRIB_ACCESS_NONE  
 Určuje objekt, který má ani `public`, `private`, ani `protected` typ přístupu.  
  
 DBG_ATTRIB_ACCESS_PUBLIC  
 Určuje objekt, který obsahuje veřejný přístup.  
  
 DBG_ATTRIB_ACCESS_PRIVATE  
 Určuje objekt, který má privátní přístup.  
  
 DBG_ATTRIB_ACCESS_PROTECTED  
 Určuje objekt, který je chráněný přístup.  
  
 DBG_ATTRIB_ACCESS_FINAL  
 Určuje objekt, který má konečné přístup.  
  
 DBG_ATTRIB_ACCESS_ALL  
 Maska budou extrahovány atributy přístup z `DBG_ATTRIB_FLAGS`.  
  
 DBG_ATTRIB_STORAGE_NONE  
 Označuje, že není zadaný žádný typ úložiště.  
  
 DBG_ATTRIB_STORAGE_GLOBAL  
 Určuje globální úložiště.  
  
 DBG_ATTRIB_STORAGE_STATIC  
 Určuje statické úložiště.  
  
 DBG_ATTRIB_STORAGE_REGISTER  
 Označuje úložiště v registru.  
  
 DBG_ATTRIB_STORAGE_ALL  
 Maska budou extrahovány atributy úložiště z `DBG_ATTRIB_FLAGS`.  
  
 DBG_ATTRIB_TYPE_NONE  
 Označuje, že neexistuje žádný typ modifikátoru.  
  
 DBG_ATTRIB_TYPE_VIRTUAL  
 Označuje, že je virtuální typ objektu.  
  
 DBG_ATTRIB_TYPE_CONSTANT  
 Označuje, že je typ objektu konstantní.  
  
 DBG_ATTRIB_TYPE_SYNCHRONIZED  
 Označuje, že se synchronizují typ objektu.  
  
 DBG_ATTRIB_TYPE_VOLATILE  
 Označuje, že je typ objektu volatile.  
  
 DBG_ATTRIB_TYPE_ALL  
 Maska budou extrahovány atributy typu z `DBG_ATTRIB_FLAGS`.  
  
 DBG_ATTRIB_DATA  
 Označuje, že tento objekt je datové pole.  
  
 DBG_ATTRIB_METHOD  
 Označuje, že tento objekt je metoda.  
  
 DBG_ATTRIB_PROPERTY  
 Označuje, že tento objekt je vlastnost.  
  
 DBG_ATTRIB_CLASS  
 Označuje, že je tento objekt třídy.  
  
 DBG_ATTRIB_BASECLASS  
 Označuje, že tento objekt je základní třídu.  
  
 DBG_ATTRIB_INTERFACE  
 Označuje, že je tento objekt rozhraní.  
  
 DBG_ATTRIB_INNERCLASS  
 Označuje, že tento objekt je vnitřní třídu.  
  
 DBG_ATTRIB_MOSTDERIVED  
 Označuje, že je tento objekt se*většinou odvozených*'. Termín "*většinou odvozených*" znamená, skutečný typ objektu a není typu jeho odkazu.  
  
 DBG_ATTRIB_CHILD_ALL  
 Označuje maskou `DBG_ATTRIB_DATA` prostřednictvím `DBG_ATTRIB_MOSTDERIVED`.  
  
 DBG_ATTRIB_MULTI_CUSTOM_VIEWERS  
 Označuje, že objekt obsahuje více vlastní prohlížečů, které jsou s ním spojená.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tento výčet hodnoty nejsou definovány ve skutečnosti v sestavení pro jazyk C#. Místo toho je nutné zkopírovat definice pro zdrojový soubor.  
  
 Tyto příznaky jsou také používány pro filtrování podřízené objekty daného objektu, například když předat jako argument k [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md). Hodnoty mohou být kombinovány s bitové `OR`.  
  
 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` Příznak údaj k [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] získat [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) rozhraní z [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) rozhraní a volání [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) seznam vlastní prohlížeče.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)