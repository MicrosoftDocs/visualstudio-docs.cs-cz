---
title: 'IDebugProcessSecurity:: getuživatelské_jméno | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 17a6ef52d7df1c60b0cb6581a7e15eeaf67e7875
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202782"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Získá uživatelské jméno z dodavatele portu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```csharp  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrUserName`  
 mimo Řetězec obsahující uživatelské jméno.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je metoda úspěšná, vrátí `S_OK` . V opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 `GetUserName` Vrátí uživatelské jméno, které se zobrazí ve sloupci **uživatelské jméno** v dialogovém okně **připojit k procesu** . Chcete-li zobrazit dialogové okno **připojit k procesu** , klikněte na tlačítko **připojit k procesu** v nabídce **nástroje** v [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] integrovaném vývojovém prostředí (IDE).  
  
## <a name="see-also"></a>Viz také  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
