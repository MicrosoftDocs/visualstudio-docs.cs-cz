---
title: Iwebappdiagnosticssetup – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 6e273f29bee6e4d2aae26c01c477373a735624c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796353"
---
# <a name="iwebappdiagnosticssetup-interface"></a>IWebAppDiagnosticsSetup – rozhraní
Toto rozhraní je implementováno PDM ladění aplikace k vytváření objektů COM v procesu, který je právě laděn a povolí se Diagnostika web. Pokud PDM ladění aplikací implementuje objekt [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438), aplikace Internet Explorer volá [setsite –](http://go.microsoft.com/fwlink/?LinkId=232439) na se po vytvoření a předává v odkaz na [rozhraní IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449). WWA aplikace zavolá [setsite –](http://go.microsoft.com/fwlink/?LinkId=232439) a předává v WWA rozhraní IWebApplicationHost místo. Pokud [setsite –](http://go.microsoft.com/fwlink/?LinkId=232439) byla volána s NENULOVOU hodnotu, [IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) vrací hodnotu true. Pokud ne, vrátí hodnotu false a volá, aby se [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) nezdaří.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup`je implementováno PDM v11.0 a větší. Nachází se v souboru activdbg100.h.  
  
## <a name="methods"></a>Metody  
 Toto rozhraní poskytuje následující metody.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Získá text dokumenty, které jsou skrytý na základě zadaného filtru.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Určuje, zda zadaný dokument patří do jedné z podřízených uzlů tohoto uzlu.|