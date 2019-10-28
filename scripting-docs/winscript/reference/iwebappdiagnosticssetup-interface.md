---
title: Rozhraní Iwebappdiagnosticssetup – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup Interface
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e9bb3905da6227b978bc27b96493500f8d6d2ff
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984544"
---
# <a name="iwebappdiagnosticssetup-interface"></a>IWebAppDiagnosticsSetup – rozhraní
Toto rozhraní je implementováno pomocí aplikace PDM Debug pro vytváření objektů COM v procesu, který je laděn, a pro povolení webové diagnostiky. Pokud objekt aplikace PDM Debug implementuje [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite), [zavolá Internet](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) Explorer po jeho vytvoření a předá odkaz na [IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127(v=vs.85)). Aplikace WWA volá [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) a předá místo toho rozhraní WWA IWebApplicationHost. Pokud byla volána [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) s jinou hodnotou než null, [Iwebappdiagnosticssetup –::D iagnosticssupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) vrátí hodnotu true. V opačném případě vrátí hodnotu false a volání funkce [iwebappdiagnosticssetup –:: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) selže.  
  
> [!IMPORTANT]
> `IWebAppDiagnosticsSetup` je implementováno pomocí PDM v 11.0 a větší. Nachází se v souboru activdbg100.h.  
  
## <a name="methods"></a>Metody  
 Toto rozhraní zpřístupňuje následující metody.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Načte textové dokumenty, které jsou skryté zadaným filtrem.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Určuje, zda zadaný dokument patří do jednoho z podřízených uzlů tohoto uzlu.|