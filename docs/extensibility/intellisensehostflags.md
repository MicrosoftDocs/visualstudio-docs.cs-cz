---
title: IntelliSenseHostFlags – | Microsoft Docs
description: Výčet IntelliSenseHostFlags určuje příznaky hostitele Technologie IntelliSense. Tento článek popisuje výčtové hodnoty.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 33345f86c69d0faeaa5863534e21eca5ecc176cc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902615"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Určuje příznaky hostitele Technologie IntelliSense.

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
|`IHF_NOSEPARATESUBJECT`|Žádný text předmětu. Kontextová vyrovnávací paměť obsahuje cíl IntelliSense (implikuje `!IHF_READONLYCONTEXT` ).|
|`IHF_SINGLELINESUBJECT`|Text předmětu není schopen více řádků.|
|`IHF_FORCECOMMITTOCONTEXT`|Stejné jako `CanCommitIntoReadOnlyBuffer` u .|
|`IHF_OVERTYPE`|Úpravy (v předmětu nebo kontextu) by se měly dělat v režimu přetypování.|

## <a name="requirements"></a>Požadavky
 SingleFileeditor.idl

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.TextManager.Interop>
