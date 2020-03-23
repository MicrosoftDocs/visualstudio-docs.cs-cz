---
title: MarkProfile | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778567"
---
# <a name="markprofile"></a>MarkProfile
Metoda `MarkProfile` vloží značku profilu do . *vsp.* Profilování pro vlákno obsahující `MarkProfile` funkci musí být zapnuto, aby byla značka vložena.

## <a name="syntax"></a>Syntaxe

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI MarkProfile( long lMarker );
```

#### <a name="parameters"></a>Parametry
 `lMarker`

 Značka, kterou chcete vložit. Značka musí být větší nebo rovna 0 (nula).

## <a name="property-valuereturn-value"></a>Hodnota/vrácená hodnota nemovitosti
 Funkce označuje úspěch nebo neúspěch pomocí **PROFILE_COMMAND_STATUS** výčtu. Vrácená hodnota může být jedna z následujících hodnot:

|Čítač výčtu|Popis|
|----------------|-----------------|
|MARK_ERROR_MARKER_RESERVED|Parametr je menší nebo roven 0. Tyto hodnoty jsou vyhrazeny. Značka a komentář se nezaznamenávají.|
|MARK_ERROR_MODE_NEVER|Režim profilování byl nastaven na NIKDY, když byla volána funkce. Značka a komentář se nezaznamenávají.|
|MARK_ERROR_MODE_OFF|Režim profilování byl nastaven na vypnuto, když byla volána funkce. Značka a komentář se nezaznamenávají.|
|MARK_ERROR_NO_SUPPORT|Žádná podpora značky v tomto kontextu. Značka a komentář se nezaznamenávají.|
|MARK_ERROR_OUTOFMEMORY|K zaznamenání události nebyla k dispozici paměť. Značka a komentář se nezaznamenávají.|
|MARK_TEXTTOOLONG|Řetězec překračuje maximálně 256 znaků. Řetězec komentáře je zkrácen a značka a komentář jsou zaznamenány.|
|MARK_OK|MARK_OK je vrácena k označení úspěchu.|

## <a name="remarks"></a>Poznámky
 Hodnota značky je vložena do . *vsp* pokaždé, když se spustí kód, pokud je vlákno obsahující funkci MarkProfile profilováno. MarkProfile můžete volat vícekrát.

 Značky profilu mají globální rozsah. Například značku profilu vloženou do jednoho vlákna lze použít k označení začátku nebo konce datového segmentu v libovolném vlákně v . *vsp.*

 Stav profilování pro vlákno, které obsahuje funkci profilu značky, musí být zapnutý, když jsou značky a komentáře vloženy pomocí příkazu Označit nebo s funkcemi rozhraní API (CommentMarkAtProfile, CommentMarkProfile nebo MarkProfile).

> [!IMPORTANT]
> MarkProfile metoda by měla být použita pouze s instrumentace profilování.

## <a name="net-framework-equivalent"></a>Ekvivalent rozhraní .NET Framework
 *Soubor Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Informace o funkci
 Záhlaví: Deklarováno v *VSPerf.h*

 Knihovna importu: *VSPerf.lib*

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
- [Odkaz na rozhraní API profileru sady Visual Studio (nativní)](../profiling/visual-studio-profiler-api-reference-native.md)
