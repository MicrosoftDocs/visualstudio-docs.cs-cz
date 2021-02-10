---
title: StartProfile | Microsoft Docs
description: Přečtěte si o funkci StartProfile a o tom, jak nastaví čítač na 1 (zapnuto) pro zadanou úroveň profilace.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- StartProfile
ms.assetid: 1761311d-c9d5-48f5-b1f8-b3605829940a
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6a2fee1e5c7a091af1ed996d374f4ed7e60b8f2f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949919"
---
# <a name="startprofile"></a>StartProfile
`StartProfile`Funkce nastaví čítač na 1 (zapnuto) pro zadanou úroveň profilace.

## <a name="syntax"></a>Syntaxe

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI StartProfile(
                        PROFILE_CONTROL_LEVEL Level,
                        unsigned int dwId);
```

#### <a name="parameters"></a>Parametry
 `Level`

 Označuje úroveň profilu, na kterou lze použít shromažďování dat výkonu. Následující výčty **PROFILE_CONTROL_LEVEL** lze použít k označení jedné ze tří úrovní, na kterou lze použít shromažďování dat výkonu:

|Čítače|Description|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|Nastavení globální úrovně má vliv na všechny procesy a vlákna v rámci procesu profilace.|
|PROFILE_PROCESSLEVEL|Nastavení úrovně procesu ovlivňuje všechna vlákna, která jsou součástí zadaného procesu.|
|PROFILE_THREADLEVEL|Nastavení úrovně profilace vlákna má vliv na zadané vlákno.|

 `dwId`

 Proces nebo identifikátor vlákna generovaný systémem.

## <a name="property-valuereturn-value"></a>Hodnota nebo návratová hodnota vlastnosti
 Funkce označuje úspěch nebo neúspěch pomocí **PROFILE_COMMAND_STATUS** výčtu. Návratová hodnota může být jedna z následujících:

|Čítače|Description|
|----------------|-----------------|
|PROFILE_ERROR_ID_NOEXIST|ID elementu profilace neexistuje.|
|PROFILE_ERROR_LEVEL_NOEXIST|Zadaná úroveň profilace neexistuje.|
|PROFILE_ERROR_MODE_NEVER|Režim profilace byl nastaven na hodnotu nikdy při volání funkce.|
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|Volání funkce profilování, úroveň profilace nebo kombinace volání a úrovně ještě není naimplementované.|
|PROFILE_OK|Volání bylo úspěšné.|

## <a name="remarks"></a>Poznámky
 StartProfile a StopProfile řídí stav spuštění/zastavení pro úroveň profilace. Výchozí hodnota spustit/zastavit je 1. Počáteční hodnota může být v registru změněna. Každé volání StartProfile sady se spustí/zastaví na 1. každé volání StopProfile nastaví na hodnotu 0.

 Když je spuštění/zastavení větší než 0, je stav spuštění/zastavení pro úroveň ZAPNUTo. Pokud je menší nebo rovno 0, je stav spuštění/zastavení VYPNUTý.

 Když je stav spuštění/zastavení i stav pozastavení/obnovení ZAPNUTý, stav profilace pro úroveň je ZAPNUTo. Aby bylo vlákno profilování, musí být pro vlákno ZAPNUTé globální stavy, procesy a úrovně vláken.

## <a name="net-framework-equivalent"></a>Ekvivalent .NET Framework
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Informace o funkci
 Hlavička: deklaruje se v *VSPerf. h*

 Knihovna importu: *VSPerf. lib*

## <a name="example"></a>Příklad
 Následující příklad ilustruje volání funkce StartProfile.

```cpp
void ExerciseStartProfile()
{
    // StartProfile and StopProfile control the
    // Start/Stop state for the profiling level.
    // The default initial value of Start/Stop is 1.
    // The initial value can be changed in the registry.
    // Each call to StartProfile sets Start/Stop to 1;
    // each call to StopProfile sets it to 0.

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare enumeration to hold return value of
    // the call to StartProfile.
    PROFILE_COMMAND_STATUS profileResult;

    profileResult = StartProfile(
        PROFILE_THREADLEVEL,
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
