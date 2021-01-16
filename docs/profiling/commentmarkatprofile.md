---
title: CommentMarkAtProfile | Microsoft Docs
description: Použijte metodu CommentMarkAtProfile k vložení hodnoty časového razítka, číselné značky a řetězce komentáře do souboru. vsp.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 43e8f9806c724da414940c92b6609846486a49c0
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533521"
---
# <a name="commentmarkatprofile"></a>CommentMarkAtProfile
`CommentMarkAtProfile`Metoda vloží hodnotu časového razítka, číselnou značku a řetězec komentáře do souboru *. vsp* . Hodnota časového razítka se dá použít k synchronizaci externích událostí. Pro vložení značky a komentáře musí být profilace vlákna obsahující funkci CommentMarkAtProfile ZAPNUTá.

## <a name="syntax"></a>Syntaxe

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (
                                   __int64 dnTimestamp,
                                   long lMarker,
                                   LPCTSTR szComment);
```

#### <a name="parameters"></a>Parametry
 `dnTimestamp`

 64 celé číslo, které představuje hodnotu časového razítka.

 `lMarker`

 Číselná značka, která má být vložena. Značka musí být větší než nebo rovna 0 (nula).

 `szComment`

 Ukazatel na textový řetězec, který má být vložen. Řetězec musí být kratší než 256 znaků, včetně ukončovacího znaku NULL.

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
 Stav profilace vlákna obsahujícího profil značky musí být zapnutý, pokud jsou značky a komentáře vložené pomocí příkazu Mark nebo s funkcemi rozhraní API (CommentMarkAtProfile, CommentMarkProfile nebo MarkProfile). Značky profilu jsou v oboru globální. Například značka Profile vložená v jednom vlákně může být použita k označení začátku nebo konce datového segmentu v jakémkoli vlákně v souboru. vsp.

> [!IMPORTANT]
> Metody CommentMarkAtProfile by se měly používat jenom s instrumentací.

## <a name="net-framework-equivalent"></a>Ekvivalent .NET Framework
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Informace o funkci

|Položka|Hodnota|
|-|-|
|**Hlavička**|Zahrnout *VSPerf. h*|
|**Knihovna**|Použití *VSPerf. lib*|
|**Kódování Unicode**|Implementováno jako CommentMarkAtProfileW (Unicode) a CommentMarkAtProfileA (ANSI).|

## <a name="example"></a>Příklad
 Následující kód ilustruje použití volání obecné funkce CommentMarkAtProfile. Příklad předpokládá použití maker řetězců Win32 a nastavení kompilátoru pro ANSI k určení, zda kód volá funkci s povoleným kódováním ANSI.

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

## <a name="see-also"></a>Viz také:
- [Referenční dokumentace rozhraní API pro Visual Studio Profiler (nativní)](../profiling/visual-studio-profiler-api-reference-native.md)
