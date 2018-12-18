---
title: Zásady šablon a okno Vlastnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8cf24f6f769ea9344d2a7716856e3c84fdf122de
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816323"
---
# <a name="template-policy-and-the-properties-window"></a>Zásady šablon a okno Vlastnosti
Pokud projekt je obsažena v šabloně projektu organizace, je tento projekt šablony organizace vynucovat zásady. Šablony zásad stane omezující systému, který je možné nastavit výchozí hodnoty pro vlastnosti, skrýt vlastnosti, přidat vlastnosti a tak dále.  
  
 Pomocí zásad šablony pro ovládací prvek zobrazení informací v **vlastnosti** okna se liší od implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> zpracovává vlastnosti objektu na úrovni součásti šablony zásad slouží k omezení vlastností objektu na úrovni řešení nebo projektu. Jinými slovy  
  
- Implementace metody na <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> k určení, co se zobrazí **vlastnosti** okna pro příslušné objekty  
  
- Použít šablonu zásad na úrovni řešení a projektu k určení, co se zobrazí **vlastnosti** okně dříve zadané objekty  
  
  Pomocí zásad šablony pro specifické vlastnosti v selektivně omezit **vlastnosti** okno při zadaného typu položky projektu je vybrán v **Průzkumníku řešení** může být výhodný pro všechny členy Vývojový tým práci na projektu. Například pomocí šablony zásad, můžete nastavit všechny připojovací řetězec informace v databázi pro vývojáře, kteří a nastavte připojovací řetězec jen pro čtení. Tímto způsobem můžete zadat jednoduchý způsob, jak zajistit, že každý vývojář používá správnou cestu pro přístup k datům.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Rozšíření vlastností](../../extensibility/internals/extending-properties.md)