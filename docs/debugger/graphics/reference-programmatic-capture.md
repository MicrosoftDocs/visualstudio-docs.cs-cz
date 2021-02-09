---
title: Referenční informace (programové zachycení) | Microsoft Docs
description: Pomocí programového rozhraní API pro programové zachycení můžete získat programovou kontrolu nad funkcemi zachycení Diagnostika grafiky.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 452360e04170bbf217c2f6ac0598533f3cab2259
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905106"
---
# <a name="reference-programmatic-capture"></a>Referenční dokumentace (zachytávání prostřednictvím kódu programu)
Diagnostika grafiky podporuje programovou kontrolu nad svými funkcemi zachycení prostřednictvím programového rozhraní API pro zachycení. Pomocí tohoto rozhraní API můžete přepínat a přidávat zprávy do HUD diagnostiky grafiky (zobrazení pro hlavní obrazovku), inicializovat a vytvářet soubory protokolu grafiky a zachytit informace grafiky.

## <a name="programmatic-capture-apis"></a>Rozhraní API pro programové zachycení

### <a name="classes"></a>Třídy

|Název|Description|
|----------|-----------------|
|[VsgDbg – třída](vsgdbg-class.md)|Představuje rozhraní, pomocí kterého je ovládána komponenta v aplikaci diagnostiky grafiky programově.|

### <a name="preprocessor-symbols"></a>Symboly preprocesoru

|Název|Description|
|----------|-----------------|
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|Definuje podle jejich přítomnosti, zda je soubor protokolu grafiky uložen do složky dočasných souborů uživatele.|
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|Definuje výchozí název souboru protokolu grafiky.|
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|Definuje podle své přítomnosti, zda `VsgDbg` je k dispozici výchozí instance třídy.|

## <a name="related-articles"></a>Související články

| Nadpis | Popis |
| - | - |
| [Zaznamenání grafických informací](capturing-graphics-information.md) | Ukazuje, jak zachytit informace grafiky z vaší aplikace založené na rozhraní DirectX, abyste mohli pomocí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Diagnostika grafikych nástrojů diagnostikovat problémy s vykreslováním. |
| [Přehled](overview-of-visual-studio-graphics-diagnostics.md) | Ukazuje, jak Diagnostika grafiky může pomáhat při ladění chyb při vykreslování v hrách a aplikacích DirectX. |
