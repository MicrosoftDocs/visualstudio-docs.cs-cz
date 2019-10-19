---
title: 'Iremotedebugapplication –:: CreateInstanceAtApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.CreateInstanceAtApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::CreateInstanceAtApplication
ms.assetid: d669ec80-2182-400d-87cc-7c1753315e5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 285e5df6960e3188ffe1ce17b1fc4f43626a3d74
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572306"
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
Umožňuje vytváření objektů v procesu aplikace podle kódu, který je mimo proces do aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreateInstanceAtApplication(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `rclsid`  
 pro Identifikátor třídy (CLSID) objektu, který se má vytvořit  
  
 `pUnkOuter`  
 pro Pokud `NULL`, objekt se nevytváří jako součást agregace. V opačném případě je `pUnkOuter` ukazatel na rozhraní `IUnknown` agregovaného objektu (řízení `IUnknown`).  
  
 `dwClsContext`  
 pro Kontext pro spuštění spustitelného kódu. Hodnoty jsou pořízeny z `CLSCTX` výčtu.  
  
 `riid`  
 pro Identifikátor rozhraní, který se používá ke komunikaci s objektem.  
  
 `ppvObject`  
 mimo Adresa ukazatele na proměnnou, která obdrží ukazatel rozhraní požadovaný v `riid`. Po úspěšném návratu `ppvObject` obsahuje požadovaný ukazatel rozhraní. Po selhání \* `ppvObject` obsahuje `NULL`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda deleguje `CoCreateInstance`.  
  
## <a name="see-also"></a>Viz také:  
 [IRemoteDebugApplication – rozhraní](../../winscript/reference/iremotedebugapplication-interface.md)