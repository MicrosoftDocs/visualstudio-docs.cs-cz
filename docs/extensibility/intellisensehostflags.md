---
title: IntelliSenseHostFlags | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
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
|`IHF_NOSEPARATESUBJECT`|Text předmětu není k dispozici. Kontextová vyrovnávací paměť obsahuje IntelliSense – cíl (implikuje `!IHF_READONLYCONTEXT` ).|
|`IHF_SINGLELINESUBJECT`|Text předmětu neumožňuje více řádků.|
|`IHF_FORCECOMMITTOCONTEXT`|Stejné jako `CanCommitIntoReadOnlyBuffer` .|
|`IHF_OVERTYPE`|Úpravy (v předmětu nebo kontextu) by se měly provádět v režimu přepisování.|

## <a name="requirements"></a>Požadavky
 SingleFileeditor. idl

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.TextManager.Interop>
