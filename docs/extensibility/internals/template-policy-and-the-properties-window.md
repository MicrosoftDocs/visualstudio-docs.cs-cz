---
title: Zásady šablony a okno Vlastnosti | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08ed6f416441d06767661e63b5e32454dbe07f93
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704663"
---
# <a name="template-policy-and-the-properties-window"></a>Zásady šablon a okno Vlastnosti
Pokud je projekt obsažen uvnitř projektu šablony organizace, může tento projekt šablony organizace vynutit zásady. Zásada šablony se stává omezujícím systémem, který lze použít k nastavení výchozích hodnot vlastností, skrytí vlastností, přidání vlastností a tak dále.

 Použití zásady šablony k řízení zobrazení informací v okně <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> **Vlastnosti** se liší od implementace . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>zpracovává vlastnosti objektu na úrovni komponenty, zatímco zásady šablony lze použít k omezení vlastností objektu na úrovni řešení nebo projektu. Jinými slovy

- Implementujte metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> k určení, co je zobrazeno v okně **Vlastnosti** pro určité objekty

- Použití zásad šablony na úrovni řešení a projektu k určení, co se zobrazí v okně **Vlastnosti** pro dříve zadané objekty

  Použití zásady šablony k selektivnímu omezení určitých vlastností v okně **Vlastnosti,** když je v **Průzkumníku řešení** vybrána položka projektu určeného typu, může být přínosné pro všechny členy vývojového týmu pracujícího na projektu. Pomocí zásad šablony můžete například nastavit všechny informace o připojovacím řetězci v databázi pro vývojáře a vytvořit připojovací řetězec jen pro čtení. Tímto způsobem můžete poskytnout jednoduchý způsob, jak zajistit, že každý vývojář používá správnou cestu pro přístup k datům.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [Rozšíření vlastností](../../extensibility/internals/extending-properties.md)
