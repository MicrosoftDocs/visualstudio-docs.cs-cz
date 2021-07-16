---
description: Představuje rozhraní pro programové řízení komponenty diagnostiky grafiky v aplikaci.
title: VsgDbg – třída | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2bb3a9009c38da483b0792b89c115c2e8e9908eb
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232450"
---
# <a name="vsgdbg-class"></a>VsgDbg – třída
Představuje rozhraní pro programové řízení komponenty diagnostiky grafiky v aplikaci.

## <a name="syntax"></a>Syntax

```C++
class VsgDbg;
```

## <a name="members"></a>Členové
 Třída `VsgDbg` podporuje následující členy.

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Description|
|----------|-----------------|
|[VsgDbg::VsgDbg (konstruktor)](vsgdbg-vsgdbg-constructor.md)|Vytvoří instanci třídy a volitelně připraví komponentu diagnostiky grafiky v aplikaci k aktivnímu zachycení a `VsgDbg` zaznamenání informací grafiky.|
|[VsgDbg::~VsgDbg (destruktor)](vsgdbg-tilde-vsgdbg-destructor.md)|Zničí instanci třídy `VsgDbg` .|

### <a name="public-methods"></a>Veřejné metody

|Název|Description|
|----------|-----------------|
|[AddMessage](addmessage.md)|Přidá vlastní zprávu do diagnostiky grafiky HUD (head-up display).|
|[BeginCapture](begincapture.md)|Začíná interval zachycení, který bude končovat `EndCapture` na .|
|[CaptureCurrentFrame](capturecurrentframe.md)|Zachycuje zbývající část aktuálního rámce do souboru protokolu grafiky.|
|[Copy (zachytávání prostřednictvím kódu programu)](copy-programmatic-capture.md)|Zkopíruje obsah aktivního souboru protokolu grafiky (.vsglog) do nového souboru.|
|[EndCapture](endcapture.md)|Ukončí interval zachycení, který byl spuštěn pomocí `BeginCapture` .|
|[Init](init.md)|Připraví komponentu diagnostiky grafiky v aplikaci k aktivnímu zaznamenání a zaznamenání informací grafiky.|
|[ToggleHUD](togglehud.md)|Přepíná překrytí HUD diagnostiky grafiky zapnout nebo vypnout.|
|[UnInit](uninit.md)|Finalizuje soubor protokolu grafiky, zavře ho a uchová prostředky, které byly použity při aktivním zaznamenávání informací grafiky aplikací.|

## <a name="remarks"></a>Poznámky
 Třída `VsgDbg` představuje rozhraní, které můžete použít k řízení funkcí diagnostiky grafiky prostřednictvím kódu programu. Některé funkce můžete použít i v případě, že aktivně nezachytávání a zaznamenávání informací grafiky. To zahrnuje `AddMessage` členská funkce `ToggleHUD` a členská funkce. Ostatní členské funkce buď připraví komponentu diagnostiky grafiky v aplikaci na spuštění nebo zastavení aktivního zachycení informací grafiky, nebo musí být volány, když aplikace aktivně zaznamenává a zaznamenává informace grafiky do souboru protokolu grafiky.
