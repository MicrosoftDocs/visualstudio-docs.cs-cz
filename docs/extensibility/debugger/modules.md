---
title: Moduly | Microsoft Docs
description: Tento článek popisuje definice a roli modulu v architektuře ladicího programu v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9aa0aaf7e82287c1dc2e35c524798a3480d2573e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926327"
---
# <a name="modules"></a>Moduly
V podobě architektury ladicího programu *modul*:

- Je fyzický kontejner kódu, jako je spustitelný soubor nebo knihovna DLL.

- Může znovu načíst své symboly a popsat sebe sama. Popisy modulů jsou zobrazeny v okně moduly rozhraní IDE.

- Je reprezentován rozhraním [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) vytvořeným ladicím modulem, který popisuje modul.

## <a name="see-also"></a>Viz také
- [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
