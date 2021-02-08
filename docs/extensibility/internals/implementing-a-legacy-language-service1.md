---
title: Implementace starší verze jazyka Service1 | Microsoft Docs
description: Naučte se implementovat službu starší verze jazyka, která podporuje funkce rozšířené jazykové služby, pomocí rozhraní Managed Package Framework (MPF). Část 1 ze 2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2337d1ee2ac8e698e93a0d8d3d1dc9324af4f933
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839986"
---
# <a name="implementing-a-legacy-language-service-1"></a>Implementace starší verze jazykové služby 1
Můžete použít třídy v rozhraní Managed Package Framework (MPF) k implementaci služby starší verze jazyka, která podporuje širokou škálu funkcí, jako je například zvýrazňování syntaxe, shoda se závorkami a dokončování IntelliSense.

 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Další informace o novém způsobu implementace jazykové služby najdete v tématu [rozšíření pro Editor a jazykové služby](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Doporučujeme začít používat nové rozhraní API editoru co nejrychleji. Tím se vylepšit výkon vaší jazykové služby a umožní vám využít nové funkce editoru.

## <a name="in-this-section"></a>V tomto oddílu
- [Přehled služby starší verze jazyka](../../extensibility/internals/legacy-language-service-overview.md)

 Přehled funkcí jazykové služby, které jsou podporovány ve formátu MPF.

- [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Popisuje, co je potřeba k implementaci jazykové služby pomocí možnosti MPF.

- [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Popisuje kroky, které jsou požadovány k registraci služby jazyka založeného na formátu MPF pomocí nástroje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Analyzátor a skener služby starší verze jazyka](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Popisuje dva analyzátory, které jsou požadovány k implementaci všech funkcí jazykové služby pomocí vlastnosti MPF.

- [Návod: Vytvoření služby starší verze jazyka](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Poskytuje základní kroky, které jsou nutné k implementaci služby MPF jazyka ve VSPackage.

- [Návod: Získání seznamu nainstalovaných fragmentů kódu (implementace starší verze)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Ukazuje techniky získání seznamu nainstalovaných fragmentů kódu.

- [Funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md)

 Obsahuje odkazy na témata, která podrobně popisují, co je třeba provést k implementaci všech funkcí jazykové služby pomocí funkce MPF.
