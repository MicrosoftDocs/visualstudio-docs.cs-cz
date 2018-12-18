---
title: IProvideExpressionContexts::EnumExpressionContexts | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProvideExpressionContexts.EnumExpressionContexts
apilocation:
- jscript.dll
helpviewer_keywords:
- IProvideExpressionContexts::EnumExpressionContexts
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c47619fface892e7e0d80141d7d4be53398a356e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794979"
---
# <a name="iprovideexpressioncontextsenumexpressioncontexts"></a>IProvideExpressionContexts::EnumExpressionContexts
Vrátí enumerátor výraz kontexty známé touto součástí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppedec`  
 [out] Enumerátor výraz kontexty známé touto součástí.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Správce procesu ladění tato metoda používá k nalezení všech kontextů globálním výrazu přidružené k dané vlákno.  
  
> [!NOTE]
>  Tato metoda je volána z vlákna, které vás zajímají. Je implementátorovi identifikovat aktuální vlákno a vrátí enumerátor vhodné.  
  
## <a name="see-also"></a>Viz také  
 [Iprovideexpressioncontexts – rozhraní](../../winscript/reference/iprovideexpressioncontexts-interface.md)