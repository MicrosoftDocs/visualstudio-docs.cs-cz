---
title: IDebugBreakpointResolution2::GetResolutionInfo | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointResolution2::GetResolutionInfo
helpviewer_keywords:
- IDebugBreakpointResolution2::GetResolutionInfo
ms.assetid: 828cbdf6-b87d-4c45-be87-d87087b04a60
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82aad1f435e152ce237fa1f2d2552d921f80621d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734779"
---
# <a name="idebugbreakpointresolution2getresolutioninfo"></a>IDebugBreakpointResolution2::GetResolutionInfo
Získá informace o rozlišení zarážky, která popisuje tuto zarážku.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetResolutionInfo( 
   BPRESI_FIELDS       dwFields,
   BP_RESOLUTION_INFO* pBPResolutionInfo
);
```

```csharp
int GetResolutionInfo( 
   enum BPRESI_FIELDS   dwFields,
   BP_RESOLUTION_INFO[] pBPResolutionInfo
);
```

## <a name="parameters"></a>Parametry
`dwFields`\
[v] Kombinace příznaků z [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md) výčtu, které určují, která pole parametru `pBPResolutionInfo` mají být vyplněna.

`pBPResolutionInfo`\
[out] Struktura [BP_RESOLUTION_INFO,](../../../extensibility/debugger/reference/bp-resolution-info.md) která má být vyplněna informacemi o této zarážky.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="example"></a>Příklad
 Následující příklad implementuje tuto `CDebugBreakpointResolution` metodu pro jednoduchý objekt, který zpřístupňuje rozhraní [IDebugBreakpointResolution2.](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)

```
HRESULT CDebugBreakpointResolution::GetResolutionInfo(
   BPRESI_FIELDS dwFields,
   BP_RESOLUTION_INFO* pBPResolutionInfo)
{
   HRESULT hr;

   if (pBPResolutionInfo)
   {
      // Copy the specified fields of the request information from the class
      // member variable to the local BP_RESOLUTION_INFO variable.
      hr = CopyBP_RESOLUTION_INFO(m_bpResolutionInfo,
                                  *pBPResolutionInfo,
                                  dwFields);
   }
   else
   {
      hr = E_INVALIDARG;
   }

   return hr;
}

HRESULT CDebugBreakpointResolution::CopyBP_RESOLUTION_INFO(
   BP_RESOLUTION_INFO& bpResSrc,
   BP_RESOLUTION_INFO& bpResDest,
   DWORD dwFields)
{
   HRESULT hr = S_OK;

   // Start with a raw copy.
   memcpy(&bpResDest, &bpResSrc, sizeof(BP_RESOLUTION_INFO));

   // The fields in the destination is the result of the AND of
   //  bpInfoSrc.dwFields and dwFields.
   bpResDest.dwFields = dwFields & bpResSrc.dwFields;

   // Fill in the bp location information if the BPRESI_BPRESLOCATION
   //  flag is set in BPRESI_FIELDS.
   if (IsFlagSet(bpResDest.dwFields, BPRESI_BPRESLOCATION))
   {
      // Switch based on the BP_TYPE.
      switch (bpResSrc.bpResLocation.bpType)
      {
         case BPT_CODE:
         {
            // AddRef the IDebugCodeContext2 of the BP_RESOLUTION_CODE structure.
            bpResDest.bpResLocation.bpResLocation.bpresCode.pCodeContext->AddRef();
            break;
         }
         case BPT_DATA:
         {
            // Copy the bstrDataExpr, bstrFunc, and bstrImage of the
            // BP_RESOLUTION_DATA structure.
            bpResDest.bpResLocation.bpResLocation.bpresData.bstrDataExpr =
               SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrDataExpr);
            bpResDest.bpResLocation.bpResLocation.bpresData.bstrFunc =
               SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrFunc);
            bpResSrc.bpResLocation.bpResLocation.bpresData.bstrImage =
               SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrImage);
            break;
         }
         default:
         {
            assert(FALSE);
            // Clear the BPRESI_BPRESLOCATION flag in the BPRESI_FIELDS
            // of the destination BP_RESOLUTION_INFO.
            ClearFlag(bpResDest.dwFields, BPRESI_BPRESLOCATION);
            break;
         }
      }
   }
   // AddRef the IDebugProgram2 if the BPRESI_PROGRAM flag is set in BPRESI_FIELDS.
   if (IsFlagSet(bpResDest.dwFields, BPRESI_PROGRAM))
   {
      bpResDest.pProgram->AddRef();
   }
   // AddRef the IDebugThread2 if the BPRESI_THREAD flag is set in BPRESI_FIELDS.
   if (IsFlagSet(bpResDest.dwFields, BPRESI_THREAD))
   {
      bpResDest.pThread->AddRef();
   }

   return hr;
}
```

## <a name="see-also"></a>Viz také
- [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
