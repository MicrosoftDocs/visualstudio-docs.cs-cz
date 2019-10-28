---
title: 'Iwebappdiagnosticssetup –:: CreateObjectWithSiteAtWebApp | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 253b995c200566868ac9ccc06b259e0a152e1676
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984611"
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Tato metoda společně vytvoří třídu, jejíž ID se předává pomocí `rclsid` pomocí `dwClsContext`. To je podobné jako [iremotedebugapplication –:: CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) funguje s tím rozdílem, že v případě `CreateObjectWithSiteAtWebApp` objekt je vytvořen asynchronně ve VLÁKNĚ uživatelského rozhraní webové aplikace. Objekt určený IDENTIFIKÁTORem třídy by měl implementovat [rozhraní iwebappdiagnosticsobjectinitialization –](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md). Po vytvoření objektu je volána metoda [iwebappdiagnosticsobjectinitialization –:: Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) s odkazem na aplikaci PDM Debug a parametrem `hPassToObject` `CreateObjectWithSiteAtWebApp`. Tuto metodu můžete použít k předání do aplikace popisovači do anonymního kanálu, který jste zkopírovali pomocí [DuplicateHandle](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle).  
  
> [!IMPORTANT]
> [Rozhraní iwebappdiagnosticssetup –](../../winscript/reference/iwebappdiagnosticssetup-interface.md) je implementováno pomocí PDM v 11.0 a větší. Nachází se v souboru activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>Parametry  
 `rclsid`  
 ID třídy, která se má vytvořit  
  
 `dwClsContext`  
 Kontext, ve kterém bude kód spuštěn. Ve většině případů se jedná o CLSCTX_INPROC_SERVER.  
  
 `riid`  
 Nepoužívá se.  
  
 `hPassToObject`  
 Hodnota, která bude předána objektu po jeho vytvoření ve vlákně uživatelského rozhraní, pokud objekt implementuje [rozhraní iwebappdiagnosticsobjectinitialization –](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).