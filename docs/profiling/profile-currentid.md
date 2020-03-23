---
title: PROFILE_CURRENTID | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- PROFILE_CURRENTID
ms.assetid: 55ccf665-a05e-48c3-adf7-7714c0a9aaef
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 63b44bee152acbf5529acfcadaa49a19e9feb52b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778359"
---
# <a name="profile_currentid"></a>PROFILE_CURRENTID
PROFILE_CURRENTID vrátí pseudotoken pro ID vlákna nebo ID procesu, ve volání NameProfile, StartProfile, StopProfile, SuspendProfile a ResumeProfile funkce. Použijte ji k tomu, aby funkce fungovala na aktuálním vlákně nebo procesu, nikoli na konkrétně určeném.

## <a name="example"></a>Příklad
 PROFILE_CURRENTID je definována v *VSPerf.h* jako:

```cpp
static const unsigned int PROFILE_CURRENTID = (unsigned int)-1;
```

## <a name="example"></a>Příklad
 Následující příklad ilustruje PROFILE_CURRENTID. Příklad používá PROFILE_CURRENTID jako parametr identifikující aktuální vlákno ve volání funkce [StartProfile.](../profiling/startprofile.md)

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
- [Odkaz na rozhraní API profileru sady Visual Studio (nativní)](../profiling/visual-studio-profiler-api-reference-native.md)
- [NameProfile](../profiling/nameprofile.md)
- [ResumeProfile](../profiling/resumeprofile.md)
- [StartProfile](../profiling/startprofile.md)
- [StopProfile](../profiling/stopprofile.md)
- [SuspendProfile](../profiling/suspendprofile.md)
