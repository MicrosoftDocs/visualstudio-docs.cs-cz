---
title: CommentmarkatProfile | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkAtProfile
- CommentMarkAtProfileA
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 51028dce1d60c0d01c83cee509a1ed7321855437
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777839"
---
# <a name="commentmarkatprofile"></a>CommentMarkAtProfile
Metoda `CommentMarkAtProfile` vloží hodnotu časového razítka, číselnou značku a řetězec komentáře do . *vsp.* Hodnotu časového razítka lze použít k synchronizaci externích událostí. Chcete-li vložit značku a komentář, musí být profilování pro vlákno, které obsahuje funkci CommentMarkAtProfile, ZAPNUTO.

## <a name="syntax"></a>Syntaxe

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (
                                   __int64 dnTimestamp,
                                   long lMarker,
                                   LPCTSTR szComment);
```

#### <a name="parameters"></a>Parametry
 `dnTimestamp`

 64bitové celé číslo představující hodnotu časového razítka.

 `lMarker`

 Číselná značka, kterou chcete vložit. Značka musí být větší nebo rovna 0 (nula).

 `szComment`

 Ukazatel na textový řetězec, který chcete vložit. Řetězec musí být menší než 256 znaků včetně zakončení NULL.

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
 Stav profilování pro vlákno, které obsahuje funkci profilu značky, musí být zapnutý, když jsou značky a komentáře vloženy pomocí příkazu Označit nebo s funkcemi rozhraní API (CommentMarkAtProfile, CommentMarkProfile nebo MarkProfile). Značky profilu mají globální rozsah. Například značku profilu vloženou do jednoho vlákna lze použít k označení začátku nebo konce datového segmentu v libovolném vlákně v souboru .vsp.

> [!IMPORTANT]
> CommentMarkAtProfile metody by měly být používány pouze s instrumentace.

## <a name="net-framework-equivalent"></a>Ekvivalent rozhraní .NET Framework
 *Soubor Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Informace o funkci

|||
|-|-|
|**Záhlaví**|Zahrnout *VSPerf.h*|
|**Knihovna**|Použití *souboru VSPerf.lib*|
|**Unicode**|Implementováno jako CommentMarkAtProfileW (Unicode) a CommentMarkAtProfileA (ANSI).|

## <a name="example"></a>Příklad
 Následující kód ilustruje použití volání obecné funkce CommentMarkAtProfile. Příklad předpokládá použití makra řetězce Win32 a nastavení kompilátoru pro ANSI k určení, zda kód volá funkci povolenou ANSI.

```cpp
void ExerciseCommentMarkAtProfile(void)
{
    // Declare and initalize variables to pass to
    // CommentMarkAtProfile.  The values of these
    // parameters are assigned based on the needs
    // of the code; and for the sake of simplicity
    // in this example, the variables are assigned
    // arbitrary values.
    int64 timeStamp = 0x1111;
    long markId = 01;
    TCHAR * markText = TEXT("Exercising CommentMarkAtProfile...");

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare MarkOperationResult Enumerator.
    // Holds return value from call to CommentMarkAtProfile.
    PROFILE_COMMAND_STATUS markResult;

    markResult = CommentMarkAtProfile(
        timeStamp,
        markId,
        markText);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("CommentMarkAtProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
    pszTxt, markResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Viz také
- [Odkaz na rozhraní API profileru sady Visual Studio (nativní)](../profiling/visual-studio-profiler-api-reference-native.md)
