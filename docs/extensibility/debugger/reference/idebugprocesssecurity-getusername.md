---
description: Získá uživatelské jméno z dodavatele portu.
title: 'IDebugProcessSecurity:: getuživatelské_jméno | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04ad8bf6ba572a1f9e14e26ef2ca37d021f6e3a0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166200"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Získá uživatelské jméno z dodavatele portu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetUserName(
    BSTR *pbstrUserName
);
```

```csharp
int GetUserName (
    string pbstrUserName
);
```

## <a name="parameters"></a>Parametry
`pbstrUserName`\
mimo Řetězec obsahující uživatelské jméno.

## <a name="return-value"></a>Návratová hodnota
 Pokud je metoda úspěšná, vrátí `S_OK` . V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 `GetUserName` Vrátí uživatelské jméno, které se zobrazí ve sloupci **uživatelské jméno** v dialogovém okně **připojit k procesu** . Chcete-li zobrazit dialogové okno **připojit k procesu** , klikněte na tlačítko **připojit k procesu** v nabídce **nástroje** v [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] integrovaném vývojovém prostředí (IDE).

## <a name="see-also"></a>Viz také
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
