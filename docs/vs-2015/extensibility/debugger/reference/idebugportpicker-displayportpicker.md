---
title: IDebugPortPicker::D isplayPortPicker | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3dd9317a73800a3886a5a807e9e28b0c24b2301c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188379"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Zobrazí zadané dialogové okno, ve kterém může uživatel vybrat port.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT DisplayPortPicker(  
   HWND hwndParentDialog,  
   BSTR* pbstrPortId  
);  
```  
  
```csharp  
public int DisplayPortPicker(  
   int hwndParentDialog,  
   out string pbstrPortId  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hwndParentDialog`  
 pro Popisovač pro nadřazené dialogové okno  
  
 `pbstrPortId`  
 mimo Řetězec identifikátoru portu.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. Návratová hodnota `S_FALSE` (nebo návratová hodnota `S_OK` s `BSTR` nastavením na `NULL` ) značí, že uživatel kliknul na **Zrušit**.  
  
## <a name="see-also"></a>Viz také  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
