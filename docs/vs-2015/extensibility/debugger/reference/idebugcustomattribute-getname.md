---
title: 'IDebugCustomAttribute:: GetName | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4463fc4f9d321b26487e885255843a7acd945f76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62569267"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Získá název vlastního atributu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetName(   
   BSTR* bstrName  
);  
```  
  
```csharp  
int GetName(  
   out string bstrName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bstrName`  
 mimo Vrátí řetězec obsahující název vlastního atributu.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Název vrácený touto metodou odpovídá názvu třídy používané k deklaraci atributu. To nemusí přesně odpovídat názvu vlastní třídy vlastního atributu jako C# umožňuje, aby byla přípona Attribute vyřazena z názvu vlastního atributu při použití v deklaraci.  
  
## <a name="see-also"></a>Viz také  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
