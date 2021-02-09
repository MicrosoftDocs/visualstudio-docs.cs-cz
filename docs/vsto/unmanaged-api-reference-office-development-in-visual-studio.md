---
title: Reference nespravovaného rozhraní API (vývoj pro Office v sadě Visual Studio)
description: Nespravovaný odkaz rozhraní API se používá pro usnadnění načítání doplňků VSTO. Implementací tohoto rozhraní můžete také vytvořit vlastní komponentu zavaděče doplňku VSTO.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cac9e2d01b47e0088543aeabcaeff30853314157
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908550"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Reference nespravovaného rozhraní API (vývoj pro Office v sadě Visual Studio)

Počínaje systémem 2007 systém Microsoft Office systém Office používá rozhraní [rozhraní IManagedAddin –](../vsto/imanagedaddin-interface.md) k volání komponenty zavaděče doplňku VSTO, která je součástí [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Tato součást slouží k načtení doplňků VSTO spravovaných pomocí. Implementací tohoto rozhraní můžete vytvořit vlastní komponentu zavaděče doplňku VSTO.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>V této části

[Rozhraní IManagedAddin –](../vsto/imanagedaddin-interface.md)

Rozhraní modelu COM, které můžete implementovat pro načtení a uvolnění spravovaných doplňků VSTO v aplikacích Office.
