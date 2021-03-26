---
title: Features2 služby starší verze jazyka | Microsoft Docs
description: Přečtěte si o některých funkcích služby starší verze jazyka, které můžete poskytnout pomocí rozšíření Managed Extensibility Framework (MEF) v sadě Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], code development aides
ms.assetid: 97c38622-ae0b-4ae0-90ed-604072c298d3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a12ee207f7fb7e4f4e2d202d5d63d468e9cea547
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074480"
---
# <a name="legacy-language-service-features-2"></a>Funkce služby starší verze jazyka 2
V následujících tématech najdete seznam některých funkcí služby starší verze jazyka, které můžete poskytnout.

 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Další informace o novém způsobu implementace jazykové služby najdete v tématu [rozšíření pro Editor a jazykové služby](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Doporučujeme začít používat nové rozhraní API editoru co nejrychleji. Tím se vylepšit výkon vaší jazykové služby a umožní vám využít nové funkce editoru.

## <a name="in-this-section"></a>V tomto oddílu
- [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Vysvětluje, jak implementovat barvy syntaxe.

- [Automatické formátování ve službě starší verze jazyka](../../extensibility/internals/automatic-formatting-in-a-legacy-language-service.md)

 Vysvětluje, jak implementovat automatické formátování.

- [Informace o parametrech ve službě starší verze jazyka](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Vysvětluje, jak implementovat ovládací prvek informace o parametru technologie IntelliSense.

- [Dokončování příkazů ve službě starší verze jazyka](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Vysvětluje, jak implementovat seznam příkazů IntelliSense a seznam dokončení členů.

- [Osnova a skrytý text ve službě starší verze jazyka](../../extensibility/internals/outlining-and-hidden-text-in-a-legacy-language-service.md)

 Vysvětluje, jak implementovat sbalení nebo skrytý text.

- [Postupy: Rozšířená podpora osnovy ve službě starší verze jazyka](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Popisuje některé kroky v tématu Implementace podpory ladicího programu..

## <a name="related-sections"></a>Související oddíly
