---
title: Zásady šablony a okno Vlastnosti | Microsoft Docs
description: Přečtěte si o použití zásad šablony k nastavení výchozích hodnot pro vlastnosti, skrytí vlastností a přidání vlastností do okno Vlastnosti.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 105a90699689ff6eab6ea5bdfa3d4037e700ecb5
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877712"
---
# <a name="template-policy-and-the-properties-window"></a>Zásady šablon a okno Vlastnosti
Pokud je projekt obsažen v projektu šablony organizace, může tento projekt šablony vynutilit zásady. Zásada šablony se stal omezeným systémem, který lze použít k nastavení výchozích hodnot pro vlastnosti, skrytí vlastností, přidání vlastností a tak dále.

 Použití zásad šablony pro řízení zobrazení informací v okně **vlastnosti** se liší od implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> zpracovává vlastnosti objektu na úrovni komponenty, zatímco zásady šablony lze použít k omezení vlastností objektu na úrovni řešení nebo projektu. Jinými slovy

- Implementujte metody pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> určení toho, co se zobrazí v okně **vlastnosti** pro konkrétní objekty

- Pomocí zásad šablony na úrovni řešení a projektu určete, co se zobrazí v okně **vlastnosti** pro dříve zadané objekty.

  Použití zásad šablony k selektivnímu omezení specifických vlastností v okně **vlastnosti** , když je vybrána položka projektu zadaného typu v **Průzkumník řešení** může být výhodné pro všechny členy vývojového týmu, který pracuje na projektu. Pomocí zásad šablony můžete například nastavit všechny informace o připojovacím řetězci v databázi pro vaše vývojáře a nastavit připojovací řetězec jen pro čtení. Tímto způsobem můžete zajistit jednoduchý způsob, jak zajistit, aby každý vývojář používal správnou cestu pro přístup k datům.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [Rozšíření vlastností](../../extensibility/internals/extending-properties.md)
