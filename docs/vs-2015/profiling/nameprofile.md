---
title: NameProfile | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- NameProfile
- NameProfileA
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e56788c36e8c77ec134ed24a7636475c54da664
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733832"
---
# <a name="nameprofile"></a>NameProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`NameProfile` Funkce přiřadí řetězec zadaný proces nebo vlákno.  
  
 Rozhraní API NameProfile je k dispozici pouze pro profilaci instrumentace. Rozhraní API NameProfile se nepodporuje pro profilaci vzorkování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(  
                                   LPCTSTR pszName,   
                                   PROFILE_CONTROL_LEVEL Level,  
                                   unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszName`  
  
 Název elementu profilování. Název je neplatný (výsledkem je návratová NAME_ERROR_INVALID_NAME NameProfileA), pokud:  
  
- Ukazatel předaný do NameProfileA je hodnota NULL  
  
- Data řetězce pszName začíná číslem  
  
- Data řetězce pszName obsahuje mezeru  
  
- Data řetězce pszName obsahuje některý z následujících znaků:,. ' ~! @# $% ^ & * () = []{}&#124;\\? / <>  
  
  `Level`  
  
  Informuje o úrovni profil, ke které výkonu shromažďování dat lze použít. Následující **PROFILE_CONTROL_LEVEL** hodnoty můžete použít k označení jednu ze tří úrovní výkonu, které lze použít shromažďování dat:  
  
|Enumerátor|Popis|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|Globální nastavení úrovně má vliv na všechny procesy a vlákna při spuštění profilace.|  
|PROFILE_PROCESSLEVEL|Nastavení úrovně procesu mít vliv na všechna vlákna, které jsou součástí určeného procesu.|  
|PROFILE_THREADLEVEL|Vlákno profilace nastavení úrovně má vliv na zadaný podproces.|  
  
 `dwId`  
  
 Profilace úrovně identifikátor. Použití procesu nebo vlákna identifikátor, který je generováno systémem.  
  
## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 Funkce označuje úspěch nebo neúspěch pomocí **PROFILE_COMMAND_STATUS** výčtu. Návratová hodnota může být jeden z následujících akcí:  
  
|Enumerátor|Popis|  
|----------------|-----------------|  
|NAME_ERROR_ID_NOEXIST|Profilace Zadaný prvek neexistuje.|  
|NAME_ERROR_INVALID_NAME|Název je neplatný.|  
|NAME_ERROR_LEVEL_NOEXIST|Zadaná úroveň profilu neexistuje.|  
|NAME_ERROR_NO_SUPPORT|Zadaná operace není podporována.|  
|NAME_ERROR_OUTOFMEMORY|Paměť není k dispozici k zaznamenání události.|  
|NAME_ERROR_REDEFINITION|Název se už přiřadit k elementu profilu. Název této funkce se ignoruje.|  
|NAME_ERROR_TEXTTRUNCATED|Text názvu překročilo 32 znaků včetně znak null a byl proto zkrácen.|  
|NAME_OK|Název byl úspěšně zaregistrován.|  
  
## <a name="remarks"></a>Poznámky  
 Pro každý proces nebo vlákno lze přiřadit pouze jeden název. Po profilování prvek má název, jsou ignorovány následných volání NameProfile pro daný element.  
  
 Pokud je na různých vláknech či procesy se stejným názvem, sestava bude obsahovat data ze všech prvků na této úrovni s tímto názvem.  
  
 Pokud zadáte proces nebo vlákno než tu, musí se ujistěte, že inicializovat a spuštěn dříve, než použijete název. V opačném případě metoda NameProfile selže.  
  
> [!IMPORTANT]
>  CreateProcess() a rozhraní API CreateThread() funkce může vrátit před vlákna nebo procesu je inicializován.  
  
## <a name="net-framework-equivalent"></a>Ekvivalent v rozhraní .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informace o funkci  
  
|||  
|-|-|  
|**Záhlaví**|Zahrnout VSPerf.h|  
|**Knihovna**|Použití VSPerf.lib|  
|**Unicode**|Implementováno jako `NameProfileW` (Unicode) a `NameProfileA` (ANSI).|  
  
## <a name="example"></a>Příklad  
 Následující kód znázorňuje volání funkce NameProfile. Příklad předpokládá použití maker řetězec Win32 a nastavení kompilátoru standardu ANSI k určení, zda kód volá ANSI povolena funkce.  
  
```  
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
 [Referenční dokumentace rozhraní Visual Studio Profiler API (nativní)](../profiling/visual-studio-profiler-api-reference-native.md)



