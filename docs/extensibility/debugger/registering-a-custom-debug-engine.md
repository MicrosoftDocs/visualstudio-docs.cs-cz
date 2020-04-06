---
title: Registrace vlastního ladicího modulu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe6fb916810bc8a7e960a4723a6a7c7a6f0c1410
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713215"
---
# <a name="register-a-custom-debug-engine"></a>Registrace vlastního ladicího stroje
Ladicí modul se musí zaregistrovat jako továrna třídy, podle konvencí COM a také zaregistrovat se v sadě Visual Studio prostřednictvím podklíče registru sady Visual Studio.

> [!NOTE]
> Můžete najít příklad, jak zaregistrovat ladicí stroj v TextInterpreter ukázky, která je sestavena jako součást [kurzu: Vytváření ladicí modul pomocí ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24).

## <a name="dll-server-process"></a>Proces serveru DLL
 Ladicí modul je obvykle nastaven ve vlastní dll jako server COM. Jako takové ladicí modul musí zaregistrovat CLSID své třídy s COM před Visual Studio přístup. Potom ladicí modul musí zaregistrovat sám s Visual Studio vytvořit všechny vlastnosti (jinak označované jako metriky) podporuje ladicí modul. Volba metriky zapsané do podklíče registru sady Visual Studio závisí na funkcích, které podporuje ladicí modul.

 [Pomocné spoje sady SDK pro ladění](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) popisují nejen umístění registru potřebná k registraci ladicího modulu. popisuje také knihovnu *dbgmetric.lib,* která obsahuje řadu užitečných funkcí a deklarací pro vývojáře jazyka C++, které usnadňují manipulaci s registrem.

### <a name="example"></a>Příklad
 Následující příklad (z TextInterpreter ukázky) ukazuje, jak používat `SetMetric` funkci (z *dbgmetric.lib*), zaregistrovat ladicí modul s Visual Studio. Předané metriky jsou také definovány v *souboru dbgmetric.lib*.

> [!NOTE]
> TextInterpreter je základní ladicí modul; nenastavuje – a proto se neregistruje – žádné další funkce. Úplnější ladicí modul by měl `SetMetric` celý seznam volání nebo jejich ekvivalent, jeden pro každou funkci, kterou ladicí modul podporuje.

```
// Define base registry subkey to Visual Studio.
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";

HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)
{
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);

    return base::RegisterServer(bRegTypeLib, pCLSID);
}
```

## <a name="see-also"></a>Viz také
- [Vytvoření vlastního ladicího modulu](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [Pomocné spoje sady SDK pro ladění](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Kurz: Vytvoření ladicího modulu pomocí služby ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)
