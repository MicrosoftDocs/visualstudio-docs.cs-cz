---
title: Implementace služby staršího jazyka1 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3805e49ffa83f7dea2ee58ef36e1bc8e48b1eaa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707689"
---
# <a name="implementing-a-legacy-language-service"></a>Implementace služby starší verze jazyka
Třídy v rámci spravovaného balíčku (MPF) můžete použít k implementaci starší jazykové služby, která podporuje širokou škálu funkcí, jako je zvýraznění syntaxe, shoda složených závorek a dokončení technologie IntelliSense.

 Starší jazykové služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkcí služby jazyka je použití rozšíření MEF. Další informace o novém způsobu implementace jazykové služby naleznete v [tématu Editor and Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Doporučujeme, abyste co nejdříve začali používat nové rozhraní API editoru. Tím se zlepší výkon služby jazyka a umožní vám využít nové funkce editoru.

## <a name="in-this-section"></a>V tomto oddílu
- [Přehled služby starší verze jazyka](../../extensibility/internals/legacy-language-service-overview.md)

 Přehled funkcí služby jazyka, které jsou podporovány v MPF.

- [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Popisuje, co je nutné implementovat službu jazyka pomocí MPF.

- [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Popisuje kroky, které jsou nutné k registraci jazykové [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]služby založené na MPF s .

- [Analyzátor a skener služby starší verze jazyka](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Popisuje dva analyzátory, které jsou nutné k implementaci všech funkcí služby jazyka pomocí MPF.

- [Návod: Vytvoření služby starší verze jazyka](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Obsahuje základní kroky, které jsou nutné k implementaci služby jazyka MPF v Balíčku VSPackage.

- [Návod: Získání seznamu nainstalovaných fragmentů kódu (implementace starší verze)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Ukazuje techniky načítání seznamu nainstalovaných fragmentů kódu.

- [Funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md)

 Obsahuje odkazy na témata, která podrobně popisují, co je třeba provést pro implementaci všech funkcí jazykové služby pomocí MPF.
