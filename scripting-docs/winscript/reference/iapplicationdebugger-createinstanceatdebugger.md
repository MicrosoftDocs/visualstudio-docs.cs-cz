---
title: 'Iapplicationdebugger –:: CreateInstanceAtDebugger | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.CreateInstanceAtDebugger
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::CreateInstanceAtDebugger
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c15dc5d9b36a718ed41813bac46bc4b9415eb853
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577893"
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
Umožňuje vytváření objektů v procesu ladicího programu pomocí kódu, který je mimo proces ladicího programu.  
  
> [!IMPORTANT]
> Tato metoda by neměla být implementována, protože umožňuje nedůvěryhodnému kódu vytvářet libovolný objekt v důvěryhodném vlákně ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreateInstanceAtDebugger(  
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
  
 Metoda není aktuálně implementována.  
  
## <a name="see-also"></a>Viz také:  
 [IApplicationDebugger – rozhraní](../../winscript/reference/iapplicationdebugger-interface.md)