---
title: Registrovat přípony názvů souborů pro souběžné rozprocesory
description: Přečtěte si o registraci přípon názvů souborů pro souběžná nasazení, která uživatelům umožňují otevřít soubory v příslušné verzi sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a457a3848917eff3d3722a8e72f0b0b720c0b43b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836992"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Registrace přípon názvů souborů pro souběžná nasazení
Pro VSPackage nasazené v souběžném prostředí musíte registrovat přípony názvů souborů k přidružení souborů ke správné verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Pokud nepoužíváte příponu názvu souboru specifickou pro verzi, umožňuje registrace uživatelům otevřít projekt a soubory položek projektu v příslušné verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>V této části
- [O příponách názvů souborů](../extensibility/about-file-name-extensions.md) Popisuje, jak jsou zaregistrované přípony názvů souborů.

- [Zadat obslužné rutiny souborů pro přípony názvů souborů](../extensibility/specifying-file-handlers-for-file-name-extensions.md) Poskytuje informace o tom, jak registrovat aplikace, které mohou otevřít, upravit a podobně, konkrétní příponu názvu souboru.

- [Registrovat operace pro přípony názvů souborů](../extensibility/registering-verbs-for-file-name-extensions.md) Popisuje, jak registrovat operace.

- [Spravovat přidružení souborů vedle](../extensibility/managing-side-by-side-file-associations.md) sebe Popisuje, jak zpracovávat souběžné instalace, ve kterých [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] by měla být vyvolána konkrétní verze pro otevření souboru.

## <a name="related-sections"></a>Související oddíly
- [Podpora více verzí sady Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) Popisuje problémy týkající se více verzí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a sady VSPackage během vývoje a nasazení pro koncové uživatele.
