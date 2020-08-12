---
title: IActiveScriptSite | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSite interface
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dcf95f74e05ebff6e1cc430c32b9fd7bdb3b005f
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144659"
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Implementováno hostitelem za účelem vytvoření webu pro skriptovací stroj Windows Obvykle bude tento web přidružen ke kontejneru všech objektů, které jsou viditelné ke skriptu (například ovládací prvky ActiveX). Obvykle bude tento kontejner odpovídat dokumentu nebo zobrazované stránce. Aplikace Microsoft Internet Explorer například vytvoří takový kontejner pro každou stránku HTML, která je zobrazena. Každý ovládací prvek ActiveX (nebo jiný objekt automatizace) na stránce a samotný skriptovací stroj by byl v rámci tohoto kontejneru vyčíslitelné.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
  
|Metoda|Popis|
|-|-|
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Načte identifikátor národního prostředí, který hostitel používá pro zobrazení prvků uživatelského rozhraní.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Získává informace o položce, která byla přidána do modulu prostřednictvím volání metody [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Načte řetězec definovaný v hostiteli, který jednoznačně identifikuje aktuální verzi dokumentu z pohledu hostitele.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Volá se po dokončení provádění skriptu.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Informuje hostitele o změně stavů skriptovacího stroje.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Informuje hostitele o tom, že došlo k chybě spuštění, když modul spustil skript.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Informuje hostitele, že skriptovací modul začal spouštět kód skriptu.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Informuje hostitele o tom, že skriptovací stroj vrátil spouštěcí kód skriptu.|  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní aktivních skriptů](../../winscript/reference/active-script-interfaces.md)