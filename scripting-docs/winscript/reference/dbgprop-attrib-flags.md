---
title: DBGPROP_ATTRIB_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBGPROP_ATTRIB_FLAGS
apilocation:
- scrobj.dll
f1_keywords:
- DBGPROP_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS
ms.assetid: 90314496-527b-4357-9df8-125a360bf216
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3170e310aa3177e2ca7a1dd81ead02bcc4050114
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572594"
---
# <a name="dbgprop_attrib_flags"></a>DBGPROP_ATTRIB_FLAGS
Popisuje různé atributy pro `IDebugProperty`. Člen struktury `DebugPropertyInfo`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
enum {  
DBGPROP_ATTRIB_NO_ATTRIB  =0x00000000,  
   DBGPROP_ATTRIB_VALUE_IS_INVALID  =0x00000008,  
   DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  =0x00000010,  
   DBGPROP_ATTRIB_VALUE_READONLY  =0x00000800,  
   DBGPROP_ATTRIB_ACCESS_PUBLIC  =0x00001000,  
   DBGPROP_ATTRIB_ACCESS_PRIVATE  =0x00002000,  
   DBGPROP_ATTRIB_ACCESS_PROTECTED  =0x00004000,  
   DBGPROP_ATTRIB_ACCESS_FINAL  =0x00008000,  
   DBGPROP_ATTRIB_STORAGE_GLOBAL  =0x00010000,  
   DBGPROP_ATTRIB_STORAGE_STATIC  =0x00020000,  
   DBGPROP_ATTRIB_STORAGE_FIELD  =0x00040000,  
   DBGPROP_ATTRIB_STORAGE_VIRTUAL  =0x00080000,  
   DBGPROP_ATTRIB_TYPE_IS_CONSTANT  =0x00100000,  
   DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  =0x00200000,  
   DBGPROP_ATTRIB_TYPE_IS_VOLATILE  =0x00400000,  
   DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  =0x00800000  
   DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  =0x08000000,  
};  
  
```  
  
## <a name="members"></a>Členové  
 DBGPROP_ATTRIB_NO_ATTRIB  
 Neurčuje žádné atributy.  
  
 DBGPROP_ATTRIB_VALUE_IS_INVALID  
 Označuje, že hodnota v `DebugPropertyInfo::bstrValue` není platná.  
  
 DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  
 Označuje, že odkaz nebo vlastnost má podřízené položky.  
  
 DBGPROP_ATTRIB_VALUE_READONLY  
 Označuje, že hodnota je jen pro čtení.  
  
 DBGPROP_ATTRIB_ACCESS_PUBLIC  
 Označuje objekt, který má veřejný přístup.  
  
 DBGPROP_ATTRIB_ACCESS_PRIVATE  
 Označuje objekt, který má privátní přístup.  
  
 DBGPROP_ATTRIB_ACCESS_PROTECTED  
 Označuje objekt, který má chráněný přístup.  
  
 DBGPROP_ATTRIB_ACCESS_FINAL  
 Označuje objekt, který má konečný přístup.  
  
 DBGPROP_ATTRIB_STORAGE_GLOBAL  
 Označuje globální úložiště.  
  
 DBGPROP_ATTRIB_STORAGE_STATIC  
 Označuje statické úložiště.  
  
 DBGPROP_ATTRIB_STORAGE_FIELD  
 Označuje objekt, který je vlastností.  
  
 DBGPROP_ATTRIB_STORAGE_VIRTUAL  
 Indikuje virtuální úložiště.  
  
 DBGPROP_ATTRIB_TYPE_IS_CONSTANT  
 Označuje, že typ objektu je konstantní.  
  
 DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  
 Indikuje, že je tento slot synchronizovaný z vlákna.  
  
 DBGPROP_ATTRIB_TYPE_IS_VOLATILE  
 Označuje, že tento slot je volatile s ohledem na trvalé úložiště.  
  
 DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  
 Označuje, že tato patice má nad rámec těchto předdefinovaných bitů atributy.  
  
 DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  
 Označuje, že hodnota je návratovou hodnotou z funkce.  
  
## <a name="remarks"></a>Poznámky  
 Tyto příznaky slouží také k filtrování podřízených objektů objektu. Hodnoty mohou být kombinovány s bitovým operátorem OR.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní idebugproperty –](../../winscript/reference/idebugproperty-interface.md)  
 [DebugPropertyInfo – struktura](../../winscript/reference/debugpropertyinfo-structure.md)