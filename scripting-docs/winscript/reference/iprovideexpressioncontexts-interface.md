---
title: Iprovideexpressioncontexts – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProvideExpressionContexts interface
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 402b439da6f1fa369accacb27f987ac77119e343
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794583"
---
# <a name="iprovideexpressioncontexts-interface"></a>IProvideExpressionContexts – rozhraní
Poskytuje způsob, jak vytvořit výčet výraz kontexty známé některých součástí. Skriptovací stroje obvykle toto rozhraní implementovat.  
  
 Správce ladění proces používá k nalezení všech kontextů globálním výrazu přidružené k dané vlákno toto rozhraní.  
  
> [!NOTE]
>  Toto rozhraní je volat z vlákna, které vás zajímají. Je implementátorovi identifikovat aktuální vlákno a vrátí enumerátor vhodné.  
  
## <a name="methods"></a>Metody  
 Kromě metod zděděno z `IUnknown`, `IProvideExpressionContexts` rozhraní poskytuje následující metody.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Vrátí enumerátor výraz kontexty známé touto součástí.|