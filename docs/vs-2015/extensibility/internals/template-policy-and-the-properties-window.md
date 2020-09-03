---
title: Zásady šablony a okno Vlastnosti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1c67150c5a71a3d70df85669319795a405c60f4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156027"
---
# <a name="template-policy-and-the-properties-window"></a>Zásady šablon a okno Vlastnosti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pokud je projekt obsažen v projektu šablony organizace, může tento projekt šablony vynutilit zásady. Zásada šablony se stal omezeným systémem, který lze použít k nastavení výchozích hodnot pro vlastnosti, skrytí vlastností, přidání vlastností a tak dále.  
  
 Použití zásad šablony pro řízení zobrazení informací v okně **vlastnosti** se liší od implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> zpracovává vlastnosti objektu na úrovni komponenty, zatímco zásady šablony lze použít k omezení vlastností objektu na úrovni řešení nebo projektu. Jinými slovy  
  
- Implementujte metody pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> určení toho, co se zobrazí v okně **vlastnosti** pro konkrétní objekty  
  
- Pomocí zásad šablony na úrovni řešení a projektu určete, co se zobrazí v okně **vlastnosti** pro dříve zadané objekty.  
  
  Použití zásad šablony k selektivnímu omezení specifických vlastností v okně **vlastnosti** , když je vybrána položka projektu zadaného typu v **Průzkumník řešení** může být výhodné pro všechny členy vývojového týmu, který pracuje na projektu. Pomocí zásad šablony můžete například nastavit všechny informace o připojovacím řetězci v databázi pro vaše vývojáře a nastavit připojovací řetězec jen pro čtení. Tímto způsobem můžete zajistit jednoduchý způsob, jak zajistit, aby každý vývojář používal správnou cestu pro přístup k datům.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Rozšíření vlastností](../../extensibility/internals/extending-properties.md)
