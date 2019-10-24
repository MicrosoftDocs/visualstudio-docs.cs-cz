---
title: 'Postupy: nastavení názvu vlákna v nativním kódu | Microsoft Docs'
ms.date: 12/17/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], threads
- SetThreadName function
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c85d0968-9f22-4d69-87f4-acca2ae777b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 1f9df52bee88722006c21c28e88a2e32113942e4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732748"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Postupy: Nastavení názvu vlákna v nativním kódu
Pojmenování vlákna je možné v libovolné verzi sady Visual Studio. Pojmenovávání vláken je užitečné pro identifikaci podprocesů zájmu v okně **vlákna** při ladění spuštěného procesu. Rozpoznatelně pojmenovaná vlákna můžou být užitečná také při provádění ladění po porážce prostřednictvím kontroly výpisu stavu systému a při analýze zachycení výkonu pomocí různých nástrojů.

## <a name="ways-to-set-a-thread-name"></a>Způsoby nastavení názvu vlákna

Existují dva způsoby, jak nastavit název vlákna. První je prostřednictvím funkce [SetThreadDescription](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) . Druhý je vyvoláním určité výjimky, pokud je k procesu připojen ladicí program sady Visual Studio. Každý přístup má výhody a upozornění. Použití `SetThreadDescription` se podporuje od Windows 10, verze 1607 nebo Windows Server 2016.

Je potřeba poznamenat, že _oba_ přístupy je možné v případě potřeby použít společně, protože mechanismy, kterými pracují, jsou nezávisle na sobě.

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>Nastavte název vlákna pomocí `SetThreadDescription`

Výhodnější
* Názvy vláken jsou viditelné při ladění v aplikaci Visual Studio bez ohledu na to, zda byl ladicí program připojen k procesu v době volání SetThreadDescription.
* Po načtení výpisu stavu systému v aplikaci Visual Studio jsou názvy vláken viditelné při provádění ladění po porážce.
* Názvy vláken jsou také viditelné při použití jiných nástrojů, jako je například ladicí program [WinDbg](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools) a analyzátor výkonu [Windows Performance Analyzer](https://docs.microsoft.com/windows-hardware/test/wpt/windows-performance-analyzer) .

Upozornění
* Názvy vláken jsou viditelné pouze v systému Visual Studio 2017 verze 15,6 a novějších verzích.
* Při ladění po porážce soubor s výpisem stavu systému jsou názvy vláken viditelné pouze v případě, že byla chyba vytvořena ve Windows 10 verze 1607, Windows Server 2016 nebo novějších verzích Windows.

*Případě*

```C++
#include <windows.h>
#include <processthreadsapi.h>

int main()
{
    HRESULT r;
    r = SetThreadDescription(
        GetCurrentThread(),
        L"ThisIsMyThreadName!"
    );

    return 0;
}
```

### <a name="set-a-thread-name-by-throwing-an-exception"></a>Nastavení názvu vlákna vyvoláním výjimky

Dalším způsobem, jak nastavit název vlákna v programu, je sdělit název požadovaného vlákna ladicímu programu sady Visual Studio vyvoláním speciálně nakonfigurované výjimky.

Výhodnější
* Funguje ve všech verzích sady Visual Studio.

Upozornění
* Funguje pouze v případě, že je ladicí program připojen v době, kdy je použita metoda založená na výjimce.
* Názvy vláken nastavené pomocí této metody nebudou k dispozici ve výpisech nebo nástrojích pro analýzu výkonu.

*Případě*

Níže uvedená funkce `SetThreadName` ukazuje tento přístup založený na výjimce. Všimněte si, že název vlákna bude automaticky zkopírován do vlákna, aby bylo možné uvolnit paměť pro parametr `threadName` po dokončení `SetThreadName` volání.

```C++
//
// Usage: SetThreadName ((DWORD)-1, "MainThread");
//
#include <windows.h>
const DWORD MS_VC_EXCEPTION = 0x406D1388;
#pragma pack(push,8)
typedef struct tagTHREADNAME_INFO
{
    DWORD dwType; // Must be 0x1000.
    LPCSTR szName; // Pointer to name (in user addr space).
    DWORD dwThreadID; // Thread ID (-1=caller thread).
    DWORD dwFlags; // Reserved for future use, must be zero.
} THREADNAME_INFO;
#pragma pack(pop)
void SetThreadName(DWORD dwThreadID, const char* threadName) {
    THREADNAME_INFO info;
    info.dwType = 0x1000;
    info.szName = threadName;
    info.dwThreadID = dwThreadID;
    info.dwFlags = 0;
#pragma warning(push)
#pragma warning(disable: 6320 6322)
    __try{
        RaiseException(MS_VC_EXCEPTION, 0, sizeof(info) / sizeof(ULONG_PTR), (ULONG_PTR*)&info);
    }
    __except (EXCEPTION_EXECUTE_HANDLER){
    }
#pragma warning(pop)
}
```

## <a name="see-also"></a>Viz také:
- [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)
- [Postupy: Nastavení názvu vlákna ve spravovaném kódu](../debugger/how-to-set-a-thread-name-in-managed-code.md)
