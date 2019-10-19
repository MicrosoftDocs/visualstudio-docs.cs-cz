---
title: 'Idisperror –:: GetHelpInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: a84e57e97bb781ad3ea0be1ac6766fd94f6f5c30
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573131"
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
Vrátí cestu k souboru nápovědy a ID kontextu tématu, které tuto chybu vysvětluje, pokud je to možné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrFileName`  
 mimo Řetězec obsahující plně kvalifikovanou cestu k souboru s příponou. Pokud není k dispozici žádný soubor Help nebo dojde k chybě, vrácená hodnota je NULL.  
  
 `pdwContext`  
 mimo ID kontextu nápovědu pro chybu. Pokud není k dispozici žádný soubor s nápovědě (Pokud `pbstrFileName` je NULL), nemá tento parametr žádný význam.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_FAIL`|Došlo k chybě specifické pro určitého poskytovatele.|  
|`E_INVALIDARG`|`pbstrFileName` nebo `pdwContext` měla hodnotu NULL.|  
|`E_OUTOFMEMORY`|Zprostředkovateli se nepovedlo přidělit dostatek paměti, ve kterém se má vrátit cesta k souboru v nápovědě.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrátí cestu k souboru nápovědy a ID kontextu tématu, které chybu vysvětluje, pokud je to možné.  
  
> [!NOTE]
> Tato metoda není implementována.  
  
## <a name="see-also"></a>Viz také:  
 [IDispError – rozhraní](../../winscript/reference/idisperror-interface.md)