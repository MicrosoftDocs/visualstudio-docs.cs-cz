---
title: Referenční informace (programové zachycení) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a462d22df9768d2ffc8b344933e9f5c1f556575a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62895518"
---
# <a name="reference-programmatic-capture"></a>Referenční dokumentace (zachytávání prostřednictvím kódu programu)
Diagnostika grafiky podporuje programovou kontrolu nad svými funkcemi zachycení prostřednictvím programového rozhraní API pro zachycení. Pomocí tohoto rozhraní API můžete přepínat a přidávat zprávy do HUD diagnostiky grafiky (zobrazení pro hlavní obrazovku), inicializovat a vytvářet soubory protokolu grafiky a zachytit informace grafiky.

## <a name="programmatic-capture-apis"></a>Rozhraní API pro programové zachycení

### <a name="classes"></a>Třídy

|Název|Popis|
|----------|-----------------|
|[VsgDbg – třída](vsgdbg-class.md)|Představuje rozhraní, pomocí kterého je ovládána komponenta v aplikaci diagnostiky grafiky programově.|

### <a name="preprocessor-symbols"></a>Symboly preprocesoru

|Název|Popis|
|----------|-----------------|
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|Definuje podle jejich přítomnosti, zda je soubor protokolu grafiky uložen do složky dočasných souborů uživatele.|
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|Definuje výchozí název souboru protokolu grafiky.|
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|Definuje podle své přítomnosti, zda `VsgDbg` je k dispozici výchozí instance třídy.|

## <a name="related-articles"></a>Související články

| Nadpis | Popis |
| - | - |
| [Zaznamenání grafických informací](capturing-graphics-information.md) | Ukazuje, jak zachytit informace grafiky z vaší aplikace založené na rozhraní DirectX, abyste mohli pomocí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Diagnostika grafikych nástrojů diagnostikovat problémy s vykreslováním. |
| [Přehled](overview-of-visual-studio-graphics-diagnostics.md) | Ukazuje, jak Diagnostika grafiky může pomáhat při ladění chyb při vykreslování v hrách a aplikacích DirectX. |
