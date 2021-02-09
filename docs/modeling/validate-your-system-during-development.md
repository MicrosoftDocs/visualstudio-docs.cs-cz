---
title: Ověřování systému během vývoje
description: Seznamte se s tím, jak Visual Studio vám může pomáhat udržet software v souladu s požadavky uživatelů a architekturou systému.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bac26664a2ef98cffbd60eee0647b39dd1108675
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924314"
---
# <a name="validate-your-system-during-development"></a>Ověřování systému během vývoje

Visual Studio může zajistit konzistenci softwaru v souladu s požadavky uživatelů a architekturou systému.

Chcete-li zjistit, které verze sady Visual Studio podporují jednotlivé funkce, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Klíčové úlohy

K ověření softwaru použijte následující úlohy:

|**Úlohy**|**Související témata**|
|-|-|
|Ujistěte **se, že váš software splňuje požadavky uživatelů**:<br /><br />Použijte požadavky a modely architektury, které vám pomůžou organizovat testy vašeho systému a jeho součástí. Tento postup pomáhá zajistit, že budete testovat požadavky, které jsou důležité pro uživatele a další zúčastněné strany, a pomůže vám rychle aktualizovat testy v případě změny požadavků.|- [Vývoj testů z modelu](../modeling/develop-tests-from-a-model.md)|
|**Ujistěte se, že váš software zůstává v souladu s zamýšleným návrhem vašeho systému:**<br /><br />Diagramy závislostí popisují zamýšlené závislosti mezi komponentami vaší aplikace. Během vývoje můžete ověřit, zda skutečné závislosti v kódu odpovídají zamýšlenému návrhu.|- [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Externí zdroje

|**Kategorie**|**Odkazy**|
|-|-|
|**Videa**|![odkaz na video ](../data-tools/media/playvideo.gif) [kanál 9: Doug 7: principy kódu a systémy s návrhem pomocí sady Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![odkaz na video ](../data-tools/media/playvideo.gif) [kanál 9: architekt aplikace](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-5-architecting-an-application)|
|**Fóra**|- [Nástroje pro vizualizaci sady Visual Studio & modelování](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Rozšiřitelnost sady Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)|

## <a name="see-also"></a>Viz také

- [Modelování uživatelských požadavků](../modeling/model-user-requirements.md)
- [Analýza a modelování architektury](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
