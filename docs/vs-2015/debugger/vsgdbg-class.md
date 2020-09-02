---
title: Třída VsgDbg | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 053647d48324f056148375bae9268b997ba8721f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145697"
---
# <a name="vsgdbg-class"></a>VsgDbg – třída
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Představuje rozhraní pro programové řízení komponenty v aplikaci diagnostiky grafiky.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
class VsgDbg;  
```  
  
## <a name="members"></a>Členové  
 `VsgDbg`Třída podporuje následující členy.  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[VsgDbg::VsgDbg (konstruktor)](../debugger/vsgdbg-vsgdbg-constructor.md)|Vytvoří instanci `VsgDbg` třídy a volitelně připraví komponentu v aplikaci diagnostiky grafiky na aktivní zachycování a zaznamenávání informací grafiky.|  
|[VsgDbg::~VsgDbg (destruktor)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)|Odstraní instanci `VsgDbg` třídy.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[AddMessage](../debugger/addmessage.md)|Přidá vlastní zprávu do HUD diagnostiky grafiky (zobrazení záhlaví).|  
|[BeginCapture](../debugger/begincapture.md)|Zahájí interval zachycení, který skončí `EndCapture` .|  
|[CaptureCurrentFrame](../debugger/capturecurrentframe.md)|Zachycuje zbytek aktuálního rámce do souboru protokolu grafiky.|  
|[Copy (zachytávání prostřednictvím kódu programu)](../debugger/copy-programmatic-capture.md)|Zkopíruje obsah souboru protokolu Active Graphics (. vsglog) do nového souboru.|  
|[EndCapture](../debugger/endcapture.md)|Ukončí interval zachycení, který byl spuštěn s `BeginCapture` .|  
|[For](../debugger/init.md)|Připraví komponentu v aplikaci diagnostiky grafiky na aktivní zachycování a zaznamenávání informací grafiky.|  
|[ToggleHUD](../debugger/togglehud.md)|Zapne nebo vypne překryv HUD diagnostiky grafiky.|  
|[UnInit](../debugger/uninit.md)|Dokončí soubor protokolu grafiky, zavře ho a uvolní prostředky, které se použily v době, kdy aplikace aktivně zapisovala informace o grafice.|  
  
## <a name="remarks"></a>Poznámky  
 `VsgDbg`Třída představuje rozhraní, které lze použít k programovému řízení funkcí diagnostiky grafiky. Některé funkce můžete použít i v případě, že nebudete aktivně zachytíte a zaznamenáte informace grafiky. To zahrnuje `AddMessage` členskou funkci a `ToggleHUD` členskou funkci. Ostatní členské funkce buď připraví komponentu v aplikaci diagnostiky grafiky na spuštění nebo zastavení aktivního zachycení informací grafiky, nebo musí být volány, zatímco aplikace aktivně zachytí a zaznamenává informace grafiky do souboru protokolu grafiky.
