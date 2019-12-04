---
title: ResumeProfile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ResumeProfile
ms.assetid: 876f145b-ec07-4240-ade6-4f6e44baadce
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3d65d5fcf8961493c2b780453f2143de788551a5
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778307"
---
# <a name="resumeprofile"></a>ResumeProfile
Metoda `ResumeProfile` snižuje počítadlo pozastavení/obnovení pro zadanou úroveň profilace.

## <a name="syntax"></a>Syntaxe

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI ResumeProfile(
                       PROFILE_CONTROL_LEVEL Level,
                       unsigned int dwId);
```

#### <a name="parameters"></a>Parametry
 `Level`

 Označuje úroveň profilu, na kterou lze použít shromažďování dat výkonu. Následující výčty **PROFILE_CONTROL_LEVEL** lze použít k označení jedné ze tří úrovní, na kterou lze použít shromažďování dat výkonu:

|Čítače|Popis|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|Nastavení globální úrovně má vliv na všechny procesy a vlákna v rámci procesu profilace.|
|PROFILE_PROCESSLEVEL|Nastavení na úrovni procesu ovlivňuje všechna vlákna, která jsou součástí zadaného procesu.|
|PROFILE_THREADLEVEL|Nastavení úrovně profilace vlákna má vliv na zadané vlákno.|

 `dwId`

 Proces nebo identifikátor vlákna generovaný systémem.

## <a name="property-valuereturn-value"></a>Hodnota nebo návratová hodnota vlastnosti
 Funkce označuje úspěch nebo neúspěch pomocí **PROFILE_COMMAND_STATUS** výčtu. Návratová hodnota může být jedna z následujících:

|Čítače|Popis|
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
 *Microsoft. VisualStudio. Profiler. dll*

## <a name="function-information"></a>Informace o funkci
 Hlavička: deklaruje se v *VSPerf. h*

 Knihovna importu: *VSPerf. lib*

## <a name="example"></a>Příklad
 Následující příklad ilustruje funkci ResumeProfile. Příklad předpokládá, že volání metody SuspendProfile bylo provedeno pro stejné vlákno nebo proces identifikovaný [PROFILE_CURRENTID](../profiling/profile-currentid.md).

```cpp
void ExerciseResumeProfile()
{
    // The initial value of the Suspend/Resume counter is 0.
    // Each call to SuspendProfile adds 1 to the Suspend/Resume
    // count; each call to ResumeProfile subtracts 1.

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare enumeration to hold result of call to ResumeProfile
    PROFILE_COMMAND_STATUS profileResult;

    profileResult = ResumeProfile(
        PROFILE_GLOBALLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("ResumeProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, profileResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Viz také:
- [Referenční dokumentace rozhraní API pro Visual Studio Profiler (nativní)](../profiling/visual-studio-profiler-api-reference-native.md)
