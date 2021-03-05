---
description: Popisuje atributy dokumentu.
title: TEXT_DOC_ATTR_2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TEXT_DOC_ATTR_2
helpviewer_keywords:
- TEXT_DOC_ATTR_2 enumeration
ms.assetid: 2333b33b-042b-4ac6-9ebe-e66f95f52f51
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c8351753c5e8da9a320bd93c17e8138dedaff03d
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221857"
---
# <a name="text_doc_attr_2"></a>TEXT_DOC_ATTR_2
Popisuje atributy dokumentu.

## <a name="syntax"></a>Syntax

```cpp
typedef DWORD TEXT_DOC_ATTR_2;
const TEXT_DOC_ATTR_2 TEXT_DOC_ATTR_READONLY_2 = 0x00000001;
```

```csharp
public const uint TEXT_DOC_ATTR_READONLY_2 = 0x00000001;
```

## <a name="members"></a>Členové
 `TEXT_DOC_ATTR_READONLY_2`\
 Označuje, že dokument je určen jen pro čtení.

## <a name="remarks"></a>Poznámky

> [!NOTE]
> Tato hodnota není ve skutečnosti definována v sestavení pro C#. Místo toho je nutné zkopírovat definici do zdrojového souboru.

 Byl předán jako argument metodě [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md) .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)
