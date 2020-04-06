---
title: IDebugProcess2::GetAttachedSessionName | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b70fd48adacdbbf936c6997fc373ad4a8d7e696b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724080"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Získá název relace, která ladí tento proces. IDE můžete zobrazit tyto informace uživateli, který je ladění určitého procesu v určitém počítači.

> [!NOTE]
> Tato metoda je zastaralé a jeho implementace `E_NOTIMPL`by měla vždy vrátit .

## <a name="syntax"></a>Syntaxe

```
HRESULT GetAttachedSessionName(
   BSTR* pbstrSessionName
);
```

## <a name="parameters"></a>Parametry
`pbstrSessionName`\

## <a name="return-value"></a>Návratová hodnota
 Tato metoda by `E_NOTIMPL`měla vždy vrátit .

## <a name="see-also"></a>Viz také
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
