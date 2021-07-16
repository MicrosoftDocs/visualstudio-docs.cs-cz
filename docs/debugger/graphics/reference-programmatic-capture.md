---
title: Referenční informace (zachytávání pomocí kódu programu) | Microsoft Docs
description: Programové rozhraní API pro zachytávání využijte k programové kontrole funkcí zachytávání Diagnostika grafiky.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 572629235e3b64028b70ff59090f9c4f7991d323
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232697"
---
# <a name="reference-programmatic-capture"></a>Referenční dokumentace (zachytávání prostřednictvím kódu programu)
Diagnostika grafiky prostřednictvím programového rozhraní API pro zachytávání podporuje programovou kontrolu nad funkcemi zachytávání. Toto rozhraní API můžete použít k přepínání a přidávání zpráv do graphics diagnostics HUD (Head-Up Display), inicializaci a vytváření souborů protokolu grafiky a zaznamenání informací grafiky.

## <a name="programmatic-capture-apis"></a>Programová rozhraní API pro zachytávání

### <a name="classes"></a>Třídy

|Název|Description|
|----------|-----------------|
|[VsgDbg – třída](vsgdbg-class.md)|Představuje rozhraní, jehož prostřednictvím je součást diagnostiky grafiky v aplikaci řízena programově.|

### <a name="preprocessor-symbols"></a>Symboly preprocesoru

|Název|Description|
|----------|-----------------|
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|Definuje přítomnost, zda je soubor protokolu grafiky uložen do adresáře dočasných souborů uživatele.|
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|Definuje výchozí název souboru protokolu grafiky.|
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|Definuje podle přítomnosti, zda je poskytnuta `VsgDbg` výchozí instance třídy.|

## <a name="related-articles"></a>Související články

| Nadpis | Popis |
| - | - |
| [Zaznamenání grafických informací](capturing-graphics-information.md) | Ukazuje, jak zachytit informace grafiky z aplikace založené na DirectX, abyste mohli pomocí nástrojů [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Diagnostika grafiky diagnostikovat problémy s vykreslováním. |
| [Přehled](overview-of-visual-studio-graphics-diagnostics.md) | Ukazuje, Diagnostika grafiky vám můžou pomoct ladit chyby vykreslování ve hraech a aplikacích DirectX. |
