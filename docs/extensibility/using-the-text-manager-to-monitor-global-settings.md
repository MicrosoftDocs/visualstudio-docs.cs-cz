---
title: Pomocí Správce Text monitorování globální nastavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3678ec0cba6f46b65f5c1d6f84e9962b5487fa93
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937860"
---
# <a name="use-the-text-manager-to-monitor-global-settings"></a>Pomocí Správce text můžete sledovat globální nastavení
Pokud se rozhodnete implementovat základní editor, je třeba sledovat změny, které jsou provedeny ke globálnímu nastavení, protože tyto změny mohou ovlivnit vaše instance editoru. Změny můžete sledovat prostřednictvím naslouchání události vyvolané službou textový správce. Například když zadáte globální předvoleb pro vzhled nebo chování součásti v základní editor, například jeho datový objekt dokumentu, textový správce ukládá tyto informace a komunikuje se všechny příslušné klienty.  
  
## <a name="text-manager-functions"></a>Textové funkce správce  
 Textový správce vyvolává události pro celou řadu nastavení, včetně následujících:  
  
- Určuje, zda vyrovnávací paměti je pod správou zdrojového kódu  
  
- Postup registrace pro oznámení o změně souboru  
  
- Tom, jak udržovat přehled o zobrazení, které jsou spojeny s určitým vyrovnávací paměti  
  
- Předvolby zabarvení textu  
  
- Karta oproti předvolby místa  
  
  Předvolby, které jsou jedinečné pro daný jazyk nespravuje textový správce. Tato nastavení se musí spravovat přes každá služba jazyka.  
  
  Oznámení události pro textový správce poskytuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> rozhraní. Toto rozhraní implementují u svého klienta vyvolá objekt zpracování událostí textový správce. Tyto události můžete zaregistrovat pomocí <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> rozhraní na textový správce.  
  
## <a name="see-also"></a>Viz také:  
 [V editoru core](../extensibility/inside-the-core-editor.md)   
 [Funkce editoru](https://msdn.microsoft.com/library/bdac940d-1f14-4019-a01f-fd0bb3dc7198)