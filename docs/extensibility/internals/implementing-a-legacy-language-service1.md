---
title: Implementace služby starší verze jazyka1 | Microsoft Docs
description: Naučte se implementovat službu starší verze jazyka, která podporuje funkce rozšířených jazykových služeb, pomocí rozhraní spravovaného balíčku (MPF). Část 1 ze 2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 34be4e54fbce413fe5ba916892216a9234d4ba93
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901146"
---
# <a name="implementing-a-legacy-language-service-1"></a>Implementace služby starší verze jazyka 1
Třídy v rozhraní spravovaného balíčku (MPF) můžete použít k implementaci služby starší verze jazyka, která podporuje širokou škálu funkcí, jako je zvýrazňování syntaxe, párování závorek a dokončování IntelliSense.

 Služby starší verze jazyka jsou implementovány jako součást balíčku VSPackage, ale novější způsob implementace funkcí služby jazyka je použití rozšíření MEF. Další informace o novém způsobu implementace služby jazyka najdete v tématu Rozšíření jazykových služeb a [editorů.](../../extensibility/editor-and-language-service-extensions.md)

> [!NOTE]
> Doporučujeme, abyste nové rozhraní API editoru začali používat co nejdříve. Tím se zlepší výkon služby jazyka a umožní vám to využívat nové funkce editoru.

## <a name="in-this-section"></a>V tomto oddílu
- [Přehled služby starší verze jazyka](../../extensibility/internals/legacy-language-service-overview.md)

 Přehled funkcí služby jazyka, které jsou podporované v MPF.

- [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Popisuje, co je potřeba k implementaci služby jazyka pomocí MPF.

- [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Popisuje kroky potřebné k registraci služby jazyka založené na MPF ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] službě .

- [Analyzátor a skener služby starší verze jazyka](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Popisuje dva analyzátory, které jsou nutné k implementaci všech funkcí služby jazyka pomocí MPF.

- [Návod: Vytvoření služby starší verze jazyka](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Poskytuje základní kroky potřebné k implementaci služby jazyka MPF v balíčky VSPackage.

- [Návod: Získání seznamu nainstalovaných fragmentů kódu (implementace starší verze)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Demonstruje techniky načtení seznamu nainstalovaných fragmentů kódu.

- [Funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md)

 Obsahuje odkazy na témata, která podrobně popisují, co je třeba provést k implementaci všech funkcí služby jazyka pomocí MPF.
