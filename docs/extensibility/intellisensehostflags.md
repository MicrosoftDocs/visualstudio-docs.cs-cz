---
title: IntelliSenseHostFlags | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0df05e7363db01bd4f16fee5d75141dc93df1c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710270"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Určuje příznaky hostitele technologie IntelliSense.

## <a name="syntax"></a>Syntaxe

```cpp
enum IntellisenseHostFlags
{
    IHF_READONLYCONTEXT      = 0x00000001
    IHF_NOSEPARATESUBJECT    = 0x00000002
    IHF_SINGLELINESUBJECT    = 0x00000004
    IHF_FORCECOMMITTOCONTEXT = 0x00000008
    IHF_OVERTYPE             = 0x00000010
};
```

### <a name="parameters"></a>Parametry

|Členové|Popis|
|-------------|-----------------|
|`IHF_READONLYCONTEXT`|Kontextová vyrovnávací paměť je jen pro čtení.|
|`IHF_NOSEPARATESUBJECT`|Žádný text předmětu. Kontextová vyrovnávací paměť obsahuje cíl `!IHF_READONLYCONTEXT`IntelliSense (implikuje).|
|`IHF_SINGLELINESUBJECT`|Text předmětu není schopen více řádků.|
|`IHF_FORCECOMMITTOCONTEXT`|Stejné `CanCommitIntoReadOnlyBuffer`jako .|
|`IHF_OVERTYPE`|Úpravy (v předmětu nebo kontextu) by měly být prováděny v režimu overtype.|

## <a name="requirements"></a>Požadavky
 SingleFileeditor.idl

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.TextManager.Interop>
