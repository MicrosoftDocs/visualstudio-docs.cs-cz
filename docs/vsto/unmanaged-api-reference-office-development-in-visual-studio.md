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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9dbb64b54d9b0dd9a244d9a614fbce211d1edfc5
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97522684"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Reference nespravovaného rozhraní API (vývoj pro Office v sadě Visual Studio)

Počínaje systémem 2007 systém Microsoft Office systém Office používá rozhraní [rozhraní IManagedAddin –](../vsto/imanagedaddin-interface.md) k volání komponenty zavaděče doplňku VSTO, která je součástí [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Tato součást slouží k načtení doplňků VSTO spravovaných pomocí. Implementací tohoto rozhraní můžete vytvořit vlastní komponentu zavaděče doplňku VSTO.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>V této části

[Rozhraní IManagedAddin –](../vsto/imanagedaddin-interface.md)

Rozhraní modelu COM, které můžete implementovat pro načtení a uvolnění spravovaných doplňků VSTO v aplikacích Office.
