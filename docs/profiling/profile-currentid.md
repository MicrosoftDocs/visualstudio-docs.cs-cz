---
title: PROFILE_CURRENTID | Microsoft Docs
description: Naučte se, jak použít PROFILE_CURRENTID k zajištění toho, aby funkce pracovala na aktuálním vlákně nebo procesu, místo konkrétně označeného jako jedna.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- PROFILE_CURRENTID
ms.assetid: 55ccf665-a05e-48c3-adf7-7714c0a9aaef
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5e5c888e1b285bb92ea44c32e26834f16668b8dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936363"
---
# <a name="profile_currentid"></a>PROFILE_CURRENTID
PROFILE_CURRENTID vrátí pseudo token pro ID vlákna nebo ID procesu ve volání funkce NameProfile, StartProfile, StopProfile, SuspendProfile a ResumeProfile. Použijte jej k tomu, aby funkce pracovala na aktuálním vlákně nebo procesu, nikoli konkrétně.

## <a name="example-1"></a>Příklad 1
 PROFILE_CURRENTID je definována v *VSPerf. h* jako:

```cpp
static const unsigned int PROFILE_CURRENTID = (unsigned int)-1;
```

## <a name="example-2"></a>Příklad 2
 Následující příklad ukazuje PROFILE_CURRENTID. Příklad používá PROFILE_CURRENTID jako parametr identifikující aktuální vlákno ve volání funkce [StartProfile](../profiling/startprofile.md) .

```cpp
void ExerciseProfileCurrentID()
{
    // Declare ProfileOperationResult enumeration
    // to hold return value of a call to StartProfile.
    PROFILE_COMMAND_STATUS profileResult;

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    profileResult = StartProfile(
        PROFILE_GLOBALLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("StartProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, profileResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Viz také
- [Referenční dokumentace rozhraní API pro Visual Studio Profiler (nativní)](../profiling/visual-studio-profiler-api-reference-native.md)
- [NameProfile](../profiling/nameprofile.md)
- [ResumeProfile](../profiling/resumeprofile.md)
- [StartProfile](../profiling/startprofile.md)
- [StopProfile](../profiling/stopprofile.md)
- [SuspendProfile](../profiling/suspendprofile.md)
