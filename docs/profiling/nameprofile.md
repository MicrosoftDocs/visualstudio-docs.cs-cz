---
title: NameProfile | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NameProfile
- NameProfileA
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d9f0c9a3259186e1581a4673cdc18d1554e92b3c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778489"
---
# <a name="nameprofile"></a>NameProfile
Funkce `NameProfile` přiřadí řetězec zadanému procesu nebo vláknu.

 Rozhraní NameProfile API je k dispozici pouze pro profilování instrumentace. Rozhraní NameProfile API není podporováno pro profilování vzorkování.

## <a name="syntax"></a>Syntaxe

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(
                                   LPCTSTR pszName,
                                   PROFILE_CONTROL_LEVEL Level,
                                   unsigned int dwId);
```

#### <a name="parameters"></a>Parametry
 `pszName`

 Název prvku profilování. Název je neplatný (výsledkem je vrácení NAME_ERROR_INVALID_NAME NameProfileA), pokud:

- Ukazatel předaný do NameProfileA je hodnota NULL

- Řetězcová data pszName začíná číslem

- Řetězcová data pszName obsahuje mezeru

- Řetězcová data pszName obsahuje některý z následujících znaků: ,;. '~!@@#$%^&*()=[]{}&#124;\\?/<>

  `Level`

  Označuje úroveň profilu, na kterou lze použít shromažďování dat o výkonu. Následující **PROFILE_CONTROL_LEVEL** hodnoty lze použít k označení jedné ze tří úrovní, na které lze použít shromažďování dat o výkonu:

|Čítač výčtu|Popis|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|Nastavení globální úrovně ovlivňuje všechny procesy a vlákna v profilování spustit.|
|PROFILE_PROCESSLEVEL|Nastavení úrovně procesu ovlivní všechna vlákna, která jsou součástí zadaného procesu.|
|PROFILE_THREADLEVEL|Nastavení úrovně profilování vláken ovlivňuje zadané vlákno.|

 `dwId`

 Identifikátor úrovně profilování. Použijte identifikátor procesu nebo vlákna, který je generován systémem.

## <a name="property-valuereturn-value"></a>Hodnota/vrácená hodnota nemovitosti
 Funkce označuje úspěch nebo neúspěch pomocí **PROFILE_COMMAND_STATUS** výčtu. Vrácená hodnota může být jedna z následujících hodnot:

|Čítač výčtu|Popis|
|----------------|-----------------|
|NAME_ERROR_ID_NOEXIST|Zadaný profilovací prvek neexistuje.|
|NAME_ERROR_INVALID_NAME|Název je neplatný.|
|NAME_ERROR_LEVEL_NOEXIST|Zadaná úroveň profilu neexistuje.|
|NAME_ERROR_NO_SUPPORT|Zadaná operace není podporována.|
|NAME_ERROR_OUTOFMEMORY|K zaznamenání události nebyla k dispozici paměť.|
|NAME_ERROR_REDEFINITION|K prvku profilu již byl přiřazen název. Název v této funkci je ignorován.|
|NAME_ERROR_TEXTTRUNCATED|Text názvu překročil 32 znaků včetně znaku null a byl proto zkrácen.|
|NAME_OK|Název byl úspěšně zaregistrován.|

## <a name="remarks"></a>Poznámky
 Ke každému procesu nebo vláknu lze přiřadit pouze jeden název. Po profilování prvek je pojmenován, následné volání NameProfile pro tento prvek jsou ignorovány.

 Pokud je stejný název přidělen různým vláknům nebo procesům, sestava bude obsahovat data ze všech prvků na této úrovni s tímto názvem.

 Pokud zadáte jiný proces nebo vlákno než aktuální, musíte se ujistit, že byl inicializován a spuštěn před jeho pojmenováním. V opačném případě se metoda NameProfile nezdaří.

> [!IMPORTANT]
> CreateProcess() a CreateThread() API funkce může vrátit před inicializování podprocesu nebo procesu.

## <a name="net-framework-equivalent"></a>Ekvivalent rozhraní .NET Framework
 *Soubor Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Informace o funkci

|||
|-|-|
|**Záhlaví**|Zahrnout *VSPerf.h*|
|**Knihovna**|Použití *souboru VSPerf.lib*|
|**Unicode**|Implementována jako `NameProfileW` (Unicode) a `NameProfileA` (ANSI).|

## <a name="example"></a>Příklad
 Následující kód ilustruje volání funkce NameProfile. Příklad předpokládá použití makra řetězce Win32 a nastavení kompilátoru pro ANSI k určení, zda kód volá funkci povolenou ANSI.

```cpp
void ExerciseNameProfile()
{
    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Create and initialize variables to pass to
    // ExerciseNameProfile.  The value of this
    // parameter is based on the needs of the code;
    // and for the sake of simplicity in this example,
    // the variable is assigned an arbitrary value.
    TCHAR * profileName = TEXT("ExerciseNameProfile");

    // Declare enumeration to hold result of call to
    // ExerciseNameProfle.
    PROFILE_COMMAND_STATUS nameResult;

    nameResult =  NameProfile(
        profileName,
        PROFILE_GLOBALLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("NameProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, nameResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Viz také
- [Odkaz na rozhraní API profileru sady Visual Studio (nativní)](../profiling/visual-studio-profiler-api-reference-native.md)
