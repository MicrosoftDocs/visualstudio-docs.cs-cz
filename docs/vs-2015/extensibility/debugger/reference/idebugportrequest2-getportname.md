---
title: 'IDebugPortRequest2:: GetPort | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: afed0bb700f41f7c39551f1a9bc7779f36b0ae57
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188369"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Získá název portu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```csharp  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrPortName`  
 mimo Vrátí název portu.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) se obvykle předává z ladicího balíčku (klienta) na dodavatele portu (Server) pro získání připojení k portu. Ladicí balíček i dodavatel portu si vědomi možných možností pro port. Pokud jednoduchý řetězec může popisovat port, pak `IDebugPortRequest2::GetPortName` má metoda dostatek informací pro vytvoření připojení. V opačném případě může klient poskytnout další rozhraní, které může server získat pomocí nástroje `IDebugPortRequest2::QueryInterface` .  
  
## <a name="see-also"></a>Viz také  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
