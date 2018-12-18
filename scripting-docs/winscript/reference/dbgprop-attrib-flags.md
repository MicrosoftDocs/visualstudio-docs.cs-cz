---
title: DBGPROP_ATTRIB_FLAGS | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 831f12d11515e6796941b64e114bdc084309b87d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862408"
---
# <a name="dbgpropattribflags"></a>DBGPROP_ATTRIB_FLAGS
Popisuje různé atributy pro `IDebugProperty`. Člen `DebugPropertyInfo` struktury.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 Označuje žádné atributy.  
  
 DBGPROP_ATTRIB_VALUE_IS_INVALID  
 Označuje, že hodnota ve `DebugPropertyInfo::bstrValue` není platný.  
  
 DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  
 Znamená, že odkaz nebo vlastnost má podřízené položky.  
  
 DBGPROP_ATTRIB_VALUE_READONLY  
 Označuje, že hodnota je jen pro čtení.  
  
 DBGPROP_ATTRIB_ACCESS_PUBLIC  
 Určuje objekt, který má přístup public.  
  
 DBGPROP_ATTRIB_ACCESS_PRIVATE  
 Určuje objekt, který má privátní přístup.  
  
 DBGPROP_ATTRIB_ACCESS_PROTECTED  
 Určuje objekt, který chrání přístup.  
  
 DBGPROP_ATTRIB_ACCESS_FINAL  
 Určuje objekt s posledním přístupem.  
  
 DBGPROP_ATTRIB_STORAGE_GLOBAL  
 Určuje globální úložiště.  
  
 DBGPROP_ATTRIB_STORAGE_STATIC  
 Určuje statické úložiště.  
  
 DBGPROP_ATTRIB_STORAGE_FIELD  
 Určuje objekt, který je vlastnost.  
  
 DBGPROP_ATTRIB_STORAGE_VIRTUAL  
 Označuje virtuálního úložiště.  
  
 DBGPROP_ATTRIB_TYPE_IS_CONSTANT  
 Označuje konstantní typ objektu.  
  
 DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  
 Označuje, že tento slot je vlákno synchronizované.  
  
 DBGPROP_ATTRIB_TYPE_IS_VOLATILE  
 Označuje, že tento slot je volatile s ohledem na trvalého úložiště.  
  
 DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  
 Označuje, že tento slot má atributy nenabízející těchto předdefinovaných bitů.  
  
 DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  
 Označuje, že hodnota je návratová hodnota z funkce.  
  
## <a name="remarks"></a>Poznámky  
 Tyto příznaky jsou také použít k filtrování podřízené objekty daného objektu. Hodnoty lze kombinovat s bitový operátor OR.  
  
## <a name="see-also"></a>Viz také  
 [Idebugproperty – rozhraní](../../winscript/reference/idebugproperty-interface.md)   
 [DebugPropertyInfo – struktura](../../winscript/reference/debugpropertyinfo-structure.md)