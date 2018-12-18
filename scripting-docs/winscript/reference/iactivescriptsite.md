---
title: Iactivescriptsite – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: c23dba403a7889fe46817a21ed8e4be65b1c05b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793611"
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Implementované hostitele pro vytvoření webu pro modul Windows Script. Tato lokalita obvykle bude přidružen k kontejneru všechny objekty, které jsou viditelné pro skript (například ovládací prvky ActiveX). Tento kontejner bude obvykle odpovídají dokumentu nebo na stránce se zobrazit. Například aplikace Microsoft Internet Explorer, by vytvořit kontejner, pro každou stránku HTML, který se zobrazuje. Každý ActiveX ovládacího prvku (nebo jiný objekt automatizace) na stránce a skriptovací stroje, samostatně, bude vyčíslitelná v tomto kontejneru.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|||  
|-|-|  
|Metoda|Popis|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Načte identifikátor národního prostředí, který hostitel používá pro zobrazení prvky uživatelského rozhraní.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Získá informace o položku, která byla přidána do modul prostřednictvím volání [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) metoda.|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Načte řetězec definované na hostitele, který jednoznačně identifikuje aktuální verze dokumentu z hlediska hostitele.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Volá se při dokončení provádění skriptu.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Informuje hostitele, že skriptovacího stroje se změnila stavy.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Informuje hostitele, že došlo k chybě provádění modul byl spuštěn skript.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Informuje hostitele, že byl zahájen skriptovacího stroje provádění kód skriptu.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Informuje o hostiteli, skriptovací stroj vrátila ve spouštění skriptu kódu.|  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní aktivních skriptů](../../winscript/reference/active-script-interfaces.md)