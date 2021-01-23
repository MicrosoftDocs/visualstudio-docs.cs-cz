---
title: NameProfile | Microsoft Docs
description: Přečtěte si, jak funkce NameProfile přiřadí řetězec do zadaného procesu nebo vlákna. Rozhraní NameProfile API je také k dispozici pouze pro profilaci instrumentace.
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
ms.openlocfilehash: 3bd210f1d92245889be8d18156c43e0cad7ee3db
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722916"
---
# <a name="nameprofile"></a>NameProfile
`NameProfile`Funkce přiřadí řetězec do zadaného procesu nebo vlákna.

 Rozhraní NameProfile API je dostupné jenom pro profilaci instrumentace. Pro profilaci vzorkování není podporováno rozhraní NameProfile API.

## <a name="syntax"></a>Syntaxe

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(
                                   LPCTSTR pszName,
                                   PROFILE_CONTROL_LEVEL Level,
                                   unsigned int dwId);
```

#### <a name="parameters"></a>Parametry
 `pszName`

 Název elementu profilace. Název je neplatný (výsledkem NameProfileA návratové NAME_ERROR_INVALID_NAME), pokud:

- Ukazatel předaný do NameProfileA je hodnota NULL.

- Řetězcová data pszName začínají číslem

- Řetězcová data pszName obsahují mezeru.

- Řetězcová data pszName obsahují kterýkoli z následujících znaků:,;. ~! @ # $% ^& * () = [] {}&#124;\\ ?/<>

  `Level`

  Označuje úroveň profilu, na kterou lze použít shromažďování dat výkonu. Následující hodnoty **PROFILE_CONTROL_LEVEL** lze použít k označení jedné ze tří úrovní, na které lze použít shromažďování dat výkonu:

|Čítače|Popis|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|Nastavení globální úrovně má vliv na všechny procesy a vlákna v rámci procesu profilace.|
|PROFILE_PROCESSLEVEL|Nastavení na úrovni procesu ovlivňuje všechna vlákna, která jsou součástí zadaného procesu.|
|PROFILE_THREADLEVEL|Nastavení úrovně profilace vlákna má vliv na zadané vlákno.|

 `dwId`

 Identifikátor úrovně profilace. Použijte proces nebo identifikátor vlákna, který je generován systémem.

## <a name="property-valuereturn-value"></a>Hodnota nebo návratová hodnota vlastnosti
 Funkce označuje úspěch nebo neúspěch pomocí **PROFILE_COMMAND_STATUS** výčtu. Návratová hodnota může být jedna z následujících:

|Čítače|Popis|
|----------------|-----------------|
|NAME_ERROR_ID_NOEXIST|Zadaný element profilace neexistuje.|
|NAME_ERROR_INVALID_NAME|Název není platný.|
|NAME_ERROR_LEVEL_NOEXIST|Zadaná úroveň profilu neexistuje.|
|NAME_ERROR_NO_SUPPORT|Zadaná operace není podporována.|
|NAME_ERROR_OUTOFMEMORY|Paměť nebyla k dispozici pro záznam události.|
|NAME_ERROR_REDEFINITION|K elementu profilu byl již přiřazen název. Název této funkce je ignorován.|
|NAME_ERROR_TEXTTRUNCATED|Text názvu přesáhl 32 znaků, včetně znaku null a byl proto zkrácen.|
|NAME_OK|Název se úspěšně zaregistroval.|

## <a name="remarks"></a>Poznámky
 Každému procesu nebo vláknu lze přiřadit pouze jeden název. Po pojmenování elementu profilování jsou následná volání NameProfile pro daný prvek ignorována.

 Pokud je stejný název přidělen různým vláknům nebo procesům, sestava bude obsahovat data ze všech prvků na této úrovni s tímto názvem.

 Pokud zadáte jiný proces nebo vlákno než aktuální, musíte se ujistit, že byl inicializován a spuštěn před jeho pojmenování. V opačném případě se metoda NameProfile nezdařila.

> [!IMPORTANT]
> Funkce rozhraní API CreateProcess () a CreateThread () mohou vracet před inicializací vlákna nebo procesu.

## <a name="net-framework-equivalent"></a>Ekvivalent .NET Framework
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Informace o funkci

|Položka|Hodnota|
|-|-|
|**Hlavička**|Zahrnout *VSPerf. h*|
|**Knihovna**|Použití *VSPerf. lib*|
|**Kódování Unicode**|Implementováno jako `NameProfileW` (Unicode) a `NameProfileA` (ANSI).|

## <a name="example"></a>Příklad
 Následující kód ilustruje volání funkce NameProfile. Příklad předpokládá použití maker řetězců Win32 a nastavení kompilátoru pro ANSI k určení, zda kód volá funkci s povoleným kódováním ANSI.

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
- [Referenční dokumentace rozhraní API pro Visual Studio Profiler (nativní)](../profiling/visual-studio-profiler-api-reference-native.md)
