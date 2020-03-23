---
title: ŽivotopisProfil | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778307"
---
# <a name="resumeprofile"></a>ResumeProfile
Metoda `ResumeProfile` sníží počitadlo Pozastavit/Obnovit pro zadanou úroveň profilování.

## <a name="syntax"></a>Syntaxe

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI ResumeProfile(
                       PROFILE_CONTROL_LEVEL Level,
                       unsigned int dwId);
```

#### <a name="parameters"></a>Parametry
 `Level`

 Označuje úroveň profilu, na kterou lze použít shromažďování dat o výkonu. Následující **PROFILE_CONTROL_LEVEL** čítače výčtu lze použít k označení jedné ze tří úrovní, na které lze použít shromažďování dat výkonu:

|Čítač výčtu|Popis|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|Nastavení globální úrovně ovlivňuje všechny procesy a vlákna v profilování spustit.|
|PROFILE_PROCESSLEVEL|Nastavení úrovně procesu ovlivní všechna vlákna, která jsou součástí zadaného procesu.|
|PROFILE_THREADLEVEL|Nastavení úrovně profilování vláken ovlivňuje zadané vlákno.|

 `dwId`

 Identifikátor procesu nebo vlákna generovaný systémem.

## <a name="property-valuereturn-value"></a>Hodnota/vrácená hodnota nemovitosti
 Funkce označuje úspěch nebo neúspěch pomocí **PROFILE_COMMAND_STATUS** výčtu. Vrácená hodnota může být jedna z následujících hodnot:

|Čítač výčtu|Popis|
|----------------|-----------------|
|PROFILE_ERROR_ID_NOEXIST|ID prvku profilování neexistuje.|
|PROFILE_ERROR_LEVEL_NOEXIST|Zadaná úroveň profilování neexistuje.|
|PROFILE_ERROR_MODE_NEVER|Režim profilování byl nastaven na NIKDY, když byla volána funkce.|
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|Profilování volání funkce, profilování úroveň nebo kombinace volání a úroveň ještě není implementována.|
|PROFILE_OK|Volání bylo úspěšné.|

## <a name="remarks"></a>Poznámky
 Počáteční hodnota počítadla Pozastavit/Pokračovat je 0. Každé volání SuspendProfile přidá 1 pozastavit/obnovit počet; každé volání ResumeProfile odečte 1.

 Pokud je počet Pozastavení/Obnovení větší než 0, stav Pozastavit/Obnovit pro úroveň je VYPNUTO. Pokud je počet menší nebo roven 0, stav Pozastavit/Pokračovat je zapnuto.

 Když jsou stav Start/Stop a Stav Pozastavení/Obnovení zapnuty, stav profilování pro úroveň je zapnuto. Aby bylo vlákno profilováno, musí být všechny globální stavy, stavy úrovně procesu a vlákna pro vlákno zapnuty.

## <a name="net-framework-equivalent"></a>Ekvivalent rozhraní .NET Framework
 *Soubor Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Informace o funkci
 Záhlaví: Deklarováno v *VSPerf.h*

 Knihovna importu: *VSPerf.lib*

## <a name="example"></a>Příklad
 Následující příklad ilustruje funkci ResumeProfile. Příklad předpokládá, že volání Metody SuspendProfile bylo provedeno pro stejné vlákno nebo proces identifikovaný [PROFILE_CURRENTID](../profiling/profile-currentid.md).

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

## <a name="see-also"></a>Viz také
- [Odkaz na rozhraní API profileru sady Visual Studio (nativní)](../profiling/visual-studio-profiler-api-reference-native.md)
