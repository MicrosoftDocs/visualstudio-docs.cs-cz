---
title: IDebugPortPicker | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f3e030facd8c70aec4fdc480b01c90ee4c0acda7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188393"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Představuje přizpůsobené uživatelské rozhraní pro výběr portu.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortPicker : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Toto rozhraní je implementováno pomocí dodavatelů portů. Dodavatel portu definuje svůj výběr portů tím, že ho zveřejňuje jako CLSID a odkazuje na `metricPortPickerCLSID` metriku na vystavené CLSID.  
  
## <a name="methods"></a>Metody  
 V následující tabulce jsou uvedeny metody `IDebugPortPicker` .  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Zobrazí zadané dialogové okno, ve kterém může uživatel vybrat port.|  
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Nastaví poskytovatele služby.|  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
