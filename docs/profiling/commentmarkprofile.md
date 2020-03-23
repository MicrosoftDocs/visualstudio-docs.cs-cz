---
title: CommentMarkProfile | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkProfile
- CommentMarkProfileA
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d45bab6b909fffa107158236d9050632f114c530
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772781"
---
# <a name="commentmarkprofile"></a>CommentMarkProfile
Funkce `CommentMarkProfile` vloží číselnou značku a textový řetězec do pole . *vsp.* Chcete-li vložit značku a komentář, musí být profilování vlákna, které obsahuje `CommentMarkProfile` funkci, zapnuto.

## <a name="syntax"></a>Syntaxe

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(
                                   long lMarker,
                                   LPCTSTR szComment);
```

#### <a name="parameters"></a>Parametry
 `lMarker`

 Číselná značka, která chcete vložit. Značka musí být větší nebo rovna 0 (nula).

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
 Stav profilování pro vlákno, které obsahuje funkci profilu značky, musí být zapnutý, když jsou značky a komentáře vloženy s příkazem VSInstr Mark nebo s funkcemi (CommentMarkAtProfile, CommentMarkProfile nebo MarkProfile).

 Značky profilu mají globální rozsah. Například značku profilu vloženou do jednoho vlákna lze použít k označení začátku nebo konce datového segmentu v libovolném vlákně v . *vsp.*

> [!IMPORTANT]
> CommentMarkProfile metodu lze použít pouze s instrumentací.

## <a name="net-framework-equivalent"></a>Ekvivalent rozhraní .NET Framework
 Soubor Microsoft.VisualStudio.Profiler.dll

## <a name="function-information"></a>Informace o funkci

|||
|-|-|
|**Záhlaví**|Zahrnout VSPerf.h|
|**Knihovna**|Použití souboru VSPerf.lib|
|**Unicode**|Implementována jako `CommentMarkProfileW` (Unicode) a `CommentMarkProfileA` (ANSI).|

## <a name="example"></a>Příklad
 Následující kód ilustruje volání funkce CommentMarkProfile. Příklad předpokládá použití makra řetězce Win32 a nastavení kompilátoru Unicode k určení, zda kód volá volání [!INCLUDE[vcpransi](../profiling/includes/vcpransi_md.md)] funkce.

```cpp
void ExerciseCommentMarkProfile()
{
    // Declare and initalize variables to pass to
    // CommentMarkProfile.  The values of these
    // parameters are assigned based on the needs
    // of the code; and for the sake of simplicity
    // in this example, the variables are assigned
    // arbitrary values.
    long markId = 01;
    TCHAR * markText = TEXT("Exercising CommentMarkProfile...");

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare MarkOperationResult Enumerator.
    // Holds return value from call to CommentMarkProfile.
    PROFILE_COMMAND_STATUS markResult;

    markResult = CommentMarkProfile(
        markId,
        markText);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("CommentMarkProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, markResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Viz také
- [Odkaz na rozhraní API profileru sady Visual Studio (nativní)](../profiling/visual-studio-profiler-api-reference-native.md)
