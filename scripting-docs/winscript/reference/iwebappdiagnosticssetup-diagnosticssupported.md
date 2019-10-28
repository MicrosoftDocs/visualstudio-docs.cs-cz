---
title: Iwebappdiagnosticssetup –::D iagnosticsSupported | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::DiagnosticsSupported
ms.assetid: 5bbcd0d0-1460-4cf7-bbb1-f4f4a04f739a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd27e7c8759054fa2d7d67858d8d006fa9c9a152
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984574"
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
Určuje, zda je v této aplikaci podporována Diagnostika. Pokud byla volána metoda [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) na objektu, který implementuje toto rozhraní s hodnotou jinou než null, vrátí [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) hodnotu `true`. V opačném případě vrátí `false` a volání [iwebappdiagnosticssetup –:: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) selže.  
  
> [!IMPORTANT]
> [Rozhraní iwebappdiagnosticssetup –](../../winscript/reference/iwebappdiagnosticssetup-interface.md) je implementováno pomocí PDM v 11.0 a větší. Nalezeno v activdbg100.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 Pokud byla volána metoda [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) na objektu, který implementuje toto rozhraní s hodnotou jinou než null, vrátí [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) hodnotu `true`. V opačném případě vrátí `false`a volání [iwebappdiagnosticssetup –:: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) selže.