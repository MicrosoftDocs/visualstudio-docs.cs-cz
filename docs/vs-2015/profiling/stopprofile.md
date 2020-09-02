---
title: StopProfile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- StopProfile
ms.assetid: be75b03c-7af5-4abe-a54a-6ee5479ad877
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b8be45de29f379161845cc7ba8ec58d2d1bc9285
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193303"
---
# <a name="stopprofile"></a>StopProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`StopProfile`Funkce nastaví čítač na hodnotu 0 (vypnuto) pro zadanou úroveň profilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI StopProfile(  
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
  
## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 Funkce označuje úspěch nebo neúspěch pomocí **PROFILE_COMMAND_STATUS** výčtu. Návratová hodnota může být jedna z následujících:  
  
|Čítače|Popis|  
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
  
## <a name="net-framework-equivalent"></a>Ekvivalent v rozhraní .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informace o funkci  
 Hlavička: deklaruje se v VSPerf. h  
  
 Knihovna importu: VSPerf. lib  
  
## <a name="example"></a>Příklad  
 Následující příklad ilustruje metodu StopProfile. Příklad předpokládá, že volání metody StartProfile bylo provedeno pro stejné vlákno nebo proces identifikovaný [PROFILE_CURRENTID](../profiling/profile-currentid.md).  
  
```  
void ExerciseStopProfile()  
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
  
    // Declare enumeration to hold result of call  
    // to StopProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = StopProfile(  
        PROFILE_THREADLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("StopProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace rozhraní API pro Visual Studio Profiler (nativní)](../profiling/visual-studio-profiler-api-reference-native.md)
