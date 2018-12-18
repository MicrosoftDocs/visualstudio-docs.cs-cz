---
title: CommentMarkAtProfile | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkAtProfile
- CommentMarkAtProfileA
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4eb29336b401b020df52d1ccaa743bb7240e1d2b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854816"
---
# <a name="commentmarkatprofile"></a>CommentMarkAtProfile
`CommentMarkAtProfile` Metoda vloží hodnoty časového razítka, číselné značku a řetězec komentáře v. *Vsp* souboru. Hodnota časového razítka je možné synchronizovat vnější události. Značky a komentáře, které má být vložen profilování pro vlákna, které obsahuje funkci CommentMarkAtProfile musí být dále.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (  
                                   __int64 dnTimestamp,  
                                   long lMarker,  
                                   LPCTSTR szComment);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dnTimestamp`  
  
 64bitové celé číslo, který představuje hodnotu časového razítka.  
  
 `lMarker`  
  
 Číselné značky pro vložení. Značky musí být větší než nebo rovna 0 (nula).  
  
 `szComment`  
  
 Ukazatel na textový řetězec pro vložení. Řetězec musí být kratší než 256 znaků včetně ukončovacího znaku NULL.  
  
## <a name="property-valuereturn-value"></a>Vlastnost hodnota nebo návratová hodnota  
 Funkce označuje úspěch nebo neúspěch pomocí **PROFILE_COMMAND_STATUS** výčtu. Návratová hodnota může být jeden z následujících akcí:  
  
|Enumerátor|Popis|  
|----------------|-----------------|  
|MARK_ERROR_MARKER_RESERVED|Parametr je menší než nebo rovna 0. Tyto hodnoty jsou vyhrazené. Nejsou zaznamenána značky a komentáře.|  
|MARK_ERROR_MODE_NEVER|Režimu profilace byla nastavena na nikdy, když byla volána funkce. Nejsou zaznamenána značky a komentáře.|  
|MARK_ERROR_MODE_OFF|Režimu profilace byl nastaven na hodnotu OFF, když byla volána funkce. Nejsou zaznamenána značky a komentáře.|  
|MARK_ERROR_NO_SUPPORT|Bez podpory označení v tomto kontextu. Nejsou zaznamenána značky a komentáře.|  
|MARK_ERROR_OUTOFMEMORY|Paměť není k dispozici k zaznamenání události. Nejsou zaznamenána značky a komentáře.|  
|MARK_TEXTTOOLONG|Řetězec překračuje maximum 256 znaků. Komentář řetězce zkráceny a značky a komentáře se zaznamenávají.|  
|MARK_OK|MARK_OK je vrácena, čímž indikuje úspěšné provedení.|  
  
## <a name="remarks"></a>Poznámky  
 Profilace stav podprocesu, který obsahuje funkci profilu značky musí být na značky a komentáře vložená značka příkaz nebo s funkcí rozhraní API (CommentMarkAtProfile, CommentMarkProfile nebo MarkProfile). Profil značky jsou globální v oboru. Například profil značky vložení v jednom vlákně slouží k označení začátku nebo konci segmentu dat v jakékoli vlákno do souboru .vsp.  
  
> [!IMPORTANT]
>  CommentMarkAtProfile metody by měla sloužit s pouze instrumentace.  
  
## <a name="net-framework-equivalent"></a>Ekvivalent .NET framework  
 *Microsoft.VisualStudio.Profiler.dll*  
  
## <a name="function-information"></a>Informace o funkci  
  
|||  
|-|-|  
|**Záhlaví**|Zahrnout *VSPerf.h*|  
|**Knihovna**|Použití *VSPerf.lib*|  
|**Unicode**|Implementovat jako CommentMarkAtProfileW (Unicode) a CommentMarkAtProfileA (ANSI).|  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje použití CommentMarkAtProfile obecná funkce volání. Příklad předpokládá použití maker řetězec Win32 a nastavení kompilátoru standardu ANSI k určení, zda kód volá ANSI povolena funkce.  
  
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
 [Referenční dokumentace jazyka Visual Studio Profiler API (nativní)](../profiling/visual-studio-profiler-api-reference-native.md)