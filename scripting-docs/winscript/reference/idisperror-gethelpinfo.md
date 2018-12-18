---
title: IDispError::GetHelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetHelpInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHelpInfo
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17098b4055bb61e9a2f639404edfe2214abc931e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794556"
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
Vrátí cestu k souboru nápovědy a ID kontextu téma, které popisuje chybu, pokud je to možné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrFileName`  
 [out] Řetězec obsahující plně kvalifikovanou cestu souboru nápovědy. Pokud není dostupný žádný soubor nápovědy nebo dojde k chybě, je vrácenou hodnotu NULL.  
  
 `pdwContext`  
 [out] ID kontextu nápovědy pro chybu. Pokud není dostupný žádný soubor nápovědy (Pokud `pbstrFileName` má hodnotu NULL), tento parametr nemá žádný význam.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_FAIL`|Specifický pro zprostředkovatele došlo k chybě.|  
|`E_INVALIDARG`|`pbstrFileName`nebo `pdwContext` byla NULL.|  
|`E_OUTOFMEMORY`|Zprostředkovatel nemohl přidělit dostatek paměti k vrácení cesta k souboru nápovědy.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrátí cestu k souboru nápovědy a ID kontextu téma, které popisuje chybu, pokud je to možné.  
  
> [!NOTE]
>  Tato metoda není implementována.  
  
## <a name="see-also"></a>Viz také  
 [Idisperror – rozhraní](../../winscript/reference/idisperror-interface.md)