---
title: Scriptprop_hostkeepalive – vlastnost | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a39ae7100c5567d2b03b7998077b20b1078810aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796395"
---
# <a name="scriptprophostkeepalive-property"></a>SCRIPTPROP_HOSTKEEPALIVE – vlastnost
Použít k určení, zda skriptovacího stroje by měly být udržovány plně funkční, pokud existují nevyřízené odkazy.  
  
 Použití [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) pro tuto vlastnost nastavit na `true`. Pokud je tato vlastnost nastavena na `true`, skriptovací stroj je udržováno plně funkční, dokud je alespoň jeden nezpracovaných odkaz na skriptovací stroj sám sebe nebo na `IDispatch` ukazatel na objekt jazyka JavaScript, který je vytvořen pomocí skriptování modul. Pokud je tato vlastnost nastavená na `true`, by měla není explicitně zavřete nebo resetovat skriptovací stroj pomocí [IActiveScript::Close](../../winscript/reference/iactivescript-close.md) nebo [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) metody. Verzi poslední odkaz na objekt skriptu vypne skriptovací stroj.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## <a name="requirements"></a>Požadavky  
 Tato vlastnost se zobrazí pouze ve verzi activscp.idl, který je nainstalován pomocí [!INCLUDE[win8](../../javascript/includes/win8-md.md)], s 2707082 KB pro Internet Explorer 8 na [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)], nebo s 2722913 KB pro Internet Explorer 9 na [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] nebo [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)].