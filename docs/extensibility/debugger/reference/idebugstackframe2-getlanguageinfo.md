---
title: 'IDebugStackFrame2:: GetLanguageInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e7e9b08847ea4d0c513ea458bd1ab40211cb9515
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956526"
---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo

Získá jazyk přidružený k tomuto bloku zásobníku.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetLanguageInfo ( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo ( 
   ref string pbstrLanguage,
   ref Guid   pguidLanguage
);
```

## <a name="parameters"></a>Parametry

`pbstrLanguage`\
mimo Vrátí název jazyka, který implementuje metodu spojenou s tímto rámcem zásobníku.

`pguidLanguage`\
mimo Vrátí `GUID` jazyk. Pro [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] jazyky lze například vrátit následující:

- `guidVBScriptLang`\

- `guidJScriptLang`\

- `guidCPPLang`\

- `guidVBLang`\

- `guidSQLLang`\

- `guidScriptLang`\

## <a name="return-value"></a>Návratová hodnota

 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také

- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
