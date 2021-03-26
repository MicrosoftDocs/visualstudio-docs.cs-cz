---
description: Povolí uživatelskému rozhraní sady Visual Studio zobrazit text v části přenosové informace dialogového okna připojit k procesu.
title: IDebugPortSupplierDescription2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dba3cd07bb84843ff4d2531cdde63ab9e671f961
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071919"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Umožňuje [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] uživatelskému rozhraní zobrazit text v části **přenosové informace** dialogového okna **připojit k procesu** .

## <a name="syntax"></a>Syntax

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno pomocí dodavatelů portů.

## <a name="methods"></a>Metody
 V následující tabulce jsou uvedeny metody `IDebugPortSupplierDescription2` .

|Metoda|Popis|
|------------|-----------------|
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Načte popis a popis metadata dodavatele portu.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
