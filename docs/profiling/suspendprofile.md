---
title: SuspendProfile | Microsoft Docs
description: Přečtěte si, jak metoda SuspendProfile zvyšuje čítač pozastavení/obnovení pro zadanou úroveň profilace.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SuspendProfile
ms.assetid: 7c8de6e6-bb88-4353-92c3-ce7290310d61
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6be94fafb1e41390236977a7a06b59cf7ac71a84
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868202"
---
# <a name="suspendprofile"></a>SuspendProfile
`SuspendProfile`Metoda zvýší čítač pozastavení/obnovení pro zadanou úroveň profilace.

## <a name="syntax"></a>Syntaxe

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI SuspendProfile(
                       PROFILE_CONTROL_LEVEL Level,
                       unsigned int dwId);
```

#### <a name="parameters"></a>Parametry
 `Level`

 Označuje úroveň profilu, na kterou lze použít shromažďování dat výkonu. Následující výčty **PROFILE_CONTROL_LEVEL** lze použít k označení jedné ze tří úrovní, na kterou lze použít shromažďování dat výkonu:

|Čítače|Description|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|Nastavení globální úrovně má vliv na všechny procesy a vlákna v rámci procesu profilace.|
|PROFILE_PROCESSLEVEL|Nastavení na úrovni procesu ovlivňuje všechna vlákna, která jsou součástí zadaného procesu.|
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
 Počáteční hodnota čítače pozastavení/obnovení je 0. Každé volání SuspendProfile přidá 1 k počtu pozastavení/obnovení; každé volání ResumeProfile odečte 1.

 Když je počet pozastavení/obnovení větší než 0, stav pozastavení/obnovení pro úroveň je VYPNUTý. Pokud je počet menší nebo roven 0, je stav pozastavení/obnovení ZAPNUTý.

 Když je stav spuštění/zastavení i stav pozastavení/obnovení ZAPNUTý, stav profilace pro úroveň je ZAPNUTo. Aby bylo vlákno profilování, musí být všechny stavy, procesy a podprocesy na úrovni vlákna zapnuty.

## <a name="net-framework-equivalent"></a>Ekvivalent .NET Framework
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Informace o funkci
 Hlavička: deklaruje se v *VSPerf. h*

 Knihovna importu: *VSPerf. lib*

## <a name="example"></a>Příklad
 Následující příklad ilustruje metodu SuspendProfile. Tento příklad předpokládá, že bylo provedeno předchozí volání StartProfile pro proces nebo vlákno identifikované [PROFILE_CURRENTID](../profiling/profile-currentid.md).

```cpp
void ExerciseSuspendProfile()
{
    // The initial value of the Suspend/Resume counter is 0.
    // Each call to SuspendProfile adds 1 to the
    // Suspend/Resume count; each call
    // to ResumeProfile subtracts 1.

    // Variables used to print output
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare enumeration to hold result of call
    // to SuspendProfile
    PROFILE_COMMAND_STATUS profileResult;

    profileResult = SuspendProfile(
        PROFILE_GLOBALLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("SuspendProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, profileResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Viz také
- [Referenční dokumentace rozhraní API pro Visual Studio Profiler (nativní)](../profiling/visual-studio-profiler-api-reference-native.md)
