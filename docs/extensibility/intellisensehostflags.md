---
title: IntelliSenseHostFlags | Microsoft Docs
description: Výčet IntelliSenseHostFlags Určuje příznaky hostitele technologie IntelliSense. Tento článek popisuje hodnoty výčtu.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: af4683dede8a57b2d42acdf357808b465efb1e8e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869502"
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

|Členové|Description|
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
