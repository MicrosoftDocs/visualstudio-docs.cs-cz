---
title: MarkProfile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MarkProfile
ms.assetid: 54dac8c8-c8ee-4023-af27-b25466e3a6ec
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f53b51f9e78e2cb5d327abd3a79ebf2faa3a9204
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74778567"
---
# <a name="markprofile"></a>MarkProfile
`MarkProfile`Metoda vloží značku profilu do.* soubor VSP* . `MarkProfile`Pro vložení značky musí být profilace vlákna obsahující funkci zapnutá.

## <a name="syntax"></a>Syntaxe

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI MarkProfile( long lMarker );
```

#### <a name="parameters"></a>Parametry
 `lMarker`

 Značka, která se má vložit Značka musí být větší než nebo rovna 0 (nula).

## <a name="property-valuereturn-value"></a>Hodnota nebo návratová hodnota vlastnosti
 Funkce označuje úspěch nebo neúspěch pomocí **PROFILE_COMMAND_STATUS** výčtu. Návratová hodnota může být jedna z následujících:

|Čítače|Popis|
|----------------|-----------------|
|MARK_ERROR_MARKER_RESERVED|Parametr je menší nebo roven 0. Tyto hodnoty jsou rezervované. Značka a komentář nejsou zaznamenávány.|
|MARK_ERROR_MODE_NEVER|Režim profilace byl nastaven na hodnotu nikdy při volání funkce. Značka a komentář nejsou zaznamenávány.|
|MARK_ERROR_MODE_OFF|Režim profilace byl nastaven na hodnotu OFF při volání funkce. Značka a komentář nejsou zaznamenávány.|
|MARK_ERROR_NO_SUPPORT|V tomto kontextu není podporována žádná podpora značek. Značka a komentář nejsou zaznamenávány.|
|MARK_ERROR_OUTOFMEMORY|Paměť nebyla k dispozici pro záznam události. Značka a komentář nejsou zaznamenávány.|
|MARK_TEXTTOOLONG|Řetězec překračuje maximální 256 znaků. Řetězec komentáře je zkrácen a je zaznamenána značka a komentář.|
|MARK_OK|MARK_OK je vráceno pro indikaci úspěchu.|

## <a name="remarks"></a>Poznámky
 Hodnota značky je vložena do. soubor *VSP* pokaždé, když se kód spustí, pokud je vlákno obsahující funkci MarkProfile profilace. Můžete volat MarkProfile víckrát.

 Značky profilu jsou v oboru globální. Například značka Profile vložená v jednom vlákně může být použita k označení začátku nebo konce datového segmentu v jakémkoli vlákně v. soubor *VSP* .

 Stav profilace vlákna obsahujícího profil značky musí být zapnutý, pokud jsou značky a komentáře vložené pomocí příkazu Mark nebo s funkcemi rozhraní API (CommentMarkAtProfile, CommentMarkProfile nebo MarkProfile).

> [!IMPORTANT]
> Metoda MarkProfile by měla být použita pouze s profilací instrumentace.

## <a name="net-framework-equivalent"></a>Ekvivalent .NET Framework
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Informace o funkci
 Hlavička: deklaruje se v *VSPerf. h*

 Knihovna importu: *VSPerf. lib*

## <a name="example"></a>Příklad
 Následující kód ilustruje funkci MarkProfile.

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

## <a name="see-also"></a>Viz také
- [Referenční dokumentace rozhraní API pro Visual Studio Profiler (nativní)](../profiling/visual-studio-profiler-api-reference-native.md)
