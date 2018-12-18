---
title: MarkProfile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- MarkProfile
ms.assetid: 54dac8c8-c8ee-4023-af27-b25466e3a6ec
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 98530a790963d1c7fc60742dda4bb16e14a28ab4
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2018
ms.locfileid: "35238157"
---
# <a name="markprofile"></a>MarkProfile
`MarkProfile` Metoda vloží značku profil v. *Vsp* souboru. Profilace pro přístup z více vláken obsahující `MarkProfile` funkce musí být ON pro značku, která má být vložen.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
PROFILE_COMMAND_STATUS PROFILERAPI MarkProfile( long lMarker );  
```  
  
#### <a name="parameters"></a>Parametry  
 `lMarker`  
  
 Značky pro vložení. Značky musí být větší než nebo rovno 0 (nula).  
  
## <a name="property-valuereturn-value"></a>Vlastnost Hodnota/Návratová hodnota  
 Funkce označuje úspěch či neúspěch pomocí **PROFILE_COMMAND_STATUS** výčtu. Vrácená hodnota může být jeden z následujících akcí:  
  
|Enumerátor|Popis|  
|----------------|-----------------|  
|MARK_ERROR_MARKER_RESERVED|Parametr je menší než nebo rovna 0. Tyto hodnoty jsou vyhrazené. Značky a komentáře nejsou popsané.|  
|MARK_ERROR_MODE_NEVER|Profilování režimu byl nastaven na nikdy, při volání funkce. Značky a komentáře nejsou popsané.|  
|MARK_ERROR_MODE_OFF|Profilování režimu byl nastaven na hodnotu OFF, při volání funkce. Značky a komentáře nejsou popsané.|  
|MARK_ERROR_NO_SUPPORT|Nepodporuje označit v tomto kontextu. Značky a komentáře nejsou popsané.|  
|MARK_ERROR_OUTOFMEMORY|Paměť nebyl k dispozici k zaznamenání události. Značky a komentáře nejsou popsané.|  
|MARK_TEXTTOOLONG|Řetězec překračuje maximální povolenou délku 256 znaků. Řetězec komentáře zkrácen a značky a komentáře se zaznamenávají.|  
|MARK_OK|MARK_OK je vrácen do indikuje úspěšné provedení.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnota značky vložena do. *vsp* souboru při každém spuštění kódu pokud je profilovaný vlákno obsahující MarkProfile funkce. MarkProfile můžete volat vícekrát.  
  
 Profil značky jsou globální v oboru. Například profil značka vložen do jedno vlákno slouží k označení počáteční nebo koncové segmentu dat v jakékoli vlákno v. *vsp* souboru.  
  
 Profilování stavu podprocesu, který obsahuje funkci profilu značky musí být v značky a komentáře vložit příkaz Označit nebo s funkcí rozhraní API (CommentMarkAtProfile, CommentMarkProfile nebo MarkProfile).  
  
> [!IMPORTANT]
>  Metoda MarkProfile musí být použit s pouze profilace instrumentace.  
  
## <a name="net-framework-equivalent"></a>Ekvivalent v rozhraní .NET framework  
 *Microsoft.VisualStudio.Profiler.dll*  
  
## <a name="function-information"></a>Informace o funkci  
 Záhlaví: Deklarované v *VSPerf.h*  
  
 Import knihovny: *VSPerf.lib*  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje MarkProfile funkce.  
  
```cpp  
void ExerciseMarkProfile()  
{  
    // Declare and initialize variables to pass to   
    // MarkProfile.  The values of these parameters   
    // are assigned based on the needs of the code;  
    // and for the sake of simplicity in this example,   
    // the variables are assigned arbitrary values.  
    int markId = 03;  
  
    // Declare enumeration to hold return value of   
    // call to MarkProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    markResult = MarkProfile(markId);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("MarkProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Viz také:  
 [Visual Studio profiler referenční dokumentace rozhraní API (nativní)](../profiling/visual-studio-profiler-api-reference-native.md)