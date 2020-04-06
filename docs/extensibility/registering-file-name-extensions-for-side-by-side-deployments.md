---
title: Registrace přípon názvů souborů pro souběžná nasazení | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6717625a44b48a25d293f68d01cd9fa3c7c24853
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701543"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Registrace přípon názvů souborů pro souběžná nasazení
Pro VSPackages nasazené v prostředí vedle sebe, musíte zaregistrovat přípony názvů souborů přidružit soubory ke správné verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]aplikace . Pokud nepoužíváte příponu názvu souboru specifické pro verzi, registrace umožňuje uživatelům [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]otevřít soubory projektu a položek projektu v příslušné verzi aplikace .

## <a name="in-this-section"></a>V tomto oddílu
- [O příponách názvů souborů](../extensibility/about-file-name-extensions.md) Popisuje, jak jsou registrovány přípony názvů souborů.

- [Určení obslužných rutin souborů pro přípony názvů souborů](../extensibility/specifying-file-handlers-for-file-name-extensions.md) Obsahuje informace o tom, jak zaregistrovat aplikace, které lze otevřít, upravit a tak dále, konkrétní příponu názvu souboru.

- [Registrace sloves pro přípony názvů souborů](../extensibility/registering-verbs-for-file-name-extensions.md) Popisuje, jak registrovat slovesa.

- [Správa přidružení souborů vedle sebe](../extensibility/managing-side-by-side-file-associations.md) Popisuje, jak zpracovat souběžné instalace, ve kterých [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] by měla být vyvolána konkrétní verze aplikace pro otevření souboru.

## <a name="related-sections"></a>Související oddíly
- [Podpora více verzí sady Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) Popisuje problémy související s [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] více verzemi a vspackage během vývoje a nasazení koncovým uživatelům.
