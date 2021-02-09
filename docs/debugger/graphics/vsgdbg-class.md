---
title: Třída VsgDbg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 67bce62612a85e0bcff5e51cd07d4c374e13b01e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861397"
---
# <a name="vsgdbg-class"></a>VsgDbg – třída
Představuje rozhraní pro programové řízení komponenty v aplikaci diagnostiky grafiky.

## <a name="syntax"></a>Syntax

```C++
class VsgDbg;
```

## <a name="members"></a>Členové
 `VsgDbg`Třída podporuje následující členy.

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Description|
|----------|-----------------|
|[VsgDbg::VsgDbg (konstruktor)](vsgdbg-vsgdbg-constructor.md)|Vytvoří instanci `VsgDbg` třídy a volitelně připraví komponentu v aplikaci diagnostiky grafiky na aktivní zachycování a zaznamenávání informací grafiky.|
|[VsgDbg::~VsgDbg (destruktor)](vsgdbg-tilde-vsgdbg-destructor.md)|Odstraní instanci `VsgDbg` třídy.|

### <a name="public-methods"></a>Veřejné metody

|Název|Description|
|----------|-----------------|
|[AddMessage](addmessage.md)|Přidá vlastní zprávu do HUD diagnostiky grafiky (zobrazení záhlaví).|
|[BeginCapture](begincapture.md)|Zahájí interval zachycení, který skončí `EndCapture` .|
|[CaptureCurrentFrame](capturecurrentframe.md)|Zachycuje zbytek aktuálního rámce do souboru protokolu grafiky.|
|[Copy (zachytávání prostřednictvím kódu programu)](copy-programmatic-capture.md)|Zkopíruje obsah souboru protokolu Active Graphics (. vsglog) do nového souboru.|
|[EndCapture](endcapture.md)|Ukončí interval zachycení, který byl spuštěn s `BeginCapture` .|
|[For](init.md)|Připraví komponentu v aplikaci diagnostiky grafiky na aktivní zachycování a zaznamenávání informací grafiky.|
|[ToggleHUD](togglehud.md)|Zapne nebo vypne překryv HUD diagnostiky grafiky.|
|[UnInit](uninit.md)|Dokončí soubor protokolu grafiky, zavře ho a uvolní prostředky, které se použily v době, kdy aplikace aktivně zapisovala informace o grafice.|

## <a name="remarks"></a>Poznámky
 `VsgDbg`Třída představuje rozhraní, které lze použít k programovému řízení funkcí diagnostiky grafiky. Některé funkce můžete použít i v případě, že nebudete aktivně zachytíte a zaznamenáte informace grafiky. To zahrnuje `AddMessage` členskou funkci a `ToggleHUD` členskou funkci. Ostatní členské funkce buď připraví komponentu v aplikaci diagnostiky grafiky na spuštění nebo zastavení aktivního zachycení informací grafiky, nebo musí být volány, zatímco aplikace aktivně zachytí a zaznamenává informace grafiky do souboru protokolu grafiky.